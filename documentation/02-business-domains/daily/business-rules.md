# Business Rules — Daily (Pigmy)

## Purpose

Numbered business rules for the **डेली (Daily / Pigmy)** module. Every rule cites its UI spec source. Rules marked **TODO** require business confirmation before implementation.

This file covers the two account/agent **creation wizards** (BR-001…BR-027). Rules for Account Register, Agent Collection Management, Agent-to-Agent Transfer, and Interest Multiplier continue in [business-rules-part2.md](business-rules-part2.md) (BR-028…BR-045).

**Sources (current specs only):** [new-daily-account-screen.md](../../05-ui-ux/daily/new-daily-account-screen.md), [new-agent-screen.md](../../05-ui-ux/daily/new-agent-screen.md), [account-register-screen.md](../../05-ui-ux/daily/account-register-screen.md), [agent-collection-management-screen.md](../../05-ui-ux/daily/agent-collection-management-screen.md), [agent-to-agent-transfer-screen.md](../../05-ui-ux/daily/agent-to-agent-transfer-screen.md), [interest-multiplier-screen.md](../../05-ui-ux/daily/interest-multiplier-screen.md).

**Superseded specs excluded per this request** (see [ux-optimization.md](../../05-ui-ux/daily/ux-optimization.md)): `daily-transaction-screen.md` → [deposit-account-transaction-screen.md](../../05-ui-ux/accounting/deposit-account-transaction-screen.md) (Accounting), Manual Interest Assessment/Provision → [manual-interest-management-screen.md](../../05-ui-ux/accounting/manual-interest-management-screen.md) (Accounting), `agent-collection-screen.md` / `agent-collection-list-screen.md` → consolidated into [agent-collection-management-screen.md](../../05-ui-ux/daily/agent-collection-management-screen.md).

## Rule Index

| ID | Title | Type | Status |
| :--- | :--- | :--- | :---: |
| [BR-001](#br-001--customer-must-exist-before-a-daily-account-can-be-opened) | Customer must exist before a Daily account can be opened | Eligibility | Confirmed |
| [BR-002](#br-002--scheme-required-and-loaded-from-daily-scheme-master) | Scheme required and loaded from Daily scheme master | Validation | Confirmed |
| [BR-003](#br-003--agent-branch-and-agent-required-agent-must-be-registered-first) | Agent Branch and Agent required; Agent must be registered first | Eligibility | Confirmed |
| [BR-004](#br-004--account-no-auto-generated) | Account No. auto-generated | Workflow | Confirmed |
| [BR-005](#br-005--duration-selected-from-scheme-grid-duration-and-rate-auto-filled) | Duration selected from scheme grid; duration and rate auto-filled | Validation | Confirmed |
| [BR-006](#br-006--commission-rate-required-at-account-opening) | Commission Rate required at account opening | Validation | Confirmed |
| [BR-007](#br-007--current-date-defaults-to-system-date) | Current Date defaults to system date | Workflow | Confirmed |
| [BR-008](#br-008--daily-deposit-amount-required-maturity-fields-optional) | Daily Deposit Amount required; maturity fields optional | Validation | Confirmed |
| [BR-009](#br-009--account-status-default-and-shared-values-across-deposit-products) | Account Status default and shared values across deposit products | Validation | Confirmed |
| [BR-010](#br-010--pigmy-account-for-loan-flag-depends-on-undocumented-loan-domain) | Pigmy Account for Loan flag depends on undocumented Loan domain | Eligibility | TODO |
| [BR-011](#br-011--advanced-settings-visibility-role-undefined) | Advanced Settings visibility role undefined | Cross-cutting | TODO |
| [BR-012](#br-012--advanced-overrides-optional-with-scheme-defaults) | Advanced overrides optional with scheme defaults | Validation | Confirmed |
| [BR-013](#br-013--nominee-section-conditional-on-add-nominee-checkbox) | Nominee section conditional on Add Nominee checkbox | Eligibility | Confirmed |
| [BR-014](#br-014--joint-holder-section-conditional-on-add-joint-holder-checkbox) | Joint Holder section conditional on Add Joint Holder checkbox | Eligibility | Confirmed |
| [BR-015](#br-015--nominee-lookup-resolves-to-existing-or-quick-added-customer) | Nominee lookup resolves to existing or quick-added Customer | Eligibility | Confirmed |
| [BR-016](#br-016--nominee-relation-reuses-canonical-membership-list) | Nominee Relation reuses canonical Membership list | Cross-cutting | Confirmed |
| [BR-017](#br-017--nominee-percentage-optional-nomination-date-and-age-system-derived) | Nominee Percentage optional; Nomination Date and Age system-derived | Validation | Confirmed |
| [BR-018](#br-018--joint-holder-guardian-and-customer-add-validates-selection) | Joint Holder Guardian and Customer; Add validates selection | Validation | Confirmed |
| [BR-019](#br-019--account-operation-instructions-required-with-defined-values) | Account Operation Instructions required with defined values | Validation | Confirmed |
| [BR-020](#br-020--new-daily-account-wizard-atomic-save-on-create) | New Daily Account wizard atomic save on create | Workflow | Confirmed |
| [BR-021](#br-021--agent-identity-requires-an-existing-customer) | Agent identity requires an existing Customer | Eligibility | Confirmed |
| [BR-022](#br-022--agent-status-and-joining-date-required) | Agent Status and Joining Date required | Validation | Confirmed |
| [BR-023](#br-023--agent-linked-savings-account-branch-and-account-holder-required) | Agent linked savings account: Branch and Account Holder required | Validation | Confirmed |
| [BR-024](#br-024--tds-reason-conditional-on-tds--no) | TDS Reason conditional on TDS = No | Eligibility | Confirmed |
| [BR-025](#br-025--agent-deduction-blocks-conditional-on-their-checkboxes) | Agent deduction blocks conditional on their checkboxes | Eligibility | Confirmed |
| [BR-026](#br-026--agent-commission-config-per-scheme-and-amount-slab) | Agent commission config per scheme and amount slab | Validation | Confirmed |
| [BR-027](#br-027--new-agent-wizard-atomic-save-on-create) | New Agent wizard atomic save on create | Workflow | Confirmed |

> BR-028…BR-045 (Account Register, Agent Collection Management, Agent-to-Agent Transfer, Interest Multiplier, cross-cutting permissions) are in [business-rules-part2.md](business-rules-part2.md).

---

## Rules — New Daily Account

### BR-001 — Customer must exist before a Daily account can be opened

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [new-daily-account-screen.md](../../05-ui-ux/daily/new-daily-account-screen.md) — Tab 1, field #1 |

**Rule:** New Daily Account Tab 1 requires selecting an **existing** Customer via Autocomplete (`entityType: customer`). The screen must not create a new Customer identity — a person must first be registered via [New Customer](../../05-ui-ux/customer/new-customer-screen.md) before a Daily account can be opened for them. The Customer summary (सभासद क्रमांक, वय, सभासद शाखा नाव, सभासद प्रकार, विशेष सूचना) is displayed read-only after resolve.

**Notes:** Same cross-screen dependency shape as [savings BR-001](../savings/business-rules.md#br-001--customer-must-exist-before-savings-account-can-be-opened) and [customer BR-026](../customer/business-rules.md#br-026--customer-must-exist-before-other-account-can-be-opened).

---

### BR-002 — Scheme required and loaded from Daily scheme master

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-daily-account-screen.md](../../05-ui-ux/daily/new-daily-account-screen.md) — Tab 1, field #2 |

**Rule:** Select Scheme (योजना निवडा) is required and loads dynamically from Settings → नवीन योजना where Scheme Type = `डेली` (Daily). Placeholder/no selection is not a valid saved value. The full list is scheme master data — not a fixed enum.

**Notes:** Dependency on [settings/schemes business-rules.md](../settings/schemes/business-rules.md) — a Daily scheme must exist before an account can be opened under it. Per [glossary.md](../../00-project-overview/glossary.md) (Scheme), Daily schemes require GL Head No. ≤ 99 per the scheme screen's validation message; that validation is owned by Settings/Schemes, not re-litigated here. Whether a scheme's Status ([settings/schemes BR-033](../settings/schemes/business-rules.md), TODO) blocks new account opening is inherited from that unresolved rule.

---

### BR-003 — Agent Branch and Agent required; Agent must be registered first

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [new-daily-account-screen.md](../../05-ui-ux/daily/new-daily-account-screen.md) — Tab 1, fields #3–#4 |

**Rule:** Select Agent Branch (एजंट शाखा निवडा) and Select Agent (एजंट निवडा) are both required Autocomplete fields. The Agent must be an **existing** agent registered via [New Agent](../../05-ui-ux/daily/new-agent-screen.md) ([BR-021](#br-021--agent-identity-requires-an-existing-customer)) — the account screen must not create an agent inline. Each Daily account is bound to exactly one collecting agent at opening; the binding is what the Agent-to-Agent Transfer screen later reassigns ([BR-041](business-rules-part2.md#br-041--from-and-to-agent-required-selection-reassigns-accounts)).

**Notes:** Internal cross-screen dependency: New Agent → New Daily Account. The same Agent Autocomplete is reused on Account Register, Agent Collection Management, and Agent-to-Agent Transfer.

---

### BR-004 — Account No. auto-generated

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [new-daily-account-screen.md](../../05-ui-ux/daily/new-daily-account-screen.md) — Tab 1, field #5 |

**Rule:** Account No. (खाते क्र.) is system-generated and displayed as a read-only Label after Save. It is not a lookup field — excluded from entity-autocomplete consolidation ([entity-autocomplete-pattern.md](../../05-ui-ux/shared/entity-autocomplete-pattern.md) Exclusions).

**Notes:** Generation algorithm (global vs. per-branch vs. per-scheme sequence) is `TODO:` not yet documented — same open pattern as [savings BR-004](../savings/business-rules.md#br-004--account-no-auto-generated) and [customer BR-001](../customer/business-rules.md#br-001--customer-number-auto-generated).

---

### BR-005 — Duration selected from scheme grid; duration and rate auto-filled

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-daily-account-screen.md](../../05-ui-ux/daily/new-daily-account-screen.md) — Tab 1, fields #6–#9 |

**Rule:** Select Duration (कालावधी निवडा) is required and its options load from the selected scheme's duration grid (Settings → नवीन योजना → कालावधी tab). Once a duration is selected, Duration (Months), Duration (Days), and Interest Rate (% p.a.) are read-only Labels auto-filled from that duration row. The actor cannot type these three values directly.

**Notes:** Dependency on the selected scheme's configured duration/rate rows in [settings/schemes business-rules.md](../settings/schemes/business-rules.md). Interest Rate here is scheme-derived, not enterable — Daily has no per-account rate override field on this screen (unlike the "admin override" phrase on [savings BR-005](../savings/business-rules.md#br-005--interest-rate-auto-filled-from-scheme-admin-override-role-undefined)).

---

### BR-006 — Commission Rate required at account opening

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-daily-account-screen.md](../../05-ui-ux/daily/new-daily-account-screen.md) — Tab 1, field #10 |

**Rule:** Commission Rate (कमिशन दर) is a required numeric field entered per account. It represents the agent collection commission rate applied to this account's collections.

**Notes:** `TODO:` The spec does not state whether Commission Rate defaults from the selected Agent's commission configuration for the chosen scheme/amount slab ([BR-026](#br-026--agent-commission-config-per-scheme-and-amount-slab), New Agent Tab 2), or is always entered manually per account. Confirm the default source and whether the per-account value may override the agent-level configuration. The Collection grid's एजंट कमिशन रेट column ([BR-036](business-rules-part2.md#br-036--collection-grid-computes-totals-penalty-discount-and-commission)) consumes whichever value is authoritative.

---

### BR-007 — Current Date defaults to system date

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [new-daily-account-screen.md](../../05-ui-ux/daily/new-daily-account-screen.md) — Tab 1, field #11 |

**Rule:** Current Date (चालू दिनांक) is a read-only Label defaulting to the system date at account opening. It is persisted and surfaced as चालू दिनांक (Opening Date) on the [Account Register](../../05-ui-ux/daily/account-register-screen.md) results grid (column #8).

---

### BR-008 — Daily Deposit Amount required; maturity fields optional

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-daily-account-screen.md](../../05-ui-ux/daily/new-daily-account-screen.md) — Tab 1, fields #12–#14 |

**Rule:** Daily Deposit Amount (दैनिक ठेव रक्कम) is required — it is the agreed daily collection installment. Maturity Date (मुदतपूर्ती दिनांक) and Maturity Amount (मुदतपूर्ती रक्कम) are optional at opening.

**Notes:** Maturity Amount here is a stored optional value, distinct from the computed मुदतपूर्ती रक्कम produced by the [Interest Multiplier](../../05-ui-ux/daily/interest-multiplier-screen.md) calculator ([BR-044](business-rules-part2.md#br-044--deposit-amount-required-calculation-is-preview-only)), which is a preview tool and does not post to the account. `TODO:` Whether the account screen auto-populates Maturity Amount from the scheme/Interest Multiplier formula, or requires manual entry, is not stated — contrast the confirmed [FD Maturity Amount derivation](../fixed-deposit/business-rules.md) standing decision.

---

### BR-009 — Account Status default and shared values across deposit products

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-daily-account-screen.md](../../05-ui-ux/daily/new-daily-account-screen.md) — Tab 1, field #16; [account-register-screen.md](../../05-ui-ux/daily/account-register-screen.md) — field #9 |

**Rule:** Select Status (स्थिती निवडा) is optional at account creation, defaulting to `चालू` (Active). Allowed values: `चालू`, `बंद` (Closed), `स्थगित` (Suspended). This is the same three-value enum used on New Savings Account, New FD Account, and New Recurring Account — implementations share one status domain across deposit product accounts.

**Notes:** Identical enum to [savings BR-008](../savings/business-rules.md#br-008--account-status-default-and-shared-values-across-deposit-products). Distinct from Customer Status, Scheme Status, and **Agent** Status ([BR-022](#br-022--agent-status-and-joining-date-required)) — do not merge these status domains.

---

### BR-010 — Pigmy Account for Loan flag depends on undocumented Loan domain

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | TODO |
| Source | [new-daily-account-screen.md](../../05-ui-ux/daily/new-daily-account-screen.md) — Tab 1, field #17 |

**Rule:** `TODO:` Pigmy Account for Loan (कर्जासाठी पिग्मी खाते) is an optional checkbox flagging that this Daily account is linked to a loan (recovery/collateral). The Loan domain (`02-business-domains/loan/`) is not yet documented (Phase 3), so the precise linkage semantics — whether the account funds loan-installment recovery, is pledged as collateral, or drives the Account Register कर्ज असलेली खाती (pink) legend ([BR-031](business-rules-part2.md#br-031--results-grid-legend-loan-linked-and-matured-highlighting)) — cannot be confirmed. Resolve when the Loan domain is authored.

---

### BR-011 — Advanced Settings visibility role undefined

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | TODO |
| Source | [new-daily-account-screen.md](../../05-ui-ux/daily/new-daily-account-screen.md) — Section: प्रगत सेटिंग्ज (Advanced Settings) |

**Rule:** `TODO:` The Advanced Settings note states "Visible to users with accounting/admin role or when expanded manually" — the same phrase repeats on New Savings and New FD accounts. No domain has resolved what "accounting/admin role" maps to against the platform's three-level permission model ([settings/master BR-017](../settings/master/business-rules.md#br-017--permission-levels-are-all-rights--view-only--no-rights)). Until resolved, treat "or when expanded manually" as operative (collapsed-by-default panel, manually expandable by any actor with screen access), not gated by an undefined role.

**Notes:** Shared open item with [savings BR-009](../savings/business-rules.md#br-009--advanced-settings-visibility-role-undefined).

---

### BR-012 — Advanced overrides optional with scheme defaults

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-daily-account-screen.md](../../05-ui-ux/daily/new-daily-account-screen.md) — Tab 1 Advanced, fields #18–#27 |

**Rule:** All Advanced Settings fields are optional overrides: Sales Agent Branch / Sales Agent (Autocomplete), Interest Type (सरळ / चक्रवाढ) and Compounding (परिणामगणन) — both defaulting from the scheme, Collection Amount Limit, Debit Limit, Minimum Balance, and the bank-payout block (IFSC Code → Bank Name, Bank Savings Account No.). None block Save when left blank.

**Notes:** Sales Agent is a separate optional reference from the required collecting Agent ([BR-003](#br-003--agent-branch-and-agent-required-agent-must-be-registered-first)); both resolve against registered agents. Interest Type / Compounding default from the scheme's interest configuration ([settings/schemes business-rules.md](../settings/schemes/business-rules.md)).

---

### BR-013 — Nominee section conditional on Add Nominee checkbox

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [new-daily-account-screen.md](../../05-ui-ux/daily/new-daily-account-screen.md) — Tab 1, field #28 |

**Rule:** Add Nominee (वारसदार जोडा) is unchecked by default. When checked, Tab 2 (वारसदार) becomes visible in the tab bar; when unchecked, Tab 2 is hidden and skipped during Next/Back navigation, and no nominee data is persisted.

**Notes:** Same conditional pattern as [savings BR-012](../savings/business-rules.md#br-012--nominee-section-conditional-on-add-nominee-checkbox).

---

### BR-014 — Joint Holder section conditional on Add Joint Holder checkbox

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [new-daily-account-screen.md](../../05-ui-ux/daily/new-daily-account-screen.md) — Tab 1, field #29 |

**Rule:** Add Joint Holder (संयुक्त खातेदार जोडा) is unchecked by default. When checked, Tab 3 (परिपक्वता / संयुक्त एसी धारक) becomes visible and skipped when unchecked. Duration/maturity fields live on Tab 1 — Tab 3 captures joint holder(s) and account operation instructions only (legacy tab title retained).

**Notes:** Same conditional pattern as [savings BR-013](../savings/business-rules.md#br-013--joint-holder-section-conditional-on-add-joint-holder-checkbox).

---

### BR-015 — Nominee lookup resolves to existing or quick-added Customer

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [new-daily-account-screen.md](../../05-ui-ux/daily/new-daily-account-screen.md) — Tab 2, field #1 |

**Rule:** The Nominee Search field is a Customer Autocomplete (`entityType: customer`) with the **+ नवीन ग्राहक जोडा** companion action per [quick-add-customer-pattern.md](../../05-ui-ux/shared/quick-add-customer-pattern.md). A nominee is always a Customer record — resolved from existing master data or created via the minimal quick-add popup. Nominee Details (fields #2–#5) become visible only after a nominee customer is resolved.

**Notes:** Shares the `app-nominee-form` / `app-nominee-grid` components with Savings/FD/Recurring — not a Daily-specific implementation ([savings BR-014](../savings/business-rules.md#br-014--nominee-lookup-resolves-to-existing-or-quick-added-customer)).

---

### BR-016 — Nominee Relation reuses canonical Membership list

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | Confirmed |
| Source | [new-daily-account-screen.md](../../05-ui-ux/daily/new-daily-account-screen.md) — Tab 2, field #2 |

**Rule:** Nominee Relation (नाते) values must come from the single canonical Relation list finalized on New Membership Tab 3: `मुलगा`, `पुतण्या`, `मुली`, `मुलगा - पती`, `पति व मुलगा`, `वरील प्रमाणे`, `बायको`, `मैत्रीण`, `केअरटेकर`, `लहान भाऊ`, `स्वतः`, `पत्नी`, `पती`. Do not maintain a Daily-specific Relation list.

**Notes:** Cross-domain dependency — the Membership operational domain (`02-business-domains/membership/`) is not yet documented (Phase 3); this list currently exists only in the UI spec, reused by Customer, Savings, and FD. Migrate the canonical definition to Membership's business-rules.md when authored and update referencing domains ([savings BR-015](../savings/business-rules.md#br-015--nominee-relation-reuses-canonical-membership-list)).

---

### BR-017 — Nominee Percentage optional; Nomination Date and Age system-derived

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-daily-account-screen.md](../../05-ui-ux/daily/new-daily-account-screen.md) — Tab 2, fields #3–#5 |

**Rule:** Nominee Percentage (टक्केवारी) is optional. Nomination Date (नामांकन दिनांक) is a read-only Label set to the system date. Age at Nomination (नामांकन करताना वय) is a read-only Label auto-calculated from the resolved nominee's Date of Birth. None of these three are directly enterable.

**Notes:** Whether multiple nominees' Percentage must total 100% is a non-binding UX suggestion, not a confirmed rule ([ux-optimization.md](../../05-ui-ux/daily/ux-optimization.md) Nominee Tab suggestion #2).

---

### BR-018 — Joint Holder Guardian and Customer; Add validates selection

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-daily-account-screen.md](../../05-ui-ux/daily/new-daily-account-screen.md) — Tab 3, fields #1–#2 |

**Rule:** On Tab 3, Guardian (पालक) is an optional checkbox and Select Customer (ग्राहक निवडा) is an optional Customer Autocomplete. The **+ जोड** (Add) action validates that a customer has been resolved before appending a row to the Joint Holder grid (`app-joint-holder-grid`). काढा (Remove) removes the selected grid row.

**Notes:** Same as [savings BR-017](../savings/business-rules.md#br-017--joint-holder-guardian-and-customer-fields-add-validates-selection).

---

### BR-019 — Account Operation Instructions required with defined values

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-daily-account-screen.md](../../05-ui-ux/daily/new-daily-account-screen.md) — Tab 3, field #3 |

**Rule:** Account Operation Instructions (खाते चालविण्याची सूचना) is required with default `स्वतः` (Self). Allowed values: `फक्त प्रमुख खातेदार` (Only Primary Holder), `फक्त संयुक्त खातेदार` (Only Joint Holder), `दोन्ही खातेदार आवश्यक` (Both Holders Required), `दोघांपैकी कोणीही` (Either Holder), `स्वतः` (Self).

**Notes:** Field lives on Tab 3, itself conditional on [BR-014](#br-014--joint-holder-section-conditional-on-add-joint-holder-checkbox). `TODO:` persisted value when Tab 3 is skipped (single-holder account) is not stated — same open item as [savings BR-018](../savings/business-rules.md#br-018--account-operation-instructions-required-with-defined-values).

---

### BR-020 — New Daily Account wizard atomic save on create

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | Standing Decision 2026-07-24; [new-daily-account-screen.md](../../05-ui-ux/daily/new-daily-account-screen.md) — Tabs 1–3, footer actions |

**Rule:** On create, New Daily Account persists the Account, Nominee(s) (if Tab 2 enabled), and Joint Holder(s) (if Tab 3 enabled) only when the actor clicks **जतन करा** (Save) on the final visible tab, after all visible tabs pass validation. **पुढे** (Next) and **मागे** (Back) must not write partial records. **रीसेट** (Reset) clears wizard state without persisting.

**Notes:** Matches the atomic-save pattern confirmed for [savings BR-019](../savings/business-rules.md#br-019--new-savings-account-wizard-atomic-save-on-create), FD, Customer, and all Settings wizards.

---

## Rules — New Agent

### BR-021 — Agent identity requires an existing Customer

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [new-agent-screen.md](../../05-ui-ux/daily/new-agent-screen.md) — Tab 1, field #1 |

**Rule:** New Agent Tab 1 requires selecting an **existing** Customer via Autocomplete (`entityType: customer`); the agent's identity (name, KYC, contact) comes from that Customer record. The screen must not create a new Customer inline. A registered agent is what the Agent Autocomplete resolves on New Daily Account, Account Register, Agent Collection Management, and Agent-to-Agent Transfer.

**Notes:** Same identity-from-Customer pattern as the confirmed "Employee requires Customer" Standing Decision ([settings/master BR-001](../settings/master/business-rules.md#br-001--customer-required-for-staff-registration)). Mobile Number (field #3) is an optional agent contact override.

---

### BR-022 — Agent Status and Joining Date required

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-agent-screen.md](../../05-ui-ux/daily/new-agent-screen.md) — Tab 1, fields #2, #4 |

**Rule:** Agent Status (स्थिती) is required, defaulting to `चालू` (Active); allowed values `चालू`, `बंद` (Closed), `स्थगित` (Suspended). Joining Date (रुजू दिनांक) is required and defaults to the system date.

**Notes:** Agent Status is a **separate status domain** from deposit-account Status ([BR-009](#br-009--account-status-default-and-shared-values-across-deposit-products)) even though the three values coincide — a closed/suspended agent affects agent selectability, not an account's lifecycle. `TODO:` Whether a `बंद`/`स्थगित` agent is excluded from the Agent Autocomplete on account opening and collection is not stated — confirm the selectability rule.

---

### BR-023 — Agent linked savings account: Branch and Account Holder required

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-agent-screen.md](../../05-ui-ux/daily/new-agent-screen.md) — Tab 1, fields #5–#7 |

**Rule:** In the बचत खाते (Savings Account) block, Select Branch (शाखा निवडा) and Select Account Holder (खातेधारक निवडा) are required Autocomplete fields; Select GL (जी.एल. निवडा) is optional. This links the agent to the settlement/commission account used when collections and commissions are posted.

**Notes:** Dependency on GL master ([settings/accounting business-rules.md](../settings/accounting/business-rules.md)) and Account Holder / Branch master. The agent's linked GL/account is a target for the Collection posting ([BR-037](business-rules-part2.md#br-037--agent-collection-is-the-posting-point-for-daily-collections)).

---

### BR-024 — TDS Reason conditional on TDS = No

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [new-agent-screen.md](../../05-ui-ux/daily/new-agent-screen.md) — Tab 1, fields #8–#9 |

**Rule:** TDS applicability (होय / नाही) is an optional radio. Select Reason (कारण निवडा) is shown only when TDS = `नाही` (No), with values `सभासद` (Member), `फॉर्म १५ डीआय`, `फॉर्म १५ एच`, `फॉर्म १५ जी` — i.e. the exemption reason for not deducting TDS.

---

### BR-025 — Agent deduction blocks conditional on their checkboxes

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [new-agent-screen.md](../../05-ui-ux/daily/new-agent-screen.md) — Tab 1 Advanced, fields #10–#26 |

**Rule:** Meghdoot Agent Code (field #10) is an optional Advanced field. The सुरक्षा ठेव (Security Deposit, #11), मशीन कपात (Machine Deduction, #17), and भविष्य निर्वाह निधी (Provident Fund, #23) blocks are each gated by their own checkbox — their GL/Account Holder/limit/deduction fields are enabled and applicable only when the parent checkbox is checked; hidden/inert otherwise.

**Notes:** When Security Deposit is enabled, its Branch (field #12) becomes required (spec `Yes*`). GL/Account Holder lookups in each block depend on GL and Account Holder master.

---

### BR-026 — Agent commission config per scheme and amount slab

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [new-agent-screen.md](../../05-ui-ux/daily/new-agent-screen.md) — Tab 2, fields #1–#8, commission grid |

**Rule:** Commission Tab 2 requires Scheme (योजना निवडा, from Daily schemes), Commission % (कमिशन %), From Amount (रकमेतून), and Up to Amount (रकमे पर्यंत) per row. **+ टाका** (Add) appends the row to the commission grid; multiple scheme/amount-slab rows per agent are allowed. Advanced fields (Loan Account Commission %, Sales Commission %, Commission per Account, Consider All Credit Transactions) are optional per row.

**Notes:** This agent-level commission configuration is the source consulted when computing the एजंट कमिशन / एजंट कमिशन रेट columns during collection ([BR-036](business-rules-part2.md#br-036--collection-grid-computes-totals-penalty-discount-and-commission)), and is the candidate default for the per-account Commission Rate ([BR-006](#br-006--commission-rate-required-at-account-opening), TODO). Scheme dependency: [settings/schemes business-rules.md](../settings/schemes/business-rules.md).

---

### BR-027 — New Agent wizard atomic save on create

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | Standing Decision 2026-07-24; [new-agent-screen.md](../../05-ui-ux/daily/new-agent-screen.md) — Tabs 1–2, footer actions |

**Rule:** On create, New Agent persists the Agent record (Tab 1 general/savings/TDS/deduction data) together with its commission grid rows (Tab 2) only on the final **पूर्ण** (Complete/Save) after all visible tabs pass validation. **पुढे** (Next) and **मागे** (Back) must not write partial records.

**Notes:** Same atomic-save pattern as [BR-020](#br-020--new-daily-account-wizard-atomic-save-on-create) and the confirmed wizard standing decisions across Savings/FD/Customer/Settings.

---

## Related Documents

- [business-rules-part2.md](business-rules-part2.md) — BR-028…BR-045
- [overview.md](overview.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [changelog.md](changelog.md)
- [../../05-ui-ux/daily/new-daily-account-screen.md](../../05-ui-ux/daily/new-daily-account-screen.md)
- [../../05-ui-ux/daily/new-agent-screen.md](../../05-ui-ux/daily/new-agent-screen.md)
- [../savings/business-rules.md](../savings/business-rules.md)
- [../settings/schemes/business-rules.md](../settings/schemes/business-rules.md)
- [../settings/master/business-rules.md](../settings/master/business-rules.md)
- [../../00-project-overview/glossary.md](../../00-project-overview/glossary.md)
