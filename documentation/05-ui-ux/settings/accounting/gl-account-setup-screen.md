# Screen Spec — GL Account Setup (सेटिंग्ज > लेखा > जी.एल. खाते सेटअप)

> **Consolidates:** [new-gl-group-screen.md](new-gl-group-screen.md) + [new-gl-head-screen.md](new-gl-head-screen.md)

## Purpose

Single wizard for creating a GL Group and its GL Head in one flow. Makes the parent-child relationship explicit for non-technical staff.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | जी.एल. खाते सेटअप | GL Account Setup |
| Breadcrumb | डॅशबोर्ड > सेटिंग्ज > लेखा > जी.एल. खाते सेटअप | Dashboard > Settings > Accounting > GL Account Setup |
| Parent Module | लेखा | Accounting |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | खाते गट | Account Group |
| 2 | जी.एल. हेड | GL Head |

---

## Tab 1: खाते गट (Account Group)

Former **New GL Group** fields.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | नफा तोटा | Profit & Loss | Radio | No | Default selected. Mutually exclusive with ताळेबंद |
| 2 | ताळेबंद | Balance Sheet | Radio | No | When selected: hides Income/Expense; shows येणे/देणे |
| 3 | उत्पन्न | Income | Radio | No | Default when P&L selected |
| 4 | खर्च | Expense | Radio | No | — |
| 5 | येणे | Receivable | Radio | No | Visible only when Balance Sheet selected |
| 6 | देणे | Payable | Radio | No | Visible only when Balance Sheet selected |
| 7 | गट प्रकार निवडा | Select Group Type | Dropdown | Yes | Default: `इतर` |
| 8 | गटाचे नाव | Group Name | Textbox | Yes | — |

### Section: प्रगत सेटिंग्ज (Advanced Settings) — collapsed by default

| # | Marathi Label | English Label | Type | Required | Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 9 | गटाचे नाव (युनिकोड) | Group Name (Unicode) | Textbox | No | Admin only |

---

## Tab 2: जी.एल. हेड (GL Head)

Former **New GL Head** fields (simplified default view).

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 10 | खाते गट | Account Group | Label | — | Read-only: populated from Tab 1 Group Name |
| 11 | खाते प्रकार | Account Type | Dropdown | Yes | Default: `इतर` |
| 12 | जी. एल. हेड क्र. | GL Head No. | Label | — | Auto-generated (e.g. `163`). Read-only |
| 13 | जी. एल. हेडचे नाव | GL Head Name | Textbox | Yes | — |
| 14 | स्थिती | Status | Dropdown | Yes | Default: `चालू`. Values: `चालू`, `बंद`, `स्थगित` |
| 15 | प्रारंभ दिनांक | Start Date | Date | Yes | System date |

### Balance Type (शिल्लक प्रकार)

| # | Marathi Label | English Label | Type | Required |
| :---: | :--- | :--- | :--- | :---: |
| 16 | जमा | Credit | Radio | No |
| 17 | नावे | Debit | Radio | No |

**Removed:** Balance Type `इतर` (Other) — ambiguous for staff.

### Account Category

| # | Marathi Label | English Label | Type | Required |
| :---: | :--- | :--- | :--- | :---: |
| 18 | सामान्य खाते | General Account | Radio | No |
| 19 | शाखा खाते | Branch Account | Radio | No |

| # | Marathi Label | English Label | Type | Required | Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 20 | संघटना | Organization | Dropdown | No | Visible when Branch Account selected |
| 21 | शाखा निवडा | Select Branch | Autocomplete | No | Visible when Branch Account selected |

### Section: प्रगत सेटिंग्ज (Advanced Settings) — collapsed by default

| # | Marathi Label | English Label | Type | Required | Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 22 | संक्षिप्त नाव | Short Name | Textbox | No | Report printing |
| 23 | युनिकोड नाव | Unicode Name | Textbox | No | — |
| 24 | सभासदाप्रमाणे खाते | Member-like Account | Radio | No | — |
| 25 | कॉन्ट्रा | Contra | Checkbox | No | — |

---

## Actions

| Button | Marathi | English |
| :--- | :--- | :--- |
| Save | पूर्ण | Complete |
| Reset | पूर्ववत | Revert |
| Next | पुढे | Next (Tab 1) |
| Back | मागे | Back (Tab 2) |

---

## Mockup

| Property | Value |
| :--- | :--- |
| HTML mockup | [mockups/settings/accounting/gl-account-setup-screen/index.html](../../mockups/settings/accounting/gl-account-setup-screen/index.html) |
| Review guide | [mockups/settings/accounting/gl-account-setup-screen/README.md](../../mockups/settings/accounting/gl-account-setup-screen/README.md) |
| Stack | Tailwind CSS v4 (CDN), Marathi labels only |
| Status | Draft — pending bank user review |

---

## Related Documents

- [overview.md](overview.md)
- [ux-optimization.md](../ux-optimization.md)
- [../../shared/ui-simplification-patterns.md](../../shared/ui-simplification-patterns.md)
- [../../shared/entity-autocomplete-pattern.md](../../shared/entity-autocomplete-pattern.md)
