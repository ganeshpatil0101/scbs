# Entity Autocomplete Pattern — Branch / GL / Account Holder / Bank

## Purpose

Define the standard UI field type for selecting Branch, GL Head, Account Holder, Customer, Member, Agent, and **Bank** across all CBS screens. Replaces legacy dual/triple fields (ID textbox + search + select dropdown) with a single **Autocomplete** control.

## Scope

Applies to every screen spec under `documentation/05-ui-ux/` where the user must look up a branch, GL head, account holder, **customer**, **member**, **agent**, or **bank** (from Bank Master) by ID or name.

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
| Customer | ग्राहक निवडा | Select Customer | `ग्राहक क्र.`, `ग्राहकाचे नाव`, `ग्राहक निवडा` (paired ID + name / select) |
| Member | सभासद निवडा | Select Member | `सभासद क्र.`, `सभासद क्रमांक`, `सभासदचे नाव`, `सभासद नाव` (paired ID + name) |
| Agent | एजंट निवडा | Select Agent | `एजंट क्रमांक`, `शोध एजंट नाव`, `एजंट निवडा`, `प्रतिनिधी क्र.` (paired ID + name / select) |
| Sales Agent | विक्री एजंट निवडा | Select Sales Agent | `विक्री एजंट क्रमांक`, `विक्री एजंटचे नाव शोधा` (paired with Sales Agent Branch) |
| Bank | बँक निवडा | Select Bank | `बँक निवडा` dropdown, `बँकेचे नाव` lookup-only select — options from [Bank Management](../bank/bank-management-screen.md) master |

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

### Customer

| ID | Name |
| :---: | :--- |
| 661 | Customer 1 |
| 662 | Customer 2 |
| 663 | Customer 3 |

Display: `661 — Customer 1`, `662 — Customer 2`, `663 — Customer 3`

### Member

| ID | Name |
| :---: | :--- |
| 208 | Member 1 |
| 209 | Member 2 |
| 210 | Member 3 |

Display: `208 — Member 1`, `209 — Member 2`, `210 — Member 3`

Loaded from membership accounts for the selected branch. Use two separate Member Autocomplete fields for From / To on Shares Transfer.

### Agent

| ID | Name |
| :---: | :--- |
| 1 | Agent 1 |
| 2 | Agent 2 |
| 3 | Agent 3 |

Display: `1 — Agent 1`, `2 — Agent 2`, `3 — Agent 3`

Loaded from registered Daily agents for the selected branch. On Agent-to-Agent Transfer, use two separate Agent Autocomplete fields (From / To).

### Bank

Loaded from society **Bank Master** ([bank-management-screen.md](../bank/bank-management-screen.md) — Tab 1 बँक खाते). Display uses bank account ID + bank name (and optionally branch) so clerks can distinguish same-name banks.

| ID | Name | Branch (sample) |
| :---: | :--- | :--- |
| 1 | बँक ऑफ इंडिया | कोतोली |
| 2 | स्टेट बँक ऑफ इंडिया | कोल्हापूर |
| 3 | बँक ऑफ महाराष्ट्र | सातारा |
| 4 | एचडीएफसी बँक | पुणे |

Display: `1 — बँक ऑफ इंडिया`, `2 — स्टेट बँक ऑफ इंडिया`, `3 — बँक ऑफ महाराष्ट्र`, `4 — एचडीएफसी बँक`

Use these samples in instrument/cheque tabs (Deposit Account Transaction, Jama, Nave, Cheque Register filters). Production options come from Bank Master API (`entityType: bank`).

## Spec Authoring Rules

1. **One row per entity** — never document separate ID, search, and select rows for the same lookup.
2. **Required** — set `Required: Yes` if any removed legacy field was required.
3. **Values / Notes** — include sample values from the tables above and the note: `Enter resolves by ID or name; shows display name`.
4. **Renumber** — after merging rows, renumber the `#` column sequentially in that table.
5. **Standalone filters** — a lone `शाखा कोड` on list/register screens with no paired select becomes a single `Autocomplete` (type change only, label may stay `शाखा कोड` / Branch Code).

## New Scheme — GL binding

On [new-scheme-screen.md](../settings/schemes/new-scheme-screen.md), field **जी.एल. निवडा (Select GL)** binds each product scheme to a GL Head from master. Use `entityType: gl`; options from GL master API (not hardcoded). Daily schemes: validate resolved GL Head number ≤ 99.

## Exclusions (do not consolidate)

- Auto-generated read-only `खाते क्र.` on new-account screens
- Auto-generated read-only `जी. एल. हेड क्र.` on [GL Account Setup](../settings/accounting/gl-account-setup-screen.md) Tab 2 (creation flow only)
- Range filters: `खाते क्र. (पासून)` / `(पर्यंत)`, `ग्राहक क्र. (पासून)` / `(पर्यंत)`, `सभासद क्र. (पासून)` / `(पर्यंत)` on list/bulk screens
- `सभासद खाते क्र.`, `बँकेचे बचत खाते क्रमांक`
- Grid column definitions
- Auto-generated read-only `ग्राहक क्र.` on New Customer (not a lookup)

## Implementation Notes (Angular / mockup)

- **Mockup:** `<input type="text" list="…">` with `<datalist>` options; class `.mockup-autocomplete`
- **Angular:** shared `app-entity-autocomplete` with `entityType`: `branch` | `gl` | `account` | `customer` | `member` | `agent` | `bank`; Material `mat-autocomplete`; debounced filter; Enter resolves selection

## Quick Add Customer (optional companion button)

When a Customer Autocomplete may need to register a person not yet in master data, add **+ नवीन ग्राहक जोडा** beside the field. See [quick-add-customer-pattern.md](quick-add-customer-pattern.md).

## Related Documents

- [../../AI_INDEX.md](../../AI_INDEX.md)
- [quick-add-customer-pattern.md](quick-add-customer-pattern.md)
- [../accounting/overview.md](../accounting/overview.md)
- [../bank/bank-management-screen.md](../bank/bank-management-screen.md)
- [../settings/schemes/new-scheme-screen.md](../settings/schemes/new-scheme-screen.md)
