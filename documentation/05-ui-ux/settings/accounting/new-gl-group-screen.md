# Screen Spec — New GL Group (सेटिंग्ज > लेखा > नवीन जी.एल ग्रुप)

## Purpose

UI specification for creating a new GL (General Ledger) group. Intended for AI agents implementing this screen.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | नवीन जी.एल ग्रुप | New GL Group |
| Breadcrumb | डॅशबोर्ड > सेटिंग्ज > लेखा > नवीन जी.एल ग्रुप | Dashboard > Settings > Accounting > New GL Group |
| Parent Module | लेखा | Accounting |

## Reference Screenshots

| Screenshot File | Section |
| :--- | :--- |
| `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-लेखा-नवीन जी.एल ग्रुप.png` | Primary Group section |

---

## Section: प्राथमिक गट (Primary Group)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | नफा तोटा | Profit & Loss | Radio | No | Default selected. Mutually exclusive with ताळेबंद |
| 2 | ताळेबंद | Balance Sheet | Radio | No | — |
| 3 | उत्पन्न | Income | Radio | No | Default selected. Mutually exclusive with खर्च |
| 4 | खर्च | Expense | Radio | No | — |
| 5 | गट प्रकार निवडा | Select Group Type | Dropdown | Yes | Default: `इतर` (Other). |
| 6 | गटाचे नाव | Group Name | Textbox | Yes | — |
| 7 | गटाचे नाव (युनिकोड) | Group Name (Unicode) | Textbox | No | — |

## Actions
 - After selecting ताळेबंद (Balance Sheet) Radio button (Income & Expense Radio buttons are getting hidden ) & visible येणे (Receiviable) & देणे (Payable) Radio Buttons
| Button | Marathi | English |
| :--- | :--- | :--- |
| Save | पूर्ण | Complete |
| Reset | पूर्ववत | Revert |

---

## Mockup

| Property | Value |
| :--- | :--- |
| HTML mockup | [mockups/settings/accounting/new-gl-group-screen/index.html](../../mockups/settings/accounting/new-gl-group-screen/index.html) |
| Review guide | [mockups/settings/accounting/new-gl-group-screen/README.md](../../mockups/settings/accounting/new-gl-group-screen/README.md) |
| Stack | Tailwind CSS v4 (CDN), Marathi labels only |
| Status | Draft — pending bank user review |

---

## Related Documents

- [overview.md](overview.md)
- [new-gl-head-screen.md](new-gl-head-screen.md)
