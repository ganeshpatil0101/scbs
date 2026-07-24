# Fixed Deposit Screens Overview

## Purpose

Index of operational UI screens under **मुदत ठेव (Fixed Deposit)**.

Branch, GL, Account Holder, Customer, and Agent lookups use a single **Autocomplete** field — see [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md).

## Current Screens

| Screen (Marathi) | Screen (English) | Document |
| :--- | :--- | :--- |
| नवीन खाते | New Account | [new-fd-account-screen.md](new-fd-account-screen.md) |
| खाते व्यवस्थापन | Account Management | [fd-account-management-screen.md](fd-account-management-screen.md) |
| ठेव कर्ज हप्ता पेमेंट | Deposit Loan Installment Payment | [deposit-loan-installment-payment-screen.md](deposit-loan-installment-payment-screen.md) |
| व्याज गुणक | Interest Multiplier | [fd-interest-multiplier-screen.md](fd-interest-multiplier-screen.md) |

## Superseded Screens

| Screen (Marathi) | Superseded by |
| :--- | :--- |
| व्यवहार | [../accounting/deposit-account-transaction-screen.md](../accounting/deposit-account-transaction-screen.md) |
| मॅन्युअल व्याज आकारणी / तरतूद | [../accounting/manual-interest-management-screen.md](../accounting/manual-interest-management-screen.md) — **मॉड्यूल निवडा** = मुदत ठेव |
| खाते रजिस्टर | [fd-account-management-screen.md](fd-account-management-screen.md) — Tab 1 |
| खाते नूतनीकरण यादी | [fd-account-management-screen.md](fd-account-management-screen.md) — Tab 2 |

## UX Optimization

**UX optimized (2026-07-11):** 7 screens → 6. Audit: [ux-optimization.md](ux-optimization.md)

## Mockups

| Screen | Mockup |
| :--- | :--- |
| नवीन खाते | [new-fd-account-screen](../mockups/fixed-deposit/new-fd-account-screen/) — Draft |
| खाते व्यवस्थापन | [fd-account-management-screen](../mockups/fixed-deposit/fd-account-management-screen/) — Draft |
| ठेव कर्ज हप्ता पेमेंट | [deposit-loan-installment-payment-screen](../mockups/fixed-deposit/deposit-loan-installment-payment-screen/) — Draft |
| व्याज गुणक | [fd-interest-multiplier-screen](../mockups/fixed-deposit/fd-interest-multiplier-screen/) — Draft |

**Superseded mockup:** [fd-manual-interest-calculation-screen](../mockups/fixed-deposit/fd-manual-interest-calculation-screen/) → [manual-interest-management-screen](../mockups/accounting/manual-interest-management-screen/)

## Screenshot Location

```text
screenshots/मुदत ठेव/
```

## Related Documents

- [ux-optimization.md](ux-optimization.md)
- [changelog.md](changelog.md)
- [../settings/schemes/new-scheme-screen.md](../settings/schemes/new-scheme-screen.md)
- [../loan/new-deposit-loan-screen.md](../loan/new-deposit-loan-screen.md)
- [../../02-business-domains/fixed-deposit/overview.md](../../02-business-domains/fixed-deposit/overview.md) — Business rules, use cases, workflows, acceptance tests
- [../../AI_INDEX.md](../../AI_INDEX.md)
