# Settings — Accounting Sub-Area

## Purpose

Documents business rules and workflows for **लेखा (Accounting)** settings: creating the chart of accounts via a unified GL Account Setup wizard (GL Group + GL Head).

## Scope

Covers one UI screen (consolidated from New GL Group + New GL Head):

| Screen | Spec | Business focus |
| :--- | :--- | :--- |
| जी.एल. खाते सेटअप (GL Account Setup) | [gl-account-setup-screen.md](../../05-ui-ux/settings/accounting/gl-account-setup-screen.md) | Create new GL Group and its GL Head in one atomic flow |

**Out of scope for this sub-area:** Operational Jama/Nave/Transfer posting, opening balances, year-end close, product schemes (Settings/Schemes), report layouts.

## Responsibilities

- Classify each new GL Group as Profit & Loss or Balance Sheet (with Income/Expense or Receivable/Payable)
- Create a new GL Head under that group with name, status, start date, balance type, and account category
- Assign Organization + Branch when the head is a Branch Account
- Auto-generate GL Head number (read-only for staff)
- Enforce naming uniqueness within the tenant

## Features

| Feature | Use case | Primary screen |
| :--- | :--- | :--- |
| Create GL Group + GL Head | UC-001 | GL Account Setup |
| Configure P&L vs Balance Sheet group classification | UC-001 Tab 1 | GL Account Setup |
| Configure Branch Account with org/branch | UC-001 Tab 2 | GL Account Setup |

## Dependencies

| Dependency | Domain / doc | Why |
| :--- | :--- | :--- |
| Organization / Branch masters | Shared (seed in tenant setup) | Branch Account requires Organization + Branch |
| Permission model | [settings/master/business-rules.md](../master/business-rules.md) BR-017 | All Rights / View Only / No Rights |
| Product schemes | [settings/schemes/](../schemes/overview.md) | Schemes bind to GL Heads (downstream) |
| Tenant setup | [tenant-setup.md](../../00-project-overview/tenant-setup.md) | Phase C1 chart of accounts |

## Owned Entities

| Entity | Description | DB doc status |
| :--- | :--- | :---: |
| `gl_group` | Chart group (P&L/BS classification, name) | TODO — `@design-database-schema` |
| `gl_head` | GL account head (number, name, status, balance type, category) | TODO |

## Open Decisions (TODO — confirm with business)

| # | Topic | Blocks |
| :---: | :--- | :--- |
| 1 | GL Head number generation algorithm (sequence range, gaps, reuse) | BR-010 notes |
| 2 | Whether Balance Type (Credit/Debit) must be selected on Save | Spec marks radios Required: No |
| 3 | Which Status values allow the GL Head in operational posting / scheme binding | Downstream eligibility |

## Related Documents

- [business-rules.md](business-rules.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [changelog.md](changelog.md)
- [../overview.md](../overview.md)
- [../../05-ui-ux/settings/accounting/overview.md](../../05-ui-ux/settings/accounting/overview.md)
- [../../00-project-overview/glossary.md](../../00-project-overview/glossary.md) — GL Group, GL Head
- [../../AI_INDEX.md](../../AI_INDEX.md)
