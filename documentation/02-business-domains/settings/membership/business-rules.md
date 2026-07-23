# Business Rules — Settings / Membership

## Purpose

Numbered business rules for Membership Configuration (Share Rules + Dividend Calculation). Every rule cites its UI spec source or a Standing Decision.

**Primary source:** [membership-configuration-screen.md](../../05-ui-ux/settings/membership/membership-configuration-screen.md).

## Rule Index

| ID | Title | Type | Status |
| :--- | :--- | :--- | :---: |
| [BR-001](#br-001--member-class-filter-mutually-exclusive) | Member class filter mutually exclusive | Validation | Confirmed |
| [BR-002](#br-002--share-rule-required-fields) | Share rule required fields | Validation | Confirmed |
| [BR-003](#br-003--share-series-unique-within-member-class) | Share Series unique within Member class | Validation | Confirmed |
| [BR-004](#br-004--share-rule-save-persists-grid-row) | Share rule Save persists grid row | Workflow | Confirmed |
| [BR-005](#br-005--share-rule-remove-deletes-selected-rows) | Share rule Remove deletes selected rows | Workflow | Confirmed |
| [BR-006](#br-006--share-amount-after-limit-transfer-removed) | Share Amount After Limit Transfer removed | Cross-cutting | Confirmed |
| [BR-007](#br-007--dividend-year-required) | Dividend Year required | Validation | Confirmed |
| [BR-008](#br-008--dividend-debit-account-head-required) | Dividend Debit Account Head required | Validation | Confirmed |
| [BR-009](#br-009--dividend-branch-filter-optional) | Dividend Branch filter optional | Eligibility | Confirmed |
| [BR-010](#br-010--dividend-percentage-optional) | Dividend Percentage optional | Validation | Confirmed |
| [BR-011](#br-011--dividend-calculate-is-preview-only) | Dividend Calculate is preview only | Workflow | Confirmed |
| [BR-012](#br-012--dividend-settings-labels-read-only) | Dividend settings labels read-only | Workflow | Confirmed |
| [BR-013](#br-013--membership-configuration-uses-master-permission-levels) | Membership Configuration uses Master permission levels | Cross-cutting | Confirmed |
| [BR-014](#br-014--dividend-debit-account-head-value-source) | Dividend Debit Account Head value source | Validation | TODO |
| [BR-015](#br-015--share-rule-grid-branch-semantics) | Share rule grid Branch semantics | Workflow | TODO |

---

## Rules

### BR-001 — Member class filter mutually exclusive

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [membership-configuration-screen.md](../../05-ui-ux/settings/membership/membership-configuration-screen.md) — Shared filter #1–#2 |

**Rule:** Exactly one membership class filter applies on both tabs: **Member** (सभासद) or **Nominal Member** (नाममात्र सभासद). Default is Member. Share rules and dividend preview are scoped to the selected class. Nominal Member is the same class as Class B Member per [glossary.md](../../00-project-overview/glossary.md).

---

### BR-002 — Share rule required fields

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [membership-configuration-screen.md](../../05-ui-ux/settings/membership/membership-configuration-screen.md) — Tab 1 #3–#8 |

**Rule:** To save a share rule, all of the following are required and must be non-blank (amounts/dates valid): Face Value (दर्शनी मूल्य), Share Series (भाग मालिका), Max Share Amount per Member (Rs.), Authorized Share Capital (Rs.), Previous Year Authorized Capital (Rs.), Rule Change Date (नियम बदलण्याची तारीख).

---

### BR-003 — Share Series unique within Member class

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | Standing Decision 2026-07-23; Tab 1 #4 |

**Rule:** Share Series must be unique within the selected Member class (Member or Nominal Member) inside the tenant. The same series code may exist for the other class. Reject Save on duplicate within the same class.

---

### BR-004 — Share rule Save persists grid row

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | Standing Decision 2026-07-23; Tab 1 Actions + Rules Grid |

**Rule:** **Complete / Save** (पूर्ण) on Tab 1 persists a share-rule **grid row** for the selected Member class (multiple series allowed). The grid shows Series, Face Value, Limit, Authorized Share Capital, Changed Date, and Branch (among other columns).

---

### BR-005 — Share rule Remove deletes selected rows

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [membership-configuration-screen.md](../../05-ui-ux/settings/membership/membership-configuration-screen.md) — Tab 1 Remove |

**Rule:** **Remove** (काढा) deletes the selected row(s) from the share-rules grid and removes the corresponding persisted share rule(s) for that Member class.

---

### BR-006 — Share Amount After Limit Transfer removed

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | Confirmed |
| Source | [membership-configuration-screen.md](../../05-ui-ux/settings/membership/membership-configuration-screen.md) — Tab 1 Removed note |

**Rule:** The field Share Amount After Limit Transfer must not appear on the unified Membership Configuration screen (no master values defined).

---

### BR-007 — Dividend Year required

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [membership-configuration-screen.md](../../05-ui-ux/settings/membership/membership-configuration-screen.md) — Tab 2 #10 |

**Rule:** Year (वर्ष) is required before Calculate Dividend. Spec values include `2026`, `2027`, `2028`. Placeholder `निवडा` is not valid.

---

### BR-008 — Dividend Debit Account Head required

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [membership-configuration-screen.md](../../05-ui-ux/settings/membership/membership-configuration-screen.md) — Tab 2 #11 |

**Rule:** Account Head Debit (नावे) is required before Calculate Dividend. Default display value: `मा.वर्षाचा शिल्लक नफा` (Last Year's Balance Profit).

**Notes:** Full option list source is [BR-014](#br-014--dividend-debit-account-head-value-source) (TODO).

---

### BR-009 — Dividend Branch filter optional

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [membership-configuration-screen.md](../../05-ui-ux/settings/membership/membership-configuration-screen.md) — Tab 2 #9 |

**Rule:** Select Branch (Autocomplete) is optional. When set, dividend preview is limited to that branch. When unset, preview includes all branches the actor is allowed to see (subject to branch rights).

---

### BR-010 — Dividend Percentage optional

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [membership-configuration-screen.md](../../05-ui-ux/settings/membership/membership-configuration-screen.md) — Tab 2 #12 |

**Rule:** Percentage (शेकडा %) is optional on the dividend filter. When provided, it must be a non-negative numeric percentage used by the calculation preview.

---

### BR-011 — Dividend Calculate is preview only

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | Standing Decision 2026-07-23; Tab 2 Calculate Dividend |

**Rule:** **Calculate Dividend** (लाभांश गणना) computes and displays the results grid (Customer No., Member No., Name, Capital) and footer totals (Total Capital, Total Dividend) for the selected Member class and filters. Year 1: this action does **not** post accounting vouchers and does **not** create operational dividend payment obligations. Posting remains in the operational Dividend Transaction module (later).

---

### BR-012 — Dividend settings labels read-only

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [membership-configuration-screen.md](../../05-ui-ux/settings/membership/membership-configuration-screen.md) — Settings Labels |

**Rule:** Dividend calculation period, pro-rata closed share account rule, and round-up hints are display-only on this screen. Staff must not edit them here.

---

### BR-013 — Membership Configuration uses Master permission levels

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | Confirmed |
| Source | [settings/master/business-rules.md](../master/business-rules.md) BR-017 |

**Rule:** Access to Membership Configuration follows Master permission levels: **All Rights** (Save, Remove, Calculate), **View Only** (read-only; Save/Remove/Calculate hidden), **No Rights** (navigation blocked). Do not redefine permission levels in this sub-area.

---

### BR-014 — Dividend Debit Account Head value source

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | TODO |
| Source | Tab 2 #11 |

**Rule:** `TODO:` Confirm whether Debit Account Head options are a fixed list (starting with Last Year's Balance Profit) or loaded dynamically from GL Heads.

---

### BR-015 — Share rule grid Branch semantics

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | TODO |
| Source | Rules Grid column शाखा |

**Rule:** `TODO:` Confirm how Branch is set on each share-rule row (actor’s current branch, HO only, or explicit selection).

---

## Related Documents

- [overview.md](overview.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [../../05-ui-ux/settings/membership/membership-configuration-screen.md](../../05-ui-ux/settings/membership/membership-configuration-screen.md)
- [../../00-project-overview/glossary.md](../../00-project-overview/glossary.md)
