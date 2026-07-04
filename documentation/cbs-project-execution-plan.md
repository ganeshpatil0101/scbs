# CBS SaaS Platform — Phase-Wise Execution Plan

**Prepared for:** Ganesh | Core Banking Software for Maharashtra Cooperative Banks
**Basis:** Current documentation state in `AI_INDEX.md`, `05-ui-ux/`, `01-architecture/architecture-overview.md`, `Software-Documentation-Standard.md`

---

## 0. Current State Snapshot (baseline for this plan)

| Area | Status |
|---|---|
| Vision / Business Goals | ✅ Done (`vision.md`, `business-goals.md`) |
| Glossary / System Boundaries | ❌ TODO |
| Architecture overview | 🟡 Draft — **AWS `ap-south-1` (Mumbai) confirmed** (DEC-006); remaining arch docs still TODO |
| `09-ai-context/` (coding standards, naming, folder structure) | ❌ Does not exist |
| `02-business-domains/` (business rules, use cases) | ❌ Not started |
| `03-api-contracts/` | ❌ Empty |
| `04-database-design/` | ❌ Not started |
| `05-ui-ux/` screen specs | 🟡 ~40 screens documented, many `TODO` dropdown values / missing tabs |
| Interactive mockups | 🟡 New Customer Tab 1–2 built (React), Tab 3 KYC pending |
| Skill files | ✅ `generate-document`, `generate-ui-screen` complete |
| Backend / Frontend code | ❌ Not started (pre-code stage) |

This plan is sequenced so **nothing gets built on an undocumented assumption** — consistent with your "clarify before generating" and "no invention" principles.

---

## PHASE 1 — Documentation, Architecture & Design Completion
**Goal:** Every artifact needed to generate code without further clarification exists. No code is written in this phase.

### 1.1 Close Project-Overview Gaps
- [x] Author `00-project-overview/glossary.md` — define *tenant, AMC, GL Head, scheme, member vs nominal member, DP (drawing power)*, etc. (referenced but undefined in `vision.md`, `business-goals.md`)
- [x] Author `00-project-overview/system-boundaries.md` — what's in/out of scope (e.g., no SMS/WhatsApp gateway build, no payment gateway integration in v1?)

### 1.2 Finalize Architecture
- [x] **Cloud provider decided**: AWS `ap-south-1` (Mumbai) — recorded as DEC-006 in `01-architecture/architecture-overview.md` (supersedes earlier OCI `ap-mumbai-1` draft)
- [ ] Add missing `01-architecture/` files per `Software-Documentation-Standard.md`: `domain-driven-design.md`, `security-architecture.md`, `technology-stack.md`
- [ ] Confirm DEC-001–DEC-006 decisions in `01-architecture/architecture-overview.md` are still valid at current scope (1 tenant Year 1)

### 1.3 Establish AI Context (`09-ai-context/`)
- [ ] `coding-standards.md` — Angular/NestJS conventions, NgRx patterns, Reactive Forms rules
- [ ] `naming-conventions.md` — file, variable, API, DB naming
- [ ] `folder-structure.md` — monorepo/module layout
- [ ] `generation-rules.md` — how Cursor/Claude should scaffold consistently
- [ ] `technology-stack.md` — pin exact versions (Angular 17+, NestJS, PostgreSQL, etc.)

> This unblocks consistent code generation in Phase 2 — currently `generate-ui-screen` skill has no coding-standards doc to point to.

### 1.4 Complete UI/UX Specs (close TODOs)
Priority order — screens with the most `TODO` dropdown values / missing tabs first:
- [ ] Fill dropdown value lists flagged `TODO` across scheme screens (Daily/Savings/FD/Recurring/Loan New Scheme — duration type, status values, month/day pickers)
- [ ] Complete missing tabs: FD New Account (Tabs 3–4), Daily Transaction (Tabs 3, 4, 6), Deposit Loan Installment Payment (Tabs 2–6), Shares Transfer (Tab 3), New Loan Scheme (Category dropdown, Fee dropdown)
- [ ] Capture User Role screen's full form list per menu (currently only Accounting sample rows captured)

### 1.5 Interactive Mockups (Tiered Workflow: Spec → Prototype → Cursor)
- [ ] Finish **New Customer** screen Tab 3 (KYC Documents) — in progress
- [ ] Build 2–3 more mockups to validate patterns before scaling to 40+ screens:
  - One **transaction screen** (e.g., Savings Transaction — 5-tab pattern reused by FD/Daily/Recurring)
  - One **New Scheme (Settings)** screen (multi-tab wizard with grids — reused pattern)
  - One **list/register screen** (validates BG-005 interactive reporting: search/filter/export)
- [ ] Once these 3 patterns are validated, mockups for remaining screens can be lower-effort (pattern reuse, not novel work)

### 1.6 Component Inventory & Design System
- [ ] Extract a **shared component list** from mockups so far: tabbed wizard shell, data grid w/ export, dropdown-with-add(`+`), read-only computed field, address block, nominee block, GL/branch/account lookup widget
- [ ] Document these as reusable Angular Material components in `generate-ui-screen/SKILL.md` (avoids reinventing per screen)

### 1.7 One Fully-Documented Business Domain (Template)
Pick **Customer & Membership** (most mockup progress already) as the template domain:
- [ ] `02-business-domains/customer/overview.md`
- [ ] `business-rules.md` (BR-001…)
- [ ] `use-cases.md` (UC-001…)
- [ ] `workflows.md`
- [ ] `acceptance-tests.md` (AT-001…)
- [ ] `changelog.md`

> Use this as the **template** so remaining domains (Accounts, Loans, Accounting) follow identical structure in Phase 3.

### 1.8 Seed API Contracts & Database Design
- [ ] `03-api-contracts/` — draft endpoints only for Customer + Auth/User modules (enough to start Phase 2), one file per endpoint per standard
- [ ] `04-database-design/` — entity docs for `customer`, `user`, `role`, `branch`, `organization` (tenant-shared master entities first)

**Phase 1 exit criteria:** AI_INDEX.md has no `TODO` links for Project Overview/Architecture/AI-Context; Customer domain is fully documented end-to-end (docs → mockup → API contract → DB entity); component inventory exists.

---

## PHASE 2 — Foundation Setup
**Goal:** A working, authenticated, multi-tenant skeleton — no business features yet.

- [ ] **Cloud & repo setup**: AWS account in `ap-south-1` (Mumbai, per DEC-006), Git repo structure per `folder-structure.md`, CI/CD pipeline (GitHub Actions) skeleton
- [ ] **Dev/QA environment** per DEC-005 (RDS `t3.micro`, EC2 free-tier, no NAT/WAF)
- [ ] **NestJS API skeleton**: control_catalog DB, tenant connection router/pool manager (per architecture Section 3–4), health check endpoint
- [ ] **Angular app skeleton**: routing shell, Angular Material theme, ngx-translate (Marathi/English) wired, NgRx store scaffold
- [ ] **Authentication & Authorization flow**:
  - JWT auth with tenant claim (per architecture sequence diagram)
  - Role-based permission matrix engine (All Rights / View Only / No Rights) driving `*appHasPermission` directive — implements the User Role screen spec
  - New User / New Employee / User Role screens built as the **first real screens** (they gate everything else)
- [ ] **Basic UI implementation**: Login screen, Dashboard shell, breadcrumb nav pattern (`डॅशबोर्ड > Module > Screen`)
- [ ] **Master data APIs**: Branch, Organization, GL Head lookups (needed by nearly every downstream screen)

**Phase 2 exit criteria:** A user can log in, be assigned a role, see permission-gated menu, and CRUD a Branch/GL Head master record end-to-end (UI → API → DB).

---

## PHASE 3 — Core Module Build-Out (Iterative, Domain by Domain)
**Goal:** Deliver working modules using the Phase 1 template (docs → API contract → DB → UI → tests) repeated per domain.

Recommended build order (based on dependency graph — Customer/Membership underpins everything else):

| Order | Domain | Key Screens (from `AI_INDEX.md`) |
|---|---|---|
| 1 | Customer & Membership | New Customer, Customer List, New Membership, Shares Transfer |
| 2 | Settings/Master + Scheme config | New User, User Role, New GL Group/Head, all New Scheme screens |
| 3 | Savings | New Account, Transaction, Manual Interest |
| 4 | Fixed Deposit | New Account, Transaction, Account Register, Interest Multiplier, Renewal List |
| 5 | Daily (Pigmy) | New Account, New Agent, Transaction, Agent Collection |
| 6 | Recurring | New Account, Credit Transaction, Manual Interest |
| 7 | Loan | New Loan, New Deposit Loan |
| 8 | Accounting (GL entries) | Jama, Nave, Transfer, Rokhapal, Multi-GL, Note Exchange |

**Per-domain checklist (repeat for each):**
1. Complete `02-business-domains/<domain>/` docs (business rules, use cases, acceptance tests)
2. Finalize `03-api-contracts/<domain>/` (one file per endpoint)
3. Finalize `04-database-design/` entities + relationships + constraints
4. Generate Angular screens via `generate-ui-screen` skill from the finished `05-ui-ux/` spec
5. Implement NestJS module (controller/service/repository) per API contract
6. Write acceptance tests (AT-xxx) as integration tests
7. Update `changelog.md`

**Phase 3 exit criteria:** All modules needed for **year-end close and accurate accounting reports** (BG-001) are functional — this is your Year-1 success metric, so Accounting + FD/Savings + Membership (shares/dividend) must be complete before pilot.

---

## PHASE 4 — Cross-Cutting: Reporting, Security, Non-Functional
**Goal:** Meet BG-005 (interactive reporting) and production-readiness bars.

- [ ] Standardize search/filter/advanced-search/export across **every** list/register screen (audit against `05-ui-ux/` — several still have `TODO` grid actions)
- [ ] `06-non-functional/` — `security.md`, `performance.md` (e.g., PERF-001 balance inquiry < 200ms), `availability.md`, `audit.md`
- [ ] `07-compliance/` — cooperative banking accounting norms (due-diligence only, not RBI-mandated per BG-008)
- [ ] Production security hardening: WAF, CMK (KMS), Secrets Manager, CloudTrail/RDS audit logging (flagged as follow-up in `01-architecture/architecture-overview.md` Section 6)
- [ ] `08-testing/` — test plan referencing AT-xxx from each domain

---

## PHASE 5 — UAT, Pilot Tenant Onboarding, Go-Live
**Goal:** BG-001 — one live tenant, accurate reports, low-friction year-end close.

- [ ] Define the missing **usability benchmark** for BG-004 (task completion time / error rate / training time) — currently unmeasured
- [ ] UAT with actual cooperative bank staff (clerk/cashier low-literacy validation — this is your core UX differentiator, test it explicitly)
- [ ] Data migration from incumbent CBS for pilot tenant
- [ ] Parallel-run period (old + new system) through at least one interest-posting cycle
- [ ] Year-end close dry run — this is your literal Year-1 success criterion
- [ ] Go-live + hypercare support window

---

## PHASE 6 — Scale-Up (Year 2–3, BG-002)
- [ ] Onboard tenants 2–10 (Maharashtra only, per `vision.md` explicit non-goal on geographic expansion)
- [ ] Revisit DEC-002 (introduce RDS Proxy/PgBouncer once tenant count > 10–15)
- [ ] Revisit pricing/margin tracking (BG-003 — price point still undefined, flagged as open commercial decision)
- [ ] Define and scope `03-api-contracts/` public API surface (BG-006 — currently unscoped: which modules, auth model, rate limits)

---

## Open Decisions Blocking This Plan (resolve early)

| # | Decision | Blocks |
|---|---|---|
| 1 | Per-branch price point / AMC amount (BG-003) | Not a technical blocker, but needed before pilot sales |
| 2 | Usability benchmark definition (BG-004) | Phase 5 UAT acceptance criteria |
| 3 | Public API scope/auth model (BG-006) | Phase 6, not urgent now |

---

## Suggested Immediate Next Steps (this week)
1. Author `glossary.md` (fast, unblocks nothing else but closes a visible TODO)
2. Finish New Customer Tab 3 mockup, then move to the Savings Transaction mockup (validates the 5-tab transaction pattern reused across 4 modules)
3. Start `09-ai-context/coding-standards.md` — needed before any Cursor-based screen generation begins
4. Add remaining `01-architecture/` docs (`domain-driven-design.md`, `security-architecture.md`, `technology-stack.md`) — now unblocked by AWS decision
