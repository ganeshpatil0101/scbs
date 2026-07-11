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
| 1 | ग्राहक निवडा | Select Customer | Autocomplete | Yes | Replaces `ग्राहक क्र.` + `ग्राहक नाव`. Enter resolves by customer no. or name; e.g. `661 — Customer 1`. See [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |

**Customer summary (read-only Labels after resolve):** सभासद प्रकार, सभासद खाते क्र., वय (व्यवहार दिनांक पर्यंतचे वर्ष), ग्राहक शाखा, पॅन क्र., विशेष सूचना.

### Section: खात्याची माहिती (Account Details)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 2 | योजना निवडा | Select Scheme | Dropdown | Yes | Loaded dynamically from FD schemes (Settings > नवीन योजना). Sample: `मुदत ठेव`, `दामदुप्पट`, `दाम दुप्पट ठेव (कर्जातील)`, `पेंशन ठेव` |
| 3 | क्लोज / ओपन एंडेड | Closed / Open Ended | Label (read-only) | No | Auto-filled from scheme; e.g. `क्लोज एंडेड` |
| 4 | व्याज प्रकार | Interest Type | Label (read-only) | No | Auto-filled from scheme; e.g. `साधे व्याज` |
| 5 | कम्पाउंडिंग | Compounding | Label (read-only) | No | Auto-filled from scheme |
| 6 | एजंट शाखा निवडा | Select Agent Branch | Autocomplete | No | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 7 | एजंट निवडा | Select Agent | Autocomplete | No | Replaces `एजंट क्रमांक` + `शोध एजंट नाव`. Scoped to field 6. Sample: `1 — Agent 1`. Enter resolves by ID or name |
| 8 | खाते क्र. | Account No. | Label (read-only) | No | Auto-generated on save |
| 9 | खाते प्रकार | Account Type | Dropdown | Yes | Same as [New Scheme FD account types](../settings/schemes/new-scheme-screen.md): `सामान्य खाते`, `ज्येष्ठ नागरिक खाते`, `महिला`, `विधवा`, `अपंग`, `दुसरी संस्था`, `नोकर`, `स्वातंत्र्यसैनिक`, `अति ज्येष्ठ नागरिक` |
| 10 | व्याज दर स्लॅब | Interest Rate Slab | Dropdown | Yes | Loaded from selected scheme's duration/benefits grid (कालावधी + व्याज दर + खाते प्रकार rows). Default: `निवडा` |
| 11 | कालावधी (महिने) | Duration (Months) | Label (read-only) | Yes | Auto-filled from slab selection |
| 12 | कालावधी (दिवस) | Duration (Days) | Label (read-only) | Yes | Auto-filled from slab selection |
| 13 | चालू दिनांक | Current Date | Date | Yes | Default: system date |
| 14 | मुदत ठेव रक्कम (रु.) | FD Amount (Rs.) | Textbox | Yes | — |
| 15 | व्याज दर | Interest Rate | Label (read-only) | Yes | Auto-filled from slab; override requires admin role |
| 16 | व्याज चालू दिनांक | Interest Start Date | Date | Yes | — |
| 17 | मुदतपूर्ती रक्कम (रु.) | Maturity Amount (Rs.) | Label (read-only) | No | Calculated |
| 18 | परतीची दिनांक | Return Date | Label (read-only) | No | Calculated |
| 19 | पावती तारीख | Receipt Date | Label (read-only) | No | Calculated |
| 20 | स्थिती | Status | Dropdown | Yes | Default: `चालू` (Active). Values: `चालू`, `बंद` (Closed), `स्थगित` (Suspended) |
| 21 | आय.एफ.एस.सी. कोड | IFSC Code | Textbox | No | Enables bank payout |
| 22 | बँकेचे नाव | Bank Name | Label (read-only) | No | Auto-filled from IFSC |
| 23 | बँकेचे बचत खाते क्रमांक | Bank Savings Account No. | Textbox | No | — |

### Section: प्रगत सेटिंग्ज (Advanced Settings)

> Collapsed by default. Visible to users with accounting/admin role or when expanded manually.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 24 | विक्री एजंट शाखा निवडा | Select Sales Agent Branch | Autocomplete | No | Sample: `1 — Branch 1`. Enter resolves by ID or name |
| 25 | विक्री एजंट निवडा | Select Sales Agent | Autocomplete | No | Replaces `विक्री एजंट क्रमांक` + `विक्री एजंटचे नाव शोधा`. Sample: `1 — Agent 1` |
| 26 | पावती प्रीफिक्स | Receipt Prefix | Textbox | Yes | Receipt series |
| 27 | पावती क्रमांक | Receipt Number | Textbox | Yes | — |
| 28 | वास्तविक एफडी रक्कम | Actual FD Amount | Textbox | No | Multiple FD workflow |
| 29 | गुणक | Multiplier | Textbox | No | Default: `1` |

**Action (Multiple FD):** `+ टाका` (Add).

**Action:** `पुढे` (Next).

---

## Tab 2: वारसदार (Nominee)

Uses shared component `app-nominee-form` + `app-nominee-grid` — same field set and dropdown rules as [Daily New Account Tab 2](../daily/new-daily-account-screen.md#tab-2-वारसदार-nominee) (salutation, occupation, relation, Google Maps address).

### वारसदाराची माहिती

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | श्री / सौ | Salutation | Dropdown | Yes | Same as [New Customer salutation](../customer/new-customer-screen.md) |
| 2 | नाव (आडनाव - पहिले नाव - मधले नाव) | Name | Textbox | Yes | — |
| 3 | जन्म दिनांक | Date of Birth | Date | No | — |
| 4 | नामांकन करताना वय | Age at Nomination | Label (read-only) | No | Calculated |
| 5 | नामांकन दिनांक | Nomination Date | Label (read-only) | No | System date |
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

`TODO` — Deferred; not documented in v1. Tab shell may render as stub until captured.

---

## Tab 4: इतर (Other)

### Section: General

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शेरा | Remarks | Textbox | No | — |
| 2 | व्याज पुनर्निवेश | Interest Reinvestment | Checkbox | No | Enables field 3 |
| 3 | एस.आय. व्याज पुनर्गंतवणूक | S.I. Interest Reinvestment | Dropdown | No | Shown when field 2 checked. e.g. `मासिक` (Monthly) |

### Section: Renewal

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 4 | ऑटो नूतनीकरण | Auto Renewal | Checkbox | No | When checked, field 5 (`नूतनीकरण`) is disabled |
| 5 | नूतनीकरण | Renewal | Checkbox | No | Disabled when field 4 checked |
| 6 | मुद्दल + व्याज | Principal + Interest | Radio | No | Renewal type; group with fields 7–8. Enabled when field 5 checked |
| 7 | फक्त मुद्दल | Only Principal | Radio | No | Default when renewal enabled |
| 8 | केवळ व्याज | Only Interest | Radio | No | — |

### Section: Interest Transfer

Visible when field 9 checked.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 9 | व्याज हस्तांतरण | Interest Transfer | Checkbox | No | Enables fields 11–16 |
| 10 | इतर बँकेत निधी हस्तांतरण | Fund Transfer to Other Bank | Checkbox | No | — |
| 11 | जी.एल. निवडा | Select GL | Autocomplete | No | Replaces `जी.एल.हेड` + `जी.एल.निवडा`. Sample: `91 — FD Interest`. See [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |
| 12 | खातेधारक निवडा | Select Account Holder | Autocomplete | No | Replaces `खाते क्र.` + `खातेधारक निवडा` dropdown. Sample: `101 — Account Holder 1` |
| 13 | वारंवारता निवडा | Select Frequency | Dropdown | No | e.g. `महिन्यात` (Monthly) |
| 14 | दिवस / तारीख निवडा | Select Day / Date | Dropdown | No | e.g. `28` (day of month when frequency is monthly) |

### Section: Account Closing

Visible when field 15 checked.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 15 | खाते बंद करतेवेळी | At Account Closing | Checkbox | No | Enables fields 16–17 |
| 16 | जी.एल. निवडा | Select GL | Autocomplete | No | Replaces `जी.एल.हेड` + `जी.एल.निवडा` |
| 17 | खातेधारक निवडा | Select Account Holder | Autocomplete | No | Replaces `खाते क्र.` + `खातेधारक निवडा` dropdown |

### Section: प्रगत सेटिंग्ज (Advanced Settings)

> Collapsed by default.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 18 | एल. एफ. क्रमांक | L.F. Number | Textbox | No | — |

**Navigation:** `मागे` (Back). **Footer:** `पूर्ण` (Complete), `पूर्ववत` (Reset).

---

## Related Documents

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [fd-transaction-screen.md](fd-transaction-screen.md)
- [fd-account-management-screen.md](fd-account-management-screen.md)
- [../settings/schemes/new-scheme-screen.md](../settings/schemes/new-scheme-screen.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
