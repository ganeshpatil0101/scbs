# Settings — Membership Sub-Area

## Purpose

Documents business rules and workflows for **सभासदत्व (Membership)** settings: share (equity) rule configuration and dividend calculation preview.

## Scope

Covers one UI screen (consolidated from Share Rules + Dividend Calculation):

| Screen | Spec | Business focus |
| :--- | :--- | :--- |
| सभासदत्व सेटिंग्ज (Membership Configuration) | [membership-configuration-screen.md](../../05-ui-ux/settings/membership/membership-configuration-screen.md) | Share rules grid + dividend calculation preview |

**Out of scope for this sub-area:** Operational New Membership, share transfer, dividend transaction posting (operational Membership module), Class A vs Class B rights beyond configuration filters.

## Responsibilities

- Maintain share rules per Member class (Member vs Nominal Member)
- Enforce face value, series, capital limits, and rule change date
- Persist share rules as grid rows; support remove
- Run dividend calculation as **preview only** (Year 1 — no posting from this screen)

## Features

| Feature | Use case | Primary screen |
| :--- | :--- | :--- |
| Save share rule row | UC-001 | Tab Share Rules |
| Remove share rule row(s) | UC-001 | Tab Share Rules |
| Preview dividend calculation | UC-002 | Tab Dividend Calculation |

## Dependencies

| Dependency | Domain / doc | Why |
| :--- | :--- | :--- |
| Member / Nominal Member | [glossary.md](../../00-project-overview/glossary.md) | Shared filter on both tabs |
| Branch master | Shared | Optional branch filter on dividend tab |
| Permission model | [settings/master/business-rules.md](../master/business-rules.md) BR-017 | Form permissions |
| Tenant setup | [tenant-setup.md](../../00-project-overview/tenant-setup.md) | Phase C3 |

## Owned Entities

| Entity | Description | DB doc status |
| :--- | :--- | :---: |
| `share_rule` | Share series rule per member class | TODO — `@design-database-schema` |
| `dividend_calc_run` | Optional preview session (not posted) | TODO — may be ephemeral only |

## Open Decisions (TODO — confirm with business)

| # | Topic | Blocks |
| :---: | :--- | :--- |
| 1 | Debit Account Head dropdown — fixed single default vs dynamic GL list | BR-014 notes |
| 2 | Read-only dividend settings labels — where configured / editable | System config ownership |
| 3 | Branch column on share-rules grid — auto HO / actor branch / explicit | Persist semantics |

## Related Documents

- [business-rules.md](business-rules.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [changelog.md](changelog.md)
- [../overview.md](../overview.md)
- [../../05-ui-ux/settings/membership/overview.md](../../05-ui-ux/settings/membership/overview.md)
- [../../AI_INDEX.md](../../AI_INDEX.md)
