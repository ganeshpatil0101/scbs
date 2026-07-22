# Technology Stack — CBS SaaS Platform

## Purpose

Pins the exact runtime, framework, and infrastructure versions AI agents and developers must use when scaffolding code for this project. Prevents version drift across generated Angular/NestJS artifacts.

## Scope

- Application runtime and frameworks (frontend, backend, database).
- Core libraries already decided in standing architectural decisions.
- AWS service mapping is **not** duplicated here — see [architecture-overview.md](../01-architecture/architecture-overview.md).

## Dependencies

- [../01-architecture/architecture-overview.md](../01-architecture/architecture-overview.md) — DEC-001–DEC-006
- [../00-project-overview/system-boundaries.md](../00-project-overview/system-boundaries.md) — v1 scope
- [coding-standards.md](coding-standards.md) — how to use these technologies
- [folder-structure.md](folder-structure.md) — where code lives (monorepo DEC-007)

---

## Content

> **Baseline pinned:** 2026-07-22  
> **Re-verify before Phase 2 kickoff:** Run `node -v`, `ng version`, and `npm outdated` in each workspace before locking `package.json`. Patch versions below are directional — confirm latest stable patch at scaffold time.

### Application stack

| Layer | Technology | Baseline version | Notes |
| :--- | :--- | :--- | :--- |
| Frontend framework | Angular | **22.x** (22.0.7 as of baseline) | Standalone components only — no NgModules |
| UI library | Angular Material | **22.x** (match Angular major) | Theme tokens — no hardcoded colors |
| Frontend state | NgRx | **19.x** (match Angular 22 peer range) | One feature state per multi-tab wizard screen |
| Local UI state | Angular signals | Built-in (Angular 22) | Tab index, expanded panels, loading flags |
| Forms | Angular Reactive Forms | Built-in | Never template-driven |
| i18n | ngx-translate | **16.x** | Marathi (`mr`) + English (`en`) required |
| Responsive layout | Angular CDK | Match Angular 22 | `BreakpointObserver` for breakpoints |
| Backend framework | NestJS | **11.x** (11.1.28 as of baseline) | NestJS 12 is pre-release — do not use until GA |
| Runtime | Node.js | **24.x LTS** ("Krypton") | Active LTS as of baseline; do not use odd-numbered Node for production |
| Language | TypeScript | **5.9+** | Strict mode enabled |
| Database | PostgreSQL (AWS RDS) | **17.10** | RDS-supported minor; PostgreSQL 18.x available but 17.x preferred for pilot stability |
| ORM / query layer | TypeORM or Prisma | **TBD at Phase 2 kickoff** | Document choice in architecture when decided |
| API format | REST + JSON | — | Internal API only in Phase 2; public API deferred (BG-006) |
| Auth | JWT | — | Tenant claim per DEC-001; see architecture sequence diagram |
| Unit tests | Jest | Match NestJS/Angular CLI defaults | Backend: Jest; Frontend: Jest or Vitest per Angular CLI default |
| Package manager | pnpm | **9.x** | Monorepo workspaces (DEC-007) — see [folder-structure.md](folder-structure.md) |

### Frontend architectural decisions (fixed — do not re-litigate)

| Decision | Value |
| :--- | :--- |
| Component model | Standalone components (no NgModules) |
| Forms | Reactive Forms (`FormGroup` / `FormBuilder`) |
| Cross-tab / wizard state | NgRx — one feature state per wizard screen |
| Local-only UI state | Component `signal()`s — not in NgRx |
| Unresolved spec gaps | Scaffold with placeholder services — never block or invent values |

### Backend architectural decisions (fixed — do not re-litigate)

| Decision | Value |
| :--- | :--- |
| Multi-tenancy | Database-per-tenant (DEC-001) — no `tenant_id` column in tenant DB tables |
| Tenant routing | Connection router / pool manager → `control_catalog` lookup |
| Validation | `class-validator` + `class-transformer` on DTOs |
| Module layout | One NestJS module per business domain |
| Financial data types | `numeric(18,2)` for money; `numeric(7,4)` for rates — never `float` |

### Infrastructure (summary — full detail in architecture doc)

| Layer | Service | Region |
| :--- | :--- | :--- |
| Cloud provider | AWS | `ap-south-1` (Mumbai) — DEC-006 |
| Frontend hosting | S3 + CloudFront | `ap-south-1` |
| API compute (prod) | ECS Fargate | `ap-south-1` |
| API compute (dev/QA) | EC2 `t3.micro` | `ap-south-1` — DEC-005 |
| Database | RDS PostgreSQL | `ap-south-1`, Single-AZ dev / Multi-AZ prod |
| Secrets (prod) | AWS Secrets Manager | — |
| Secrets (dev/QA) | SSM Parameter Store | DEC-005 |
| CI/CD | GitHub Actions | — (skeleton at Phase 2) |

### Dev tooling (Phase 2)

| Tool | Purpose |
| :--- | :--- |
| ESLint + `@angular-eslint` | Frontend lint |
| Prettier | Formatting (shared config at repo root) |
| Husky + lint-staged | Pre-commit hooks (optional at Phase 2) |
| Docker | Local dev containers (optional) |

### Explicitly out of scope for v1

Per [system-boundaries.md](../00-project-overview/system-boundaries.md):

- Mobile banking, UPI/payment rails, SMS/WhatsApp gateways
- Third-party e-KYC APIs
- External BI / data warehouse
- Public/third-party API surface (BG-006 — Phase 6)

---

## Related Documents

- [../01-architecture/architecture-overview.md](../01-architecture/architecture-overview.md)
- [../04-database-design/database-design-standards.md](../04-database-design/database-design-standards.md)
- [coding-standards.md](coding-standards.md)
- [folder-structure.md](folder-structure.md)
- [generation-rules.md](generation-rules.md)
- [../cbs-project-execution-plan.md](../cbs-project-execution-plan.md)
