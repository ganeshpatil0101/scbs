# Changelog — Settings / Master Business Domain

| Version | Date | Changes | Author | Reason |
| :--- | :--- | :--- | :--- | :--- |
| 0.9 | 2026-07-23 | Confirmed BR-023: unregistered form → No Rights (fail closed); AT-024; Settings/Master TODO pass complete except optional matrix tweaks | AI agent + business | Standing Decision resolution pass |
| 0.8 | 2026-07-23 | Confirmed BR-022: soft warning on self-lockout risk for Staff Access / User Role; Save allowed; AT-023 | AI agent + business | Standing Decision resolution pass |
| 0.7 | 2026-07-23 | Confirmed BR-021: blank password on edit keeps existing hash; AT-022 | AI agent + business | Standing Decision resolution pass |
| 0.6 | 2026-07-23 | Confirmed BR-020 (assign existing Role); added Clerk/Cashier/Manager default-role-templates.md (51 forms); linked tenant-setup.md; AT-021 | AI agent + business | Standing Decision + tenant seed data |
| 0.5 | 2026-07-23 | Confirmed BR-019 / WF-001: create wizard persists only on final Save (atomic); added AT-020 | AI agent + business | Standing Decision resolution pass |
| 0.4 | 2026-07-23 | Confirmed BR-018: ≥1 branch right required; single-branch (HO) tenant auto-assigns that branch; added AT-019 | AI agent + business | Standing Decision resolution pass |
| 0.3 | 2026-07-23 | Confirmed BR-012: Super User = All Rights on all forms; branch rights still enforced; updated AT-018, WF-003 | AI agent + business | Standing Decision resolution pass |
| 0.2 | 2026-07-23 | Confirmed BR-010 (login unique within tenant) and BR-011 (min 8, letter+digit, no history); updated AT-016, AT-017 | AI agent + business | Standing Decision resolution pass |
| 0.1 | 2026-07-23 | Initial domain documentation: overview, 18 business rules (14 confirmed, 4 TODO), 3 use cases, 3 workflows, 18 acceptance tests | AI agent | Phase 1.7 template — Settings/Master first domain per resequenced execution plan |
| 0.1 | 2026-07-23 | Created `@generate-business-domain` skill; registered in AI_INDEX and generation-rules | AI agent | Reusable workflow for remaining domains |

## Open Items Requiring Business Confirmation

| BR | Topic | Raised in |
| :--- | :--- | :--- |
| — | Default role matrix cell values (Clerk/Cashier/Manager) — optional bank review | default-role-templates.md |

## Related Documents

- [overview.md](overview.md)
- [business-rules.md](business-rules.md)
- [use-cases.md](use-cases.md)
- [../../cbs-project-execution-plan.md](../../cbs-project-execution-plan.md)
