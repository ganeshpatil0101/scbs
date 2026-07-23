# Settings — Loan Sub-Area

## Purpose

Documents business rules and workflows for **कर्ज (Loan)** settings: changing interest rates on existing Loan schemes (scheme templates created under Settings/Schemes).

## Scope

Covers one UI screen:

| Screen | Spec | Business focus |
| :--- | :--- | :--- |
| व्याज दरात बदल (Interest Rate Change) | [loan-interest-rate-change-screen.md](../../05-ui-ux/settings/loan/loan-interest-rate-change-screen.md) | Update loan scheme rates + application scope + history |

**Out of scope for this sub-area:** Creating loan schemes (Settings/Schemes), operational loan disbursement/transactions, NPA processing.

## Responsibilities

- Select a Loan scheme and effective Change Date
- Capture new interest rate (required) and optional penalty rate
- Always update the scheme template rates
- Apply new rate to all accounts or to new accounts only per radio selection
- Retain a collapsible history of past rate changes

## Features

| Feature | Use case | Primary screen |
| :--- | :--- | :--- |
| Change loan scheme interest rate | UC-001 | Interest Rate Change |
| View past rate changes | UC-001 | Collapsible history |
| Export rate-change form/history | UC-001 | Export action |

## Dependencies

| Dependency | Domain / doc | Why |
| :--- | :--- | :--- |
| Loan schemes | [settings/schemes/](../schemes/overview.md) | Scheme dropdown source |
| Permission model | [settings/master/business-rules.md](../master/business-rules.md) BR-017 | Form permissions |
| Tenant setup | [tenant-setup.md](../../00-project-overview/tenant-setup.md) | Phase C4 |

## Owned Entities

| Entity | Description | DB doc status |
| :--- | :--- | :---: |
| `loan_scheme_rate_change` | History row (scheme, date, previous/new rates, apply scope) | TODO — `@design-database-schema` |
| `scheme` (loan) | Template rates updated on Save | See schemes domain |

## Open Decisions (TODO — confirm with business)

| # | Topic | Blocks |
| :---: | :--- | :--- |
| 1 | Whether rate change revises all duration slabs or a selected duration only | History grid has Duration column |
| 2 | Export format and contents | Export button on screen |

## Related Documents

- [business-rules.md](business-rules.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [changelog.md](changelog.md)
- [../overview.md](../overview.md)
- [../schemes/overview.md](../schemes/overview.md)
- [../../05-ui-ux/settings/loan/overview.md](../../05-ui-ux/settings/loan/overview.md)
- [../../AI_INDEX.md](../../AI_INDEX.md)
