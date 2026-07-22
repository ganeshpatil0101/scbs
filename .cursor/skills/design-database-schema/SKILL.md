---
name: design-database-schema
description: >-
  Design and document CBS database entities from 05-ui-ux screen specs and mockups
  into 04-database-design/. Follows database-design-standards.md, reuses shared
  master entities, cross-checks report requirements, and asks questions for
  unknowns instead of inventing. Use when the user asks to design database schema,
  generate db entities, create ER diagram documentation, or invokes
  "/design-database-schema <module>".
---

# Design Database Schema (Core Banking Software)

Turns approved `05-ui-ux/` screen specs and mockups into modular entity documentation under `documentation/04-database-design/`. Documentation only — no SQL DDL at this phase.

**Canonical standards:** [documentation/04-database-design/database-design-standards.md](../../documentation/04-database-design/database-design-standards.md)

## When to Use

- User asks to design, generate, or update database schema for a module/domain
- User invokes `/design-database-schema <module>` (e.g. `customer`, `loan`, `shared`, `accounting`)
- Before authoring `03-api-contracts/` for a domain (execution plan §1.8, §3)
- After UI specs/mockups are stable for a domain — run after `@optimize-ui-ux` if applicable

## Non-Negotiable Principles

| Principle | Rule |
| :--- | :--- |
| No invention | Never invent business rules, enum values, or entities not traceable to a spec, glossary term, or explicit user answer |
| Spec is source of truth | Every persisted column cites a screen spec field `#` or report column |
| Reuse shared entities | Check `04-database-design/shared/` before creating any master entity |
| No tenant_id | DEC-001: database-per-tenant — no `tenant_id` column in tenant-DB tables |
| Docs only | Entity markdown files — no `.sql` until Phase 2/3 code generation |
| Ask, don't guess | Unknown voucher scope, account number format, balance caching → `AskQuestion` (max 1–2 at a time) or `TODO:` marker |
| Report-driven | Cross-check [reports-traceability.md](../../documentation/04-database-design/reports-traceability.md) before marking domain done |

## Standing Decisions (do not re-litigate)

| Decision | Value |
| :--- | :--- |
| Primary keys | `bigint generated always as identity`; column always named `id` |
| Business numbers | Separate unique columns: `customer_no`, `account_no`, `voucher_no`, etc. |
| Table/column naming | Singular `snake_case` |
| Doc location | `documentation/04-database-design/<domain>/` + `shared/` |
| Money / rates | `numeric(18,2)` / `numeric(7,4)` |
| Ledger | All transactions post to shared `gl_transaction` |

---

## Read Order (follow before writing)

1. [documentation/AI_INDEX.md](../../documentation/AI_INDEX.md)
2. [documentation/00-project-overview/glossary.md](../../documentation/00-project-overview/glossary.md)
3. [documentation/00-project-overview/business-goals.md](../../documentation/00-project-overview/business-goals.md) — BG-001 reporting accuracy
4. [documentation/00-project-overview/system-boundaries.md](../../documentation/00-project-overview/system-boundaries.md)
5. [documentation/01-architecture/architecture-overview.md](../../documentation/01-architecture/architecture-overview.md) — DEC-001 multi-tenancy
6. [documentation/04-database-design/database-design-standards.md](../../documentation/04-database-design/database-design-standards.md)
7. [documentation/04-database-design/overview.md](../../documentation/04-database-design/overview.md) — existing entity status
8. All existing `documentation/04-database-design/shared/*.md` and `documentation/04-database-design/<domain>/*.md` (update mode)
9. Target domain UI docs:
   - `documentation/05-ui-ux/<domain>/overview.md`
   - `documentation/05-ui-ux/<domain>/ux-optimization.md` (if present)
   - Current (non-superseded) `documentation/05-ui-ux/<domain>/*-screen.md` specs
   - Approved mockups under `documentation/05-ui-ux/mockups/<domain>/` (layout confirmation only)
10. [documentation/05-ui-ux/shared/entity-autocomplete-pattern.md](../../documentation/05-ui-ux/shared/entity-autocomplete-pattern.md)
11. [documentation/05-ui-ux/shared/ui-simplification-patterns.md](../../documentation/05-ui-ux/shared/ui-simplification-patterns.md)
12. [documentation/05-ui-ux/reports/overview.md](../../documentation/05-ui-ux/reports/overview.md) + relevant report specs
13. `documentation/02-business-domains/<domain>/business-rules.md` — if exists
14. [documentation/09-ai-context/naming-conventions.md](../../documentation/09-ai-context/naming-conventions.md)
15. [documentation/09-ai-context/coding-standards.md](../../documentation/09-ai-context/coding-standards.md) — NestJS/TypeScript conventions when entity docs reference code patterns
16. [documentation/09-ai-context/generation-rules.md](../../documentation/09-ai-context/generation-rules.md)

**Skip superseded UI specs** — use the replacement linked in the Superseded banner.

---

## Execution Workflow (follow in order)

### Phase 1 — Resolve scope

1. Map user request to a domain folder (see Domain Map below). If ambiguous, ask via `AskQuestion`.
2. Determine mode: **Create** (no existing entity files) or **Update** (entity files exist — merge, don't duplicate).
3. List all current screen specs for the domain from `overview.md`. Note any spec fields marked `TODO`.

### Phase 2 — Inventory & classify fields

4. For each screen spec, walk every field table row (`#`, Marathi Label, Type, Required, Values/Notes).
5. Classify each field per [database-design-standards.md § Field Classification](../../documentation/04-database-design/database-design-standards.md):

   | Classification | Action |
   | :--- | :--- |
   | Persisted column | Add to entity with type from standards |
   | FK lookup (Autocomplete) | Map to `<entity>_id` → shared master |
   | Child grid row | Child table (nominee, guarantor, installment, etc.) |
   | Computed / derived | Document as computed — omit column unless spec stores it |
   | UI-only / session | Skip — e.g. Organization header, tab state |
   | Auto-fill from FK | Skip — derive at read time from join |

6. Map Autocomplete fields using [entity-autocomplete-pattern.md](../../documentation/05-ui-ux/shared/entity-autocomplete-pattern.md):

   | entityType | FK target |
   | :--- | :--- |
   | branch | `branch_id` |
   | gl | `gl_head_id` |
   | account | product account FK (context-specific) |
   | customer | `customer_id` |
   | member | `member_id` |
   | agent | `agent_id` |
   | bank | `bank_id` |

7. Map shared UI components to shared child tables (nominee, address, kyc_document, rate_duration_slab, scheme_charge, interest_posting_schedule).

### Phase 3 — Apply standards

8. Assign PostgreSQL types, NOT NULL, defaults, CHECK constraints (enum values copied verbatim from spec).
9. Define FK relationships — default `ON DELETE RESTRICT`.
10. Define indexes — every FK + business number + report filter columns.
11. Add standard audit columns (`created_at`, `created_by`, `updated_at`, `updated_by`) to every table.
12. For transaction screens: document how rows post to shared `gl_transaction` (voucher, debit/credit, cash/transfer split).

### Phase 4 — Report cross-check

13. Read [reports-traceability.md](../../documentation/04-database-design/reports-traceability.md).
14. For each report consuming this domain, confirm required columns/grain exist in planned entities.
15. Update `reports-traceability.md` if new dependencies discovered.

### Phase 5 — Resolve unknowns

16. Collect all ambiguities (TODO spec fields, voucher scope, account number format, fiscal year, balance caching).
17. Ask user via `AskQuestion` — **max 1–2 questions per turn**.
18. Insert `TODO:` markers in entity docs for anything still unresolved after asking.

### Phase 6 — Write documentation

19. Create/update one file per entity: `documentation/04-database-design/<domain>/<entity>.md`
20. Create/update `documentation/04-database-design/<domain>/overview.md` — owned entities list
21. Create/update `documentation/04-database-design/<domain>/changelog.md`
22. Update [documentation/04-database-design/overview.md](../../documentation/04-database-design/overview.md) — status column
23. Update [documentation/AI_INDEX.md](../../documentation/AI_INDEX.md) — entity links
24. Add Related Documents link in source `documentation/05-ui-ux/<domain>/overview.md`

---

## Domain Map

| User says | Domain folder | Primary UI path |
| :--- | :--- | :--- |
| `shared`, `foundation`, `master`, `settings` | `shared/` | `05-ui-ux/settings/`, auth screens |
| `customer` | `customer/` (+ shared customer entity) | `05-ui-ux/customer/` |
| `membership` | `membership/` | `05-ui-ux/membership/` |
| `savings` | `savings/` | `05-ui-ux/savings/` |
| `fixed-deposit`, `fd` | `fixed-deposit/` | `05-ui-ux/fixed-deposit/` |
| `daily`, `pigmy` | `daily/` | `05-ui-ux/daily/` |
| `recurring` | `recurring/` | `05-ui-ux/recurring/` |
| `loan` | `loan/` | `05-ui-ux/loan/` |
| `accounting` | `accounting/` (+ shared gl_transaction) | `05-ui-ux/accounting/` |
| `bank` | `bank/` | `05-ui-ux/bank/` |
| `investment` | `investment/` | `05-ui-ux/investment/` |

**Deposit transactions:** Unified [deposit-account-transaction-screen.md](../../documentation/05-ui-ux/accounting/deposit-account-transaction-screen.md) spans Savings/FD/Daily/Recurring — design one shared transaction pattern, product-specific account FK.

---

## Entity File Template

Use for every `<entity>.md`:

```markdown
# Entity — <table_name>

## Purpose
[One paragraph]

## Source
- [screen-spec.md](../../05-ui-ux/<domain>/<screen>.md) — Tab N, fields #X–#Y

## Fields

| Column | Type | Nullable | Default | Source | Notes |
| :--- | :--- | :---: | :--- | :--- | :--- |
| id | bigint | No | generated always as identity | — | PK |
| ... | ... | ... | ... | spec field #N | ... |

## Constraints
- PRIMARY KEY (id)
- FOREIGN KEY (customer_id) REFERENCES customer(id) ON DELETE RESTRICT
- CHECK (status IN ('active', 'closed', ...)) — values from spec

## Relationships
- customer_id → customer.id (many-to-one)

## Indexes

| Index | Columns | Supports |
| :--- | :--- | :--- |
| idx_<table>_customer_id | customer_id | Customer lookup, list screens |

## Report Usage
- [Trial Balance](../../04-database-design/reports-traceability.md#trial-balance-तेरीज-पत्रक) — via gl_transaction

## Referenced Business Rules
- TODO: BR-NNN when 02-business-domains exists

## Related Documents
- ../shared/<entity>.md
- overview.md
```

Full template and type rules: [database-design-standards.md § Entity Documentation Template](../../documentation/04-database-design/database-design-standards.md).

---

## Enum Handling Examples

**From spec (fixed list) — use CHECK:**

```text
Customer Type: Individual, Proprietorship Firm, Self Help Group, Other Institution
→ CHECK (customer_type IN ('individual', 'proprietorship_firm', 'self_help_group', 'other_institution'))
```

**From spec (dynamic master) — use FK:**

```text
Select Scheme: Loaded dynamically from Loan schemes
→ scheme_id bigint FK → scheme(id)
```

**From spec (TODO) — ask user:**

```text
Scroll dropdown: TODO
→ TODO: scroll lifecycle not documented — ask user before adding scroll_id FK
```

---

## Deliverables Checklist

- [ ] Every spec field classified (persisted / FK / child / computed / UI-only)
- [ ] Every persisted column has Source (spec file + field #)
- [ ] Shared entities reused — no duplicate master definitions
- [ ] Enum values copied verbatim — no invented dropdown values
- [ ] `gl_transaction` posting documented for transaction entities
- [ ] Indexes documented with query/report they support
- [ ] `reports-traceability.md` checked and updated if needed
- [ ] Open questions asked via `AskQuestion` — not guessed
- [ ] `TODO:` markers for unresolved items
- [ ] Domain `overview.md` + `changelog.md` updated
- [ ] `04-database-design/overview.md` status updated
- [ ] `AI_INDEX.md` links added
- [ ] `05-ui-ux/<domain>/overview.md` Related Documents updated

---

## Pre-Completion Checklist

- [ ] No `tenant_id` columns in tenant-DB entity docs
- [ ] No `float`/`double` for money or rates
- [ ] Business numbers (`customer_no`, `account_no`) separate from `id`
- [ ] FK default ON DELETE RESTRICT on financial tables
- [ ] Audit columns on every table
- [ ] Entity files ≤ 700 lines (split if exceeded)
- [ ] All `## Related Documents` links resolve
- [ ] Cross-links to UI specs and reports are bidirectional where applicable

If any item fails, fix before reporting done.

---

## Open Project Gaps (flag once per session)

- `02-business-domains/` not started — BR-NNN references will be TODO
- `03-api-contracts/` not started — entity docs unblock API design next
- Fiscal year configuration undefined — blocks comparative Balance Sheet / P&L precision
- Several UI specs still have `TODO` tabs/fields — entity docs mark matching TODOs

---

## Related Documents

- [database-design-standards.md](../../documentation/04-database-design/database-design-standards.md)
- [overview.md](../../documentation/04-database-design/overview.md)
- [reports-traceability.md](../../documentation/04-database-design/reports-traceability.md)
- [entity-autocomplete-pattern.md](../../documentation/05-ui-ux/shared/entity-autocomplete-pattern.md)
- [ui-simplification-patterns.md](../../documentation/05-ui-ux/shared/ui-simplification-patterns.md)
- [.cursor/rules/design-database-schema.mdc](../../.cursor/rules/design-database-schema.mdc)
- [.cursor/rules/generate-document.mdc](../../.cursor/rules/generate-document.mdc)
- [cbs-project-execution-plan.md](../../documentation/cbs-project-execution-plan.md)
- [documentation/09-ai-context/naming-conventions.md](../../documentation/09-ai-context/naming-conventions.md)
- [documentation/09-ai-context/generation-rules.md](../../documentation/09-ai-context/generation-rules.md)

## Notes for Cursor

- Invoke with `@design-database-schema` or `/design-database-schema <domain>`.
- Start with `shared` + `customer` per execution plan §1.8 unless user specifies another domain.
- Phase 1–5 can run as review/plan without file writes; Phase 6 writes entity docs after user confirms plan or says "apply"/"generate".
- When updating existing entities, append to `changelog.md` — do not silently overwrite without noting changes.
- Prefer canvas for presenting entity relationship review; markdown entity files are the source of truth.
