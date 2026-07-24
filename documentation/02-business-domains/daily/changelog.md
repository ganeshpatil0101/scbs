# Changelog — Daily (Pigmy) Business Domain

| Version | Date | Changes | Author | Reason |
| :--- | :--- | :--- | :--- | :--- |
| 0.1 | 2026-07-24 | Initial domain documentation: overview, 45 business rules (39 confirmed, 6 TODO) across [business-rules.md](business-rules.md) (BR-001…BR-027) and [business-rules-part2.md](business-rules-part2.md) (BR-028…BR-045), 6 use cases, 7 workflows, 45 acceptance tests. Superseded specs (Daily Transaction, Manual Interest, old Agent Collection / Collection List) excluded per explicit request. Cross-checked dependencies on Customer (holder/nominee/agent identity), New Agent → New Daily Account (internal agent prerequisite), Settings/Schemes (scheme, duration/rate grid, agent commission), Settings/Accounting (GL posting), Settings/Master (permissions), Membership (canonical Nominee Relation list, not yet documented), Bank master (cheque instrument), and the not-yet-documented Accounting/Loan domains (collection posting, pigmy-for-loan linkage) | AI agent + business | `@generate-business-domain daily` |

## Standing Decisions Confirmed (2026-07-24)

| Decision | Value |
| :--- | :--- |
| Agent Collection posting point | Agent Collection Management is the financial-posting point for daily collections: the final action atomically posts member-account credits, agent commission, and the balancing GL transfer voucher under one Challan ([BR-037](business-rules-part2.md#br-037--agent-collection-is-the-posting-point-for-daily-collections)) |
| Agent-to-Agent Transfer commit | Selecting accounts and confirming reassigns (persists) the accounts' collecting-agent binding from the From-agent to the To-agent; blocked when From = To ([BR-041](business-rules-part2.md#br-041--from-and-to-agent-required-selection-reassigns-accounts)) |
| New Daily Account wizard save (create) | Persist Account + Nominee(s) + Joint Holder(s) only on final जतन करा after all visible tabs valid; Next/Back do not write partial records ([BR-020](business-rules.md#br-020--new-daily-account-wizard-atomic-save-on-create)) |
| New Agent wizard save (create) | Persist Agent + commission grid rows only on final पूर्ण after all visible tabs valid; Next/Back do not write partial records ([BR-027](business-rules.md#br-027--new-agent-wizard-atomic-save-on-create)) |
| Agent identity from Customer | Agent identity is drawn from an existing Customer record selected on New Agent Tab 1 (same pattern as Employee requires Customer) ([BR-021](business-rules.md#br-021--agent-identity-requires-an-existing-customer)) |
| काढा (Remove) semantics | Daily Account Register काढा deletes the account registration row (not hide) — same as Savings वगळा; the Daily register has no Close Account action ([BR-032](business-rules-part2.md#br-032--काढा-remove-deletes-the-account-registration-row)) |

## Open Items Requiring Business Confirmation

| BR | Topic | Raised in |
| :--- | :--- | :--- |
| BR-006 | Commission Rate default source (per-account vs agent config) | overview.md Open Decisions |
| BR-008 | Maturity Amount auto-derivation on New Daily Account | overview.md Open Decisions |
| BR-010 | Pigmy Account for Loan linkage (pending Loan domain) | overview.md Open Decisions |
| BR-011 | "Admin role" for Advanced Settings visibility | overview.md Open Decisions |
| BR-022 | Closed/suspended agent selectability | overview.md Open Decisions |
| BR-031 | Loan-linked (pink) register highlight source | overview.md Open Decisions |
| BR-033 | Account Details / Account Statement — no dedicated spec | overview.md Open Decisions |
| BR-036 | RD Penalty / RD Discount formulas | overview.md Open Decisions |
| BR-039 | Transfer-line balancing enforcement | overview.md Open Decisions |

## Related Documents

- [overview.md](overview.md)
- [business-rules.md](business-rules.md)
- [business-rules-part2.md](business-rules-part2.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [../../cbs-project-execution-plan.md](../../cbs-project-execution-plan.md)
