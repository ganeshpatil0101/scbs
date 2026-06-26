# Settings — Scheme Screens Overview

## Purpose

Index of UI screen specifications for **नवीन योजना (New Scheme)** creation under **सेटिंग्ज (Settings)**. Each linked document is self-contained for AI agents generating frontend screens.

## Scope

Covers four deposit-product scheme types accessible from the top navigation:

| Module (Marathi) | Module (English) | Screen Document |
| :--- | :--- | :--- |
| डेली | Daily | [daily-new-scheme-screen.md](daily-new-scheme-screen.md) |
| बचत | Savings | [savings-new-scheme-screen.md](savings-new-scheme-screen.md) |
| मुदत ठेव | Fixed Deposit | [fixed-deposit-new-scheme-screen.md](fixed-deposit-new-scheme-screen.md) |
| रिकरिंग | Recurring | [recurring-new-scheme-screen.md](recurring-new-scheme-screen.md) |
| कर्ज | Loan | [loan-new-scheme-screen.md](loan-new-scheme-screen.md) |

## Common Navigation Pattern

All four screens share:

- **Breadcrumb root:** `डॅशबोर्ड > सेटिंग्ज > <Product> > नवीन योजना`
- **English breadcrumb:** `Dashboard > Settings > <Product> > New Scheme`
- **Required-field legend:** `(*) आवश्यक फील्ड दर्शविते` — fields marked `*` are mandatory
- **Tabbed wizard layout** with `मागे (Back)` / `पुढे (Next)` navigation on most tabs
- **Charges tab** shares the same dropdown values across all four products (see each screen doc)

## Screenshot Location

All reference screenshots live under:

```text
screenshots/settings/
```

Filename pattern: `डॅशबोर्ड-सेटिंग्ज-<Product>-नवीन योजना-<TabOrSection>.png`

## Dependencies

- Top navigation modules: सेटिंग्ज, बचत, मुदत ठेव, डेली, रिकरिंग (visible in screenshots)
- GL Head master data (जीएल हेड क्र.) — source not shown in screenshots

## Related Documents

- [../overview.md](../overview.md)
- [../../AI_INDEX.md](../../AI_INDEX.md)
- [changelog.md](changelog.md)
