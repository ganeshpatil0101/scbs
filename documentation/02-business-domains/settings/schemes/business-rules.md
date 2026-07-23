# Business Rules — Settings / Schemes

## Purpose

Numbered business rules for the unified New Scheme wizard. Every rule cites its UI spec source. Rules marked **TODO** require business confirmation before implementation.

**Primary source:** [new-scheme-screen.md](../../05-ui-ux/settings/schemes/new-scheme-screen.md). Type-specific field details use superseded product specs as **field reference only** (Approach B, confirmed 2026-07-23).

## Rule Index

| ID | Title | Type | Status |
| :--- | :--- | :--- | :---: |
| [BR-001](#br-001--scheme-type-required) | Scheme Type required | Validation | Confirmed |
| [BR-002](#br-002--scheme-type-change-resets-wizard) | Scheme Type change resets wizard | Workflow | Confirmed |
| [BR-003](#br-003--tab-visibility-by-scheme-type) | Tab visibility by Scheme Type | Eligibility | Confirmed |
| [BR-004](#br-004--gl-head-required-from-gl-master) | GL Head required from GL master | Eligibility | Confirmed |
| [BR-005](#br-005--daily-scheme-gl-head-number--99) | Daily scheme GL Head number ≤ 99 | Validation | Confirmed |
| [BR-006](#br-006--multiple-schemes-may-share-one-gl-head) | Multiple schemes may share one GL Head | Eligibility | Confirmed |
| [BR-007](#br-007--scheme-name-required) | Scheme Name required | Validation | Confirmed |
| [BR-008](#br-008--scheme-name-unique-within-scheme-type) | Scheme Name unique within Scheme Type | Validation | Confirmed |
| [BR-009](#br-009--scheme-status-required-with-defined-values) | Scheme Status required with defined values | Validation | Confirmed |
| [BR-010](#br-010--allow-only-members-optional) | Allow Only Members optional | Eligibility | Confirmed |
| [BR-011](#br-011--interest-posting-day-and-month-on-add) | Interest Posting day and month on Add | Validation | Confirmed |
| [BR-012](#br-012--shared-charge-types) | Shared charge types | Validation | Confirmed |
| [BR-013](#br-013--scheme-wizard-atomic-save-on-create) | Scheme wizard atomic save on create | Workflow | Confirmed |
| [BR-014](#br-014--new-scheme-form-uses-master-permission-levels) | New Scheme form uses Master permission levels | Cross-cutting | Confirmed |
| [BR-015](#br-015--savings-product-subtype-and-interest-rate-required) | Savings product subtype and interest rate required | Validation | Confirmed |
| [BR-016](#br-016--savings-interest-calculation-mode) | Savings interest calculation mode | Validation | Confirmed |
| [BR-017](#br-017--open-ended-and-close-ended-mutually-exclusive) | Open Ended and Close Ended mutually exclusive | Validation | Confirmed |
| [BR-018](#br-018--compound-frequency-when-compound-interest) | Compound frequency when Compound Interest | Eligibility | Confirmed |
| [BR-019](#br-019--daily-calculation-day-required) | Daily Calculation Day required | Validation | Confirmed |
| [BR-020](#br-020--duration-and-rates-row-required-fields) | Duration & Rates row required fields | Validation | Confirmed |
| [BR-021](#br-021--account-closing-tab-deposit-types-only) | Account Closing tab — deposit types only | Eligibility | Confirmed |
| [BR-022](#br-022--fd-required-identity-fields) | FD required identity fields | Validation | Confirmed |
| [BR-023](#br-023--fd-auto-renewal-dependent-fields) | FD Auto Renewal dependent fields | Eligibility | Confirmed |
| [BR-024](#br-024--fd-benefits-on-duration-tab-only) | FD Benefits on Duration tab only | Workflow | Confirmed |
| [BR-025](#br-025--recurring-duration-row-includes-agent-rate) | Recurring duration row includes agent rate | Validation | Confirmed |
| [BR-026](#br-026--recurring-salary-and-rebate-under-advanced) | Recurring Salary and Rebate under Advanced | Workflow | Confirmed |
| [BR-027](#br-027--loan-type-required) | Loan Type required | Validation | Confirmed |
| [BR-028](#br-028--credit-card-billing-cycle-day-conditional) | Credit Card billing cycle day conditional | Eligibility | Confirmed |
| [BR-029](#br-029--loan-deposit-account-mandatory-enables-fields) | Loan deposit account mandatory enables fields | Eligibility | Confirmed |
| [BR-030](#br-030--loan-duration-row-required-fields) | Loan duration row required fields | Validation | Confirmed |
| [BR-031](#br-031--loan-guarantor-total-is-sum) | Loan guarantor total is sum | Validation | Confirmed |
| [BR-032](#br-032--loan-charges-deduction-or-fee-mode) | Loan charges Deduction or Fee mode | Validation | Confirmed |
| [BR-033](#br-033--scheme-status-account-opening-eligibility) | Scheme Status account-opening eligibility | Eligibility | TODO |
| [BR-034](#br-034--minimum-grid-rows-on-save) | Minimum grid rows on Save | Eligibility | TODO |

---

## Rules

### BR-001 — Scheme Type required

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-scheme-screen.md](../../05-ui-ux/settings/schemes/new-scheme-screen.md) — Scheme Type Selector, field #1 |

**Rule:** Scheme Type (योजना प्रकार) is required before the wizard can proceed. Allowed values: `बचत` (Savings), `डेली` (Daily), `मुदत ठेव` (FD), `रिकरिंग` (Recurring), `कर्ज` (Loan).

---

### BR-002 — Scheme Type change resets wizard

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [new-scheme-screen.md](../../05-ui-ux/settings/schemes/new-scheme-screen.md) — Scheme Type Selector |

**Rule:** Changing Scheme Type resets the wizard to Tab 1 (Scheme Info) and replaces the visible tab set with the set defined for the newly selected type ([BR-003](#br-003--tab-visibility-by-scheme-type)). Previously entered values for the prior type are discarded from the wizard state.

---

### BR-003 — Tab visibility by Scheme Type

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [new-scheme-screen.md](../../05-ui-ux/settings/schemes/new-scheme-screen.md) — Tab Visibility Matrix |

**Rule:** Only the tabs marked for the selected Scheme Type are shown:

| Tab | Savings | Daily | FD | Recurring | Loan |
| :--- | :---: | :---: | :---: | :---: | :---: |
| Scheme Info | ✓ | ✓ | ✓ | ✓ | ✓ |
| Duration & Rates | — | ✓ | ✓ | ✓ | ✓ |
| Interest Posting | ✓ | ✓ | ✓ | ✓ | ✓ |
| Account Closing | — | ✓ | ✓ | ✓ | — |
| Charges | ✓ | ✓ | ✓ | ✓ | ✓ |
| Loan Specific | — | — | — | — | ✓ |
| Advanced | — | — | ✓ | ✓ | ✓ |

Hidden tabs contribute no persisted data for that scheme.

---

### BR-004 — GL Head required from GL master

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [new-scheme-screen.md](../../05-ui-ux/settings/schemes/new-scheme-screen.md) — Tab 1, field #2 |

**Rule:** Each scheme must bind to exactly one existing **GL Head** selected via Autocomplete (`entityType: gl`). The system must not invent or auto-generate a GL Head from this screen. Options load from the GL master created via Settings → Accounting → GL Account Setup.

**Notes:** Lookup pattern: [entity-autocomplete-pattern.md](../../05-ui-ux/shared/entity-autocomplete-pattern.md).

---

### BR-005 — Daily scheme GL Head number ≤ 99

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-scheme-screen.md](../../05-ui-ux/settings/schemes/new-scheme-screen.md) — Tab 1, field #2 (Daily note); field-reference [daily-new-scheme-screen.md](../../05-ui-ux/settings/schemes/daily-new-scheme-screen.md) Tab 1 #1 |

**Rule:** When Scheme Type is `डेली` (Daily), the selected GL Head number must be less than or equal to **99**. Resolve/validate on Autocomplete selection or Save. Reject with the validation message equivalent to: enter a GL Head number ≤ 99.

---

### BR-006 — Multiple schemes may share one GL Head

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | Standing Decision 2026-07-23; [new-scheme-screen.md](../../05-ui-ux/settings/schemes/new-scheme-screen.md) — Tab 1 (one GL per scheme) |

**Rule:** A single GL Head may be linked to more than one scheme within the tenant. Each scheme still references exactly one GL Head ([BR-004](#br-004--gl-head-required-from-gl-master)).

---

### BR-007 — Scheme Name required

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-scheme-screen.md](../../05-ui-ux/settings/schemes/new-scheme-screen.md) — Tab 1, field #3 |

**Rule:** Scheme Name (योजनेचे नाव / योजना नाव) is required and must be non-blank after trim.

---

### BR-008 — Scheme Name unique within Scheme Type

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | Standing Decision 2026-07-23; [new-scheme-screen.md](../../05-ui-ux/settings/schemes/new-scheme-screen.md) — Tab 1, field #3 |

**Rule:** Scheme Name must be unique within the same Scheme Type inside the tenant. The same name may exist for a different Scheme Type. On edit, uniqueness excludes the scheme being edited.

---

### BR-009 — Scheme Status required with defined values

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-scheme-screen.md](../../05-ui-ux/settings/schemes/new-scheme-screen.md) — Tab 1, field #4 |

**Rule:** Status (स्थिती) is required. Allowed values for all types: `चालू`, `बंद`, `स्थगित`. When Scheme Type is Daily, `कालबाह्य` is also allowed.

**Notes:** Effect of each status on account opening is [BR-033](#br-033--scheme-status-account-opening-eligibility) (TODO).

---

### BR-010 — Allow Only Members optional

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [new-scheme-screen.md](../../05-ui-ux/settings/schemes/new-scheme-screen.md) — Tab 1, field #5 |

**Rule:** Allow Only Members (फक्त सदस्यांना परवानगी द्या) is optional on all scheme types. When checked and persisted, operational account-opening for that scheme must require the account holder to be a **Member**. When unchecked, Member status is not required by this flag.

---

### BR-011 — Interest Posting day and month on Add

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-scheme-screen.md](../../05-ui-ux/settings/schemes/new-scheme-screen.md) — Tab Interest Posting (`app-interest-posting-grid`) |

**Rule:** To add an interest posting row, Interest Posting Day must be an integer **1–31** and Interest Posting Month must be a selected calendar month. Placeholder `निवडा` is not a valid add value. Added rows appear in the posting grid and may be removed.

**Notes:** Whether ≥1 posting row is mandatory on Save is [BR-034](#br-034--minimum-grid-rows-on-save) (TODO).

---

### BR-012 — Shared charge types

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-scheme-screen.md](../../05-ui-ux/settings/schemes/new-scheme-screen.md) — Tab Charges |

**Rule:** Charge selections use `app-charges-select`. Allowed charge names for all scheme types:

| Marathi | English |
| :--- | :--- |
| कर्जदार कल्याण निधी | Borrower Welfare Fund |
| पिग्मी कमिशन | Pigmy Commission |
| प्रोसेसिंग फी | Processing Fee |
| ब वर्ग सभासद फी | Class B Member Fee |
| स्टेशनरी फी | Stationery Fee |

Placeholder `निवडा` is not persisted as a charge. Charges are optional unless loan Fee/Deduction grid validation requires a selected name when adding a loan charge row ([BR-032](#br-032--loan-charges-deduction-or-fee-mode)).

---

### BR-013 — Scheme wizard atomic save on create

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | Standing Decision 2026-07-23; [new-scheme-screen.md](../../05-ui-ux/settings/schemes/new-scheme-screen.md) — Actions |

**Rule:** On create, the scheme and all related grids persist only when the actor clicks **Complete / Save** (पूर्ण / जतन करा) after all visible tabs for the selected Scheme Type are valid. **Next** (पुढे) and **Back** (मागे) must not write partial scheme records. **Reset** (पूर्ववत / रीसेट) clears wizard state without persisting.

---

### BR-014 — New Scheme form uses Master permission levels

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | Confirmed |
| Source | [settings/master/business-rules.md](../master/business-rules.md) BR-017; New Scheme form in default role matrix |

**Rule:** Access to New Scheme follows Master permission levels: **All Rights** (full edit/save), **View Only** (read-only; Save hidden), **No Rights** (navigation blocked). Do not redefine permission levels in this sub-area.

---

### BR-015 — Savings product subtype and interest rate required

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-scheme-screen.md](../../05-ui-ux/settings/schemes/new-scheme-screen.md) — Tab 1 type-specific; field-reference [savings-new-scheme-screen.md](../../05-ui-ux/settings/schemes/savings-new-scheme-screen.md) Tab 1 #3–#4 |

**Rule:** When Scheme Type is Savings, product subtype (योजनेचे प्रकार) is required. Allowed values: `कायम ठेव`, `सेव्हिंग`, `करंट`, `लवचिक ठेव` (placeholder `निवडा` invalid). Interest Rate (p.a. %) is required.

---

### BR-016 — Savings interest calculation mode

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | Field-reference [savings-new-scheme-screen.md](../../05-ui-ux/settings/schemes/savings-new-scheme-screen.md) — Interest Calculation section |

**Rule:** When Scheme Type is Savings, exactly one interest calculation mode must be selected: **In Days** (दिवसात) or **In Months** (महिन्यात). Default is In Days. When In Months is selected, Start of Month (महिन्याची सुरुवात) day **1–31** is required. When In Days is selected, Start of Month is not applicable and must not be required.

---

### BR-017 — Open Ended and Close Ended mutually exclusive

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | Field-reference Daily/FD/Recurring Tab 1 Open Ended / Close Ended radios |

**Rule:** When Scheme Type is Daily, FD, or Recurring, Open Ended (ओपन एंडेड) and Close Ended (क्लोज एंडेड) are mutually exclusive. At most one may be selected; default is Open Ended.

---

### BR-018 — Compound frequency when Compound Interest

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | Field-reference Daily/FD/Recurring Interest Type sections; [new-scheme-screen.md](../../05-ui-ux/settings/schemes/new-scheme-screen.md) Tab 1 type-specific |

**Rule:** When Interest Type is **Compound Interest** (चक्रवाढ व्याज), a compound frequency must be selectable from: Monthly, Quarterly, Half-Yearly, Yearly (labels per product spec). When Interest Type is **Simple Interest** (सरळ व्याज), compound frequency controls are not applicable (hidden or disabled) and are not persisted as active compound settings.

---

### BR-019 — Daily Calculation Day required

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | Field-reference [daily-new-scheme-screen.md](../../05-ui-ux/settings/schemes/daily-new-scheme-screen.md) Tab 1 #15 |

**Rule:** When Scheme Type is Daily, Calculation Day (गणना दिवस) is required and must be an integer **1–31**.

**Notes:** Spec footer note: week for debit-limit fields is Sunday–Saturday — persist as documented behaviour when those optional limit fields are used.

---

### BR-020 — Duration & Rates row required fields

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-scheme-screen.md](../../05-ui-ux/settings/schemes/new-scheme-screen.md) — Tab Duration & Rates (`app-rate-duration-grid`); field-reference per product Tab 2 |

**Rule:** When adding a Duration & Rates grid row, required input fields for the selected Scheme Type must be present:

| Scheme Type | Required on Add |
| :--- | :--- |
| Daily | Duration, Duration Type, Interest Rate (p.a. %) |
| FD | Duration, Duration Type, Maturity Amount, Interest Rate (p.a. %) |
| Recurring | Duration, Interest Rate (p.a. %), Agent Interest Rate (p.a. %) — see [BR-025](#br-025--recurring-duration-row-includes-agent-rate) |
| Loan | Duration (Months), Maximum Loan Amount, Interest Rate (p.a. %) — see [BR-030](#br-030--loan-duration-row-required-fields) |

Rows may be removed from the grid. Whether ≥1 row is mandatory on Save is [BR-034](#br-034--minimum-grid-rows-on-save) (TODO).

---

### BR-021 — Account Closing tab — deposit types only

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [new-scheme-screen.md](../../05-ui-ux/settings/schemes/new-scheme-screen.md) — Tab Visibility Matrix; Tab Account Closing |

**Rule:** Account Closing (खाते बंद) is available only for Daily, FD, and Recurring. Before-maturity and pre-maturity commission slabs use `app-rate-slab-editor`. Savings and Loan must not show or persist Account Closing tab data.

---

### BR-022 — FD required identity fields

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | Field-reference [fixed-deposit-new-scheme-screen.md](../../05-ui-ux/settings/schemes/fixed-deposit-new-scheme-screen.md) Tab 1; Advanced placement per [new-scheme-screen.md](../../05-ui-ux/settings/schemes/new-scheme-screen.md) |

**Rule:** When Scheme Type is FD: product subtype (योजनेचे प्रकार) is required (values include मुदत ठेव, दाम दुप्पट, कॅश सर्टिफिकेट, पेन्शन, ठेव कर्ज — placeholder `निवडा` invalid); Multiplier is required; Receipt No. Series Start and Receipt No. Series Number are required (Advanced tab in unified layout).

---

### BR-023 — FD Auto Renewal dependent fields

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | Field-reference [fixed-deposit-new-scheme-screen.md](../../05-ui-ux/settings/schemes/fixed-deposit-new-scheme-screen.md) Advance Setting; [new-scheme-screen.md](../../05-ui-ux/settings/schemes/new-scheme-screen.md) Advanced |

**Rule:** FD Auto Renewal waiting period, renewal locking period, renewal period after maturity, and renewal interest rate after maturity are editable only when Auto Renewal is checked. When Auto Renewal is unchecked, those dependent values are not required and must not be treated as active renewal configuration.

---

### BR-024 — FD Benefits on Duration tab only

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [new-scheme-screen.md](../../05-ui-ux/settings/schemes/new-scheme-screen.md) — Tab 2 FD notes |

**Rule:** FD Additional Benefits is a single Benefits section on the Duration & Rates tab. The legacy separate Additional Benefits tab must not appear in the unified wizard.

---

### BR-025 — Recurring duration row includes agent rate

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | Field-reference [recurring-new-scheme-screen.md](../../05-ui-ux/settings/schemes/recurring-new-scheme-screen.md) Tab 2; Agent rate → Advanced per [new-scheme-screen.md](../../05-ui-ux/settings/schemes/new-scheme-screen.md) |

**Rule:** When Scheme Type is Recurring, each Duration & Rates add requires Duration, Interest Rate (p.a. %), and Agent Interest Rate (p.a. %). Agent Interest Rate may be edited from Advanced when the unified layout moves it there; the value remains required for each duration row on Save.

---

### BR-026 — Recurring Salary and Rebate under Advanced

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [new-scheme-screen.md](../../05-ui-ux/settings/schemes/new-scheme-screen.md) — Advanced (Recurring) |

**Rule:** For Recurring, Salary Payment (पगाराप्रमाणे भरणा) and Rebate (रिबेट) content live under the Advanced tab (collapsed by default), not as top-level wizard tabs.

---

### BR-027 — Loan Type required

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | Field-reference [loan-new-scheme-screen.md](../../05-ui-ux/settings/schemes/loan-new-scheme-screen.md) Tab 1 #1 |

**Rule:** When Scheme Type is Loan, Loan Type (कर्ज प्रकार) is required. Allowed values are the Loan Type dropdown list in the loan field-reference spec (e.g. Member Loan, Gold Mortgage Loan, Credit Card, Fixed Deposit Loan, Unsecured Loan, …). Placeholder `निवडा` is invalid.

---

### BR-028 — Credit Card billing cycle day conditional

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [new-scheme-screen.md](../../05-ui-ux/settings/schemes/new-scheme-screen.md) — Loan Tab 1 simplifications; field-reference [loan-new-scheme-screen.md](../../05-ui-ux/settings/schemes/loan-new-scheme-screen.md) #28 |

**Rule:** Monthly Billing Cycle Day (1–31) is visible and required only when Loan Type is `क्रेडीट कार्ड` (Credit Card). For all other Loan Types the field is hidden and not required.

---

### BR-029 — Loan deposit account mandatory enables fields

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | Field-reference [loan-new-scheme-screen.md](../../05-ui-ux/settings/schemes/loan-new-scheme-screen.md) #22–#24 |

**Rule:** Select Deposit G.L. Head and Minimum Deposit Account Duration (Months) are enabled and applicable only when Deposit Account Mandatory (ठेव खाते अनिवार्य असावे) is checked. When unchecked, those fields are hidden/disabled and not required.

---

### BR-030 — Loan duration row required fields

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | Field-reference [loan-new-scheme-screen.md](../../05-ui-ux/settings/schemes/loan-new-scheme-screen.md) Tab 2; Category removed per [new-scheme-screen.md](../../05-ui-ux/settings/schemes/new-scheme-screen.md) |

**Rule:** When adding a Loan Duration/Interest Rate row, Duration (Months), Maximum Loan Amount (Rs.), and Interest Rate (% p.a.) are required. Category is not required and is omitted from the default unified UI.

---

### BR-031 — Loan guarantor total is sum

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | Field-reference [loan-new-scheme-screen.md](../../05-ui-ux/settings/schemes/loan-new-scheme-screen.md) Tab 4; Loan Specific tab per [new-scheme-screen.md](../../05-ui-ux/settings/schemes/new-scheme-screen.md) |

**Rule:** On Loan Specific → Guarantor, Total Guarantors (एकूण जामीनदार) is the read-only sum of Customer (A) + Class A Member (B) + Nominal Member (C) counts. The actor must not manually override the total independently of A/B/C.

---

### BR-032 — Loan charges Deduction or Fee mode

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | Field-reference [loan-new-scheme-screen.md](../../05-ui-ux/settings/schemes/loan-new-scheme-screen.md) Tab 6; [new-scheme-screen.md](../../05-ui-ux/settings/schemes/new-scheme-screen.md) Charges/Loan |

**Rule:** For Loan schemes, Charges/Deduction tab uses Deduction (कपात) or Fee (शुल्क) mode (radio). Charge/deduction names use the shared list in [BR-012](#br-012--shared-charge-types). Grid rows may include % / Amount. Processing-fee timing radios apply only when Loan Processing Fee Required is checked.

---

### BR-033 — Scheme Status account-opening eligibility

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | TODO |
| Source | [new-scheme-screen.md](../../05-ui-ux/settings/schemes/new-scheme-screen.md) — Tab 1, field #4 |

**Rule:** `TODO:` Confirm which Status values (`चालू`, `बंद`, `स्थगित`, `कालबाह्य`) allow opening new accounts under the scheme in operational modules.

---

### BR-034 — Minimum grid rows on Save

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | TODO |
| Source | Duration & Rates / Interest Posting tabs |

**Rule:** `TODO:` Confirm whether Save requires at least one Duration & Rates row (for types that show that tab) and/or at least one Interest Posting row.

---

## Related Documents

- [overview.md](overview.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [../../05-ui-ux/settings/schemes/new-scheme-screen.md](../../05-ui-ux/settings/schemes/new-scheme-screen.md)
- [../master/business-rules.md](../master/business-rules.md)
- [../../00-project-overview/glossary.md](../../00-project-overview/glossary.md)
