# Acceptance Tests — Savings

## Purpose

Given/When/Then tests verifying business rules and use cases for the Savings module. Each test references `BR-NNN` and/or `UC-NNN`.

---

### AT-001 — New Savings Account requires an existing customer

**Verifies:** [BR-001](business-rules.md#br-001--customer-must-exist-before-savings-account-can-be-opened), [UC-001](use-cases.md#uc-001--open-a-new-savings-account)

**Given** the actor types a customer number with no matching Customer record into the Tab 1 Autocomplete
**When** the actor presses Enter
**Then** the system shows no match and does not resolve a customer
**And** the actor cannot proceed to open the account for a non-existent customer

---

### AT-002 — Scheme required and limited to Savings type

**Verifies:** [BR-002](business-rules.md#br-002--scheme-required-and-loaded-from-savings-scheme-master)

**Given** Tab 1 has a resolved Customer and Select Scheme left at placeholder
**When** the actor clicks Next or Save
**Then** the system blocks the action with a validation error on Select Scheme
**And** the Select Scheme dropdown only lists schemes where Scheme Type = `बचत`

---

### AT-003 — Member-only scheme enforcement is unresolved (TODO)

**Verifies:** [BR-003](business-rules.md#br-003--member-only-scheme-enforcement-not-verifiable-on-this-screen)

**Given** the selected Scheme has Allow Only Members checked in Settings
**When** the actor selects a Customer who is not a registered Member
**Then** `TODO:` expected system behaviour (block, warn, or no check) is not yet confirmed

---

### AT-004 — Account No. is read-only and system-generated

**Verifies:** [BR-004](business-rules.md#br-004--account-no-auto-generated)

**Given** a new New Savings Account wizard is open on Tab 1
**When** the actor views the Account No. field
**Then** it renders as a read-only Label showing no value until after Save
**And** the actor cannot type into it

---

### AT-005 — Interest Rate auto-fills; override role is unresolved (TODO)

**Verifies:** [BR-005](business-rules.md#br-005--interest-rate-auto-filled-from-scheme-admin-override-role-undefined)

**Given** the actor selects a Scheme with a configured Interest Rate of `4.00`
**When** Tab 1 re-renders
**Then** Interest Rate displays `4.00` as a read-only Label

**Given** an actor attempts to override the auto-filled Interest Rate
**When** the system evaluates the actor's permission
**Then** `TODO:` which permission level or role satisfies "admin role" for the override is not yet confirmed

---

### AT-006 — Current Date defaults to system date

**Verifies:** [BR-006](business-rules.md#br-006--current-date-defaults-to-system-date)

**Given** a new New Savings Account wizard is opened on 2026-07-24
**When** the actor views Tab 1
**Then** Current Date shows `2026-07-24`
**And** the actor may edit it before Save

---

### AT-007 — Minimum Balance is required

**Verifies:** [BR-007](business-rules.md#br-007--minimum-balance-required-at-opening)

**Given** Tab 1 has Minimum Balance left blank
**When** the actor clicks Next or Save
**Then** the system blocks the action with a validation error on Minimum Balance

---

### AT-008 — Account Status defaults to Active with three shared values

**Verifies:** [BR-008](business-rules.md#br-008--account-status-default-and-shared-values-across-deposit-products)

**Given** a new New Savings Account wizard is opened
**When** the actor views the Select Status dropdown on Tab 1
**Then** the default selected value is `चालू` (Active)
**And** the only other selectable values are `बंद` and `स्थगित`

---

### AT-009 — Advanced Settings visibility role is unresolved (TODO)

**Verifies:** [BR-009](business-rules.md#br-009--advanced-settings-visibility-role-undefined)

**Given** an actor without a defined "accounting/admin role" opens New Savings Account
**When** the actor views Tab 1
**Then** the actor can still manually expand प्रगत सेटिंग्ज (Advanced Settings)
**And** `TODO:` whether any actor is blocked from expanding it is not yet confirmed

---

### AT-010 — Debit Limit and Fund Transfer Limit are optional

**Verifies:** [BR-010](business-rules.md#br-010--debit-limit-and-fund-transfer-limit-optional-overrides)

**Given** Advanced Settings is expanded with Debit Limit and Fund Transfer Limit left blank
**When** the actor clicks Save
**Then** the account is created successfully with no validation error on either field

---

### AT-011 — IFSC Code auto-fills Bank Name

**Verifies:** [BR-011](business-rules.md#br-011--ifsc-code-enables-bank-payout-auto-fill)

**Given** the actor enters a valid IFSC Code in Advanced Settings
**When** the field resolves
**Then** the read-only Bank Name Label populates
**And** the actor may optionally enter a Bank Savings Account No. for payout

---

### AT-012 — Nominee tab hidden until Add Nominee checked

**Verifies:** [BR-012](business-rules.md#br-012--nominee-section-conditional-on-add-nominee-checkbox)

**Given** Tab 1 has Add Nominee unchecked
**When** the actor views the tab bar
**Then** Tab 2 (वारसदार) is not shown and is skipped during Next/Back navigation

**Given** the actor checks Add Nominee
**When** the tab bar re-renders
**Then** Tab 2 becomes visible

---

### AT-013 — Joint Holder tab hidden until Add Joint Holder checked

**Verifies:** [BR-013](business-rules.md#br-013--joint-holder-section-conditional-on-add-joint-holder-checkbox)

**Given** Tab 1 has Add Joint Holder unchecked
**When** the actor views the tab bar
**Then** Tab 3 (संयुक्त खाते धारक) is not shown and is skipped during Next/Back navigation

**Given** the actor checks Add Joint Holder
**When** the tab bar re-renders
**Then** Tab 3 becomes visible

---

### AT-014 — Nominee resolves via Autocomplete or quick-add

**Verifies:** [BR-014](business-rules.md#br-014--nominee-lookup-resolves-to-existing-or-quick-added-customer)

**Given** Tab 2 is open and the actor searches for a nominee not found in Customer master
**When** the actor clicks **+ नवीन ग्राहक जोडा**
**Then** the quick-add popup opens with Salutation, Name, Date of Birth, and Mobile Number fields
**And** on Save, the new Customer is created and the Autocomplete displays the resolved `id — name`

---

### AT-015 — Nominee Relation matches canonical Membership list

**Verifies:** [BR-015](business-rules.md#br-015--nominee-relation-reuses-canonical-membership-list)

**Given** a nominee customer is resolved on Tab 2
**When** the actor opens the Relation dropdown
**Then** the options exactly match the canonical Relation list defined on New Membership Tab 3 (`मुलगा`, `पुतण्या`, `मुली`, `मुलगा - पती`, `पति व मुलगा`, `वरील प्रमाणे`, `बायको`, `मैत्रीण`, `केअरटेकर`, `लहान भाऊ`, `स्वतः`, `पत्नी`, `पती`)
**And** no additional Savings-specific Relation values are present

---

### AT-016 — Nominee Percentage optional; Nomination Date and Age read-only

**Verifies:** [BR-016](business-rules.md#br-016--nominee-percentage-optional-nomination-date-and-age-system-derived)

**Given** a nominee customer with Date of Birth 2000-01-01 is resolved on Tab 2
**When** the actor views Nomination Date and Age at Nomination
**Then** both render as read-only Labels, with Age at Nomination computed from the nominee's Date of Birth
**And** leaving Percentage blank does not block Add

---

### AT-017 — Joint Holder Add validates a resolved customer

**Verifies:** [BR-017](business-rules.md#br-017--joint-holder-guardian-and-customer-fields-add-validates-selection)

**Given** Tab 3 has Select Customer left unresolved
**When** the actor clicks **+ जोड (Add)**
**Then** the system blocks the add with a validation error requiring a resolved customer

---

### AT-018 — Account Operation Instructions defaults to Self

**Verifies:** [BR-018](business-rules.md#br-018--account-operation-instructions-required-with-defined-values)

**Given** Tab 3 is opened for the first time
**When** the actor views Account Operation Instructions
**Then** the default selected value is `स्वतः` (Self)
**And** the only other selectable values are `फक्त प्रमुख खातेदार`, `फक्त संयुक्त खातेदार`, `दोन्ही खातेदार आवश्यक`, `दोघांपैकी कोणीही`

---

### AT-019 — Wizard does not persist until final Save

**Verifies:** [BR-019](business-rules.md#br-019--new-savings-account-wizard-atomic-save-on-create), [WF-001](workflows.md#wf-001--new-savings-account-wizard)

**Given** an actor is creating a new Savings account with Add Nominee and Add Joint Holder both checked
**And** Tabs 1–2 have valid data entered
**When** the actor clicks Next (or Back) without clicking Save
**Then** no Account record is persisted

**Given** the actor completes Tab 3 and clicks Save with Tabs 1–2 valid
**When** the save request completes
**Then** the Account, Nominee(s), and Joint Holder(s) are persisted together

---

### AT-020 — View Only hides Save across Savings screens

**Verifies:** [BR-020](business-rules.md#br-020--savings-screens-use-master-permission-levels)

**Given** a User with View Only on New Savings Account
**When** the User opens New Savings Account
**Then** all fields across all tabs are read-only
**And** Save is not visible

---

### AT-021 — Account Register Show works with zero filters

**Verifies:** [BR-021](business-rules.md#br-021--account-register-primary-search-fields-all-optional)

**Given** the actor leaves all eight Primary Search fields blank
**When** the actor clicks Show
**Then** the system does not block the search
**And** the grid displays results per the actor's entitled scope

---

### AT-022 — Loan-linked accounts filter (TODO)

**Verifies:** [BR-022](business-rules.md#br-022--loan-linked-accounts-filter-depends-on-undocumented-loan-domain)

**Given** a Savings account has an associated Loan
**When** the actor checks कर्ज संलग्नीत खाते and clicks Show
**Then** `TODO:` the exact filter/highlight behaviour (show only linked accounts vs. highlight within full result set) is not yet confirmed pending the Loan domain

---

### AT-023 — Account Register Show applies filters

**Verifies:** [BR-023](business-rules.md#br-023--account-register-grid-and-search-follow-interactive-reporting-standard)

**Given** the actor selects Status = `चालू` and Branch = `1 — Branch 1`
**When** the actor clicks Show
**Then** the grid displays only Active Savings accounts in Branch 1
**And** the footer shows total record count with pagination

---

### AT-024 — वगळा removes the account registration row

**Verifies:** [BR-024](business-rules.md#br-024--वगळा-exclude-is-equivalent-to-काढा-remove)

**Given** the actor has selected a Savings account row in the register
**When** the actor clicks वगळा (Exclude)
**Then** the account registration row is removed from the register, the same as काढा on the FD/Daily/Recurring registers
**And** the row is not merely hidden from the current view

---

### AT-025 — Close Account requires zero balance and no other active accounts

**Verifies:** [BR-025](business-rules.md#br-025--close-account-requires-zero-balance-and-no-other-active-bank-relationships), [UC-002](use-cases.md#uc-002--search-view-and-maintain-savings-accounts-via-account-register)

**Given** a selected Savings account has a non-zero balance
**When** the actor clicks खाते बंद करा (Close Account)
**Then** the system blocks the close with a validation error citing the outstanding balance

**Given** a selected Savings account has a zero balance but its customer holds an active Loan account
**When** the actor clicks Close Account
**Then** the system blocks the close with a validation error citing the active Loan relationship

**Given** a selected Savings account has a zero balance and its customer holds no other active Loan/Daily/Recurring/FD account
**When** the actor clicks Close Account
**Then** the account Status becomes `बंद` and Account Close Date is set to the current date

---

### AT-026 — Account Details and Account Statement gaps (TODO)

**Verifies:** [BR-026](business-rules.md#br-026--account-details-and-account-statement-lack-dedicated-specs)

**Given** the actor clicks खाते उतारा (Account Statement) for a selected account
**When** the system attempts to render the statement
**Then** `TODO:` no dedicated report spec exists yet to define its layout or data — behaviour is unconfirmed

---

## Related Documents

- [overview.md](overview.md)
- [business-rules.md](business-rules.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [../../08-testing/](../../08-testing/) — future integration test plan (Phase 4)
