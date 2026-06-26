# Screen Spec — New Agent (डेली > एजंट > नवीन एजंट)

## Purpose

UI specification for registering a new daily-collection agent. Two-tab wizard.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | नवीन एजंट | New Agent |
| Breadcrumb | डॅशबोर्ड > डेली > एजंट > नवीन एजंट | Dashboard > Daily > Agent > New Agent |
| Parent Module | डेली | Daily |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | निधी माहिती | Fund / General Information |
| 2 | प्रतिनिधी माहिती | Representative / Commission Information |

## Reference Screenshots / Media

| File | Tab |
| :--- | :--- |
| `screenshots/डेली/डॅशबोर्ड_डेली_एजंट_नवीन एजंट.mp4` | All tabs (from video) |
| `screenshots/डेली/new-agent-frames/frame_0000.jpg` | Tab 1 |
| `screenshots/डेली/new-agent-frames/frame_0040.jpg` | Tab 2 |

---

## Tab 1: निधी माहिती (General Information)

### Agent Details

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | ग्राहक क्र. | Customer No. | Textbox | Yes | — |
| 2 | ग्राहक नाव | Customer Name | Textbox | No | — |
| 3 | स्थिती | Status | Dropdown | Yes | e.g. `चालू`. Other values: `TODO` |
| 4 | मेघदूत एजंट कोड | Meghdoot Agent Code | Textbox | No | — |
| 5 | मोबाईल क्रमांक | Mobile Number | Textbox | No | — |
| 6 | रुजू दिनांक | Joining Date | Date | Yes | System date |

### बचत खाते (Savings Account)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 7 | शाखा कोड | Branch Code | Textbox | Yes | e.g. `1` |
| 8 | शाखा निवडा | Select Branch | Dropdown | Yes | e.g. कोतोली मुख्य कार्यालय |
| 9 | जी एल क्रमांक | GL Number | Textbox | No | — |
| 10 | खाते निवडा | Select Account | Dropdown | Yes | Values: `TODO` |
| 11 | खाते क्रमांक | Account Number | Textbox | Yes | — |
| 12 | खातेधारक निवडा | Select Account Holder | Dropdown | Yes | Values: `TODO` |

### सुरक्षा ठेव (Security Deposit)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 13 | सुरक्षा ठेव | Security Deposit | Checkbox | No | Enables fields 14–21 |
| 14 | शाखा कोड | Branch Code | Textbox | Yes* | e.g. `1` |
| 15 | शाखा निवडा | Select Branch | Dropdown | Yes* | — |
| 16 | जी एल क्रमांक | GL Number | Textbox | No | — |
| 17 | खाते निवडा | Select Account | Dropdown | No | Values: `TODO` |
| 18 | खाते क्रमांक | Account Number | Textbox | No | — |
| 19 | खातेधारक निवडा | Select Account Holder | Dropdown | No | Values: `TODO` |
| 20 | मर्यादा | Limit | Textbox | No | — |
| 21 | कपात (%) | Deduction (%) | Textbox | No | — |

### मशीन कपात (Machine Deduction)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 22 | मशीन कपात | Machine Deduction | Checkbox | No | Enables fields below |
| 23 | जी एल क्रमांक | GL Number | Textbox | No | — |
| 24 | खाते निवडा | Select Account | Dropdown | No | Values: `TODO` |
| 25 | खाते क्रमांक | Account Number | Textbox | No | — |
| 26 | खातेधारक निवडा | Select Account Holder | Dropdown | No | Values: `TODO` |
| 27 | मर्यादा | Limit | Textbox | No | — |
| 28 | कपात | Deduction | Textbox | No | — |
| 29 | रु. / टक्के | Rs. / Percentage | Radio | No | — |

### टीडीएस (TDS)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 30 | होय / नाही | Yes / No | Radio | No | TDS applicable |
| 31 | कारण निवडा | Select Reason | Dropdown | No | e.g. `सभासद`. Other values: `TODO` |

### भविष्य निर्वाह निधी (Provident Fund)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 32 | भविष्य निर्वाह निधी | Provident Fund | Checkbox | No | Enables PF fields |
| 33 | जी एल क्रमांक | GL Number | Textbox | No | — |
| 34 | खाते निवडा | Select Account | Dropdown | No | Values: `TODO` |
| 35 | खाते क्रमांक | Account Number | Textbox | No | — |
| 36 | खातेधारक निवडा | Select Account Holder | Dropdown | No | Values: `TODO` |
| 37 | कपात (%) | Deduction (%) | Textbox | No | — |

**Action:** `पुढे` (Next).

---

## Tab 2: प्रतिनिधी माहिती (Commission Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | योजना निवडा | Select Scheme | Dropdown | Yes | Values: `TODO` |
| 2 | कमिशन (%) | Commission (%) | Textbox | Yes | — |
| 3 | कमिशन (कर्ज खाते) (%) | Commission (Loan Account) (%) | Textbox | No | — |
| 4 | विक्री कमिशन (%) | Sales Commission (%) | Textbox | No | — |
| 5 | रकमेतून (रु.) | From Amount (Rs.) | Textbox | Yes | — |
| 6 | रकमे पर्यंत (रुपये) | Up to Amount (Rs.) | Textbox | Yes | — |
| 7 | खात्याप्रमाणे कमिशन गणना | Commission per Account | Checkbox | No | — |
| 8 | कमिशन गणनेसाठी सर्व क्रेडिट व्यवहार विचारात घ्या | Consider All Credit Transactions | Checkbox | No | — |

**Action:** `+ टाका` (Add) — adds row to commission grid.

### Commission Grid Columns

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | अनु. क्र. | Sr. No. |
| 3 | योजना | Scheme |
| 4 | कमिशन | Commission |
| 5 | कर्ज खाते कमिशन | Loan Account Commission |
| 6 | रकमे पासून | From Amount |
| 7 | रकमे पर्यंत | Up to Amount |
| 8 | खात्यानुसार कमिशन | Per-Account Commission |
| 9 | सर्व क्रेडिट्स विचारात घ्या | All Credits Considered |

**Grid actions:** `निर्यात करा`, `काढा`, `मागे`.

**Footer:** `पूर्ण`, `पूर्वत`.

---

## Cross-Links

- [overview.md](overview.md)
- [agent-collection-screen.md](agent-collection-screen.md)
