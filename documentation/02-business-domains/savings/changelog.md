# Changelog — Savings Business Domain

| Version | Date | Changes | Author | Reason |
| :--- | :--- | :--- | :--- | :--- |
| 0.1 | 2026-07-24 | Initial domain documentation: overview, 26 business rules (18 confirmed, 8 TODO), 2 use cases, 2 workflows, 26 acceptance tests. Superseded specs (Savings Transaction, Manual Interest Calculation) excluded per explicit request — deferred to the Accounting domain. Cross-checked dependencies on Customer (account holder/nominee eligibility), Settings/Schemes (scheme selection, interest rate, Allow Only Members), Settings/Master (permission model), Membership (canonical Nominee Relation list, not yet documented), and the not-yet-documented Loan/Daily/Recurring/FD domains (Close Account cross-product relationship check) | AI agent + business | `@generate-business-domain savings` |

## Standing Decisions Confirmed (2026-07-24)

| Decision | Value |
| :--- | :--- |
| Close Account precondition | Requires account balance = 0 **and** the customer holds no other active relationship with the bank (Loan, Daily, Recurring, Fixed Deposit) — all such relationships must be closed first ([BR-025](business-rules.md#br-025--close-account-requires-zero-balance-and-no-other-active-bank-relationships)) |
| वगळा vs. काढा | The Savings Account Register's वगळा (Exclude) sidebar action is the same action as काढा (Remove) on the FD/Daily/Recurring Account Register/Management screens — spec wording variance only, not a distinct behavior ([BR-024](business-rules.md#br-024--वगळा-exclude-is-equivalent-to-काढा-remove)) |

## Open Items Requiring Business Confirmation

| BR | Topic | Raised in |
| :--- | :--- | :--- |
| BR-003 | Member-only scheme enforcement mechanism not exposed on New Savings Account | overview.md Open Decisions |
| BR-005 | "Admin role" undefined for Interest Rate override | overview.md Open Decisions |
| BR-009 | "Admin role" undefined for Advanced Settings visibility | overview.md Open Decisions |
| BR-021 | Account Register branch-scoping of results | overview.md Open Decisions |
| BR-022 | Loan-linked accounts filter exact semantics (pending Loan domain) | overview.md Open Decisions |
| BR-024 (Notes) | Remove confirmation dialog and transaction-history restriction | overview.md Open Decisions |
| BR-026 | Account Details / Account Statement — no dedicated spec | overview.md Open Decisions |

## Related Documents

- [overview.md](overview.md)
- [business-rules.md](business-rules.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [../../cbs-project-execution-plan.md](../../cbs-project-execution-plan.md)
