# Acceptance Tests — Recurring (Recurring Deposit)

## Purpose

Given/When/Then tests verifying business rules and use cases for the Recurring module. Each test references `BR-NNN` and/or `UC-NNN`.

---

### AT-001 — New Recurring Account requires an existing customer

**Verifies:** [BR-001](business-rules.md#br-001--customer-must-exist-before-recurring-account-can-be-opened), [UC-001](use-cases.md#uc-001--open-a-new-recurring-deposit-account)

**Given** the actor types a customer number with no matching Customer record into the Tab 1 Autocomplete
**When** the actor presses Enter
**Then** the system shows no match and does not resolve a customer
**And** the actor cannot proceed to open the account for a non-existent customer

---

### AT-002 — Scheme required and limited to Recurring type

**Verifies:** [BR-002](business-rules.md#br-002--scheme-required-and-loaded-from-recurring-scheme-master)

**Given** Tab 1 has a resolved Customer and Select Scheme left at placeholder
**When** the actor clicks Next or Save
**Then** the system blocks the action with a validation error on Select Scheme
**And** the Select Scheme dropdown only lists schemes where Scheme Type = `रिकरिंग`

---

### AT-003 — Scheme-derived attributes auto-fill read-only

**Verifies:** [BR-003](business-rules.md#br-003--scheme-derived-attributes-auto-filled-read-only)

**Given** the actor selects a Recurring scheme with Interest Type and Compounding = `वार्षिक`
**When** Tab 1 re-renders
**Then** Scheme/Interest Type and Compounding display as read-only Labels from the scheme
**And** the actor cannot type into either field

---

### AT-004 — Agent and Sales Agent are optional and branch-scoped

**Verifies:** [BR-004](business-rules.md#br-004--agent-and-sales-agent-optional-agent-scoped-to-agent-branch)

**Given** Tab 1 has a resolved Customer and Scheme but no Agent selected
**When** the actor clicks Save with all required fields valid
**Then** the account is created successfully with no validation error on Agent or Sales Agent
**And** when an Agent Branch is set, the Agent Autocomplete only resolves agents scoped to that branch

---

### AT-005 — Account No. is read-only and system-generated

**Verifies:** [BR-005](business-rules.md#br-005--account-no-auto-generated)

**Given** a new New Recurring Account wizard is open on Tab 1
**When** the actor views the Account Number field
**Then** it renders as a read-only Label showing no value until after Save
**And** the actor cannot type into it

---

### AT-006 — Account Type required with the shared FD list

**Verifies:** [BR-006](business-rules.md#br-006--account-type-required-with-defined-values)

**Given** Tab 1 has Account Type left unselected
**When** the actor clicks Next or Save
**Then** the system blocks the action with a validation error on Account Type
**And** the dropdown lists exactly the shared account-type values (`सामान्य खाते`, `ज्येष्ठ नागरिक खाते`, `महिला`, `विधवा`, `अपंग`, `दुसरी संस्था`, `नोकर`, `स्वातंत्र्यसैनिक`, `अति ज्येष्ठ नागरिक`)

---

### AT-007 — Duration selection auto-fills Duration (Months) and Interest Rate

**Verifies:** [BR-007](business-rules.md#br-007--duration-selected-from-scheme-grid-duration-and-rate-auto-filled)

**Given** a scheme with a duration slab `0-60` (Duration 60 months, Rate 12.37) is selected
**When** the actor selects that Duration
**Then** Duration (Months) displays `60` and Interest Rate displays `12.37` as read-only Labels
**And** the actor cannot type into either Label

---

### AT-008 — Interest Rate admin override role is unresolved (TODO)

**Verifies:** [BR-008](business-rules.md#br-008--interest-rate-admin-override-role-undefined)

**Given** the auto-filled Interest Rate is displayed
**When** an actor attempts to override it
**Then** `TODO:` which permission level or role satisfies "admin role" for the override is not yet confirmed

---

### AT-009 — Account Opening Date defaults to system date

**Verifies:** [BR-009](business-rules.md#br-009--account-opening-date-defaults-to-system-date)

**Given** a new New Recurring Account wizard is opened on 2026-07-24
**When** the actor views Tab 1
**Then** Account Opening Date shows `2026-07-24`
**And** the actor may edit it before Save

---

### AT-010 — Maturity Date is calculated read-only

**Verifies:** [BR-010](business-rules.md#br-010--maturity-date-system-calculated)

**Given** an Account Opening Date of 2026-07-24 and a selected Duration of 60 months
**When** Tab 1 re-renders
**Then** Maturity Date displays as a read-only Label of 2031-07-24
**And** the actor cannot type into it

---

### AT-011 — Installment Amount is required

**Verifies:** [BR-011](business-rules.md#br-011--installment-amount-required)

**Given** Tab 1 has Installment Amount left blank
**When** the actor clicks Next or Save
**Then** the system blocks the action with a validation error on Installment Amount

---

### AT-012 — Deposit Type is required; frequency values are TODO

**Verifies:** [BR-012](business-rules.md#br-012--deposit-type-required-frequency-values-todo)

**Given** Tab 1 has Select Deposit Type left at placeholder
**When** the actor clicks Next or Save
**Then** the system blocks the action with a validation error on Select Deposit Type
**And** `TODO:` the full frequency value set beyond the sample `मासिक` is not yet confirmed by the bank

---

### AT-013 — Maturity Amount is system-computed read-only

**Verifies:** [BR-013](business-rules.md#br-013--maturity-amount-system-computed-from-scheme-interest-formula)

**Given** a scheme, Duration, Interest Rate, Installment Amount, and Deposit Type are all set on Tab 1
**When** Tab 1 re-renders
**Then** Maturity Amount displays as a read-only computed Label derived from the scheme interest formula
**And** the actor cannot type into it
**And** `TODO:` the exact day-count/compounding formula is not yet documented

---

### AT-014 — Account Status defaults to Active with three shared values

**Verifies:** [BR-014](business-rules.md#br-014--account-status-default-and-shared-values-across-deposit-products)

**Given** a new New Recurring Account wizard is opened
**When** the actor views the Select Status dropdown on Tab 1
**Then** the default selected value is `चालू` (Active)
**And** the only other selectable values are `बंद` and `स्थगित`

---

### AT-015 — Advanced Settings visibility role is unresolved (TODO)

**Verifies:** [BR-015](business-rules.md#br-015--advanced-settings-visibility-role-undefined)

**Given** an actor without a defined "accounting/admin role" opens New Recurring Account
**When** the actor views Tab 1
**Then** the actor can still manually expand प्रगत सेटिंग्ज (Advanced Settings)
**And** `TODO:` whether any actor is blocked from expanding it is not yet confirmed

---

### AT-016 — IFSC Code auto-fills Bank Name

**Verifies:** [BR-016](business-rules.md#br-016--ifsc-code-enables-bank-payout-auto-fill)

**Given** the actor enters a valid IFSC Code in Advanced Settings
**When** the field resolves
**Then** the read-only Bank Name Label populates
**And** the actor may optionally enter a Bank Savings Account No. for maturity payout

---

### AT-017 — Nominee tab hidden until Add Nominee checked

**Verifies:** [BR-017](business-rules.md#br-017--nominee-section-conditional-on-add-nominee-checkbox)

**Given** Tab 1 has Add Nominee unchecked
**When** the actor views the tab bar
**Then** Tab 2 (वारसदार) is not shown and is skipped during Next/Back navigation

**Given** the actor checks Add Nominee
**When** the tab bar re-renders
**Then** Tab 2 becomes visible

---

### AT-018 — Joint Holder tab hidden until Add Joint Holder checked

**Verifies:** [BR-018](business-rules.md#br-018--joint-holder-section-conditional-on-add-joint-holder-checkbox)

**Given** Tab 1 has Add Joint Holder unchecked
**When** the actor views the tab bar
**Then** Tab 3 (संयुक्त खातेदार) is not shown and is skipped during Next/Back navigation

**Given** the actor checks Add Joint Holder
**When** the tab bar re-renders
**Then** Tab 3 becomes visible

---

### AT-019 — Nominee resolves via Autocomplete or quick-add

**Verifies:** [BR-019](business-rules.md#br-019--nominee-lookup-resolves-to-existing-or-quick-added-customer)

**Given** Tab 2 is open and the actor searches for a nominee not found in Customer master
**When** the actor clicks **+ नवीन ग्राहक जोडा**
**Then** the quick-add popup opens to create a minimal Customer record
**And** on Save, the new Customer is created and the Autocomplete displays the resolved `id — name`
**And** Nominee Details fields become visible only after the nominee is resolved

---

### AT-020 — Nominee Relation matches canonical Membership list

**Verifies:** [BR-020](business-rules.md#br-020--nominee-relation-reuses-canonical-membership-list)

**Given** a nominee customer is resolved on Tab 2
**When** the actor opens the Relation dropdown
**Then** the options exactly match the canonical Relation list defined on New Membership Tab 3
**And** no additional Recurring-specific Relation values are present

---

### AT-021 — Nominee Percentage optional; Nomination Date and Age read-only

**Verifies:** [BR-021](business-rules.md#br-021--nominee-percentage-optional-nomination-date-and-age-system-derived)

**Given** a nominee customer with Date of Birth 2000-01-01 is resolved on Tab 2
**When** the actor views Nomination Date and Age at Nomination
**Then** both render as read-only Labels, with Age at Nomination computed from the nominee's Date of Birth
**And** leaving Percentage blank does not block Add

---

### AT-022 — Joint Holder Add validates a resolved customer

**Verifies:** [BR-022](business-rules.md#br-022--joint-holder-guardian-and-customer-fields-add-validates-selection)

**Given** Tab 3 has Select Customer left unresolved
**When** the actor clicks **+ जोड (Add)**
**Then** the system blocks the add with a validation error requiring a resolved customer

---

### AT-023 — Account Operation Instructions defaults to Self

**Verifies:** [BR-023](business-rules.md#br-023--account-operation-instructions-required-with-defined-values)

**Given** Tab 3 is opened for the first time
**When** the actor views Account Operation Instructions
**Then** the default selected value is `स्वतः` (Self)
**And** the only other selectable values are `फक्त प्रमुख खातेदार`, `फक्त संयुक्त खातेदार`, `दोन्ही खातेदार आवश्यक`, `दोघांपैकी कोणीही`

---

### AT-024 — Wizard does not persist until final Save

**Verifies:** [BR-024](business-rules.md#br-024--new-recurring-account-wizard-atomic-save-on-create), [WF-001](workflows.md#wf-001--new-recurring-account-wizard)

**Given** an actor is creating a new Recurring account with Add Nominee and Add Joint Holder both checked
**And** Tabs 1–2 have valid data entered
**When** the actor clicks Next (or Back) without clicking Save
**Then** no Account record is persisted

**Given** the actor completes Tab 3 and clicks Save with Tabs 1–2 valid
**When** the save request completes
**Then** the Account, Nominee(s), and Joint Holder(s) are persisted together

---

### AT-025 — View Only hides Save across Recurring screens

**Verifies:** [BR-025](business-rules.md#br-025--recurring-screens-use-master-permission-levels)

**Given** a User with View Only on New Recurring Account
**When** the User opens New Recurring Account
**Then** all fields across all tabs are read-only
**And** Save is not visible

---

### AT-026 — Organization header auto-fills from session

**Verifies:** [BR-026](business-rules.md#br-026--organization-auto-fill-header-from-session)

**Given** the actor opens Account Register in a tenant session
**When** the screen renders
**Then** the संस्था (Organization) header shows the session tenant as a read-only Label
**And** it does not appear as an editable filter field

---

### AT-027 — Account Register Show works with zero filters

**Verifies:** [BR-027](business-rules.md#br-027--account-register-primary-search-fields-all-optional)

**Given** the actor leaves all Primary Search fields blank
**When** the actor clicks Show
**Then** the system does not block the search
**And** the grid displays results per the actor's entitled scope

---

### AT-028 — Results grid legend highlighting (TODO on loan-linked)

**Verifies:** [BR-028](business-rules.md#br-028--results-grid-legend-loan-linked-and-matured-highlighting)

**Given** a Recurring account whose Maturity Date has passed
**When** the account appears in the results grid
**Then** the row renders with blue (matured) highlighting

**Given** a Recurring account linked to a loan
**When** the account appears in the results grid
**Then** `TODO:` the pink loan-linked highlight depends on the not-yet-documented Loan domain

---

### AT-029 — काढा removes the account registration row

**Verifies:** [BR-029](business-rules.md#br-029--काढा-remove-deletes-the-account-registration-row)

**Given** the actor has selected a Recurring account row in the register
**When** the actor clicks काढा (Remove)
**Then** the account registration row is deleted, the same as काढा on the FD/Daily registers and वगळा on the Savings register
**And** the row is not merely hidden from the current view
**And** `TODO:` confirmation dialog and transaction-history restriction are not yet confirmed

---

### AT-030 — Account Register applies filters with pagination

**Verifies:** [BR-030](business-rules.md#br-030--account-register-follows-interactive-reporting-standard)

**Given** the actor selects Status = `चालू` and Branch = `1 — Branch 1`
**When** the actor clicks Show
**Then** the grid displays only Active Recurring accounts in Branch 1
**And** the footer shows the एकूण नोंदी record count with pagination controls

---

### AT-031 — Account Details and Account Statement gaps (TODO)

**Verifies:** [BR-031](business-rules.md#br-031--account-details-and-account-statement-lack-dedicated-specs)

**Given** the actor clicks खाते उतारा (Account Statement) for a selected account
**When** the system attempts to render the statement
**Then** `TODO:` no dedicated report spec exists yet to define its layout or data — behaviour is unconfirmed

---

### AT-032 — Interest Multiplier persists nothing

**Verifies:** [BR-032](business-rules.md#br-032--interest-multiplier-is-a-scheme-based-calculator-with-no-persistence)

**Given** the actor completes a calculation on the Interest Multiplier
**When** the actor navigates away from the screen
**Then** no account or record is created
**And** re-opening the screen shows a cleared form

---

### AT-033 — Interest Multiplier conditional field visibility

**Verifies:** [BR-033](business-rules.md#br-033--interest-multiplier-conditional-field-visibility)

**Given** no Scheme is selected on the Interest Multiplier
**When** the actor views the form
**Then** the Simple/Compound radio is hidden

**Given** a scheme resolving to Compound interest is selected
**When** the form re-renders
**Then** the Compounding Frequency radio (मासिक/तिमाही/सहामाही/वार्षिक) becomes visible

**Given** a scheme resolving to Simple interest is selected
**When** the form re-renders
**Then** the Compounding Frequency radio remains hidden

---

### AT-034 — Interest Multiplier computes deposit, interest, and maturity amounts

**Verifies:** [BR-034](business-rules.md#br-034--interest-multiplier-computes-deposit-interest-and-maturity-amounts), [UC-003](use-cases.md#uc-003--preview-recurring-deposit-maturity-via-interest-multiplier)

**Given** a Scheme, Monthly Deposit Amount, Duration, and Interest Rate are entered
**When** the actor clicks गणना करा (Calculate)
**Then** Deposit Amount, Interest Amount, and Maturity Amount display as read-only outputs
**And** the interest-breakdown grid populates with per-period rows
**And** the underlying formula's exact day-count basis is `TODO:` pending DB/API phase

---

## Related Documents

- [overview.md](overview.md)
- [business-rules.md](business-rules.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [../../08-testing/](../../08-testing/) — future integration test plan (Phase 4)
