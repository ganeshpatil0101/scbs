# Use Cases — Daily (Pigmy)

## Purpose

Actor goals for the Daily module screens. Each use case references business rules by ID ([business-rules.md](business-rules.md), [business-rules-part2.md](business-rules-part2.md)).

---

### UC-001 — Open a new Daily account

**Actors:** Clerk / Administrator (User with All Rights on New Daily Account form)

**Preconditions:**
1. Actor has All Rights on New Daily Account ([BR-045](business-rules-part2.md#br-045--daily-screens-use-master-permission-levels)).
2. A Customer record exists for the intended account holder ([BR-001](business-rules.md#br-001--customer-must-exist-before-a-daily-account-can-be-opened)).
3. At least one Daily scheme exists in Settings ([BR-002](business-rules.md#br-002--scheme-required-and-loaded-from-daily-scheme-master)).
4. At least one collecting Agent has been registered ([BR-003](business-rules.md#br-003--agent-branch-and-agent-required-agent-must-be-registered-first), [UC-002](#uc-002--register-a-new-collection-agent)).

**Main Flow:**
1. Actor opens **नवीन खाते (New Account)** under डेली (Daily).
2. **Tab 1 — खात्याची माहिती:** Actor resolves the Customer via Autocomplete ([BR-001](business-rules.md#br-001--customer-must-exist-before-a-daily-account-can-be-opened)); the read-only customer summary displays.
3. Actor selects Scheme ([BR-002](business-rules.md#br-002--scheme-required-and-loaded-from-daily-scheme-master)), Agent Branch, and Agent ([BR-003](business-rules.md#br-003--agent-branch-and-agent-required-agent-must-be-registered-first)).
4. Actor selects Duration — Duration (Months/Days) and Interest Rate auto-fill read-only ([BR-005](business-rules.md#br-005--duration-selected-from-scheme-grid-duration-and-rate-auto-filled)); enters Commission Rate ([BR-006](business-rules.md#br-006--commission-rate-required-at-account-opening)) and Daily Deposit Amount ([BR-008](business-rules.md#br-008--daily-deposit-amount-required-maturity-fields-optional)); confirms Current Date ([BR-007](business-rules.md#br-007--current-date-defaults-to-system-date)) and Status (default Active, [BR-009](business-rules.md#br-009--account-status-default-and-shared-values-across-deposit-products)).
5. Optionally, actor expands **प्रगत सेटिंग्ज** to set Sales Agent, interest overrides, limits, or bank-payout details ([BR-011](business-rules.md#br-011--advanced-settings-visibility-role-undefined), [BR-012](business-rules.md#br-012--advanced-overrides-optional-with-scheme-defaults)) and may set Pigmy Account for Loan ([BR-010](business-rules.md#br-010--pigmy-account-for-loan-flag-depends-on-undocumented-loan-domain)).
6. Actor optionally checks Add Nominee and/or Add Joint Holder to reveal Tabs 2/3 ([BR-013](business-rules.md#br-013--nominee-section-conditional-on-add-nominee-checkbox), [BR-014](business-rules.md#br-014--joint-holder-section-conditional-on-add-joint-holder-checkbox)), then clicks **पुढे (Next)**.
7. **Tab 2 — वारसदार (if enabled):** Actor resolves a nominee Customer or quick-adds one ([BR-015](business-rules.md#br-015--nominee-lookup-resolves-to-existing-or-quick-added-customer)), selects Relation ([BR-016](business-rules.md#br-016--nominee-relation-reuses-canonical-membership-list)), optionally enters Percentage ([BR-017](business-rules.md#br-017--nominee-percentage-optional-nomination-date-and-age-system-derived)), and clicks टाका (Add).
8. **Tab 3 — संयुक्त एसी धारक (if enabled):** Actor optionally checks Guardian, resolves a joint holder, clicks + जोड ([BR-018](business-rules.md#br-018--joint-holder-guardian-and-customer-add-validates-selection)), and selects Account Operation Instructions ([BR-019](business-rules.md#br-019--account-operation-instructions-required-with-defined-values)).
9. Actor clicks **जतन करा (Save)** — the only persist point ([BR-020](business-rules.md#br-020--new-daily-account-wizard-atomic-save-on-create)); the Account (with auto Account No., [BR-004](business-rules.md#br-004--account-no-auto-generated)) and any Nominee/Joint Holder rows are persisted.

**Alternative Flow:**
- **A1 — Single holder:** Actor leaves Add Nominee and Add Joint Holder unchecked; only Tab 1 is completed and saved.
- **A2 — Quick Add nominee:** Actor uses + नवीन ग्राहक जोडा to create a minimal Customer inline for the nominee.

**Exception Flow:**
- **E1 — Customer not found:** No match on Tab 1; actor must register the person via New Customer first ([BR-001](business-rules.md#br-001--customer-must-exist-before-a-daily-account-can-be-opened)).
- **E2 — Agent not registered:** No agent resolves; actor must register the agent via New Agent first ([BR-003](business-rules.md#br-003--agent-branch-and-agent-required-agent-must-be-registered-first)).
- **E3 — Required field missing:** System blocks Next/Save with a validation error (Scheme, Agent, Duration, Commission Rate, Daily Deposit Amount, Account Operation Instructions).
- **E4 — View Only:** Actor with View Only can view all tabs but cannot Save ([BR-045](business-rules-part2.md#br-045--daily-screens-use-master-permission-levels)).

**Post Conditions:**
1. A Daily account exists with a system-generated Account No., linked to the Customer, Scheme, and collecting Agent.
2. Zero or more Nominee and Joint Holder records exist per the enabled tabs.

**Referenced Business Rules:** BR-001 through BR-020, BR-045

---

### UC-002 — Register a new collection Agent

**Actors:** Administrator / Manager (User with All Rights on New Agent form)

**Preconditions:**
1. Actor has All Rights on New Agent ([BR-045](business-rules-part2.md#br-045--daily-screens-use-master-permission-levels)).
2. A Customer record exists for the person to be registered as agent ([BR-021](business-rules.md#br-021--agent-identity-requires-an-existing-customer)).
3. At least one Daily scheme exists for commission configuration ([BR-026](business-rules.md#br-026--agent-commission-config-per-scheme-and-amount-slab)).

**Main Flow:**
1. Actor opens **नवीन एजंट (New Agent)** under डेली → एजंट.
2. **Tab 1 — निधी माहिती:** Actor resolves the Customer ([BR-021](business-rules.md#br-021--agent-identity-requires-an-existing-customer)); sets Status (default Active) and Joining Date (default system date) ([BR-022](business-rules.md#br-022--agent-status-and-joining-date-required)); selects the linked savings account Branch and Account Holder ([BR-023](business-rules.md#br-023--agent-linked-savings-account-branch-and-account-holder-required)).
3. Actor optionally sets TDS applicability and, when No, the exemption Reason ([BR-024](business-rules.md#br-024--tds-reason-conditional-on-tds--no)).
4. Actor optionally expands **प्रगत सेटिंग्ज** and enables Security Deposit / Machine Deduction / Provident Fund blocks ([BR-025](business-rules.md#br-025--agent-deduction-blocks-conditional-on-their-checkboxes)), then clicks पुढे.
5. **Tab 2 — प्रतिनिधी माहिती:** Actor selects Scheme, enters Commission %, From/Up-to Amount, and clicks + टाका to add one or more commission slab rows ([BR-026](business-rules.md#br-026--agent-commission-config-per-scheme-and-amount-slab)).
6. Actor clicks **पूर्ण (Complete/Save)** — the only persist point ([BR-027](business-rules.md#br-027--new-agent-wizard-atomic-save-on-create)); the Agent and its commission rows are persisted together.

**Alternative Flow:**
- **A1 — Multiple slabs:** Actor adds several scheme/amount-slab rows before Save.

**Exception Flow:**
- **E1 — Customer not found:** Actor must register the person via New Customer first ([BR-021](business-rules.md#br-021--agent-identity-requires-an-existing-customer)).
- **E2 — Required field missing:** System blocks Next/Complete for missing Customer, Status, Joining Date, savings Branch/Account Holder (Tab 1) or Scheme/Commission/amount range (Tab 2).
- **E3 — View Only:** Actor can view but cannot Complete ([BR-045](business-rules-part2.md#br-045--daily-screens-use-master-permission-levels)).

**Post Conditions:**
1. An Agent exists, resolvable via Agent Autocomplete on all Daily screens.
2. One or more commission slab rows exist for the agent.

**Referenced Business Rules:** BR-021 through BR-027, BR-045

---

### UC-003 — Record and post an agent daily collection

**Actors:** Cashier / Clerk (User with All Rights on Agent Collection Management)

**Preconditions:**
1. Actor has All Rights on Agent Collection Management ([BR-045](business-rules-part2.md#br-045--daily-screens-use-master-permission-levels)).
2. A registered Agent with bound Daily accounts exists ([UC-001](#uc-001--open-a-new-daily-account), [UC-002](#uc-002--register-a-new-collection-agent)).

**Main Flow:**
1. Actor opens **एजंट कलेक्शन व्यवस्थापन** under डेली → एजंट. A Challan Number is generated ([BR-034](business-rules-part2.md#br-034--challan-number-auto-generated)).
2. **Tab 1 — एजंट संकलन:** Actor selects Agent, Cash/Transfer mode, Collection Amount, One Day / Multiple Days, and Collection Date; optionally narrows by Scheme/account range; clicks **बघा (View)** ([BR-035](business-rules-part2.md#br-035--collection-requires-agent-and-mode-selections-grid-loaded-on-view)).
3. System loads the collection grid with per-account balances, day-wise amounts, totals, RD penalty/discount, and agent commission ([BR-036](business-rules-part2.md#br-036--collection-grid-computes-totals-penalty-discount-and-commission)). Actor selects rows (or सर्व निवडा) and clicks **निर्मीती करा (Create)**.
4. **Tab 2 — संक्षिप्त तपशील:** Actor confirms instrument details; for Cheque, enters cheque no./date/name/bank ([BR-038](business-rules-part2.md#br-038--brief-details-instrument-fields-conditional-on-cheque)).
5. **Tab 3 — ट्रान्स्फर:** Actor adds GL/account posting lines that reconcile to the collection total ([BR-039](business-rules-part2.md#br-039--transfer-tab-posting-lines-reconcile-to-collection-total)).
6. On the final posting action, the system atomically posts member-account credits, agent commission, and the balancing GL transfer voucher ([BR-037](business-rules-part2.md#br-037--agent-collection-is-the-posting-point-for-daily-collections)).

**Alternative Flow:**
- **A1 — Zero an amount:** Actor uses रक्कम शुन्यवर सेट करा to exclude specific day amounts before posting.
- **A2 — Collection List:** Actor switches to **कलेक्शन यादी (Tab 4)**, enters Branch + Agent (required) and a date range, and clicks दाखवा to review historical collections ([BR-040](business-rules-part2.md#br-040--collection-list-search-requires-branch-and-agent)).

**Exception Flow:**
- **E1 — No accounts:** View returns an empty grid; nothing to post.
- **E2 — Unbalanced transfer:** `TODO:` behaviour when posting lines do not equal the collection total is unconfirmed ([BR-039](business-rules-part2.md#br-039--transfer-tab-posting-lines-reconcile-to-collection-total)).
- **E3 — View Only:** Actor can view collections/lists but cannot Create/Post ([BR-045](business-rules-part2.md#br-045--daily-screens-use-master-permission-levels)).

**Post Conditions:**
1. Selected member Daily accounts are credited, agent commission is recorded, and a balancing GL transfer voucher is posted, all under one Challan.
2. The collection appears in the Collection List.

**Referenced Business Rules:** BR-034 through BR-040, BR-045

---

### UC-004 — Reassign accounts between agents

**Actors:** Administrator / Manager (User with All Rights on Agent-to-Agent Transfer)

**Preconditions:**
1. Actor has All Rights on Agent-to-Agent Transfer ([BR-045](business-rules-part2.md#br-045--daily-screens-use-master-permission-levels)).
2. Two distinct registered agents exist, and the From-agent has at least one bound Daily account ([BR-041](business-rules-part2.md#br-041--from-and-to-agent-required-selection-reassigns-accounts), [BR-042](business-rules-part2.md#br-042--only-the-from-agents-accounts-are-listed-for-reassignment)).

**Main Flow:**
1. Actor opens **एजंट कडून एजंट कडे खाते ट्रान्सफर** under डेली → एजंट.
2. Actor resolves Agent (From) and Agent (To) ([BR-041](business-rules-part2.md#br-041--from-and-to-agent-required-selection-reassigns-accounts)); the grid lists the From-agent's accounts ([BR-042](business-rules-part2.md#br-042--only-the-from-agents-accounts-are-listed-for-reassignment)).
3. Actor selects specific accounts or सर्व निवडा and confirms the transfer.
4. System reassigns the selected accounts' collecting-agent binding from the From-agent to the To-agent ([BR-041](business-rules-part2.md#br-041--from-and-to-agent-required-selection-reassigns-accounts)).

**Alternative Flow:**
- **A1 — Export:** Actor clicks निर्यात करा to export the account list without reassigning.

**Exception Flow:**
- **E1 — Same agent:** System blocks the transfer when Agent (From) = Agent (To) ([BR-041](business-rules-part2.md#br-041--from-and-to-agent-required-selection-reassigns-accounts)).
- **E2 — Cross-branch / confirmation:** `TODO:` same-branch restriction and confirmation dialog unconfirmed ([BR-041](business-rules-part2.md#br-041--from-and-to-agent-required-selection-reassigns-accounts) Notes).
- **E3 — View Only:** Actor can view/export but cannot reassign ([BR-045](business-rules-part2.md#br-045--daily-screens-use-master-permission-levels)).

**Post Conditions:**
1. The selected Daily accounts are bound to the To-agent for future collections; balances and posted entries are unchanged.

**Referenced Business Rules:** BR-041, BR-042, BR-045

---

### UC-005 — Search and maintain Daily accounts via Account Register

**Actors:** Clerk / Cashier / Administrator (View Only for search; All Rights for Remove)

**Preconditions:**
1. Actor has View Only or All Rights on Account Register ([BR-045](business-rules-part2.md#br-045--daily-screens-use-master-permission-levels)).
2. One or more Daily accounts exist ([UC-001](#uc-001--open-a-new-daily-account)).

**Main Flow:**
1. Actor opens **खाते रजिस्टर** under डेली; the Organization header shows read-only ([BR-028](business-rules-part2.md#br-028--organization-auto-fill-header-from-session)).
2. Actor optionally enters any combination of Branch, Scheme, Agent, Account No. range, Customer No. range, Account Holder, and Status filters — all optional ([BR-029](business-rules-part2.md#br-029--account-register-primary-search-fields-all-optional), [BR-030](business-rules-part2.md#br-030--status-filter-shares-deposit-product-enum)) — and clicks **दाखवा (Show)**.
3. System displays matching accounts with pagination/totals; loan-linked rows render pink and matured rows light blue ([BR-031](business-rules-part2.md#br-031--results-grid-legend-loan-linked-and-matured-highlighting), [BR-033](business-rules-part2.md#br-033--account-register-follows-interactive-reporting-detail-and-statement-gaps)).
4. Actor optionally clicks तपशील, निर्यात करा, or खाते उतारा for the selected row ([BR-033](business-rules-part2.md#br-033--account-register-follows-interactive-reporting-detail-and-statement-gaps), TODO).
5. **To remove a row:** actor clicks काढा (Remove) to delete the selected account registration row ([BR-032](business-rules-part2.md#br-032--काढा-remove-deletes-the-account-registration-row)).

**Alternative Flow:**
- **A1 — No filters:** Show with no filters returns all entitled Daily accounts, subject to branch-scoping ([BR-029](business-rules-part2.md#br-029--account-register-primary-search-fields-all-optional) Notes, TODO).

**Exception Flow:**
- **E1 — No matches:** Empty grid state, not an error.
- **E2 — Remove with history:** `TODO:` remove behaviour on accounts with posted transactions is unresolved ([BR-032](business-rules-part2.md#br-032--काढा-remove-deletes-the-account-registration-row) Notes).
- **E3 — View Only / No Rights:** View Only cannot Remove; No Rights cannot navigate to the screen ([BR-045](business-rules-part2.md#br-045--daily-screens-use-master-permission-levels)).

**Post Conditions:**
1. Search: no data modified.
2. Remove: the selected account registration row is deleted.

**Referenced Business Rules:** BR-028 through BR-033, BR-045

---

### UC-006 — Calculate daily interest and maturity (Interest Multiplier)

**Actors:** Clerk / Cashier (any User with access to the Interest Multiplier screen)

**Preconditions:**
1. Actor has at least View Only on the Interest Multiplier screen ([BR-045](business-rules-part2.md#br-045--daily-screens-use-master-permission-levels)).
2. At least one Daily scheme exists ([BR-043](business-rules-part2.md#br-043--interest-multiplier-scheme-required-duration-and-rate-auto-filled)).

**Main Flow:**
1. Actor opens **व्याज गुणक** under डेली.
2. Actor selects Scheme — Duration and Interest Rate auto-fill read-only ([BR-043](business-rules-part2.md#br-043--interest-multiplier-scheme-required-duration-and-rate-auto-filled)); optionally chooses Simple/Compound and frequency.
3. Actor enters Deposit Amount and clicks **गणना करा (Calculate)** ([BR-044](business-rules-part2.md#br-044--deposit-amount-required-calculation-is-preview-only)).
4. System displays Total Amount, Interest Amount, Maturity Amount, and the daily interest chart — a preview only, with no account or posting side-effect.

**Alternative Flow:**
- **A1 — Reset:** Actor clicks पुनर्रचना करा to clear inputs and recalculate.

**Exception Flow:**
- **E1 — Missing input:** Calculate is blocked until Scheme and Deposit Amount are provided ([BR-044](business-rules-part2.md#br-044--deposit-amount-required-calculation-is-preview-only)).

**Post Conditions:**
1. No data is persisted; the calculation is informational only.

**Referenced Business Rules:** BR-043, BR-044, BR-045

---

## Related Documents

- [overview.md](overview.md)
- [business-rules.md](business-rules.md)
- [business-rules-part2.md](business-rules-part2.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [../../05-ui-ux/daily/new-daily-account-screen.md](../../05-ui-ux/daily/new-daily-account-screen.md)
- [../../05-ui-ux/daily/new-agent-screen.md](../../05-ui-ux/daily/new-agent-screen.md)
- [../../05-ui-ux/daily/agent-collection-management-screen.md](../../05-ui-ux/daily/agent-collection-management-screen.md)
