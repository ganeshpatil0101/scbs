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
| 1 | ग्राहक निवडा | Select Customer | Autocomplete | Yes | Replaces `ग्राहक क्र.` + `ग्राहक नाव`. Enter resolves by customer no. or name; e.g. `661 — Customer 1`. See [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |

**Customer summary (read-only Labels after resolve):** सभासद क्रमांक, वय (वर्षे), सभासद शाखा नाव, सभासद प्रकार, विशेष सूचना.

### खात्याची माहिती (Account / Agent)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 2 | योजना निवडा | Select Scheme | Dropdown | Yes | Loaded dynamically from Daily schemes (Settings > नवीन योजना). Sample: `डेली १`, `डेली २`, `पिग्मी ठेव` |
| 3 | एजंट शाखा निवडा | Select Agent Branch | Autocomplete | Yes | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 4 | एजंट निवडा | Select Agent | Autocomplete | Yes | Replaces `एजंट क्रमांक` + `शोध एजंट नाव`. Sample: `1 — Agent 1`. Enter resolves by ID or name |
| 5 | खाते क्र. | Account No. | Label (read-only) | No | Auto-generated on save |

### खाते तपशील (Account Details)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 6 | कालावधी निवडा | Select Duration | Dropdown | Yes | Loaded from selected scheme's duration grid (Settings > नवीन योजना > कालावधी tab) |
| 7 | कालावधी (महिने) | Duration (Months) | Label (read-only) | Yes | Auto-filled from selected duration |
| 8 | कालावधी (दिवस) | Duration (Days) | Label (read-only) | Yes | Auto-filled from selected duration |
| 9 | व्याज दर (% पीए) | Interest Rate (% p.a.) | Label (read-only) | Yes | Auto-filled from selected duration |
| 10 | कमिशन दर | Commission Rate | Textbox | Yes | — |
| 11 | चालू दिनांक | Current Date | Label (read-only) | Yes | System date |
| 12 | मुदतपूर्ती दिनांक | Maturity Date | Date | No | — |
| 13 | दैनिक ठेव रक्कम | Daily Deposit Amount | Textbox | Yes | — |
| 14 | मुदतपूर्ती रक्कम | Maturity Amount | Textbox | No | — |
| 15 | विशेष सूचना | Special Instructions | Textbox | No | — |
| 16 | स्थिती निवडा | Select Status | Dropdown | No | Default: `चालू` (Active). Values: `चालू`, `बंद` (Closed), `स्थगित` (Suspended) |
| 17 | कर्जासाठी पिग्मी खाते | Pigmy Account for Loan | Checkbox | No | — |

### Section: प्रगत सेटिंग्ज (Advanced Settings)

> Collapsed by default. Visible to users with accounting/admin role or when expanded manually.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 18 | विक्री एजंट शाखा निवडा | Select Sales Agent Branch | Autocomplete | No | Sample: `1 — Branch 1`. Enter resolves by ID or name |
| 19 | विक्री एजंट निवडा | Select Sales Agent | Autocomplete | No | Replaces `विक्री एजंट क्रमांक` + `विक्री एजंटचे नाव शोधा`. Sample: `1 — Agent 1` |
| 20 | व्याज प्रकार | Interest Type | Dropdown | No | Default from scheme. `सरळ व्याज` (Simple Interest), `चक्रवाढ व्याज` (Compound Interest) |
| 21 | परिणामगणन | Compounding | Dropdown | No | Default from scheme. `दैनिक`, `पाक्षिक`, `मासिक`, `तिमाही`, `सहामाही`, `वार्षिक` |
| 22 | कलेक्शन रक्कम मर्यादा | Collection Amount Limit | Textbox | No | — |
| 23 | नावे मर्यादा | Debit Limit | Textbox | No | — |
| 24 | किमान शिल्लक | Minimum Balance | Textbox | No | — |
| 25 | आयएफएससी कोड | IFSC Code | Textbox | No | — |
| 26 | बँक नाव | Bank Name | Textbox | No | — |
| 27 | बँक बचत खाते नं | Bank Savings Account No. | Textbox | No | — |

**Action:** `पुढे` (Next).

Tabs 3–4: `TODO` — not captured. Deferred until screenshots/MP4 available.

---

## Tab 2: वारसदार (Nominee)

### वारसदाराची माहिती

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | श्री / सौ | Title | Dropdown | Yes | Same as [New Customer salutation](../customer/new-customer-screen.md): `श्री.`, `सौ.`, `श्रीमती`, `कुमारी.`, `चि.`, `मेसर्स`, blank |
| 2 | नाव(आडनाव -पहिले नाव-मधले नाव) | Name | Textbox | Yes | — |
| 3 | जन्म दिनांक | Date of Birth | Date | No | — |
| 4 | नामांकन करताना वय | Age at Nomination | Textbox | No | — |
| 5 | नामांकन दिनांक | Nomination Date | Date | No | System date |
| 6 | व्यवसाय | Occupation | Dropdown | No | Same as [New Customer occupation](../customer/new-customer-screen.md) |
| 7 | नाते | Relation | Dropdown | Yes | Same as [Membership nominee relation](../membership/new-membership-screen.md): `मुलगा`, `पुतण्या`, `मुली`, `मुलगा - पती`, `पति व मुलगा`, `वरील प्रमाणे`, `बायको`, `मैत्रीण`, `केअरटेकर`, `लहान भाऊ`, `स्वतः`, `पत्नी`, `पती` |
| 8 | टक्केवारी | Percentage | Textbox | No | — |

### संपर्क माहिती

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 9 | दूरध्वनी क्रमांक | Telephone | Textbox | No | — |
| 10 | मोबाईल | Mobile | Textbox | No | — |
| 11 | ई - मेल आय.डी. | Email ID | Textbox | No | — |

### पत्ता माहिती (Address)

Google Maps Places Autocomplete — same pattern as [New Customer Tab 2](../customer/new-customer-screen.md#google-maps-address-capture). No geographic master dropdowns.

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

**Actions:** `टाका` (Add), `निवड करा`, `काढा`.

**Multiple nominees table columns:** निवडा, अनु. क्र., श्री/सौ, नाव, नामांकन करताना वय, जन्मदिनांक, पत्ता, जिल्हा, तालुका, शहर, ठिकाण, पिन कोड, व्यवसाय, दूरध्वनी, मोबाईल, नाते, टक्केवारी, नामांकन दिनांक.

**Footer:** `पूर्ण`, `पूर्ववत`.

---

## Mockup

- [HTML mockup (Draft)](../mockups/daily/new-daily-account-screen/) — Marathi layout for bank review

---

## Cross-Links

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [../settings/schemes/new-scheme-screen.md](../settings/schemes/new-scheme-screen.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
