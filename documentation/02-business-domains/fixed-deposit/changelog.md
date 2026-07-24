# Changelog — Fixed Deposit Business Domain

| Version | Date | Changes | Author | Reason |
| :--- | :--- | :--- | :--- | :--- |
| 0.1 | 2026-07-24 | Initial domain documentation: overview, 43 business rules (34 confirmed, 9 TODO), 4 use cases, 4 workflows, 43 acceptance tests. Superseded specs (FD Transaction, FD Manual Interest Calculation, FD Account Register, Account Renewal List) excluded per explicit request — Transaction/Manual Interest deferred to the Accounting domain; Register/Renewal consolidated into FD Account Management. Cross-checked dependencies on Customer (account holder / nominee / joint holder eligibility), Settings/Schemes (scheme selection, interest type/compounding, interest-rate slab, duration & maturity amount, auto renewal), Settings/Master (permission model), Membership (canonical Nominee Relation list, not yet documented), Daily/Agent master (Agent lookups), and the not-yet-documented Loan/Deposit-Loan and Accounting domains (loan-linked legend, Deposit Loan Installment, renewal execution) | AI agent + business | `@generate-business-domain fixed-deposit` |

## Standing Decisions Confirmed (2026-07-24)

| Decision | Value |
| :--- | :--- |
| Maturity Amount / Return Date derivation | System-computed from the selected scheme's interest formula (Interest Type / Compounding, Interest Rate, Duration, FD Amount). The scheme Duration & Rates "Maturity Amount" column is a reference value used only for fixed-maturity double-money schemes (दामदुप्पट / कॅश सर्टिफिकेट) ([BR-012](business-rules.md#br-012--maturity-amount-return-date-and-receipt-date-system-computed)) |
| New FD Account atomic save | Account + Nominee(s) + Joint Holder(s) persist only on final **पूर्ण** (Complete) after all visible tabs validate; Next/Back never persist partial records ([BR-029](business-rules.md#br-029--new-fd-account-wizard-atomic-save-on-create)) |
| काढा (Remove) semantics | Deletes the selected account registration row (not a hide); same semantics the Savings register's वगळा was aligned to ([BR-034](business-rules.md#br-034--काढा-remove-deletes-the-account-registration-row)) |

## Open Items Requiring Business Confirmation

| BR | Topic | Raised in |
| :--- | :--- | :--- |
| BR-010 | "Admin role" undefined for Interest Rate override | overview.md Open Decisions #4 |
| BR-015 | "Admin role" undefined for Advanced Settings visibility | overview.md Open Decisions #4 |
| BR-016 | Receipt Number auto-increment vs. manual entry | overview.md Open Decisions #5 |
| BR-017 | Multiple FD workflow semantics (one vs. many accounts) | overview.md Open Decisions #2 |
| BR-012 / BR-043 | Exact FD interest day-count/compounding formula | overview.md Open Decisions #3 |
| BR-024 | Account Operation Instructions persisted value when Joint Holder tab skipped | overview.md Open Decisions #6 |
| BR-026 / BR-036 | Renewal execution at maturity and Renewal List event source | overview.md Open Decisions #7 |
| BR-031 | Register branch-scoping of results | overview.md Open Decisions #8 |
| BR-032 | Loan-linked (pink) highlight exact linkage (pending Loan domain) | overview.md Open Decisions #9 |
| BR-034 | काढा confirmation dialog and transaction-history restriction | overview.md Open Decisions #10 |
| BR-035 | Account Details / Account Statement — no dedicated spec | overview.md Open Decisions #11 |
| BR-039 | Deposit Loan Installment interest basis + what "Set" persists (pending Loan domain) | overview.md Open Decisions #12 |
| BR-040 | Deposit Loan Installment Tabs 2–6 (uncaptured; candidate for removal) | overview.md Open Decisions #13 |

## Related Documents

- [overview.md](overview.md)
- [business-rules.md](business-rules.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [../../cbs-project-execution-plan.md](../../cbs-project-execution-plan.md)
