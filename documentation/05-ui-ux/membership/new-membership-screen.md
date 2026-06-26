# Screen Spec — New Membership (सभासदत्व > नवीन सभासदत्व)

## Purpose

UI specification for creating a new membership (share account). Three-tab wizard. Intended for AI agents implementing this screen.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | नवीन सभासदत्व | New Membership |
| Breadcrumb | डॅशबोर्ड > सभासदत्व > नवीन सभासदत्व | Dashboard > Membership > New Membership |
| Parent Module | सभासदत्व | Membership |

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
| 3 | संस्था | Organization | Label | — | Read-only; branch name |
| 4 | शाखा | Branch | Label | — | Read-only |
| 5 | ग्राहक क्र. | Customer No. | Textbox | Yes | — |
| 6 | सभासदचे नाव | Member Name | Textbox | Yes | — |
| 7 | सभासद क्रमांक | Member Number | Label | — | Auto-generated (e.g. `208`) |
| 8 | स्थिती | Status | Dropdown | Yes | Default: `चालू` (Active). Other values: `TODO` |
| 9 | ठराव क्र. | Resolution No. | Textbox | Yes | — |
| 10 | ठराव दिनांक | Resolution Date | Date | Yes | — |
| 11 | सदस्तवाचे कारण | Reason for Membership | Textbox | No | — |
| 12 | संचालक | Director | Dropdown | No | `TODO` |
| 13 | वार्षिक अहवाल | Annual Report | Dropdown | No | Default: `पोस्ट` (Post). Other values: `TODO` |
| 14 | शेअर मर्यादा | Share Limit | Textbox | Yes | e.g. `1000000` |
| 15 | विशेष सूचना | Special Instructions | Textarea | No | — |
| 16 | जी.एल.हेड | G.L. Head | Textbox | No | — |
| 17 | जी.एल.हेड निवडा | Select G.L. Head | Dropdown | No | `TODO` |
| 18 | खाते क्रमांक | Account Number | Textbox | No | — |
| 19 | खातेधारक निवडा | Select Account Holder | Textbox/Search | No | — |
| 20 | संचालक नातेवाईक | Director Relative | Checkbox | No | — |

---

## Tab 2: परिचयकर्ता / संयुक्त खातेदार (Introducer / Joint Holder)

### Section: सूचक (Introducer)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | ग्राहक क्र. | Customer No. | Textbox | Yes | — |
| 2 | सभासदचे नाव | Member Name | Textbox | Yes | — |

### Section: संयुक्त खातेदार (Joint Holder)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 3 | पालक | Guardian | Checkbox | No | — |
| 4 | ग्राहक क्रमांक | Customer Number | Textbox | No | — |
| 5 | ग्राहकाचे नाव | Customer Name | Textbox | No | — |

**Action:** `+ जोड` (Add) — add joint holder to grid.

### Joint Holder Grid

Columns: निवडा, अ.क्र., ग्राहक क्रमांक, ग्राहकाचे नाव, पालक.

**Grid actions:** `निर्यात` (Export), `काढा` (Remove).

### Account Operation Instructions

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 6 | खाते चालविण्याची सूचना | Account Operation Instructions | Dropdown | No | `फक्त प्रमुख खातेदार` (Only Primary Holder), `फक्त संयुक्त खातेदार` (Only Joint Holder), `दोन्ही खातेदार आवश्यक` (Both Holders Required), `दोघांपैकी कोणीही` (Either Holder), `स्वतः` (Self) |

**Navigation:** `मागे` (Back), `पुढे` (Next).

---

## Tab 3: वारसदार (Nominee)

### Section: वारसदार माहिती (Nominee Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | श्री. / सौ. | Salutation | Dropdown | Yes | `श्री.`, `सौ.`, `श्रीमती`, `कुमारी`, `चि.` |
| 2 | नाव (आडनाव - पहिले नाव - मधले नाव) | Name (Surname - First - Middle) | Textbox | Yes | — |
| 3 | जन्म दिनांक | Date of Birth | Date | No | — |
| 4 | वय (वर्षे) | Age (Years) | Textbox | No | — |
| 5 | वय (महिने) | Age (Months) | Textbox | No | Read-only |
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
| 19 | व्यवसाय | Occupation | Dropdown | No | Default: `एन/ए`. Has `+` button |
| 20 | नाते | Relation | Dropdown | Yes | `मुलगा` (Son), `पुतण्या` (Nephew), `मुली` (Daughter), `मुलगा - पती` (Son - Husband), `पति व मुलगा` (Husband and Son), `वरील प्रमाणे` (As Above), `बायको` (Wife), `मैत्रीण` (Friend), `केअरटेकर` (Caretaker), `लहान भाऊ` (Younger Brother), `स्वतः` (Self), `पत्नी` (Wife), `पती` (Husband). Full list may extend: `TODO` |
| 21 | वारसदार टक्केवारी | Nominee Percentage | Textbox | No | — |
| 22 | बँकेचे बचत खाते क्रमांक | Bank Savings Account No. | Textbox | No | — |
| 23 | आय.एफ.एस.सी. कोड | IFSC Code | Textbox | No | — |
| 24 | बँकेचे नाव | Bank Name | Textbox | No | Read-only; derived from IFSC |

**Navigation:** `मागे` (Back). **Footer:** `पूर्ण` (Complete), `पूर्ववत` (Reset).

---

## Related Documents

- [overview.md](overview.md)
- [../customer/new-customer-screen.md](../customer/new-customer-screen.md)
- [../settings/membership/share-rules-screen.md](../settings/membership/share-rules-screen.md)
- [../settings/membership/dividend-calculation-screen.md](../settings/membership/dividend-calculation-screen.md)
