---
name: generate-business-domain
description: >-
  Derive business rules, use cases, workflows, and acceptance tests from
  approved 05-ui-ux screen specs into 02-business-domains/. Follows
  Software-Documentation-Standard.md and generate-document.mdc; asks questions
  for unknowns instead of inventing. Use when the user asks to document a
  business domain, generate BR/UC/AT, or invokes
  "/generate-business-domain <domain>" or "/generate-business-domain <domain>/<sub-area>".
---

# Generate Business Domain (Core Banking Software)

Turns approved `05-ui-ux/` screen specs into modular business-domain documentation under `documentation/02-business-domains/`. Documentation only — no API contracts, DB entities, or code at this phase.

**Canonical standards:** [documentation/Software-Documentation-Standard.md](../../documentation/Software-Documentation-Standard.md), [.cursor/rules/generate-document.mdc](../../.cursor/rules/generate-document.mdc)

## When to Use

- User asks to document, generate, or update business rules, use cases, workflows, or acceptance tests for a module
- User invokes `/generate-business-domain <domain>` (e.g. `settings/master`, `customer`, `membership`)
- Before authoring `03-api-contracts/` or `@design-database-schema` for a domain — business rules must exist first
- After UI specs/mockups are stable for a domain — run after `@optimize-ui-ux` if applicable

## Non-Negotiable Principles

| Principle | Rule |
| :--- | :--- |
| No invention | Every BR/UC/AT traces to a spec field/behavior or an explicit user answer recorded in Standing Decisions or changelog |
| Spec is source of truth | Cite spec file + field `#` on every BR; `TODO` spec fields → `TODO:` in BR/UC, never guessed |
| UI vs business rule | Field Required/format/visibility from spec → validation BR only when it affects data integrity or downstream modules; pure layout → skip |
| Glossary reuse | Use terms from [glossary.md](../../documentation/00-project-overview/glossary.md) verbatim — never redefine |
| Test coverage | Every BR has ≥1 acceptance test (`AT-NNN`); every UC references linked BRs |
| Ask, don't guess | Unknown eligibility, uniqueness, or workflow semantics → `AskQuestion` (max 1–2 per turn) or `TODO:` marker |
| Skip superseded | Use replacement spec linked in Superseded banner — never derive rules from superseded files |
| No code | Do not generate NestJS/Angular/SQL while producing domain docs |

## Standing Decisions (update when user confirms — do not re-litigate)

| Decision | Value | Confirmed |
| :--- | :--- | :---: |
| Domain folder layout | Mirror `05-ui-ux/<domain>/<sub-area>/` under `02-business-domains/` (Settings uses `settings/master/`, `settings/accounting/`, etc.) | 2026-07-23 |
| BR/UC/AT numbering | Scoped per leaf folder — each `business-rules.md` starts at BR-001; do not reuse IDs across folders (deprecate, don't renumber) | 2026-07-23 |
| Phase 1 domain order | Settings sub-areas first (Master → Accounting → Schemes → Membership → Loan), then Customer, then Phase 3 operational domains | 2026-07-23 |
| Permission levels | Exactly three per form: **All Rights**, **View Only**, **No Rights** — documented in `settings/master/business-rules.md`; other domains reference, do not re-derive | 2026-07-23 |
| Permission mutual exclusivity | At most one permission level selected per form row in the role matrix | 2026-07-23 |
| Login name uniqueness | Unique within tenant; reject save on duplicate (exclude self on edit) | 2026-07-23 |
| Password complexity | Min 8 characters; ≥1 letter and ≥1 digit; no Year-1 password history/reuse | 2026-07-23 |
| Super User bypass | Super User = All Rights on all forms; branch rights still enforced | 2026-07-23 |
| Minimum branch rights | ≥1 branch rights row required on create/edit; single-branch tenant auto-assigns that HO/only branch | 2026-07-23 |
| Staff wizard save (create) | Persist only on final Save after all tabs valid; Next/Back do not write partial records | 2026-07-23 |
| Staff Tab 4 Role assignment | Select existing Role (required); optional create-new-Role then assign; no per-user permission rows outside Role | 2026-07-23 |
| Default seed Roles | Clerk / Cashier / Manager with 51-form matrix in `settings/master/default-role-templates.md` | 2026-07-23 |
| Blank password on edit | Blank Password + Confirm Password on edit keeps existing hash; non-blank must match + meet BR-011 | 2026-07-23 |
| Self-lockout permission warning | Soft warning when setting No Rights on Staff Access / User Role for own Role; Save still allowed | 2026-07-23 |
| Unregistered form permission | Missing registry / role_permission → No Rights (fail closed); do not block app startup in Year 1 | 2026-07-23 |
| Employee requires Customer | Staff registration selects existing Customer via Autocomplete (Tab 1 #1) — employee identity comes from Customer record | 2026-07-23 |
| Schemes type-specific fields | Unified `new-scheme-screen.md` is primary; superseded product specs used as field-reference only (Approach B) | 2026-07-23 |
| Scheme name uniqueness | Unique within Scheme Type (tenant-scoped); same name allowed across different types | 2026-07-23 |
| Scheme ↔ GL Head cardinality | Each scheme binds to exactly one GL Head; many schemes may share one GL Head | 2026-07-23 |
| Scheme wizard save (create) | Persist only on final Complete/Save after all visible tabs valid; Next/Back do not write partial records | 2026-07-23 |
| GL setup create flow | Always new GL Group + new GL Head in one wizard; Year 1 has no select-existing Group on this screen | 2026-07-23 |
| GL setup wizard save | Persist Group + Head together only on final Complete; Next/Back do not write partial records | 2026-07-23 |
| GL Group Name uniqueness | Unique within tenant | 2026-07-23 |
| GL Head Name uniqueness | Unique within tenant | 2026-07-23 |
| Branch Account org/branch | When Account Category = Branch Account, Organization and Branch are required | 2026-07-23 |
| Share Series uniqueness | Unique within Member class (Member vs Nominal), tenant-wide | 2026-07-23 |
| Share Rules Save | Persists a grid row (multiple series allowed per class) | 2026-07-23 |
| Dividend Calculate | Preview only — no posting / no payment obligation from Settings screen | 2026-07-23 |
| Loan rate change — new rates | New Interest Rate required; New Penalty Rate optional | 2026-07-23 |
| Loan rate change — template | Scheme template always updated on Save | 2026-07-23 |
| Loan rate change — apply scope | All Accounts updates existing+future; New Accounts Only keeps existing rates | 2026-07-23 |
| FD Maturity Amount derivation | System-computed from scheme interest formula (Interest Type/Compounding, rate, duration, FD amount); scheme grid Maturity Amount is a reference for double-money (दामदुप्पट/कॅश सर्टिफिकेट) schemes only | 2026-07-24 |
| FD wizard save (create) | Persist Account + Nominee(s) + Joint Holder(s) only on final पूर्ण (Complete) after all visible tabs valid; Next/Back do not write partial records | 2026-07-24 |
| FD काढा (Remove) semantics | Deletes the account registration row (not hide) — same as Savings वगळा | 2026-07-24 |

> **Skill maintenance:** When the user confirms a TODO decision, move it from TODO to a confirmed row above and append the decision to the domain `changelog.md`.

---

## Read Order (follow before writing)

1. [documentation/AI_INDEX.md](../../documentation/AI_INDEX.md)
2. [documentation/00-project-overview/glossary.md](../../documentation/00-project-overview/glossary.md)
3. [documentation/00-project-overview/business-goals.md](../../documentation/00-project-overview/business-goals.md)
4. [documentation/00-project-overview/system-boundaries.md](../../documentation/00-project-overview/system-boundaries.md)
5. [documentation/01-architecture/architecture-overview.md](../../documentation/01-architecture/architecture-overview.md) — DEC-001 tenant, auth flow
6. Target domain UI docs:
   - `documentation/05-ui-ux/<domain>/overview.md`
   - `documentation/05-ui-ux/<domain>/ux-optimization.md` (if present)
   - Current (non-superseded) `documentation/05-ui-ux/<domain>/**/*-screen.md`
   - Approved mockups under `documentation/05-ui-ux/mockups/<domain>/` (behaviour confirmation only)
7. `documentation/04-database-design/<domain>/` — if entity docs already exist (align BR with planned constraints)
8. Existing `documentation/02-business-domains/<domain>/` (update mode)
9. [documentation/09-ai-context/naming-conventions.md](../../documentation/09-ai-context/naming-conventions.md)
10. [documentation/09-ai-context/generation-rules.md](../../documentation/09-ai-context/generation-rules.md)
11. This skill's **Standing Decisions** table (above)

**Skip superseded UI specs** — use the replacement linked in the Superseded banner.

---

## Execution Workflow (follow in order)

### Phase 1 — Resolve scope

1. Map user request to a domain folder (see Domain Map below). If ambiguous, ask via `AskQuestion`.
2. Determine mode: **Create** (no domain files) or **Update** (merge, don't duplicate IDs).
3. List all current screen specs from `overview.md`. Note any spec fields marked `TODO`.

### Phase 2 — Inventory & classify

4. For each screen spec, walk every field table row (`#`, Marathi Label, Type, Required, Values/Notes).
5. Classify each item:

   | Classification | Document |
   | :--- | :--- |
   | Required field / allowed values | BR (validation) |
   | Conditional visibility | BR (eligibility) + workflow step |
   | Cross-entity dependency (e.g. Customer must exist) | BR (eligibility) |
   | Default / auto-fill behaviour | BR if persisted; workflow note if UI-only |
   | Wizard tab sequence / save points | `workflows.md` |
   | Actor goal (register, assign, configure) | `use-cases.md` |
   | Pure layout / breadcrumb / collapsible Advanced | Skip |

6. Cross-check [glossary.md](../../documentation/00-project-overview/glossary.md) and [system-boundaries.md](../../documentation/00-project-overview/system-boundaries.md) for scope limits.

### Phase 3 — Draft identifiers

7. Assign sequential `BR-NNN`, `UC-NNN`, `AT-NNN` within the leaf folder.
8. Each BR includes: Description, Source (spec + field #), Type (Validation | Eligibility | Workflow | Cross-cutting), Status (Confirmed | TODO).

### Phase 4 — Resolve unknowns

9. Collect ambiguities not derivable from specs (uniqueness, password policy, Super User semantics, partial-save behaviour).
10. Ask user via `AskQuestion` — **max 1–2 questions per turn**.
11. Insert `TODO:` markers for anything still unresolved.

### Phase 5 — Write documentation

12. Create/update per leaf folder:
    - `overview.md`
    - `business-rules.md`
    - `use-cases.md`
    - `workflows.md`
    - `acceptance-tests.md`
    - `changelog.md`
13. Create/update `documentation/02-business-domains/<domain>/overview.md` (domain index) when first sub-area is authored.
14. Update [documentation/AI_INDEX.md](../../documentation/AI_INDEX.md).
15. Add Related Documents link in source `documentation/05-ui-ux/<domain>/<sub-area>/overview.md`.

### Phase 6 — Downstream alignment

16. Flag `@design-database-schema` and `03-api-contracts/` as next steps — entity constraints must cite `BR-NNN`.
17. Update Standing Decisions table when user confirms open TODOs.

---

## Domain Map

| User says | Business domain path | Primary UI path | Status |
| :--- | :--- | :--- | :--- |
| `settings/master` | `02-business-domains/settings/master/` | `05-ui-ux/settings/master/` | **Template (Phase 1.7)** |
| `settings/accounting` | `02-business-domains/settings/accounting/` | `05-ui-ux/settings/accounting/` | **Done (2026-07-23)** |
| `settings/schemes` | `02-business-domains/settings/schemes/` | `05-ui-ux/settings/schemes/` | **Done (2026-07-23)** |
| `settings/membership` | `02-business-domains/settings/membership/` | `05-ui-ux/settings/membership/` | **Done (2026-07-23)** |
| `settings/loan` | `02-business-domains/settings/loan/` | `05-ui-ux/settings/loan/` | **Done (2026-07-23)** |
| `customer` | `02-business-domains/customer/` | `05-ui-ux/customer/` | Next after Settings |
| `membership` | `02-business-domains/membership/` | `05-ui-ux/membership/` | Phase 3 |
| `savings` | `02-business-domains/savings/` | `05-ui-ux/savings/` | Phase 3 |
| `fixed-deposit`, `fd` | `02-business-domains/fixed-deposit/` | `05-ui-ux/fixed-deposit/` | **Done (2026-07-24)** |
| `daily`, `pigmy` | `02-business-domains/daily/` | `05-ui-ux/daily/` | Phase 3 |
| `recurring` | `02-business-domains/recurring/` | `05-ui-ux/recurring/` | Phase 3 |
| `loan` | `02-business-domains/loan/` | `05-ui-ux/loan/` | Phase 3 |
| `accounting` | `02-business-domains/accounting/` | `05-ui-ux/accounting/` | Phase 3 |

---

## Templates

### Business Rule (`BR-NNN`)

```markdown
### BR-NNN — <short title>

| Property | Value |
| :--- | :--- |
| Type | Validation \| Eligibility \| Workflow \| Cross-cutting |
| Status | Confirmed \| TODO |
| Source | [screen-spec.md](../../05-ui-ux/.../screen.md) — Tab N, field #X |

**Rule:** <explicit statement — no "usually" or "often">

**Notes:** <optional cross-references>
```

### Use Case (`UC-NNN`)

```markdown
### UC-NNN — <title>

**Actors:** <role names from glossary>

**Preconditions:**
1. ...

**Main Flow:**
1. ...

**Alternative Flow:**
- ...

**Exception Flow:**
- ...

**Post Conditions:**
- ...

**Referenced Business Rules:** [BR-NNN](business-rules.md#br-nnn--...)
```

### Workflow

```markdown
### WF-NNN — <name>

| Property | Value |
| :--- | :--- |
| Trigger | <event> |
| Outcome | <state change> |

**Steps:**
1. ...

**Exceptions:**
- ...

**Referenced Rules:** BR-NNN
```

### Acceptance Test (`AT-NNN`)

```markdown
### AT-NNN — <title>

**Verifies:** [BR-NNN](business-rules.md#br-nnn--...) / [UC-NNN](use-cases.md#uc-nnn--...)

**Given** ...
**When** ...
**Then** ...
**And** ...
```

---

## Deliverables Checklist

- [ ] Every spec field classified (BR / UC / workflow / skip)
- [ ] Every BR has Source (spec file + field #)
- [ ] Every BR has ≥1 AT
- [ ] Every UC has all 7 required sections
- [ ] Unresolved items marked `TODO:` — not guessed
- [ ] Standing Decisions updated for newly confirmed rules
- [ ] Domain + sub-area `overview.md` + `changelog.md` updated
- [ ] `02-business-domains/<domain>/overview.md` index updated
- [ ] `AI_INDEX.md` links added
- [ ] `05-ui-ux/<sub-area>/overview.md` Related Documents updated

---

## Pre-Completion Checklist

- [ ] No vague language in BR descriptions ("usually", "often", "sometimes")
- [ ] IDs sequential with no duplicates within the leaf folder
- [ ] Deprecated BRs marked deprecated — IDs never reused
- [ ] Files ≤ 700 lines (split into `-part2.md` if exceeded)
- [ ] All `## Related Documents` links resolve
- [ ] Cross-links to UI specs are bidirectional where applicable
- [ ] Glossary terms used consistently

If any item fails, fix before reporting done.

---

## Open Project Gaps (flag once per session)

- Optional: bank may tweak Clerk/Cashier/Manager cells in default-role-templates.md
- Settings/Master Standing Decisions BR-010–BR-023 confirmed 2026-07-23
- Settings/Schemes Standing Decisions (name uniqueness, GL sharing, atomic save, Approach B) confirmed 2026-07-23; open: BR-033 status→account-open, BR-034 min grid rows, DP formula
- Settings/Accounting Standing Decisions (atomic Group+Head, always new Group, name uniqueness, Branch Account Org+Branch) confirmed 2026-07-23; open: BR-020 Balance Type required?, BR-021 status eligibility, BR-022 number algorithm
- Settings/Membership + Loan Standing Decisions confirmed 2026-07-23 — **Settings Phase 1.7 complete**; next domain: `customer/`
- `03-api-contracts/` not started — UC flows unblock API design next
- `04-database-design/shared/` entity files not started — BR references entity names provisionally
- `01-architecture/security-architecture.md` not yet authored — JWT/RBAC BRs reference UI spec + glossary only

---

## Related Documents

- [Software-Documentation-Standard.md](../../documentation/Software-Documentation-Standard.md)
- [.cursor/rules/generate-document.mdc](../../.cursor/rules/generate-document.mdc)
- [documentation/09-ai-context/generation-rules.md](../../documentation/09-ai-context/generation-rules.md)
- [documentation/09-ai-context/naming-conventions.md](../../documentation/09-ai-context/naming-conventions.md)
- [.cursor/skills/design-database-schema/SKILL.md](../design-database-schema/SKILL.md)
- [cbs-project-execution-plan.md](../../documentation/cbs-project-execution-plan.md)

## Notes for Cursor

- Invoke with `@generate-business-domain` or `/generate-business-domain <domain>/<sub-area>`.
- Start with `settings/master` per execution plan §1.7 (resequenced 2026-07-23) unless user specifies another domain.
- Phase 1–4 can run as review/plan without file writes; Phase 5 writes docs after user confirms plan or says "apply"/"generate".
- When updating existing domain docs, append to `changelog.md` — do not silently overwrite without noting changes.
- After confirming a business decision with the user, update **Standing Decisions** in this file and the domain changelog in the same session.
