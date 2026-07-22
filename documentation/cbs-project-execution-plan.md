# CBS SaaS Platform — Phase-Wise Execution Plan

**Prepared for:** Ganesh | Core Banking Software for Maharashtra Cooperative Banks
**Basis:** Current documentation state in `AI_INDEX.md`, `05-ui-ux/`, `01-architecture/architecture-overview.md`, `Software-Documentation-Standard.md`

---

## 0. Current State Snapshot (re-validated 2026-07-22)

| Area | Status |
|---|---|
| Vision / Business Goals | ✅ Done (`vision.md`, `business-goals.md`) |
| Glossary / System Boundaries | ✅ Done (`glossary.md`, `system-boundaries.md`) |
| Architecture overview | 🟡 Draft — **AWS `ap-south-1` (Mumbai)** + DEC-001–007 recorded; still missing `domain-driven-design.md` + `security-architecture.md` |
| `09-ai-context/` (coding standards, naming, folder structure, generation-rules, technology-stack) | ✅ Done — 5 files; skills/rules wired to [Agent Skills](https://agentskills.io) standard |
| `02-business-domains/` (business rules, use cases) | ❌ Not started |
| `03-api-contracts/` | ❌ Empty (folder not created) |
| `04-database-design/` | 🟡 Standards + overview + reports-traceability done; **shared/domain entity files not started** |
| `05-ui-ux/` screen specs | 🟡 **~51 active** specs; **§1.4 priority closed**; residual = Deposit Loan Installment Tabs 2–6 + low-priority secondary TODOs |
| Interactive mockups | ✅ **58 HTML mockups** — active-spec coverage complete; patterns validated |
| Component inventory (§1.6) | ✅ Starting catalog in `generate-ui-screen.mdc` + `ui-simplification-patterns.md` |
| Skill files | ✅ `generate-document`, `generate-ui-screen`, `generate-ui-mockup`, `design-database-schema`, `optimize-ui-ux`, `coding-standards` |
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
- [x] **`technology-stack.md`** — pinned in [`09-ai-context/technology-stack.md`](09-ai-context/technology-stack.md) (Angular 22, NestJS 11, Node 24 LTS, PostgreSQL 17.10 — baseline 2026-07-22); lives under AI Context per `Software-Documentation-Standard.md`, not duplicated under `01-architecture/`
- [x] **DEC-001–DEC-007 recorded** in `architecture-overview.md` and remain consistent with Year-1 scope (1 pilot tenant; monorepo DEC-007; RDS Proxy deferred per DEC-002 until 10–15 tenants)
- [ ] Author `01-architecture/domain-driven-design.md` — bounded contexts, aggregates, anti-corruption notes aligned to UI modules
- [ ] Author `01-architecture/security-architecture.md` — JWT/tenant claim, RBAC (All Rights / View Only / No Rights), encryption, secrets, audit trail (prod hardening stays Phase 4)

### 1.3 Establish AI Context (`09-ai-context/`)
- [x] `coding-standards.md` — Angular/NestJS conventions, NgRx patterns, Reactive Forms rules
- [x] `naming-conventions.md` — file, variable, API, DB naming
- [x] `folder-structure.md` — monorepo/module layout (DEC-007)
- [x] `generation-rules.md` — how Cursor/Claude should scaffold consistently
- [x] `technology-stack.md` — pin exact versions (Angular 22, NestJS 11, Node 24 LTS, PostgreSQL 17.10 — baseline 2026-07-22)

> ✅ **§1.3 closed** — unblocks consistent code generation in Phase 2. `generate-ui-screen` and `coding-standards.mdc` delegate to `09-ai-context/`.

### 1.4 Complete UI/UX Specs (close TODOs)
**Status:** 🟡 **Priority items closed** (re-validated 2026-07-22) — original 1.4 blockers resolved via capture + UX consolidation; **not blocking** Phase 1 template domain or Phase 2 skeleton.

**Original priority items (2026-07 audit) — closed:**
- [x] Fill dropdown value lists flagged `TODO` across scheme screens (Daily/Savings/FD/Recurring/Loan New Scheme — duration type, status values, month/day pickers) — **done**; unified [new-scheme-screen.md](05-ui-ux/settings/schemes/new-scheme-screen.md) has zero `TODO` markers
- [x] Complete missing tabs where originally flagged:
  - [x] FD New Account Tab 4 (Other) — captured in [new-fd-account-screen.md](05-ui-ux/fixed-deposit/new-fd-account-screen.md)
  - [x] Shares Transfer Tab 3 (Transfer) — captured in [shares-transfer-screen.md](05-ui-ux/membership/shares-transfer-screen.md) / management consolidation
  - [x] New Loan Scheme Category + Fee dropdowns — captured (superseded into unified scheme screen)
  - [x] FD New Account Tab 3 (Joint Holder) — **captured** (shared joint-holder pattern; conditional on Tab 1 checkbox)
  - [x] Daily Transaction Tabs 3, 4, 6 — **superseded** by unified [deposit-account-transaction-screen.md](05-ui-ux/accounting/deposit-account-transaction-screen.md) (Savings/FD/Daily/Recurring deposit Txn)
  - [x] Savings / Recurring / Daily New Account Nominee + Joint Holder tabs — **captured** (zero `TODO` on those specs)
  - [x] Daily Agent Collection Tabs 2–3 — **captured** in [agent-collection-management-screen.md](05-ui-ux/daily/agent-collection-management-screen.md) (Brief Details + Transfer + Collection List)
- [x] User Role form list — **closed by design** in [user-role-screen.md](05-ui-ux/settings/master/user-role-screen.md): rows load dynamically from the app menu registry (Accounting sample is layout-only; no static full-matrix capture needed)
- [ ] Deposit Loan Installment Payment Tabs 2–6 — still `TODO` in [deposit-loan-installment-payment-screen.md](05-ui-ux/fixed-deposit/deposit-loan-installment-payment-screen.md) (needs source capture; **defer** — not on Phase 2 / Customer-domain critical path)

**Residual `TODO` gaps (re-audit 2026-07-22 — low priority / non-blocking):**

| Category | Screens still flagged |
|---|---|
| Uncaptured tabs / sections | Deposit Loan Installment (Tabs 2–6); Membership/Dividend Transaction (Nominee/KYC shared tabs — reuse patterns); Loan Information (one tab); New Deposit Loan (one section header) |
| Master-data dropdowns | Bank select, cheque type, scheme/status/scroll lists on transaction screens (dynamic master data — scaffold at build time per `generate-ui-screen` skill) |
| Deferred / low priority | Transaction Passing advanced filters; Loan Account Register / Member Register advanced-search links; deposit-account Ledger detail link; interest-date pickers on assessment screens |

> **Note:** Remaining dropdown `TODO`s are **dynamic master data** — scaffold in Phase 2/3. Shared KYC/Nominee tabs reuse already-captured patterns (`app-kyc-info-tab`, nominee-as-customer). Only Deposit Loan Installment secondary tabs remain as meaningful capture leftovers.

### 1.5 Interactive Mockups (Tiered Workflow: Spec → Prototype → Cursor)
**Status:** ✅ **Closed** (re-validated 2026-07-21) — **58** HTML mockups; **51/51** active (non-superseded) screen specs have a mockup under `05-ui-ux/mockups/`.

- [x] Finish **New Customer** screen Tab 3 (KYC Documents) — done in [mockups/customer/new-customer-screen/](05-ui-ux/mockups/customer/new-customer-screen/)
- [x] Build 2–3 more mockups to validate patterns before scaling:
  - [x] One **transaction screen** — Savings/FD/Daily/Recurring + unified deposit-account transaction mockups
  - [x] One **New Scheme (Settings)** screen — [mockups/settings/schemes/new-scheme-screen/](05-ui-ux/mockups/settings/schemes/new-scheme-screen/)
  - [x] One **list/register screen** — Customer List + Account Register mockups across Savings/FD/Daily/Recurring/Loan
- [x] Once these 3 patterns are validated, mockups for remaining screens — **done** (full active-spec coverage via pattern reuse)

### 1.6 Component Inventory & Design System
- [x] Extract a **shared component list** from mockups/specs — captured in [ui-simplification-patterns.md](05-ui-ux/shared/ui-simplification-patterns.md) (`app-entity-autocomplete`, nominee, charges, rate slabs, interest-posting grid, quick-add customer, …) plus entity-autocomplete + quick-add pattern docs
- [x] Document reusable Angular Material targets in [`.cursor/rules/generate-ui-screen.mdc`](../.cursor/rules/generate-ui-screen.mdc) **Reusable Component Catalog** (`app-data-grid`, `app-entity-autocomplete`, `app-nominee-*`, `app-ledger-tab`, `app-kyc-info-tab`, `app-master-select`, …)

> ✅ **§1.6 closed** at starting-catalog level. Extend the catalog when a new repeating pattern appears during Phase 2/3 builds — do not block Phase 1 exit on a perfect inventory.

### 1.7 One Fully-Documented Business Domain (Template)
Pick **Customer & Membership** (UI specs + mockups already ready) as the template domain:
- [ ] `02-business-domains/customer/overview.md` *(folder does not exist yet)*
- [ ] `business-rules.md` (BR-001…)
- [ ] `use-cases.md` (UC-001…)
- [ ] `workflows.md`
- [ ] `acceptance-tests.md` (AT-001…)
- [ ] `changelog.md`

> Use this as the **template** so remaining domains (Accounts, Loans, Accounting) follow identical structure in Phase 3. **This is the primary Phase 1 unblocker remaining.**

### 1.8 Seed API Contracts & Database Design
- [ ] `03-api-contracts/` — draft endpoints only for Customer + Auth/User modules (enough to start Phase 2), one file per endpoint per standard *(folder does not exist yet)*
- [x] `04-database-design/` foundation — [standards](04-database-design/database-design-standards.md), [overview](04-database-design/overview.md), [reports-traceability](04-database-design/reports-traceability.md), `@design-database-schema` skill
- [ ] `04-database-design/` entity docs for `customer`, `user`, `role`, `branch`, `organization` (and other shared masters listed in overview — **not started**)

**Phase 1 exit criteria:** AI_INDEX.md has no `TODO` links for Project Overview/Architecture/AI-Context; Customer domain is fully documented end-to-end (docs → mockup → API contract → DB entity); component inventory exists.

---

## PHASE 2 — Foundation Setup
**Goal:** A working, authenticated, multi-tenant skeleton — no business features yet.

- [ ] **Cloud & repo setup**: AWS account in `ap-south-1` (Mumbai, per DEC-006), **monorepo** per [folder-structure.md](09-ai-context/folder-structure.md) (DEC-007), pnpm workspaces, CI/CD pipeline (GitHub Actions) skeleton
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

**Closed since last plan update:** §1.1, §1.3 (all AI Context), §1.5 (mockups), §1.6 (component catalog), technology-stack + DEC log, User Role matrix (dynamic registry).

**Focus next (unblocks Phase 1 exit → Phase 2):**

1. **§1.7 Customer & Membership business-domain template** — highest leverage. Author `02-business-domains/customer/` (`overview`, `business-rules`, `use-cases`, `workflows`, `acceptance-tests`, `changelog`). UI specs + mockups already exist; this is what Phase 3 will clone for every other domain.
2. **§1.8 in parallel (same domain):** run `@design-database-schema shared` then `customer` / `membership` for entity docs; draft `03-api-contracts/` for Auth/User + Customer endpoints only.
3. **§1.2 remaining architecture docs** (can run alongside §1.7): `domain-driven-design.md` (bounded contexts matching UI modules) + `security-architecture.md` (JWT tenant claim + RBAC levels). Needed before Phase 2 auth skeleton, not before Customer business rules.
4. **Defer:** Deposit Loan Installment Tabs 2–6 capture — not on Customer or Phase 2 critical path.

**Do not start Phase 2 code** until §1.7 + Auth/Customer slice of §1.8 + `security-architecture.md` exist — otherwise the skeleton will invent contracts and entities.
