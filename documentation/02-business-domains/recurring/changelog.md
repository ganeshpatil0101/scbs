# Changelog — Recurring Business Domain

| Version | Date | Changes | Author | Reason |
| :--- | :--- | :--- | :--- | :--- |
| 0.1 | 2026-07-24 | Initial domain documentation: overview, 34 business rules (28 confirmed, 6 TODO), 3 use cases, 3 workflows, 34 acceptance tests. Superseded specs (Recurring Transaction / Credit Transaction, Manual Interest Assessment/Provision/Management) excluded per explicit request — deferred to the Accounting domain. Cross-checked dependencies on Customer (account holder/nominee eligibility), Settings/Schemes (scheme selection, duration/rate slab, interest type/compounding, Maturity Amount formula), Daily (Agent master), Settings/Master (permission model), Membership (canonical Nominee Relation list, not yet documented), and the not-yet-documented Loan domain (loan-linked pink row highlight) | AI agent + business | `@generate-business-domain recurring` |

## Standing Decisions Confirmed (2026-07-24)

| Decision | Value |
| :--- | :--- |
| Recurring Maturity Amount derivation | System-computed from the scheme interest formula (Interest Type/Compounding, rate, duration, installment amount, deposit-type frequency); scheme-grid Maturity Amount is a reference only for fixed double-money schemes — same approach as the confirmed FD Maturity Amount derivation ([BR-013](business-rules.md#br-013--maturity-amount-system-computed-from-scheme-interest-formula)) |
| New Recurring Account wizard save (create) | Persist Account + Nominee(s) + Joint Holder(s) only on final जतन करा after all visible tabs valid; Next/Back do not write partial records ([BR-024](business-rules.md#br-024--new-recurring-account-wizard-atomic-save-on-create)) |
| Recurring काढा (Remove) semantics | Account Register काढा deletes the registration row (not hide); no Close Account action on the Recurring register ([BR-029](business-rules.md#br-029--काढा-remove-deletes-the-account-registration-row)) |

## Open Items Requiring Business Confirmation

| BR | Topic | Raised in |
| :--- | :--- | :--- |
| BR-008 | "Admin role" undefined for Interest Rate override | overview.md Open Decisions |
| BR-012 | Deposit Type (installment frequency) full value set | overview.md Open Decisions |
| BR-013 / BR-034 | RD interest/day-count/compounding formula (DB/API phase) | overview.md Open Decisions |
| BR-015 | "Admin role" undefined for Advanced Settings visibility | overview.md Open Decisions |
| BR-028 | Loan-linked (pink) row highlight semantics (pending Loan domain) | overview.md Open Decisions |
| BR-029 (Notes) | Remove confirmation dialog and transaction-history restriction | overview.md Open Decisions |
| BR-031 | Account Details / Account Statement — no dedicated spec | overview.md Open Decisions |
| BR-005 | Account No. generation algorithm | overview.md Open Decisions |
| BR-027 | Account Register branch-scoping of results | overview.md Open Decisions |
| BR-023 | Account Operation Instructions persisted value when Tab 3 skipped | overview.md Open Decisions |

## Related Documents

- [overview.md](overview.md)
- [business-rules.md](business-rules.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [../../cbs-project-execution-plan.md](../../cbs-project-execution-plan.md)
