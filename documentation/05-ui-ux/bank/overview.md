# Bank Screens Overview

## Purpose

Index of operational UI screens under **बँक (Bank)** — society bank accounts and cheque processing.

**UX optimized (2026-07-07):** 3 menu screens → 1 consolidated screen with 2 tabs. Audit: [ux-optimization.md](ux-optimization.md).

Branch and GL lookups follow [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md).

## Current Screens

| Screen (Marathi) | Screen (English) | Document |
| :--- | :--- | :--- |
| बँक व्यवस्थापन | Bank Management | [bank-management-screen.md](bank-management-screen.md) |

### Tabs (Bank Management)

| Tab (Marathi) | Tab (English) | Functionality |
| :--- | :--- | :--- |
| बँक खाते | Bank Accounts | List + Create + Update on one page |
| चेक रजिस्टर | Cheque Register | List + Update (clearance / return) on one page |

## Superseded Screens

| Superseded spec | Consolidated into |
| :--- | :--- |
| [bank-register-screen.md](bank-register-screen.md) | [bank-management-screen.md](bank-management-screen.md) — Tab 1 |
| [new-bank-screen.md](new-bank-screen.md) | [bank-management-screen.md](bank-management-screen.md) — Tab 1 |
| [check-register-screen.md](check-register-screen.md) | [bank-management-screen.md](bank-management-screen.md) — Tab 2 |

## Screenshot Location

```text
screenshots/Bank/
```

## Related Documents

- [ux-optimization.md](ux-optimization.md)
- [changelog.md](changelog.md)
- [../investment/overview.md](../investment/overview.md) — Investment bank deposit screens (separate module)
- [../../AI_INDEX.md](../../AI_INDEX.md)
