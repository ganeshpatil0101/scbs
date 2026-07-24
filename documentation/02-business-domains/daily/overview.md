# Daily (Pigmy) — Business Domain

## Purpose

Documents business rules, use cases, workflows, and acceptance tests for the **डेली (Daily / Pigmy)** module: opening daily-collection deposit accounts, registering collection agents, recording and posting agent collections, reassigning accounts between agents, searching/maintaining accounts, and previewing interest via the Interest Multiplier calculator.

## Scope

Covers six current UI screens (superseded specs excluded per this generation request and [ux-optimization.md](../../05-ui-ux/daily/ux-optimization.md)):

| Screen | Spec | Business focus |
| :--- | :--- | :--- |
| नवीन खाते (New Account) | [new-daily-account-screen.md](../../05-ui-ux/daily/new-daily-account-screen.md) | Open a Daily account for an existing Customer under a Daily scheme + collecting Agent, with optional Nominee(s)/Joint Holder(s) |
| नवीन एजंट (New Agent) | [new-agent-screen.md](../../05-ui-ux/daily/new-agent-screen.md) | Register a collection agent (identity from an existing Customer) with commission slabs |
| खाते रजिस्टर (Account Register) | [account-register-screen.md](../../05-ui-ux/daily/account-register-screen.md) | Search, view, export, and remove Daily accounts |
| एजंट कलेक्शन व्यवस्थापन (Agent Collection Management) | [agent-collection-management-screen.md](../../05-ui-ux/daily/agent-collection-management-screen.md) | Capture and **post** daily collections (member credits + commission + GL transfer); review history |
| एजंट कडून एजंट कडे खाते ट्रान्सफर (Agent-to-Agent Transfer) | [agent-to-agent-transfer-screen.md](../../05-ui-ux/daily/agent-to-agent-transfer-screen.md) | Reassign accounts' collecting-agent binding between agents |
| व्याज गुणक (Interest Multiplier) | [interest-multiplier-screen.md](../../05-ui-ux/daily/interest-multiplier-screen.md) | Preview interest/maturity calculation (no posting) |

**Explicitly out of scope for this domain (superseded, per instruction):**

| Superseded spec | Superseded by | Domain |
| :--- | :--- | :--- |
| `daily-transaction-screen.md` | [deposit-account-transaction-screen.md](../../05-ui-ux/accounting/deposit-account-transaction-screen.md) | Accounting (Phase 3) |
| Manual Interest Assessment / Provision | [manual-interest-management-screen.md](../../05-ui-ux/accounting/manual-interest-management-screen.md) | Accounting (Phase 3) |
| `agent-collection-screen.md`, `agent-collection-list-screen.md` | [agent-collection-management-screen.md](../../05-ui-ux/daily/agent-collection-management-screen.md) (Tabs 1 + 4) | Daily (consolidated) |

Generic deposit-account transactions and manual interest provisioning/assessment are documented under the unified Accounting domain. Note: the **agent collection posting** documented here ([BR-037](business-rules-part2.md#br-037--agent-collection-is-the-posting-point-for-daily-collections)) is the Daily-specific collection flow retained in this domain, distinct from the superseded generic Daily Transaction screen.

## Responsibilities

- Open **Daily (pigmy)** deposit accounts under a Daily scheme, bound to a collecting Agent, for an existing Customer
- Register and configure collection Agents (identity + commission slabs)
- Capture and post daily agent collections (member-account credits, agent commission, and the balancing GL transfer voucher)
- Reassign accounts between agents; search/list accounts (interactive reporting per BG-005); preview interest

## Features

| Feature | Use case | Primary screen |
| :--- | :--- | :--- |
| Open a new Daily account (3-tab wizard) | UC-001 | New Account |
| Register a collection agent (2-tab wizard) | UC-002 | New Agent |
| Record and post an agent collection | UC-003 | Agent Collection Management |
| Reassign accounts between agents | UC-004 | Agent-to-Agent Transfer |
| Search, view, export, remove accounts | UC-005 | Account Register |
| Preview daily interest / maturity | UC-006 | Interest Multiplier |

## Dependencies

| Dependency | Domain / doc | Why |
| :--- | :--- | :--- |
| Customer must exist | [customer/business-rules.md](../customer/business-rules.md); [savings BR-001](../savings/business-rules.md#br-001--customer-must-exist-before-savings-account-can-be-opened) (same shape) | Account holder, nominee, joint holder, and agent identity resolve against Customer ([BR-001](business-rules.md#br-001--customer-must-exist-before-a-daily-account-can-be-opened), [BR-021](business-rules.md#br-021--agent-identity-requires-an-existing-customer)) |
| Agent must be registered first | This domain — New Agent | New Daily Account, Account Register, Collection, and Transfer all resolve a registered Agent ([BR-003](business-rules.md#br-003--agent-branch-and-agent-required-agent-must-be-registered-first)) |
| Settings/Schemes — Daily scheme configuration | [settings/schemes/business-rules.md](../settings/schemes/business-rules.md) | Scheme, duration/rate grid, interest type, and commission scheme flow into accounts, agents, collection, and multiplier ([BR-002](business-rules.md#br-002--scheme-required-and-loaded-from-daily-scheme-master), [BR-005](business-rules.md#br-005--duration-selected-from-scheme-grid-duration-and-rate-auto-filled), [BR-026](business-rules.md#br-026--agent-commission-config-per-scheme-and-amount-slab), [BR-043](business-rules-part2.md#br-043--interest-multiplier-scheme-required-duration-and-rate-auto-filled)) |
| Settings/Accounting — GL master | [settings/accounting/business-rules.md](../settings/accounting/business-rules.md) | Agent linked savings/deduction accounts and collection transfer posting lines resolve GL heads ([BR-023](business-rules.md#br-023--agent-linked-savings-account-branch-and-account-holder-required), [BR-039](business-rules-part2.md#br-039--transfer-tab-posting-lines-reconcile-to-collection-total)) |
| Settings/Master permission model | [settings/master/business-rules.md](../settings/master/business-rules.md) BR-017 | All Rights / View Only / No Rights on all Daily screens ([BR-045](business-rules-part2.md#br-045--daily-screens-use-master-permission-levels)) |
| Membership canonical Relation list | [new-membership-screen.md](../../05-ui-ux/membership/new-membership-screen.md) Tab 3 (Phase 3 domain not yet documented) | Nominee Relation dropdown ([BR-016](business-rules.md#br-016--nominee-relation-reuses-canonical-membership-list)) |
| Quick Add Customer pattern | [quick-add-customer-pattern.md](../../05-ui-ux/shared/quick-add-customer-pattern.md) | Nominee lookup fallback ([BR-015](business-rules.md#br-015--nominee-lookup-resolves-to-existing-or-quick-added-customer)) |
| Bank master | [bank-management-screen.md](../../05-ui-ux/bank/bank-management-screen.md) | Cheque instrument Select Bank on collection Brief Details ([BR-038](business-rules-part2.md#br-038--brief-details-instrument-fields-conditional-on-cheque)) |
| Accounting ledger/GL posting (Phase 3) | `02-business-domains/accounting/` | Collection posting produces ledger entries per Accounting rules ([BR-037](business-rules-part2.md#br-037--agent-collection-is-the-posting-point-for-daily-collections)) |
| Loan domain (Phase 3) | `02-business-domains/loan/` | Pigmy Account for Loan flag and loan-linked (pink) register highlight ([BR-010](business-rules.md#br-010--pigmy-account-for-loan-flag-depends-on-undocumented-loan-domain), [BR-031](business-rules-part2.md#br-031--results-grid-legend-loan-linked-and-matured-highlighting)) |
| Branch master | Shared | Autocomplete across account/agent/collection screens |

## Downstream Dependents

| Dependent | Domain / doc | Dependency |
| :--- | :--- | :--- |
| Accounting — ledger/GL | `02-business-domains/accounting/` (Phase 3) | Consumes the vouchers posted by agent collection ([BR-037](business-rules-part2.md#br-037--agent-collection-is-the-posting-point-for-daily-collections)) |
| Loan (Phase 3) | `02-business-domains/loan/` | May reference a pigmy account linked for loan recovery/collateral ([BR-010](business-rules.md#br-010--pigmy-account-for-loan-flag-depends-on-undocumented-loan-domain)) |

## Owned Entities

| Entity | Description | DB doc status |
| :--- | :--- | :---: |
| `daily_account` | Daily/pigmy account (account no., customer, scheme, agent binding, daily amount, commission rate, status) | TODO — `@design-database-schema daily` |
| `daily_account_nominee` | Zero or more nominees per Daily account | TODO |
| `daily_account_joint_holder` | Zero or more joint holders per Daily account | TODO |
| `daily_agent` | Collection agent (customer-linked identity, status, linked settlement/deduction accounts) | TODO |
| `daily_agent_commission` | Agent commission slab rows (scheme, %, amount range) | TODO |
| `daily_collection` | Collection batch (challan, agent, date, mode) and its posted lines | TODO |

## Open Decisions (TODO — confirm with business)

| # | Topic | Blocks |
| :---: | :--- | :--- |
| 1 | ~~Agent Collection posting semantics~~ — **Confirmed 2026-07-24:** Daily owns posting (member credits + commission + GL transfer voucher) | BR-037 |
| 2 | ~~Agent-to-Agent Transfer commit~~ — **Confirmed 2026-07-24:** reassigns (persists) accounts; block From = To | BR-041 |
| 3 | Commission Rate default source (per-account vs. agent commission config) | BR-006 |
| 4 | Maturity Amount auto-derivation on New Daily Account | BR-008 |
| 5 | Pigmy Account for Loan linkage semantics (pending Loan domain) | BR-010 |
| 6 | "Admin role" definition for Advanced Settings visibility | BR-011 |
| 7 | Closed/suspended agent excluded from Agent Autocomplete? | BR-022 |
| 8 | RD Penalty / RD Discount formulas | BR-036 |
| 9 | Cash-mode cashier hand-off + voucher/scroll numbering | BR-034, BR-037 |
| 10 | Transfer-line balancing enforcement on collection post | BR-039 |
| 11 | Agent-to-Agent same-branch restriction + confirmation dialog | BR-041 |
| 12 | Loan-linked (pink) register highlight source | BR-031 |
| 13 | काढा (Remove) confirmation + transaction-history restriction | BR-032 |
| 14 | Account Details / Account Statement — no dedicated spec | BR-033 |
| 15 | Account Register branch-scoping of results | BR-029 |

## Related Documents

- [business-rules.md](business-rules.md) — BR-001…BR-027
- [business-rules-part2.md](business-rules-part2.md) — BR-028…BR-045
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [changelog.md](changelog.md)
- [../overview.md](../overview.md)
- [../../05-ui-ux/daily/overview.md](../../05-ui-ux/daily/overview.md)
- [../savings/business-rules.md](../savings/business-rules.md)
- [../settings/schemes/business-rules.md](../settings/schemes/business-rules.md)
- [../settings/master/business-rules.md](../settings/master/business-rules.md)
- [../../00-project-overview/glossary.md](../../00-project-overview/glossary.md)
- [../../AI_INDEX.md](../../AI_INDEX.md)
