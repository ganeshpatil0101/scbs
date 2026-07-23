# Settings — Schemes Sub-Area

## Purpose

Documents business rules and workflows for **योजना (Schemes)** settings: creating product configuration templates (Savings, Daily, FD, Recurring, Loan) that operational account-opening screens select from.

## Scope

Covers one UI screen (consolidated from five product-specific screens):

| Screen | Spec | Business focus |
| :--- | :--- | :--- |
| नवीन योजना (New Scheme) | [new-scheme-screen.md](../../05-ui-ux/settings/schemes/new-scheme-screen.md) | Unified wizard — Scheme Type selector drives tabs and fields |

**Field reference:** Type-specific field lists live in superseded product specs (retained for field reference only). Rules cite the unified screen as primary Source and note the field-reference file where needed.

**Out of scope for this sub-area:** Operational account opening, interest posting runs, loan disbursement, Settings/Loan interest-rate-change screen, GL chart setup.

## Responsibilities

- Bind each scheme to an existing **GL Head** via Autocomplete
- Capture scheme identity (name, status, product type) and product-specific parameters
- Configure duration/rate slabs, interest posting dates, account-closing slabs, charges
- Enforce tab visibility and required fields by Scheme Type
- Persist a complete scheme only on final Save (create wizard)

## Features

| Feature | Use case | Primary screen |
| :--- | :--- | :--- |
| Create deposit or loan scheme | UC-001 | New Scheme |
| Configure duration & rates by product | UC-001 | Tab Duration & Rates |
| Configure interest posting calendar | UC-001 | Tab Interest Posting |
| Configure account-closing penalties (deposit types) | UC-001 | Tab Account Closing |
| Configure loan guarantor / security / fees | UC-001 | Loan Specific + Charges |

## Dependencies

| Dependency | Domain / doc | Why |
| :--- | :--- | :--- |
| GL Head master | Settings/Accounting (UI done; business domain pending) | Scheme binds to one GL Head |
| Permission model | [settings/master/business-rules.md](../master/business-rules.md) BR-017 | All Rights / View Only / No Rights on New Scheme form |
| Member / Customer | Membership, Customer (later) | Allow Only Members; loan guarantor counts |
| Tenant setup | [tenant-setup.md](../../00-project-overview/tenant-setup.md) | Bootstrap product schemes (C2) |

## Owned Entities

| Entity | Description | DB doc status |
| :--- | :--- | :---: |
| `scheme` | Product template (type, name, status, GL, flags) | TODO — `@design-database-schema` |
| `scheme_duration_rate` | Duration/rate (and type-specific) slab rows | TODO |
| `scheme_interest_posting` | Interest posting day/month rows | TODO |
| `scheme_closing_slab` | Before-maturity / commission slab rows | TODO |
| `scheme_charge` | Selected charge types (and loan %/amount) | TODO |
| `scheme_loan_config` | Loan-specific guarantor, security, penalty params | TODO |

## Open Decisions (TODO — confirm with business)

| # | Topic | Blocks |
| :---: | :--- | :--- |
| 1 | Which Status values allow new account opening under the scheme | Operational open-account eligibility |
| 2 | Whether ≥1 Duration & Rates row and/or ≥1 Interest Posting row is required on Save | BR-022 / BR-011 notes |
| 3 | Exact Drawing Power (D.P.) formula and reduction schedule | Loan Tab Duration — glossary TODO |

## Related Documents

- [business-rules.md](business-rules.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [changelog.md](changelog.md)
- [../overview.md](../overview.md)
- [../../05-ui-ux/settings/schemes/overview.md](../../05-ui-ux/settings/schemes/overview.md)
- [../../00-project-overview/glossary.md](../../00-project-overview/glossary.md) — Scheme
- [../../AI_INDEX.md](../../AI_INDEX.md)
