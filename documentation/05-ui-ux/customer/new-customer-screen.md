# Screen Spec — New Customer (ग्राहक > नवीन ग्राहक)

## Purpose

UI specification for registering a new customer. Three-tab wizard. Intended for AI agents implementing this screen.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | नवीन ग्राहक | New Customer |
| Breadcrumb | डॅशबोर्ड > ग्राहक > नवीन ग्राहक | Dashboard > Customer > New Customer |
| Parent Module | ग्राहक | Customer |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | सभासद तपशील | Member Details |
| 2 | पत्ता | Address |
| 3 | केवायसी कागदपत्रे | KYC Documents |

## Reference Media

| File | Tab / Section |
| :--- | :--- |
| `screenshots/grahak_khatedar/डॅशबोर्ड-ग्राहक-नवीन ग्राहक-1.mp4` | Tab 1 — Member Details (scroll + dropdowns) |
| `screenshots/grahak_khatedar/डॅशबोर्ड-ग्राहक-नवीन ग्राहक-2.mp4` | Tab 2 — Address |
| `screenshots/grahak_khatedar/डॅशबोर्ड-ग्राहक-नवीन ग्राहक-3.png` | Tab 3 — KYC Documents |

Extracted frames: `screenshots/grahak_khatedar/new-customer-1-frames/`, `new-customer-2-frames/`.

---

## Tab 1: सभासद तपशील (Member Details)

### Top Field

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | ग्राहक प्रकार | Customer Type | Dropdown | No | `वैयक्तिक` (Individual), `मालमत्ता फर्म` (Proprietorship Firm), `एसजी` (Self Help Group), `दुसरी संस्था` (Other Institution) |

### Section: सभासद माहिती (Member Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 2 | पॅन | PAN | Textbox | No | With `ई-पडताळणी` (e-Verification) button |
| 3 | आधार क्र. | Aadhaar No. | Textbox | No | With `ई-पडताळणी` button |
| 4 | ग्राहक क्र. | Customer No. | Textbox | Yes | Auto-generated; read-only (e.g. `661`) |
| 5 | शाखा क्रमांक | Branch Number | Textbox | Yes | Read-only (e.g. `1`) |
| 6 | शाखा | Branch | Dropdown | Yes | Read-only; e.g. कोतोली मुख्य कार्यालय |
| 7 | श्री. / सौ. | Salutation | Dropdown | No | Default: `श्री.` (Mr.). Other values: `TODO` |
| 8 | नाव (आडनाव - पहिले नाव - मधले नाव) | Name (Surname - First - Middle) | Textbox | Yes | — |
| 9 | लिंग | Gender | Dropdown | No | Default: `पुरुष` (Male). Read-only when salutation set. Other values: `TODO` |
| 10 | जन्म दिनांक | Date of Birth | Date | Yes | — |
| 11 | वय (वर्षे) | Age (Years) | Textbox | No | Auto-calculated from DOB |
| 12 | वय (महिने) | Age (Months) | Textbox | No | Read-only |
| 13 | व्यवसाय | Occupation | Dropdown | No | Default: `एन/ए` (N/A). Has `+` add button. Master list: `TODO` |
| 14 | ग्राहक झाल्याची दिनांक | Customer Since Date | Date | No | Read-only; system date |

### Section: इतर तपशील (Other Details)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 15 | वैवाहिक स्थिती | Marital Status | Dropdown | No | Default: `निवडा`. Values: `TODO` |
| 16 | जात | Caste | Dropdown | No | Default: `एन/ए`. Has `+` button. Values: `TODO` |
| 17 | धर्म | Religion | Dropdown | No | Default: `एन/ए`. Values: `TODO` |
| 18 | राष्ट्रीयत्व | Nationality | Dropdown | No | Default: `भारतीय` (Indian) |
| 19 | वर्ग | Category | Dropdown | No | `TODO` |
| 20 | स्थिती | Status | Dropdown | Yes | Default: `चालू` (Active). Other values: `TODO` |
| 21 | पर्याय १ | Option 1 | Dropdown | No | `TODO` |
| 22 | पर्याय २ | Option 2 | Dropdown | No | `TODO` |
| 23 | पर्याय ३ | Option 3 | Dropdown | No | `TODO` |
| 24 | पर्याय ४ | Option 4 | Dropdown | No | `TODO` |
| 25 | ई.एस.आय. / ई.पी.एफ. न. | ESI / EPF No. | Textbox | No | — |
| 26 | पासपोर्ट क्रमांक | Passport Number | Textbox | No | — |
| 27 | शिक्षण | Education | Textbox | No | — |
| 28 | लेजर फोलिओ नं. | Ledger Folio No. | Textbox | No | — |
| 29 | स्थावर मालमत्तेचा तपशील | Immovable Property Details | Textbox | No | — |
| 30 | ग्राहक होण्याचा उद्देश | Purpose of Becoming Customer | Dropdown | No | `TODO` |
| 31 | देहावसान तारीख | Date of Death | Date | No | Disabled unless status warrants |
| 32 | जोखीम श्रेणी | Risk Category | Dropdown | No | Default: `निवडा`. Values: `TODO` |
| 33 | व्यवहार रकमेवर अलर्ट | Transaction Amount Alert | Textbox | No | — |
| 34 | सोसायटी मतदार आहे का? | Is Society Voter? | Checkbox | No | — |
| 35 | अपंग आहे का? | Is Disabled? | Checkbox | No | — |
| 36 | आर्मी | Army | Checkbox | No | — |
| 37 | वडिलांचे नाव | Father's Name | Textbox | No | — |
| 38 | आईचे नाव | Mother's Name | Textbox | No | — |
| 39 | जोडीदाराचे नाव | Spouse's Name | Textbox | No | — |

### Section: सूचक (Introducer)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 40 | ग्राहक क्र. | Customer No. | Textbox | No | — |
| 41 | सभासदचे नाव | Member Name | Dropdown | No | `TODO` |

### Section: पालक कर्मचारी (Guardian Employee)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 42 | पालक कर्मचारी | Guardian Employee | Dropdown | No | `TODO` |
| 43 | ग्राहकाचे नाव | Customer Name | Dropdown | No | `TODO` |

### Section: टीडीएस (TDS)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 44 | टीडीएस | TDS | Radio | No | `होय` (Yes) / `नाही` (No). Default: `नाही` |
| 45 | नसेल तर कारण निवडा | If No, Select Reason | Dropdown | No | Shown when TDS = No. e.g. `सभासद` (Member). Full list: `TODO` |

### Section: इंटरनेट बँकिंग (Internet Banking)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 46 | लॉगिन नाव | Login Name | Textbox | No | — |
| 47 | पासवर्ड | Password | Textbox | No | Masked |
| 48 | सभासद उत्पन्न | Member Income | Textbox | No | — |
| 49 | कौटुंबिक उत्पन्न | Family Income | Textbox | No | — |

### Section: ॲडव्हान्स सेवा (Advance Services)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 50 | एसएमएस अलर्ट सक्रिय करा | Activate SMS Alert | Checkbox | No | — |
| 51 | व्हॉट्सॲप अलर्ट सक्रिय करा | Activate WhatsApp Alert | Checkbox | No | — |
| 52 | ईमेल अलर्ट सक्रिय करा | Activate Email Alert | Checkbox | No | — |
| 53 | ईमेल वर स्टेटमेंट (का-सा) | Email Statement (CA-SA) | Dropdown | No | Default: `आवश्यक नाही` (Not Required). Other values: `TODO` |
| 54 | निधी हस्तांतरण मर्यादा | Fund Transfer Limit | Textbox | No | — |
| 55 | वारसदार टाका | Add Nominee | Checkbox | No | — |
| 56 | कर्ज जोखिम मर्यादा | Loan Risk Limit | Textbox | No | — |

### Section: इतर भाषा माहिती (Other Language Information)

Section header visible at bottom; fields not captured in video.

**Navigation:** `पुढे` (Next) — proceed to Address tab. `वर` (Up) — scroll to top.

---

## Tab 2: पत्ता (Address)

### Section: पत्त्याची माहिती (Address Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | पत्त्याचा प्रकार | Address Type | Dropdown | Yes | `कायमचा` (Permanent), `कॉन्टॅक्ट` (Contact), `इतर` (Other) |
| 2 | पत्ता / इमारत / फ्लॅट / घर नं. | Address / Building / Flat / House No. | Textbox | Yes | — |
| 3 | रस्ता | Road | Textbox | No | — |
| 4 | लँडमार्क | Landmark | Textbox | No | — |
| 5 | ठिकाण | Location | Dropdown | Yes | Default: `एन/ए` or `निवडा`. Has `+` button. Values: `TODO` |
| 6 | राज्य | State | Dropdown | Yes | Default: `निवडा`. Has `+` button. Values: `TODO` |
| 7 | जिल्हा | District | Dropdown | Yes | Default: `निवडा`. Has `+` button. Values: `TODO` |
| 8 | तालुका | Taluka | Dropdown | Yes | Default: `निवडा`. Has `+` button. Values: `TODO` |
| 9 | शहर | City | Dropdown | Yes | Default: `निवडा`. Has `+` button. Values: `TODO` |
| 10 | पिन कोड | Pin Code | Textbox | No | — |
| 11 | मोबाईल क्रमांक | Mobile Number | Textbox | Yes | — |
| 12 | दूरध्वनी क्रमांक | Telephone Number | Textbox | No | — |
| 13 | ई - मेल | E-mail | Textbox | No | — |
| 14 | संपर्क व कायमचा पत्ते सारखेच आहेत | Contact Same as Permanent | Checkbox | No | — |

**Actions:** `टाका +` (Add) — add row to address grid. `क्लिअर` (Clear), `तपशील` (Details), `काढा` (Remove).

### Address Grid Columns

निवडा, अनु. क्र, पत्त्याचा प्रकार, पत्ता, जिल्हा, ब्लॉक, शहर, ठिकाण, पिन कोड, दूरध्वनी क्रमांक, मोबाईल क्रमांक, ई - मेल.

---

## Tab 3: केवायसी कागदपत्रे (KYC Documents)

### Document Grid

| # | Marathi Column | English Column | Type |
| :---: | :--- | :--- | :--- |
| 1 | निवडा | Select | Checkbox |
| 2 | अनु. क्र | Sr. No. | Label |
| 3 | कागदपत्र नाव | Document Name | Label |
| 4 | बंधनकारक आहे का? | Is Mandatory? | Label (`होय`/`नाही`) |
| 5 | दस्तावेज क्रमांक | Document Number | Textbox |
| 6 | स्थिती | Status | Label (e.g. `उपलब्ध नाही`) |
| 7 | पहा | View | Button |

**Pre-loaded document rows:**

| Sr. | Document (Marathi) | Document (English) | Mandatory |
| :---: | :--- | :--- | :---: |
| 1 | फोटो | Photo | Yes |
| 2 | सही | Signature | Yes |
| 3 | पत्ता पुरावा | Address Proof | Yes |
| 4 | ओळख पुरावा | Identity Proof | Yes |
| 5 | Original Aadhar Photo | Original Aadhar Photo | No |
| 6 | मूळ आधार फोटो | Original Aadhar Photo (Marathi) | No |

**Upload:** `Choose File` + `अपलोड` (Upload) button. `काढा` (Remove) for selected rows.

**Footer actions:** `पूर्ण` (Complete/Save), `पूर्ववत` (Reset).

---

## Related Documents

- [overview.md](overview.md)
- [customer-list-screen.md](customer-list-screen.md)
- [../membership/new-membership-screen.md](../membership/new-membership-screen.md)
