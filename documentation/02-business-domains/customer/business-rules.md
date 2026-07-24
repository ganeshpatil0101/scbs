# Business Rules — Customer

## Purpose

Numbered business rules for the Customer module: Customer List, New Customer (3-tab wizard), and Other Account Management (2 tabs). Every rule cites its UI spec source. Rules marked **TODO** require business confirmation before implementation.

**Sources:** [customer-list-screen.md](../../05-ui-ux/customer/customer-list-screen.md), [new-customer-screen.md](../../05-ui-ux/customer/new-customer-screen.md), [other-account-management-screen.md](../../05-ui-ux/customer/other-account-management-screen.md). Superseded specs (`new-other-account-screen.md`, `other-account-registration-screen.md`) are not used as sources — see [ux-optimization.md](../../05-ui-ux/customer/ux-optimization.md).

## Rule Index

| ID | Title | Type | Status |
| :--- | :--- | :--- | :---: |
| [BR-001](#br-001--customer-number-auto-generated) | Customer Number auto-generated | Workflow | Confirmed |
| [BR-002](#br-002--customer-type-optional-with-defined-values) | Customer Type optional with defined values | Validation | Confirmed |
| [BR-003](#br-003--branch-defaults-to-logged-in-branch-editable) | Branch defaults to logged-in branch, editable | Eligibility | Confirmed |
| [BR-004](#br-004--salutation-and-name-required) | Salutation and Name required | Validation | Confirmed |
| [BR-005](#br-005--date-of-birth-required-age-auto-calculated) | Date of Birth required; Age auto-calculated | Workflow | Confirmed |
| [BR-006](#br-006--mobile-number-required-one-per-customer) | Mobile Number required; one per customer | Validation | Confirmed |
| [BR-007](#br-007--customer-since-date-auto-filled) | Customer Since Date auto-filled | Workflow | Confirmed |
| [BR-008](#br-008--customer-status-required-with-defined-values) | Customer Status required with defined values | Validation | Confirmed |
| [BR-009](#br-009--date-of-death-visible-only-when-status-is-deceased) | Date of Death visible only when Status is Deceased | Eligibility | Confirmed |
| [BR-010](#br-010--alert-checkboxes-are-preference-flags-only) | Alert checkboxes are preference flags only | Cross-cutting | Confirmed |
| [BR-011](#br-011--nominee-section-conditional-on-add-nominee-checkbox) | Nominee section conditional on Add Nominee checkbox | Eligibility | Confirmed |
| [BR-012](#br-012--new-customer-supports-at-most-one-nominee) | New Customer supports at most one nominee | Eligibility | Confirmed |
| [BR-013](#br-013--nominee-required-fields) | Nominee required fields | Validation | Confirmed |
| [BR-014](#br-014--nominee-relation-reuses-canonical-membership-list) | Nominee Relation reuses canonical Membership list | Cross-cutting | Confirmed |
| [BR-015](#br-015--address-captured-via-google-maps-autocomplete) | Address captured via Google Maps Autocomplete | Workflow | Confirmed |
| [BR-016](#br-016--address-type-required) | Address Type required | Validation | Confirmed |
| [BR-017](#br-017--required-address-sub-fields-from-google-maps) | Required address sub-fields from Google Maps | Validation | Confirmed |
| [BR-018](#br-018--contact-same-as-permanent-copies-address) | Contact Same as Permanent copies address | Workflow | Confirmed |
| [BR-019](#br-019--kyc-mandatory-documents-do-not-block-save) | KYC mandatory documents do not block Save | Workflow | Confirmed |
| [BR-020](#br-020--document-number-required-only-for-address-and-identity-proof) | Document Number required only for Address and Identity Proof | Validation | Confirmed |
| [BR-021](#br-021--new-customer-wizard-atomic-save-on-create) | New Customer wizard atomic save on create | Workflow | Confirmed |
| [BR-022](#br-022--customer-screens-use-master-permission-levels) | Customer screens use Master permission levels | Cross-cutting | Confirmed |
| [BR-023](#br-023--customer-list-search-filter-and-export-standard) | Customer List search, filter, and export standard | Cross-cutting | Confirmed |
| [BR-024](#br-024--customer-list-branch-scoped-results-eligibility) | Customer List branch-scoped results eligibility | Eligibility | TODO |
| [BR-025](#br-025--customer-type-does-not-alter-required-fields) | Customer Type does not alter required fields | Eligibility | TODO |
| [BR-026](#br-026--customer-must-exist-before-other-account-can-be-opened) | Customer must exist before Other Account can be opened | Eligibility | Confirmed |
| [BR-027](#br-027--account-by-customer-type-required-with-defined-values) | Account by Customer type required with defined values | Validation | Confirmed |
| [BR-028](#br-028--other-account-customer-status-filter-inconsistency) | Other Account customer-status filter inconsistency | Eligibility | TODO |
| [BR-029](#br-029--duplicate-other-account-prevention) | Duplicate other-account prevention | Eligibility | TODO |
| [BR-030](#br-030--other-account-registration-status-distinct-from-customer-status) | Other Account registration status distinct from Customer status | Cross-cutting | Confirmed |
| [BR-031](#br-031--registration-list-filters-required) | Registration List filters required | Validation | Confirmed |
| [BR-032](#br-032--bulk-remove-requires-confirmation) | Bulk remove requires confirmation | Workflow | Confirmed |
| [BR-033](#br-033--account-status-update-visible-only-when-rows-selected) | Account Status Update visible only when rows selected | Eligibility | Confirmed |

---

## Rules

### BR-001 — Customer Number auto-generated

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [new-customer-screen.md](../../05-ui-ux/customer/new-customer-screen.md) — Tab 1, field #4 |

**Rule:** Customer No. (ग्राहक क्र.) is system-generated and displayed as a read-only Label. Staff must not enter or edit it. It is not a lookup field — excluded from the entity-autocomplete consolidation ([entity-autocomplete-pattern.md](../../05-ui-ux/shared/entity-autocomplete-pattern.md) Exclusions).

**Notes:** Generation algorithm (global sequence vs per-branch) is `TODO:` not yet documented — same open-item pattern as [settings/accounting BR-022](../settings/accounting/business-rules.md#br-022--gl-head-number-generation-algorithm) for GL Head numbers. The [Quick Add Customer](../../05-ui-ux/shared/quick-add-customer-pattern.md) popup (used from Nominee Autocompletes on deposit account screens) also auto-generates a Customer No. through this same rule when creating a minimal customer record.

---

### BR-002 — Customer Type optional with defined values

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-customer-screen.md](../../05-ui-ux/customer/new-customer-screen.md) — Tab 1, field #1 |

**Rule:** Customer Type (ग्राहक प्रकार) is optional (`Required: No` per spec). Allowed values: `वैयक्तिक` (Individual), `मालमत्ता फर्म` (Proprietorship Firm), `एसजी` (Self Help Group), `दुसरी संस्था` (Other Institution). No default value is specified in the spec.

**Notes:** See [BR-025](#br-025--customer-type-does-not-alter-required-fields) for the open question on whether non-Individual types should relax Individual-specific required fields.

---

### BR-003 — Branch defaults to logged-in branch, editable

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [new-customer-screen.md](../../05-ui-ux/customer/new-customer-screen.md) — Tab 1, field #5 |

**Rule:** Select Branch (शाखा निवडा) is required and defaults to the actor's logged-in branch. An administrator may pick a different branch via Autocomplete (`entityType: branch`) before Save.

**Notes:** The [Quick Add Customer](../../05-ui-ux/shared/quick-add-customer-pattern.md) popup does not expose this field — it silently sets Branch = the actor's session branch with no override, unlike the full New Customer screen.

---

### BR-004 — Salutation and Name required

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-customer-screen.md](../../05-ui-ux/customer/new-customer-screen.md) — Tab 1, fields #6–#7 |

**Rule:** Name (नाव — Surname-First-Middle) is required. Salutation (श्री. / सौ.) is optional with default `श्री.`; allowed values: `श्री.`, `सौ.`, `श्रीमती`, `कुमारी.`, `चि.`, `मेसर्स`, or blank.

---

### BR-005 — Date of Birth required; Age auto-calculated

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [new-customer-screen.md](../../05-ui-ux/customer/new-customer-screen.md) — Tab 1, fields #8–#10 |

**Rule:** Date of Birth (जन्म दिनांक) is required. Age (Years) and Age (Months) are read-only Labels auto-calculated from Date of Birth — the actor must not enter these directly.

---

### BR-006 — Mobile Number required; one per customer

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-customer-screen.md](../../05-ui-ux/customer/new-customer-screen.md) — Tab 1, fields #12–#13; UX consolidation 2026-07-09 |

**Rule:** Mobile Number is required; E-mail is optional. Both are captured **once per customer** on Tab 1 (ग्राहक माहिती), not per address row on Tab 2 — a customer with multiple addresses (Tab 2 grid) does not get separate mobile/e-mail values per address.

**Notes:** This consolidation is a confirmed UX decision (moved from the legacy Address tab) — see [ux-optimization.md](../../05-ui-ux/customer/ux-optimization.md). Downstream screens (Tab 2 Address grid) must not re-collect these fields.

---

### BR-007 — Customer Since Date auto-filled

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [new-customer-screen.md](../../05-ui-ux/customer/new-customer-screen.md) — Tab 1, field #14 |

**Rule:** Customer Since Date (ग्राहक झाल्याची दिनांक) is a read-only Label auto-filled with the system date at creation. The actor cannot edit it.

---

### BR-008 — Customer Status required with defined values

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-customer-screen.md](../../05-ui-ux/customer/new-customer-screen.md) — Tab 1, field #15; [customer-list-screen.md](../../05-ui-ux/customer/customer-list-screen.md) — field #5 |

**Rule:** Customer Status (स्थिती) is required. Default at creation is `चालू` (Active). Allowed values: `चालू`, `बंद`, `स्थगित`, `मृत`, `निलंबित`, `निवृत्त`, `वैद्यकीय`, `काढला` — the same 8-value list is used on New Customer and as the Customer List filter.

**Notes:** This is the **Customer**-level status. It is a distinct value domain from the **Other Account** status used on [other-account-management-screen.md](../../05-ui-ux/customer/other-account-management-screen.md) Tab 2 (`चालू`, `बंद`, `स्थगित` only — see [BR-030](#br-030--other-account-registration-status-distinct-from-customer-status)). Implementations must not merge these into one status enum.

---

### BR-009 — Date of Death visible only when Status is Deceased

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [new-customer-screen.md](../../05-ui-ux/customer/new-customer-screen.md) — Tab 1, field #16; UX consolidation 2026-07-09 |

**Rule:** Date of Death (देहावसान तारीख) is visible and enterable only when Customer Status (#15) equals `मृत` (Deceased). For every other Status value, the field is hidden and must not be persisted.

---

### BR-010 — Alert checkboxes are preference flags only

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | Confirmed |
| Source | [new-customer-screen.md](../../05-ui-ux/customer/new-customer-screen.md) — Tab 1 Advanced, fields #21–#23; [system-boundaries.md](../../00-project-overview/system-boundaries.md) — SMS/WhatsApp Gateway |

**Rule:** Activate SMS Alert, Activate WhatsApp Alert, and Activate Email Alert are optional checkboxes that persist a **preference flag only**. No SMS, WhatsApp, or e-mail gateway integration exists in v1 — checking these fields does not trigger any outbound notification.

---

### BR-011 — Nominee section conditional on Add Nominee checkbox

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [new-customer-screen.md](../../05-ui-ux/customer/new-customer-screen.md) — Tab 1 Advanced, field #24 |

**Rule:** The वारसदार माहिती (Nominee Information) section (fields #25–#31) is visible only when Add Nominee (वारसदार टाका) is checked. When unchecked, the section is hidden and no nominee data is persisted.

---

### BR-012 — New Customer supports at most one nominee

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [new-customer-screen.md](../../05-ui-ux/customer/new-customer-screen.md) — Tab 1, वारसदार माहिती section note |

**Rule:** The New Customer Nominee section is a **single compact form**, not a grid — it captures at most one nominee per customer. Multiple-nominee capture (with Add/Remove grid rows) is out of scope for this screen and remains on product account-opening screens using the shared `app-nominee-form` / `app-nominee-grid` pattern.

---

### BR-013 — Nominee required fields

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-customer-screen.md](../../05-ui-ux/customer/new-customer-screen.md) — Tab 1, fields #25–#28 |

**Rule:** When the Nominee section is shown ([BR-011](#br-011--nominee-section-conditional-on-add-nominee-checkbox)), Salutation, Name, and Relation are required. Date of Birth, Mobile Number, Nominee Percentage, and Address (fields #27, #29–#31) are optional. Salutation allowed values match customer Salutation ([BR-004](#br-004--salutation-and-name-required)).

---

### BR-014 — Nominee Relation reuses canonical Membership list

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | Confirmed |
| Source | [new-customer-screen.md](../../05-ui-ux/customer/new-customer-screen.md) — Tab 1, field #28; [new-membership-screen.md](../../05-ui-ux/membership/new-membership-screen.md) — Tab 3, field #19 |

**Rule:** Nominee Relation (नाते) values must come from the single **canonical Relation list** finalized on the Membership module's New Membership Tab 3 (`मुलगा`, `पुतण्या`, `मुली`, `मुलगा - पती`, `पति व मुलगा`, `वरील प्रमाणे`, `बायको`, `मैत्रीण`, `केअरटेकर`, `लहान भाऊ`, `स्वतः`, `पत्नी`, `पती`) — the same list reused by FD/Savings/Daily/Recurring/Loan nominee screens. Do not maintain a separate Relation list for Customer.

**Notes:** Cross-domain dependency — the Membership operational domain (`02-business-domains/membership/`) is not yet documented (Phase 3); this list currently exists only in the UI spec. When Membership's business-rules.md is authored, migrate this canonical definition there and update this cross-reference.

---

### BR-015 — Address captured via Google Maps Autocomplete

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [new-customer-screen.md](../../05-ui-ux/customer/new-customer-screen.md) — Tab 2, field #1 and Google `address_component` mapping table |

**Rule:** The primary address input is a **Google Maps Places Autocomplete** field (Search Address). On place selection, `address_components`/`formatted_address` populate Address/Building, Road, Location, State, District, Taluka, City, and Pin Code. The CBS platform does **not** maintain its own master lists for State, District, Taluka, or City — these are external, Google-sourced values, editable after auto-fill.

**Notes:** This is an external third-party API dependency (Google Maps JavaScript/Places API), distinct from every other Autocomplete in the platform which resolves against internal master data ([entity-autocomplete-pattern.md](../../05-ui-ux/shared/entity-autocomplete-pattern.md)). Requires an API key/billing configuration — not yet tracked in [architecture-overview.md](../../01-architecture/architecture-overview.md).

---

### BR-016 — Address Type required

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-customer-screen.md](../../05-ui-ux/customer/new-customer-screen.md) — Tab 2, field #2 |

**Rule:** Address Type (पत्त्याचा प्रकार) is required. Allowed values: `कायमचा` (Permanent), `कॉन्टॅक्ट` (Contact), `इतर` (Other).

---

### BR-017 — Required address sub-fields from Google Maps

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-customer-screen.md](../../05-ui-ux/customer/new-customer-screen.md) — Tab 2, fields #3, #6–#9 |

**Rule:** Address/Building/Flat/House No., Location, State, District, and Taluka are required after Google Maps auto-fill (editable). Road, Landmark, City, Pin Code, and Telephone Number (fields #4–#5, #10–#12) are optional.

**Notes:** City (#10) is listed `Required: Yes` in the field table header context of the address block per spec row — confirmed required alongside the four above based on the spec's `Required` column.

---

### BR-018 — Contact Same as Permanent copies address

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [new-customer-screen.md](../../05-ui-ux/customer/new-customer-screen.md) — Tab 2, field #13 |

**Rule:** When Contact Same as Permanent (संपर्क व कायमचा पत्ते सारखेच आहेत) is checked, the system copies the Permanent (कायमचा) address values into a Contact (कॉन्टॅक्ट) address row rather than requiring the actor to re-enter or re-search the same address via Google Maps.

**Notes:** Exact behaviour if no Permanent address exists yet when the checkbox is checked is `TODO:` not specified — implementation should disable the checkbox until a Permanent address row exists, or confirm with business.

---

### BR-019 — KYC mandatory documents do not block Save

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [new-customer-screen.md](../../05-ui-ux/customer/new-customer-screen.md) — Tab 3; Standing Decision 2026-07-24 |

**Rule:** Photo, Signature, Address Proof, and Identity Proof are marked `आवश्यक` (Mandatory) on the KYC Documents tab, but this is a **UI reminder only**. Save/Complete on New Customer is **not blocked** by missing mandatory KYC document uploads. Original Aadhaar Photo remains optional in all cases. Documents may be uploaded later via customer edit.

**Notes:** Standing decision confirmed 2026-07-24 — matches the "document cards" UX pattern (no enforced grid/checklist gate).

---

### BR-020 — Document Number required only for Address and Identity Proof

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-customer-screen.md](../../05-ui-ux/customer/new-customer-screen.md) — Tab 3, Documents table |

**Rule:** The Document Number (दस्तावेज क्रमांक) field appears only on the Address Proof and Identity Proof cards. It must not appear on Photo, Signature, or Original Aadhaar Photo cards. When present and a file is uploaded, Document Number is not separately marked required in the spec — treat as optional unless a value is entered, in which case format validation is `TODO:` not specified.

---

### BR-021 — New Customer wizard atomic save on create

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | Standing Decision 2026-07-24; [new-customer-screen.md](../../05-ui-ux/customer/new-customer-screen.md) — Tabs 1–3 |

**Rule:** On create, New Customer persists Customer, Address(es), and KYC document metadata only when the actor clicks **Complete/Save** (पूर्ण) after all three tabs pass their field validations. **Next** (पुढे) and **Back** (मागे) between tabs must not write partial records. **Reset**/**पूर्ववत** clears wizard state without persisting.

**Notes:** Matches the atomic-save pattern already confirmed for Staff & System Access ([settings/master BR-019](../settings/master/business-rules.md#br-019--staff-access-wizard-atomic-save-on-create)), New Scheme ([settings/schemes BR-013](../schemes/business-rules.md#br-013--scheme-wizard-atomic-save-on-create)), and GL Account Setup ([settings/accounting BR-002](../settings/accounting/business-rules.md#br-002--gl-setup-atomic-save-on-create)). Save is not blocked by missing KYC uploads ([BR-019](#br-019--kyc-mandatory-documents-do-not-block-save)) — only by field-level validation failures on Tabs 1–2.

---

### BR-022 — Customer screens use Master permission levels

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | Confirmed |
| Source | [settings/master/business-rules.md](../settings/master/business-rules.md#br-017--permission-levels-are-all-rights--view-only--no-rights) BR-017 |

**Rule:** Access to Customer List, New Customer, and Other Account Management follows Master permission levels: **All Rights** (full edit/save), **View Only** (read-only; Save/Complete/Remove hidden), **No Rights** (navigation blocked). Do not redefine permission semantics in this domain.

---

### BR-023 — Customer List search, filter, and export standard

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | Confirmed |
| Source | [customer-list-screen.md](../../05-ui-ux/customer/customer-list-screen.md); [business-goals.md](../../00-project-overview/business-goals.md) BG-005 |

**Rule:** Customer List implements the platform-wide interactive reporting standard (BG-005): Primary Search filters, an expandable Advance Search section, a results grid with Details/Export actions, and additional columns available via Details/Export/column picker rather than shown by default.

---

### BR-024 — Customer List branch-scoped results eligibility

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | TODO |
| Source | [customer-list-screen.md](../../05-ui-ux/customer/customer-list-screen.md) — field #1; [system-boundaries.md](../../00-project-overview/system-boundaries.md) — "Branch-scoped data access where configured" |

**Rule:** `TODO:` Confirm whether Customer List results default to only the branches the logged-in actor has rights to (per [settings/master branch rights](../settings/master/business-rules.md#br-013--organization-and-branch-required-for-rights-row)), with the Select Branch filter narrowing further — or whether results are organization-wide by default with Branch as a pure optional filter and no row-level branch restriction.

---

### BR-025 — Customer Type does not alter required fields

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | TODO |
| Source | [new-customer-screen.md](../../05-ui-ux/customer/new-customer-screen.md) — Tab 1, field #1 vs. fields #6–#10 |

**Rule:** `TODO:` The spec shows one flat Tab 1 form regardless of Customer Type ([BR-002](#br-002--customer-type-optional-with-defined-values)) — Salutation, Date of Birth, and Age remain present and required the same way for Individual and non-Individual types (Proprietorship Firm, Self Help Group, Other Institution). Confirm with business whether non-Individual customer types should hide/relax person-specific fields (Salutation, DOB, Age) or whether the current uniform behaviour is intentional for Year 1.

---

### BR-026 — Customer must exist before Other Account can be opened

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [other-account-management-screen.md](../../05-ui-ux/customer/other-account-management-screen.md) — Tab 1, field #2 |

**Rule:** Other Account Management Tab 1 requires selecting an **existing** Customer via Autocomplete (`entityType: customer`). The screen must not create a new Customer identity — a person must first be registered via New Customer ([BR-001](#br-001--customer-number-auto-generated) through [BR-021](#br-021--new-customer-wizard-atomic-save-on-create)) before an Other Account can be opened for them.

**Notes:** Cross-screen dependency, same shape as [settings/master BR-001](../settings/master/business-rules.md#br-001--customer-required-for-staff-registration) (Staff registration also requires an existing Customer).

---

### BR-027 — Account by Customer type required with defined values

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [other-account-management-screen.md](../../05-ui-ux/customer/other-account-management-screen.md) — Tab 1, field #3; Tab 2, field #10 |

**Rule:** Account by Customer (ग्राहकानुसार खाते) is required on both Tab 1 (opening) and Tab 2 (filtering). Allowed values on both tabs: `ब वर्ग देणे लाभांश` (Class B Dividend Payable), `अनामत खाते` (Deposit Account), `प्रवेश फी` (Entrance Fee), `नोकर पगार खर्च` (Staff Salary Expense). Placeholder `निवडा` is not a valid saved/filter value.

**Notes:** `ब वर्ग देणे लाभांश` relates to the Nominal Member / Class B membership category — see [glossary.md](../../00-project-overview/glossary.md) Nominal Member, Class B Member. Which GL Head each account type posts to is configured in Settings → Accounting, not on this screen; that GL linkage is `TODO:` not documented (no field on this spec exposes it).

---

### BR-028 — Other Account customer-status filter inconsistency

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | TODO |
| Source | [other-account-management-screen.md](../../05-ui-ux/customer/other-account-management-screen.md) — Tab 1, field #4; compare [BR-008](#br-008--customer-status-required-with-defined-values) |

**Rule:** `TODO:` Tab 1's Status filter (`सर्व`, `चालू`, `स्थगित`, `मृत`, `निलंबित`, `निवृत्त`, `वैद्यकीय`, `काढला`) omits `बंद` (Closed) — the only value present in the full 8-value Customer Status list ([BR-008](#br-008--customer-status-required-with-defined-values)) that is missing here. Confirm with business whether: (a) Closed customers are intentionally ineligible to open Other Accounts, so `बंद` should never appear even under `सर्व`; or (b) this is a spec gap and `बंद` should be added. Do not assume either answer.

---

### BR-029 — Duplicate other-account prevention

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | TODO |
| Source | [other-account-management-screen.md](../../05-ui-ux/customer/other-account-management-screen.md) — Tab 1 |

**Rule:** `TODO:` The spec does not state whether a customer may hold more than one Other Account of the **same** Account by Customer type (e.g., two `प्रवेश फी` accounts). Confirm whether Save/Complete on Tab 1 should reject opening a duplicate (customer, account type) combination or whether multiple are allowed.

---

### BR-030 — Other Account registration status distinct from Customer status

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | Confirmed |
| Source | [other-account-management-screen.md](../../05-ui-ux/customer/other-account-management-screen.md) — Tab 2, fields #11, #14; compare [BR-008](#br-008--customer-status-required-with-defined-values) |

**Rule:** The Other Account **registration status** used on Tab 2 (Registration List filter field #11, and Account Status Update field #14) has exactly three values — `चालू` (Active), `बंद` (Closed), `स्थगित` (Suspended) — and applies to the **account registration**, not the underlying Customer. It is a separate value domain from Customer Status ([BR-008](#br-008--customer-status-required-with-defined-values)); a Customer can remain `चालू` while an individual Other Account registration is set to `बंद`, and vice versa. Implementations must model these as two distinct status columns/enums.

---

### BR-031 — Registration List filters required

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [other-account-management-screen.md](../../05-ui-ux/customer/other-account-management-screen.md) — Tab 2, fields #9–#11 |

**Rule:** On Tab 2 (नोंदणी यादी), Select Branch, Account by Customer, and Status are required before running Show (दाखवा). Customer No. (From/To) range fields (#12–#13) are optional narrowing filters.

---

### BR-032 — Bulk remove requires confirmation

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [other-account-management-screen.md](../../05-ui-ux/customer/other-account-management-screen.md) — Tab 2, Results Grid action |

**Rule:** Remove (काढा) on the Registration List grid deletes the selected registration row(s) only after the actor confirms a confirmation dialog. `सर्व निवडा` (Select all) may pre-select every visible row before Remove.

---

### BR-033 — Account Status Update visible only when rows selected

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [other-account-management-screen.md](../../05-ui-ux/customer/other-account-management-screen.md) — Tab 2, Account Status section |

**Rule:** The खाते स्थिती (Account Status — Update) section is visible only when one or more grid rows are selected. Save (जतन करा) applies the selected status ([BR-030](#br-030--other-account-registration-status-distinct-from-customer-status)) to every selected row; Revert (पूर्ववत) discards the pending status change without saving.

---

## Related Documents

- [overview.md](overview.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [../../05-ui-ux/customer/customer-list-screen.md](../../05-ui-ux/customer/customer-list-screen.md)
- [../../05-ui-ux/customer/new-customer-screen.md](../../05-ui-ux/customer/new-customer-screen.md)
- [../../05-ui-ux/customer/other-account-management-screen.md](../../05-ui-ux/customer/other-account-management-screen.md)
- [../settings/master/business-rules.md](../settings/master/business-rules.md)
- [../../00-project-overview/glossary.md](../../00-project-overview/glossary.md)
