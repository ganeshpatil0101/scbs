# Screen Spec — New FD Account (मुदत ठेव > नवीन खाते)

## Purpose

UI specification for opening a new fixed deposit account. Four-tab wizard.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | नवीन खाते | New Account |
| Breadcrumb | डॅशबोर्ड > मुदत ठेव > नवीन खाते | Dashboard > Fixed Deposit > New Account |
| Parent Module | मुदत ठेव | Fixed Deposit |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | खात्याची माहिती | Account Information |
| 2 | वारसदार | Nominee |
| 3 | परिचयकर्ता / संयुक्त खाते धारक | Introducer / Joint Holder |
| 4 | इतर | Other |

## Reference Screenshots

| File | Tab |
| :--- | :--- |
| `screenshots/मुदत ठेव/डॅशबोर्ड-मुदत ठेव-नवीन खाते.png` | Tab 1 — full form |
| `screenshots/मुदत ठेव/डॅशबोर्ड-मुदत ठेव-नवीन खाते-1.png` | Tab 1 — Scheme dropdown open |
| `screenshots/मुदत ठेव/डॅशबोर्ड-मुदत ठेव-नवीन खाते-2.png` | Tab 2 — Nominee |

---

## Tab 1: खात्याची माहिती (Account Information)

### Section: खाते धारकाची माहिती (Account Holder Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | ग्राहक क्र. | Customer No. | Textbox | Yes | — |
| 2 | ग्राहक नाव | Customer Name | Textbox | No | Read-only |
| 3 | सभासद प्रकार | Member Type | Textbox | No | Read-only |
| 4 | सभासद खाते क्र. | Member Account No. | Textbox | No | Read-only |
| 5 | वय (व्यवहार दिनांक पर्यंतचे वर्ष) | Age (Years) | Textbox | No | Read-only |
| 6 | ग्राहक शाखा | Customer Branch | Textbox | No | Read-only |
| 7 | पॅन क्र. | PAN No. | Textbox | No | Read-only |
| 8 | विशेष सूचना | Special Instructions | Textbox | No | — |

### Section: खात्याची माहिती (Account Details)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 9 | योजना निवडा | Select Scheme | Dropdown | Yes | `निवडा`, `मुदत ठेव`, `दामदुप्पट`, `दाम दुप्पट ठेव (कर्जातील)`, `पेंशन ठेव` |
| 10 | क्लोज / ओपन एंडेड | Closed / Open Ended | Textbox | No | Read-only; e.g. `क्लोज एंडेड` |
| 11 | व्याज प्रकार | Interest Type | Textbox | No | e.g. `साधे व्याज` |
| 12 | कम्पाउंडिंग | Compounding | Textbox | No | — |
| 13 | एजंट शाखा क्र. | Agent Branch No. | Textbox | No | Read-only |
| 14 | एजंट शाखा निवडा | Select Agent Branch | Dropdown | No | — |
| 15 | एजंट क्रमांक | Agent Number | Textbox | No | — |
| 16 | शोध एजंट नाव | Search Agent Name | Textbox | No | — |
| 17 | विक्री एजंट शाखा क्र. | Sales Agent Branch No. | Textbox | No | Read-only |
| 18 | विक्री एजंट शाखा निवडा | Select Sales Agent Branch | Dropdown | No | — |
| 19 | विक्री एजंट क्रमांक | Sales Agent Number | Textbox | No | — |
| 20 | विक्री एजंटचे नाव शोधा | Search Sales Agent Name | Textbox | No | — |
| 21 | खाते क्र. | Account No. | Textbox | No | Auto-generated |
| 22 | खाते प्रकार | Account Type | Dropdown | Yes | e.g. `सामान्य खाते` (Normal Account). Other values: `TODO` |
| 23 | व्याज दर स्लॅब | Interest Rate Slab | Dropdown | Yes | Default: `निवडा`. Values: `TODO` |
| 24 | कालावधी (महिने) | Duration (Months) | Textbox | Yes | — |
| 25 | कालावधी (दिवस) | Duration (Days) | Textbox | Yes | — |
| 26 | चालू दिनांक | Current Date | Date | Yes | — |
| 27 | मुदत ठेव रक्कम (रु.) | FD Amount (Rs.) | Textbox | Yes | — |
| 28 | व्याज दर | Interest Rate | Textbox | Yes | — |
| 29 | व्याज चालू दिनांक | Interest Start Date | Date | Yes | — |
| 30 | मुदतपूर्ती रक्कम (रु.) | Maturity Amount (Rs.) | Textbox | No | Read-only / calculated |
| 31 | पावती प्रीफिक्स | Receipt Prefix | Textbox | Yes | — |
| 32 | पावती क्रमांक | Receipt Number | Textbox | Yes | — |
| 33 | परतीची दिनांक | Return Date | Date | No | Read-only |
| 34 | पावती तारीख | Receipt Date | Date | No | Read-only |
| 35 | स्थिती | Status | Dropdown | Yes | Default: `चालू`. Other values: `TODO` |
| 36 | आय.एफ.एस.सी. कोड | IFSC Code | Textbox | No | — |
| 37 | बँकेचे नाव | Bank Name | Textbox | No | Read-only from IFSC |
| 38 | बँकेचे बचत खाते क्रमांक | Bank Savings Account No. | Textbox | No | — |

### Section: अनेक मुदत ठेव (Multiple FD)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 39 | वास्तविक एफडी रक्कम | Actual FD Amount | Textbox | No | — |
| 40 | गुणक | Multiplier | Textbox | No | Default: `1` |

**Action:** `+ टाका` (Add).

---

## Tab 2: वारसदार (Nominee)

### Nominee Entry Form

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | श्री / सौ | Salutation | Dropdown | Yes | Default: `निवडा`. Values: `TODO` |
| 2 | नाव (आडनाव - पहिले नाव - मधले नाव) | Name | Textbox | Yes | — |
| 3 | जन्म दिनांक | Date of Birth | Date | No | — |
| 4 | नामांकन करताना वय | Age at Nomination | Textbox | No | Read-only |
| 5 | नामांकन दिनांक | Nomination Date | Date | No | System date |
| 6 | व्यवसाय | Occupation | Dropdown | No | Default: `निवडा` |
| 7 | नाते | Relation | Dropdown | Yes | Default: `निवडा`. Values: `TODO` |
| 8 | टक्केवारी | Percentage | Textbox | No | — |
| 9 | दूरध्वनी क्रमांक | Telephone | Textbox | No | — |
| 10 | मोबाईल | Mobile | Textbox | No | — |
| 11 | ई - मेल आय.डी. | E-mail | Textbox | No | — |
| 12 | पत्ता / इमारत / फ्लॅट / घर नं. | Address | Textbox | Yes | — |
| 13 | रस्ता | Road | Textbox | No | — |
| 14 | लँडमार्क | Landmark | Textbox | No | — |
| 15 | ठिकाण | Location | Dropdown | Yes | e.g. `एन ए` |
| 16 | राज्य | State | Dropdown | Yes | Default: `निवडा` |
| 17 | जिल्हा | District | Dropdown | Yes | Default: `निवडा` |
| 18 | तालुका | Taluka | Dropdown | Yes | Default: `निवडा` |
| 19 | शहर | City | Dropdown | Yes | Default: `निवडा` |
| 20 | पिन कोड | Pin Code | Textbox | No | — |

**Action:** `टाका` (Add).

### Nominee Grid

Columns: निवडा, अनु. क्र., श्री/सौ, नाव, नामांकन करताना वय, जन्मदिनांक, पत्ता, जिल्हा, तालुका, शहर, ठिकाण, पिन कोड, व्यवसाय, दूरध्वनी, मोबाईल, नाते, टक्केवारी, नामांकन दिनांक.

**Actions:** `निश्चित करा` (Confirm), `रद्द करा` (Cancel).

Tabs 3–4: `TODO`.

---

## Related Documents

- [overview.md](overview.md)
- [fd-transaction-screen.md](fd-transaction-screen.md)
- [../settings/schemes/fixed-deposit-new-scheme-screen.md](../settings/schemes/fixed-deposit-new-scheme-screen.md)
