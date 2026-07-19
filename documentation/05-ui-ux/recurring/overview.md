# Recurring Screens Overview

## Purpose

Index of operational UI screens under **रिकरिंग (Recurring Deposit)**.

Branch, GL, and Account Holder lookups use a single **Autocomplete** field — see [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md).

**UX optimization (2026-07-12):** 6 → 5 screens per [ux-optimization.md](ux-optimization.md).

## Current Screens

| Screen (Marathi) | Screen (English) | Document |
| :--- | :--- | :--- |
| नवीन खाते | New Account | [new-recurring-account-screen.md](new-recurring-account-screen.md) |
| खाते रजिस्टर | Account Register | [account-register-screen.md](account-register-screen.md) |
| व्याज गुणक | Interest Multiplier | [interest-multiplier-screen.md](interest-multiplier-screen.md) |

## Superseded Screens

| Screen (Marathi) | Screen (English) | Superseded by |
| :--- | :--- | :--- |
| व्यवहार | Transaction | [../accounting/deposit-account-transaction-screen.md](../accounting/deposit-account-transaction-screen.md) |
| मॅन्युअल व्याज आकारणी / तरतूद | Manual Interest Assessment / Provision | [../accounting/manual-interest-management-screen.md](../accounting/manual-interest-management-screen.md) — **मॉड्यूल निवडा** = रिकरिंग |
| जमा व्यवहार | Credit Transaction | [recurring-transaction-screen.md](recurring-transaction-screen.md) → [deposit-account-transaction-screen.md](../accounting/deposit-account-transaction-screen.md) |
| मॅन्युअल व्याज > आकारणी | Manual Interest Assessment | [recurring-interest-management-screen.md](recurring-interest-management-screen.md) → [manual-interest-management-screen.md](../accounting/manual-interest-management-screen.md) |
| मॅन्युअल व्याज > तरतूद | Manual Interest Provision | [recurring-interest-management-screen.md](recurring-interest-management-screen.md) → [manual-interest-management-screen.md](../accounting/manual-interest-management-screen.md) |

## Screenshot Location

```text
screenshots/रिकरिंग/
```

## Mockups (Draft)

| Screen | Mockup |
| :--- | :--- |
| नवीन खाते | [mockups/recurring/new-recurring-account-screen/](../mockups/recurring/new-recurring-account-screen/) |
| खाते रजिस्टर | [mockups/recurring/account-register-screen/](../mockups/recurring/account-register-screen/) |
| व्याज गुणक | [mockups/recurring/interest-multiplier-screen/](../mockups/recurring/interest-multiplier-screen/) |

**Superseded mockup:** [recurring-interest-management-screen](../mockups/recurring/recurring-interest-management-screen/) → [manual-interest-management-screen](../mockups/accounting/manual-interest-management-screen/)

## Related Documents

- [changelog.md](changelog.md)
- [ux-optimization.md](ux-optimization.md)
- [../settings/schemes/new-scheme-screen.md](../settings/schemes/new-scheme-screen.md)
- [../../AI_INDEX.md](../../AI_INDEX.md)
