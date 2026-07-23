# Acceptance Tests — Settings / Schemes

## Purpose

Given/When/Then tests verifying business rules and use cases for Schemes settings. Each test references `BR-NNN` and/or `UC-NNN`.

---

### AT-001 — Scheme Type required

**Verifies:** [BR-001](business-rules.md#br-001--scheme-type-required), [UC-001](use-cases.md#uc-001--create-product-scheme)

**Given** the New Scheme wizard is open with no Scheme Type selected
**When** the actor attempts to proceed without selecting Scheme Type
**Then** the system blocks progress with a validation error on Scheme Type

---

### AT-002 — Scheme Type change resets to Tab 1

**Verifies:** [BR-002](business-rules.md#br-002--scheme-type-change-resets-wizard), [WF-002](workflows.md#wf-002--scheme-type-switch-mid-wizard)

**Given** Scheme Type is Savings and Tab Interest Posting has entered data
**When** the actor changes Scheme Type to Loan
**Then** the wizard shows Tab Scheme Info for Loan
**And** Savings-only tabs and prior Savings draft values are not retained

---

### AT-003 — Tab set for Daily excludes Loan Specific

**Verifies:** [BR-003](business-rules.md#br-003--tab-visibility-by-scheme-type)

**Given** Scheme Type is Daily
**When** the actor views the wizard tabs
**Then** Scheme Info, Duration & Rates, Interest Posting, Account Closing, and Charges are available
**And** Loan Specific and Advanced are not shown

---

### AT-004 — GL Head required

**Verifies:** [BR-004](business-rules.md#br-004--gl-head-required-from-gl-master)

**Given** Scheme Type is Savings on Tab Scheme Info
**When** the actor clicks Next without selecting a GL Head
**Then** the system blocks advancement with a validation error on Select GL

---

### AT-005 — Daily GL Head number ≤ 99

**Verifies:** [BR-005](business-rules.md#br-005--daily-scheme-gl-head-number--99), [UC-001](use-cases.md#uc-001--create-product-scheme) E3

**Given** Scheme Type is Daily
**When** the actor selects a GL Head with number `163`
**Then** the system rejects the selection or Save with a GL Head ≤ 99 validation message

---

### AT-006 — Shared GL Head allowed across schemes

**Verifies:** [BR-006](business-rules.md#br-006--multiple-schemes-may-share-one-gl-head)

**Given** an existing Savings scheme already linked to GL Head `50`
**When** the actor creates a Daily scheme also selecting GL Head `50` (valid for Daily) and Saves successfully
**Then** both schemes persist with the same GL Head

---

### AT-007 — Scheme Name required

**Verifies:** [BR-007](business-rules.md#br-007--scheme-name-required)

**Given** Tab Scheme Info has GL Head and Status set
**When** Scheme Name is blank and the actor clicks Next or Save
**Then** the system blocks with a validation error on Scheme Name

---

### AT-008 — Scheme Name unique within Scheme Type

**Verifies:** [BR-008](business-rules.md#br-008--scheme-name-unique-within-scheme-type), [UC-001](use-cases.md#uc-001--create-product-scheme) E2

**Given** a Savings scheme named `सामान्य बचत` already exists
**When** the actor creates another Savings scheme with the same name and clicks Save
**Then** the system rejects Save for duplicate name within Savings
**And** creating an FD scheme named `सामान्य बचत` is allowed

---

### AT-009 — Status values include कालबाह्य for Daily only

**Verifies:** [BR-009](business-rules.md#br-009--scheme-status-required-with-defined-values)

**Given** Scheme Type is Daily
**When** the actor opens the Status dropdown
**Then** options include `चालू`, `बंद`, `स्थगित`, and `कालबाह्य`
**And** when Scheme Type is Savings, `कालबाह्य` is not offered

---

### AT-010 — Allow Only Members persists when checked

**Verifies:** [BR-010](business-rules.md#br-010--allow-only-members-optional)

**Given** a valid scheme wizard with Allow Only Members checked
**When** the actor Saves successfully
**Then** the persisted scheme has Allow Only Members = true

---

### AT-011 — Interest Posting Add requires day 1–31 and month

**Verifies:** [BR-011](business-rules.md#br-011--interest-posting-day-and-month-on-add)

**Given** the Interest Posting tab is open
**When** the actor clicks Add with Day or Month still `निवडा`
**Then** no row is added
**And** when Day is `15` and Month is January, Add inserts a posting row

---

### AT-012 — Shared charge type list

**Verifies:** [BR-012](business-rules.md#br-012--shared-charge-types)

**Given** the Charges tab is open for any Scheme Type
**When** the actor opens the Charges dropdown
**Then** the options are Borrower Welfare Fund, Pigmy Commission, Processing Fee, Class B Member Fee, and Stationery Fee (Marathi labels per spec)

---

### AT-013 — Next does not persist scheme

**Verifies:** [BR-013](business-rules.md#br-013--scheme-wizard-atomic-save-on-create), [UC-001](use-cases.md#uc-001--create-product-scheme)

**Given** a new scheme with valid Tab Scheme Info
**When** the actor clicks Next to another tab
**Then** no scheme record exists in persistent storage until Complete/Save

---

### AT-014 — View Only cannot Save

**Verifies:** [BR-014](business-rules.md#br-014--new-scheme-form-uses-master-permission-levels)

**Given** the actor has View Only on New Scheme
**When** the actor opens New Scheme
**Then** fields are read-only or Save is hidden
**And** no scheme can be created

---

### AT-015 — Savings subtype and interest rate required

**Verifies:** [BR-015](business-rules.md#br-015--savings-product-subtype-and-interest-rate-required)

**Given** Scheme Type is Savings
**When** product subtype is `निवडा` or Interest Rate is blank and the actor clicks Next
**Then** the system blocks with validation errors on those fields

---

### AT-016 — Savings Start of Month required only for In Months

**Verifies:** [BR-016](business-rules.md#br-016--savings-interest-calculation-mode)

**Given** Scheme Type is Savings and In Days is selected
**When** the actor views Interest Calculation
**Then** Start of Month is not required
**And** when In Months is selected, Start of Month 1–31 is required before Next

---

### AT-017 — Open Ended default for Daily

**Verifies:** [BR-017](business-rules.md#br-017--open-ended-and-close-ended-mutually-exclusive)

**Given** a new Daily scheme on Tab Scheme Info
**When** the screen loads
**Then** Open Ended is selected by default
**And** selecting Close Ended clears Open Ended

---

### AT-018 — Compound frequency not required for Simple Interest

**Verifies:** [BR-018](business-rules.md#br-018--compound-frequency-when-compound-interest)

**Given** Scheme Type is FD and Simple Interest is selected
**When** the actor views Interest Type controls
**Then** compound frequency radios are hidden or disabled
**And** when Compound Interest is selected, a frequency option is available

---

### AT-019 — Daily Calculation Day required

**Verifies:** [BR-019](business-rules.md#br-019--daily-calculation-day-required)

**Given** Scheme Type is Daily
**When** Calculation Day is empty and the actor clicks Next
**Then** the system blocks with a validation error on Calculation Day

---

### AT-020 — FD duration row requires maturity amount

**Verifies:** [BR-020](business-rules.md#br-020--duration-and-rates-row-required-fields)

**Given** Scheme Type is FD on Duration & Rates
**When** the actor clicks Add with Duration and Rate filled but Maturity Amount blank
**Then** no row is added and Maturity Amount shows a validation error

---

### AT-021 — Account Closing hidden for Loan

**Verifies:** [BR-021](business-rules.md#br-021--account-closing-tab-deposit-types-only)

**Given** Scheme Type is Loan
**When** the actor views wizard tabs
**Then** Account Closing is not shown

---

### AT-022 — FD multiplier and receipt series required

**Verifies:** [BR-022](business-rules.md#br-022--fd-required-identity-fields)

**Given** Scheme Type is FD
**When** Multiplier or Receipt Series fields are blank on Save
**Then** the system rejects Save with validation on the missing FD identity fields

---

### AT-023 — FD Auto Renewal dependents gated

**Verifies:** [BR-023](business-rules.md#br-023--fd-auto-renewal-dependent-fields)

**Given** Scheme Type is FD and Auto Renewal is unchecked
**When** the actor views Advanced Auto Renewal fields
**Then** waiting period / locking / post-maturity renewal rate fields are disabled or hidden
**And** checking Auto Renewal enables those fields

---

### AT-024 — FD has no separate Additional Benefits tab

**Verifies:** [BR-024](business-rules.md#br-024--fd-benefits-on-duration-tab-only)

**Given** Scheme Type is FD
**When** the actor views wizard tabs
**Then** there is no standalone Additional Benefits tab
**And** Benefits checkboxes appear on Duration & Rates

---

### AT-025 — Recurring duration row requires agent rate

**Verifies:** [BR-025](business-rules.md#br-025--recurring-duration-row-includes-agent-rate)

**Given** Scheme Type is Recurring on Duration & Rates
**When** the actor clicks Add without Agent Interest Rate
**Then** no row is added and Agent Interest Rate shows a validation error

---

### AT-026 — Recurring Salary under Advanced

**Verifies:** [BR-026](business-rules.md#br-026--recurring-salary-and-rebate-under-advanced)

**Given** Scheme Type is Recurring
**When** the actor views top-level tabs
**Then** Salary Payment and Rebate are not separate top-level tabs
**And** those sections are available under Advanced

---

### AT-027 — Loan Type required

**Verifies:** [BR-027](business-rules.md#br-027--loan-type-required)

**Given** Scheme Type is Loan
**When** Loan Type remains `निवडा` and the actor clicks Next
**Then** the system blocks with a validation error on Loan Type

---

### AT-028 — Billing cycle day only for Credit Card

**Verifies:** [BR-028](business-rules.md#br-028--credit-card-billing-cycle-day-conditional)

**Given** Scheme Type is Loan and Loan Type is Member Loan
**When** the actor views Tab Scheme Info
**Then** Monthly Billing Cycle Day is hidden
**And** when Loan Type is Credit Card, Monthly Billing Cycle Day is visible and required

---

### AT-029 — Deposit mandatory gates deposit GL fields

**Verifies:** [BR-029](business-rules.md#br-029--loan-deposit-account-mandatory-enables-fields)

**Given** Scheme Type is Loan and Deposit Account Mandatory is unchecked
**When** the actor views deposit-related fields
**Then** Deposit G.L. Head and Minimum Deposit Duration are disabled or hidden
**And** checking Deposit Account Mandatory enables them

---

### AT-030 — Loan duration row required columns

**Verifies:** [BR-030](business-rules.md#br-030--loan-duration-row-required-fields)

**Given** Scheme Type is Loan on Duration & Rates
**When** the actor clicks Add without Maximum Loan Amount
**Then** no row is added and Maximum Loan Amount shows a validation error

---

### AT-031 — Guarantor total equals A+B+C

**Verifies:** [BR-031](business-rules.md#br-031--loan-guarantor-total-is-sum)

**Given** Loan Specific Guarantor has Customer (A)=1, Class A (B)=2, Nominal (C)=0
**When** the total field is displayed
**Then** Total Guarantors shows `3`
**And** the total is not independently editable

---

### AT-032 — Loan Deduction mode uses shared charge names

**Verifies:** [BR-032](business-rules.md#br-032--loan-charges-deduction-or-fee-mode), [BR-012](business-rules.md#br-012--shared-charge-types)

**Given** Scheme Type is Loan on Charges with Deduction selected
**When** the actor opens the Deduction dropdown
**Then** the shared five charge names are available

---

### AT-033 — Reset clears without save

**Verifies:** [BR-013](business-rules.md#br-013--scheme-wizard-atomic-save-on-create), [UC-002](use-cases.md#uc-002--reset-scheme-wizard-without-saving)

**Given** the wizard has unsaved Scheme Info data
**When** the actor clicks Reset
**Then** wizard fields clear
**And** no scheme record is persisted

---

### AT-034 — Status gates account opening — pending confirmation

**Verifies:** [BR-033](business-rules.md#br-033--scheme-status-account-opening-eligibility)

**Given** `TODO:` business confirms which Status values allow new account opening
**When** an operational New Account screen lists schemes
**Then** only schemes with allowed Status values appear (or selection is rejected for disallowed Status)
**And** this test remains blocked until BR-033 is Confirmed

---

### AT-035 — Minimum grid rows on Save — pending confirmation

**Verifies:** [BR-034](business-rules.md#br-034--minimum-grid-rows-on-save)

**Given** `TODO:` business confirms whether ≥1 Duration & Rates and/or Interest Posting row is required
**When** the actor Saves a scheme with empty applicable grids
**Then** the system either accepts Save or rejects per the confirmed rule
**And** this test remains blocked until BR-034 is Confirmed

---

## Related Documents

- [overview.md](overview.md)
- [business-rules.md](business-rules.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [../../05-ui-ux/settings/schemes/new-scheme-screen.md](../../05-ui-ux/settings/schemes/new-scheme-screen.md)
