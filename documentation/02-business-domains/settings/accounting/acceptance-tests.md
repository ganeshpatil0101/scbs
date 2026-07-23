# Acceptance Tests — Settings / Accounting

## Purpose

Given/When/Then tests verifying business rules and use cases for GL Account Setup. Each test references `BR-NNN` and/or `UC-NNN`.

---

### AT-001 — Always creates new Group and Head

**Verifies:** [BR-001](business-rules.md#br-001--gl-setup-creates-new-group-and-head), [UC-001](use-cases.md#uc-001--create-gl-group-and-gl-head)

**Given** existing GL Groups already exist in the tenant
**When** the actor opens GL Account Setup Tab 2
**Then** Account Group is a read-only label from Tab 1
**And** there is no control to select an existing Group

---

### AT-002 — Next does not persist Group or Head

**Verifies:** [BR-002](business-rules.md#br-002--gl-setup-atomic-save-on-create)

**Given** Tab 1 has a valid new Group Name
**When** the actor clicks Next
**Then** no `gl_group` or `gl_head` record is persisted until Complete

---

### AT-003 — Complete persists Group and Head together

**Verifies:** [BR-002](business-rules.md#br-002--gl-setup-atomic-save-on-create), [UC-001](use-cases.md#uc-001--create-gl-group-and-gl-head)

**Given** Tab 1 and Tab 2 are fully valid
**When** the actor clicks Complete
**Then** both a new GL Group and a new GL Head are persisted
**And** the Head is linked to that Group

---

### AT-004 — P&L is default primary classification

**Verifies:** [BR-003](business-rules.md#br-003--primary-group-pnl-or-balance-sheet)

**Given** a new GL Account Setup wizard on Tab 1
**When** the screen loads
**Then** Profit & Loss is selected
**And** Balance Sheet is not selected

---

### AT-005 — Income default under P&L

**Verifies:** [BR-004](business-rules.md#br-004--pnl-income-or-expense-visibility)

**Given** Profit & Loss is selected
**When** the actor views Tab 1
**Then** Income and Expense are visible
**And** Income is selected by default
**And** Receivable and Payable are hidden

---

### AT-006 — Balance Sheet shows Receivable/Payable

**Verifies:** [BR-005](business-rules.md#br-005--balance-sheet-receivable-or-payable-visibility), [WF-002](workflows.md#wf-002--pnl-vs-balance-sheet-classification-switch)

**Given** Tab 1 is open
**When** the actor selects Balance Sheet
**Then** Receivable and Payable are visible
**And** Income and Expense are hidden

---

### AT-007 — Group Type fixed to Other

**Verifies:** [BR-006](business-rules.md#br-006--group-type-fixed-to-other)

**Given** Tab 1 is open
**When** the actor views Group Type
**Then** the value is `इतर`
**And** the control is disabled

---

### AT-008 — Group Name required

**Verifies:** [BR-007](business-rules.md#br-007--group-name-required)

**Given** Tab 1 with primary classification selected
**When** Group Name is blank and the actor clicks Next
**Then** the system blocks with a validation error on Group Name

---

### AT-009 — Group Name unique within tenant

**Verifies:** [BR-008](business-rules.md#br-008--group-name-unique-within-tenant), [UC-001](use-cases.md#uc-001--create-gl-group-and-gl-head) E2

**Given** a GL Group named `ठेवी` already exists
**When** the actor enters Group Name `ठेवी` and completes a valid wizard Save
**Then** the system rejects Complete for duplicate Group Name

---

### AT-010 — Tab 2 shows Group Name from Tab 1

**Verifies:** [BR-009](business-rules.md#br-009--tab-2-account-group-readonly-from-tab-1)

**Given** Tab 1 Group Name is `गुंतवणूक`
**When** the actor advances to Tab 2
**Then** Account Group displays `गुंतवणूक` as read-only

---

### AT-011 — GL Head number is read-only auto value

**Verifies:** [BR-010](business-rules.md#br-010--gl-head-number-auto-generated)

**Given** Tab 2 is open
**When** the actor views GL Head No.
**Then** a system-generated number is shown
**And** the actor cannot edit the number

---

### AT-012 — Account Type fixed to Other

**Verifies:** [BR-011](business-rules.md#br-011--account-type-fixed-to-other)

**Given** Tab 2 is open
**When** the actor views Account Type
**Then** the value is `इतर`
**And** the control is disabled

---

### AT-013 — GL Head Name required

**Verifies:** [BR-012](business-rules.md#br-012--gl-head-name-required)

**Given** Tab 2 is open
**When** GL Head Name is blank and the actor clicks Complete
**Then** the system blocks with a validation error on GL Head Name

---

### AT-014 — GL Head Name unique within tenant

**Verifies:** [BR-013](business-rules.md#br-013--gl-head-name-unique-within-tenant), [UC-001](use-cases.md#uc-001--create-gl-group-and-gl-head) E3

**Given** a GL Head named `सामान्य बचत` already exists
**When** the actor enters the same GL Head Name and clicks Complete
**Then** the system rejects Complete for duplicate GL Head Name

---

### AT-015 — Status default Active

**Verifies:** [BR-014](business-rules.md#br-014--gl-head-status-required)

**Given** a new wizard on Tab 2
**When** the screen loads
**Then** Status default is `चालू`
**And** allowed values include `चालू`, `बंद`, `स्थगित`

---

### AT-016 — Start Date defaults to system date

**Verifies:** [BR-015](business-rules.md#br-015--start-date-required)

**Given** a new wizard on Tab 2
**When** the screen loads
**Then** Start Date is the system/business date
**And** Complete is blocked if Start Date is cleared

---

### AT-017 — Balance Type Other not available

**Verifies:** [BR-016](business-rules.md#br-016--balance-type-credit-or-debit-only)

**Given** Tab 2 Balance Type section is visible
**When** the actor views options
**Then** Credit and Debit are available
**And** Other (`इतर`) is not available

---

### AT-018 — Branch Account requires Organization and Branch

**Verifies:** [BR-017](business-rules.md#br-017--branch-account-requires-organization-and-branch), [UC-001](use-cases.md#uc-001--create-gl-group-and-gl-head) E4

**Given** Account Category is Branch Account
**When** Organization or Branch is empty and the actor clicks Complete
**Then** the system rejects Complete with validation on the missing field(s)

---

### AT-019 — General Account hides Organization and Branch

**Verifies:** [BR-017](business-rules.md#br-017--branch-account-requires-organization-and-branch)

**Given** Account Category is General Account
**When** the actor views Tab 2
**Then** Organization and Branch controls are hidden
**And** Complete does not require them

---

### AT-020 — Advanced Member-like and Contra optional

**Verifies:** [BR-018](business-rules.md#br-018--member-like-and-contra-in-advanced)

**Given** Tab 2 Advanced Settings is collapsed
**When** the actor expands Advanced and sets Contra checked
**Then** Complete succeeds without requiring Short Name or Unicode Name
**And** Contra is persisted on the GL Head

---

### AT-021 — View Only cannot Complete

**Verifies:** [BR-019](business-rules.md#br-019--gl-account-setup-uses-master-permission-levels)

**Given** the actor has View Only on GL Account Setup
**When** the actor opens the screen
**Then** Complete is hidden or disabled
**And** no Group or Head is created

---

### AT-022 — Reset clears without save

**Verifies:** [BR-002](business-rules.md#br-002--gl-setup-atomic-save-on-create), [UC-002](use-cases.md#uc-002--reset-gl-account-setup-without-saving)

**Given** the wizard has unsaved Tab 1 and Tab 2 data
**When** the actor clicks Reset
**Then** wizard fields clear
**And** no Group or Head is persisted

---

### AT-023 — Balance Type required on Save — pending confirmation

**Verifies:** [BR-020](business-rules.md#br-020--balance-type-required-on-save)

**Given** `TODO:` business confirms whether Credit or Debit is mandatory
**When** the actor Completes with neither Balance Type selected
**Then** the system accepts or rejects per the confirmed rule
**And** this test remains blocked until BR-020 is Confirmed

---

### AT-024 — Status operational eligibility — pending confirmation

**Verifies:** [BR-021](business-rules.md#br-021--gl-head-status-operational-eligibility)

**Given** `TODO:` business confirms which Status values are eligible for posting/scheme lookup
**When** an operational or scheme GL Autocomplete loads
**Then** only eligible Status heads appear (or disallowed Status is rejected)
**And** this test remains blocked until BR-021 is Confirmed

---

### AT-025 — GL Head number algorithm — pending confirmation

**Verifies:** [BR-022](business-rules.md#br-022--gl-head-number-generation-algorithm)

**Given** `TODO:` business confirms the number generation algorithm
**When** two successive GL Heads are created
**Then** numbers follow the confirmed sequence/range rules
**And** this test remains blocked until BR-022 is Confirmed

---

## Related Documents

- [overview.md](overview.md)
- [business-rules.md](business-rules.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [../../05-ui-ux/settings/accounting/gl-account-setup-screen.md](../../05-ui-ux/settings/accounting/gl-account-setup-screen.md)
