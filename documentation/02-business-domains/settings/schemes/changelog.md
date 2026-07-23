# Changelog — Settings / Schemes Business Domain

| Version | Date | Changes | Author | Reason |
| :--- | :--- | :--- | :--- | :--- |
| 0.1 | 2026-07-23 | Initial domain documentation: overview, 34 business rules (32 confirmed, 2 TODO), 2 use cases, 2 workflows, 35 acceptance tests | AI agent + business | Phase 1.7 Settings/Schemes; Standing Decisions: unique name within type, many schemes per GL, atomic Save; field-reference from superseded product specs (Approach B) |

## Standing Decisions Recorded

| Decision | Value | Confirmed |
| :--- | :--- | :---: |
| Type-specific field source | Superseded product specs as field-reference only; unified screen is primary | 2026-07-23 |
| Scheme name uniqueness | Unique within Scheme Type (tenant-scoped) | 2026-07-23 |
| GL Head cardinality | Many schemes may share one GL Head; each scheme has exactly one GL | 2026-07-23 |
| Create wizard persist | Atomic on final Complete/Save only; Next/Back do not persist | 2026-07-23 |

## Open Items Requiring Business Confirmation

| BR | Topic |
| :--- | :--- |
| BR-033 | Which Status values allow opening new accounts under the scheme |
| BR-034 | Whether ≥1 Duration & Rates and/or Interest Posting row is required on Save |
| — | Exact Drawing Power (D.P.) formula (glossary TODO) |

## Related Documents

- [overview.md](overview.md)
- [business-rules.md](business-rules.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
