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
| 1 | ग्राहक निवडा | Select Customer | Autocomplete | Yes | Replaces `ग्राहक क्र.` + `ग्राहक नाव`. Enter resolves by customer no. or name; e.g. `661 — Customer 1`. See [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |
| 2 | स्थिती | Status | Dropdown | Yes | Default: `चालू` (Active). Values: `चालू`, `बंद` (Closed), `स्थगित` (Suspended) |
| 3 | मोबाईल क्रमांक | Mobile Number | Textbox | No | — |
| 4 | रुजू दिनांक | Joining Date | Date | Yes | System date |

### बचत खाते (Savings Account)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 5 | शाखा निवडा | Select Branch | Autocomplete | Yes | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 6 | जी.एल. निवडा | Select GL | Autocomplete | No | Sample: `38 — Saving`. Enter resolves by ID or name; shows display name |
| 7 | खातेधारक निवडा | Select Account Holder | Autocomplete | Yes | Sample: `101 — Account Holder 1`, `102 — Account Holder 2`, `103 — Account Holder 3`. Enter resolves by ID or name; shows display name |

### टीडीएस (TDS)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 8 | होय / नाही | Yes / No | Radio | No | TDS applicable |
| 9 | कारण निवडा | Select Reason | Dropdown | No | Shown when TDS = `नाही`. Values: `सभासद` (Member), `फॉर्म १५ डीआय`, `फॉर्म १५ एच`, `फॉर्म १५ जी` |

### Section: प्रगत सेटिंग्ज (Advanced Settings)

> Collapsed by default. Visible to users with accounting/admin role or when expanded manually.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 10 | मेघदूत एजंट कोड | Meghdoot Agent Code | Textbox | No | — |

#### सुरक्षा ठेव (Security Deposit)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 11 | सुरक्षा ठेव | Security Deposit | Checkbox | No | Enables fields 12–15 |
| 12 | शाखा निवडा | Select Branch | Autocomplete | Yes* | Sample: `1 — Branch 1`. Enter resolves by ID or name |
| 13 | जी.एल. निवडा | Select GL | Autocomplete | No | Sample: `38 — Saving` |
| 14 | खातेधारक निवडा | Select Account Holder | Autocomplete | No | Sample: `101 — Account Holder 1` |
| 15 | मर्यादा | Limit | Textbox | No | — |
| 16 | कपात (%) | Deduction (%) | Textbox | No | — |

#### मशीन कपात (Machine Deduction)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 17 | मशीन कपात | Machine Deduction | Checkbox | No | Enables fields below |
| 18 | जी.एल. निवडा | Select GL | Autocomplete | No | Sample: `38 — Saving` |
| 19 | खातेधारक निवडा | Select Account Holder | Autocomplete | No | Sample: `101 — Account Holder 1` |
| 20 | मर्यादा | Limit | Textbox | No | — |
| 21 | कपात | Deduction | Textbox | No | — |
| 22 | रु. / टक्के | Rs. / Percentage | Radio | No | — |

#### भविष्य निर्वाह निधी (Provident Fund)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 23 | भविष्य निर्वाह निधी | Provident Fund | Checkbox | No | Enables PF fields |
| 24 | जी.एल. निवडा | Select GL | Autocomplete | No | Sample: `38 — Saving` |
| 25 | खातेधारक निवडा | Select Account Holder | Autocomplete | No | Sample: `101 — Account Holder 1` |
| 26 | कपात (%) | Deduction (%) | Textbox | No | — |

**Action:** `पुढे` (Next).

---

## Tab 2: प्रतिनिधी माहिती (Commission Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | योजना निवडा | Select Scheme | Dropdown | Yes | Loaded dynamically from Daily schemes (Settings > नवीन योजना). Sample: `डेली १`, `डेली २`, `पिग्मी ठेव` |
| 2 | कमिशन (%) | Commission (%) | Textbox | Yes | — |
| 3 | रकमेतून (रु.) | From Amount (Rs.) | Textbox | Yes | — |
| 4 | रकमे पर्यंत (रुपये) | Up to Amount (Rs.) | Textbox | Yes | — |

### Section: प्रगत सेटिंग्ज (Advanced Settings)

> Collapsed by default.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 5 | कमिशन (कर्ज खाते) (%) | Commission (Loan Account) (%) | Textbox | No | — |
| 6 | विक्री कमिशन (%) | Sales Commission (%) | Textbox | No | — |
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
- [ux-optimization.md](ux-optimization.md)
- [agent-collection-management-screen.md](agent-collection-management-screen.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
