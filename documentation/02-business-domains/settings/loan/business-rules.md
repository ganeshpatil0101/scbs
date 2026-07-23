# Business Rules — Settings / Loan

## Purpose

Numbered business rules for Loan Interest Rate Change. Every rule cites its UI spec source or a Standing Decision.

**Primary source:** [loan-interest-rate-change-screen.md](../../05-ui-ux/settings/loan/loan-interest-rate-change-screen.md).

## Rule Index

| ID | Title | Type | Status |
| :--- | :--- | :--- | :---: |
| [BR-001](#br-001--loan-scheme-required) | Loan Scheme required | Validation | Confirmed |
| [BR-002](#br-002--scheme-list-from-loan-schemes-only) | Scheme list from Loan schemes only | Eligibility | Confirmed |
| [BR-003](#br-003--change-date-required) | Change Date required | Validation | Confirmed |
| [BR-004](#br-004--new-interest-rate-required) | New Interest Rate required | Validation | Confirmed |
| [BR-005](#br-005--new-penalty-rate-optional) | New Penalty Rate optional | Validation | Confirmed |
| [BR-006](#br-006--apply-scope-mutually-exclusive) | Apply scope mutually exclusive | Validation | Confirmed |
| [BR-007](#br-007--scheme-template-always-updated-on-save) | Scheme template always updated on Save | Workflow | Confirmed |
| [BR-008](#br-008--apply-new-rate-to-all-accounts) | Apply new rate to all accounts | Eligibility | Confirmed |
| [BR-009](#br-009--apply-new-rate-to-new-accounts-only) | Apply new rate to new accounts only | Eligibility | Confirmed |
| [BR-010](#br-010--rate-change-appends-history-row) | Rate change appends history row | Workflow | Confirmed |
| [BR-011](#br-011--history-section-collapsed-by-default) | History section collapsed by default | Workflow | Confirmed |
| [BR-012](#br-012--loan-interest-rate-change-uses-master-permission-levels) | Loan Interest Rate Change uses Master permission levels | Cross-cutting | Confirmed |
| [BR-013](#br-013--rate-change-duration-slab-scope) | Rate change duration slab scope | Eligibility | TODO |
| [BR-014](#br-014--export-contents) | Export contents | Workflow | TODO |

---

## Rules

### BR-001 — Loan Scheme required

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [loan-interest-rate-change-screen.md](../../05-ui-ux/settings/loan/loan-interest-rate-change-screen.md) — field #1 |

**Rule:** Scheme (योजना) is required. Placeholder empty/`निवडा` is not a valid saved value.

---

### BR-002 — Scheme list from Loan schemes only

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [loan-interest-rate-change-screen.md](../../05-ui-ux/settings/loan/loan-interest-rate-change-screen.md) — field #1 |

**Rule:** Scheme dropdown options load dynamically from schemes where Scheme Type = `कर्ज` (Loan) created via Settings → New Scheme. Options are not a fixed enum and must not include Savings/Daily/FD/Recurring schemes.

---

### BR-003 — Change Date required

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [loan-interest-rate-change-screen.md](../../05-ui-ux/settings/loan/loan-interest-rate-change-screen.md) — field #2 |

**Rule:** Change Date (बदल दिनांक) is required.

---

### BR-004 — New Interest Rate required

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | Standing Decision 2026-07-23; [loan-interest-rate-change-screen.md](../../05-ui-ux/settings/loan/loan-interest-rate-change-screen.md) — field #5 (added) |

**Rule:** New Interest Rate (नवीन व्याज दर, p.a. %) is required and must be a non-negative numeric percentage. Save is blocked when blank.

---

### BR-005 — New Penalty Rate optional

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | Standing Decision 2026-07-23; [loan-interest-rate-change-screen.md](../../05-ui-ux/settings/loan/loan-interest-rate-change-screen.md) — field #6 (added) |

**Rule:** New Penalty Rate (नवीन दंड व्याज दर, p.a. %) is optional. When provided, it must be a non-negative numeric percentage. When blank, the scheme’s existing penalty rate is left unchanged unless business later defines otherwise.

---

### BR-006 — Apply scope mutually exclusive

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [loan-interest-rate-change-screen.md](../../05-ui-ux/settings/loan/loan-interest-rate-change-screen.md) — fields #3–#4 |

**Rule:** Exactly one apply scope must be selected: **Apply New Rate to All Accounts** (सर्व खात्यांना…) or **Apply New Rate to New Accounts Only** (फक्त नवीन खात्यांना…). Default is Apply to All Accounts.

---

### BR-007 — Scheme template always updated on Save

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | Standing Decision 2026-07-23 |

**Rule:** On successful Save, the selected Loan scheme’s template interest rate is always updated to the New Interest Rate (and penalty rate when provided), regardless of apply-scope radio. Apply-scope controls which **existing accounts** receive the new rate ([BR-008](#br-008--apply-new-rate-to-all-accounts), [BR-009](#br-009--apply-new-rate-to-new-accounts-only)).

---

### BR-008 — Apply new rate to all accounts

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | Standing Decision 2026-07-23; field #3 |

**Rule:** When Apply New Rate to All Accounts is selected, Save updates the scheme template ([BR-007](#br-007--scheme-template-always-updated-on-save)) and applies the new interest rate to **all existing accounts** under that scheme (effective from Change Date for interest calculation going forward) as well as to accounts opened later under the scheme.

---

### BR-009 — Apply new rate to new accounts only

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | Standing Decision 2026-07-23; field #4 |

**Rule:** When Apply New Rate to New Accounts Only is selected, Save updates the scheme template ([BR-007](#br-007--scheme-template-always-updated-on-save)) so **new accounts** opened on/after Change Date use the new rate. Existing accounts retain their previously applied rates.

---

### BR-010 — Rate change appends history row

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [loan-interest-rate-change-screen.md](../../05-ui-ux/settings/loan/loan-interest-rate-change-screen.md) — Past Rate Changes grid |

**Rule:** Each successful Save appends a history row capturing at least: Scheme identity, Change Date, Previous Interest Rate, and Previous Penalty Rate (as shown in the grid). History is retained for audit/display.

---

### BR-011 — History section collapsed by default

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [loan-interest-rate-change-screen.md](../../05-ui-ux/settings/loan/loan-interest-rate-change-screen.md) — Past Rate Changes |

**Rule:** The Past Rate Changes section is collapsed by default and expands on actor request. Collapse/expand does not change persisted data.

---

### BR-012 — Loan Interest Rate Change uses Master permission levels

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | Confirmed |
| Source | [settings/master/business-rules.md](../master/business-rules.md) BR-017 |

**Rule:** Access follows Master permission levels: **All Rights** (Save/Export), **View Only** (read-only; Save hidden), **No Rights** (navigation blocked).

---

### BR-013 — Rate change duration slab scope

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | TODO |
| Source | History grid Duration column |

**Rule:** `TODO:` Confirm whether a rate change applies to all duration slabs on the Loan scheme or requires selecting a specific duration row (history grid shows Duration).

---

### BR-014 — Export contents

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | TODO |
| Source | Export action |

**Rule:** `TODO:` Confirm Export format (e.g. Excel/PDF) and whether it exports the form values, the history grid, or both.

---

## Related Documents

- [overview.md](overview.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [../../05-ui-ux/settings/loan/loan-interest-rate-change-screen.md](../../05-ui-ux/settings/loan/loan-interest-rate-change-screen.md)
- [../schemes/business-rules.md](../schemes/business-rules.md)
