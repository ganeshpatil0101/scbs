# Business Rules — Daily (Pigmy) — Part 2

## Purpose

Continuation of [business-rules.md](business-rules.md). Covers the **डेली (Daily)** operational screens: Account Register (BR-028…BR-033), Agent Collection Management (BR-034…BR-040), Agent-to-Agent Transfer (BR-041…BR-042), Interest Multiplier (BR-043…BR-044), and the cross-cutting permission rule (BR-045).

**Sources:** [account-register-screen.md](../../05-ui-ux/daily/account-register-screen.md), [agent-collection-management-screen.md](../../05-ui-ux/daily/agent-collection-management-screen.md), [agent-to-agent-transfer-screen.md](../../05-ui-ux/daily/agent-to-agent-transfer-screen.md), [interest-multiplier-screen.md](../../05-ui-ux/daily/interest-multiplier-screen.md).

## Rule Index

| ID | Title | Type | Status |
| :--- | :--- | :--- | :---: |
| [BR-028](#br-028--organization-auto-fill-header-from-session) | Organization auto-fill header from session | Workflow | Confirmed |
| [BR-029](#br-029--account-register-primary-search-fields-all-optional) | Account Register primary search fields all optional | Eligibility | Confirmed |
| [BR-030](#br-030--status-filter-shares-deposit-product-enum) | Status filter shares deposit-product enum | Validation | Confirmed |
| [BR-031](#br-031--results-grid-legend-loan-linked-and-matured-highlighting) | Results grid legend: loan-linked and matured highlighting | Cross-cutting | TODO |
| [BR-032](#br-032--काढा-remove-deletes-the-account-registration-row) | काढा (Remove) deletes the account registration row | Workflow | Confirmed |
| [BR-033](#br-033--account-register-follows-interactive-reporting-detail-and-statement-gaps) | Account Register follows interactive reporting; detail and statement gaps | Cross-cutting | TODO |
| [BR-034](#br-034--challan-number-auto-generated) | Challan Number auto-generated | Workflow | Confirmed |
| [BR-035](#br-035--collection-requires-agent-and-mode-selections-grid-loaded-on-view) | Collection requires Agent and mode selections; grid loaded on View | Validation | Confirmed |
| [BR-036](#br-036--collection-grid-computes-totals-penalty-discount-and-commission) | Collection grid computes totals, penalty, discount, and commission | Workflow | Confirmed |
| [BR-037](#br-037--agent-collection-is-the-posting-point-for-daily-collections) | Agent Collection is the posting point for daily collections | Workflow | Confirmed |
| [BR-038](#br-038--brief-details-instrument-fields-conditional-on-cheque) | Brief Details instrument fields conditional on Cheque | Validation | Confirmed |
| [BR-039](#br-039--transfer-tab-posting-lines-reconcile-to-collection-total) | Transfer tab posting lines reconcile to collection total | Validation | Confirmed |
| [BR-040](#br-040--collection-list-search-requires-branch-and-agent) | Collection List search requires Branch and Agent | Eligibility | Confirmed |
| [BR-041](#br-041--from-and-to-agent-required-selection-reassigns-accounts) | From and To agent required; selection reassigns accounts | Workflow | Confirmed |
| [BR-042](#br-042--only-the-from-agents-accounts-are-listed-for-reassignment) | Only the From-agent's accounts are listed for reassignment | Eligibility | Confirmed |
| [BR-043](#br-043--interest-multiplier-scheme-required-duration-and-rate-auto-filled) | Interest Multiplier scheme required; duration and rate auto-filled | Validation | Confirmed |
| [BR-044](#br-044--deposit-amount-required-calculation-is-preview-only) | Deposit Amount required; calculation is preview only | Workflow | Confirmed |
| [BR-045](#br-045--daily-screens-use-master-permission-levels) | Daily screens use Master permission levels | Cross-cutting | Confirmed |

---

## Rules — Account Register

### BR-028 — Organization auto-fill header from session

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [account-register-screen.md](../../05-ui-ux/daily/account-register-screen.md) — Auto-fill header |

**Rule:** संस्था (Organization) is a read-only header Label sourced from the tenant session (see [glossary.md](../../00-project-overview/glossary.md) Organization). It is not repeated as a filter field and is not enterable.

---

### BR-029 — Account Register primary search fields all optional

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [account-register-screen.md](../../05-ui-ux/daily/account-register-screen.md) — Primary Search, fields #1–#9 |

**Rule:** All Primary Search fields (Branch, Scheme, Agent, Account No. From/To, Customer No. From/To, Account Holder, Status) are optional. Clicking **दाखवा** (Show) with no filters returns results per the actor's entitled scope. The legacy अतिरिक्त शोध पर्याय link is out of scope (no stub, no TODO), same as [savings BR-021](../savings/business-rules.md#br-021--account-register-primary-search-fields-all-optional).

**Notes:** Branch-scoping of results for actors with limited branch rights is `TODO:` unresolved — same open pattern as savings.

---

### BR-030 — Status filter shares deposit-product enum

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [account-register-screen.md](../../05-ui-ux/daily/account-register-screen.md) — field #9 |

**Rule:** Select Status (स्थिती निवडा) filter defaults to `चालू` (Active) and uses the same three-value deposit enum (`चालू`, `बंद`, `स्थगित`) as [BR-009](business-rules.md#br-009--account-status-default-and-shared-values-across-deposit-products) and the Savings Account Register.

---

### BR-031 — Results grid legend: loan-linked and matured highlighting

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | TODO |
| Source | [account-register-screen.md](../../05-ui-ux/daily/account-register-screen.md) — Results Grid legend |

**Rule:** `TODO:` The results grid legend colours rows: **Pink** = कर्ज असलेली खाती (accounts with a loan); **Light blue** = मुदत संपलेली खाती (matured accounts). Matured-row highlighting is derivable from the account's Maturity Date ([BR-008](business-rules.md#br-008--daily-deposit-amount-required-maturity-fields-optional)) versus current date. The loan-linked (pink) highlight depends on the undocumented Loan domain and the Pigmy-Account-for-Loan linkage ([BR-010](business-rules.md#br-010--pigmy-account-for-loan-flag-depends-on-undocumented-loan-domain)) — confirm the exact linkage when the Loan domain is authored.

**Notes:** Same pink loan-linked legend appears on Savings/FD/Recurring registers; Daily is legend-only (no explicit filter checkbox), unlike [savings BR-022](../savings/business-rules.md#br-022--loan-linked-accounts-filter-depends-on-undocumented-loan-domain).

---

### BR-032 — काढा (Remove) deletes the account registration row

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [account-register-screen.md](../../05-ui-ux/daily/account-register-screen.md) — Sidebar actions |

**Rule:** The Account Register sidebar action काढा (Remove) deletes the selected account registration row — it does not merely hide the row from the current view. This is the same semantics confirmed for the Savings register's वगळा action ([savings BR-024](../savings/business-rules.md#br-024--वगळा-exclude-is-equivalent-to-काढा-remove)).

**Notes:** The Daily Account Register sidebar has तपशील, निर्यात करा, काढा, and खाते उतारा — it does **not** expose a खाते बंद करा (Close Account) action (unlike the Savings register); Daily account closure is not initiated from this screen. `TODO:` Whether Remove requires a confirmation dialog and whether it is blocked for accounts with posted transaction history is unresolved — same open item as savings.

---

### BR-033 — Account Register follows interactive reporting; detail and statement gaps

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | TODO |
| Source | [account-register-screen.md](../../05-ui-ux/daily/account-register-screen.md); [business-goals.md](../../00-project-overview/business-goals.md) BG-005 |

**Rule:** Account Register implements the platform interactive-reporting standard (BG-005): optional Primary Search filters, a 17-column results grid, and तपशील / निर्यात करा / खाते उतारा sidebar actions. `TODO:` तपशील (Details) has no dedicated Account Information screen spec, and खाते उतारा (Account Statement) has no deposit-account statement report ([reports/overview.md](../../05-ui-ux/reports/overview.md) documents a Loan statement only). Same deferral as [savings BR-026](../savings/business-rules.md#br-026--account-details-and-account-statement-lack-dedicated-specs).

---

## Rules — Agent Collection Management

### BR-034 — Challan Number auto-generated

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [agent-collection-management-screen.md](../../05-ui-ux/daily/agent-collection-management-screen.md) — Tab 1, field #1 |

**Rule:** Challan Number (चलन क्रमांक) is a system-generated read-only Label identifying the collection batch. It is not enterable.

**Notes:** Generation algorithm (per-branch vs. global sequence) is `TODO:` not specified — same open pattern as other auto-generated numbers ([BR-004](business-rules.md#br-004--account-no-auto-generated)).

---

### BR-035 — Collection requires Agent and mode selections; grid loaded on View

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [agent-collection-management-screen.md](../../05-ui-ux/daily/agent-collection-management-screen.md) — Tab 1, fields #2–#12 |

**Rule:** Tab 1 requires Select Agent (एजंट निवडा, [BR-021](business-rules.md#br-021--agent-identity-requires-an-existing-customer)), a Cash / Transfer (रोख / ट्रान्सफर) mode, Collection Amount (कलेक्शन रक्कम), a One Day / Multiple Days (एक दिवसीय / अनेक दिवस) mode, and Collection Date (From). Branch defaults to the logged-in branch. Scheme, Account No. range, Mark Receipt Number, and the account/L.F. ordering radio are optional filters. **बघा** (View) loads the collection grid for the selected agent and filters.

**Notes:** The Cash / Transfer mode determines the downstream posting path — Cash settles at the cashier; Transfer routes through the Transfer tab GL posting lines ([BR-039](#br-039--transfer-tab-posting-lines-reconcile-to-collection-total)). One Day vs Multiple Days governs how many day columns (१ ला दिवस…१० वा दिवस) are captured in the grid.

---

### BR-036 — Collection grid computes totals, penalty, discount, and commission

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [agent-collection-management-screen.md](../../05-ui-ux/daily/agent-collection-management-screen.md) — Tab 1, Collection Grid + footer summary |

**Rule:** The collection grid lists each account's balance and per-day collection amounts (Day 1…Day 10), and derives per-row एकूण (Total), आर डी दंड (RD Penalty), आर डी सवलत (RD Discount), एजंट कमिशन (Agent Commission), and एजंट कमिशन रेट (Agent Commission Rate). The footer aggregates एकूण रक्कम, एकूण एजंट कमिशन, and एकूण निवडलेल्या नोंदी. सर्व निवडा selects all rows; रक्कम शुन्यवर सेट करा zeroes the selected amounts.

**Notes:** Agent Commission Rate is derived from the agent's commission configuration ([BR-026](business-rules.md#br-026--agent-commission-config-per-scheme-and-amount-slab)) and/or the per-account Commission Rate ([BR-006](business-rules.md#br-006--commission-rate-required-at-account-opening)). `TODO:` The exact RD Penalty / RD Discount formulas are not defined in the spec — confirm with the scheme's penalty/discount configuration when documented.

---

### BR-037 — Agent Collection is the posting point for daily collections

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | Standing Decision 2026-07-24 (business-confirmed); [agent-collection-management-screen.md](../../05-ui-ux/daily/agent-collection-management-screen.md) — Tab 1 निर्मीती करा; Tabs 2–3 |

**Rule:** Agent Collection Management is the financial-posting point for daily collections (confirmed 2026-07-24). On the final posting action (निर्मीती करा / Create after the collection, instrument, and transfer tabs are completed), the system posts, as one atomic voucher: (a) credit entries to each selected member's Daily account for that account's collected amount, (b) the agent commission, and (c) the balancing GL/account transfer voucher against the agent's linked settlement account ([BR-023](business-rules.md#br-023--agent-linked-savings-account-branch-and-account-holder-required)). Partial/interim navigation between tabs must not post.

**Notes:** This confirms Daily owns collection posting rather than deferring it to the Accounting [deposit-account-transaction-screen.md](../../05-ui-ux/accounting/deposit-account-transaction-screen.md); that superseded per-product Transaction screen is excluded from this domain. Cross-domain dependency: the resulting ledger entries follow the Accounting ledger/GL posting rules (`02-business-domains/accounting/`, Phase 3). `TODO:` exact voucher/scroll numbering and cashier (रोखपाल) hand-off for the Cash mode is not detailed on this screen.

---

### BR-038 — Brief Details instrument fields conditional on Cheque

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [agent-collection-management-screen.md](../../05-ui-ux/daily/agent-collection-management-screen.md) — Tab 2 (संक्षिप्त तपशील) |

**Rule:** Tab 2 captures the instrument details for the collection using the same field set as the deposit-transaction Instrument tab. Cheque Type (धनादेश प्रकार) defaults to `स्लिप` (Slip). When Cheque Type = `चेक` (Cheque), the cheque fields become applicable — Cheque Date (default system date), Cheque No., Name, and Select Bank (from Bank Master) are required per the spec's Required column. Cheque Amount may default from the Tab 1 collection total and Amount in Words may auto-fill from it.

**Notes:** Shares the instrument pattern with [deposit-account-transaction-screen.md](../../05-ui-ux/accounting/deposit-account-transaction-screen.md) Tab 2; Select Bank resolves against Bank Master via Autocomplete.

---

### BR-039 — Transfer tab posting lines reconcile to collection total

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [agent-collection-management-screen.md](../../05-ui-ux/daily/agent-collection-management-screen.md) — Tab 3 (ट्रान्स्फर) |

**Rule:** Tab 3 captures GL/account posting lines for the collection. Each line requires Branch, GL, Account Holder, Account No., and Transaction Amount (Autocomplete-resolved per [entity-autocomplete-pattern.md](../../05-ui-ux/shared/entity-autocomplete-pattern.md)); **+ टाका** (Add) appends a row. The एकूण व्यवहार रक्कम (Total Transaction Amount) reconciles to the collection total from Tab 1 ([BR-036](#br-036--collection-grid-computes-totals-penalty-discount-and-commission)). अनियमित करा marks a line irregular; निटवा clears selected lines.

**Notes:** This is the posting-lines tab of the collection ([BR-037](#br-037--agent-collection-is-the-posting-point-for-daily-collections)); it is **not** the Agent-to-Agent Transfer screen ([BR-041](#br-041--from-and-to-agent-required-selection-reassigns-accounts)). `TODO:` Whether Save is blocked when total posting lines do not equal the collection total (strict balancing) is not stated — recommend a balancing check consistent with Multi-GL transactions.

---

### BR-040 — Collection List search requires Branch and Agent

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [agent-collection-management-screen.md](../../05-ui-ux/daily/agent-collection-management-screen.md) — Tab 4 (कलेक्शन यादी) |

**Rule:** The Collection List tab requires Select Branch and Select Agent before **दाखवा** (Show); Scheme and Transaction Date From/To are optional filters. Results list each collection's Agent Name, Transaction Date, and Collection Amount, with तपशील / निर्यात करा actions and an एकूण footer total.

**Notes:** This tab is the read/history view (consolidating the superseded Agent Collection List spec). Required Branch + Agent contrasts with the all-optional Account Register search ([BR-029](#br-029--account-register-primary-search-fields-all-optional)).

---

## Rules — Agent-to-Agent Transfer

### BR-041 — From and To agent required; selection reassigns accounts

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | Standing Decision 2026-07-24 (business-confirmed); [agent-to-agent-transfer-screen.md](../../05-ui-ux/daily/agent-to-agent-transfer-screen.md) — fields #1–#3, results grid |

**Rule:** Select Agent (From) (एजंट निवडा (कडून)) and Select Agent (To) (एजंट निवडा (कडे)) are both required Autocomplete fields resolving to registered agents ([BR-021](business-rules.md#br-021--agent-identity-requires-an-existing-customer)). Selecting one or more listed accounts (or सर्व निवडा) and confirming the transfer **reassigns (persists)** those Daily accounts' collecting-agent binding ([BR-003](business-rules.md#br-003--agent-branch-and-agent-required-agent-must-be-registered-first)) from the From-agent to the To-agent (confirmed 2026-07-24). The transfer must be blocked when From-agent = To-agent.

**Notes:** The spec lists only a निर्यात करा (Export) action for the grid; the commit action reassigns the selected accounts. `TODO:` Whether reassignment is additionally restricted to agents in the same branch, and whether it requires a confirmation dialog, is not stated — confirm before implementation. Reassignment changes future collection responsibility only; it does not move account balances or post financial entries.

---

### BR-042 — Only the From-agent's accounts are listed for reassignment

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [agent-to-agent-transfer-screen.md](../../05-ui-ux/daily/agent-to-agent-transfer-screen.md) — results grid |

**Rule:** After the From-agent is resolved, the results grid lists that agent's currently bound Daily accounts (Account, Account No., Name, Balance). Only accounts presently assigned to the From-agent are eligible for reassignment to the To-agent.

---

## Rules — Interest Multiplier

### BR-043 — Interest Multiplier scheme required; duration and rate auto-filled

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [interest-multiplier-screen.md](../../05-ui-ux/daily/interest-multiplier-screen.md) — Input fields #1, #5, #6 |

**Rule:** Select Scheme (योजना निवडा) is required and loads from Daily schemes. Duration (Months) and Interest Rate (% p.a.) are read-only Labels auto-filled from the selected scheme (sample defaults `12` months, `6`%). Simple/Compound and compounding-frequency radios are optional inputs to the calculation.

**Notes:** Scheme dependency mirrors [BR-002](business-rules.md#br-002--scheme-required-and-loaded-from-daily-scheme-master). Breadcrumb shows `ठेवी` (Deposits) in the screenshot but the screen serves pigmy/daily scheme calculation (audit note in [ux-optimization.md](../../05-ui-ux/daily/ux-optimization.md)).

---

### BR-044 — Deposit Amount required; calculation is preview only

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [interest-multiplier-screen.md](../../05-ui-ux/daily/interest-multiplier-screen.md) — field #4, Output, formulas |

**Rule:** Deposit Amount (ठेव रक्कम) is required. **गणना करा** (Calculate) computes Total Amount, Interest Amount, and Maturity Amount (all read-only) plus the दैनिक व्याज चार्ट grid, using the displayed formulas (मासिक संग्रह = ठेव रक्कम × 365/12; एकूण रक्कम = मासिक संग्रह × कालावधी). The screen is a **preview/what-if calculator only** — it does not open an account or post any transaction. निश्चित करा confirms the chart view; पुनर्रचना करा resets inputs.

**Notes:** Distinct from the stored Maturity Amount on New Daily Account ([BR-008](business-rules.md#br-008--daily-deposit-amount-required-maturity-fields-optional)). Same preview-only, non-posting nature as the Membership Dividend Calculate ([Standing Decision](../settings/membership/business-rules.md)).

---

## Rules — Cross-cutting

### BR-045 — Daily screens use Master permission levels

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | Confirmed |
| Source | [settings/master business-rules.md](../settings/master/business-rules.md#br-017--permission-levels-are-all-rights--view-only--no-rights) BR-017 |

**Rule:** Access to all Daily screens (New Daily Account, New Agent, Account Register, Agent Collection Management, Agent-to-Agent Transfer, Interest Multiplier) follows Master permission levels: **All Rights** (full edit/save/post), **View Only** (read-only; Save/Add/Remove/Create/Post/Transfer actions hidden), **No Rights** (navigation blocked). Do not redefine permission semantics in this domain.

**Notes:** Same cross-cutting rule as [savings BR-020](../savings/business-rules.md#br-020--savings-screens-use-master-permission-levels).

---

## Related Documents

- [business-rules.md](business-rules.md) — BR-001…BR-027
- [overview.md](overview.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [../../05-ui-ux/daily/account-register-screen.md](../../05-ui-ux/daily/account-register-screen.md)
- [../../05-ui-ux/daily/agent-collection-management-screen.md](../../05-ui-ux/daily/agent-collection-management-screen.md)
- [../../05-ui-ux/daily/agent-to-agent-transfer-screen.md](../../05-ui-ux/daily/agent-to-agent-transfer-screen.md)
- [../../05-ui-ux/daily/interest-multiplier-screen.md](../../05-ui-ux/daily/interest-multiplier-screen.md)
- [../savings/business-rules.md](../savings/business-rules.md)
- [../../00-project-overview/glossary.md](../../00-project-overview/glossary.md)
