# Business Rules — Fixed Deposit

## Purpose

Numbered business rules for the **मुदत ठेव (Fixed Deposit)** operational module: New FD Account (4-tab wizard), FD Account Management (Register + Renewal List), Deposit Loan Installment Payment, and FD Interest Multiplier. Every rule cites its UI spec source. Rules marked **TODO** require business confirmation before implementation.

**Sources (current, non-superseded specs only):**

- [new-fd-account-screen.md](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md)
- [fd-account-management-screen.md](../../05-ui-ux/fixed-deposit/fd-account-management-screen.md)
- [deposit-loan-installment-payment-screen.md](../../05-ui-ux/fixed-deposit/deposit-loan-installment-payment-screen.md)
- [fd-interest-multiplier-screen.md](../../05-ui-ux/fixed-deposit/fd-interest-multiplier-screen.md)

**Superseded specs excluded per this generation request** (see [ux-optimization.md](../../05-ui-ux/fixed-deposit/ux-optimization.md)): `fd-transaction-screen.md` → [deposit-account-transaction-screen.md](../../05-ui-ux/accounting/deposit-account-transaction-screen.md); `fd-manual-interest-calculation-screen.md` → [manual-interest-management-screen.md](../../05-ui-ux/accounting/manual-interest-management-screen.md); `fd-account-register-screen.md` and `account-renewal-list-screen.md` → consolidated into [fd-account-management-screen.md](../../05-ui-ux/fixed-deposit/fd-account-management-screen.md). FD deposit/withdrawal transactions and manual interest are documented under the Accounting domain (Phase 3), not here.

## Rule Index

| ID | Title | Type | Status |
| :--- | :--- | :--- | :---: |
| [BR-001](#br-001--customer-must-exist-before-fd-account-can-be-opened) | Customer must exist before FD account can be opened | Eligibility | Confirmed |
| [BR-002](#br-002--scheme-required-and-loaded-from-fd-scheme-master) | Scheme required and loaded from FD scheme master | Validation | Confirmed |
| [BR-003](#br-003--scheme-derived-attributes-auto-filled-read-only) | Scheme-derived attributes auto-filled read-only | Workflow | Confirmed |
| [BR-004](#br-004--agent-and-sales-agent-optional-agent-scoped-to-agent-branch) | Agent and Sales Agent optional; Agent scoped to Agent Branch | Validation | Confirmed |
| [BR-005](#br-005--account-no-auto-generated) | Account No. auto-generated | Workflow | Confirmed |
| [BR-006](#br-006--account-type-required-with-defined-values) | Account Type required with defined values | Validation | Confirmed |
| [BR-007](#br-007--interest-rate-slab-required-and-drives-duration) | Interest Rate Slab required and drives Duration | Validation | Confirmed |
| [BR-008](#br-008--current-date-defaults-to-system-date) | Current Date defaults to system date | Workflow | Confirmed |
| [BR-009](#br-009--fd-amount-required) | FD Amount required | Validation | Confirmed |
| [BR-010](#br-010--interest-rate-auto-filled-from-slab-admin-override-role-undefined) | Interest Rate auto-filled from slab; admin override role undefined | Eligibility | TODO |
| [BR-011](#br-011--interest-start-date-required) | Interest Start Date required | Validation | Confirmed |
| [BR-012](#br-012--maturity-amount-return-date-and-receipt-date-system-computed) | Maturity Amount, Return Date, and Receipt Date system-computed | Workflow | Confirmed |
| [BR-013](#br-013--account-status-default-and-shared-values-across-deposit-products) | Account Status default and shared values across deposit products | Validation | Confirmed |
| [BR-014](#br-014--ifsc-code-enables-bank-payout-auto-fill) | IFSC Code enables bank payout auto-fill | Workflow | Confirmed |
| [BR-015](#br-015--advanced-settings-visibility-role-undefined) | Advanced Settings visibility role undefined | Cross-cutting | TODO |
| [BR-016](#br-016--receipt-prefix-and-receipt-number-required) | Receipt Prefix and Receipt Number required | Validation | Confirmed |
| [BR-017](#br-017--multiple-fd-workflow-semantics-undefined) | Multiple FD workflow semantics undefined | Workflow | TODO |
| [BR-018](#br-018--nominee-section-conditional-on-add-nominee-checkbox) | Nominee section conditional on Add Nominee checkbox | Eligibility | Confirmed |
| [BR-019](#br-019--joint-holder-section-conditional-on-add-joint-holder-checkbox) | Joint Holder section conditional on Add Joint Holder checkbox | Eligibility | Confirmed |
| [BR-020](#br-020--nominee-lookup-resolves-to-existing-or-quick-added-customer) | Nominee lookup resolves to existing or quick-added Customer | Eligibility | Confirmed |
| [BR-021](#br-021--nominee-relation-reuses-canonical-membership-list) | Nominee Relation reuses canonical Membership list | Cross-cutting | Confirmed |
| [BR-022](#br-022--nominee-percentage-optional-nomination-date-and-age-system-derived) | Nominee Percentage optional; Nomination Date and Age system-derived | Validation | Confirmed |
| [BR-023](#br-023--joint-holder-guardian-and-customer-fields-add-validates-selection) | Joint Holder Guardian and Customer fields; Add validates selection | Validation | Confirmed |
| [BR-024](#br-024--account-operation-instructions-required-with-defined-values) | Account Operation Instructions required with defined values | Validation | Confirmed |
| [BR-025](#br-025--interest-reinvestment-enables-si-reinvestment-frequency) | Interest Reinvestment enables S.I. reinvestment frequency | Eligibility | Confirmed |
| [BR-026](#br-026--auto-renewal-and-renewal-mutually-exclusive-renewal-type-radios) | Auto Renewal and Renewal mutually exclusive; renewal-type radios | Eligibility | Confirmed |
| [BR-027](#br-027--interest-transfer-enables-gl-holder-and-frequency-routing) | Interest Transfer enables GL, holder, and frequency routing | Eligibility | Confirmed |
| [BR-028](#br-028--account-closing-gl-routing-enabled-by-checkbox) | Account Closing GL routing enabled by checkbox | Eligibility | Confirmed |
| [BR-029](#br-029--new-fd-account-wizard-atomic-save-on-create) | New FD Account wizard atomic save on create | Workflow | Confirmed |
| [BR-030](#br-030--fd-screens-use-master-permission-levels) | FD screens use Master permission levels | Cross-cutting | Confirmed |
| [BR-031](#br-031--account-management-search-fields-all-optional-organization-auto-filled) | Account Management search fields all optional; Organization auto-filled | Eligibility | Confirmed |
| [BR-032](#br-032--register-grid-legend-loan-linked-and-matured-accounts) | Register grid legend: loan-linked and matured accounts | Cross-cutting | TODO |
| [BR-033](#br-033--account-management-follows-interactive-reporting-standard) | Account Management follows interactive reporting standard | Cross-cutting | Confirmed |
| [BR-034](#br-034--काढा-remove-deletes-the-account-registration-row) | काढा (Remove) deletes the account registration row | Workflow | Confirmed |
| [BR-035](#br-035--account-statement-and-details-lack-dedicated-specs) | Account Statement and Details lack dedicated specs | Cross-cutting | TODO |
| [BR-036](#br-036--renewal-list-is-read-and-export-only) | Renewal List is read/export only | Workflow | Confirmed |
| [BR-037](#br-037--deposit-loan-must-exist-before-installment-payment) | Deposit Loan must exist before installment payment | Eligibility | Confirmed |
| [BR-038](#br-038--installment-interest-tab-requires-mode-gl-and-a-customer-or-account-holder-lookup) | Installment Interest tab requires mode, GL, and a Customer or Account Holder lookup | Validation | Confirmed |
| [BR-039](#br-039--calculate-interest-populates-installment-grid-set-applies) | Calculate Interest populates installment grid; Set applies | Workflow | TODO |
| [BR-040](#br-040--deposit-loan-installment-tabs-26-not-captured) | Deposit Loan Installment Tabs 2–6 not captured | Cross-cutting | TODO |
| [BR-041](#br-041--interest-multiplier-is-a-scheme-based-calculator-with-no-persistence) | Interest Multiplier is a scheme-based calculator with no persistence | Workflow | Confirmed |
| [BR-042](#br-042--interest-multiplier-conditional-field-visibility) | Interest Multiplier conditional field visibility | Validation | Confirmed |
| [BR-043](#br-043--interest-multiplier-computes-interest-rate-or-duration) | Interest Multiplier computes Interest Rate or Duration | Workflow | Confirmed |

---

## Rules

### BR-001 — Customer must exist before FD account can be opened

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [new-fd-account-screen.md](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md) — Tab 1, field #1 |

**Rule:** New FD Account Tab 1 requires selecting an **existing** Customer via Autocomplete (`entityType: customer`). The screen must not create a new Customer identity — a person must first be registered via [New Customer](../../05-ui-ux/customer/new-customer-screen.md) before an FD account can be opened. After resolve, the customer summary (सभासद प्रकार, सभासद खाते क्र., वय, ग्राहक शाखा, पॅन क्र., विशेष सूचना) is shown read-only.

**Notes:** Same cross-screen dependency shape as [savings BR-001](../savings/business-rules.md#br-001--customer-must-exist-before-savings-account-can-be-opened) and [customer BR-026](../customer/business-rules.md#br-026--customer-must-exist-before-other-account-can-be-opened).

---

### BR-002 — Scheme required and loaded from FD scheme master

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-fd-account-screen.md](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md) — Tab 1, field #2 |

**Rule:** Select Scheme (योजना निवडा) is required and loads dynamically from Settings → नवीन योजना where Scheme Type = `मुदत ठेव` (FD). Placeholder/no selection is not a valid saved value. The full list is scheme master data — not a fixed enum. Samples: `मुदत ठेव`, `दामदुप्पट`, `दाम दुप्पट ठेव (कर्जातील)`, `पेंशन ठेव`.

**Notes:** Dependency on [settings/schemes business-rules.md](../settings/schemes/business-rules.md) — FD scheme creation ([BR-022](../settings/schemes/business-rules.md#br-022--fd-required-identity-fields) FD identity fields, [BR-020](../settings/schemes/business-rules.md#br-020--duration-and-rates-row-required-fields) duration & rates incl. Maturity Amount) must exist before an account can be opened under it. Whether a scheme's Status blocks new account opening is inherited from the schemes domain (open item), not re-litigated here.

---

### BR-003 — Scheme-derived attributes auto-filled read-only

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [new-fd-account-screen.md](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md) — Tab 1, fields #3–#5 |

**Rule:** On Scheme selection, Closed / Open Ended (क्लोज / ओपन एंडेड, #3), Interest Type (व्याज प्रकार, #4), and Compounding (कम्पाउंडिंग, #5) are populated as read-only Labels from the selected scheme's configuration. They are not directly editable on this screen.

**Notes:** These derive from scheme rules [schemes BR-018](../settings/schemes/business-rules.md#br-018--open-ended-and-close-ended-mutually-exclusive-daily-fd-recurring) (Open/Close Ended) and [schemes BR-019](../settings/schemes/business-rules.md#br-019--compound-interest-frequency-required-when-compounding). Interest Type/Compounding also feed the Maturity Amount computation in [BR-012](#br-012--maturity-amount-return-date-and-receipt-date-system-computed).

---

### BR-004 — Agent and Sales Agent optional; Agent scoped to Agent Branch

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-fd-account-screen.md](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md) — Tab 1, fields #6–#7; Advanced, fields #24–#25 |

**Rule:** Select Agent Branch (#6), Select Agent (#7), Select Sales Agent Branch (#24), and Select Sales Agent (#25) are all optional Autocomplete fields. When an Agent/Sales Agent is selected, its lookup is scoped to the corresponding Agent Branch field. Agent and Sales Agent both resolve against the **Agent** master (एजंट) owned by the Daily/Pigmy module.

**Notes:** Agent master is owned by the Daily module ([glossary.md](../../00-project-overview/glossary.md) Agent; [new-agent-screen.md](../../05-ui-ux/daily/new-agent-screen.md)) — the Daily operational domain is not yet documented (Phase 3), so the exact Agent eligibility/status filter applied here is deferred to that domain.

---

### BR-005 — Account No. auto-generated

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [new-fd-account-screen.md](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md) — Tab 1, field #8 |

**Rule:** Account No. (खाते क्र.) is system-generated and displayed as a read-only Label after Save. It is not a lookup field — excluded from entity-autocomplete consolidation ([entity-autocomplete-pattern.md](../../05-ui-ux/shared/entity-autocomplete-pattern.md) Exclusions).

**Notes:** Generation algorithm (global vs. per-branch vs. per-scheme sequence) is `TODO:` not yet documented — same open-item pattern as [savings BR-004](../savings/business-rules.md#br-004--account-no-auto-generated), [customer BR-001](../customer/business-rules.md#br-001--customer-number-auto-generated), and [settings/accounting BR-022](../settings/accounting/business-rules.md#br-022--gl-head-number-generation-algorithm).

---

### BR-006 — Account Type required with defined values

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-fd-account-screen.md](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md) — Tab 1, field #9 |

**Rule:** Account Type (खाते प्रकार) is required. Allowed values are the FD account-type list shared with [New Scheme](../../05-ui-ux/settings/schemes/new-scheme-screen.md): `सामान्य खाते`, `ज्येष्ठ नागरिक खाते`, `महिला`, `विधवा`, `अपंग`, `दुसरी संस्था`, `नोकर`, `स्वातंत्र्यसैनिक`, `अति ज्येष्ठ नागरिक`. The Interest Rate Slab ([BR-007](#br-007--interest-rate-slab-required-and-drives-duration)) is filtered by Account Type because scheme duration/benefit rows are keyed by account type.

**Notes:** This is an account-classification enum, distinct from Customer Type ([customer glossary](../../00-project-overview/glossary.md#customer-ग्राहक)) and Account **Status** ([BR-013](#br-013--account-status-default-and-shared-values-across-deposit-products)).

---

### BR-007 — Interest Rate Slab required and drives Duration

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-fd-account-screen.md](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md) — Tab 1, fields #10–#12 |

**Rule:** Interest Rate Slab (व्याज दर स्लॅब, #10) is required and is loaded from the selected scheme's Duration & Rates grid (कालावधी + व्याज दर + खाते प्रकार rows). Default `निवडा` is invalid. On slab selection, Duration (Months) (#11) and Duration (Days) (#12) auto-fill as read-only Labels, and Interest Rate ([BR-010](#br-010--interest-rate-auto-filled-from-slab-admin-override-role-undefined)) is populated from the slab.

**Notes:** Direct dependency on [settings/schemes BR-020](../settings/schemes/business-rules.md#br-020--duration-and-rates-row-required-fields) — for FD, each Duration & Rates row requires Duration, Duration Type, Maturity Amount, and Interest Rate (p.a. %).

---

### BR-008 — Current Date defaults to system date

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [new-fd-account-screen.md](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md) — Tab 1, field #13 |

**Rule:** Current Date (चालू दिनांक) defaults to the system date and is editable. It is persisted and surfaced as चालू दिनांक (Start Date) on the [Account Management](../../05-ui-ux/fixed-deposit/fd-account-management-screen.md) Register grid (column #8).

---

### BR-009 — FD Amount required

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-fd-account-screen.md](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md) — Tab 1, field #14 |

**Rule:** मुदत ठेव रक्कम (FD Amount, Rs.) is a required numeric value (> 0). It is the principal used for Maturity Amount computation ([BR-012](#br-012--maturity-amount-return-date-and-receipt-date-system-computed)) and is shown as मुदत ठेव रक्कम on the Register grid (column #12).

---

### BR-010 — Interest Rate auto-filled from slab; admin override role undefined

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | TODO |
| Source | [new-fd-account-screen.md](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md) — Tab 1, field #15 |

**Rule:** Interest Rate (व्याज दर) is a required read-only Label auto-filled from the selected slab ([BR-007](#br-007--interest-rate-slab-required-and-drives-duration)). The spec states "override requires admin role," but this platform defines only three permission levels — All Rights / View Only / No Rights ([settings/master BR-017](../settings/master/business-rules.md#br-017--permission-levels-are-all-rights--view-only--no-rights)) — plus a Super User bypass ([settings/master BR-012](../settings/master/business-rules.md#br-012--super-user-permission-bypass)). `TODO:` Confirm which permission (or a new role concept) satisfies "admin role" for this override, and whether it also governs [BR-015](#br-015--advanced-settings-visibility-role-undefined). Same unresolved item as [savings BR-005](../savings/business-rules.md#br-005--interest-rate-auto-filled-from-scheme-admin-override-role-undefined).

---

### BR-011 — Interest Start Date required

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-fd-account-screen.md](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md) — Tab 1, field #16 |

**Rule:** व्याज चालू दिनांक (Interest Start Date) is required. It is the date from which interest accrual begins and is surfaced as व्याज सुरु दिनांक (Interest Start Date) on the Register grid (column #9). The spec does not state whether it may differ from Current Date ([BR-008](#br-008--current-date-defaults-to-system-date)); both are captured independently.

---

### BR-012 — Maturity Amount, Return Date, and Receipt Date system-computed

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [new-fd-account-screen.md](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md) — Tab 1, fields #17–#19 |

**Rule:** मुदतपूर्ती रक्कम (Maturity Amount, #17), परतीची दिनांक (Return Date, #18), and पावती तारीख (Receipt Date, #19) are read-only calculated Labels. **Maturity Amount is computed by the system from the selected scheme's interest formula** — Interest Type / Compounding ([BR-003](#br-003--scheme-derived-attributes-auto-filled-read-only)), Interest Rate ([BR-010](#br-010--interest-rate-auto-filled-from-slab-admin-override-role-undefined)), Duration ([BR-007](#br-007--interest-rate-slab-required-and-drives-duration)), and FD Amount ([BR-009](#br-009--fd-amount-required)). Return Date is derived from Interest Start Date ([BR-011](#br-011--interest-start-date-required)) plus Duration. The scheme's Duration & Rates "Maturity Amount" column ([schemes BR-020](../settings/schemes/business-rules.md#br-020--duration-and-rates-row-required-fields)) is a **reference value used only for fixed-maturity double-money schemes** (`दामदुप्पट` / `कॅश सर्टिफिकेट`), not the general derivation source.

**Notes:** Confirmed 2026-07-24 (business decision — computed, not taken from grid except for double-money schemes). `TODO:` The exact day-count/compounding formula (e.g. actual/365, month rounding) is not documented in any spec — resolve at DB/API phase. The same interest formula backs the [Interest Multiplier](#br-043--interest-multiplier-computes-interest-rate-or-duration) calculator.

---

### BR-013 — Account Status default and shared values across deposit products

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-fd-account-screen.md](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md) — Tab 1, field #20; [fd-account-management-screen.md](../../05-ui-ux/fixed-deposit/fd-account-management-screen.md) — Tab 1, field #3 |

**Rule:** स्थिती (Status) defaults to `चालू` (Active). Allowed values: `चालू`, `बंद` (Closed), `स्थगित` (Suspended). This is the same three-value enum used on [New Savings Account](../../05-ui-ux/savings/new-savings-account-screen.md) ([savings BR-008](../savings/business-rules.md#br-008--account-status-default-and-shared-values-across-deposit-products)), New Daily Account, and New Recurring Account — implementations should share one status domain across deposit-product accounts.

**Notes:** Distinct from Customer Status (8-value enum, [customer BR-008](../customer/business-rules.md#br-008--customer-status-required-with-defined-values)) and Scheme Status ([settings/schemes BR-009](../settings/schemes/business-rules.md#br-009--scheme-status-required-with-defined-values)). Do not merge these status domains.

---

### BR-014 — IFSC Code enables bank payout auto-fill

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [new-fd-account-screen.md](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md) — Tab 1, fields #21–#23 |

**Rule:** IFSC Code (आय.एफ.एस.सी. कोड, #21) is optional; when entered it enables bank payout and auto-fills the read-only Bank Name (बँकेचे नाव, #22) Label. Bank Savings Account No. (बँकेचे बचत खाते क्रमांक, #23) is an optional companion field for the payout account, independent of the CBS Account No. ([BR-005](#br-005--account-no-auto-generated)).

**Notes:** IFSC → Bank Name resolution mechanism (external lookup vs. manual entry) is `TODO:` not specified — same open pattern as [savings BR-011](../savings/business-rules.md#br-011--ifsc-code-enables-bank-payout-auto-fill).

---

### BR-015 — Advanced Settings visibility role undefined

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | TODO |
| Source | [new-fd-account-screen.md](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md) — Tab 1 Section: प्रगत सेटिंग्ज |

**Rule:** `TODO:` The Advanced Settings section note states "Visible to users with accounting/admin role or when expanded manually" — the same phrase repeats on New Savings and New Daily accounts. No documented domain has resolved what "accounting/admin role" maps to against the platform's three-level permission model ([settings/master BR-017](../settings/master/business-rules.md#br-017--permission-levels-are-all-rights--view-only--no-rights)). Until resolved, treat "or when expanded manually" as the operative behaviour (collapsed-by-default panel, manually expandable by any actor with screen access) and do not gate visibility by an undefined role. Same as [savings BR-009](../savings/business-rules.md#br-009--advanced-settings-visibility-role-undefined).

---

### BR-016 — Receipt Prefix and Receipt Number required

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-fd-account-screen.md](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md) — Tab 1 Advanced, fields #26–#27 |

**Rule:** पावती प्रीफिक्स (Receipt Prefix, #26) and पावती क्रमांक (Receipt Number, #27) are required (spec `Required: Yes`), even though they live in the Advanced Settings section. They establish the physical FD receipt series and are surfaced as पावती क्रमांक on the Register grid (column #10).

**Notes:** Defaults for the series derive from FD scheme configuration ([settings/schemes BR-022](../settings/schemes/business-rules.md#br-022--fd-required-identity-fields) — Receipt No. Series Start / Number). `TODO:` Whether Receipt Number auto-increments from the scheme series or is manually keyed per account is not stated — confirm with the receipt-numbering mechanism alongside [BR-005](#br-005--account-no-auto-generated).

---

### BR-017 — Multiple FD workflow semantics undefined

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | TODO |
| Source | [new-fd-account-screen.md](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md) — Tab 1 Advanced, fields #28–#29 + `+ टाका` action |

**Rule:** `TODO:` The Advanced Settings "Multiple FD" block — वास्तविक एफडी रक्कम (Actual FD Amount, #28), गुणक (Multiplier, default `1`, #29), and the `+ टाका` (Add) action — supports opening more than one FD in a single flow, but the exact semantics are not confirmed. Candidate interpretations: (a) split one deposit into multiple equal-denomination receipts, (b) create N identical FD accounts where N = Multiplier, or (c) record a single FD with Multiplier/Actual Amount for reporting only. Behaviour, the number of persisted accounts, and how Account No./Receipt Number series are consumed must be confirmed before implementation.

**Notes:** Flagged as an explicit open decision (business answer deferred 2026-07-24). Interacts with [BR-005](#br-005--account-no-auto-generated), [BR-016](#br-016--receipt-prefix-and-receipt-number-required), and [BR-029](#br-029--new-fd-account-wizard-atomic-save-on-create) (atomic save scope).

---

### BR-018 — Nominee section conditional on Add Nominee checkbox

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [new-fd-account-screen.md](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md) — Tab 1, field #30 |

**Rule:** वारसदार जोडा (Add Nominee) is unchecked by default. When checked, Tab 2 (वारसदार) becomes visible in the tab bar; when unchecked, Tab 2 is hidden and skipped during Next/Back navigation, and no nominee data is persisted. Same conditional pattern as [savings BR-012](../savings/business-rules.md#br-012--nominee-section-conditional-on-add-nominee-checkbox).

---

### BR-019 — Joint Holder section conditional on Add Joint Holder checkbox

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [new-fd-account-screen.md](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md) — Tab 1, field #31 |

**Rule:** संयुक्त खातेदार जोडा (Add Joint Holder) is unchecked by default. When checked, Tab 3 (संयुक्त खाते धारक) becomes visible in the tab bar; when unchecked, Tab 3 is hidden and skipped during Next/Back navigation, and no joint holder data is persisted. Same conditional pattern as [savings BR-013](../savings/business-rules.md#br-013--joint-holder-section-conditional-on-add-joint-holder-checkbox).

---

### BR-020 — Nominee lookup resolves to existing or quick-added Customer

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [new-fd-account-screen.md](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md) — Tab 2, field #1 |

**Rule:** The Nominee Search field is a Customer Autocomplete (`entityType: customer`) with the **+ नवीन ग्राहक जोडा** companion action per [quick-add-customer-pattern.md](../../05-ui-ux/shared/quick-add-customer-pattern.md). A nominee is always a Customer record — resolved from existing master data or created via the minimal quick-add popup (Salutation, Name, Date of Birth, Mobile Number; Branch = session branch; Customer No. auto-generated per [customer BR-001](../customer/business-rules.md#br-001--customer-number-auto-generated)). Nominee Details ([BR-022](#br-022--nominee-percentage-optional-nomination-date-and-age-system-derived)) become visible only after a nominee customer is resolved.

**Notes:** Shares the `app-nominee-form` / `app-nominee-grid` component with Savings, Daily, and Recurring — not an FD-specific implementation. Same rule as [savings BR-014](../savings/business-rules.md#br-014--nominee-lookup-resolves-to-existing-or-quick-added-customer).

---

### BR-021 — Nominee Relation reuses canonical Membership list

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | Confirmed |
| Source | [new-fd-account-screen.md](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md) — Tab 2, field #2; [new-membership-screen.md](../../05-ui-ux/membership/new-membership-screen.md) — Tab 3 |

**Rule:** Nominee Relation (नाते) values must come from the single canonical Relation list finalized on New Membership Tab 3: `मुलगा`, `पुतण्या`, `मुली`, `मुलगा - पती`, `पति व मुलगा`, `वरील प्रमाणे`, `बायको`, `मैत्रीण`, `केअरटेकर`, `लहान भाऊ`, `स्वतः`, `पत्नी`, `पती`. Do not maintain an FD-specific Relation list.

**Notes:** Cross-domain dependency — Membership operational domain (`02-business-domains/membership/`) is not yet documented (Phase 3); the list currently exists only in the UI spec. Migrate the canonical definition to Membership's business-rules.md when authored and repoint referencing domains (Customer, Savings, FD, Daily, Recurring, Loan). Same rule as [savings BR-015](../savings/business-rules.md#br-015--nominee-relation-reuses-canonical-membership-list).

---

### BR-022 — Nominee Percentage optional; Nomination Date and Age system-derived

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-fd-account-screen.md](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md) — Tab 2, fields #3–#5 |

**Rule:** Nominee Percentage (टक्केवारी, #3) is optional. Nomination Date (नामांकन दिनांक, #4) is a read-only Label set to the system date. Age at Nomination (नामांकन करताना वय, #5) is a read-only Label auto-calculated from the resolved nominee's Date of Birth. None of these three are directly enterable.

**Notes:** The spec does not require multiple nominees' Percentage to total 100% — the running-total warning is a non-binding UX suggestion in [ux-optimization.md](../../05-ui-ux/fixed-deposit/ux-optimization.md) "Nominee Tab — UX Enhancement Suggestions" #2, not a confirmed rule. Same as [savings BR-016](../savings/business-rules.md#br-016--nominee-percentage-optional-nomination-date-and-age-system-derived).

---

### BR-023 — Joint Holder Guardian and Customer fields; Add validates selection

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-fd-account-screen.md](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md) — Tab 3, fields #1–#2 |

**Rule:** On Tab 3, Guardian (पालक, #1) is an optional checkbox and Select Customer (ग्राहक निवडा, #2) is an optional Autocomplete (`entityType: customer`). The `+ जोड` (Add) action validates that a customer has been resolved before appending a row to the Joint Holder grid (`app-joint-holder-grid`). The Introducer section from Membership is omitted for deposit products per bank review.

**Notes:** Same rule shape as [savings BR-017](../savings/business-rules.md#br-017--joint-holder-guardian-and-customer-fields-add-validates-selection).

---

### BR-024 — Account Operation Instructions required with defined values

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-fd-account-screen.md](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md) — Tab 3, field #3 |

**Rule:** खाते चालविण्याची सूचना (Account Operation Instructions) is required with default `स्वतः` (Self). Allowed values: `फक्त प्रमुख खातेदार` (Only Primary Holder), `फक्त संयुक्त खातेदार` (Only Joint Holder), `दोन्ही खातेदार आवश्यक` (Both Holders Required), `दोघांपैकी कोणीही` (Either Holder), `स्वतः` (Self).

**Notes:** This field lives on Tab 3, which is conditional on [BR-019](#br-019--joint-holder-section-conditional-on-add-joint-holder-checkbox). `TODO:` The persisted value when Tab 3 is skipped (single-holder account) is not stated — confirm whether `स्वतः` is persisted as the operative instruction or the field is not applicable. Same open item as [savings BR-018](../savings/business-rules.md#br-018--account-operation-instructions-required-with-defined-values).

---

### BR-025 — Interest Reinvestment enables S.I. reinvestment frequency

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [new-fd-account-screen.md](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md) — Tab 4, fields #2–#3 |

**Rule:** व्याज पुनर्निवेश (Interest Reinvestment, #2) is an optional checkbox. When checked, एस.आय. व्याज पुनर्गंतवणूक (S.I. Interest Reinvestment frequency, #3) becomes visible and selectable (e.g. `मासिक` / Monthly); when unchecked, field #3 is hidden and not persisted.

---

### BR-026 — Auto Renewal and Renewal mutually exclusive; renewal-type radios

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [new-fd-account-screen.md](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md) — Tab 4, fields #4–#8 |

**Rule:** ऑटो नूतनीकरण (Auto Renewal, #4) and नूतनीकरण (Renewal, #5) are mutually exclusive: when Auto Renewal is checked, Renewal is disabled, and vice versa. The renewal-type radio group — मुद्दल + व्याज (Principal + Interest, #6), फक्त मुद्दल (Only Principal, #7, default), केवळ व्याज (Only Interest, #8) — is enabled only when Renewal (#5) is checked, and exactly one radio applies.

**Notes:** Depends on scheme-level FD renewal configuration [settings/schemes BR-023](../settings/schemes/business-rules.md#br-023--fd-auto-renewal-dependent-fields) (waiting period, locking period, renewal period/rate after maturity). `TODO:` How renewal is actually executed at maturity (automatic batch vs. manual action) and how it produces the Renewal List events ([BR-036](#br-036--renewal-list-is-read-and-export-only)) is not captured in any current spec — resolve when the FD maturity/interest posting flow (Accounting domain) is authored.

---

### BR-027 — Interest Transfer enables GL, holder, and frequency routing

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [new-fd-account-screen.md](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md) — Tab 4, fields #9–#14 |

**Rule:** व्याज हस्तांतरण (Interest Transfer, #9) is an optional checkbox. When checked, it enables the routing fields: Select GL (#11), Select Account Holder (#12), Select Frequency (#13), and Select Day/Date (#14). इतर बँकेत निधी हस्तांतरण (Fund Transfer to Other Bank, #10) is an independent optional flag. Select GL and Select Account Holder are Autocomplete fields ([entity-autocomplete-pattern.md](../../05-ui-ux/shared/entity-autocomplete-pattern.md)).

**Notes:** When Interest Transfer is unchecked, fields #11–#14 are not required and not persisted as active routing.

---

### BR-028 — Account Closing GL routing enabled by checkbox

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [new-fd-account-screen.md](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md) — Tab 4, fields #15–#17 |

**Rule:** खाते बंद करतेवेळी (At Account Closing, #15) is an optional checkbox. When checked, it enables Select GL (#16) and Select Account Holder (#17) — both Autocomplete — to define where proceeds route at account closing. When unchecked, these fields are hidden and not persisted.

**Notes:** This configures closing routing at account-open time; the actual FD closure/maturity payout transaction belongs to the Accounting/transaction domain (Phase 3), not this screen.

---

### BR-029 — New FD Account wizard atomic save on create

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | Standing Decision (deposit wizards, 2026-07-24); [new-fd-account-screen.md](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md) — Tabs 1–4 footer actions |

**Rule:** On create, New FD Account persists the Account, Nominee(s) (if Tab 2 enabled), and Joint Holder(s) (if Tab 3 enabled) only when the actor clicks **पूर्ण** (Complete) on the final visible tab (Tab 4), after all visible tabs pass validation. **पुढे** (Next) and **मागे** (Back) must not write partial records. **पूर्ववत** (Reset) clears wizard state without persisting.

**Notes:** Matches the atomic-save pattern confirmed for [savings BR-019](../savings/business-rules.md#br-019--new-savings-account-wizard-atomic-save-on-create), [customer BR-021](../customer/business-rules.md#br-021--new-customer-wizard-atomic-save-on-create), [settings/schemes BR-013](../settings/schemes/business-rules.md#br-013--scheme-wizard-atomic-save-on-create), and [settings/master BR-019](../settings/master/business-rules.md#br-019--staff-access-wizard-atomic-save-on-create). Interaction with Multiple FD ([BR-017](#br-017--multiple-fd-workflow-semantics-undefined)) — i.e. whether one Complete persists one or many accounts — is `TODO:` pending that decision.

---

### BR-030 — FD screens use Master permission levels

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | Confirmed |
| Source | [settings/master business-rules.md](../settings/master/business-rules.md#br-017--permission-levels-are-all-rights--view-only--no-rights) BR-017 |

**Rule:** Access to New FD Account, FD Account Management, Deposit Loan Installment Payment, and FD Interest Multiplier follows Master permission levels: **All Rights** (full edit/save), **View Only** (read-only; Save/Add/Remove/Set/Calculate-that-persist actions hidden), **No Rights** (navigation blocked). Do not redefine permission semantics in this domain.

**Notes:** The Interest Multiplier and Deposit-Loan Interest calculation actions are read-only computations; View Only actors may run them but cannot persist any resulting installment/setting. Same model as [savings BR-020](../savings/business-rules.md#br-020--savings-screens-use-master-permission-levels).

---

### BR-031 — Account Management search fields all optional; Organization auto-filled

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [fd-account-management-screen.md](../../05-ui-ux/fixed-deposit/fd-account-management-screen.md) — Tab 1 fields #1–#8, Tab 2 fields #1–#10 |

**Rule:** All Primary Search filters on Tab 1 — Account Register (Branch, Scheme, Status default `चालू`, Account No. From/To, Account Holder, Customer No. From/To) — and all Filter fields on Tab 2 — Renewal List (adds Renewal Date From/To and Receipt Number) — are optional. Clicking **दाखवा** (Show) with no filters returns results per the actor's entitled scope. `संस्था` (Organization) is a read-only header Label auto-filled from the tenant session and is not repeated in the filter bar.

**Notes:** The legacy `अतिरिक्त शोध पर्याय` (Advanced Search) link is out of scope (no stub, no TODO), same as [Savings Account Register](../../05-ui-ux/savings/account-register-screen.md) and [savings BR-021](../savings/business-rules.md#br-021--account-register-primary-search-fields-all-optional). Branch-scoping of results for actors with limited branch rights is `TODO:` unresolved — same open pattern as [customer BR-024](../customer/business-rules.md#br-024--customer-list-branch-scoped-results-eligibility).

---

### BR-032 — Register grid legend: loan-linked and matured accounts

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | TODO |
| Source | [fd-account-management-screen.md](../../05-ui-ux/fixed-deposit/fd-account-management-screen.md) — Tab 1 Results Grid legend |

**Rule:** `TODO:` The Account Register grid renders row highlighting per its legend — **Pink** = कर्ज असलेली खाती (accounts with a loan against the FD), **Blue** = मुदत संपलेली खाती (matured accounts). The matured highlight is derivable from Maturity Date vs. current date. The loan-linked (pink) highlight depends on the Loan / Deposit Loan domain (`02-business-domains/loan/`), which is not yet documented (Phase 3), so the precise linkage (a Deposit Loan lien against this FD vs. any loan held by the same customer) cannot be confirmed. Resolve when the Loan domain is authored.

**Notes:** The same pink loan-linked legend appears on the Savings, Daily, and Recurring registers ([savings BR-022](../savings/business-rules.md#br-022--loan-linked-accounts-filter-depends-on-undocumented-loan-domain)). FD uses legend-only styling (no explicit filter checkbox). Directly relevant to Deposit Loan Installment ([BR-037](#br-037--deposit-loan-must-exist-before-installment-payment)).

---

### BR-033 — Account Management follows interactive reporting standard

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | Confirmed |
| Source | [fd-account-management-screen.md](../../05-ui-ux/fixed-deposit/fd-account-management-screen.md); [business-goals.md](../../00-project-overview/business-goals.md) BG-005 |

**Rule:** Both tabs implement the platform-wide interactive reporting standard (BG-005): Primary Search/Filter, a results grid with pagination, and Export. Tab 1 shows totals (एकूण एफडी शिल्लक, एकूण व्याज दिले, एकूण तरतूद व्याज) and an एकूण नोंदी record count. Additional detail beyond the base grid columns is reached via the तपशील (Details) sidebar action ([BR-035](#br-035--account-statement-and-details-lack-dedicated-specs)) rather than shown by default.

---

### BR-034 — काढा (Remove) deletes the account registration row

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [fd-account-management-screen.md](../../05-ui-ux/fixed-deposit/fd-account-management-screen.md) — Tab 1 sidebar actions |

**Rule:** The Account Register sidebar action काढा (Remove) deletes the selected account registration row — it does not merely hide the row from the current view. This is the same semantics that the Savings register's वगळा (Exclude) action was aligned to ([savings BR-024](../savings/business-rules.md#br-024--वगळा-exclude-is-equivalent-to-काढा-remove)).

**Notes:** `TODO:` Whether Remove requires a confirmation dialog, and whether it is blocked for accounts that already have posted ledger transactions (vs. only accounts created in error with zero transaction history), is not stated — confirm before implementation, since removing a financial account differs materially from removing a non-financial registration row.

---

### BR-035 — Account Statement and Details lack dedicated specs

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | TODO |
| Source | [fd-account-management-screen.md](../../05-ui-ux/fixed-deposit/fd-account-management-screen.md) — Tab 1 sidebar actions तपशील, खाते उतारा |

**Rule:** `TODO:` तपशील (Details) opens account detail in context with no separate FD Account Information screen spec. खाते उतारा (Account Statement) has no dedicated report spec — [reports/overview.md](../../05-ui-ux/reports/overview.md) documents a **Loan** Account Statement report only, with no equivalent for FD/Savings/Daily/Recurring deposit accounts. Both gaps should be resolved by authoring the missing specs or confirming reuse of an existing pattern. Same gap as [savings BR-026](../savings/business-rules.md#br-026--account-details-and-account-statement-lack-dedicated-specs).

---

### BR-036 — Renewal List is read/export only

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [fd-account-management-screen.md](../../05-ui-ux/fixed-deposit/fd-account-management-screen.md) — Tab 2 |

**Rule:** Tab 2 (नूतनीकरण यादी / Renewal List) is a read-only report of renewal events for filtered FD accounts, with a single निर्यात करा (Export) action. It does not create, edit, or reverse renewals — it lists renewal events (Renewal Date, Current Date, Amount, Maturity Amount, Duration, Interest Rate, Maturity Date) produced elsewhere.

**Notes:** `TODO:` The source that generates renewal events (Auto Renewal batch at maturity vs. a manual renewal action) is not defined in any current spec — see [BR-026](#br-026--auto-renewal-and-renewal-mutually-exclusive-renewal-type-radios). Resolve when the FD maturity/renewal processing flow is authored (Accounting/transaction domain, Phase 3).

---

### BR-037 — Deposit Loan must exist before installment payment

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [deposit-loan-installment-payment-screen.md](../../05-ui-ux/fixed-deposit/deposit-loan-installment-payment-screen.md) — Purpose; Tab 1 |

**Rule:** Deposit Loan Installment Payment processes installments on an **existing** loan-against-deposit. The loan itself is opened on [New Deposit Loan](../../05-ui-ux/loan/new-deposit-loan-screen.md) (Loan module); this FD-menu screen only records installment payments against a loan that already exists. The actor identifies the loan by resolving its Customer ([BR-038](#br-038--installment-interest-tab-requires-mode-gl-and-a-customer-or-account-holder-lookup)) and calculating due interest ([BR-039](#br-039--calculate-interest-populates-installment-grid-set-applies)).

**Notes:** Cross-domain dependency on the Loan domain (`02-business-domains/loan/`), not yet documented (Phase 3). Deposit Loan concept per [glossary.md](../../00-project-overview/glossary.md#deposit-loan-ठेव-कर्ज). The FD accounts pledged as collateral are those opened via [BR-029](#br-029--new-fd-account-wizard-atomic-save-on-create) and flagged loan-linked (pink) on the Register ([BR-032](#br-032--register-grid-legend-loan-linked-and-matured-accounts)).

---

### BR-038 — Installment Interest tab requires mode, GL, and a Customer or Account Holder lookup

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [deposit-loan-installment-payment-screen.md](../../05-ui-ux/fixed-deposit/deposit-loan-installment-payment-screen.md) — Tab 1, fields #1–#5 |

**Rule:** On the Interest tab, रोख / ट्रान्सफर (Cash / Transfer, #1) is a required radio and Select GL (#2) is a required Autocomplete. The actor must resolve **either** Select Customer (#3) **or** Select Account Holder (#4) — not both required — per the on-screen note "कृपया खाते क्रमांक किंवा ग्राहक क्रमांक प्रविष्ट करा". दिनांक (Date, #5) is a read-only Label set to the system date.

**Notes:** Select Customer, Select Account Holder, and Select GL follow [entity-autocomplete-pattern.md](../../05-ui-ux/shared/entity-autocomplete-pattern.md). Cash/Transfer mode aligns with the platform v1 transaction modes ([system-boundaries.md](../../00-project-overview/system-boundaries.md) — Cash + Cheque; no live clearing).

---

### BR-039 — Calculate Interest populates installment grid; Set applies

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | TODO |
| Source | [deposit-loan-installment-payment-screen.md](../../05-ui-ux/fixed-deposit/deposit-loan-installment-payment-screen.md) — Tab 1 actions व्याज गणना करा, निर्धारित करा |

**Rule:** व्याज गणना करा (Calculate Interest) populates the results grid with per-account installment lines (Balance, Principal Installment, Current Interest, Total Installment, etc.), `सर्व निवडा` selects all rows, and निर्धारित करा (Set/Determine) applies the selected installments, updating the summary (एकूण तरतूद, एकूण व्याज, एकूण रक्कम). `TODO:` The interest calculation basis (rate source, day-count, principal-vs-interest split) and what "Set" persists (a posted transaction vs. a staged installment) are not fully captured in the source video/frames and depend on the Loan domain — confirm when the Loan domain is authored.

**Notes:** Cross-dependency on Loan domain ([BR-037](#br-037--deposit-loan-must-exist-before-installment-payment)). The FD interest formula referenced in [BR-012](#br-012--maturity-amount-return-date-and-receipt-date-system-computed) governs deposit interest, not the loan installment interest here.

---

### BR-040 — Deposit Loan Installment Tabs 2–6 not captured

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | TODO |
| Source | [deposit-loan-installment-payment-screen.md](../../05-ui-ux/fixed-deposit/deposit-loan-installment-payment-screen.md) — Tabs 2–6 |

**Rule:** `TODO:` Tabs 2–6 — इतर कपात (Other Deductions), कर्ज माहिती (Loan Information), साहित्य/तारण तपशील (Collateral Details), ट्रान्सफर (Transfer), केवायसी माहिती (KYC Information) — are marked `TODO` in the source spec (not captured in the reference video). No business rules are derived for these tabs. Per [ux-optimization.md](../../05-ui-ux/fixed-deposit/ux-optimization.md) Open Gaps (2026-07-21), these tabs are candidates for removal pending bank review. Loan Information defers to [New Deposit Loan Tab 2](../../05-ui-ux/loan/new-deposit-loan-screen.md); Transfer follows the deposit transaction pattern; KYC uses the shared `app-kyc-info-tab`.

**Notes:** Do not scaffold rules for uncaptured tabs. Revisit when either the bank confirms removal or the tabs are captured.

---

### BR-041 — Interest Multiplier is a scheme-based calculator with no persistence

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [fd-interest-multiplier-screen.md](../../05-ui-ux/fixed-deposit/fd-interest-multiplier-screen.md) — Purpose; Calculator Section |

**Rule:** FD Interest Multiplier (व्याज गुणक) is a stateless calculator. Select Scheme (योजना निवडा, #1) is required and loads from FD schemes (Settings → नवीन योजना, Scheme Type = मुदत ठेव). गणना करा (Calculate) produces read-only outputs — व्याज दर (Interest Rate, #9) and दिनांक फरक (Date Difference, #10); पूर्वत (Reset) clears the form. The screen creates no account and persists nothing.

**Notes:** Same calculator pattern (no persistence) as the Daily and Recurring Interest Multiplier screens; the calculation service is shared where formulas match ([generate-ui-screen.mdc](../../../.cursor/rules/generate-ui-screen.mdc) Reusable Component Catalog).

---

### BR-042 — Interest Multiplier conditional field visibility

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [fd-interest-multiplier-screen.md](../../05-ui-ux/fixed-deposit/fd-interest-multiplier-screen.md) — Calculator Section, fields #2–#8 |

**Rule:** Calculator option controls are hidden until a Scheme is selected (#1). Once selected, the product-type radio (#2), Simple/Compounding radio (#3), Duration in Days/Months radio (#5), and Calculate Interest Rate/Duration radio (#6) become visible. The Compounding Frequency radio (#4, मासिक/तिमाही/सहामाही/वार्षिक) is visible **only** when field #3 = Compounding. Duration (Months) (#7) shows only when #5 = Months; Duration (Days) (#8) shows only when #5 = Days.

---

### BR-043 — Interest Multiplier computes Interest Rate or Duration

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [fd-interest-multiplier-screen.md](../../05-ui-ux/fixed-deposit/fd-interest-multiplier-screen.md) — Calculator Section, field #6; Output Sections |

**Rule:** The Calculate Interest Rate / Duration radio (#6) selects the calculation target: when set to व्याज दर (Interest Rate), the calculator solves for the rate; when set to कालावधी (Duration), it solves for duration. गणना करा outputs the computed व्याज दर (#9) and दिनांक फरक (Date Difference, #10) as read-only Labels using the selected scheme's Simple/Compounding basis and frequency ([BR-042](#br-042--interest-multiplier-conditional-field-visibility)).

**Notes:** Uses the same FD interest formula as [BR-012](#br-012--maturity-amount-return-date-and-receipt-date-system-computed). `TODO:` The precise day-count/compounding formula is not documented (shared open item with BR-012) — resolve at DB/API phase.

---

## Related Documents

- [overview.md](overview.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [changelog.md](changelog.md)
- [../../05-ui-ux/fixed-deposit/new-fd-account-screen.md](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md)
- [../../05-ui-ux/fixed-deposit/fd-account-management-screen.md](../../05-ui-ux/fixed-deposit/fd-account-management-screen.md)
- [../../05-ui-ux/fixed-deposit/deposit-loan-installment-payment-screen.md](../../05-ui-ux/fixed-deposit/deposit-loan-installment-payment-screen.md)
- [../../05-ui-ux/fixed-deposit/fd-interest-multiplier-screen.md](../../05-ui-ux/fixed-deposit/fd-interest-multiplier-screen.md)
- [../savings/business-rules.md](../savings/business-rules.md)
- [../customer/business-rules.md](../customer/business-rules.md)
- [../settings/schemes/business-rules.md](../settings/schemes/business-rules.md)
- [../settings/master/business-rules.md](../settings/master/business-rules.md)
- [../../00-project-overview/glossary.md](../../00-project-overview/glossary.md)
