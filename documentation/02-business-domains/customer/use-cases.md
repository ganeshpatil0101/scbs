# Use Cases — Customer

## Purpose

Actor goals for the Customer module screens. Each use case references business rules by ID.

---

### UC-001 — Register a new customer

**Actors:** Clerk / Administrator (User with All Rights on New Customer form)

**Preconditions:**
1. Actor has All Rights on New Customer ([BR-022](business-rules.md#br-022--customer-screens-use-master-permission-levels)).
2. Branch master data exists for the branch Autocomplete.

**Main Flow:**
1. Actor opens **नवीन ग्राहक (New Customer)**.
2. **Tab 1 — ग्राहक तपशील (Customer Details):** Actor optionally selects Customer Type, enters PAN/Aadhaar (manual, no e-Verification), and completes Salutation, Name, Date of Birth, Occupation, Mobile Number, and Status (default Active). Branch defaults to the actor's branch but may be changed ([BR-003](business-rules.md#br-003--branch-defaults-to-logged-in-branch-editable)). Customer No., Age, and Customer Since Date are system-derived ([BR-001](business-rules.md#br-001--customer-number-auto-generated), [BR-005](business-rules.md#br-005--date-of-birth-required-age-auto-calculated), [BR-007](business-rules.md#br-007--customer-since-date-auto-filled)).
3. Optionally, actor expands **प्रगत सेटिंग्ज (Advanced Settings)** to enter Education/family names, activate alert preferences ([BR-010](business-rules.md#br-010--alert-checkboxes-are-preference-flags-only)), and check Add Nominee to capture a single nominee ([BR-011](business-rules.md#br-011--nominee-section-conditional-on-add-nominee-checkbox), [BR-012](business-rules.md#br-012--new-customer-supports-at-most-one-nominee), [BR-013](business-rules.md#br-013--nominee-required-fields), [BR-014](business-rules.md#br-014--nominee-relation-reuses-canonical-membership-list)).
4. Actor clicks **पुढे (Next)**.
5. **Tab 2 — पत्ता (Address):** Actor searches an address via Google Maps Places Autocomplete; the system parses the result into Address/Building, Road, Location, State, District, Taluka, City, Pin Code ([BR-015](business-rules.md#br-015--address-captured-via-google-maps-autocomplete), [BR-017](business-rules.md#br-017--required-address-sub-fields-from-google-maps)). Actor selects Address Type ([BR-016](business-rules.md#br-016--address-type-required)) and clicks **टाका + (Add)** to add the row to the address grid. Actor may check Contact Same as Permanent to copy the Permanent address into a Contact row ([BR-018](business-rules.md#br-018--contact-same-as-permanent-copies-address)).
6. Actor clicks **Next**.
7. **Tab 3 — केवायसी कागदपत्रे (KYC Documents):** Actor optionally uploads Photo, Signature, Address Proof, Identity Proof, and Original Aadhaar Photo document cards. Document Number is entered only for Address Proof and Identity Proof ([BR-020](business-rules.md#br-020--document-number-required-only-for-address-and-identity-proof)). Missing mandatory documents do not block Save ([BR-019](business-rules.md#br-019--kyc-mandatory-documents-do-not-block-save)).
8. Actor clicks **पूर्ण (Complete/Save)**. On create, this is the only persist point ([BR-021](business-rules.md#br-021--new-customer-wizard-atomic-save-on-create)).
9. System persists the Customer, its address(es), and any uploaded KYC document metadata.

**Alternative Flow:**
- **A1 — Back navigation:** On Tab 2–3, actor clicks **मागे (Back)**. Values entered on prior tabs remain in wizard state until Reset or a successful Save.
- **A2 — Deceased status:** Actor sets Status = `मृत` on Tab 1, which reveals Date of Death for entry ([BR-009](business-rules.md#br-009--date-of-death-visible-only-when-status-is-deceased)).
- **A3 — Multiple addresses:** Actor repeats the Search Address + Add flow on Tab 2 to add more than one address row (e.g. Permanent and Other).

**Exception Flow:**
- **E1 — Required field missing:** System blocks Next or Save and displays a validation message for the missing required field (e.g. Name, Date of Birth, Mobile Number, Address Type).
- **E2 — Google Maps no match:** Actor types an address with no matching place suggestion; actor must refine the search text before a place can be selected and parsed.
- **E3 — View Only permission:** Actor with View Only on New Customer can view all tabs but cannot Save ([BR-022](business-rules.md#br-022--customer-screens-use-master-permission-levels)).

**Post Conditions:**
1. A Customer record exists with a system-generated Customer No.
2. Zero or more Address rows exist for the Customer.
3. Zero or more KYC document metadata rows exist (upload may be deferred).
4. At most one Nominee record exists if Add Nominee was checked.

**Referenced Business Rules:** BR-001 through BR-021, BR-025

---

### UC-002 — Search and view customer list

**Actors:** Clerk / Cashier / Administrator (User with at least View Only on Customer List)

**Preconditions:**
1. Actor has View Only or All Rights on Customer List ([BR-022](business-rules.md#br-022--customer-screens-use-master-permission-levels)).

**Main Flow:**
1. Actor opens **ग्राहक यादी (Customer List)**.
2. Actor optionally enters Primary Search filters — Select Branch, Customer Name, Customer No. range, Status (default Active) ([BR-008](business-rules.md#br-008--customer-status-required-with-defined-values), [BR-024](business-rules.md#br-024--customer-list-branch-scoped-results-eligibility)).
3. Actor optionally expands **अॅडव्हान्स शोध (Advance Search)** and sets Masters Passing.
4. Actor clicks **दाखवा (Show)**.
5. System displays matching customers in the results grid with default identity/contact columns ([BR-023](business-rules.md#br-023--customer-list-search-filter-and-export-standard)).
6. Actor optionally clicks **तपशील (Details)** to view additional columns for a row, or **निर्यात करा (Export)** to export the current result set.

**Alternative Flow:**
- **A1 — No filters:** Actor clicks Show without entering any filter; system returns all customers the actor is entitled to see, subject to [BR-024](business-rules.md#br-024--customer-list-branch-scoped-results-eligibility) (TODO).

**Exception Flow:**
- **E1 — No Rights:** Actor with No Rights on Customer List cannot navigate to the screen ([BR-022](business-rules.md#br-022--customer-screens-use-master-permission-levels)).
- **E2 — No matches:** Grid displays an empty state when no customer matches the filters.

**Post Conditions:**
1. No data is modified — this is a read-only search use case.

**Referenced Business Rules:** BR-008, BR-022, BR-023, BR-024

---

### UC-003 — Open an Other Account for an existing customer

**Actors:** Clerk / Administrator (User with All Rights on Other Account Management)

**Preconditions:**
1. A Customer record already exists ([BR-026](business-rules.md#br-026--customer-must-exist-before-other-account-can-be-opened)) — created via [UC-001](#uc-001--register-a-new-customer).
2. Actor has All Rights on Other Account Management ([BR-022](business-rules.md#br-022--customer-screens-use-master-permission-levels)).

**Main Flow:**
1. Actor opens **इतर खाते व्यवस्थापन (Other Account Management)** — Tab 1 नवीन खाते (New Account).
2. Actor optionally selects Branch, then selects the Customer via Autocomplete ([BR-026](business-rules.md#br-026--customer-must-exist-before-other-account-can-be-opened)).
3. System displays the resolved customer's summary (Customer No., Name, Address, Mobile Number) read-only.
4. Actor selects Account by Customer type ([BR-027](business-rules.md#br-027--account-by-customer-type-required-with-defined-values)).
5. Actor clicks **पूर्ण / जतन करा (Complete/Save)**.
6. System opens the Other Account for the selected customer and account type.

**Alternative Flow:**
- **A1 — Refresh context:** Actor clicks **दाखवा (Show)** to re-resolve the customer context before completing.
- **A2 — Status-filtered lookup:** Actor sets the Status filter to narrow the Customer Autocomplete to customers in a given state ([BR-028](business-rules.md#br-028--other-account-customer-status-filter-inconsistency), TODO).

**Exception Flow:**
- **E1 — Customer not found:** Autocomplete returns no match; actor must register the person via New Customer first ([BR-026](business-rules.md#br-026--customer-must-exist-before-other-account-can-be-opened)).
- **E2 — Account type not selected:** System blocks Save when Account by Customer is left at placeholder `निवडा` ([BR-027](business-rules.md#br-027--account-by-customer-type-required-with-defined-values)).
- **E3 — Duplicate account:** Whether a second account of the same type for the same customer is rejected is [BR-029](business-rules.md#br-029--duplicate-other-account-prevention) (TODO).

**Post Conditions:**
1. An Other Account registration exists for the (Customer, Account by Customer type) pair, with its own registration status ([BR-030](business-rules.md#br-030--other-account-registration-status-distinct-from-customer-status)).

**Referenced Business Rules:** BR-022, BR-026, BR-027, BR-028, BR-029, BR-030

---

### UC-004 — Maintain Other Account registrations in bulk

**Actors:** Administrator (User with All Rights on Other Account Management)

**Preconditions:**
1. One or more Other Account registrations exist ([UC-003](#uc-003--open-an-other-account-for-an-existing-customer)).
2. Actor has All Rights on Other Account Management.

**Main Flow:**
1. Actor opens **इतर खाते व्यवस्थापन** — Tab 2 नोंदणी यादी (Registration List).
2. Actor sets required filters — Select Branch, Account by Customer, Status — and optional Customer No. range ([BR-031](business-rules.md#br-031--registration-list-filters-required)).
3. Actor clicks **दाखवा (Show)**.
4. System displays matching registrations in the results grid.
5. Actor selects one or more rows (or **सर्व निवडा** Select all).
6. **To update status:** the खाते स्थिती (Account Status) section appears ([BR-033](business-rules.md#br-033--account-status-update-visible-only-when-rows-selected)); actor selects a new status and clicks **जतन करा (Save)**.
7. **To remove:** actor clicks **काढा (Remove)**; system asks for confirmation before deleting the selected registration(s) ([BR-032](business-rules.md#br-032--bulk-remove-requires-confirmation)).

**Alternative Flow:**
- **A1 — Revert:** After selecting a new status but before Save, actor clicks **पूर्ववत (Revert)** to discard the pending change.

**Exception Flow:**
- **E1 — Missing required filter:** System blocks Show when Branch, Account by Customer, or Status is not selected ([BR-031](business-rules.md#br-031--registration-list-filters-required)).
- **E2 — No rows selected:** Account Status section stays hidden until at least one row is selected ([BR-033](business-rules.md#br-033--account-status-update-visible-only-when-rows-selected)).

**Post Conditions:**
1. Selected registrations have an updated status, or are removed from the registration list.

**Referenced Business Rules:** BR-030, BR-031, BR-032, BR-033

---

## Related Documents

- [overview.md](overview.md)
- [business-rules.md](business-rules.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [../../05-ui-ux/customer/customer-list-screen.md](../../05-ui-ux/customer/customer-list-screen.md)
- [../../05-ui-ux/customer/new-customer-screen.md](../../05-ui-ux/customer/new-customer-screen.md)
- [../../05-ui-ux/customer/other-account-management-screen.md](../../05-ui-ux/customer/other-account-management-screen.md)
