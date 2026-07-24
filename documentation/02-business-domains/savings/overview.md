# Savings — Business Domain

## Purpose

Documents business rules, use cases, workflows, and acceptance tests for the **बचत (Savings)** module: opening a new Savings deposit account and searching/maintaining Savings accounts via the Account Register (including account closure).

## Scope

Covers two current UI screens (superseded specs excluded per this generation request and [ux-optimization.md](../../05-ui-ux/savings/ux-optimization.md)):

| Screen | Spec | Business focus |
| :--- | :--- | :--- |
| नवीन खाते (New Account) | [new-savings-account-screen.md](../../05-ui-ux/savings/new-savings-account-screen.md) | Open a Savings account for an existing Customer, with optional Nominee(s) and Joint Holder(s) |
| खाते रजिस्टर (Account Register) | [account-register-screen.md](../../05-ui-ux/savings/account-register-screen.md) | Search, view, export, remove, and close Savings accounts |

**Explicitly out of scope for this domain (superseded, per user instruction):**

| Superseded spec | Superseded by | Domain |
| :--- | :--- | :--- |
| [savings-transaction-screen.md](../../05-ui-ux/savings/savings-transaction-screen.md) | [deposit-account-transaction-screen.md](../../05-ui-ux/accounting/deposit-account-transaction-screen.md) | Accounting (Phase 3) |
| [manual-interest-calculation-screen.md](../../05-ui-ux/savings/manual-interest-calculation-screen.md) | [manual-interest-management-screen.md](../../05-ui-ux/accounting/manual-interest-management-screen.md) | Accounting (Phase 3) |

Savings deposit/withdrawal transactions and manual interest provisioning/assessment are documented under the unified Accounting domain when it is authored, not here.

## Responsibilities

- Open **Savings** deposit accounts under a configured Savings scheme, for an existing Customer, with optional Nominee and Joint Holder capture
- Provide account search/list with the platform interactive-reporting standard (BG-005)
- Remove erroneous account registrations and close accounts that meet zero-balance and no-other-active-relationship conditions

## Features

| Feature | Use case | Primary screen |
| :--- | :--- | :--- |
| Open a new Savings account (3-tab wizard) | UC-001 | New Account |
| Search, view, export, remove, and close Savings accounts | UC-002 | Account Register |

## Dependencies

| Dependency | Domain / doc | Why |
| :--- | :--- | :--- |
| Customer must exist | [customer/business-rules.md](../customer/business-rules.md) BR-026 (same pattern) | Account Holder and Nominee/Joint Holder lookups resolve against Customer ([BR-001](business-rules.md#br-001--customer-must-exist-before-savings-account-can-be-opened)) |
| Settings/Schemes — Savings scheme configuration | [settings/schemes/business-rules.md](../settings/schemes/business-rules.md) | Scheme selection, Interest Rate, and Allow Only Members flag flow into account opening ([BR-002](business-rules.md#br-002--scheme-required-and-loaded-from-savings-scheme-master), [BR-003](business-rules.md#br-003--member-only-scheme-enforcement-not-verifiable-on-this-screen), [BR-005](business-rules.md#br-005--interest-rate-auto-filled-from-scheme-admin-override-role-undefined)) |
| Settings/Master permission model | [settings/master/business-rules.md](../settings/master/business-rules.md) BR-017 | All Rights / View Only / No Rights on both screens ([BR-020](business-rules.md#br-020--savings-screens-use-master-permission-levels)) |
| Membership canonical Relation list | [new-membership-screen.md](../../05-ui-ux/membership/new-membership-screen.md) Tab 3 (Phase 3 domain not yet documented) | Nominee Relation dropdown ([BR-015](business-rules.md#br-015--nominee-relation-reuses-canonical-membership-list)) |
| Quick Add Customer pattern | [quick-add-customer-pattern.md](../../05-ui-ux/shared/quick-add-customer-pattern.md) | Nominee lookup fallback ([BR-014](business-rules.md#br-014--nominee-lookup-resolves-to-existing-or-quick-added-customer)) |
| Loan domain (not yet documented — Phase 3) | `02-business-domains/loan/` | Loan-linked accounts filter and Close Account's "no active Loan" condition ([BR-022](business-rules.md#br-022--loan-linked-accounts-filter-depends-on-undocumented-loan-domain), [BR-025](business-rules.md#br-025--close-account-requires-zero-balance-and-no-other-active-bank-relationships)) |
| Daily, Recurring, Fixed Deposit domains (not yet documented — Phase 3) | Respective domains | Close Account's "no other active relationship" condition ([BR-025](business-rules.md#br-025--close-account-requires-zero-balance-and-no-other-active-bank-relationships)) |
| Branch master | Shared | Autocomplete on Account Register |

## Downstream Dependents

| Dependent | Domain / doc | Dependency |
| :--- | :--- | :--- |
| Accounting — Deposit Account Transaction | [accounting/deposit-account-transaction-screen.md](../../05-ui-ux/accounting/deposit-account-transaction-screen.md) | Posts deposits/withdrawals against Savings accounts opened here |
| Accounting — Manual Interest Management | [accounting/manual-interest-management-screen.md](../../05-ui-ux/accounting/manual-interest-management-screen.md) | Applies interest provisioning/assessment to Savings accounts opened here |
| Loan (Phase 3) | `02-business-domains/loan/` | May reference a Savings account as collateral/lien source (कर्ज संलग्नीत खाते) |

## Owned Entities

| Entity | Description | DB doc status |
| :--- | :--- | :---: |
| `savings_account` | Savings account record (account no., customer, scheme, balance, status, interest rate) | TODO — `@design-database-schema savings` |
| `savings_account_nominee` | Zero or more nominees per Savings account | TODO |
| `savings_account_joint_holder` | Zero or more joint holders per Savings account | TODO |

## Open Decisions (TODO — confirm with business)

| # | Topic | Blocks |
| :---: | :--- | :--- |
| 1 | ~~Close Account precondition~~ — **Confirmed 2026-07-24:** balance = 0 AND no other active bank relationships (Loan/Daily/Recurring/FD) | BR-025 |
| 2 | ~~वगळा vs. काढा semantics~~ — **Confirmed 2026-07-24:** same action (Remove) | BR-024 |
| 3 | Member-only scheme enforcement mechanism on New Savings Account | BR-003 |
| 4 | "Admin role" definition for Interest Rate override and Advanced Settings visibility | BR-005, BR-009 |
| 5 | Loan-linked accounts filter exact semantics (pending Loan domain) | BR-022 |
| 6 | Remove (वगळा/काढा) confirmation dialog and transaction-history restriction | BR-024 |
| 7 | Account Details and Account Statement — no dedicated screen/report spec | BR-026 |
| 8 | Account Register branch-scoping of results | BR-021 |
| 9 | Whether multiple nominees' Percentage must total 100% | BR-016 (Notes) |

## Related Documents

- [business-rules.md](business-rules.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [changelog.md](changelog.md)
- [../overview.md](../overview.md)
- [../../05-ui-ux/savings/overview.md](../../05-ui-ux/savings/overview.md)
- [../customer/business-rules.md](../customer/business-rules.md)
- [../settings/schemes/business-rules.md](../settings/schemes/business-rules.md)
- [../settings/master/business-rules.md](../settings/master/business-rules.md)
- [../../00-project-overview/glossary.md](../../00-project-overview/glossary.md)
- [../../AI_INDEX.md](../../AI_INDEX.md)
