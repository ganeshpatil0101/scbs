# Acceptance Tests — Daily (Pigmy)

## Purpose

Given/When/Then tests verifying business rules and use cases for the Daily module. Each test references `BR-NNN` and/or `UC-NNN` ([business-rules.md](business-rules.md), [business-rules-part2.md](business-rules-part2.md)).

---

### AT-001 — New Daily Account requires an existing customer

**Verifies:** [BR-001](business-rules.md#br-001--customer-must-exist-before-a-daily-account-can-be-opened), [UC-001](use-cases.md#uc-001--open-a-new-daily-account)

**Given** the actor types a customer number with no matching Customer into the Tab 1 Autocomplete
**When** the actor presses Enter
**Then** the system shows no match and does not resolve a customer
**And** the actor cannot open the account for a non-existent customer

---

### AT-002 — Scheme required and limited to Daily type

**Verifies:** [BR-002](business-rules.md#br-002--scheme-required-and-loaded-from-daily-scheme-master)

**Given** Tab 1 has a resolved Customer and Select Scheme left at placeholder
**When** the actor clicks Next or Save
**Then** the system blocks the action with a validation error on Select Scheme
**And** the dropdown lists only schemes where Scheme Type = `डेली`

---

### AT-003 — Agent Branch and Agent required and must be pre-registered

**Verifies:** [BR-003](business-rules.md#br-003--agent-branch-and-agent-required-agent-must-be-registered-first)

**Given** Tab 1 has no Agent resolved
**When** the actor clicks Next or Save
**Then** the system blocks with a validation error on Select Agent (and Agent Branch)
**And** the Agent Autocomplete resolves only agents already registered via New Agent

---

### AT-004 — Account No. is read-only and system-generated

**Verifies:** [BR-004](business-rules.md#br-004--account-no-auto-generated)

**Given** a new New Daily Account wizard on Tab 1
**When** the actor views the Account No. field
**Then** it renders as a read-only Label with no value until after Save
**And** the actor cannot type into it

---

### AT-005 — Duration selection auto-fills months, days, and rate

**Verifies:** [BR-005](business-rules.md#br-005--duration-selected-from-scheme-grid-duration-and-rate-auto-filled)

**Given** a scheme with a duration row of 12 months / 365 days / 6% is selected
**When** the actor selects that duration
**Then** Duration (Months), Duration (Days), and Interest Rate populate read-only as `12`, `365`, `6`
**And** the actor cannot edit those three fields directly

---

### AT-006 — Commission Rate is required

**Verifies:** [BR-006](business-rules.md#br-006--commission-rate-required-at-account-opening)

**Given** Tab 1 has Commission Rate left blank
**When** the actor clicks Next or Save
**Then** the system blocks with a validation error on Commission Rate
**And** `TODO:` whether it defaults from the agent's commission configuration is unconfirmed

---

### AT-007 — Current Date defaults to system date

**Verifies:** [BR-007](business-rules.md#br-007--current-date-defaults-to-system-date)

**Given** a new wizard opened on 2026-07-24
**When** the actor views Tab 1
**Then** Current Date shows `2026-07-24` as a read-only Label
**And** it appears as Opening Date on the Account Register grid after Save

---

### AT-008 — Daily Deposit Amount required; maturity fields optional

**Verifies:** [BR-008](business-rules.md#br-008--daily-deposit-amount-required-maturity-fields-optional)

**Given** Tab 1 has Daily Deposit Amount blank and Maturity Date/Amount blank
**When** the actor clicks Save
**Then** the system blocks with a validation error on Daily Deposit Amount only
**And** leaving Maturity Date and Maturity Amount blank does not block Save

---

### AT-009 — Account Status defaults to Active with three shared values

**Verifies:** [BR-009](business-rules.md#br-009--account-status-default-and-shared-values-across-deposit-products)

**Given** a new New Daily Account wizard
**When** the actor views Select Status
**Then** the default is `चालू` (Active)
**And** the only other values are `बंद` and `स्थगित`

---

### AT-010 — Pigmy Account for Loan flag (TODO)

**Verifies:** [BR-010](business-rules.md#br-010--pigmy-account-for-loan-flag-depends-on-undocumented-loan-domain)

**Given** the actor checks कर्जासाठी पिग्मी खाते
**When** the account is saved
**Then** `TODO:` the loan-linkage effect (recovery/collateral, register pink highlight) is unconfirmed pending the Loan domain

---

### AT-011 — Advanced Settings visibility role (TODO)

**Verifies:** [BR-011](business-rules.md#br-011--advanced-settings-visibility-role-undefined)

**Given** an actor without a defined "accounting/admin role" opens New Daily Account
**When** the actor views Tab 1
**Then** the actor can still manually expand प्रगत सेटिंग्ज
**And** `TODO:` whether any actor is blocked from expanding it is unconfirmed

---

### AT-012 — Advanced overrides are optional

**Verifies:** [BR-012](business-rules.md#br-012--advanced-overrides-optional-with-scheme-defaults)

**Given** Advanced Settings is expanded with Sales Agent, limits, and IFSC left blank
**When** the actor clicks Save
**Then** the account is created with no validation error on any Advanced field
**And** Interest Type and Compounding show scheme defaults

---

### AT-013 — Nominee tab hidden until Add Nominee checked

**Verifies:** [BR-013](business-rules.md#br-013--nominee-section-conditional-on-add-nominee-checkbox)

**Given** Tab 1 has Add Nominee unchecked
**When** the actor views the tab bar
**Then** Tab 2 (वारसदार) is not shown and is skipped during Next/Back

**Given** the actor checks Add Nominee
**When** the tab bar re-renders
**Then** Tab 2 becomes visible

---

### AT-014 — Joint Holder tab hidden until Add Joint Holder checked

**Verifies:** [BR-014](business-rules.md#br-014--joint-holder-section-conditional-on-add-joint-holder-checkbox)

**Given** Tab 1 has Add Joint Holder unchecked
**When** the actor views the tab bar
**Then** Tab 3 is not shown and is skipped during Next/Back

**Given** the actor checks Add Joint Holder
**When** the tab bar re-renders
**Then** Tab 3 becomes visible

---

### AT-015 — Nominee resolves via Autocomplete or quick-add

**Verifies:** [BR-015](business-rules.md#br-015--nominee-lookup-resolves-to-existing-or-quick-added-customer)

**Given** Tab 2 is open and the nominee is not found in Customer master
**When** the actor clicks **+ नवीन ग्राहक जोडा**
**Then** the quick-add popup opens with Salutation, Name, Date of Birth, and Mobile Number
**And** on Save the new Customer resolves in the Autocomplete and Nominee Details become visible

---

### AT-016 — Nominee Relation matches canonical Membership list

**Verifies:** [BR-016](business-rules.md#br-016--nominee-relation-reuses-canonical-membership-list)

**Given** a nominee customer is resolved on Tab 2
**When** the actor opens the Relation dropdown
**Then** the options exactly match the canonical Membership Relation list
**And** no Daily-specific Relation values are present

---

### AT-017 — Nominee Percentage optional; Date and Age read-only

**Verifies:** [BR-017](business-rules.md#br-017--nominee-percentage-optional-nomination-date-and-age-system-derived)

**Given** a nominee with Date of Birth 2000-01-01 is resolved on Tab 2
**When** the actor views Nomination Date and Age at Nomination
**Then** both are read-only Labels, Age computed from Date of Birth
**And** leaving Percentage blank does not block Add

---

### AT-018 — Joint Holder Add validates a resolved customer

**Verifies:** [BR-018](business-rules.md#br-018--joint-holder-guardian-and-customer-add-validates-selection)

**Given** Tab 3 has Select Customer unresolved
**When** the actor clicks **+ जोड (Add)**
**Then** the system blocks the add with a validation error requiring a resolved customer

---

### AT-019 — Account Operation Instructions defaults to Self

**Verifies:** [BR-019](business-rules.md#br-019--account-operation-instructions-required-with-defined-values)

**Given** Tab 3 is opened for the first time
**When** the actor views Account Operation Instructions
**Then** the default is `स्वतः` (Self)
**And** the other values are `फक्त प्रमुख खातेदार`, `फक्त संयुक्त खातेदार`, `दोन्ही खातेदार आवश्यक`, `दोघांपैकी कोणीही`

---

### AT-020 — Wizard does not persist until final Save

**Verifies:** [BR-020](business-rules.md#br-020--new-daily-account-wizard-atomic-save-on-create), [WF-001](workflows.md#wf-001--new-daily-account-wizard)

**Given** a new Daily account with Add Nominee and Add Joint Holder both checked and Tabs 1–2 valid
**When** the actor clicks Next or Back without Save
**Then** no Account record is persisted

**Given** the actor completes Tab 3 and clicks Save with all tabs valid
**When** the save completes
**Then** the Account, Nominee(s), and Joint Holder(s) are persisted together

---

### AT-021 — Agent identity requires an existing customer

**Verifies:** [BR-021](business-rules.md#br-021--agent-identity-requires-an-existing-customer), [UC-002](use-cases.md#uc-002--register-a-new-collection-agent)

**Given** the New Agent Tab 1 Autocomplete has no matching Customer
**When** the actor presses Enter
**Then** no customer resolves and the agent cannot be registered
**And** a resolved Customer supplies the agent's identity details

---

### AT-022 — Agent Status and Joining Date required

**Verifies:** [BR-022](business-rules.md#br-022--agent-status-and-joining-date-required)

**Given** New Agent Tab 1
**When** the actor views Status and Joining Date
**Then** Status defaults to `चालू` and Joining Date to the system date
**And** clearing either blocks Next with a validation error

---

### AT-023 — Agent linked savings account requires Branch and Account Holder

**Verifies:** [BR-023](business-rules.md#br-023--agent-linked-savings-account-branch-and-account-holder-required)

**Given** the बचत खाते block has Branch or Account Holder unresolved
**When** the actor clicks Next
**Then** the system blocks with a validation error
**And** Select GL may be left blank

---

### AT-024 — TDS Reason appears only when TDS = No

**Verifies:** [BR-024](business-rules.md#br-024--tds-reason-conditional-on-tds--no)

**Given** TDS is set to `होय` (Yes)
**When** the actor views the TDS block
**Then** Select Reason is not shown

**Given** TDS is set to `नाही` (No)
**When** the block re-renders
**Then** Select Reason appears with values `सभासद`, `फॉर्म १५ डीआय`, `फॉर्म १५ एच`, `फॉर्म १५ जी`

---

### AT-025 — Deduction blocks gated by their checkboxes

**Verifies:** [BR-025](business-rules.md#br-025--agent-deduction-blocks-conditional-on-their-checkboxes)

**Given** Security Deposit, Machine Deduction, and Provident Fund checkboxes are unchecked
**When** the actor views Advanced Settings
**Then** each block's fields are inert/hidden

**Given** the actor checks Security Deposit
**When** the block enables
**Then** its Branch becomes required

---

### AT-026 — Agent commission configured per scheme and amount slab

**Verifies:** [BR-026](business-rules.md#br-026--agent-commission-config-per-scheme-and-amount-slab)

**Given** Tab 2 with Scheme, Commission %, From Amount, and Up to Amount entered
**When** the actor clicks **+ टाका**
**Then** a commission row is appended to the grid
**And** multiple scheme/amount-slab rows may be added before Complete

---

### AT-027 — New Agent persists only on Complete

**Verifies:** [BR-027](business-rules.md#br-027--new-agent-wizard-atomic-save-on-create), [WF-002](workflows.md#wf-002--new-agent-wizard)

**Given** Tab 1 is valid and the actor clicks Next to Tab 2 without Complete
**When** the actor inspects persistence
**Then** no Agent record is written

**Given** the actor completes Tab 2 and clicks Complete
**When** the save finishes
**Then** the Agent and its commission rows are persisted together

---

### AT-028 — Organization header is read-only from session

**Verifies:** [BR-028](business-rules-part2.md#br-028--organization-auto-fill-header-from-session)

**Given** the actor opens Account Register
**When** the header renders
**Then** संस्था shows the session organization as a read-only Label
**And** it is not a filter field

---

### AT-029 — Account Register Show works with zero filters

**Verifies:** [BR-029](business-rules-part2.md#br-029--account-register-primary-search-fields-all-optional)

**Given** the actor leaves all Primary Search fields blank
**When** the actor clicks दाखवा (Show)
**Then** the system does not block the search
**And** the grid displays results per the actor's entitled scope

---

### AT-030 — Status filter shares the deposit enum

**Verifies:** [BR-030](business-rules-part2.md#br-030--status-filter-shares-deposit-product-enum)

**Given** the Account Register Status filter
**When** the actor opens it
**Then** the default is `चालू` and values are `चालू`, `बंद`, `स्थगित`

---

### AT-031 — Results grid legend highlighting (TODO on loan link)

**Verifies:** [BR-031](business-rules-part2.md#br-031--results-grid-legend-loan-linked-and-matured-highlighting)

**Given** a matured Daily account
**When** the grid renders
**Then** the matured row is highlighted light blue

**Given** an account flagged as loan-linked
**When** the grid renders
**Then** `TODO:` the pink highlight's exact linkage source is unconfirmed pending the Loan domain

---

### AT-032 — काढा removes the account registration row

**Verifies:** [BR-032](business-rules-part2.md#br-032--काढा-remove-deletes-the-account-registration-row)

**Given** the actor selects a Daily account row
**When** the actor clicks काढा (Remove)
**Then** the account registration row is deleted, the same as वगळा on the Savings register
**And** the row is not merely hidden

**And** the register exposes no खाते बंद करा (Close Account) action

---

### AT-033 — Account Register reporting and detail/statement gaps (TODO)

**Verifies:** [BR-033](business-rules-part2.md#br-033--account-register-follows-interactive-reporting-detail-and-statement-gaps)

**Given** the actor clicks तपशील or खाते उतारा for a selected row
**When** the system attempts to render it
**Then** `TODO:` no dedicated Account Information screen / deposit-account statement report exists yet — behaviour is unconfirmed

---

### AT-034 — Challan Number auto-generated

**Verifies:** [BR-034](business-rules-part2.md#br-034--challan-number-auto-generated)

**Given** the actor opens Agent Collection Management
**When** Tab 1 renders
**Then** Challan Number shows a system-generated value as a read-only Label

---

### AT-035 — Collection requires Agent and mode; grid loads on View

**Verifies:** [BR-035](business-rules-part2.md#br-035--collection-requires-agent-and-mode-selections-grid-loaded-on-view)

**Given** Tab 1 with no Agent or no mode selected
**When** the actor clicks बघा (View)
**Then** the system blocks with a validation error on the missing required selections

**Given** Agent, Cash/Transfer, Collection Amount, One Day/Multiple Days, and Collection Date are set
**When** the actor clicks View
**Then** the collection grid loads for the selected agent

---

### AT-036 — Collection grid computes totals, penalty, discount, commission

**Verifies:** [BR-036](business-rules-part2.md#br-036--collection-grid-computes-totals-penalty-discount-and-commission)

**Given** a loaded collection grid with day-wise amounts
**When** the grid renders
**Then** per-row Total, RD Penalty, RD Discount, Agent Commission, and Agent Commission Rate are shown
**And** the footer aggregates एकूण रक्कम, एकूण एजंट कमिशन, and selected-row count
**And** `TODO:` the exact RD penalty/discount formulas are unconfirmed

---

### AT-037 — Collection posts member credits, commission, and GL voucher

**Verifies:** [BR-037](business-rules-part2.md#br-037--agent-collection-is-the-posting-point-for-daily-collections), [UC-003](use-cases.md#uc-003--record-and-post-an-agent-daily-collection)

**Given** a completed collection across Tabs 1–3 with selected rows
**When** the actor performs the final posting action
**Then** the system atomically posts member-account credits, agent commission, and a balancing GL transfer voucher under the Challan
**And** intermediate tab navigation posts nothing

---

### AT-038 — Brief Details cheque fields required for Cheque type

**Verifies:** [BR-038](business-rules-part2.md#br-038--brief-details-instrument-fields-conditional-on-cheque)

**Given** Tab 2 with Cheque Type = `स्लिप`
**When** the actor proceeds
**Then** cheque-specific fields are not enforced

**Given** Cheque Type = `चेक`
**When** the actor proceeds with Cheque No./Date/Name/Bank blank
**Then** the system blocks with validation errors on the required cheque fields

---

### AT-039 — Transfer lines reconcile to collection total

**Verifies:** [BR-039](business-rules-part2.md#br-039--transfer-tab-posting-lines-reconcile-to-collection-total)

**Given** Tab 3 with GL/account posting lines added
**When** the actor views Total Transaction Amount
**Then** it equals the collection total from Tab 1
**And** `TODO:` whether Save is blocked on a mismatch is unconfirmed

---

### AT-040 — Collection List requires Branch and Agent

**Verifies:** [BR-040](business-rules-part2.md#br-040--collection-list-search-requires-branch-and-agent)

**Given** the Collection List tab with Branch or Agent unset
**When** the actor clicks दाखवा (Show)
**Then** the system blocks with a validation error

**Given** Branch and Agent are set
**When** the actor clicks Show
**Then** collections list with Agent Name, Transaction Date, Collection Amount, and an एकूण total

---

### AT-041 — Agent transfer reassigns accounts; same-agent blocked

**Verifies:** [BR-041](business-rules-part2.md#br-041--from-and-to-agent-required-selection-reassigns-accounts), [UC-004](use-cases.md#uc-004--reassign-accounts-between-agents)

**Given** Agent (From) = Agent (To)
**When** the actor confirms the transfer
**Then** the system blocks it with a validation error

**Given** distinct From/To agents and selected accounts
**When** the actor confirms the transfer
**Then** the selected accounts' collecting-agent binding is reassigned (persisted) to the To-agent
**And** account balances and posted entries are unchanged

---

### AT-042 — Only the From-agent's accounts are listed

**Verifies:** [BR-042](business-rules-part2.md#br-042--only-the-from-agents-accounts-are-listed-for-reassignment)

**Given** the From-agent is resolved
**When** the grid renders
**Then** it lists only the accounts currently bound to the From-agent

---

### AT-043 — Interest Multiplier scheme drives duration and rate

**Verifies:** [BR-043](business-rules-part2.md#br-043--interest-multiplier-scheme-required-duration-and-rate-auto-filled)

**Given** the actor selects a Daily scheme with duration 12 and rate 6
**When** the inputs re-render
**Then** Duration (Months) shows `12` and Interest Rate shows `6` as read-only Labels

**Given** no scheme selected
**When** the actor clicks Calculate
**Then** the system blocks with a validation error on Select Scheme

---

### AT-044 — Interest Multiplier is preview only

**Verifies:** [BR-044](business-rules-part2.md#br-044--deposit-amount-required-calculation-is-preview-only), [UC-006](use-cases.md#uc-006--calculate-daily-interest-and-maturity-interest-multiplier)

**Given** a selected scheme and Deposit Amount entered
**When** the actor clicks गणना करा (Calculate)
**Then** Total Amount, Interest Amount, Maturity Amount, and the daily chart are displayed
**And** no account is opened and no transaction is posted

---

### AT-045 — View Only hides write actions across Daily screens

**Verifies:** [BR-045](business-rules-part2.md#br-045--daily-screens-use-master-permission-levels)

**Given** a User with View Only on a Daily screen
**When** the User opens that screen
**Then** all fields are read-only and Save/Add/Remove/Create/Post/Transfer actions are not visible

**Given** a User with No Rights on a Daily screen
**When** the User attempts to navigate to it
**Then** navigation is blocked

---

## Related Documents

- [overview.md](overview.md)
- [business-rules.md](business-rules.md)
- [business-rules-part2.md](business-rules-part2.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [../../08-testing/](../../08-testing/) — future integration test plan (Phase 4)
