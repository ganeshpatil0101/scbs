# Database Design Standards — CBS SaaS Platform

## Purpose

Canonical database design principles for the cooperative-bank CBS SaaS platform. AI agents and developers must follow these rules when authoring entity documentation under `04-database-design/`.

This document is the single source of truth for naming, types, constraints, multi-tenancy, shared patterns, and report-driven design. The `@design-database-schema` skill references it on every run.

## Scope

- Tenant financial databases (PostgreSQL, one database per cooperative bank — DEC-001).
- Entity documentation only at this phase — no `.sql` DDL files until Phase 2/3 code generation.
- Does **not** define the `control_catalog` schema (platform routing DB) — that is documented separately in architecture.

## Location Convention

Entity docs live in:

```text
documentation/04-database-design/
  database-design-standards.md   ← this file
  overview.md
  reports-traceability.md
  shared/                        ← master entities reused across domains
    <entity>.md
  <domain>/                      ← domain-specific entities
    overview.md
    <entity>.md
    changelog.md
```

**Note:** `generate-document.mdc` shows a nested `02-business-domains/<module>/database/` layout for general module docs. For CBS, database entity files use the top-level `04-database-design/` folder per `Software-Documentation-Standard.md` and `cbs-project-execution-plan.md` §1.8. Cross-link from `02-business-domains/<domain>/overview.md` when that domain is authored.

---

## Multi-Tenancy (DEC-001)

| Rule | Detail |
| :--- | :--- |
| Isolation model | One PostgreSQL **database** per tenant on a shared RDS instance |
| `tenant_id` column | **Do not add** to tenant-DB tables — isolation is at the database boundary |
| Session context | Organization name, branch defaults, and user identity come from JWT/session — not duplicated as tenant columns |
| `control_catalog` | Separate platform DB mapping `tenant_id → db_name/credentials`; out of scope for domain entity docs |

---

## Naming Conventions

| Element | Convention | Example |
| :--- | :--- | :--- |
| Table name | Singular `snake_case` | `loan_account`, `gl_head`, `customer` |
| Primary key column | Always `id` | `bigint generated always as identity` |
| Foreign key column | `<referenced_entity>_id` | `customer_id`, `gl_head_id`, `branch_id` |
| Boolean columns | `is_<flag>` | `is_active`, `is_collateral` |
| Business-visible numbers | Separate column, **not** the PK | `customer_no`, `account_no`, `member_no`, `voucher_no` |
| Timestamps | `created_at`, `updated_at` | `timestamptz`, default `now()` |
| Audit user refs | `created_by`, `updated_by` | FK to `user.id` where applicable |
| Enum/check columns | Match spec value in English snake_case | `status`, `customer_type`, `salutation` |
| Index names | `idx_<table>_<columns>` | `idx_gl_transaction_gl_head_id_txn_date` |

### Surrogate PK vs Business Number

UI specs label auto-generated fields as `Label (read-only)` — e.g. `ग्राहक क्र.` (Customer No.), `खाते क्र.` (Account No.). These are **business sequence numbers**, stored as separate unique-indexed columns. The internal `id` is never exposed in UI or reports.

---

## Data Types

| Use case | PostgreSQL type | Notes |
| :--- | :--- | :--- |
| Money / amounts | `numeric(18,2)` | All rupee amounts: loan amount, balance, debit, credit |
| Rates / percentages | `numeric(7,4)` | Interest rate, penalty rate, depreciation % |
| Dates (business) | `date` | Transaction date, DOB, installment date |
| Timestamps (audit) | `timestamptz` | `created_at`, `updated_at`; default `now()` |
| Short text | `varchar(n)` | Set `n` from spec max length; default `varchar(255)` when unspecified |
| Long text / notes | `text` | Narration, collateral details, special instructions |
| Boolean | `boolean` | Checkbox fields from UI specs |
| Fixed enums | `varchar` + `CHECK` | Closed lists from spec `Values` column |
| Document/file refs | `varchar(500)` | S3 object key or file path for KYC uploads |

**Never use** `float`/`double precision` for money or rates.

---

## Enums vs Lookup Tables

| Spec signal | Database approach |
| :--- | :--- |
| `Values:` lists fixed options (e.g. Salutation, Customer Type, Status) | `varchar` column + `CHECK` constraint listing exact spec values |
| `Loaded dynamically from master` / `not a fixed enum` | FK to existing or new master table |
| `TODO` in spec | `TODO:` marker in entity doc; ask user — do not invent values |

Copy enum values **verbatim** from the spec's English or Marathi `Values` column. Document the CHECK constraint text in the entity file's Constraints section.

---

## Shared Master Entities

Define once under `04-database-design/shared/`. Domain entities reference them via FK — never redefine.

| Entity | Source UI pattern | Key columns (minimum) |
| :--- | :--- | :--- |
| `branch` | [entity-autocomplete-pattern.md](../05-ui-ux/shared/entity-autocomplete-pattern.md) | `id`, `branch_no` (unique), `name`, `code`, `status` |
| `gl_group` | GL Account Setup | `id`, `name`, `category` |
| `gl_head` | GL Account Setup, Autocomplete `entityType: gl` | `id`, `gl_head_no` (unique), `name`, `gl_group_id`, `balance_type`, `category`, `is_member_like`, `is_contra` |
| `organization` | Session read-only header | `id`, `name` — one row per tenant DB in Year 1 |
| `customer` | Customer module | `id`, `customer_no` (unique), `branch_id`, name fields, `customer_type`, `status`, … |
| `member` | Membership module | `id`, `member_no` (unique), `customer_id`, share fields, … |
| `agent` | Daily module | `id`, `agent_no` (unique), `branch_id`, name, … |
| `bank` | Bank Management | `id`, `name`, branch, account details |
| `employee` | Staff System Access | `id`, `employee_no`, `name`, … |
| `user` | Staff System Access | `id`, `username`, `employee_id`, … |
| `role` | User Role | `id`, `name`, permission matrix |
| `scheme` | New Scheme (unified) | `id`, `name`, `scheme_type`, `gl_head_id`, product-specific params |

When a new domain needs a master entity not yet in `shared/`, create the shared entity file first, then reference it from the domain.

---

## Cross-Module Child Patterns

Repeated UI components (see [ui-simplification-patterns.md](../05-ui-ux/shared/ui-simplification-patterns.md)) map to shared child tables under `04-database-design/shared/`:

| Pattern | Shared table | Owner link |
| :--- | :--- | :--- |
| `app-nominee-form` | `nominee` | `owner_type` enum + `owner_id` (polymorphic) |
| Guarantor grid (Loan) | `guarantor` | `loan_account_id` FK (prefer explicit FK over polymorphic when owner is always loan) |
| KYC document cards | `kyc_document` | `owner_type` + `owner_id` |
| Address grid | `address` | `owner_type` + `owner_id` |
| Rate/duration slab grid | `rate_duration_slab` | `scheme_id` FK |
| Charges select | `scheme_charge` | `scheme_id` FK |
| Interest posting grid | `interest_posting_schedule` | `scheme_id` FK |

### Polymorphic owner pattern

When one table serves multiple parent types:

```text
owner_type  varchar  NOT NULL  -- CHECK: customer | member | savings_account | fd_account | ...
owner_id    bigint   NOT NULL
```

**Trade-off:** PostgreSQL cannot enforce FK integrity on polymorphic references. Document this explicitly. Prefer explicit FK (e.g. `loan_account_id`) when the child always belongs to one parent type.

---

## Double-Entry Ledger Pattern

All accounting and product transaction screens post to a shared ledger. This is the foundation for GL Wise, Trial Balance, Balance Sheet, Daybook, P&L, and Purvani reports.

### Core table: `gl_transaction`

| Column | Type | Notes |
| :--- | :--- | :--- |
| `id` | bigint PK | Identity |
| `voucher_no` | varchar | Business voucher number — Daybook, Purvani |
| `txn_date` | date | Business transaction date — all report date filters |
| `gl_head_id` | bigint FK | → `gl_head.id` — GL Wise, Trial Balance grouping |
| `account_id` | bigint FK nullable | → product account (`savings_account`, `loan_account`, etc.) when applicable |
| `branch_id` | bigint FK | → `branch.id` |
| `debit_amount` | numeric(18,2) | Nave side — default 0 |
| `credit_amount` | numeric(18,2) | Jama side — default 0 |
| `cash_amount` | numeric(18,2) nullable | Daybook/Purvani cash column |
| `transfer_amount` | numeric(18,2) nullable | Daybook/Purvani transfer column |
| `narration` | text nullable | Particulars |
| `reference_type` | varchar nullable | Source screen/entity: `jama`, `nave`, `transfer`, `loan_payment`, … |
| `reference_id` | bigint nullable | PK of source transaction record |
| `status` | varchar | `posted`, `pending`, `reversed` — Transaction Passing/Verification |
| `created_at`, `created_by`, … | audit | Standard audit columns |

**Rule:** Every voucher must balance — sum of debits = sum of credits for the same `voucher_no`.

### Product-specific transaction tables

Product screens (Savings/FD/Daily/Recurring/Loan transaction) may have a domain-specific header table (e.g. `loan_transaction`) that creates one or more `gl_transaction` rows. Document both: the product table for screen/API fidelity, and the ledger rows it produces.

### Loan statement ledger

Loan Account Statement report needs per-transaction breakdown: principal, interest, penalty interest, overdue interest, other charges. Model as:

- `loan_transaction` — header per payment/receipt event
- `loan_transaction_component` — child rows: `component_type` (`principal`, `interest`, `penalty_interest`, `overdue_interest`, `other_charge`), `debit_amount`, `credit_amount`

---

## Constraints

| Rule | Detail |
| :--- | :--- |
| NOT NULL | Apply when spec `Required: Yes` |
| FK default | `ON DELETE RESTRICT` — never `CASCADE` on financial history |
| Unique | Business numbers (`customer_no`, `account_no`, `voucher_no` per branch/date scope as confirmed) |
| CHECK | Enum columns — exact values from spec |
| Balance rule | `gl_transaction`: `(debit_amount > 0 AND credit_amount = 0) OR (credit_amount > 0 AND debit_amount = 0) OR both = 0` for adjustment rows — confirm with user if spec is silent |

---

## Indexes

Index every:

- Foreign key column
- Business-visible unique number (`customer_no`, `account_no`, `voucher_no`)
- Report filter columns: `(gl_head_id, txn_date)`, `(txn_date, branch_id)`, `(account_id, txn_date)`
- Status columns used in list/register screens
- Autocomplete search columns: `(branch_no)`, `(gl_head_no)`, name prefix searches as needed

Document indexes in each entity file's Indexes section with the query/report they support.

---

## Audit Columns

Every table includes:

| Column | Type | Notes |
| :--- | :--- | :--- |
| `created_at` | timestamptz | `NOT NULL DEFAULT now()` |
| `created_by` | bigint FK nullable | → `user.id` |
| `updated_at` | timestamptz | `NOT NULL DEFAULT now()` |
| `updated_by` | bigint FK nullable | → `user.id` |

Soft-delete (`deleted_at`) — add only when a spec explicitly requires retaining deleted records in lists. Default: use `status` enum (e.g. `closed`, `cancelled`) instead of hard delete.

---

## Field Classification (from UI Specs)

When walking a `*-screen.md` field table, classify each field:

| Classification | Action |
| :--- | :--- |
| **Persisted column** | Map to entity column with type from standards above |
| **FK lookup** | Map to `<entity>_id` referencing shared or domain master |
| **Child grid row** | Map to child table (one row per grid line) |
| **Computed / derived** | Document in entity Notes as computed — do not persist unless spec says stored (e.g. cached balance) |
| **UI-only / session** | Do not persist — e.g. Organization header from session, tab navigation state |
| **Auto-fill from FK** | Do not duplicate — derive at read time from joined entity (e.g. Customer Age from DOB) |

Traceability: every persisted column must cite source spec file + field `#` in the entity doc's Source section.

---

## Report-Driven Design

Before finalizing a domain schema:

1. Read [reports-traceability.md](reports-traceability.md).
2. Identify reports that consume this domain's data.
3. Confirm required columns and grain exist (or will exist via `gl_transaction` posting).
4. Update `reports-traceability.md` if new report dependencies are discovered.

Reports never invent schema — they aggregate existing ledger and master data.

---

## Entity Documentation Template

Each entity file (`<entity>.md`) must include:

```markdown
# Entity — <table_name>

## Purpose
One paragraph: what this entity stores and which business process owns it.

## Source
- [screen-spec.md](../05-ui-ux/<domain>/<screen>.md) — Tab N, fields #X–#Y
- [mockup](../05-ui-ux/mockups/<domain>/<screen>/) — optional

## Fields

| Column | Type | Nullable | Default | Source | Notes |
| ... one row per column ...

## Constraints
- PK, FK, UNIQUE, CHECK — list each with SQL-style definition

## Relationships
- `<entity>.<column>` → `<other_entity>.id` — cardinality and meaning

## Indexes
| Index | Columns | Supports |
| ... query or report name ...

## Report Usage
- Which reports read this entity (link to reports-traceability.md rows)

## Referenced Business Rules
- BR-NNN (when 02-business-domains exists) or TODO

## Related Documents
- ../shared/<entity>.md
- ../<domain>/overview.md
```

Maximum 700 lines per file — split into `<entity>-part2.md` if exceeded.

---

## Open Decisions (ask user — do not invent)

| Topic | When to ask |
| :--- | :--- |
| Voucher number scope | Per branch? Per day? Global sequence? |
| Account number format | `{branch_no}/{seq}` as shown in Loan Statement spec? |
| Balance caching | Real-time sum from `gl_transaction` vs materialized balance column? |
| Fiscal year boundaries | Required for Balance Sheet / P&L comparative columns |
| Polymorphic vs explicit FK | When child pattern owner is ambiguous in spec |

Use `AskQuestion` (max 1–2 questions at a time). Insert `TODO:` in entity doc for unresolved items.

---

## Related Documents

- [overview.md](overview.md)
- [reports-traceability.md](reports-traceability.md)
- [../01-architecture/architecture-overview.md](../01-architecture/architecture-overview.md) — DEC-001, DEC-002
- [../05-ui-ux/shared/entity-autocomplete-pattern.md](../05-ui-ux/shared/entity-autocomplete-pattern.md)
- [../05-ui-ux/shared/ui-simplification-patterns.md](../05-ui-ux/shared/ui-simplification-patterns.md)
- [../Software-Documentation-Standard.md](../Software-Documentation-Standard.md)
- [../cbs-project-execution-plan.md](../cbs-project-execution-plan.md)
- [../../.cursor/skills/design-database-schema/SKILL.md](../../.cursor/skills/design-database-schema/SKILL.md)
