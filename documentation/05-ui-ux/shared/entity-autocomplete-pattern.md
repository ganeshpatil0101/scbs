# Entity Autocomplete Pattern — Branch / GL / Account Holder

## Purpose

Define the standard UI field type for selecting Branch, GL Head, and Account Holder across all CBS screens. Replaces legacy dual/triple fields (ID textbox + search + select dropdown) with a single **Autocomplete** control.

## Scope

Applies to every screen spec under `documentation/05-ui-ux/` where the user must look up a branch, GL head, or account holder by ID or name.

## Field Type: Autocomplete

| Property | Value |
| :--- | :--- |
| Type (spec column) | `Autocomplete` |
| Input | User types **ID or name** (partial or full) |
| Resolve trigger | **Enter** key |
| After resolve | Input displays `id — name` (e.g. `1 — Branch 1`) |
| Stored value | Both `id` and `name` (internal form/API payload) |
| Suggestions | Optional dropdown while typing; filtered by ID or name prefix |
| Invalid input | On Enter with no match, show validation error; do not submit |

### Interaction flow

1. User focuses the field and types an ID (e.g. `1`) or name fragment (e.g. `Branch`).
2. Optional: suggestion list shows matching records as `id — name`.
3. User presses **Enter**.
4. System resolves the match; field shows full display `id — name`.
5. Dependent read-only fields (balance, etc.) load from the resolved entity.

## Standard Labels (merged from legacy fields)

| Entity | Marathi Label | English Label | Legacy fields removed |
| :--- | :--- | :--- | :--- |
| Branch | शाखा निवडा | Select Branch | `शाखा क्र.`, `शाखा कोड`, `शाखा निवडा` |
| Agent Branch | एजंट शाखा निवडा | Select Agent Branch | `एजंट शाखा क्र.`, `एजंट शाखा निवडा` |
| Sales Agent Branch | विक्री एजंट शाखा निवडा | Select Sales Agent Branch | `विक्री एजंट शाखा क्र.`, `विक्री एजंट शाखा निवडा` |
| GL | जी.एल. निवडा | Select GL | `जि.एल.क्र.`, `जी.एल.हेड.क्र.`, `जी.एल. हेड`, `जी.एल. हेड शोधा`, `जी.एल.निवडा` |
| Account Holder | खातेधारक निवडा | Select Account Holder | `खाते क्र.`, `खातेधारक शोधा`, `खातेदार निवडा`, `खाते धारक निवडा` |

## Reference Sample Values (documentation and mockups only)

Use these in spec `Values / Notes` columns and HTML mockups. Production data comes from master-data APIs.

### Branch

| ID | Name |
| :---: | :--- |
| 1 | Branch 1 |
| 2 | Branch 2 |
| 3 | Branch 3 |

Display: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`

### GL Head

| ID | Name | Typical use |
| :---: | :--- | :--- |
| 38 | Saving | Savings / Pigmy |
| 91 | FD | Fixed Deposit |
| 42 | Loan | Loan products |
| 38 | Pigmy | Daily (Pigmy) |

Display: `38 — Saving`, `91 — FD`, `42 — Loan`, `38 — Pigmy`

Use the product-appropriate sample on each screen (e.g. Pigmy on Daily transaction, FD on FD transaction).

### Account Holder

| ID | Name |
| :---: | :--- |
| 101 | Account Holder 1 |
| 102 | Account Holder 2 |
| 103 | Account Holder 3 |

Display: `101 — Account Holder 1`, `102 — Account Holder 2`, `103 — Account Holder 3`

## Spec Authoring Rules

1. **One row per entity** — never document separate ID, search, and select rows for the same lookup.
2. **Required** — set `Required: Yes` if any removed legacy field was required.
3. **Values / Notes** — include sample values from the tables above and the note: `Enter resolves by ID or name; shows display name`.
4. **Renumber** — after merging rows, renumber the `#` column sequentially in that table.
5. **Standalone filters** — a lone `शाखा कोड` on list/register screens with no paired select becomes a single `Autocomplete` (type change only, label may stay `शाखा कोड` / Branch Code).

## Exclusions (do not consolidate)

- Auto-generated read-only `खाते क्र.` on new-account screens
- Range filters: `खाते क्र. (पासून)` / `(पर्यंत)`
- `सभासद खाते क्र.`, `बँकेचे बचत खाते क्रमांक`
- Grid column definitions
- Scheme setup `जीएल हेड क्र.` on New Scheme screens (creation field, not lookup)
- `ग्राहक क्र.` + `ग्राहक निवडा` pairs (separate pattern; not in scope)

## Implementation Notes (Angular / mockup)

- **Mockup:** `<input type="text" list="…">` with `<datalist>` options; class `.mockup-autocomplete`
- **Angular:** shared `app-entity-autocomplete` with `entityType`: `branch` | `gl` | `account`; Material `mat-autocomplete`; debounced filter; Enter resolves selection

## Related Documents

- [../../AI_INDEX.md](../../AI_INDEX.md)
- [../accounting/overview.md](../accounting/overview.md)
