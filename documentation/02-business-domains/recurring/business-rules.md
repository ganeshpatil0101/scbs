# Business Rules — Recurring (Recurring Deposit)

## Purpose

Numbered business rules for the **रिकरिंग (Recurring Deposit / RD)** operational module: New Recurring Account (3-tab wizard), Recurring Account Register, and Recurring Interest Multiplier. Every rule cites its UI spec source. Rules marked **TODO** require business confirmation before implementation.

**Sources (current, non-superseded specs only):**

- [new-recurring-account-screen.md](../../05-ui-ux/recurring/new-recurring-account-screen.md)
- [account-register-screen.md](../../05-ui-ux/recurring/account-register-screen.md)
- [interest-multiplier-screen.md](../../05-ui-ux/recurring/interest-multiplier-screen.md)

**Superseded specs excluded per this generation request** (see [ux-optimization.md](../../05-ui-ux/recurring/ux-optimization.md) and [overview.md](../../05-ui-ux/recurring/overview.md)): `recurring-transaction-screen.md` / `credit-transaction-screen.md` → [deposit-account-transaction-screen.md](../../05-ui-ux/accounting/deposit-account-transaction-screen.md); `recurring-interest-management-screen.md` / `manual-interest-assessment-screen.md` / `manual-interest-provision-screen.md` → [manual-interest-management-screen.md](../../05-ui-ux/accounting/manual-interest-management-screen.md). Recurring deposit/withdrawal (installment) transactions, missed-installment penalty, and manual interest are documented under the **Accounting** domain (Phase 3), not here.

## Rule Index

| ID | Title | Type | Status |
| :--- | :--- | :--- | :---: |
| [BR-001](#br-001--customer-must-exist-before-recurring-account-can-be-opened) | Customer must exist before Recurring account can be opened | Eligibility | Confirmed |
| [BR-002](#br-002--scheme-required-and-loaded-from-recurring-scheme-master) | Scheme required and loaded from Recurring scheme master | Validation | Confirmed |
| [BR-003](#br-003--scheme-derived-attributes-auto-filled-read-only) | Scheme-derived attributes auto-filled read-only | Workflow | Confirmed |
| [BR-004](#br-004--agent-and-sales-agent-optional-agent-scoped-to-agent-branch) | Agent and Sales Agent optional; Agent scoped to Agent Branch | Validation | Confirmed |
| [BR-005](#br-005--account-no-auto-generated) | Account No. auto-generated | Workflow | Confirmed |
| [BR-006](#br-006--account-type-required-with-defined-values) | Account Type required with defined values | Validation | Confirmed |
| [BR-007](#br-007--duration-selected-from-scheme-grid-duration-and-rate-auto-filled) | Duration selected from scheme grid; duration and rate auto-filled | Validation | Confirmed |
| [BR-008](#br-008--interest-rate-admin-override-role-undefined) | Interest Rate admin override role undefined | Eligibility | TODO |
| [BR-009](#br-009--account-opening-date-defaults-to-system-date) | Account Opening Date defaults to system date | Workflow | Confirmed |
| [BR-010](#br-010--maturity-date-system-calculated) | Maturity Date system-calculated | Workflow | Confirmed |
| [BR-011](#br-011--installment-amount-required) | Installment Amount required | Validation | Confirmed |
| [BR-012](#br-012--deposit-type-required-frequency-values-todo) | Deposit Type required; frequency values TODO | Validation | TODO |
| [BR-013](#br-013--maturity-amount-system-computed-from-scheme-interest-formula) | Maturity Amount system-computed from scheme interest formula | Workflow | Confirmed |
| [BR-014](#br-014--account-status-default-and-shared-values-across-deposit-products) | Account Status default and shared values across deposit products | Validation | Confirmed |
| [BR-015](#br-015--advanced-settings-visibility-role-undefined) | Advanced Settings visibility role undefined | Cross-cutting | TODO |
| [BR-016](#br-016--ifsc-code-enables-bank-payout-auto-fill) | IFSC Code enables bank payout auto-fill | Workflow | Confirmed |
| [BR-017](#br-017--nominee-section-conditional-on-add-nominee-checkbox) | Nominee section conditional on Add Nominee checkbox | Eligibility | Confirmed |
| [BR-018](#br-018--joint-holder-section-conditional-on-add-joint-holder-checkbox) | Joint Holder section conditional on Add Joint Holder checkbox | Eligibility | Confirmed |
| [BR-019](#br-019--nominee-lookup-resolves-to-existing-or-quick-added-customer) | Nominee lookup resolves to existing or quick-added Customer | Eligibility | Confirmed |
| [BR-020](#br-020--nominee-relation-reuses-canonical-membership-list) | Nominee Relation reuses canonical Membership list | Cross-cutting | Confirmed |
| [BR-021](#br-021--nominee-percentage-optional-nomination-date-and-age-system-derived) | Nominee Percentage optional; Nomination Date and Age system-derived | Validation | Confirmed |
| [BR-022](#br-022--joint-holder-guardian-and-customer-fields-add-validates-selection) | Joint Holder Guardian and Customer fields; Add validates selection | Validation | Confirmed |
| [BR-023](#br-023--account-operation-instructions-required-with-defined-values) | Account Operation Instructions required with defined values | Validation | Confirmed |
| [BR-024](#br-024--new-recurring-account-wizard-atomic-save-on-create) | New Recurring Account wizard atomic save on create | Workflow | Confirmed |
| [BR-025](#br-025--recurring-screens-use-master-permission-levels) | Recurring screens use Master permission levels | Cross-cutting | Confirmed |
| [BR-026](#br-026--organization-auto-fill-header-from-session) | Organization auto-fill header from session | Workflow | Confirmed |
| [BR-027](#br-027--account-register-primary-search-fields-all-optional) | Account Register primary search fields all optional | Eligibility | Confirmed |
| [BR-028](#br-028--results-grid-legend-loan-linked-and-matured-highlighting) | Results grid legend: loan-linked and matured highlighting | Cross-cutting | TODO |
| [BR-029](#br-029--काढा-remove-deletes-the-account-registration-row) | काढा (Remove) deletes the account registration row | Workflow | Confirmed |
| [BR-030](#br-030--account-register-follows-interactive-reporting-standard) | Account Register follows interactive reporting standard | Cross-cutting | Confirmed |
| [BR-031](#br-031--account-details-and-account-statement-lack-dedicated-specs) | Account Details and Account Statement lack dedicated specs | Cross-cutting | TODO |
| [BR-032](#br-032--interest-multiplier-is-a-scheme-based-calculator-with-no-persistence) | Interest Multiplier is a scheme-based calculator with no persistence | Workflow | Confirmed |
| [BR-033](#br-033--interest-multiplier-conditional-field-visibility) | Interest Multiplier conditional field visibility | Validation | Confirmed |
| [BR-034](#br-034--interest-multiplier-computes-deposit-interest-and-maturity-amounts) | Interest Multiplier computes deposit, interest, and maturity amounts | Workflow | Confirmed |

---

## Rules — New Recurring Account

### BR-001 — Customer must exist before Recurring account can be opened

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [new-recurring-account-screen.md](../../05-ui-ux/recurring/new-recurring-account-screen.md) — Tab 1, field #1 |

**Rule:** New Recurring Account Tab 1 requires selecting an **existing** Customer via Autocomplete (`entityType: customer`). The screen must not create a new Customer identity — a person must first be registered via [New Customer](../../05-ui-ux/customer/new-customer-screen.md) before a Recurring account can be opened for them. After resolve, the customer summary (सभासद खाते क्र., वय (वर्षे), सभासदत्व प्रकार, ग्राहक शाखा, विशेष सूचना) is displayed read-only.

**Notes:** Same cross-screen dependency shape as [savings BR-001](../savings/business-rules.md#br-001--customer-must-exist-before-savings-account-can-be-opened), [fixed-deposit BR-001](../fixed-deposit/business-rules.md#br-001--customer-must-exist-before-fd-account-can-be-opened), [daily BR-001](../daily/business-rules.md#br-001--customer-must-exist-before-a-daily-account-can-be-opened), and [customer BR-026](../customer/business-rules.md#br-026--customer-must-exist-before-other-account-can-be-opened).

---

### BR-002 — Scheme required and loaded from Recurring scheme master

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-recurring-account-screen.md](../../05-ui-ux/recurring/new-recurring-account-screen.md) — Tab 1, field #2 |

**Rule:** Select Scheme (योजना निवडा) is required and loads dynamically from Settings → नवीन योजना where Scheme Type = `रिकरिंग` (Recurring). Placeholder/no selection is not a valid saved value. The full list is scheme master data — not a fixed enum. Sample: `रिकरिंग ठेव`.

**Notes:** Dependency on [settings/schemes business-rules.md](../settings/schemes/business-rules.md) — a Recurring scheme (with its duration/rate slab grid, interest type, and compounding configuration) must exist before an account can be opened under it. Whether a scheme's Status ([settings/schemes BR-033](../settings/schemes/business-rules.md), TODO) blocks new account opening is inherited from that unresolved rule, not re-litigated here.

---

### BR-003 — Scheme-derived attributes auto-filled read-only

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [new-recurring-account-screen.md](../../05-ui-ux/recurring/new-recurring-account-screen.md) — Tab 1, fields #3–#4 |

**Rule:** On Scheme selection, Scheme / Interest Type (योजना / व्याज प्रकार, #3) and Compounding (परिणामगणन, #4; e.g. `वार्षिक`) are populated as read-only Labels from the selected scheme's configuration. They are not directly editable on this screen.

**Notes:** These derive from the scheme's interest configuration ([settings/schemes business-rules.md](../settings/schemes/business-rules.md)). Interest Type / Compounding feed the Maturity Amount computation in [BR-013](#br-013--maturity-amount-system-computed-from-scheme-interest-formula) and the [Interest Multiplier](#br-034--interest-multiplier-computes-deposit-interest-and-maturity-amounts). Same scheme-derived-attribute pattern as [fixed-deposit BR-003](../fixed-deposit/business-rules.md#br-003--scheme-derived-attributes-auto-filled-read-only).

---

### BR-004 — Agent and Sales Agent optional; Agent scoped to Agent Branch

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-recurring-account-screen.md](../../05-ui-ux/recurring/new-recurring-account-screen.md) — Tab 1, fields #6–#7; Advanced, fields #19–#20 |

**Rule:** Select Agent Branch (#6), Select Agent (#7), Select Sales Agent Branch (#19), and Select Sales Agent (#20) are all optional Autocomplete fields. When an Agent / Sales Agent is selected, its lookup is scoped to the corresponding Agent Branch field. Agent and Sales Agent both resolve against the **Agent** master (एजंट) owned by the Daily/Pigmy module.

**Notes:** Agent master is owned by the Daily module ([glossary.md](../../00-project-overview/glossary.md) Agent; [new-agent-screen.md](../../05-ui-ux/daily/new-agent-screen.md), [daily BR-021](../daily/business-rules.md#br-021--agent-identity-requires-an-existing-customer)). The exact Agent eligibility/status filter (whether a `बंद`/`स्थगित` agent is selectable, [daily BR-022](../daily/business-rules.md#br-022--agent-status-and-joining-date-required)) is deferred to the Daily domain. Same optional-agent pattern as [fixed-deposit BR-004](../fixed-deposit/business-rules.md#br-004--agent-and-sales-agent-optional-agent-scoped-to-agent-branch).

---

### BR-005 — Account No. auto-generated

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [new-recurring-account-screen.md](../../05-ui-ux/recurring/new-recurring-account-screen.md) — Tab 1, field #5 |

**Rule:** Account Number (खाते क्रमांक) is system-generated and displayed as a read-only Label after Save. It is not a lookup field — excluded from entity-autocomplete consolidation ([entity-autocomplete-pattern.md](../../05-ui-ux/shared/entity-autocomplete-pattern.md) Exclusions).

**Notes:** Generation algorithm (global vs. per-branch vs. per-scheme sequence) is `TODO:` not yet documented — same open-item pattern as [savings BR-004](../savings/business-rules.md#br-004--account-no-auto-generated), [fixed-deposit BR-005](../fixed-deposit/business-rules.md#br-005--account-no-auto-generated), [daily BR-004](../daily/business-rules.md#br-004--account-no-auto-generated), and [customer BR-001](../customer/business-rules.md#br-001--customer-number-auto-generated).

---

### BR-006 — Account Type required with defined values

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-recurring-account-screen.md](../../05-ui-ux/recurring/new-recurring-account-screen.md) — Tab 1, field #8 |

**Rule:** Account Type (खाते प्रकार) is required. Allowed values are the account-type list shared with [New FD Account](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md) / FD scheme benefits: `सामान्य खाते`, `ज्येष्ठ नागरिक खाते`, `महिला`, `विधवा`, `अपंग`, `दुसरी संस्था`, `नोकर`, `स्वातंत्र्यसैनिक`, `अति ज्येष्ठ नागरिक`. The Duration/rate slab ([BR-007](#br-007--duration-selected-from-scheme-grid-duration-and-rate-auto-filled)) may be filtered by Account Type where scheme duration/benefit rows are keyed by account type.

**Notes:** This is an account-classification enum, distinct from Customer Type and Account **Status** ([BR-014](#br-014--account-status-default-and-shared-values-across-deposit-products)). Same shared list as [fixed-deposit BR-006](../fixed-deposit/business-rules.md#br-006--account-type-required-with-defined-values).

---

### BR-007 — Duration selected from scheme grid; duration and rate auto-filled

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-recurring-account-screen.md](../../05-ui-ux/recurring/new-recurring-account-screen.md) — Tab 1, fields #9–#11 |

**Rule:** Select Duration (कालावधी निवडा, #9) is required and its options load from the selected scheme's duration/rate slab grid (Settings → नवीन योजना; e.g. `0-60`). Once a duration is selected, Duration (Months) (कालावधी(महिने), #10; e.g. `60`) and Interest Rate (% p.a.) (व्याज दर(% वार्षिक), #11; e.g. `12.37`) are read-only Labels auto-filled from that slab row. The actor cannot type these values directly.

**Notes:** Direct dependency on the selected scheme's configured duration/rate rows ([settings/schemes business-rules.md](../settings/schemes/business-rules.md)). Same slab-drives-duration/rate pattern as [daily BR-005](../daily/business-rules.md#br-005--duration-selected-from-scheme-grid-duration-and-rate-auto-filled) and [fixed-deposit BR-007](../fixed-deposit/business-rules.md#br-007--interest-rate-slab-required-and-drives-duration).

---

### BR-008 — Interest Rate admin override role undefined

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | TODO |
| Source | [new-recurring-account-screen.md](../../05-ui-ux/recurring/new-recurring-account-screen.md) — Tab 1, field #11 |

**Rule:** Interest Rate (व्याज दर(% वार्षिक)) is a required read-only Label auto-filled from the selected slab ([BR-007](#br-007--duration-selected-from-scheme-grid-duration-and-rate-auto-filled)). The spec states "Admin override requires admin role," but this platform defines only three permission levels — All Rights / View Only / No Rights ([settings/master BR-017](../settings/master/business-rules.md#br-017--permission-levels-are-all-rights--view-only--no-rights)) — plus a Super User bypass ([settings/master BR-012](../settings/master/business-rules.md#br-012--super-user-permission-bypass)). `TODO:` Confirm which permission (or a new role concept) satisfies "admin role" for this override, and whether it also governs [BR-015](#br-015--advanced-settings-visibility-role-undefined). Same unresolved item as [savings BR-005](../savings/business-rules.md#br-005--interest-rate-auto-filled-from-scheme-admin-override-role-undefined) and [fixed-deposit BR-010](../fixed-deposit/business-rules.md#br-010--interest-rate-auto-filled-from-slab-admin-override-role-undefined).

---

### BR-009 — Account Opening Date defaults to system date

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [new-recurring-account-screen.md](../../05-ui-ux/recurring/new-recurring-account-screen.md) — Tab 1, field #12 |

**Rule:** Account Opening Date (खाते चालू दिनांक) defaults to the system date and is editable. It is persisted and surfaced as चालू दिनांक (Open Date) on the [Account Register](../../05-ui-ux/recurring/account-register-screen.md) results grid (column #8). It is the base date for the Maturity Date derivation ([BR-010](#br-010--maturity-date-system-calculated)).

**Notes:** Same defaulting behaviour as [savings BR-006](../savings/business-rules.md#br-006--current-date-defaults-to-system-date), [fixed-deposit BR-008](../fixed-deposit/business-rules.md#br-008--current-date-defaults-to-system-date), and [daily BR-007](../daily/business-rules.md#br-007--current-date-defaults-to-system-date).

---

### BR-010 — Maturity Date system-calculated

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [new-recurring-account-screen.md](../../05-ui-ux/recurring/new-recurring-account-screen.md) — Tab 1, field #13 |

**Rule:** Maturity Date (परतीची दिनांक) is a required read-only Label calculated from the Account Opening Date ([BR-009](#br-009--account-opening-date-defaults-to-system-date)) plus the selected Duration (Months) ([BR-007](#br-007--duration-selected-from-scheme-grid-duration-and-rate-auto-filled)). The actor cannot enter it directly.

**Notes:** Surfaced as परतीची दिनांक (Return Date) on the Account Register grid (column #14). Analogous to [fixed-deposit BR-012](../fixed-deposit/business-rules.md#br-012--maturity-amount-return-date-and-receipt-date-system-computed) (Return Date component).

---

### BR-011 — Installment Amount required

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-recurring-account-screen.md](../../05-ui-ux/recurring/new-recurring-account-screen.md) — Tab 1, field #14 |

**Rule:** Installment Amount (भरणा रक्कम) is a required numeric value (> 0). It is the core Recurring Deposit field — the agreed periodic deposit installment — and is the principal input for the Maturity Amount computation ([BR-013](#br-013--maturity-amount-system-computed-from-scheme-interest-formula)). It is surfaced as हप्ता (Installment) on the Account Register grid (column #17).

**Notes:** Distinct from FD's single lump-sum मुदत ठेव रक्कम ([fixed-deposit BR-009](../fixed-deposit/business-rules.md#br-009--fd-amount-required)) and Daily's दैनिक ठेव रक्कम ([daily BR-008](../daily/business-rules.md#br-008--daily-deposit-amount-required-maturity-fields-optional)) — a Recurring account collects this installment repeatedly at the Deposit Type frequency ([BR-012](#br-012--deposit-type-required-frequency-values-todo)).

---

### BR-012 — Deposit Type required; frequency values TODO

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | TODO |
| Source | [new-recurring-account-screen.md](../../05-ui-ux/recurring/new-recurring-account-screen.md) — Tab 1, field #15 |

**Rule:** Select Deposit Type (भरणा प्रकार निवडा) is a required dropdown selecting the installment collection frequency; it may default from the scheme. The spec provides only the sample value `मासिक` (Monthly). `TODO:` The full frequency value set is not finalized by the bank (confirmed open 2026-07-24 — left as master-data TODO). Candidate values pending confirmation: `मासिक` (Monthly), `तिमाही` (Quarterly), `सहामाही` (Half-yearly), `वार्षिक` (Yearly). Do not hard-code the enum until confirmed; back it with a master-data source.

**Notes:** The chosen frequency, together with Installment Amount ([BR-011](#br-011--installment-amount-required)) and Duration ([BR-007](#br-007--duration-selected-from-scheme-grid-duration-and-rate-auto-filled)), determines the number of installments feeding the Maturity Amount computation ([BR-013](#br-013--maturity-amount-system-computed-from-scheme-interest-formula)).

---

### BR-013 — Maturity Amount system-computed from scheme interest formula

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | Standing Decision 2026-07-24; [new-recurring-account-screen.md](../../05-ui-ux/recurring/new-recurring-account-screen.md) — Tab 1, field #16 |

**Rule:** Maturity Amount (परतीची रक्कम, #16) is an optional read-only calculated Label. **It is computed by the system from the selected scheme's interest formula** — Interest Type / Compounding ([BR-003](#br-003--scheme-derived-attributes-auto-filled-read-only)), Interest Rate ([BR-007](#br-007--duration-selected-from-scheme-grid-duration-and-rate-auto-filled)), Duration ([BR-007](#br-007--duration-selected-from-scheme-grid-duration-and-rate-auto-filled)), Installment Amount ([BR-011](#br-011--installment-amount-required)), and Deposit Type frequency ([BR-012](#br-012--deposit-type-required-frequency-values-todo)). The actor does not enter it. The same computed value is previewed by the [Interest Multiplier](#br-034--interest-multiplier-computes-deposit-interest-and-maturity-amounts) calculator.

**Notes:** Confirmed 2026-07-24 (business decision — system-computed, same approach as the confirmed [FD Maturity Amount derivation](../fixed-deposit/business-rules.md#br-012--maturity-amount-return-date-and-receipt-date-system-computed)); a scheme-grid Maturity Amount reference is used only for fixed-maturity double-money schemes, not the general RD derivation source. `TODO:` The exact day-count/compounding formula (e.g. actual/365, month rounding, per-installment accrual) is not documented in any spec — resolve at DB/API phase. Surfaced as परतीची रक्कम (Return Amount) on the Account Register grid (column #15).

---

### BR-014 — Account Status default and shared values across deposit products

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-recurring-account-screen.md](../../05-ui-ux/recurring/new-recurring-account-screen.md) — Tab 1, field #18; [account-register-screen.md](../../05-ui-ux/recurring/account-register-screen.md) — field #3 |

**Rule:** Select Status (स्थिती निवडा) is required at account creation, defaulting to `चालू` (Active). Allowed values: `चालू`, `बंद` (Closed), `स्थगित` (Suspended). This is the same three-value enum used on [New Savings Account](../../05-ui-ux/savings/new-savings-account-screen.md), [New FD Account](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md), and [New Daily Account](../../05-ui-ux/daily/new-daily-account-screen.md) — implementations share one status domain across deposit-product accounts.

**Notes:** Identical enum to [savings BR-008](../savings/business-rules.md#br-008--account-status-default-and-shared-values-across-deposit-products). Distinct from Customer Status, Scheme Status, and Agent Status — do not merge these status domains.

---

### BR-015 — Advanced Settings visibility role undefined

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | TODO |
| Source | [new-recurring-account-screen.md](../../05-ui-ux/recurring/new-recurring-account-screen.md) — Section: प्रगत सेटिंग्ज (Advanced Settings) |

**Rule:** `TODO:` The Advanced Settings section note states "Visible to users with accounting/admin role or when expanded manually" — the same phrase repeats on New Savings, New FD, and New Daily accounts. No documented domain has resolved what "accounting/admin role" maps to against the platform's three-level permission model ([settings/master BR-017](../settings/master/business-rules.md#br-017--permission-levels-are-all-rights--view-only--no-rights)). Until resolved, treat "or when expanded manually" as the operative behaviour (collapsed-by-default panel, manually expandable by any actor with screen access) and do not gate visibility by an undefined role.

**Notes:** Shared open item with [savings BR-009](../savings/business-rules.md#br-009--advanced-settings-visibility-role-undefined), [fixed-deposit BR-015](../fixed-deposit/business-rules.md#br-015--advanced-settings-visibility-role-undefined), and [daily BR-011](../daily/business-rules.md#br-011--advanced-settings-visibility-role-undefined).

---

### BR-016 — IFSC Code enables bank payout auto-fill

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [new-recurring-account-screen.md](../../05-ui-ux/recurring/new-recurring-account-screen.md) — Tab 1 Advanced, fields #21–#23 |

**Rule:** IFSC Code (आय.एफ.एस.सी. कोड, #21) is optional; when entered it enables bank payout on maturity and auto-fills the read-only Bank Name (बँकेचे नाव, #22) Label. Bank Savings Account No. (बँकेचे बचत खाते क्रमांक, #23) is an optional companion field for the payout account, independent of the CBS Account No. ([BR-005](#br-005--account-no-auto-generated)).

**Notes:** IFSC → Bank Name resolution mechanism (external lookup vs. manual entry) is `TODO:` not specified — same open pattern as [savings BR-011](../savings/business-rules.md#br-011--ifsc-code-enables-bank-payout-auto-fill) and [fixed-deposit BR-014](../fixed-deposit/business-rules.md#br-014--ifsc-code-enables-bank-payout-auto-fill).

---

### BR-017 — Nominee section conditional on Add Nominee checkbox

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [new-recurring-account-screen.md](../../05-ui-ux/recurring/new-recurring-account-screen.md) — Tab 1, field #24 |

**Rule:** Add Nominee (वारसदार जोडा) is unchecked by default. When checked, Tab 2 (वारसदार) becomes visible in the tab bar; when unchecked, Tab 2 is hidden and skipped during Next/Back navigation, and no nominee data is persisted.

**Notes:** Same conditional pattern as [savings BR-012](../savings/business-rules.md#br-012--nominee-section-conditional-on-add-nominee-checkbox), [fixed-deposit BR-018](../fixed-deposit/business-rules.md#br-018--nominee-section-conditional-on-add-nominee-checkbox), and [daily BR-013](../daily/business-rules.md#br-013--nominee-section-conditional-on-add-nominee-checkbox).

---

### BR-018 — Joint Holder section conditional on Add Joint Holder checkbox

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [new-recurring-account-screen.md](../../05-ui-ux/recurring/new-recurring-account-screen.md) — Tab 1, field #25 |

**Rule:** Add Joint Holder (संयुक्त खातेदार जोडा) is unchecked by default. When checked, Tab 3 (संयुक्त खातेदार) becomes visible in the tab bar; when unchecked, Tab 3 is hidden and skipped during Next/Back navigation, and no joint holder data is persisted.

**Notes:** Same conditional pattern as [savings BR-013](../savings/business-rules.md#br-013--joint-holder-section-conditional-on-add-joint-holder-checkbox) and [fixed-deposit BR-019](../fixed-deposit/business-rules.md#br-019--joint-holder-section-conditional-on-add-joint-holder-checkbox).

---

### BR-019 — Nominee lookup resolves to existing or quick-added Customer

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [new-recurring-account-screen.md](../../05-ui-ux/recurring/new-recurring-account-screen.md) — Tab 2, field #1 |

**Rule:** The Nominee Search field is a Customer Autocomplete (`entityType: customer`) with the **+ नवीन ग्राहक जोडा** companion action per [quick-add-customer-pattern.md](../../05-ui-ux/shared/quick-add-customer-pattern.md). A nominee is always a Customer record — resolved from existing master data or created via the minimal quick-add popup. Nominee Details (fields #2–#5) become visible only after a nominee customer is resolved.

**Notes:** Shares the `app-nominee-form` / `app-nominee-grid` components with Savings/FD/Daily — not a Recurring-specific implementation ([savings BR-014](../savings/business-rules.md#br-014--nominee-lookup-resolves-to-existing-or-quick-added-customer)).

---

### BR-020 — Nominee Relation reuses canonical Membership list

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | Confirmed |
| Source | [new-recurring-account-screen.md](../../05-ui-ux/recurring/new-recurring-account-screen.md) — Tab 2, field #2; [new-membership-screen.md](../../05-ui-ux/membership/new-membership-screen.md) — Tab 3 |

**Rule:** Nominee Relation (नाते) values must come from the single canonical Relation list finalized on New Membership Tab 3: `मुलगा`, `पुतण्या`, `मुली`, `मुलगा - पती`, `पति व मुलगा`, `वरील प्रमाणे`, `बायको`, `मैत्रीण`, `केअरटेकर`, `लहान भाऊ`, `स्वतः`, `पत्नी`, `पती`. Do not maintain a Recurring-specific Relation list.

**Notes:** Cross-domain dependency — the Membership operational domain (`02-business-domains/membership/`) is not yet documented (Phase 3); this list currently exists only in the UI spec, reused by Customer, Savings, FD, and Daily. Migrate the canonical definition to Membership's business-rules.md when authored and update referencing domains ([savings BR-015](../savings/business-rules.md#br-015--nominee-relation-reuses-canonical-membership-list)).

---

### BR-021 — Nominee Percentage optional; Nomination Date and Age system-derived

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-recurring-account-screen.md](../../05-ui-ux/recurring/new-recurring-account-screen.md) — Tab 2, fields #3–#5 |

**Rule:** Nominee Percentage (टक्केवारी, #3) is optional (e.g. `100`). Nomination Date (नामांकन दिनांक, #4) is a read-only Label set to the system date. Age at Nomination (नामांकन करताना वय, #5) is a read-only Label auto-calculated from the resolved nominee's Date of Birth. None of these three are directly enterable.

**Notes:** Whether multiple nominees' Percentage must total 100% is a non-binding UX suggestion, not a confirmed rule ([ux-optimization.md](../../05-ui-ux/recurring/ux-optimization.md) Nominee Tab suggestion #2). Same as [savings BR-016](../savings/business-rules.md#br-016--nominee-percentage-optional-nomination-date-and-age-system-derived).

---

### BR-022 — Joint Holder Guardian and Customer fields; Add validates selection

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-recurring-account-screen.md](../../05-ui-ux/recurring/new-recurring-account-screen.md) — Tab 3, fields #1–#2 |

**Rule:** On Tab 3, Guardian (पालक, #1) is an optional checkbox and Select Customer (ग्राहक निवडा, #2) is an optional Customer Autocomplete. The **+ जोड** (Add) action validates that a customer has been resolved before appending a row to the Joint Holder grid (`app-joint-holder-grid`). काढा (Remove) removes the selected grid row; निर्यात (Export) exports the grid. The Introducer section from Membership is omitted for deposit products per bank review.

**Notes:** Same rule shape as [savings BR-017](../savings/business-rules.md#br-017--joint-holder-guardian-and-customer-fields-add-validates-selection) and [fixed-deposit BR-023](../fixed-deposit/business-rules.md#br-023--joint-holder-guardian-and-customer-fields-add-validates-selection).

---

### BR-023 — Account Operation Instructions required with defined values

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-recurring-account-screen.md](../../05-ui-ux/recurring/new-recurring-account-screen.md) — Tab 3, field #3 |

**Rule:** Account Operation Instructions (खाते चालविण्याची सूचना) is required with default `स्वतः` (Self). Allowed values: `फक्त प्रमुख खातेदार` (Only Primary Holder), `फक्त संयुक्त खातेदार` (Only Joint Holder), `दोन्ही खातेदार आवश्यक` (Both Holders Required), `दोघांपैकी कोणीही` (Either Holder), `स्वतः` (Self).

**Notes:** This field lives on Tab 3, which is itself conditional on [BR-018](#br-018--joint-holder-section-conditional-on-add-joint-holder-checkbox). `TODO:` The persisted value when Tab 3 is skipped (single-holder account) is not stated — same open item as [savings BR-018](../savings/business-rules.md#br-018--account-operation-instructions-required-with-defined-values) and [fixed-deposit BR-024](../fixed-deposit/business-rules.md#br-024--account-operation-instructions-required-with-defined-values).

---

### BR-024 — New Recurring Account wizard atomic save on create

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | Standing Decision (deposit wizards, 2026-07-24); [new-recurring-account-screen.md](../../05-ui-ux/recurring/new-recurring-account-screen.md) — Tabs 1–3, footer actions |

**Rule:** On create, New Recurring Account persists the Account, Nominee(s) (if Tab 2 enabled), and Joint Holder(s) (if Tab 3 enabled) only when the actor clicks **जतन करा** (Save) on the final visible tab, after all visible tabs pass validation. **पुढे** (Next) and **मागे** (Back) must not write partial records. **रीसेट** (Reset) clears wizard state without persisting.

**Notes:** Matches the atomic-save pattern confirmed for [savings BR-019](../savings/business-rules.md#br-019--new-savings-account-wizard-atomic-save-on-create), [fixed-deposit BR-029](../fixed-deposit/business-rules.md#br-029--new-fd-account-wizard-atomic-save-on-create), [daily BR-020](../daily/business-rules.md#br-020--new-daily-account-wizard-atomic-save-on-create), and all Settings/Customer wizards.

---

### BR-025 — Recurring screens use Master permission levels

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | Confirmed |
| Source | [settings/master business-rules.md](../settings/master/business-rules.md#br-017--permission-levels-are-all-rights--view-only--no-rights) BR-017 |

**Rule:** Access to New Recurring Account, Recurring Account Register, and Recurring Interest Multiplier follows Master permission levels: **All Rights** (full edit/save), **View Only** (read-only; Save/Add/Remove/Export-persisting actions hidden), **No Rights** (navigation blocked). Do not redefine permission semantics in this domain.

**Notes:** The Interest Multiplier गणना करा (Calculate) action is a read-only computation ([BR-032](#br-032--interest-multiplier-is-a-scheme-based-calculator-with-no-persistence)); View Only actors may run it but persist nothing. Same model as [savings BR-020](../savings/business-rules.md#br-020--savings-screens-use-master-permission-levels) and [fixed-deposit BR-030](../fixed-deposit/business-rules.md#br-030--fd-screens-use-master-permission-levels).

---

## Rules — Account Register

### BR-026 — Organization auto-fill header from session

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [account-register-screen.md](../../05-ui-ux/recurring/account-register-screen.md) — Auto-fill header |

**Rule:** संस्था (Organization) is a read-only header Label sourced from the tenant session (see [glossary.md](../../00-project-overview/glossary.md) Organization). It is not repeated as a filter field and is not enterable.

**Notes:** Same pattern as [daily BR-028](../daily/business-rules-part2.md#br-028--organization-auto-fill-header-from-session) and [fixed-deposit BR-031](../fixed-deposit/business-rules.md#br-031--account-management-search-fields-all-optional-organization-auto-filled).

---

### BR-027 — Account Register primary search fields all optional

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [account-register-screen.md](../../05-ui-ux/recurring/account-register-screen.md) — Primary Search, fields #1–#8 |

**Rule:** All Primary Search fields (Branch, Scheme, Status default `चालू`, Account No. From/To, Account Holder, Customer No. From/To) are optional. Clicking **दाखवा** (Show) with no filters returns results per the actor's entitled scope. The legacy अतिरिक्त शोध पर्याय (Advanced Search) link is out of scope (no stub, no TODO).

**Notes:** Branch-scoping of results for actors with limited branch rights is `TODO:` unresolved — same open pattern as [savings BR-021](../savings/business-rules.md#br-021--account-register-primary-search-fields-all-optional), [daily BR-029](../daily/business-rules-part2.md#br-029--account-register-primary-search-fields-all-optional), and [fixed-deposit BR-031](../fixed-deposit/business-rules.md#br-031--account-management-search-fields-all-optional-organization-auto-filled).

---

### BR-028 — Results grid legend: loan-linked and matured highlighting

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | TODO |
| Source | [account-register-screen.md](../../05-ui-ux/recurring/account-register-screen.md) — Results Grid legend |

**Rule:** `TODO:` The Account Register grid renders row highlighting per its legend — **Pink** = कर्ज असलेली खाती (accounts with a loan against the RD), **Blue** = मुदत संपलेली खाती (matured accounts). The matured highlight is derivable from Maturity Date ([BR-010](#br-010--maturity-date-system-calculated)) vs. current date. The loan-linked (pink) highlight depends on the Loan / Deposit Loan domain (`02-business-domains/loan/`), which is not yet documented (Phase 3), so the precise linkage (a Deposit Loan lien against this RD vs. any loan held by the same customer) cannot be confirmed. Resolve when the Loan domain is authored.

**Notes:** The same pink loan-linked legend appears on the Savings, Daily, and FD registers ([savings BR-022](../savings/business-rules.md#br-022--loan-linked-accounts-filter-depends-on-undocumented-loan-domain), [fixed-deposit BR-032](../fixed-deposit/business-rules.md#br-032--register-grid-legend-loan-linked-and-matured-accounts)). Recurring uses legend-only styling (no explicit filter checkbox), same as FD and Daily.

---

### BR-029 — काढा (Remove) deletes the account registration row

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [account-register-screen.md](../../05-ui-ux/recurring/account-register-screen.md) — Sidebar actions |

**Rule:** The Account Register sidebar action काढा (Remove) deletes the selected account registration row — it does not merely hide the row from the current view. This is the same semantics as काढा on the FD/Daily registers and the वगळा (Exclude) action on the Savings register ([savings BR-024](../savings/business-rules.md#br-024--वगळा-exclude-is-equivalent-to-काढा-remove)). There is no Close Account action on the Recurring register — only तपशील (Details), निर्यात (Export), काढा (Remove), and खाते उतारा (Account Statement).

**Notes:** `TODO:` Whether Remove requires a confirmation dialog, and whether it is blocked for accounts that already have posted ledger (installment) transactions (vs. only accounts created in error with zero transaction history), is not stated — confirm before implementation, since removing a financial account differs materially from removing a non-financial registration row. Same open item as [fixed-deposit BR-034](../fixed-deposit/business-rules.md#br-034--काढा-remove-deletes-the-account-registration-row) and [daily BR-032](../daily/business-rules-part2.md#br-032--काढा-remove-deletes-the-account-registration-row).

---

### BR-030 — Account Register follows interactive reporting standard

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | Confirmed |
| Source | [account-register-screen.md](../../05-ui-ux/recurring/account-register-screen.md); [business-goals.md](../../00-project-overview/business-goals.md) BG-005 |

**Rule:** Account Register implements the platform-wide interactive reporting standard (BG-005): Primary Search filters, a results grid with pagination (पहिले, मागील, पुढील) and an एकूण नोंदी record count, and Export. Additional detail beyond the base 20-column grid is reached via the तपशील (Details) sidebar action ([BR-031](#br-031--account-details-and-account-statement-lack-dedicated-specs)) rather than shown by default.

**Notes:** Same standard as [savings BR-023](../savings/business-rules.md#br-023--account-register-grid-and-search-follow-interactive-reporting-standard) and [fixed-deposit BR-033](../fixed-deposit/business-rules.md#br-033--account-management-follows-interactive-reporting-standard).

---

### BR-031 — Account Details and Account Statement lack dedicated specs

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | TODO |
| Source | [account-register-screen.md](../../05-ui-ux/recurring/account-register-screen.md) — Sidebar actions तपशील, खाते उतारा |

**Rule:** `TODO:` तपशील (Details) opens account detail in context with no separate Recurring Account Information screen spec. खाते उतारा (Account Statement) has no dedicated report spec — [reports/overview.md](../../05-ui-ux/reports/overview.md) documents a **Loan** Account Statement report only, with no equivalent for Savings/FD/Daily/Recurring deposit accounts. Both gaps should be resolved by authoring the missing specs or confirming reuse of an existing pattern.

**Notes:** Same gap as [savings BR-026](../savings/business-rules.md#br-026--account-details-and-account-statement-lack-dedicated-specs), [fixed-deposit BR-035](../fixed-deposit/business-rules.md#br-035--account-statement-and-details-lack-dedicated-specs), and [daily BR-033](../daily/business-rules-part2.md#br-033--account-register-follows-interactive-reporting-detail-and-statement-gaps).

---

## Rules — Interest Multiplier

### BR-032 — Interest Multiplier is a scheme-based calculator with no persistence

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [interest-multiplier-screen.md](../../05-ui-ux/recurring/interest-multiplier-screen.md) — Purpose; Input Fields; Actions |

**Rule:** Recurring Interest Multiplier (व्याज गुणक) is a stateless calculator. Select Scheme (योजना निवडा, #1) is required and loads from Recurring schemes (Settings → नवीन योजना, Scheme Type = रिकरिंग). गणना करा (Calculate) produces read-only outputs; पुनर्रचना करा (Reset) clears the form. The screen creates no account and persists nothing; निर्यात करा (Export) exports the interest-breakdown grid only.

**Notes:** Same calculator pattern (no persistence) as the [FD Interest Multiplier](../fixed-deposit/business-rules.md#br-041--interest-multiplier-is-a-scheme-based-calculator-with-no-persistence) and [Daily Interest Multiplier](../daily/business-rules-part2.md#br-044--deposit-amount-required-calculation-is-preview-only); the calculation service is shared where formulas match.

---

### BR-033 — Interest Multiplier conditional field visibility

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [interest-multiplier-screen.md](../../05-ui-ux/recurring/interest-multiplier-screen.md) — Input Fields, fields #2–#6 |

**Rule:** The Simple / Compound radio (सरळ / चक्रव्याज, #2) is hidden until a Scheme is selected (#1) and defaults from the scheme. The Compounding Frequency radio (मासिक / तिमाही / सहामाही / वार्षिक, #3) is visible **only** when field #2 = Compound. Monthly Deposit Amount (मासिक ठेव रक्कम, #4) is required. Duration (Months) (#5; default `60`) and Interest Rate (% p.a.) (#6; default `12.37`) auto-fill as read-only Labels from the scheme but allow override.

**Notes:** Same conditional-visibility pattern as [fixed-deposit BR-042](../fixed-deposit/business-rules.md#br-042--interest-multiplier-conditional-field-visibility) and [daily BR-043](../daily/business-rules-part2.md#br-043--interest-multiplier-scheme-required-duration-and-rate-auto-filled).

---

### BR-034 — Interest Multiplier computes deposit, interest, and maturity amounts

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [interest-multiplier-screen.md](../../05-ui-ux/recurring/interest-multiplier-screen.md) — Output Labels #7–#9; Interest Breakdown Grid |

**Rule:** गणना करा (Calculate) computes and displays three read-only output Labels — ठेव रक्कम (Deposit Amount, #7), व्याज रक्कम (Interest Amount, #8), and मुदतपूर्ती रक्कम (Maturity Amount, #9) — using the Monthly Deposit Amount, Duration, Interest Rate, and the scheme's Simple/Compound basis and frequency ([BR-033](#br-033--interest-multiplier-conditional-field-visibility)). It also populates the व्याज प्रकार (Interest Breakdown) grid with per-period rows (अ. क्र., ठेव रक्कम, मासिक व्याज, पोस्टिंग व्याज, मासिक शिल्लक).

**Notes:** Uses the same Recurring interest formula that computes the New Recurring Account Maturity Amount ([BR-013](#br-013--maturity-amount-system-computed-from-scheme-interest-formula)). `TODO:` The precise day-count/compounding formula is not documented (shared open item with BR-013) — resolve at DB/API phase.

---

## Related Documents

- [overview.md](overview.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [changelog.md](changelog.md)
- [../../05-ui-ux/recurring/new-recurring-account-screen.md](../../05-ui-ux/recurring/new-recurring-account-screen.md)
- [../../05-ui-ux/recurring/account-register-screen.md](../../05-ui-ux/recurring/account-register-screen.md)
- [../../05-ui-ux/recurring/interest-multiplier-screen.md](../../05-ui-ux/recurring/interest-multiplier-screen.md)
- [../savings/business-rules.md](../savings/business-rules.md)
- [../fixed-deposit/business-rules.md](../fixed-deposit/business-rules.md)
- [../daily/business-rules.md](../daily/business-rules.md)
- [../settings/schemes/business-rules.md](../settings/schemes/business-rules.md)
- [../settings/master/business-rules.md](../settings/master/business-rules.md)
- [../../00-project-overview/glossary.md](../../00-project-overview/glossary.md)
