# Screen Spec — New Membership (सभासदत्व > नवीन सभासदत्व)

## Purpose

UI specification for creating a new membership (share account). Three-tab wizard. Intended for AI agents implementing this screen.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | नवीन सभासदत्व | New Membership |
| Breadcrumb | डॅशबोर्ड > सभासदत्व > नवीन सभासदत्व | Dashboard > Membership > New Membership |
| Parent Module | सभासदत्व | Membership |

**Auto-fill (header):** `संस्था` (Organization) — read-only `Label` from tenant session; not repeated in form fields.

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | भाग माहिती | Share Information |
| 2 | परिचयकर्ता / संयुक्त खातेदार | Introducer / Joint Holder |
| 3 | वारसदार | Nominee |

## Reference Media

| File | Tab / Section |
| :--- | :--- |
| `screenshots/sabhsadatv/डॅशबोर्ड-सभासदत्व-नवीन सभासदत्व-1.png` | Tab 1 — Share Information |
| `screenshots/sabhsadatv/डॅशबोर्ड-सभासदत्व-नवीन सभासदत्व-2.png` | Tab 2 — Introducer / Joint Holder |
| `screenshots/sabhsadatv/डॅशबोर्ड-सभासदत्व-नवीन सभासदत्व-3.mp4` | Tab 3 — Nominee (dropdowns) |

Extracted frames: `screenshots/sabhsadatv/new-membership-3-frames/`.

---

## Tab 1: भाग माहिती (Share Information)

### Member Type

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | सभासद | Member | Radio | No | Default selected |
| 2 | नाममात्र सभासद | Nominal Member | Radio | No | — |

### Fields

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 3 | शाखा निवडा | Select Branch | Autocomplete | Yes | Read-only from session by default; editable for branch managers. e.g. `1 — कोतोली मुख्य कार्यालय`. See [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |
| 4 | ग्राहक निवडा | Select Customer | Autocomplete | Yes | Enter resolves by customer no. or name; e.g. `661 — Customer 1`. Replaces Customer No. + Member Name |
| 5 | सभासद क्रमांक | Member Number | Label | No | Auto-generated (e.g. `208`) |
| 6 | स्थिती | Status | Dropdown | Yes | Default: `चालू` (Active). Other values: `TODO` |
| 7 | ठराव क्र. | Resolution No. | Textbox | Yes | — |
| 8 | ठराव दिनांक | Resolution Date | Date | Yes | — |
| 9 | सदस्तवाचे कारण | Reason for Membership | Textbox | No | — |
| 10 | शेअर मर्यादा | Share Limit | Textbox | Yes | e.g. `1000000` |
| 11 | विशेष सूचना | Special Instructions | Textarea | No | — |

### Section: प्रगत सेटिंग्ज (Advanced Settings)

> Collapsed by default. Visible to users with accounting/admin role or when expanded manually.

| # | Marathi Label | English Label | Type | Required | Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 12 | संचालक | Director | Dropdown | No | Values: `TODO` |
| 13 | वार्षिक अहवाल | Annual Report | Dropdown | No | Default: `पोस्ट` (Post). Other values: `TODO` |
| 14 | जी.एल. निवडा | Select GL | Autocomplete | No | Sample: `38 — Saving`, `91 — FD`, `42 — Loan`. Optional accounting linkage at opening |
| 15 | खातेधारक निवडा | Select Account Holder | Autocomplete | No | Sample: `101 — Account Holder 1` |
| 16 | संचालक नातेवाईक | Director Relative | Checkbox | No | — |

---

## Tab 2: परिचयकर्ता / संयुक्त खातेदार (Introducer / Joint Holder)

### Section: सूचक (Introducer)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | ग्राहक निवडा | Select Customer | Autocomplete | Yes | Enter resolves by customer no. or name. Replaces Customer No. + Member Name for introducer |

### Section: संयुक्त खातेदार (Joint Holder)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 2 | पालक | Guardian | Checkbox | No | — |
| 3 | ग्राहक निवडा | Select Customer | Autocomplete | No | Enter resolves by customer no. or name. Replaces Customer Number + Customer Name input row |

**Action:** `+ जोड` (Add) — add joint holder to grid.

### Joint Holder Grid (`app-joint-holder-grid`)

Columns: निवडा, अ.क्र., ग्राहक क्रमांक, ग्राहकाचे नाव, पालक.

**Grid actions:** `निर्यात` (Export), `काढा` (Remove).

### Account Operation Instructions

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 4 | खाते चालविण्याची सूचना | Account Operation Instructions | Dropdown | No | `फक्त प्रमुख खातेदार` (Only Primary Holder), `फक्त संयुक्त खातेदार` (Only Joint Holder), `दोन्ही खातेदार आवश्यक` (Both Holders Required), `दोघांपैकी कोणीही` (Either Holder), `स्वतः` (Self) |

**Navigation:** `मागे` (Back), `पुढे` (Next).

---

## Tab 3: वारसदार (Nominee)

> **Shared component:** `app-nominee-form` + `app-nominee-grid`. Same field set as FD/Savings/Recurring nominee tabs.

### Section: वारसदार माहिती (Nominee Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | श्री. / सौ. | Salutation | Dropdown | Yes | `श्री.`, `सौ.`, `श्रीमती`, `कुमारी`, `चि.` |
| 2 | नाव (आडनाव - पहिले नाव - मधले नाव) | Name (Surname - First - Middle) | Textbox | Yes | — |
| 3 | जन्म दिनांक | Date of Birth | Date | No | — |
| 4 | वय (वर्षे) | Age (Years) | Textbox | No | — |
| 5 | वय (महिने) | Age (Months) | Label | No | Read-only; computed from DOB |
| 6 | लिंग | Gender | Dropdown | No | Default: `पुरुष` (Male) |

### Section: संपर्क माहिती (Contact Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 7 | दूरध्वनी क्रमांक | Telephone Number | Textbox | No | — |
| 8 | मोबाईल क्र | Mobile No. | Textbox | No | — |
| 9 | ईमेल | Email | Textbox | No | — |

### Section: पत्ता माहिती (Address Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 10 | पत्ता/इमारत/फ्लॅट/घर क्र | Address/Building/Flat/House No. | Textbox | Yes | — |
| 11 | रस्ता | Road | Textbox | No | — |
| 12 | लँडमार्क | Landmark | Textbox | No | — |
| 13 | स्थान | Location | Dropdown | Yes | Default: `निवडा`. Has `+` button. Values: `TODO` |
| 14 | राज्य | State | Dropdown | Yes | Default: `निवडा`. Has `+` button. Indian states (partial list in video): पंजाब, राजस्थान, सिक्किम, तामिळ नाडू, तेलंगणा, त्रिपुरा, उत्तर प्रदेश, उत्तराखंड, पश्चिम बंगाल, … |
| 15 | जिल्हा | District | Dropdown | Yes | Default: `निवडा`. Has `+` button. Values: `TODO` |
| 16 | तालुका | Taluka | Dropdown | Yes | Default: `निवडा`. Has `+` button. Values: `TODO` |
| 17 | शहर | City | Dropdown | Yes | Default: `निवडा`. Has `+` button. Values: `TODO` |
| 18 | पिन कोड | Pin Code | Textbox | No | — |

### Section: इतर तपशील (Other Details)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 19 | नाते | Relation | Dropdown | Yes | `मुलगा` (Son), `पुतण्या` (Nephew), `मुली` (Daughter), `मुलगा - पती` (Son - Husband), `पति व मुलगा` (Husband and Son), `वरील प्रमाणे` (As Above), `बायको` (Wife), `मैत्रीण` (Friend), `केअरटेकर` (Caretaker), `लहान भाऊ` (Younger Brother), `स्वतः` (Self), `पत्नी` (Wife), `पती` (Husband). Full list may extend: `TODO` |
| 20 | वारसदार टक्केवारी | Nominee Percentage | Textbox | No | — |

### Section: प्रगत सेटिंग्ज (Advanced Settings)

> Collapsed by default.

| # | Marathi Label | English Label | Type | Required | Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 21 | व्यवसाय | Occupation | Dropdown | No | Default: `एन/ए` |
| 22 | बँकेचे बचत खाते क्रमांक | Bank Savings Account No. | Textbox | No | Optional payout details |
| 23 | आय.एफ.एस.सी. कोड | IFSC Code | Textbox | No | — |
| 24 | बँकेचे नाव | Bank Name | Label | No | Read-only; derived from IFSC |

**Navigation:** `मागे` (Back). **Footer:** `पूर्ण` (Complete), `पूर्ववत` (Reset).

---

## Mockup

- [HTML mockup (Draft)](../mockups/membership/new-membership-screen/) — Marathi 3-tab wizard for bank review

## Related Documents

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [../customer/new-customer-screen.md](../customer/new-customer-screen.md)
- [../settings/membership/membership-configuration-screen.md](../settings/membership/membership-configuration-screen.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
- [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md)
