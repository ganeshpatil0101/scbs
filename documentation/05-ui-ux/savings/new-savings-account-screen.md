# Screen Spec — New Savings Account (बचत > नवीन खाते)

## Purpose

UI specification for opening a new savings account. Four-tab wizard.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | नवीन खाते | New Account |
| Breadcrumb | डॅशबोर्ड > बचत > नवीन खाते | Dashboard > Savings > New Account |
| Parent Module | बचत | Savings |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | खात्याची माहिती | Account Information |
| 2 | वारसदार | Nominee |
| 3 | परिचयकर्ता / संयुक्त खाते धारक | Introducer / Joint Holder |
| 4 | मंजूरी | Approval |

## Reference Screenshots

| File | Tab |
| :--- | :--- |
| `screenshots/bachat/डॅशबोर्ड-बचत-नवीन खाते.png` | Tab 1 — Account Information |

---

## Tab 1: खात्याची माहिती (Account Information)

### Section: ग्राहक माहिती (Customer Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | ग्राहक क्र. | Customer No. | Textbox | Yes | e.g. `1` |
| 2 | ग्राहक नाव | Customer Name | Textbox | No | Read-only after lookup |
| 3 | सभासद क्रमांक | Member Number | Textbox | No | Read-only |
| 4 | वय (वर्षे) | Age (Years) | Textbox | No | Read-only |
| 5 | ग्राहक शाखा नाव | Customer Branch Name | Textbox | No | Read-only |
| 6 | सभासद प्रकार | Member Type | Textbox | No | e.g. `सभासद` |
| 7 | विशेष सूचना | Special Instructions | Textbox | No | — |

### Section: खात्याची माहिती (Account Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 8 | योजना निवडा | Select Scheme | Dropdown | Yes | Default: `योजना निवडा`. Values: `TODO` |
| 9 | एजंट शाखा क्र. | Agent Branch No. | Textbox | No | e.g. `1` |
| 10 | एजंट शाखा निवडा | Select Agent Branch | Dropdown | No | e.g. कोतोली मुख्य कार्यालय |
| 11 | एजंट क्रमांक | Agent Number | Textbox | No | — |
| 12 | एजंट नाव शोध | Search Agent Name | Textbox | No | — |
| 13 | खाते क्र. | Account No. | Textbox | No | Auto-generated (e.g. `113`) |
| 14 | विक्री एजंट शाखा क्र. | Sales Agent Branch No. | Textbox | No | e.g. `1` |
| 15 | विक्री एजंट शाखा निवडा | Select Sales Agent Branch | Dropdown | No | e.g. कोतोली मुख्य कार्यालय |
| 16 | विक्री एजंट क्रमांक | Sales Agent Number | Textbox | No | — |
| 17 | विक्री एजंटचे नाव शोधा | Search Sales Agent Name | Textbox | No | — |

### Section: खाते तपशील (Account Details)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 18 | व्याज दर (% पी ए) | Interest Rate (% p.a.) | Textbox | Yes | e.g. `4.00` |
| 19 | चालू दिनांक | Current Date | Date | Yes | System date |
| 20 | विशेष सूचना | Special Instructions | Textbox | No | — |
| 21 | नावे मर्यादा | Debit Limit | Textbox | No | — |
| 22 | किमान शिल्लक | Minimum Balance | Textbox | Yes | e.g. `0.00` |
| 23 | स्थिती निवडा | Select Status | Dropdown | No | Default: `चालू` (Active). Other values: `TODO` |
| 24 | खाते श्रेणी निवडा | Select Account Category | Dropdown | No | Default: `नियमित` (Regular). Other values: `TODO` |
| 25 | निधी हस्तांतरण मर्यादा | Fund Transfer Limit | Textbox | No | e.g. `0` |
| 26 | आयएफएससी कोड | IFSC Code | Textbox | No | — |
| 27 | बँक नाव | Bank Name | Textbox | No | — |
| 28 | बँक बचत खाते नं | Bank Savings Account No. | Textbox | No | — |

Tabs 2–4: `TODO` — no screenshots captured.

---

## Related Documents

- [overview.md](overview.md)
- [../settings/schemes/savings-new-scheme-screen.md](../settings/schemes/savings-new-scheme-screen.md)
- [../customer/new-customer-screen.md](../customer/new-customer-screen.md)
