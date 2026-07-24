# Acceptance Tests — Fixed Deposit

## Purpose

Given/When/Then tests verifying business rules and use cases for the Fixed Deposit module. Each test references `BR-NNN` and/or `UC-NNN`.

---

### AT-001 — New FD Account requires an existing customer

**Verifies:** [BR-001](business-rules.md#br-001--customer-must-exist-before-fd-account-can-be-opened), [UC-001](use-cases.md#uc-001--open-a-new-fd-account)

**Given** the actor types a customer number with no matching Customer record into the Tab 1 Autocomplete
**When** the actor presses Enter
**Then** the system shows no match and does not resolve a customer
**And** the actor cannot proceed to open the account for a non-existent customer

---

### AT-002 — Scheme required and limited to FD type

**Verifies:** [BR-002](business-rules.md#br-002--scheme-required-and-loaded-from-fd-scheme-master)

**Given** Tab 1 has a resolved Customer and Select Scheme left at placeholder
**When** the actor clicks Next or Complete
**Then** the system blocks the action with a validation error on Select Scheme
**And** the Select Scheme dropdown only lists schemes where Scheme Type = `मुदत ठेव`

---

### AT-003 — Scheme attributes auto-fill read-only

**Verifies:** [BR-003](business-rules.md#br-003--scheme-derived-attributes-auto-filled-read-only)

**Given** the actor selects an FD scheme configured as क्लोज एंडेड with साधे व्याज
**When** Tab 1 re-renders
**Then** Closed/Open Ended, Interest Type, and Compounding display those scheme values as read-only Labels
**And** the actor cannot edit them on this screen

---

### AT-004 — Agent and Sales Agent optional; Agent scoped to branch

**Verifies:** [BR-004](business-rules.md#br-004--agent-and-sales-agent-optional-agent-scoped-to-agent-branch)

**Given** Tab 1 has no Agent Branch selected
**When** the actor opens the Select Agent Autocomplete
**Then** the lookup is unscoped or empty until an Agent Branch is chosen
**And** leaving Agent and Sales Agent blank does not block Complete

---

### AT-005 — Account No. is read-only and system-generated

**Verifies:** [BR-005](business-rules.md#br-005--account-no-auto-generated)

**Given** a new New FD Account wizard is open on Tab 1
**When** the actor views the Account No. field
**Then** it renders as a read-only Label showing no value until after Complete
**And** the actor cannot type into it

---

### AT-006 — Account Type required with defined values

**Verifies:** [BR-006](business-rules.md#br-006--account-type-required-with-defined-values)

**Given** Tab 1 has Account Type left unselected
**When** the actor clicks Next or Complete
**Then** the system blocks the action with a validation error on Account Type
**And** the selectable values match the FD account-type list (`सामान्य खाते`, `ज्येष्ठ नागरिक खाते`, `महिला`, `विधवा`, `अपंग`, `दुसरी संस्था`, `नोकर`, `स्वातंत्र्यसैनिक`, `अति ज्येष्ठ नागरिक`)

---

### AT-007 — Interest Rate Slab required and drives Duration

**Verifies:** [BR-007](business-rules.md#br-007--interest-rate-slab-required-and-drives-duration)

**Given** a scheme is selected and Interest Rate Slab is left at `निवडा`
**When** the actor clicks Next or Complete
**Then** the system blocks with a validation error on Interest Rate Slab

**Given** the actor selects a valid slab
**When** Tab 1 re-renders
**Then** Duration (Months), Duration (Days), and Interest Rate auto-fill as read-only Labels from that slab

---

### AT-008 — Current Date defaults to system date

**Verifies:** [BR-008](business-rules.md#br-008--current-date-defaults-to-system-date)

**Given** a new New FD Account wizard is opened on 2026-07-24
**When** the actor views Tab 1
**Then** Current Date shows `2026-07-24`
**And** the actor may edit it before Complete

---

### AT-009 — FD Amount is required

**Verifies:** [BR-009](business-rules.md#br-009--fd-amount-required)

**Given** Tab 1 has FD Amount left blank
**When** the actor clicks Next or Complete
**Then** the system blocks the action with a validation error on FD Amount

---

### AT-010 — Interest Rate auto-fills; override role unresolved (TODO)

**Verifies:** [BR-010](business-rules.md#br-010--interest-rate-auto-filled-from-slab-admin-override-role-undefined)

**Given** the actor selects a slab with Interest Rate `7.50`
**When** Tab 1 re-renders
**Then** Interest Rate displays `7.50` as a read-only Label

**Given** an actor attempts to override the auto-filled Interest Rate
**When** the system evaluates the actor's permission
**Then** `TODO:` which permission level or role satisfies "admin role" for the override is not yet confirmed

---

### AT-011 — Interest Start Date is required

**Verifies:** [BR-011](business-rules.md#br-011--interest-start-date-required)

**Given** Tab 1 has Interest Start Date left blank
**When** the actor clicks Next or Complete
**Then** the system blocks the action with a validation error on Interest Start Date

---

### AT-012 — Maturity Amount is computed from the scheme interest formula

**Verifies:** [BR-012](business-rules.md#br-012--maturity-amount-return-date-and-receipt-date-system-computed), [UC-001](use-cases.md#uc-001--open-a-new-fd-account)

**Given** the actor enters FD Amount, a slab (rate + duration), and Interest Start Date on an interest-bearing FD scheme
**When** Tab 1 re-renders
**Then** Maturity Amount, Return Date, and Receipt Date display as read-only computed Labels derived from the scheme interest formula and duration

**Given** the selected scheme is a double-money type (`दामदुप्पट` / `कॅश सर्टिफिकेट`)
**When** the maturity is displayed
**Then** Maturity Amount reflects the scheme grid's fixed maturity value rather than a computed accrual
**And** `TODO:` the exact day-count/compounding formula remains unconfirmed

---

### AT-013 — Account Status defaults to Active with three shared values

**Verifies:** [BR-013](business-rules.md#br-013--account-status-default-and-shared-values-across-deposit-products)

**Given** a new New FD Account wizard is opened
**When** the actor views the Status dropdown on Tab 1
**Then** the default selected value is `चालू` (Active)
**And** the only other selectable values are `बंद` and `स्थगित`

---

### AT-014 — IFSC Code auto-fills Bank Name

**Verifies:** [BR-014](business-rules.md#br-014--ifsc-code-enables-bank-payout-auto-fill)

**Given** the actor enters a valid IFSC Code on Tab 1
**When** the field resolves
**Then** the read-only Bank Name Label populates
**And** the actor may optionally enter a Bank Savings Account No. for payout

---

### AT-015 — Advanced Settings visibility role unresolved (TODO)

**Verifies:** [BR-015](business-rules.md#br-015--advanced-settings-visibility-role-undefined)

**Given** an actor without a defined "accounting/admin role" opens New FD Account
**When** the actor views Tab 1
**Then** the actor can still manually expand प्रगत सेटिंग्ज (Advanced Settings)
**And** `TODO:` whether any actor is blocked from expanding it is not yet confirmed

---

### AT-016 — Receipt Prefix and Receipt Number are required

**Verifies:** [BR-016](business-rules.md#br-016--receipt-prefix-and-receipt-number-required)

**Given** Advanced Settings is expanded with Receipt Prefix or Receipt Number left blank
**When** the actor clicks Complete
**Then** the system blocks the action with a validation error on the blank receipt field
**And** `TODO:` whether Receipt Number auto-increments from the scheme series is not yet confirmed

---

### AT-017 — Multiple FD semantics unresolved (TODO)

**Verifies:** [BR-017](business-rules.md#br-017--multiple-fd-workflow-semantics-undefined)

**Given** the actor enters an Actual FD Amount and a Multiplier greater than 1 and clicks `+ टाका`
**When** the actor completes the wizard
**Then** `TODO:` how many FD accounts are persisted and how Account No./Receipt series are consumed is not yet confirmed

---

### AT-018 — Nominee tab hidden until Add Nominee checked

**Verifies:** [BR-018](business-rules.md#br-018--nominee-section-conditional-on-add-nominee-checkbox)

**Given** Tab 1 has Add Nominee unchecked
**When** the actor views the tab bar
**Then** Tab 2 (वारसदार) is not shown and is skipped during Next/Back navigation

**Given** the actor checks Add Nominee
**When** the tab bar re-renders
**Then** Tab 2 becomes visible

---

### AT-019 — Joint Holder tab hidden until Add Joint Holder checked

**Verifies:** [BR-019](business-rules.md#br-019--joint-holder-section-conditional-on-add-joint-holder-checkbox)

**Given** Tab 1 has Add Joint Holder unchecked
**When** the actor views the tab bar
**Then** Tab 3 (संयुक्त खाते धारक) is not shown and is skipped during Next/Back navigation

**Given** the actor checks Add Joint Holder
**When** the tab bar re-renders
**Then** Tab 3 becomes visible

---

### AT-020 — Nominee resolves via Autocomplete or quick-add

**Verifies:** [BR-020](business-rules.md#br-020--nominee-lookup-resolves-to-existing-or-quick-added-customer)

**Given** Tab 2 is open and the actor searches for a nominee not found in Customer master
**When** the actor clicks **+ नवीन ग्राहक जोडा**
**Then** the quick-add popup opens with Salutation, Name, Date of Birth, and Mobile Number fields
**And** on Save, the new Customer is created and the Autocomplete displays the resolved `id — name`

---

### AT-021 — Nominee Relation matches canonical Membership list

**Verifies:** [BR-021](business-rules.md#br-021--nominee-relation-reuses-canonical-membership-list)

**Given** a nominee customer is resolved on Tab 2
**When** the actor opens the Relation dropdown
**Then** the options exactly match the canonical Relation list defined on New Membership Tab 3 (`मुलगा`, `पुतण्या`, `मुली`, `मुलगा - पती`, `पति व मुलगा`, `वरील प्रमाणे`, `बायको`, `मैत्रीण`, `केअरटेकर`, `लहान भाऊ`, `स्वतः`, `पत्नी`, `पती`)
**And** no additional FD-specific Relation values are present

---

### AT-022 — Nominee Percentage optional; Nomination Date and Age read-only

**Verifies:** [BR-022](business-rules.md#br-022--nominee-percentage-optional-nomination-date-and-age-system-derived)

**Given** a nominee customer with Date of Birth 2000-01-01 is resolved on Tab 2
**When** the actor views Nomination Date and Age at Nomination
**Then** both render as read-only Labels, with Age computed from the nominee's Date of Birth
**And** leaving Percentage blank does not block Add

---

### AT-023 — Joint Holder Add validates a resolved customer

**Verifies:** [BR-023](business-rules.md#br-023--joint-holder-guardian-and-customer-fields-add-validates-selection)

**Given** Tab 3 has Select Customer left unresolved
**When** the actor clicks **+ जोड (Add)**
**Then** the system blocks the add with a validation error requiring a resolved customer

---

### AT-024 — Account Operation Instructions defaults to Self

**Verifies:** [BR-024](business-rules.md#br-024--account-operation-instructions-required-with-defined-values)

**Given** Tab 3 is opened for the first time
**When** the actor views Account Operation Instructions
**Then** the default selected value is `स्वतः` (Self)
**And** the only other selectable values are `फक्त प्रमुख खातेदार`, `फक्त संयुक्त खातेदार`, `दोन्ही खातेदार आवश्यक`, `दोघांपैकी कोणीही`

---

### AT-025 — Interest Reinvestment reveals S.I. frequency

**Verifies:** [BR-025](business-rules.md#br-025--interest-reinvestment-enables-si-reinvestment-frequency)

**Given** Tab 4 has व्याज पुनर्निवेश unchecked
**When** the actor views the section
**Then** the S.I. Interest Reinvestment frequency field is hidden

**Given** the actor checks व्याज पुनर्निवेश
**When** the section re-renders
**Then** the S.I. Interest Reinvestment frequency dropdown becomes visible and selectable

---

### AT-026 — Auto Renewal and Renewal are mutually exclusive

**Verifies:** [BR-026](business-rules.md#br-026--auto-renewal-and-renewal-mutually-exclusive-renewal-type-radios)

**Given** Tab 4 has ऑटो नूतनीकरण checked
**When** the actor views नूतनीकरण
**Then** the नूतनीकरण checkbox is disabled

**Given** the actor checks नूतनीकरण instead
**When** the renewal-type radios render
**Then** मुद्दल + व्याज / फक्त मुद्दल / केवळ व्याज become enabled with फक्त मुद्दल as default
**And** `TODO:` how renewal executes at maturity is not yet confirmed

---

### AT-027 — Interest Transfer reveals routing fields

**Verifies:** [BR-027](business-rules.md#br-027--interest-transfer-enables-gl-holder-and-frequency-routing)

**Given** Tab 4 has व्याज हस्तांतरण unchecked
**When** the actor views the section
**Then** Select GL, Select Account Holder, Select Frequency, and Select Day/Date are hidden

**Given** the actor checks व्याज हस्तांतरण
**When** the section re-renders
**Then** those routing fields become visible and are not persisted as active routing when the checkbox is later cleared

---

### AT-028 — Account Closing routing reveals GL and holder fields

**Verifies:** [BR-028](business-rules.md#br-028--account-closing-gl-routing-enabled-by-checkbox)

**Given** Tab 4 has खाते बंद करतेवेळी unchecked
**When** the actor views the section
**Then** the Select GL and Select Account Holder fields are hidden

**Given** the actor checks खाते बंद करतेवेळी
**When** the section re-renders
**Then** Select GL and Select Account Holder become visible for closing-proceeds routing

---

### AT-029 — Wizard does not persist until final Complete

**Verifies:** [BR-029](business-rules.md#br-029--new-fd-account-wizard-atomic-save-on-create), [WF-001](workflows.md#wf-001--new-fd-account-wizard)

**Given** an actor is creating a new FD account with Add Nominee and Add Joint Holder both checked
**And** Tabs 1–3 have valid data entered
**When** the actor clicks Next (or Back) without clicking Complete
**Then** no Account record is persisted

**Given** the actor completes Tab 4 and clicks Complete with all visible tabs valid
**When** the save request completes
**Then** the Account, Nominee(s), and Joint Holder(s) are persisted together

---

### AT-030 — View Only hides persist actions across FD screens

**Verifies:** [BR-030](business-rules.md#br-030--fd-screens-use-master-permission-levels)

**Given** a User with View Only on New FD Account
**When** the User opens New FD Account
**Then** all fields across all tabs are read-only
**And** Complete is not visible

**Given** a User with No Rights on FD Account Management
**When** the User attempts to navigate to it
**Then** navigation is blocked

---

### AT-031 — Account Management Show works with zero filters

**Verifies:** [BR-031](business-rules.md#br-031--account-management-search-fields-all-optional-organization-auto-filled)

**Given** the actor leaves all Register Primary Search fields blank
**When** the actor clicks Show
**Then** the system does not block the search
**And** the grid displays results per the actor's entitled scope
**And** the Organization header shows the session Organization read-only

---

### AT-032 — Register legend highlights loan-linked and matured accounts (TODO)

**Verifies:** [BR-032](business-rules.md#br-032--register-grid-legend-loan-linked-and-matured-accounts)

**Given** the Register grid contains a matured account and a loan-linked account
**When** the grid renders
**Then** the matured account row is highlighted blue
**And** the loan-linked account row is highlighted pink
**And** `TODO:` the exact loan-linkage definition is unconfirmed pending the Loan domain

---

### AT-033 — Account Management follows interactive reporting standard

**Verifies:** [BR-033](business-rules.md#br-033--account-management-follows-interactive-reporting-standard)

**Given** the actor selects Status = `चालू` and Branch = `1 — Branch 1` on the Register
**When** the actor clicks Show
**Then** the grid displays only Active FD accounts in Branch 1 with pagination
**And** the footer shows एकूण नोंदी and the totals (एकूण एफडी शिल्लक, एकूण व्याज दिले, एकूण तरतूद व्याज)

---

### AT-034 — काढा removes the account registration row

**Verifies:** [BR-034](business-rules.md#br-034--काढा-remove-deletes-the-account-registration-row)

**Given** the actor has selected an FD account row in the Register
**When** the actor clicks काढा (Remove)
**Then** the account registration row is deleted from the register, not merely hidden
**And** `TODO:` whether a confirmation dialog appears and whether removal is blocked for accounts with posted transactions is unconfirmed

---

### AT-035 — Account Statement and Details gaps (TODO)

**Verifies:** [BR-035](business-rules.md#br-035--account-statement-and-details-lack-dedicated-specs)

**Given** the actor clicks खाते उतारा (Account Statement) for a selected FD account
**When** the system attempts to render the statement
**Then** `TODO:` no dedicated report spec exists to define its layout or data — behaviour is unconfirmed

---

### AT-036 — Renewal List is read/export only

**Verifies:** [BR-036](business-rules.md#br-036--renewal-list-is-read-and-export-only)

**Given** the actor opens the नूतनीकरण यादी tab and clicks Show
**When** the renewal events render
**Then** the only available action is निर्यात करा (Export)
**And** no create/edit/reverse action is offered
**And** `TODO:` the source that generates renewal events is unconfirmed

---

### AT-037 — Deposit Loan Installment requires an existing deposit loan

**Verifies:** [BR-037](business-rules.md#br-037--deposit-loan-must-exist-before-installment-payment), [UC-003](use-cases.md#uc-003--record-a-deposit-loan-installment-payment)

**Given** the actor resolves a Customer who has no active loan-against-deposit
**When** the actor clicks Calculate Interest
**Then** no installment lines are returned
**And** the loan itself must first be opened via New Deposit Loan (Loan module)

---

### AT-038 — Installment Interest tab requires mode, GL, and a party lookup

**Verifies:** [BR-038](business-rules.md#br-038--installment-interest-tab-requires-mode-gl-and-a-customer-or-account-holder-lookup)

**Given** the Interest tab has Cash/Transfer unset or Select GL blank
**When** the actor clicks Calculate Interest
**Then** the system blocks with a validation error on the missing required field

**Given** the actor resolves either a Customer or an Account Holder (not both)
**When** the actor proceeds
**Then** the system accepts the single party lookup per the on-screen note

---

### AT-039 — Calculate Interest populates grid; Set applies (TODO)

**Verifies:** [BR-039](business-rules.md#br-039--calculate-interest-populates-installment-grid-set-applies)

**Given** a resolved deposit loan with due installments
**When** the actor clicks Calculate Interest and then निर्धारित करा (Set) on selected rows
**Then** the summary totals (एकूण तरतूद, एकूण व्याज, एकूण रक्कम) update
**And** `TODO:` the interest basis and what "Set" persists (posted transaction vs. staged installment) are unconfirmed pending the Loan domain

---

### AT-040 — Deposit Loan Installment Tabs 2–6 uncaptured (TODO)

**Verifies:** [BR-040](business-rules.md#br-040--deposit-loan-installment-tabs-26-not-captured)

**Given** the actor opens the Deposit Loan Installment Payment screen
**When** the actor views Tabs 2–6 (Other Deductions, Loan Information, Collateral, Transfer, KYC)
**Then** `TODO:` these tabs are not captured and no business rules are defined; they are candidates for removal pending bank review

---

### AT-041 — Interest Multiplier persists nothing

**Verifies:** [BR-041](business-rules.md#br-041--interest-multiplier-is-a-scheme-based-calculator-with-no-persistence)

**Given** the actor completes an Interest Multiplier calculation
**When** the actor navigates away without any further action
**Then** no account or record is created
**And** reopening the screen shows an empty form

---

### AT-042 — Interest Multiplier conditional field visibility

**Verifies:** [BR-042](business-rules.md#br-042--interest-multiplier-conditional-field-visibility)

**Given** no Scheme is selected
**When** the actor views the calculator
**Then** the product-type, Simple/Compounding, Duration, and target radios are hidden

**Given** the actor selects a Scheme and sets Simple/Compounding = Compounding
**When** the form re-renders
**Then** the Compounding Frequency radio (मासिक/तिमाही/सहामाही/वार्षिक) becomes visible
**And** it stays hidden when Simple is selected

---

### AT-043 — Interest Multiplier computes Interest Rate or Duration

**Verifies:** [BR-043](business-rules.md#br-043--interest-multiplier-computes-interest-rate-or-duration)

**Given** the actor sets the target radio to व्याज दर (Interest Rate) and enters a Duration
**When** the actor clicks गणना करा (Calculate)
**Then** the read-only व्याज दर and दिनांक फरक outputs display

**Given** the actor sets the target radio to कालावधी (Duration)
**When** the actor clicks Calculate
**Then** the calculator solves for duration using the selected scheme's Simple/Compounding basis
**And** `TODO:` the exact day-count/compounding formula is unconfirmed

---

## Related Documents

- [overview.md](overview.md)
- [business-rules.md](business-rules.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [../../08-testing/](../../08-testing/) — future integration test plan (Phase 4)
