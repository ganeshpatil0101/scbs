# Business Rules — Savings

## Purpose

Numbered business rules for the Savings module: New Savings Account (3-tab wizard) and Savings Account Register. Every rule cites its UI spec source. Rules marked **TODO** require business confirmation before implementation.

**Sources:** [new-savings-account-screen.md](../../05-ui-ux/savings/new-savings-account-screen.md), [account-register-screen.md](../../05-ui-ux/savings/account-register-screen.md). Superseded specs (`savings-transaction-screen.md`, `manual-interest-calculation-screen.md`) are **not** used as sources per this request — see [ux-optimization.md](../../05-ui-ux/savings/ux-optimization.md) and their replacements ([deposit-account-transaction-screen.md](../../05-ui-ux/accounting/deposit-account-transaction-screen.md), [manual-interest-management-screen.md](../../05-ui-ux/accounting/manual-interest-management-screen.md)) which belong to the Accounting domain.

## Rule Index

| ID | Title | Type | Status |
| :--- | :--- | :--- | :---: |
| [BR-001](#br-001--customer-must-exist-before-savings-account-can-be-opened) | Customer must exist before Savings Account can be opened | Eligibility | Confirmed |
| [BR-002](#br-002--scheme-required-and-loaded-from-savings-scheme-master) | Scheme required and loaded from Savings scheme master | Validation | Confirmed |
| [BR-003](#br-003--member-only-scheme-enforcement-not-verifiable-on-this-screen) | Member-only scheme enforcement not verifiable on this screen | Eligibility | TODO |
| [BR-004](#br-004--account-no-auto-generated) | Account No. auto-generated | Workflow | Confirmed |
| [BR-005](#br-005--interest-rate-auto-filled-from-scheme-admin-override-role-undefined) | Interest Rate auto-filled from scheme; admin override role undefined | Eligibility | TODO |
| [BR-006](#br-006--current-date-defaults-to-system-date) | Current Date defaults to system date | Workflow | Confirmed |
| [BR-007](#br-007--minimum-balance-required-at-opening) | Minimum Balance required at opening | Validation | Confirmed |
| [BR-008](#br-008--account-status-default-and-shared-values-across-deposit-products) | Account Status default and shared values across deposit products | Validation | Confirmed |
| [BR-009](#br-009--advanced-settings-visibility-role-undefined) | Advanced Settings visibility role undefined | Cross-cutting | TODO |
| [BR-010](#br-010--debit-limit-and-fund-transfer-limit-optional-overrides) | Debit Limit and Fund Transfer Limit optional overrides | Validation | Confirmed |
| [BR-011](#br-011--ifsc-code-enables-bank-payout-auto-fill) | IFSC Code enables bank payout auto-fill | Workflow | Confirmed |
| [BR-012](#br-012--nominee-section-conditional-on-add-nominee-checkbox) | Nominee section conditional on Add Nominee checkbox | Eligibility | Confirmed |
| [BR-013](#br-013--joint-holder-section-conditional-on-add-joint-holder-checkbox) | Joint Holder section conditional on Add Joint Holder checkbox | Eligibility | Confirmed |
| [BR-014](#br-014--nominee-lookup-resolves-to-existing-or-quick-added-customer) | Nominee lookup resolves to existing or quick-added Customer | Eligibility | Confirmed |
| [BR-015](#br-015--nominee-relation-reuses-canonical-membership-list) | Nominee Relation reuses canonical Membership list | Cross-cutting | Confirmed |
| [BR-016](#br-016--nominee-percentage-optional-nomination-date-and-age-system-derived) | Nominee Percentage optional; Nomination Date and Age system-derived | Validation | Confirmed |
| [BR-017](#br-017--joint-holder-guardian-and-customer-fields-add-validates-selection) | Joint Holder Guardian and Customer fields; Add validates selection | Validation | Confirmed |
| [BR-018](#br-018--account-operation-instructions-required-with-defined-values) | Account Operation Instructions required with defined values | Validation | Confirmed |
| [BR-019](#br-019--new-savings-account-wizard-atomic-save-on-create) | New Savings Account wizard atomic save on create | Workflow | Confirmed |
| [BR-020](#br-020--savings-screens-use-master-permission-levels) | Savings screens use Master permission levels | Cross-cutting | Confirmed |
| [BR-021](#br-021--account-register-primary-search-fields-all-optional) | Account Register primary search fields all optional | Eligibility | Confirmed |
| [BR-022](#br-022--loan-linked-accounts-filter-depends-on-undocumented-loan-domain) | Loan-linked accounts filter depends on undocumented Loan domain | Eligibility | TODO |
| [BR-023](#br-023--account-register-grid-and-search-follow-interactive-reporting-standard) | Account Register grid and search follow interactive reporting standard | Cross-cutting | Confirmed |
| [BR-024](#br-024--वगळा-exclude-is-equivalent-to-काढा-remove) | वगळा (Exclude) is equivalent to काढा (Remove) | Workflow | Confirmed |
| [BR-025](#br-025--close-account-requires-zero-balance-and-no-other-active-bank-relationships) | Close Account requires zero balance and no other active bank relationships | Eligibility | Confirmed |
| [BR-026](#br-026--account-details-and-account-statement-lack-dedicated-specs) | Account Details and Account Statement lack dedicated specs | Cross-cutting | TODO |

---

## Rules

### BR-001 — Customer must exist before Savings Account can be opened

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [new-savings-account-screen.md](../../05-ui-ux/savings/new-savings-account-screen.md) — Tab 1, field #1 |

**Rule:** New Savings Account Tab 1 requires selecting an **existing** Customer via Autocomplete (`entityType: customer`). The screen must not create a new Customer identity — a person must first be registered via [New Customer](../../05-ui-ux/customer/new-customer-screen.md) before a Savings account can be opened for them.

**Notes:** Same cross-screen dependency shape as [customer BR-026](../customer/business-rules.md#br-026--customer-must-exist-before-other-account-can-be-opened) (Other Account) and [settings/master BR-001](../settings/master/business-rules.md#br-001--customer-required-for-staff-registration) (Staff registration).

---

### BR-002 — Scheme required and loaded from Savings scheme master

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-savings-account-screen.md](../../05-ui-ux/savings/new-savings-account-screen.md) — Tab 1, field #2 |

**Rule:** Select Scheme (योजना निवडा) is required and loads dynamically from Settings → नवीन योजना where Scheme Type = `बचत` (Savings). Placeholder/no selection is not a valid saved value. The full list is scheme master data — not a fixed enum.

**Notes:** Dependency on [settings/schemes business-rules.md](../settings/schemes/business-rules.md) — Savings scheme creation ([BR-001](../settings/schemes/business-rules.md#br-001--scheme-type-required), [BR-015](../settings/schemes/business-rules.md#br-015--savings-product-subtype-and-interest-rate-required), [BR-016](../settings/schemes/business-rules.md#br-016--savings-interest-calculation-mode)) must exist before an account can be opened under it. Whether a scheme's Status ([settings/schemes BR-033](../settings/schemes/business-rules.md#br-033--scheme-status-account-opening-eligibility), TODO) blocks new account opening is inherited from that unresolved rule — not re-litigated here.

---

### BR-003 — Member-only scheme enforcement not verifiable on this screen

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | TODO |
| Source | [settings/schemes business-rules.md](../settings/schemes/business-rules.md#br-010--allow-only-members-optional) BR-010; [new-savings-account-screen.md](../../05-ui-ux/savings/new-savings-account-screen.md) — Tab 1 |

**Rule:** `TODO:` When the selected Savings scheme has **Allow Only Members** (फक्त सदस्यांना परवानगी द्या) checked ([settings/schemes BR-010](../settings/schemes/business-rules.md#br-010--allow-only-members-optional)), account opening must require the selected Customer to also hold Membership. The New Savings Account spec exposes **no field or read-only indicator** confirming the selected Customer's Member status, and the Membership operational domain (`02-business-domains/membership/`) is not yet documented (Phase 3). Confirm: (a) how/where this check surfaces on this screen (blocking error vs. warning vs. hidden pre-filter on the Customer Autocomplete), and (b) the exact eligibility criteria (Member vs. Nominal Member — see [glossary.md](../../00-project-overview/glossary.md) Class B Member).

---

### BR-004 — Account No. auto-generated

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [new-savings-account-screen.md](../../05-ui-ux/savings/new-savings-account-screen.md) — Tab 1, field #3 |

**Rule:** Account No. (खाते क्र.) is system-generated and displayed as a read-only Label after Save. It is not a lookup field — excluded from entity-autocomplete consolidation ([entity-autocomplete-pattern.md](../../05-ui-ux/shared/entity-autocomplete-pattern.md) Exclusions).

**Notes:** Generation algorithm (global vs. per-branch vs. per-scheme sequence) is `TODO:` not yet documented — same open-item pattern as [customer BR-001](../customer/business-rules.md#br-001--customer-number-auto-generated) (Customer No.) and [settings/accounting BR-022](../settings/accounting/business-rules.md#br-022--gl-head-number-generation-algorithm) (GL Head No.).

---

### BR-005 — Interest Rate auto-filled from scheme; admin override role undefined

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | TODO |
| Source | [new-savings-account-screen.md](../../05-ui-ux/savings/new-savings-account-screen.md) — Tab 1, field #4 |

**Rule:** Interest Rate (व्याज दर % पी ए) is a required read-only Label auto-filled from the selected Scheme's configured rate ([settings/schemes BR-015](../settings/schemes/business-rules.md#br-015--savings-product-subtype-and-interest-rate-required)). The spec states "Admin override requires admin role," but this platform defines only three permission levels — All Rights / View Only / No Rights ([settings/master BR-017](../settings/master/business-rules.md#br-017--permission-levels-are-all-rights--view-only--no-rights)) — plus a Super User bypass flag ([settings/master BR-012](../settings/master/business-rules.md#br-012--super-user-permission-bypass)). `TODO:` Confirm which of these (or a new role concept) satisfies "admin role" for this override, and whether the same undefined "admin role" gate also governs [BR-009](#br-009--advanced-settings-visibility-role-undefined) below.

---

### BR-006 — Current Date defaults to system date

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [new-savings-account-screen.md](../../05-ui-ux/savings/new-savings-account-screen.md) — Tab 1, field #5 |

**Rule:** Current Date (चालू दिनांक) defaults to the system date and is editable. It is persisted and displayed as चालू दिनांक (Open Date) on the [Account Register](../../05-ui-ux/savings/account-register-screen.md) results grid (column #8).

---

### BR-007 — Minimum Balance required at opening

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-savings-account-screen.md](../../05-ui-ux/savings/new-savings-account-screen.md) — Tab 1, field #7 |

**Rule:** Minimum Balance (किमान शिल्लक) is required, may default from the selected scheme, and remains editable. This value is the basis referenced by [BR-025](#br-025--close-account-requires-zero-balance-and-no-other-active-bank-relationships) (Close Account balance check).

---

### BR-008 — Account Status default and shared values across deposit products

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-savings-account-screen.md](../../05-ui-ux/savings/new-savings-account-screen.md) — Tab 1, field #8; [account-register-screen.md](../../05-ui-ux/savings/account-register-screen.md) — field #3 |

**Rule:** Select Status (स्थिती निवडा) is optional at account creation, defaulting to `चालू` (Active). Allowed values: `चालू`, `बंद` (Closed), `स्थगित` (Suspended). This is the same three-value enum used on [New FD Account](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md), [New Daily Account](../../05-ui-ux/daily/new-daily-account-screen.md), and [New Recurring Account](../../05-ui-ux/recurring/new-recurring-account-screen.md) — implementations should share one status domain across deposit product accounts rather than duplicating it per product.

**Notes:** This is distinct from **Customer** Status ([customer BR-008](../customer/business-rules.md#br-008--customer-status-required-with-defined-values), an 8-value enum) and from **Scheme** Status ([settings/schemes BR-009](../settings/schemes/business-rules.md#br-009--scheme-status-required-with-defined-values)). Do not merge these three status domains.

---

### BR-009 — Advanced Settings visibility role undefined

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | TODO |
| Source | [new-savings-account-screen.md](../../05-ui-ux/savings/new-savings-account-screen.md) — Section: प्रगत सेटिंग्ज (Advanced Settings) |

**Rule:** `TODO:` The Advanced Settings section note states "Visible to users with accounting/admin role or when expanded manually" — the same phrase repeats verbatim on [New FD Account](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md) and [New Daily Account](../../05-ui-ux/daily/new-daily-account-screen.md). No existing domain (Customer, Settings/Master, Settings/Schemes) has resolved what "accounting/admin role" maps to against the platform's three-level permission model ([settings/master BR-017](../settings/master/business-rules.md#br-017--permission-levels-are-all-rights--view-only--no-rights)). Until resolved, implementations should treat "or when expanded manually" as the operative behaviour (collapsed-by-default panel, manually expandable by any actor with access to the screen) and not gate visibility by an undefined role.

---

### BR-010 — Debit Limit and Fund Transfer Limit optional overrides

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-savings-account-screen.md](../../05-ui-ux/savings/new-savings-account-screen.md) — Tab 1 Advanced, fields #9–#10 |

**Rule:** Debit Limit (नावे मर्यादा) and Fund Transfer Limit (निधी हस्तांतरण मर्यादा) are optional numeric overrides with no scheme-derived default specified in the spec beyond the sample `0` for Fund Transfer Limit.

---

### BR-011 — IFSC Code enables bank payout auto-fill

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [new-savings-account-screen.md](../../05-ui-ux/savings/new-savings-account-screen.md) — Tab 1 Advanced, fields #11–#13 |

**Rule:** IFSC Code (आय.एफ.एस.सी. कोड) is optional; when entered, it enables bank payout and auto-fills the read-only Bank Name (बँकेचे नाव) Label. Bank Savings Account No. (बँकेचे बचत खाते क्रमांक) is an optional companion field for the payout account, independent of the CBS Account No. ([BR-004](#br-004--account-no-auto-generated)).

**Notes:** IFSC → Bank Name resolution mechanism (external lookup API vs. manual entry) is `TODO:` not specified in the spec, same open pattern as other IFSC fields across FD/Daily nominee payout blocks.

---

### BR-012 — Nominee section conditional on Add Nominee checkbox

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [new-savings-account-screen.md](../../05-ui-ux/savings/new-savings-account-screen.md) — Tab 1, field #14 |

**Rule:** Add Nominee (वारसदार जोडा) is unchecked by default. When checked, Tab 2 (वारसदार) becomes visible in the tab bar; when unchecked, Tab 2 is hidden and skipped during Next/Back navigation, and no nominee data is persisted.

---

### BR-013 — Joint Holder section conditional on Add Joint Holder checkbox

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [new-savings-account-screen.md](../../05-ui-ux/savings/new-savings-account-screen.md) — Tab 1, field #15 |

**Rule:** Add Joint Holder (संयुक्त खातेदार जोडा) is unchecked by default. When checked, Tab 3 (संयुक्त खाते धारक) becomes visible in the tab bar; when unchecked, Tab 3 is hidden and skipped during Next/Back navigation, and no joint holder data is persisted.

---

### BR-014 — Nominee lookup resolves to existing or quick-added Customer

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [new-savings-account-screen.md](../../05-ui-ux/savings/new-savings-account-screen.md) — Tab 2, field #1 |

**Rule:** The Nominee Search field is a Customer Autocomplete (`entityType: customer`) with the **+ नवीन ग्राहक जोडा** companion action per [quick-add-customer-pattern.md](../../05-ui-ux/shared/quick-add-customer-pattern.md). A nominee is always a Customer record — either resolved from existing master data or created via the minimal quick-add popup (Salutation, Name, Date of Birth, Mobile Number; Branch = session branch; Customer No. auto-generated per [customer BR-001](../customer/business-rules.md#br-001--customer-number-auto-generated)).

**Notes:** Nominee Details (fields #2–#5) become visible only after a nominee customer is resolved in field #1 — same visibility gate documented on [New Daily Account Tab 2](../../05-ui-ux/daily/new-daily-account-screen.md#tab-2-वारसदार-nominee) and [New FD Account Tab 2](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md#tab-2-वारसदार-nominee); this domain shares the same `app-nominee-form` / `app-nominee-grid` component, not a Savings-specific implementation.

---

### BR-015 — Nominee Relation reuses canonical Membership list

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | Confirmed |
| Source | [new-savings-account-screen.md](../../05-ui-ux/savings/new-savings-account-screen.md) — Tab 2, field #2; [new-membership-screen.md](../../05-ui-ux/membership/new-membership-screen.md) — Tab 3, field #19 |

**Rule:** Nominee Relation (नाते) values must come from the single canonical Relation list finalized on the Membership module's New Membership Tab 3: `मुलगा`, `पुतण्या`, `मुली`, `मुलगा - पती`, `पति व मुलगा`, `वरील प्रमाणे`, `बायको`, `मैत्रीण`, `केअरटेकर`, `लहान भाऊ`, `स्वतः`, `पत्नी`, `पती`. Do not maintain a Savings-specific Relation list — the same list is already reused by Customer ([customer BR-014](../customer/business-rules.md#br-014--nominee-relation-reuses-canonical-membership-list)), Daily, and FD nominee screens.

**Notes:** Cross-domain dependency — Membership operational domain (`02-business-domains/membership/`) is not yet documented (Phase 3); this list currently exists only in the UI spec. Migrate this canonical definition to Membership's business-rules.md when authored, and update all referencing domains (Customer, Savings, FD, Daily, Recurring, Loan) to point there.

---

### BR-016 — Nominee Percentage optional; Nomination Date and Age system-derived

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-savings-account-screen.md](../../05-ui-ux/savings/new-savings-account-screen.md) — Tab 2, fields #3–#5 |

**Rule:** Nominee Percentage (टक्केवारी) is optional. Nomination Date (नामांकन दिनांक) is a read-only Label set to the system date. Age at Nomination (नामांकन करताना वय) is a read-only Label auto-calculated from the resolved nominee's Date of Birth. None of these three fields are directly enterable by the actor.

**Notes:** The spec does not state whether multiple nominees' Percentage values must total 100% — same open UX suggestion flagged in [ux-optimization.md](../../05-ui-ux/savings/ux-optimization.md) "Nominee Tab — UX Enhancement Suggestions" #2 (non-binding suggestion, not a confirmed rule).

---

### BR-017 — Joint Holder Guardian and Customer fields; Add validates selection

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-savings-account-screen.md](../../05-ui-ux/savings/new-savings-account-screen.md) — Tab 3, fields #1–#2 |

**Rule:** On Tab 3, Guardian (पालक) is an optional checkbox and Select Customer (ग्राहक निवडा) is an optional Autocomplete (`entityType: customer`). The `+ जोड` (Add) action validates that a customer has been resolved in field #2 before appending a row to the Joint Holder grid (`app-joint-holder-grid`).

---

### BR-018 — Account Operation Instructions required with defined values

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-savings-account-screen.md](../../05-ui-ux/savings/new-savings-account-screen.md) — Tab 3, field #3 |

**Rule:** Account Operation Instructions (खाते चालविण्याची सूचना) is required with default `स्वतः` (Self). Allowed values: `फक्त प्रमुख खातेदार` (Only Primary Holder), `फक्त संयुक्त खातेदार` (Only Joint Holder), `दोन्ही खातेदार आवश्यक` (Both Holders Required), `दोघांपैकी कोणीही` (Either Holder), `स्वतः` (Self).

**Notes:** This field lives on Tab 3, which is itself conditional on [BR-013](#br-013--joint-holder-section-conditional-on-add-joint-holder-checkbox). `TODO:` The spec does not state the persisted value when Tab 3 is skipped entirely (single-holder account) — confirm whether `स्वतः` is still persisted as the operative instruction or the field is simply not applicable.

---

### BR-019 — New Savings Account wizard atomic save on create

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | Standing Decision 2026-07-24; [new-savings-account-screen.md](../../05-ui-ux/savings/new-savings-account-screen.md) — Tabs 1–3, footer actions |

**Rule:** On create, New Savings Account persists the Account, Nominee(s) (if Tab 2 enabled), and Joint Holder(s) (if Tab 3 enabled) only when the actor clicks **जतन करा** (Save) on the final visible tab, after all visible tabs pass field validation. **Next** (पुढे) and **Back** (मागे) between tabs must not write partial records. **Reset** (रीसेट) clears wizard state without persisting.

**Notes:** Matches the atomic-save pattern already confirmed for [customer BR-021](../customer/business-rules.md#br-021--new-customer-wizard-atomic-save-on-create), [settings/schemes BR-013](../settings/schemes/business-rules.md#br-013--scheme-wizard-atomic-save-on-create), [settings/master BR-019](../settings/master/business-rules.md#br-019--staff-access-wizard-atomic-save-on-create), and [settings/accounting BR-002](../settings/accounting/business-rules.md#br-002--gl-setup-atomic-save-on-create).

---

### BR-020 — Savings screens use Master permission levels

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | Confirmed |
| Source | [settings/master business-rules.md](../settings/master/business-rules.md#br-017--permission-levels-are-all-rights--view-only--no-rights) BR-017 |

**Rule:** Access to New Savings Account and Account Register follows Master permission levels: **All Rights** (full edit/save), **View Only** (read-only; Save/Add/Remove/Close actions hidden), **No Rights** (navigation blocked). Do not redefine permission semantics in this domain.

---

### BR-021 — Account Register primary search fields all optional

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [account-register-screen.md](../../05-ui-ux/savings/account-register-screen.md) — Primary Search, fields #1–#8 |

**Rule:** All eight Primary Search fields (Branch, Scheme, Status, Account No. From/To, Account Holder, Customer No. From/To) are optional. Clicking **दाखवा** (Show) with no filters entered returns results per the actor's entitled scope, unlike [customer BR-031](../customer/business-rules.md#br-031--registration-list-filters-required) (Other Account Registration List) which requires Branch, Account by Customer, and Status before Show.

**Notes:** Branch-scoping of results for actors with limited branch rights is `TODO:` unresolved — same open pattern as [customer BR-024](../customer/business-rules.md#br-024--customer-list-branch-scoped-results-eligibility).

---

### BR-022 — Loan-linked accounts filter depends on undocumented Loan domain

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | TODO |
| Source | [account-register-screen.md](../../05-ui-ux/savings/account-register-screen.md) — Results filter, field #9 |

**Rule:** `TODO:` The कर्ज संलग्नीत खाते (Loan-linked accounts) checkbox filters or highlights (pink row) Savings accounts with an associated loan. The Loan domain (`02-business-domains/loan/`) is not yet documented (Phase 3), so the precise linkage (e.g. Deposit Loan lien against this Savings account vs. any loan held by the same customer) cannot be confirmed from existing documentation. This linkage is directly relevant to [BR-025](#br-025--close-account-requires-zero-balance-and-no-other-active-bank-relationships) (Close Account) and must be resolved when the Loan domain is authored.

**Notes:** The same pink-highlight legend for loan-linked accounts appears on [FD Account Management](../../05-ui-ux/fixed-deposit/fd-account-management-screen.md), [Daily Account Register](../../05-ui-ux/daily/account-register-screen.md), and [Recurring Account Register](../../05-ui-ux/recurring/account-register-screen.md) — Savings is the only one of the four with an explicit filter checkbox rather than legend-only styling.

---

### BR-023 — Account Register grid and search follow interactive reporting standard

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | Confirmed |
| Source | [account-register-screen.md](../../05-ui-ux/savings/account-register-screen.md); [business-goals.md](../../00-project-overview/business-goals.md) BG-005 |

**Rule:** Account Register implements the platform-wide interactive reporting standard (BG-005): Primary Search filters, a results grid with pagination and totals, and Details/Export actions. Additional columns are available via the तपशील (Details) sidebar action rather than shown by default in the base 19-column grid.

---

### BR-024 — वगळा (Exclude) is equivalent to काढा (Remove)

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | Standing Decision 2026-07-24; [account-register-screen.md](../../05-ui-ux/savings/account-register-screen.md) — Sidebar actions; compare [fd-account-management-screen.md](../../05-ui-ux/fixed-deposit/fd-account-management-screen.md), [daily/account-register-screen.md](../../05-ui-ux/daily/account-register-screen.md), [recurring/account-register-screen.md](../../05-ui-ux/recurring/account-register-screen.md) |

**Rule:** The Savings Account Register sidebar action वगळा (Exclude) is a spec wording variance and must be implemented with the **same semantics as काढा (Remove)** used in the equivalent sidebar position on the FD, Daily, and Recurring Account Register/Management screens — it removes the selected account registration row, it does not merely hide the row from the current view.

**Notes:** `TODO:` Whether this remove action requires a confirmation dialog (as with [customer BR-032](../customer/business-rules.md#br-032--bulk-remove-requires-confirmation) bulk remove), and whether it is blocked for accounts that already have posted ledger transactions (vs. only allowed for accounts created in error with zero transaction history), is not stated in any of the four sibling specs — confirm before implementation, since this differs materially from removing a non-financial registration row.

---

### BR-025 — Close Account requires zero balance and no other active bank relationships

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | Standing Decision 2026-07-24; [account-register-screen.md](../../05-ui-ux/savings/account-register-screen.md) — Bottom actions |

**Rule:** खाते बंद करा (Close Account) succeeds only when **both** conditions hold for the selected Savings account's customer:

1. The Savings account balance equals its Minimum Balance floor of zero — i.e. the account balance is **0** ([BR-007](#br-007--minimum-balance-required-at-opening) defines the opening minimum; closing requires the account to actually be drawn down to zero, not merely at its configured minimum).
2. The customer holds **no other active relationship with the bank** — no active Loan, Daily (Pigmy), Recurring, or Fixed Deposit accounts. All such relationships must be closed/settled first.

If either condition fails, the system must block Close Account with a validation error identifying which condition is unmet. On success, the account's Status becomes `बंद` (Closed) ([BR-008](#br-008--account-status-default-and-shared-values-across-deposit-products)) and Account Close Date (grid column #19) is set to the current date.

**Notes:** Condition 2 is a cross-domain dependency on Loan, Daily, Recurring, and Fixed Deposit domains, none of which are yet documented (Phase 3) — the exact query (per-customer active account count across all four products) must be re-confirmed when those domains are authored. Related to the कर्ज संलग्नीत खाते (Loan-linked accounts) indicator ([BR-022](#br-022--loan-linked-accounts-filter-depends-on-undocumented-loan-domain)), which flags at least the Loan-linkage subset of this condition. `TODO:` Whether Close Account requires a confirmation dialog is not stated in the spec — recommend one given the irreversible nature of the action, consistent with [BR-024](#br-024--वगळा-exclude-is-equivalent-to-काढा-remove).

---

### BR-026 — Account Details and Account Statement lack dedicated specs

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | TODO |
| Source | [account-register-screen.md](../../05-ui-ux/savings/account-register-screen.md) — Sidebar actions तपशील, खाते उतारा |

**Rule:** `TODO:` तपशील (Details) opens account detail "in context" with no separate Account Information screen spec — same deferral pattern noted in [ux-optimization.md](../../05-ui-ux/savings/ux-optimization.md) #13. खाते उतारा (Account Statement) has no dedicated report spec; [reports/overview.md](../../05-ui-ux/reports/overview.md) documents a **Loan** Account Statement report only, with no equivalent for Savings/FD/Daily/Recurring deposit accounts. Both gaps should be resolved — either by authoring the missing specs or by confirming the sidebar action reuses an existing pattern not yet cross-referenced here.

---

## Related Documents

- [overview.md](overview.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [../../05-ui-ux/savings/new-savings-account-screen.md](../../05-ui-ux/savings/new-savings-account-screen.md)
- [../../05-ui-ux/savings/account-register-screen.md](../../05-ui-ux/savings/account-register-screen.md)
- [../customer/business-rules.md](../customer/business-rules.md)
- [../settings/schemes/business-rules.md](../settings/schemes/business-rules.md)
- [../settings/master/business-rules.md](../settings/master/business-rules.md)
- [../../00-project-overview/glossary.md](../../00-project-overview/glossary.md)
