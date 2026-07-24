# Fixed Deposit — Business Domain

## Purpose

Documents business rules, use cases, workflows, and acceptance tests for the **मुदत ठेव (Fixed Deposit)** operational module: opening term-deposit accounts, searching/maintaining FD accounts and their renewal history, recording installment payments on loans-against-deposits, and calculating FD interest/duration via the Interest Multiplier.

## Scope

Covers four current UI screens (superseded specs excluded per this generation request and [ux-optimization.md](../../05-ui-ux/fixed-deposit/ux-optimization.md)):

| Screen | Spec | Business focus |
| :--- | :--- | :--- |
| नवीन खाते (New Account) | [new-fd-account-screen.md](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md) | Open an FD account (4-tab wizard) for an existing Customer, with optional Nominee(s), Joint Holder(s), renewal, interest-transfer, and closing-routing setup |
| खाते व्यवस्थापन (Account Management) | [fd-account-management-screen.md](../../05-ui-ux/fixed-deposit/fd-account-management-screen.md) | Search FD accounts (Register) and view renewal events (Renewal List); export, view details, remove registration rows |
| ठेव कर्ज हप्ता पेमेंट (Deposit Loan Installment Payment) | [deposit-loan-installment-payment-screen.md](../../05-ui-ux/fixed-deposit/deposit-loan-installment-payment-screen.md) | Record installment payments on an existing loan-against-deposit (Interest tab captured; Tabs 2–6 TODO) |
| व्याज गुणक (Interest Multiplier) | [fd-interest-multiplier-screen.md](../../05-ui-ux/fixed-deposit/fd-interest-multiplier-screen.md) | Stateless calculator for FD interest rate or duration |

**Explicitly out of scope for this domain (superseded, per user instruction):**

| Superseded spec | Superseded by | Domain |
| :--- | :--- | :--- |
| `fd-transaction-screen.md` | [deposit-account-transaction-screen.md](../../05-ui-ux/accounting/deposit-account-transaction-screen.md) | Accounting (Phase 3) |
| `fd-manual-interest-calculation-screen.md` | [manual-interest-management-screen.md](../../05-ui-ux/accounting/manual-interest-management-screen.md) | Accounting (Phase 3) |
| `fd-account-register-screen.md` | [fd-account-management-screen.md](../../05-ui-ux/fixed-deposit/fd-account-management-screen.md) — Tab 1 | Fixed Deposit |
| `account-renewal-list-screen.md` | [fd-account-management-screen.md](../../05-ui-ux/fixed-deposit/fd-account-management-screen.md) — Tab 2 | Fixed Deposit |

FD deposit/withdrawal transactions and manual interest provisioning/assessment are documented under the unified Accounting domain when authored, not here.

## Responsibilities

- Open **FD** term-deposit accounts under a configured FD scheme, for an existing Customer, with optional Nominee/Joint Holder capture and renewal / interest-transfer / account-closing routing configuration
- Compute Maturity Amount and Return Date from the scheme interest formula at account opening ([BR-012](business-rules.md#br-012--maturity-amount-return-date-and-receipt-date-system-computed))
- Provide account search/list and renewal history with the platform interactive-reporting standard (BG-005)
- Record installment payments against existing loans-against-deposits (loan opening lives in the Loan module)
- Provide an FD interest-rate/duration calculator (no persistence)

## Features

| Feature | Use case | Primary screen |
| :--- | :--- | :--- |
| Open a new FD account (4-tab wizard) | [UC-001](use-cases.md#uc-001--open-a-new-fd-account) | New Account |
| Search FD accounts and view renewal history | [UC-002](use-cases.md#uc-002--search-and-maintain-fd-accounts-and-renewal-history) | Account Management |
| Record a deposit-loan installment payment | [UC-003](use-cases.md#uc-003--record-a-deposit-loan-installment-payment) | Deposit Loan Installment Payment |
| Calculate FD interest rate or duration | [UC-004](use-cases.md#uc-004--calculate-fd-interest-rate-or-duration) | Interest Multiplier |

## Dependencies

| Dependency | Domain / doc | Why |
| :--- | :--- | :--- |
| Customer must exist | [customer/business-rules.md](../customer/business-rules.md) BR-026 (same pattern) | Account Holder, Nominee, and Joint Holder lookups resolve against Customer ([BR-001](business-rules.md#br-001--customer-must-exist-before-fd-account-can-be-opened)) |
| Settings/Schemes — FD scheme configuration | [settings/schemes/business-rules.md](../settings/schemes/business-rules.md) BR-020, BR-022, BR-023, BR-024 | Scheme selection, Interest Type/Compounding, Interest Rate slab, Duration & Maturity Amount, and Auto Renewal fields flow into account opening ([BR-002](business-rules.md#br-002--scheme-required-and-loaded-from-fd-scheme-master), [BR-003](business-rules.md#br-003--scheme-derived-attributes-auto-filled-read-only), [BR-007](business-rules.md#br-007--interest-rate-slab-required-and-drives-duration), [BR-012](business-rules.md#br-012--maturity-amount-return-date-and-receipt-date-system-computed), [BR-026](business-rules.md#br-026--auto-renewal-and-renewal-mutually-exclusive-renewal-type-radios)) |
| Settings/Master permission model | [settings/master/business-rules.md](../settings/master/business-rules.md) BR-017 | All Rights / View Only / No Rights on all FD screens ([BR-030](business-rules.md#br-030--fd-screens-use-master-permission-levels)) |
| Membership canonical Relation list | [new-membership-screen.md](../../05-ui-ux/membership/new-membership-screen.md) Tab 3 (Phase 3 domain not yet documented) | Nominee Relation dropdown ([BR-021](business-rules.md#br-021--nominee-relation-reuses-canonical-membership-list)) |
| Quick Add Customer pattern | [quick-add-customer-pattern.md](../../05-ui-ux/shared/quick-add-customer-pattern.md) | Nominee lookup fallback ([BR-020](business-rules.md#br-020--nominee-lookup-resolves-to-existing-or-quick-added-customer)) |
| Agent master (Daily/Pigmy) | [new-agent-screen.md](../../05-ui-ux/daily/new-agent-screen.md) (Phase 3 domain not yet documented) | Agent / Sales Agent Autocomplete on New FD Account ([BR-004](business-rules.md#br-004--agent-and-sales-agent-optional-agent-scoped-to-agent-branch)) |
| Loan / Deposit-Loan domain (not yet documented — Phase 3) | `02-business-domains/loan/`, [new-deposit-loan-screen.md](../../05-ui-ux/loan/new-deposit-loan-screen.md) | Loan-linked (pink) legend and Deposit Loan Installment Payment ([BR-032](business-rules.md#br-032--register-grid-legend-loan-linked-and-matured-accounts), [BR-037](business-rules.md#br-037--deposit-loan-must-exist-before-installment-payment), [BR-039](business-rules.md#br-039--calculate-interest-populates-installment-grid-set-applies)) |
| Accounting / FD transaction & interest posting (not yet documented — Phase 3) | `02-business-domains/accounting/` | FD deposit/maturity/renewal execution and interest posting that generate Renewal List events ([BR-026](business-rules.md#br-026--auto-renewal-and-renewal-mutually-exclusive-renewal-type-radios), [BR-036](business-rules.md#br-036--renewal-list-is-read-and-export-only)) |
| Branch master | Shared | Branch / Agent Branch Autocomplete |

## Downstream Dependents

| Dependent | Domain / doc | Dependency |
| :--- | :--- | :--- |
| Accounting — Deposit Account Transaction | [deposit-account-transaction-screen.md](../../05-ui-ux/accounting/deposit-account-transaction-screen.md) | Posts deposits/withdrawals and maturity/renewal against FD accounts opened here |
| Accounting — Manual Interest Management | [manual-interest-management-screen.md](../../05-ui-ux/accounting/manual-interest-management-screen.md) | Applies interest provisioning/assessment to FD accounts (मॉड्यूल = मुदत ठेव) |
| Loan — New Deposit Loan | [new-deposit-loan-screen.md](../../05-ui-ux/loan/new-deposit-loan-screen.md) | Pledges FD accounts opened here as collateral; installment payments recorded via this domain's Deposit Loan Installment screen |

## Owned Entities

| Entity | Description | DB doc status |
| :--- | :--- | :---: |
| `fd_account` | Fixed-deposit account record (account no., customer, scheme, account type, FD amount, interest rate, duration, maturity amount, status, receipt series) | TODO — `@design-database-schema fixed-deposit` |
| `fd_account_nominee` | Zero or more nominees per FD account | TODO |
| `fd_account_joint_holder` | Zero or more joint holders per FD account | TODO |
| `fd_account_renewal` | Renewal events surfaced on the Renewal List (source flow TODO — see [BR-036](business-rules.md#br-036--renewal-list-is-read-and-export-only)) | TODO |

> Deposit-loan installment records are owned by the **Loan** domain, not Fixed Deposit; this domain only records payments against them.

## Open Decisions (TODO — confirm with business)

| # | Topic | Blocks |
| :---: | :--- | :--- |
| 1 | ~~Maturity Amount / Return Date derivation~~ — **Confirmed 2026-07-24:** system-computed from scheme interest formula; scheme grid Maturity Amount is a reference for double-money (दामदुप्पट / कॅश सर्टिफिकेट) schemes only | [BR-012](business-rules.md#br-012--maturity-amount-return-date-and-receipt-date-system-computed) |
| 2 | Multiple FD workflow semantics (Actual FD Amount + Multiplier + Add) — one vs. many accounts, series consumption | [BR-017](business-rules.md#br-017--multiple-fd-workflow-semantics-undefined), [BR-029](business-rules.md#br-029--new-fd-account-wizard-atomic-save-on-create) |
| 3 | Exact FD interest day-count/compounding formula | [BR-012](business-rules.md#br-012--maturity-amount-return-date-and-receipt-date-system-computed), [BR-043](business-rules.md#br-043--interest-multiplier-computes-interest-rate-or-duration) |
| 4 | "Admin role" definition for Interest Rate override and Advanced Settings visibility | [BR-010](business-rules.md#br-010--interest-rate-auto-filled-from-slab-admin-override-role-undefined), [BR-015](business-rules.md#br-015--advanced-settings-visibility-role-undefined) |
| 5 | Account No. and Receipt Number generation/auto-increment mechanism | [BR-005](business-rules.md#br-005--account-no-auto-generated), [BR-016](business-rules.md#br-016--receipt-prefix-and-receipt-number-required) |
| 6 | Account Operation Instructions persisted value when Joint Holder tab skipped | [BR-024](business-rules.md#br-024--account-operation-instructions-required-with-defined-values) |
| 7 | Renewal execution at maturity (auto batch vs. manual) and how Renewal List events are generated | [BR-026](business-rules.md#br-026--auto-renewal-and-renewal-mutually-exclusive-renewal-type-radios), [BR-036](business-rules.md#br-036--renewal-list-is-read-and-export-only) |
| 8 | Register branch-scoping of results for limited-branch actors | [BR-031](business-rules.md#br-031--account-management-search-fields-all-optional-organization-auto-filled) |
| 9 | Loan-linked (pink) highlight exact linkage (pending Loan domain) | [BR-032](business-rules.md#br-032--register-grid-legend-loan-linked-and-matured-accounts) |
| 10 | काढा (Remove) confirmation dialog and transaction-history restriction | [BR-034](business-rules.md#br-034--काढा-remove-deletes-the-account-registration-row) |
| 11 | Account Details / Account Statement — no dedicated screen/report spec | [BR-035](business-rules.md#br-035--account-statement-and-details-lack-dedicated-specs) |
| 12 | Deposit Loan Installment interest basis + what "Set" persists (pending Loan domain) | [BR-039](business-rules.md#br-039--calculate-interest-populates-installment-grid-set-applies) |
| 13 | Deposit Loan Installment Tabs 2–6 (uncaptured; candidate for removal) | [BR-040](business-rules.md#br-040--deposit-loan-installment-tabs-26-not-captured) |

## Related Documents

- [business-rules.md](business-rules.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [changelog.md](changelog.md)
- [../overview.md](../overview.md)
- [../../05-ui-ux/fixed-deposit/overview.md](../../05-ui-ux/fixed-deposit/overview.md)
- [../savings/overview.md](../savings/overview.md)
- [../customer/business-rules.md](../customer/business-rules.md)
- [../settings/schemes/business-rules.md](../settings/schemes/business-rules.md)
- [../settings/master/business-rules.md](../settings/master/business-rules.md)
- [../../00-project-overview/glossary.md](../../00-project-overview/glossary.md)
- [../../AI_INDEX.md](../../AI_INDEX.md)
