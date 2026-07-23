# Use Cases — Settings / Accounting

## Purpose

Actor goals for GL Account Setup. Each use case references business rules by ID.

---

### UC-001 — Create GL Group and GL Head

**Actors:** Administrator (User with All Rights on GL Account Setup form)

**Preconditions:**
1. Actor has All Rights on the GL Account Setup form ([BR-019](business-rules.md#br-019--gl-account-setup-uses-master-permission-levels)).
2. If creating a Branch Account head, at least one Organization and Branch exist in master data ([BR-017](business-rules.md#br-017--branch-account-requires-organization-and-branch)).

**Main Flow:**
1. Actor opens **GL Account Setup** (जी.एल. खाते सेटअप).
2. **Tab 1 — Account Group:** Actor selects Profit & Loss or Balance Sheet ([BR-003](business-rules.md#br-003--primary-group-pnl-or-balance-sheet)), chooses Income/Expense or Receivable/Payable as applicable ([BR-004](business-rules.md#br-004--pnl-income-or-expense-visibility), [BR-005](business-rules.md#br-005--balance-sheet-receivable-or-payable-visibility)), leaves Group Type as `इतर` ([BR-006](business-rules.md#br-006--group-type-fixed-to-other)), and enters Group Name ([BR-007](business-rules.md#br-007--group-name-required)).
3. Actor clicks **Next**.
4. **Tab 2 — GL Head:** System shows Account Group read-only from Tab 1 ([BR-009](business-rules.md#br-009--tab-2-account-group-readonly-from-tab-1)) and an auto-generated GL Head No. ([BR-010](business-rules.md#br-010--gl-head-number-auto-generated)). Actor enters GL Head Name ([BR-012](business-rules.md#br-012--gl-head-name-required)), Status (default `चालू`) ([BR-014](business-rules.md#br-014--gl-head-status-required)), Start Date ([BR-015](business-rules.md#br-015--start-date-required)), optional Balance Type ([BR-016](business-rules.md#br-016--balance-type-credit-or-debit-only)), and Account Category.
5. Actor clicks **Complete**. System validates uniqueness ([BR-008](business-rules.md#br-008--group-name-unique-within-tenant), [BR-013](business-rules.md#br-013--gl-head-name-unique-within-tenant)) and persists Group + Head atomically ([BR-001](business-rules.md#br-001--gl-setup-creates-new-group-and-head), [BR-002](business-rules.md#br-002--gl-setup-atomic-save-on-create)).

**Alternative Flow:**
- **A1 — Balance Sheet path:** Actor selects Balance Sheet; Income/Expense hide; Receivable/Payable show ([BR-005](business-rules.md#br-005--balance-sheet-receivable-or-payable-visibility)).
- **A2 — Branch Account:** Actor selects Branch Account; Organization and Branch become required ([BR-017](business-rules.md#br-017--branch-account-requires-organization-and-branch)).
- **A3 — Advanced:** Actor expands Advanced to set Short Name, Unicode Name, Member-like, or Contra ([BR-018](business-rules.md#br-018--member-like-and-contra-in-advanced)).
- **A4 — Back:** Actor returns to Tab 1; Tab 1 values remain until Reset or successful Save.

**Exception Flow:**
- **E1 — Required field missing:** System blocks Next or Complete with field-level validation.
- **E2 — Duplicate Group Name:** System rejects Complete ([BR-008](business-rules.md#br-008--group-name-unique-within-tenant)).
- **E3 — Duplicate GL Head Name:** System rejects Complete ([BR-013](business-rules.md#br-013--gl-head-name-unique-within-tenant)).
- **E4 — Branch fields missing:** When Branch Account is selected without Organization or Branch, system rejects Complete ([BR-017](business-rules.md#br-017--branch-account-requires-organization-and-branch)).
- **E5 — View Only:** Actor can view but cannot Complete ([BR-019](business-rules.md#br-019--gl-account-setup-uses-master-permission-levels)).

**Post Conditions:**
1. A new `gl_group` exists with the entered classification and name.
2. A new `gl_head` exists under that group with auto-generated number and entered attributes.
3. No orphan Group or Head exists from Next/Back alone ([BR-002](business-rules.md#br-002--gl-setup-atomic-save-on-create)).

**Referenced Business Rules:** BR-001 through BR-019 (as applicable); BR-020–BR-022 when resolved

---

### UC-002 — Reset GL Account Setup without saving

**Actors:** Administrator

**Preconditions:**
1. GL Account Setup wizard is open with in-progress data.

**Main Flow:**
1. Actor clicks **Reset** (पूर्ववत).
2. System clears wizard state on both tabs.
3. No GL Group or GL Head is created ([BR-002](business-rules.md#br-002--gl-setup-atomic-save-on-create)).

**Alternative Flow:**
- None.

**Exception Flow:**
- None.

**Post Conditions:**
1. Wizard returns to create defaults (P&L selected, Income default, Status default on Tab 2 when re-entered).

**Referenced Business Rules:** BR-002

---

## Related Documents

- [overview.md](overview.md)
- [business-rules.md](business-rules.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [../../05-ui-ux/settings/accounting/gl-account-setup-screen.md](../../05-ui-ux/settings/accounting/gl-account-setup-screen.md)
