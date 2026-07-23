# Business Rules — Settings / Accounting

## Purpose

Numbered business rules for the GL Account Setup wizard. Every rule cites its UI spec source. Rules marked **TODO** require business confirmation before implementation.

**Primary source:** [gl-account-setup-screen.md](../../05-ui-ux/settings/accounting/gl-account-setup-screen.md).

## Rule Index

| ID | Title | Type | Status |
| :--- | :--- | :--- | :---: |
| [BR-001](#br-001--gl-setup-creates-new-group-and-head) | GL setup creates new Group and Head | Workflow | Confirmed |
| [BR-002](#br-002--gl-setup-atomic-save-on-create) | GL setup atomic save on create | Workflow | Confirmed |
| [BR-003](#br-003--primary-group-pnl-or-balance-sheet) | Primary group P&L or Balance Sheet | Validation | Confirmed |
| [BR-004](#br-004--pnl-income-or-expense-visibility) | P&L Income or Expense visibility | Eligibility | Confirmed |
| [BR-005](#br-005--balance-sheet-receivable-or-payable-visibility) | Balance Sheet Receivable or Payable visibility | Eligibility | Confirmed |
| [BR-006](#br-006--group-type-fixed-to-other) | Group Type fixed to Other | Validation | Confirmed |
| [BR-007](#br-007--group-name-required) | Group Name required | Validation | Confirmed |
| [BR-008](#br-008--group-name-unique-within-tenant) | Group Name unique within tenant | Validation | Confirmed |
| [BR-009](#br-009--tab-2-account-group-readonly-from-tab-1) | Tab 2 Account Group read-only from Tab 1 | Workflow | Confirmed |
| [BR-010](#br-010--gl-head-number-auto-generated) | GL Head number auto-generated | Workflow | Confirmed |
| [BR-011](#br-011--account-type-fixed-to-other) | Account Type fixed to Other | Validation | Confirmed |
| [BR-012](#br-012--gl-head-name-required) | GL Head Name required | Validation | Confirmed |
| [BR-013](#br-013--gl-head-name-unique-within-tenant) | GL Head Name unique within tenant | Validation | Confirmed |
| [BR-014](#br-014--gl-head-status-required) | GL Head Status required | Validation | Confirmed |
| [BR-015](#br-015--start-date-required) | Start Date required | Validation | Confirmed |
| [BR-016](#br-016--balance-type-credit-or-debit-only) | Balance Type Credit or Debit only | Validation | Confirmed |
| [BR-017](#br-017--branch-account-requires-organization-and-branch) | Branch Account requires Organization and Branch | Eligibility | Confirmed |
| [BR-018](#br-018--member-like-and-contra-in-advanced) | Member-like and Contra in Advanced | Workflow | Confirmed |
| [BR-019](#br-019--gl-account-setup-uses-master-permission-levels) | GL Account Setup uses Master permission levels | Cross-cutting | Confirmed |
| [BR-020](#br-020--balance-type-required-on-save) | Balance Type required on Save | Validation | TODO |
| [BR-021](#br-021--gl-head-status-operational-eligibility) | GL Head Status operational eligibility | Eligibility | TODO |
| [BR-022](#br-022--gl-head-number-generation-algorithm) | GL Head number generation algorithm | Workflow | TODO |

---

## Rules

### BR-001 — GL setup creates new Group and Head

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [gl-account-setup-screen.md](../../05-ui-ux/settings/accounting/gl-account-setup-screen.md) — Purpose; Standing Decision 2026-07-23 |

**Rule:** The GL Account Setup wizard always creates a **new** GL Group (Tab 1) and a **new** GL Head (Tab 2) in one flow. Year 1 does not provide “select existing Group” to attach a new Head on this screen.

---

### BR-002 — GL setup atomic save on create

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | Standing Decision 2026-07-23; [gl-account-setup-screen.md](../../05-ui-ux/settings/accounting/gl-account-setup-screen.md) — Actions |

**Rule:** On create, the GL Group and GL Head persist together only when the actor clicks **Complete** (पूर्ण) after Tab 1 and Tab 2 are valid. **Next** (पुढे) and **Back** (मागे) must not write partial records. **Reset** (पूर्ववत) clears wizard state without persisting. If Save fails, neither Group nor Head is created.

---

### BR-003 — Primary group P&L or Balance Sheet

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [gl-account-setup-screen.md](../../05-ui-ux/settings/accounting/gl-account-setup-screen.md) — Tab 1, fields #1–#2 |

**Rule:** Exactly one primary classification must apply: **Profit & Loss** (नफा तोटा) or **Balance Sheet** (ताळेबंद). They are mutually exclusive. Default at creation is Profit & Loss.

---

### BR-004 — P&L Income or Expense visibility

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [gl-account-setup-screen.md](../../05-ui-ux/settings/accounting/gl-account-setup-screen.md) — Tab 1, fields #3–#4 |

**Rule:** When Profit & Loss is selected, Income (उत्पन्न) and Expense (खर्च) radios are visible; Receivable and Payable are hidden. Default under P&L is Income. Income and Expense are mutually exclusive.

---

### BR-005 — Balance Sheet Receivable or Payable visibility

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [gl-account-setup-screen.md](../../05-ui-ux/settings/accounting/gl-account-setup-screen.md) — Tab 1, fields #5–#6 |

**Rule:** When Balance Sheet is selected, Receivable (येणे) and Payable (देणे) radios are visible; Income and Expense are hidden. Receivable and Payable are mutually exclusive.

---

### BR-006 — Group Type fixed to Other

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [gl-account-setup-screen.md](../../05-ui-ux/settings/accounting/gl-account-setup-screen.md) — Tab 1, field #7 |

**Rule:** Group Type (गट प्रकार निवडा) is required and fixed to `इतर` (Other). The control is disabled; staff must not change it. Persist `इतर` on Save.

---

### BR-007 — Group Name required

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [gl-account-setup-screen.md](../../05-ui-ux/settings/accounting/gl-account-setup-screen.md) — Tab 1, field #8 |

**Rule:** Group Name (गटाचे नाव) is required and must be non-blank after trim.

---

### BR-008 — Group Name unique within tenant

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | Standing Decision 2026-07-23; [gl-account-setup-screen.md](../../05-ui-ux/settings/accounting/gl-account-setup-screen.md) — Tab 1, field #8 |

**Rule:** Group Name must be unique within the tenant. Reject Save on duplicate. On edit (if later supported), uniqueness excludes the group being edited.

---

### BR-009 — Tab 2 Account Group read-only from Tab 1

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [gl-account-setup-screen.md](../../05-ui-ux/settings/accounting/gl-account-setup-screen.md) — Tab 2, field #10 |

**Rule:** On Tab 2, Account Group (खाते गट) is a read-only label showing the Group Name entered on Tab 1. The actor must not pick a different group on Tab 2.

---

### BR-010 — GL Head number auto-generated

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [gl-account-setup-screen.md](../../05-ui-ux/settings/accounting/gl-account-setup-screen.md) — Tab 2, field #12 |

**Rule:** GL Head No. (जी. एल. हेड क्र.) is system-generated and displayed as a read-only label. Staff must not enter or edit the number on this screen.

**Notes:** Generation algorithm is [BR-022](#br-022--gl-head-number-generation-algorithm) (TODO). Downstream Daily schemes require GL Head number ≤ 99 ([settings/schemes BR-005](../schemes/business-rules.md#br-005--daily-scheme-gl-head-number--99)).

---

### BR-011 — Account Type fixed to Other

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [gl-account-setup-screen.md](../../05-ui-ux/settings/accounting/gl-account-setup-screen.md) — Tab 2, field #11 |

**Rule:** Account Type (खाते प्रकार) is required and fixed to `इतर` (Other). The control is disabled; staff must not change it. Persist `इतर` on Save.

---

### BR-012 — GL Head Name required

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [gl-account-setup-screen.md](../../05-ui-ux/settings/accounting/gl-account-setup-screen.md) — Tab 2, field #13 |

**Rule:** GL Head Name (जी. एल. हेडचे नाव) is required and must be non-blank after trim.

---

### BR-013 — GL Head Name unique within tenant

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | Standing Decision 2026-07-23; [gl-account-setup-screen.md](../../05-ui-ux/settings/accounting/gl-account-setup-screen.md) — Tab 2, field #13 |

**Rule:** GL Head Name must be unique within the tenant. Reject Save on duplicate. On edit (if later supported), uniqueness excludes the head being edited.

---

### BR-014 — GL Head Status required

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [gl-account-setup-screen.md](../../05-ui-ux/settings/accounting/gl-account-setup-screen.md) — Tab 2, field #14 |

**Rule:** Status (स्थिती) is required. Allowed values: `चालू`, `बंद`, `स्थगित`. Default at creation is `चालू`.

**Notes:** Operational eligibility by status is [BR-021](#br-021--gl-head-status-operational-eligibility) (TODO).

---

### BR-015 — Start Date required

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [gl-account-setup-screen.md](../../05-ui-ux/settings/accounting/gl-account-setup-screen.md) — Tab 2, field #15 |

**Rule:** Start Date (प्रारंभ दिनांक) is required. Default at creation is the system (business) date. The actor may change it before Save.

---

### BR-016 — Balance Type Credit or Debit only

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [gl-account-setup-screen.md](../../05-ui-ux/settings/accounting/gl-account-setup-screen.md) — Balance Type #16–#17 |

**Rule:** Balance Type options are **Credit** (जमा) and **Debit** (नावे) only. Balance Type `इतर` (Other) must not appear. Credit and Debit are mutually exclusive when selected.

**Notes:** Whether one of Credit/Debit is mandatory on Save is [BR-020](#br-020--balance-type-required-on-save) (TODO). Spec marks both radios Required: No.

---

### BR-017 — Branch Account requires Organization and Branch

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | Standing Decision 2026-07-23; [gl-account-setup-screen.md](../../05-ui-ux/settings/accounting/gl-account-setup-screen.md) — fields #18–#21 |

**Rule:** When Account Category is **Branch Account** (शाखा खाते), Organization (संघटना) and Select Branch (शाखा निवडा Autocomplete) are visible and **required**. When Account Category is **General Account** (सामान्य खाते), Organization and Branch are hidden and not required. General and Branch are mutually exclusive category choices when selected.

---

### BR-018 — Member-like and Contra in Advanced

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [gl-account-setup-screen.md](../../05-ui-ux/settings/accounting/gl-account-setup-screen.md) — Advanced #22–#25 |

**Rule:** Short Name, Unicode Name, Member-like Account (सभासदाप्रमाणे खाते), and Contra (कॉन्ट्रा) live under Advanced Settings (collapsed by default). They are optional. Member-like and Contra, when set, are persisted with the GL Head.

**Notes:** Glossary: Member-like Account, Contra.

---

### BR-019 — GL Account Setup uses Master permission levels

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | Confirmed |
| Source | [settings/master/business-rules.md](../master/business-rules.md) BR-017 |

**Rule:** Access to GL Account Setup follows Master permission levels: **All Rights** (full edit/save), **View Only** (read-only; Complete hidden), **No Rights** (navigation blocked). Do not redefine permission levels in this sub-area.

---

### BR-020 — Balance Type required on Save

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | TODO |
| Source | [gl-account-setup-screen.md](../../05-ui-ux/settings/accounting/gl-account-setup-screen.md) — Balance Type #16–#17 |

**Rule:** `TODO:` Confirm whether Save requires exactly one of Credit or Debit to be selected (spec lists Required: No).

---

### BR-021 — GL Head Status operational eligibility

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | TODO |
| Source | [gl-account-setup-screen.md](../../05-ui-ux/settings/accounting/gl-account-setup-screen.md) — field #14 |

**Rule:** `TODO:` Confirm which Status values (`चालू`, `बंद`, `स्थगित`) allow the GL Head to appear in operational posting lookups and in scheme GL Autocomplete.

---

### BR-022 — GL Head number generation algorithm

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | TODO |
| Source | [gl-account-setup-screen.md](../../05-ui-ux/settings/accounting/gl-account-setup-screen.md) — field #12 |

**Rule:** `TODO:` Confirm how GL Head numbers are assigned (global sequence, per-group sequence, reserved ranges for Daily ≤ 99, gap reuse).

---

## Related Documents

- [overview.md](overview.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [../../05-ui-ux/settings/accounting/gl-account-setup-screen.md](../../05-ui-ux/settings/accounting/gl-account-setup-screen.md)
- [../master/business-rules.md](../master/business-rules.md)
- [../schemes/business-rules.md](../schemes/business-rules.md)
- [../../00-project-overview/glossary.md](../../00-project-overview/glossary.md)
