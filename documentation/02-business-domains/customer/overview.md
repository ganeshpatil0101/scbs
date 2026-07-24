# Customer — Business Domain

## Purpose

Documents business rules, use cases, workflows, and acceptance tests for the **ग्राहक (Customer)** module: customer registration/KYC, customer search, and "other account" (non-product) account opening and bulk maintenance.

## Scope

Covers three current UI screens (superseded specs excluded per [ux-optimization.md](../../05-ui-ux/customer/ux-optimization.md)):

| Screen | Spec | Business focus |
| :--- | :--- | :--- |
| ग्राहक यादी (Customer List) | [customer-list-screen.md](../../05-ui-ux/customer/customer-list-screen.md) | Search, filter, view, export customers |
| नवीन ग्राहक (New Customer) | [new-customer-screen.md](../../05-ui-ux/customer/new-customer-screen.md) | Register customer identity, address(es), KYC documents |
| इतर खाते व्यवस्थापन (Other Account Management) | [other-account-management-screen.md](../../05-ui-ux/customer/other-account-management-screen.md) | Open Class B Dividend Payable / Deposit / Entrance Fee / Staff Salary Expense accounts for a customer; bulk status/remove |

**Out of scope for this domain:** Membership (share accounts, share transfer, dividend) — Phase 3 `membership/`; operational product accounts (Savings, FD, Daily, Recurring, Loan) which use Customer as Account Holder but are documented in their own domains.

## Responsibilities

- Register and maintain **Customer** identity records (KYC, address, contact) — the base identity referenced by Membership, Staff registration, and every product account holder lookup across the platform
- Provide customer search/list with the platform interactive-reporting standard (BG-005)
- Open and bulk-maintain non-product "other" accounts (dividend payable, deposit, entrance fee, staff salary expense) tied to a customer

## Features

| Feature | Use case | Primary screen |
| :--- | :--- | :--- |
| Register new customer (3-tab wizard) | UC-001 | New Customer |
| Search and view customer list | UC-002 | Customer List |
| Open an Other Account for an existing customer | UC-003 | Other Account Management — Tab 1 |
| Bulk maintain Other Account registrations | UC-004 | Other Account Management — Tab 2 |

## Dependencies

| Dependency | Domain / doc | Why |
| :--- | :--- | :--- |
| Google Maps Places API | External (not yet in [architecture-overview.md](../../01-architecture/architecture-overview.md)) | Tab 2 Address capture — no CBS geography master |
| Membership canonical Relation list | [new-membership-screen.md](../../05-ui-ux/membership/new-membership-screen.md) Tab 3 (Phase 3 domain not yet documented) | Nominee Relation dropdown ([BR-014](business-rules.md#br-014--nominee-relation-reuses-canonical-membership-list)) |
| Settings/Master permission model | [settings/master/business-rules.md](../settings/master/business-rules.md) BR-017 | All Rights / View Only / No Rights on all three screens ([BR-022](business-rules.md#br-022--customer-screens-use-master-permission-levels)) |
| Settings/Master branch rights | [settings/master/business-rules.md](../settings/master/business-rules.md) BR-013 | Possible branch scoping of Customer List results ([BR-024](business-rules.md#br-024--customer-list-branch-scoped-results-eligibility), TODO) |
| Settings/Accounting GL configuration | [settings/accounting/overview.md](../settings/accounting/overview.md) | Which GL Head each Other Account type posts to — not exposed on this screen, `TODO:` per [BR-027](business-rules.md#br-027--account-by-customer-type-required-with-defined-values) |
| Branch master | Shared | Autocomplete on all three screens |

## Downstream Dependents

Other domains depend on the Customer record documented here:

| Dependent | Domain / doc | Dependency |
| :--- | :--- | :--- |
| Staff & System Access | [settings/master/business-rules.md](../settings/master/business-rules.md) BR-001 | Employee/Director must link to an existing Customer |
| Quick Add Customer | [quick-add-customer-pattern.md](../../05-ui-ux/shared/quick-add-customer-pattern.md) | Creates a minimal Customer record (Salutation, Name, DOB, Mobile) reusing [BR-001](business-rules.md#br-001--customer-number-auto-generated) auto-numbering and session-branch default |
| Membership (Phase 3) | `02-business-domains/membership/` (not yet documented) | A Member is a Customer that additionally holds a share account — see [glossary.md](../../00-project-overview/glossary.md) Customer vs Member |
| Product account opening (Savings, FD, Daily, Recurring, Loan — Phase 3) | Respective domains | Account Holder lookup resolves against Customer |

## Owned Entities

| Entity | Description | DB doc status |
| :--- | :--- | :---: |
| `customer` | Identity/KYC record (customer no., type, name, DOB, status) | TODO — `@design-database-schema shared` |
| `customer_address` | One or more addresses per customer | TODO |
| `customer_kyc_document` | Uploaded KYC document metadata per customer | TODO |
| `customer_nominee` | At most one nominee per customer ([BR-012](business-rules.md#br-012--new-customer-supports-at-most-one-nominee)) | TODO |
| `other_account` | Non-product account registration (Customer + Account by Customer type + registration status) | TODO |

## Open Decisions (TODO — confirm with business)

| # | Topic | Blocks |
| :---: | :--- | :--- |
| 1 | ~~New Customer wizard partial save vs atomic save-on-final~~ — **Confirmed:** atomic on final Complete/Save | BR-021 / WF-001 |
| 2 | ~~KYC mandatory documents gate Save~~ — **Confirmed:** does not block Save; reminder only | BR-019 |
| 3 | Customer List branch-scoping of results | BR-024 |
| 4 | Whether non-Individual Customer Types relax person-specific required fields | BR-025 |
| 5 | Other Account Status filter omits `बंद` (Closed) — spec gap or intentional | BR-028 |
| 6 | Duplicate Other Account (same customer, same type) prevention | BR-029 |
| 7 | Which GL Head each Other Account type posts to | BR-027 (Notes) |

## Related Documents

- [business-rules.md](business-rules.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [changelog.md](changelog.md)
- [../overview.md](../overview.md)
- [../../05-ui-ux/customer/overview.md](../../05-ui-ux/customer/overview.md)
- [../settings/master/business-rules.md](../settings/master/business-rules.md)
- [../../00-project-overview/glossary.md](../../00-project-overview/glossary.md)
- [../../AI_INDEX.md](../../AI_INDEX.md)
