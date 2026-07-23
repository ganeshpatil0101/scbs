# Changelog — Settings / Loan Business Domain

| Version | Date | Changes | Author | Reason |
| :--- | :--- | :--- | :--- | :--- |
| 0.1 | 2026-07-23 | Initial domain documentation: overview, 14 business rules (12 confirmed, 2 TODO), 1 use case, 1 workflow, 14 acceptance tests; UI spec fields #5–#6 added for new rates | AI agent + business | Phase 1.7 Settings/Loan; Standing Decisions: new interest required, penalty optional, template always updated, apply radios as stated |

## Standing Decisions Recorded

| Decision | Value | Confirmed |
| :--- | :--- | :---: |
| New Interest Rate | Required (p.a. %) | 2026-07-23 |
| New Penalty Rate | Optional (p.a. %) | 2026-07-23 |
| Scheme template | Always updated on Save | 2026-07-23 |
| Apply to All Accounts | Updates existing + future accounts under scheme | 2026-07-23 |
| Apply to New Accounts Only | Template updated; existing accounts keep prior rates | 2026-07-23 |

## Open Items Requiring Business Confirmation

| BR | Topic |
| :--- | :--- |
| BR-013 | All duration slabs vs selected duration |
| BR-014 | Export format and contents |

## Related Documents

- [overview.md](overview.md)
- [business-rules.md](business-rules.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
