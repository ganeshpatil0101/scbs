# Architecture Overview — CBS SaaS Infrastructure (ARCH-001)

Status: Draft for discussion. Covers multi-tenancy approach, request flow, AWS service mapping, and cost-efficiency decisions for the cooperative-bank CBS SaaS platform.

## 1. Scope

This document describes the infrastructure architecture for the multi-tenant core banking SaaS platform: how tenants (cooperative banks) are isolated at the database layer, how API requests are routed to the correct tenant database, which AWS services back each layer, and the cost trade-offs behind each environment decision.

It does not cover business domain logic (Accounts, Loans, Transactions modules) — those will get their own module documentation once domain requirements are defined.

> **Open item:** an earlier architecture decision recorded OCI (`ap-mumbai-1`) as the deployment target. This document evaluates an AWS-based deployment for cost/service comparison. The cloud provider choice is **not yet finalized** — treat the AWS service mapping and costs below as one option under evaluation, not a committed decision, until confirmed.

## 2. Decision log

### DEC-001: Multi-tenancy model

- **Context:** Each cooperative bank's data must be isolated for compliance and audit reasons, and each bank's data migration must be independently scoped.
- **Options considered:**
  1. Single database, shared tables, `tenant_id` column on every row.
  2. One RDS instance, separate PostgreSQL database per tenant.
  3. One RDS instance per tenant.
- **Decision:** Option 2 — one RDS instance hosting a separate PostgreSQL database per cooperative bank.
- **Rationale:** Strong logical isolation (no `tenant_id` filter bugs, independent backup/restore, clean migration boundary per bank) without paying for a dedicated instance per tenant.
- **Trade-off accepted:** Postgres connections are bound to a single database, so the API layer must maintain a separate connection pool per tenant (see Section 4). This adds connection-count management work as tenant count grows (see DEC-002).

### DEC-002: Connection pooling at scale

- **Context:** Each tenant pool consumes several connections; multiplied across API nodes and tenants, this can approach the RDS instance's `max_connections` limit well before traffic actually requires it.
- **Decision:** Start with in-process pooling (one pool per tenant, cached after first use). Introduce **Amazon RDS Proxy** (or self-managed PgBouncer) once tenant count exceeds roughly 10–15, or sooner if connection-count alarms fire.
- **Rationale:** Avoids premature complexity for the pilot phase while having a defined trigger to add pooling infrastructure before it becomes an incident.

### DEC-003: Environment uptime scheduling

- **Context:** Dev/QA and Prod compute both bill by the hour; nightly shutdown was evaluated for both to reduce cost.
- **Decision:** Stop Dev/QA compute and database outside working hours (e.g., 7:00 AM–9:00 PM, weekdays) using a scheduler. **Do not** stop Production compute on a nightly schedule.
- **Rationale:** Dev/QA has no external users and the saving is close to 100% of off-hours compute cost with zero risk. Production serves a banking platform where customers expect 24x7 access (UPI/mobile banking conventions in India are always-on); a nightly outage carries SLA, contractual, and reputational risk that outweighs the partial saving (compute is only one line of the prod bill — storage, NAT, ALB, and WAF keep running regardless of whether compute is stopped). Production cost is instead addressed via DEC-004.

### DEC-004: Production cost optimization (without downtime)

- **Decision:** Use Reserved Instances/Savings Plans (1-year term) on RDS and compute once usage patterns stabilize post-pilot, scheduled scale-down of API node count during low-traffic overnight hours (not a full stop), and Graviton (ARM, `t4g`/`m7g`) instance families instead of Intel equivalents.
- **Rationale:** Each lever reduces cost without an availability window. Combined, expected to offset roughly 40–55% of the on-demand compute cost.

## 3. System architecture

```mermaid
graph TD
    U[Bank user / app] -->|HTTPS, static assets| CF[CloudFront CDN]
    CF --> S3F[S3 - Angular build]
    U -->|API calls, HTTPS| WAF[WAF]
    WAF --> ALB[Application Load Balancer]
    ALB --> API1[API node 1 - NestJS, Fargate]
    ALB --> API2[API node 2 - NestJS, Fargate]
    API1 --> ROUTER[Connection router / pool manager]
    API2 --> ROUTER
    API1 --> SM[Secrets Manager]
    API1 --> S3D[S3 - documents/KYC]
    ROUTER --> CAT[(control_catalog DB)]
    ROUTER --> RDS[(RDS PostgreSQL instance)]
    RDS --> DB1[(bank_abc database)]
    RDS --> DB2[(bank_xyz database)]
```

Notes:
- `control_catalog` is a small internal database (not customer financial data) mapping `tenant_id → database name/credentials`. Looked up once per tenant per API process, then cached.
- `bank_abc` / `bank_xyz` represent one database per cooperative-bank tenant, all hosted on the same RDS instance (see DEC-001).
- API nodes are stateless and interchangeable — any node can serve any tenant; there is no per-tenant server.

## 4. Request flow (sequence)

Typical authenticated transaction request, showing the cold-start path (first request for a tenant on a given API node) versus the warm path (pool already cached):

```mermaid
sequenceDiagram
    participant U as Bank user (app)
    participant ALB as Load balancer
    participant API as API node (NestJS)
    participant ROUTER as Connection router
    participant CAT as control_catalog DB
    participant TDB as Tenant DB (bank_abc)

    U->>ALB: POST /transactions (JWT with tenant claim)
    ALB->>API: forward request
    API->>API: extract tenant_id from JWT
    API->>ROUTER: getTenantPool(tenant_id)
    alt pool not cached on this node
        ROUTER->>CAT: lookup db_name, credentials
        CAT-->>ROUTER: connection details
        ROUTER->>TDB: open pooled connection
    end
    ROUTER-->>API: pooled connection
    API->>TDB: insert transaction record
    TDB-->>API: success
    API-->>ALB: 201 Created
    ALB-->>U: response
```

## 5. AWS service mapping

| Layer | Service | Purpose |
|---|---|---|
| Frontend hosting | S3 + CloudFront | Angular static build, edge caching |
| TLS / DNS | ACM, Route 53 | Certificates, domain routing |
| API compute | ECS Fargate (or EC2 + Auto Scaling) | Stateless NestJS containers |
| Load balancing | Application Load Balancer | Routes to API nodes, health checks |
| Database | RDS for PostgreSQL | One instance, database-per-tenant (DEC-001) |
| Connection scaling | RDS Proxy (added per DEC-002) | Pool multiplexing once tenant count grows |
| File storage | S3 (separate bucket from frontend) | KYC documents, statements |
| Secrets | Secrets Manager | DB credentials, API keys |
| Security | WAF, KMS | Edge filtering, encryption at rest |
| Monitoring | CloudWatch | Logs, metrics, alarms (incl. connection-count alarm for DEC-002 trigger) |
| Networking | VPC, NAT Gateway | Private subnets for API/DB, controlled outbound |

## 6. Security

- All inter-tier traffic stays inside the VPC; only the ALB and CloudFront are internet-facing.
- Database credentials are never embedded in application code or images — fetched from Secrets Manager at runtime.
- Each tenant database is a distinct PostgreSQL database (not just a schema or row filter), so a query-construction bug cannot leak across tenants at the data-access layer.
- WAF sits in front of the ALB for common web-attack filtering; this is a baseline, not a substitute for a dedicated security review before go-live with real customer financial data.
- Audit logging (CloudTrail, RDS audit logging) is required before production go-live but is not detailed in this document — track as a follow-up architecture item.

## 7. Deployment environments

| Aspect | Dev/QA | Production |
|---|---|---|
| RDS Multi-AZ | No (Single-AZ) | Yes |
| API node count | 1 | 2 (minimum, for HA) |
| Uptime schedule | Stopped outside ~7 AM–9 PM weekdays (DEC-003) | Always-on, scaled down overnight (DEC-004) |
| Purpose | Feature development, QA testing, tenant migration rehearsal | Live tenant traffic |

## 8. Scalability

- API nodes scale horizontally behind the ALB; adding a node requires no database change since all nodes share the same tenant-pool-resolution logic.
- The RDS instance scales vertically (larger instance class) as aggregate tenant data/load grows; because tenants share one instance, this is a single scaling decision rather than per-tenant infrastructure changes.
- Read-heavy reporting workloads, if they emerge, should be offloaded to a read replica rather than scaling the primary instance further — not yet required at pilot scale.
- Connection pooling (DEC-002) is the primary scaling constraint to monitor as tenant count grows, ahead of raw compute or storage limits.

## 9. Cost efficiency

Estimates below are **directional, on-demand, ap-south-1 (Mumbai) list-price approximations** as of mid-2026 — confirm exact figures with the [AWS Pricing Calculator](https://calculator.aws/) before budgeting. All figures USD/month unless noted.

### 9.1 Dev/QA

| Item | Always-on | Scheduled stop (DEC-003: ~10 hrs/day, weekdays) |
|---|---|---|
| API compute | ~$38 | ~$13 |
| RDS Single-AZ | ~$68 | ~$23 |
| NAT Gateway | ~$50 | ~$50 (cannot be stopped the same way) |
| S3 + CloudFront | ~$10 | ~$10 |
| Misc (Secrets Manager, Route 53, CloudWatch) | ~$10 | ~$10 |
| **Total** | **~$176/mo (~$2,100/yr)** | **~$106/mo (~$1,270/yr)** |

### 9.2 Production

| Item | On-demand | With DEC-004 optimizations applied |
|---|---|---|
| API compute (2 nodes, HA) | ~$80 | ~$50 (RI + Graviton + overnight scale-down) |
| ALB | ~$25 | ~$25 |
| RDS Multi-AZ | ~$150 | ~$95 (RI + Graviton) |
| NAT Gateway (2 AZ) | ~$90 | ~$90 |
| S3 + CloudFront | ~$30 | ~$30 |
| WAF | ~$10 | ~$10 |
| Secrets Manager, CloudWatch, Route 53, KMS, backups | ~$20 | ~$20 |
| **Total** | **~$405/mo (~$4,900/yr)** | **~$320/mo (~$3,840/yr)** |

### 9.3 Combined annual estimate

- On-demand, no optimization: **~$7,000/yr**
- With DEC-003 (Dev/QA scheduling) and DEC-004 (Prod RI + scale-down + Graviton): **~$5,100/yr**

A 1-year Reserved Instance/Savings Plan commitment should only be made after 2–3 months of observed real usage, not at launch — committing too early on guessed instance sizes can lock in the wrong shape.

## Related Documents
- ../AI_INDEX.md
