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
| 3 | स्थिती | Status | Dropdown | Yes | Default: `चालू` (Active). Values: `चालू`, `बंद` (Closed), `स्थगित` (Suspended) |
| 4 | मेघदूत एजंट कोड | Meghdoot Agent Code | Textbox | No | — |
| 5 | मोबाईल क्रमांक | Mobile Number | Textbox | No | — |
| 6 | रुजू दिनांक | Joining Date | Date | Yes | System date |

### बचत खाते (Savings Account)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 7 | शाखा निवडा | Select Branch | Autocomplete | Yes | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 8 | जी.एल. निवडा | Select GL | Autocomplete | No | Sample: `38 — Saving`. Enter resolves by ID or name; shows display name |
| 9 | खातेधारक निवडा | Select Account Holder | Autocomplete | Yes | Sample: `101 — Account Holder 1`, `102 — Account Holder 2`, `103 — Account Holder 3`. Enter resolves by ID or name; shows display name |

### सुरक्षा ठेव (Security Deposit)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 10 | सुरक्षा ठेव | Security Deposit | Checkbox | No | Enables fields 11–16 |
| 11 | शाखा निवडा | Select Branch | Autocomplete | Yes* | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 12 | जी.एल. निवडा | Select GL | Autocomplete | No | Sample: `38 — Saving`. Enter resolves by ID or name; shows display name |
| 13 | खातेधारक निवडा | Select Account Holder | Autocomplete | No | Sample: `101 — Account Holder 1`, `102 — Account Holder 2`, `103 — Account Holder 3`. Enter resolves by ID or name; shows display name |
| 14 | मर्यादा | Limit | Textbox | No | — |
| 15 | कपात (%) | Deduction (%) | Textbox | No | — |

### मशीन कपात (Machine Deduction)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 16 | मशीन कपात | Machine Deduction | Checkbox | No | Enables fields below |
| 17 | जी.एल. निवडा | Select GL | Autocomplete | No | Sample: `38 — Saving`. Enter resolves by ID or name; shows display name |
| 18 | खातेधारक निवडा | Select Account Holder | Autocomplete | No | Sample: `101 — Account Holder 1`, `102 — Account Holder 2`, `103 — Account Holder 3`. Enter resolves by ID or name; shows display name |
| 19 | मर्यादा | Limit | Textbox | No | — |
| 20 | कपात | Deduction | Textbox | No | — |
| 21 | रु. / टक्के | Rs. / Percentage | Radio | No | — |

### टीडीएस (TDS)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 22 | होय / नाही | Yes / No | Radio | No | TDS applicable |
| 23 | कारण निवडा | Select Reason | Dropdown | No | Shown when TDS = `नाही`. Values: `सभासद` (Member), `फॉर्म १५ डीआय`, `फॉर्म १५ एच`, `फॉर्म १५ जी` |

### भविष्य निर्वाह निधी (Provident Fund)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 24 | भविष्य निर्वाह निधी | Provident Fund | Checkbox | No | Enables PF fields |
| 25 | जी.एल. निवडा | Select GL | Autocomplete | No | Sample: `38 — Saving`. Enter resolves by ID or name; shows display name |
| 26 | खातेधारक निवडा | Select Account Holder | Autocomplete | No | Sample: `101 — Account Holder 1`, `102 — Account Holder 2`, `103 — Account Holder 3`. Enter resolves by ID or name; shows display name |
| 27 | कपात (%) | Deduction (%) | Textbox | No | — |

**Action:** `पुढे` (Next).

---

## Tab 2: प्रतिनिधी माहिती (Commission Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | योजना निवडा | Select Scheme | Dropdown | Yes | Loaded dynamically from Daily schemes (Settings > नवीन योजना). Sample: `डेली १`, `डेली २`, `पिग्मी ठेव` |
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
