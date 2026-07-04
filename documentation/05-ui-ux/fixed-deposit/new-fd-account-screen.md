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
| User screenshot (Tab 4 — इतर) | Tab 4 — Other |

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
| 13 | एजंट शाखा निवडा | Select Agent Branch | Autocomplete | No | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 14 | एजंट क्रमांक | Agent Number | Textbox | No | — |
| 15 | शोध एजंट नाव | Search Agent Name | Textbox | No | — |
| 16 | विक्री एजंट शाखा निवडा | Select Sales Agent Branch | Autocomplete | No | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 17 | विक्री एजंट क्रमांक | Sales Agent Number | Textbox | No | — |
| 18 | विक्री एजंटचे नाव शोधा | Search Sales Agent Name | Textbox | No | — |
| 19 | खाते क्र. | Account No. | Textbox | No | Auto-generated |
| 20 | खाते प्रकार | Account Type | Dropdown | Yes | Same as [FD New Scheme account types](../settings/schemes/fixed-deposit-new-scheme-screen.md#account-type-dropdown-values): `सामान्य खाते`, `ज्येष्ठ नागरिक खाते`, `महिला`, `विधवा`, `अपंग`, `दुसरी संस्था`, `नोकर`, `स्वातंत्र्यसैनिक`, `अति ज्येष्ठ नागरिक` |
| 21 | व्याज दर स्लॅब | Interest Rate Slab | Dropdown | Yes | Loaded from selected scheme's duration/benefits grid (कालावधी + व्याज दर + खाते प्रकार rows). Default: `निवडा` |
| 22 | कालावधी (महिने) | Duration (Months) | Textbox | Yes | — |
| 23 | कालावधी (दिवस) | Duration (Days) | Textbox | Yes | — |
| 24 | चालू दिनांक | Current Date | Date | Yes | — |
| 25 | मुदत ठेव रक्कम (रु.) | FD Amount (Rs.) | Textbox | Yes | — |
| 26 | व्याज दर | Interest Rate | Textbox | Yes | — |
| 27 | व्याज चालू दिनांक | Interest Start Date | Date | Yes | — |
| 28 | मुदतपूर्ती रक्कम (रु.) | Maturity Amount (Rs.) | Textbox | No | Read-only / calculated |
| 29 | पावती प्रीफिक्स | Receipt Prefix | Textbox | Yes | — |
| 30 | पावती क्रमांक | Receipt Number | Textbox | Yes | — |
| 31 | परतीची दिनांक | Return Date | Date | No | Read-only |
| 32 | पावती तारीख | Receipt Date | Date | No | Read-only |
| 33 | स्थिती | Status | Dropdown | Yes | Default: `चालू` (Active). Values: `चालू`, `बंद` (Closed), `स्थगित` (Suspended) |
| 34 | आय.एफ.एस.सी. कोड | IFSC Code | Textbox | No | — |
| 35 | बँकेचे नाव | Bank Name | Textbox | No | Read-only from IFSC |
| 36 | बँकेचे बचत खाते क्रमांक | Bank Savings Account No. | Textbox | No | — |

### Section: अनेक मुदत ठेव (Multiple FD)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 37 | वास्तविक एफडी रक्कम | Actual FD Amount | Textbox | No | — |
| 38 | गुणक | Multiplier | Textbox | No | Default: `1` |

**Action:** `+ टाका` (Add).

---

## Tab 2: वारसदार (Nominee)

Same field set and dropdown rules as [Daily New Account Tab 2](../daily/new-daily-account-screen.md#tab-2-वारसदार-nominee) (salutation, occupation, relation, Google Maps address).

### वारसदाराची माहिती

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | श्री / सौ | Salutation | Dropdown | Yes | Same as [New Customer salutation](../customer/new-customer-screen.md) |
| 2 | नाव (आडनाव - पहिले नाव - मधले नाव) | Name | Textbox | Yes | — |
| 3 | जन्म दिनांक | Date of Birth | Date | No | — |
| 4 | नामांकन करताना वय | Age at Nomination | Textbox | No | Read-only |
| 5 | नामांकन दिनांक | Nomination Date | Date | No | System date |
| 6 | व्यवसाय | Occupation | Dropdown | No | Same as [New Customer occupation](../customer/new-customer-screen.md) |
| 7 | नाते | Relation | Dropdown | Yes | Same as [Membership nominee relation](../membership/new-membership-screen.md) |
| 8 | टक्केवारी | Percentage | Textbox | No | — |

### संपर्क माहिती

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 9 | दूरध्वनी क्रमांक | Telephone | Textbox | No | — |
| 10 | मोबाईल | Mobile | Textbox | No | — |
| 11 | ई - मेल आय.डी. | E-mail | Textbox | No | — |

### पत्ता माहिती (Address)

Google Maps Places Autocomplete — same pattern as [New Customer Tab 2](../customer/new-customer-screen.md#google-maps-address-capture).

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 12 | पत्ता शोधा | Search Address | Google Maps Autocomplete | Yes | Populates fields 13–20 |
| 13 | पत्ता / इमारत / फ्लॅट / घर नं. | Address | Textbox | Yes | Auto-populated from Google Maps; editable |
| 14 | रस्ता | Road | Textbox | No | Auto-populated from Google Maps; editable |
| 15 | लँडमार्क | Landmark | Textbox | No | Manual entry |
| 16 | ठिकाण | Location | Textbox | Yes | Auto-populated from Google Maps; editable |
| 17 | राज्य | State | Textbox | Yes | Auto-populated from Google Maps; editable |
| 18 | जिल्हा | District | Textbox | No | Auto-populated from Google Maps; editable |
| 19 | तालुका | Taluka | Textbox | No | Auto-populated from Google Maps; editable |
| 20 | शहर | City | Textbox | No | Auto-populated from Google Maps; editable |
| 21 | पिन कोड | Pin Code | Textbox | No | Auto-populated from Google Maps; editable |

**Action:** `टाका` (Add).

### Nominee Grid

Columns: निवडा, अनु. क्र., श्री/सौ, नाव, नामांकन करताना वय, जन्मदिनांक, पत्ता, जिल्हा, तालुका, शहर, ठिकाण, पिन कोड, व्यवसाय, दूरध्वनी, मोबाईल, नाते, टक्केवारी, नामांकन दिनांक.

**Actions:** `निश्चित करा` (Confirm), `रद्द करा` (Cancel).

---

## Tab 3: परिचयकर्ता / संयुक्त खाते धारक (Introducer / Joint Holder)

Deferred — not documented in v1. Tab shell may render as stub until captured.

---

## Tab 4: इतर (Other)

### Section: General

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शेरा | Remarks | Textbox | No | — |
| 2 | एल. एफ. क्रमांक | L.F. Number | Textbox | No | — |
| 3 | व्याज पुनर्निवेश | Interest Reinvestment | Checkbox | No | Enables field 4 |
| 4 | एस.आय. व्याज पुनर्गंतवणूक | S.I. Interest Reinvestment | Dropdown | No | Shown when field 3 checked. e.g. `मासिक` (Monthly) |

### Section: Renewal

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 5 | ऑटो नूतनीकरण | Auto Renewal | Checkbox | No | When checked, field 6 (`नूतनीकरण`) is disabled |
| 6 | नूतनीकरण | Renewal | Checkbox | No | Disabled when field 5 checked |
| 7 | मुद्दल + व्याज | Principal + Interest | Radio | No | Renewal type; group with fields 8–9. Enabled when field 6 checked |
| 8 | फक्त मुद्दल | Only Principal | Radio | No | Default when renewal enabled |
| 9 | केवळ व्याज | Only Interest | Radio | No | — |

### Section: Interest Transfer

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 10 | व्याज हस्तांतरण | Interest Transfer | Checkbox | No | Enables fields 12–18 |
| 11 | इतर बँकेत निधी हस्तांतरण | Fund Transfer to Other Bank | Checkbox | No | — |
| 12 | जी.एल.हेड | GL Head No. | Textbox | No | Shown when field 10 checked |
| 13 | जी.एल.निवडा | Select GL | Dropdown | No | Shown when field 10 checked. e.g. `सेव्हिंग ठेव व्याज` (Saving Deposit Interest) |
| 14 | खाते क्र. | Account No. | Textbox | No | — |
| 15 | खातेधारक निवडा | Select Account Holder | Dropdown | No | Default: `निवडा` |
| 16 | वारंवारता निवडा | Select Frequency | Dropdown | No | e.g. `महिन्यात` (Monthly) |
| 17 | दिवस / तारीख निवडा | Select Day / Date | Dropdown | No | e.g. `28` (day of month when frequency is monthly) |

### Section: Account Closing

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 18 | खाते बंद करतेवेळी | At Account Closing | Checkbox | No | Enables fields 19–22 |
| 19 | जी.एल.हेड | GL Head No. | Textbox | No | Shown when field 18 checked |
| 20 | जी.एल.निवडा | Select GL | Dropdown | No | Shown when field 18 checked |
| 21 | खाते क्र. | Account No. | Textbox | No | — |
| 22 | खातेधारक निवडा | Select Account Holder | Dropdown | No | Default: `निवडा` |

**Navigation:** `मागे` (Back). **Footer:** `पूर्ण` (Complete), `पूर्ववत` (Reset).

---

## Related Documents

- [overview.md](overview.md)
- [fd-transaction-screen.md](fd-transaction-screen.md)
- [../settings/schemes/fixed-deposit-new-scheme-screen.md](../settings/schemes/fixed-deposit-new-scheme-screen.md)
