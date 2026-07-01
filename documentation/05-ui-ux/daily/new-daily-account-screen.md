# Screen Spec — New Daily Account (डेली > नवीन खाते)

## Purpose

UI specification for opening a new daily (pigmy) deposit account. Four-tab wizard.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | नवीन खाते | New Account |
| Breadcrumb | डॅशबोर्ड > डेली > नवीन खाते | Dashboard > Daily > New Account |
| Parent Module | डेली | Daily |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | खात्याची माहिती | Account Information |
| 2 | वारसदार | Nominee |
| 3 | परिपक्वता / संयुक्त एसी धारक | Maturity / Joint AC Holder |
| 4 | मंजूरी | Approval |

## Reference Screenshots / Media

| File | Tab |
| :--- | :--- |
| `screenshots/डेली/डॅशबोर्ड_डेली _नवीन खाते.mp4` | All tabs (from video) |
| `screenshots/डेली/new-account-frames/frame_0000.jpg` | Tab 1 |
| `screenshots/डेली/new-account-frames/frame_0040.jpg` | Tab 2 — Nominee |

---

## Tab 1: खात्याची माहिती (Account Information)

### ग्राहक माहिती (Customer Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | ग्राहक क्र. | Customer No. | Textbox | Yes | — |
| 2 | ग्राहक नाव | Customer Name | Textbox | Yes | — |
| 3 | सभासद क्रमांक | Member Number | Textbox | No | Read-only |
| 4 | वय (वर्षे) | Age (Years) | Textbox | No | Read-only |
| 5 | सभासद शाखा नाव | Member Branch Name | Textbox | No | Read-only |
| 6 | सभासद प्रकार | Member Type | Textbox | No | Read-only |
| 7 | विशेष सूचना | Special Instructions | Textbox | No | Read-only |

### खात्याची माहिती (Account / Agent)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 8 | योजना निवडा | Select Scheme | Dropdown | Yes | Values: `TODO` |
| 9 | एजंट शाखा निवडा | Select Agent Branch | Autocomplete | Yes | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 10 | एजंट क्रमांक | Agent Number | Textbox | Yes | — |
| 11 | शोध एजंट नाव | Search Agent Name | Textbox | No | — |
| 12 | खाते क्र. | Account No. | Textbox | No | Auto-generated |
| 13 | विक्री एजंट शाखा निवडा | Select Sales Agent Branch | Autocomplete | No | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 14 | विक्री एजंट क्रमांक | Sales Agent Number | Textbox | No | — |
| 15 | विक्री एजंटचे नाव शोधा | Search Sales Agent Name | Textbox | No | — |

### खाते तपशील (Account Details)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 16 | कालावधी निवडा | Select Duration | Dropdown | Yes | Values: `TODO` |
| 17 | कालावधी (महिने) | Duration (Months) | Textbox | Yes | — |
| 18 | कालावधी (दिवस) | Duration (Days) | Textbox | Yes | — |
| 19 | व्याज दर (% पीए) | Interest Rate (% p.a.) | Textbox | Yes | — |
| 20 | कमिशन दर | Commission Rate | Textbox | Yes | — |
| 21 | व्याज प्रकार | Interest Type | Dropdown | No | Values: `TODO` |
| 22 | परिणामगणन | Compounding | Dropdown | No | Values: `TODO` |
| 23 | चालू दिनांक | Current Date | Date | Yes | System date |
| 24 | मुदतपूर्ती दिनांक | Maturity Date | Date | No | — |
| 25 | दैनिक ठेव रक्कम | Daily Deposit Amount | Textbox | Yes | — |
| 26 | मुदतपूर्ती रक्कम | Maturity Amount | Textbox | No | — |
| 27 | विशेष सूचना | Special Instructions | Textbox | No | — |
| 28 | कलेक्शन रक्कम मर्यादा | Collection Amount Limit | Textbox | No | — |
| 29 | नावे मर्यादा | Debit Limit | Textbox | No | — |
| 30 | स्थिती निवडा | Select Status | Dropdown | No | e.g. `चालू`. Other values: `TODO` |
| 31 | कर्जासाठी पिग्मी खाते | Pigmy Account for Loan | Checkbox | No | — |
| 32 | आयएफएससी कोड | IFSC Code | Textbox | No | — |
| 33 | बँक नाव | Bank Name | Textbox | No | — |
| 34 | बँक बचत खाते नं | Bank Savings Account No. | Textbox | No | — |
| 35 | किमान शिल्लक | Minimum Balance | Textbox | No | — |

**Action:** `पुढे` (Next).

Tabs 3–4: `TODO` — not captured in video.

---

## Tab 2: वारसदार (Nominee)

### वारसदाराची माहिती

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | श्री / सौ | Title | Dropdown | Yes | Values: `TODO` |
| 2 | नाव(आडनाव -पहिले नाव-मधले नाव) | Name | Textbox | Yes | — |
| 3 | जन्म दिनांक | Date of Birth | Date | No | — |
| 4 | नामांकन करताना वय | Age at Nomination | Textbox | No | — |
| 5 | नामांकन दिनांक | Nomination Date | Date | No | System date |
| 6 | व्यवसाय | Occupation | Dropdown | No | Values: `TODO` |
| 7 | नाते | Relation | Dropdown | Yes | Values: `TODO` |
| 8 | टक्केवारी | Percentage | Textbox | No | — |

### संपर्क माहिती

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 9 | दूरध्वनी क्रमांक | Telephone | Textbox | No | — |
| 10 | मोबाईल | Mobile | Textbox | No | — |
| 11 | ई - मेल आय.डी. | Email ID | Textbox | No | — |

### पत्ता माहिती

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 12 | पत्ता / इमारत / फ्लॅट / घर नं. | Address | Textbox | Yes | — |
| 13 | रस्ता | Road | Textbox | No | — |
| 14 | लँडमार्क | Landmark | Textbox | No | — |
| 15 | ठिकाण | Location | Dropdown | Yes | e.g. `एन / ए` |
| 16 | राज्य | State | Dropdown | Yes | Values: `TODO` |
| 17 | जिल्हा | District | Dropdown | No | Values: `TODO` |
| 18 | तालुका | Taluka | Dropdown | No | Values: `TODO` |
| 19 | शहर | City | Dropdown | No | Values: `TODO` |
| 20 | पिन कोड | Pin Code | Textbox | No | — |

**Actions:** `टाका` (Add), `निवड करा`, `काढा`.

**Multiple nominees table columns:** निवडा, अनु. क्र., श्री/सौ, नाव, नामांकन करताना वय, जन्मदिनांक, पत्ता, जिल्हा, तालुका, शहर, ठिकाण, पिन कोड, व्यवसाय, दूरध्वनी, मोबाईल, नाते, टक्केवारी, नामांकन दिनांक.

**Footer:** `पूर्ण`, `पूर्ववत`.

---

## Cross-Links

- [overview.md](overview.md)
- [../settings/schemes/daily-new-scheme-screen.md](../settings/schemes/daily-new-scheme-screen.md)
