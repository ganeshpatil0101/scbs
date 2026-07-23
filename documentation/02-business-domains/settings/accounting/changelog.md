# Changelog — Settings / Accounting Business Domain

| Version | Date | Changes | Author | Reason |
| :--- | :--- | :--- | :--- | :--- |
| 0.1 | 2026-07-23 | Initial domain documentation: overview, 22 business rules (19 confirmed, 3 TODO), 2 use cases, 2 workflows, 25 acceptance tests | AI agent + business | Phase 1.7 Settings/Accounting; Standing Decisions: atomic Group+Head create, always new Group, Group/Head name unique tenant-wide, Branch Account requires Org+Branch |

## Standing Decisions Recorded

| Decision | Value | Confirmed |
| :--- | :--- | :---: |
| Create flow | Always new GL Group + new GL Head (no select-existing Group in Year 1) | 2026-07-23 |
| Persist | Atomic on final Complete only; Next/Back do not write | 2026-07-23 |
| Group Name uniqueness | Unique within tenant | 2026-07-23 |
| GL Head Name uniqueness | Unique within tenant | 2026-07-23 |
| Branch Account | Organization + Branch required when Branch Account selected | 2026-07-23 |

## Open Items Requiring Business Confirmation

| BR | Topic |
| :--- | :--- |
| BR-020 | Whether Balance Type Credit/Debit is mandatory on Save |
| BR-021 | Which Status values allow posting / scheme GL lookup |
| BR-022 | GL Head number generation algorithm (incl. Daily ≤ 99 ranges) |

## Related Documents

- [overview.md](overview.md)
- [business-rules.md](business-rules.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
