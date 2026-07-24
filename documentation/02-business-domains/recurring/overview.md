# Recurring — Business Domain

## Purpose

Documents business rules, use cases, workflows, and acceptance tests for the **रिकरिंग (Recurring Deposit / RD)** module: opening a new Recurring account (periodic installment deposit), searching/maintaining Recurring accounts via the Account Register, and previewing maturity via the Interest Multiplier calculator.

## Scope

Covers three current UI screens (superseded specs excluded per this generation request and [ux-optimization.md](../../05-ui-ux/recurring/ux-optimization.md)):

| Screen | Spec | Business focus |
| :--- | :--- | :--- |
| नवीन खाते (New Account) | [new-recurring-account-screen.md](../../05-ui-ux/recurring/new-recurring-account-screen.md) | Open a Recurring account for an existing Customer, with optional Nominee(s) and Joint Holder(s) |
| खाते रजिस्टर (Account Register) | [account-register-screen.md](../../05-ui-ux/recurring/account-register-screen.md) | Search, view, export, and remove Recurring accounts |
| व्याज गुणक (Interest Multiplier) | [interest-multiplier-screen.md](../../05-ui-ux/recurring/interest-multiplier-screen.md) | Preview RD maturity/interest for a scheme (no persistence) |

**Explicitly out of scope for this domain (superseded, per user instruction):**

| Superseded spec | Superseded by | Domain |
| :--- | :--- | :--- |
| recurring-transaction-screen.md / credit-transaction-screen.md | [deposit-account-transaction-screen.md](../../05-ui-ux/accounting/deposit-account-transaction-screen.md) | Accounting (Phase 3) |
| recurring-interest-management-screen.md / manual-interest-assessment-screen.md / manual-interest-provision-screen.md | [manual-interest-management-screen.md](../../05-ui-ux/accounting/manual-interest-management-screen.md) | Accounting (Phase 3) |

Recurring installment (credit) transactions, missed-installment penalty, and manual interest provisioning/assessment are documented under the unified Accounting domain when it is authored, not here.

## Responsibilities

- Open **Recurring** deposit accounts under a configured Recurring scheme, for an existing Customer, with optional Nominee and Joint Holder capture
- Compute Maturity Date and Maturity Amount from the scheme interest formula at account opening
- Provide account search/list with the platform interactive-reporting standard (BG-005), plus row removal
- Provide a stateless Interest Multiplier calculator for RD maturity previews

## Features

| Feature | Use case | Primary screen |
| :--- | :--- | :--- |
| Open a new Recurring account (3-tab wizard) | UC-001 | New Account |
| Search, view, export, and remove Recurring accounts | UC-002 | Account Register |
| Preview RD maturity/interest | UC-003 | Interest Multiplier |

## Dependencies

| Dependency | Domain / doc | Why |
| :--- | :--- | :--- |
| Customer must exist | [customer/business-rules.md](../customer/business-rules.md) BR-026 (same pattern) | Account Holder and Nominee/Joint Holder lookups resolve against Customer ([BR-001](business-rules.md#br-001--customer-must-exist-before-recurring-account-can-be-opened)) |
| Settings/Schemes — Recurring scheme configuration | [settings/schemes/business-rules.md](../settings/schemes/business-rules.md) | Scheme selection, duration/rate slab, interest type, compounding, and Maturity Amount formula ([BR-002](business-rules.md#br-002--scheme-required-and-loaded-from-recurring-scheme-master), [BR-003](business-rules.md#br-003--scheme-derived-attributes-auto-filled-read-only), [BR-007](business-rules.md#br-007--duration-selected-from-scheme-grid-duration-and-rate-auto-filled), [BR-013](business-rules.md#br-013--maturity-amount-system-computed-from-scheme-interest-formula)) |
| Daily/Pigmy — Agent master | [daily/business-rules.md](../daily/business-rules.md) BR-021 | Agent and Sales Agent Autocomplete on New Account ([BR-004](business-rules.md#br-004--agent-and-sales-agent-optional-agent-scoped-to-agent-branch)) |
| Settings/Master permission model | [settings/master/business-rules.md](../settings/master/business-rules.md) BR-017 | All Rights / View Only / No Rights on all three screens ([BR-025](business-rules.md#br-025--recurring-screens-use-master-permission-levels)) |
| Membership canonical Relation list | [new-membership-screen.md](../../05-ui-ux/membership/new-membership-screen.md) Tab 3 (Phase 3 domain not yet documented) | Nominee Relation dropdown ([BR-020](business-rules.md#br-020--nominee-relation-reuses-canonical-membership-list)) |
| Quick Add Customer pattern | [quick-add-customer-pattern.md](../../05-ui-ux/shared/quick-add-customer-pattern.md) | Nominee lookup fallback ([BR-019](business-rules.md#br-019--nominee-lookup-resolves-to-existing-or-quick-added-customer)) |
| Loan domain (not yet documented — Phase 3) | `02-business-domains/loan/` | Loan-linked (pink) row highlight on the Register ([BR-028](business-rules.md#br-028--results-grid-legend-loan-linked-and-matured-highlighting)) |
| Branch / Account Holder master | Shared | Autocomplete on Account Register |

## Downstream Dependents

| Dependent | Domain / doc | Dependency |
| :--- | :--- | :--- |
| Accounting — Deposit Account Transaction | [accounting/deposit-account-transaction-screen.md](../../05-ui-ux/accounting/deposit-account-transaction-screen.md) | Posts installment credits/withdrawals against Recurring accounts opened here |
| Accounting — Manual Interest Management | [accounting/manual-interest-management-screen.md](../../05-ui-ux/accounting/manual-interest-management-screen.md) | Applies interest provisioning/assessment to Recurring accounts opened here |
| Loan (Phase 3) | `02-business-domains/loan/` | May reference a Recurring account as collateral/lien source (कर्ज असलेली खाती) |

## Owned Entities

| Entity | Description | DB doc status |
| :--- | :--- | :---: |
| `recurring_account` | Recurring account record (account no., customer, scheme, account type, installment amount, deposit type/frequency, duration, rate, maturity date/amount, status) | TODO — `@design-database-schema recurring` |
| `recurring_account_nominee` | Zero or more nominees per Recurring account | TODO |
| `recurring_account_joint_holder` | Zero or more joint holders per Recurring account | TODO |

## Open Decisions (TODO — confirm with business)

| # | Topic | Blocks |
| :---: | :--- | :--- |
| 1 | ~~Maturity Amount derivation~~ — **Confirmed 2026-07-24:** system-computed from scheme interest formula (same as FD) | BR-013 |
| 2 | Deposit Type (installment frequency) full value set — left as master-data TODO 2026-07-24 | BR-012 |
| 3 | RD interest/day-count/compounding formula (shared with Interest Multiplier) | BR-013, BR-034 |
| 4 | "Admin role" definition for Interest Rate override and Advanced Settings visibility | BR-008, BR-015 |
| 5 | Account No. generation algorithm | BR-005 |
| 6 | Loan-linked (pink) row highlight exact semantics (pending Loan domain) | BR-028 |
| 7 | काढा (Remove) confirmation dialog and transaction-history restriction | BR-029 |
| 8 | Account Details and Account Statement — no dedicated screen/report spec | BR-031 |
| 9 | Account Register branch-scoping of results | BR-027 |
| 10 | Account Operation Instructions persisted value when Tab 3 is skipped | BR-023 |
| 11 | Whether multiple nominees' Percentage must total 100% | BR-021 (Notes) |

## Related Documents

- [business-rules.md](business-rules.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [changelog.md](changelog.md)
- [../overview.md](../overview.md)
- [../../05-ui-ux/recurring/overview.md](../../05-ui-ux/recurring/overview.md)
- [../savings/business-rules.md](../savings/business-rules.md)
- [../fixed-deposit/business-rules.md](../fixed-deposit/business-rules.md)
- [../daily/business-rules.md](../daily/business-rules.md)
- [../settings/schemes/business-rules.md](../settings/schemes/business-rules.md)
- [../settings/master/business-rules.md](../settings/master/business-rules.md)
- [../../00-project-overview/glossary.md](../../00-project-overview/glossary.md)
- [../../AI_INDEX.md](../../AI_INDEX.md)
