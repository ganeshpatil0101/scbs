# Changelog — Customer Business Domain

| Version | Date | Changes | Author | Reason |
| :--- | :--- | :--- | :--- | :--- |
| 0.1 | 2026-07-24 | Initial domain documentation: overview, 33 business rules (28 confirmed, 5 TODO), 4 use cases, 4 workflows, 33 acceptance tests. Cross-checked dependencies on Settings/Master (permission model, branch rights, Staff→Customer link), Membership (canonical Nominee Relation list), Settings/Accounting (GL linkage for Other Account types), and the shared Quick Add Customer / entity-autocomplete / Google Maps address patterns | AI agent + business | `@generate-business-domain customer` — first full domain after Settings Phase 1.7 |

## Standing Decisions Confirmed (2026-07-24)

| Decision | Value |
| :--- | :--- |
| New Customer wizard save (create) | Persist only on final Complete/Save after Tabs 1–2 valid; Next/Back do not write partial records ([BR-021](business-rules.md#br-021--new-customer-wizard-atomic-save-on-create)) |
| KYC mandatory documents | Do not block Save; `आवश्यक` badge is a reminder only, upload may happen later ([BR-019](business-rules.md#br-019--kyc-mandatory-documents-do-not-block-save)) |

## Open Items Requiring Business Confirmation

| BR | Topic | Raised in |
| :--- | :--- | :--- |
| BR-024 | Customer List branch-scoping of results | overview.md Open Decisions |
| BR-025 | Non-Individual Customer Type required-field relaxation | overview.md Open Decisions |
| BR-028 | Other Account Status filter omits `बंद` (Closed) | overview.md Open Decisions |
| BR-029 | Duplicate Other Account (same customer, same type) prevention | overview.md Open Decisions |
| BR-027 (Notes) | GL Head linkage per Other Account type | overview.md Open Decisions |

## Related Documents

- [overview.md](overview.md)
- [business-rules.md](business-rules.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [../../cbs-project-execution-plan.md](../../cbs-project-execution-plan.md)
