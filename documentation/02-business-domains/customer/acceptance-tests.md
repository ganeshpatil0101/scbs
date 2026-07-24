# Acceptance Tests — Customer

## Purpose

Given/When/Then tests verifying business rules and use cases for the Customer module. Each test references `BR-NNN` and/or `UC-NNN`.

---

### AT-001 — Customer No. is read-only and system-generated

**Verifies:** [BR-001](business-rules.md#br-001--customer-number-auto-generated)

**Given** a new New Customer wizard is open on Tab 1
**When** the actor views the Customer No. field
**Then** it renders as a read-only Label
**And** the actor cannot type into it

---

### AT-002 — Customer Type is optional

**Verifies:** [BR-002](business-rules.md#br-002--customer-type-optional-with-defined-values)

**Given** Tab 1 is open with Customer Type left at its unselected state
**When** the actor completes all other required fields and clicks Next
**Then** the wizard advances to Tab 2 without a Customer Type validation error

---

### AT-003 — Branch defaults to logged-in branch

**Verifies:** [BR-003](business-rules.md#br-003--branch-defaults-to-logged-in-branch-editable)

**Given** an actor logged in against Branch 1 opens New Customer
**When** Tab 1 loads
**Then** Select Branch shows `1 — Branch 1` pre-filled
**And** the actor can change it to another branch via Autocomplete before Save

---

### AT-004 — Name is required

**Verifies:** [BR-004](business-rules.md#br-004--salutation-and-name-required)

**Given** Tab 1 has Name left blank
**When** the actor clicks Next
**Then** the system blocks advancement with a validation error on Name

---

### AT-005 — Age auto-calculates from Date of Birth

**Verifies:** [BR-005](business-rules.md#br-005--date-of-birth-required-age-auto-calculated)

**Given** the actor enters a Date of Birth on Tab 1
**When** the field loses focus
**Then** Age (Years) and Age (Months) update automatically as read-only values
**And** the actor cannot edit them directly

---

### AT-006 — Mobile Number required and captured once

**Verifies:** [BR-006](business-rules.md#br-006--mobile-number-required-one-per-customer)

**Given** Tab 1 has Mobile Number left blank
**When** the actor clicks Next
**Then** the system blocks advancement with a validation error on Mobile Number
**And** Tab 2 (Address) does not present a Mobile Number field on any address row

---

### AT-007 — Customer Since Date auto-fills to system date

**Verifies:** [BR-007](business-rules.md#br-007--customer-since-date-auto-filled)

**Given** a new New Customer wizard is opened on 2026-07-24
**When** the actor views Tab 1
**Then** Customer Since Date shows `2026-07-24` as a read-only Label

---

### AT-008 — Customer Status defaults to Active with defined values

**Verifies:** [BR-008](business-rules.md#br-008--customer-status-required-with-defined-values)

**Given** a new New Customer wizard is opened
**When** the actor views the Status dropdown on Tab 1
**Then** the default selected value is `चालू` (Active)
**And** the only other selectable values are `बंद`, `स्थगित`, `मृत`, `निलंबित`, `निवृत्त`, `वैद्यकीय`, `काढला`

---

### AT-009 — Date of Death hidden unless Status is Deceased

**Verifies:** [BR-009](business-rules.md#br-009--date-of-death-visible-only-when-status-is-deceased)

**Given** Tab 1 Status is `चालू` (Active)
**When** the actor views the form
**Then** Date of Death is not visible

**Given** the actor changes Status to `मृत` (Deceased)
**When** the form re-renders
**Then** Date of Death becomes visible and enterable

---

### AT-010 — Alert checkboxes do not trigger notifications

**Verifies:** [BR-010](business-rules.md#br-010--alert-checkboxes-are-preference-flags-only)

**Given** the actor checks Activate SMS Alert, Activate WhatsApp Alert, and Activate Email Alert on Tab 1 Advanced Settings
**When** the customer is saved
**Then** the preference flags are persisted
**And** no SMS, WhatsApp, or e-mail message is sent by the system

---

### AT-011 — Nominee section hidden until Add Nominee checked

**Verifies:** [BR-011](business-rules.md#br-011--nominee-section-conditional-on-add-nominee-checkbox)

**Given** Tab 1 Advanced Settings is expanded with Add Nominee unchecked
**When** the actor views the form
**Then** the Nominee Information section is not visible

**Given** the actor checks Add Nominee
**When** the form re-renders
**Then** the Nominee Information section becomes visible with fields #25–#31

---

### AT-012 — New Customer nominee section is single-entry, not a grid

**Verifies:** [BR-012](business-rules.md#br-012--new-customer-supports-at-most-one-nominee)

**Given** Add Nominee is checked on Tab 1
**When** the actor views the Nominee Information section
**Then** there is no Add/Remove row control or grid — only one set of nominee fields is presented

---

### AT-013 — Nominee required fields enforced

**Verifies:** [BR-013](business-rules.md#br-013--nominee-required-fields)

**Given** Add Nominee is checked and Nominee Name is left blank
**When** the actor clicks Next
**Then** the system blocks advancement with a validation error on Nominee Name

---

### AT-014 — Nominee Relation values match canonical Membership list

**Verifies:** [BR-014](business-rules.md#br-014--nominee-relation-reuses-canonical-membership-list)

**Given** Add Nominee is checked
**When** the actor opens the Relation dropdown
**Then** the options exactly match the canonical Relation list defined on New Membership Tab 3 (`मुलगा`, `पुतण्या`, `मुली`, `मुलगा - पती`, `पति व मुलगा`, `वरील प्रमाणे`, `बायको`, `मैत्रीण`, `केअरटेकर`, `लहान भाऊ`, `स्वतः`, `पत्नी`, `पती`)
**And** no additional Customer-specific Relation values are present

---

### AT-015 — Google Maps selection populates address fields

**Verifies:** [BR-015](business-rules.md#br-015--address-captured-via-google-maps-autocomplete), [BR-017](business-rules.md#br-017--required-address-sub-fields-from-google-maps)

**Given** Tab 2 is open
**When** the actor searches an address and selects a Google Maps place suggestion
**Then** Address/Building, Location, State, District, Taluka, and City fields populate from the place's `address_components`
**And** all populated fields remain editable

---

### AT-016 — Address Type required before Add

**Verifies:** [BR-016](business-rules.md#br-016--address-type-required)

**Given** Tab 2 has a resolved Google Maps address but Address Type left at `निवडा`
**When** the actor clicks Add (टाका +)
**Then** the system blocks the add with a validation error on Address Type

---

### AT-017 — Required address sub-fields block Add when missing

**Verifies:** [BR-017](business-rules.md#br-017--required-address-sub-fields-from-google-maps)

**Given** a resolved address is missing District (cleared by the actor)
**When** the actor clicks Add
**Then** the system blocks the add with a validation error on District

---

### AT-018 — Contact Same as Permanent copies address

**Verifies:** [BR-018](business-rules.md#br-018--contact-same-as-permanent-copies-address)

**Given** a Permanent (कायमचा) address row already exists in the grid
**When** the actor checks Contact Same as Permanent and confirms
**Then** a Contact (कॉन्टॅक्ट) address row is created with the same address values as the Permanent row
**And** the actor is not required to re-search the address via Google Maps

---

### AT-019 — Save succeeds without any KYC document uploaded

**Verifies:** [BR-019](business-rules.md#br-019--kyc-mandatory-documents-do-not-block-save), [UC-001](use-cases.md#uc-001--register-a-new-customer)

**Given** Tabs 1–2 are valid and no KYC document has been uploaded on Tab 3
**When** the actor clicks Complete/Save
**Then** the Customer record is created successfully
**And** the KYC document cards still display their `आवश्यक` (Mandatory) badges as a reminder for later upload

---

### AT-020 — Document Number only on Address/Identity Proof cards

**Verifies:** [BR-020](business-rules.md#br-020--document-number-required-only-for-address-and-identity-proof)

**Given** Tab 3 is open
**When** the actor views the Photo and Signature cards
**Then** neither shows a Document Number field
**And** the Address Proof and Identity Proof cards each show a Document Number field

---

### AT-021 — Wizard does not persist until final Complete/Save

**Verifies:** [BR-021](business-rules.md#br-021--new-customer-wizard-atomic-save-on-create), [WF-001](workflows.md#wf-001--new-customer-registration-wizard)

**Given** an actor is creating a new customer
**And** Tabs 1–2 have valid data entered
**When** the actor clicks Next (or Back) without clicking Complete/Save
**Then** no Customer record is persisted

**Given** the actor completes Tab 3 and clicks Complete/Save with Tabs 1–2 valid
**When** the save request completes
**Then** the Customer, its address(es), and any uploaded KYC metadata are persisted together

---

### AT-022 — View Only hides Save across Customer screens

**Verifies:** [BR-022](business-rules.md#br-022--customer-screens-use-master-permission-levels)

**Given** a User with View Only on New Customer
**When** the User opens New Customer
**Then** all fields across all tabs are read-only
**And** Complete/Save is not visible

---

### AT-023 — Customer List Show applies filters

**Verifies:** [BR-023](business-rules.md#br-023--customer-list-search-filter-and-export-standard)

**Given** the actor enters Customer Name `Patil` and leaves Status at default `चालू`
**When** the actor clicks Show
**Then** the grid displays only Active customers whose name matches `Patil`

---

### AT-024 — Customer List branch scoping (TODO)

**Verifies:** [BR-024](business-rules.md#br-024--customer-list-branch-scoped-results-eligibility)

**Given** an actor with branch rights limited to Branch 1 only
**And** customers exist in both Branch 1 and Branch 2
**When** the actor opens Customer List and clicks Show without a Branch filter
**Then** `TODO:` expected result set (Branch 1 only vs. all branches) is not yet confirmed — test to be finalized once [BR-024](business-rules.md#br-024--customer-list-branch-scoped-results-eligibility) is resolved

---

### AT-025 — Non-Individual Customer Type still requires person fields (TODO)

**Verifies:** [BR-025](business-rules.md#br-025--customer-type-does-not-alter-required-fields)

**Given** Customer Type is set to `एसजी` (Self Help Group)
**When** the actor leaves Date of Birth blank and clicks Next
**Then** `TODO:` current spec behaviour blocks Next (DOB required regardless of type) — confirm whether this is the intended business behaviour for non-Individual types

---

### AT-026 — Other Account requires an existing customer

**Verifies:** [BR-026](business-rules.md#br-026--customer-must-exist-before-other-account-can-be-opened), [UC-003](use-cases.md#uc-003--open-an-other-account-for-an-existing-customer)

**Given** the actor types a customer number with no matching Customer record into the Tab 1 Autocomplete
**When** the actor presses Enter
**Then** the system shows no match and does not resolve a customer
**And** the actor cannot proceed to select Account by Customer for a non-existent customer

---

### AT-027 — Account by Customer type required to open

**Verifies:** [BR-027](business-rules.md#br-027--account-by-customer-type-required-with-defined-values)

**Given** a Customer is resolved on Tab 1 and Account by Customer is left at `निवडा`
**When** the actor clicks Complete/Save
**Then** the system blocks the action with a validation error on Account by Customer

---

### AT-028 — Closed customers excluded from Other Account status filter (TODO)

**Verifies:** [BR-028](business-rules.md#br-028--other-account-customer-status-filter-inconsistency)

**Given** the actor opens the Tab 1 Status filter dropdown
**When** the actor views the available options
**Then** `बंद` (Closed) is absent from the list while present on Customer List/New Customer Status
**And** `TODO:` whether this is intentional (Closed customers cannot open Other Accounts) is unconfirmed

---

### AT-029 — Duplicate Other Account of same type (TODO)

**Verifies:** [BR-029](business-rules.md#br-029--duplicate-other-account-prevention)

**Given** Customer 661 already has an active `प्रवेश फी` (Entrance Fee) Other Account
**When** an actor attempts to open a second `प्रवेश फी` account for Customer 661
**Then** `TODO:` expected outcome (reject vs. allow) is not yet confirmed

---

### AT-030 — Other Account status independent of Customer status

**Verifies:** [BR-030](business-rules.md#br-030--other-account-registration-status-distinct-from-customer-status)

**Given** Customer 661 has Customer Status `चालू` (Active)
**And** Customer 661's Entrance Fee Other Account registration has status `बंद` (Closed)
**When** an administrator views Customer 661's Customer record
**Then** Customer Status still reads `चालू`
**And** the Other Account registration status remains independently `बंद`

---

### AT-031 — Registration List Show requires Branch, Account type, and Status

**Verifies:** [BR-031](business-rules.md#br-031--registration-list-filters-required)

**Given** Tab 2 has Account by Customer and Status selected but Branch left empty
**When** the actor clicks Show
**Then** the system blocks the search with a validation error on Select Branch

---

### AT-032 — Remove requires confirmation

**Verifies:** [BR-032](business-rules.md#br-032--bulk-remove-requires-confirmation)

**Given** the actor has selected two rows in the Registration List grid
**When** the actor clicks Remove (काढा)
**Then** a confirmation dialog appears before any row is deleted
**And** cancelling the dialog leaves both rows intact

---

### AT-033 — Account Status Update section requires row selection

**Verifies:** [BR-033](business-rules.md#br-033--account-status-update-visible-only-when-rows-selected)

**Given** zero rows are selected in the Registration List grid
**When** the actor views the screen
**Then** the Account Status (Update) section is not visible

**Given** the actor selects one row
**When** the form re-renders
**Then** the Account Status section becomes visible with Save and Revert actions

---

## Related Documents

- [overview.md](overview.md)
- [business-rules.md](business-rules.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [../../08-testing/](../../08-testing/) — future integration test plan (Phase 4)
