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
| 7 | श्री. / सौ. | Salutation | Dropdown | No | Default: `श्री.`. Values: `श्री.`, `सौ.`, `श्रीमती`, `कुमारी.`, `चि.`, `मेसर्स`, blank |
| 8 | नाव (आडनाव - पहिले नाव - मधले नाव) | Name (Surname - First - Middle) | Textbox | Yes | — |
| 9 | जन्म दिनांक | Date of Birth | Date | Yes | — |
| 10 | वय (वर्षे) | Age (Years) | Label | No | Auto-calculated from DOB |
| 11 | वय (महिने) | Age (Months) | Label | No | Read-only |
| 12 | व्यवसाय | Occupation | Dropdown | No | Default: `एन/ए` (N/A). Has `+` add button. Values: `एन/ए`, `पेन्शनर(निवृत्त)`, `गृहिणी`, `नोकर`, `शेती`, `व्यवसाय`, `शिक्षण`, `शिक्षक`, `डॉक्टर`, `इतर` |
| 13 | ग्राहक झाल्याची दिनांक | Customer Since Date | Date | No | Read-only; system date |

### Section: इतर तपशील (Other Details)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 27 | शिक्षण | Education | Textbox | No | — |
| 31 | देहावसान तारीख | Date of Death | Date | No | Disabled unless status warrants |
| 37 | वडिलांचे नाव | Father's Name | Textbox | No | — |
| 38 | आईचे नाव | Mother's Name | Textbox | No | — |
| 39 | जोडीदाराचे नाव | Spouse's Name | Textbox | No | — |

### Section: ॲडव्हान्स सेवा (Advance Services)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 50 | एसएमएस अलर्ट सक्रिय करा | Activate SMS Alert | Checkbox | No | — |
| 51 | व्हॉट्सॲप अलर्ट सक्रिय करा | Activate WhatsApp Alert | Checkbox | No | — |
| 52 | ईमेल अलर्ट सक्रिय करा | Activate Email Alert | Checkbox | No | — |
| 55 | वारसदार टाका | Add Nominee | Checkbox | No | — |

---

## Tab 2: पत्ता (Address)

### Google Maps Address Capture

Geographic address fields are **not** master-data dropdowns. Use a single **Google Maps Places Autocomplete** component (Google Maps JavaScript API / Places API) as the primary address input.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | पत्ता शोधा | Search Address | Google Maps Autocomplete | Yes | Google Places Autocomplete; user selects a place from suggestions |

**On place selection**, parse `address_components` and `formatted_address` to populate fields 3–11 below. No CBS master lists for location, state, district, taluka, or city.

| Google `address_component` type | Maps to field |
| :--- | :--- |
| `street_number`, `premise`, `subpremise`, `route` | पत्ता / इमारत / फ्लॅट / घर नं., रस्ता |
| `sublocality`, `locality`, `neighborhood` | ठिकाण |
| `administrative_area_level_3` (or nearest match) | तालुका |
| `administrative_area_level_2` | जिल्हा |
| `locality` / `administrative_area_level_2` | शहर |
| `administrative_area_level_1` | राज्य |
| `postal_code` | पिन कोड |

Fields remain editable after auto-fill so the user can correct parsed values. `+` add buttons on geographic fields are **not** used.

### Section: पत्त्याची माहिती (Address Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 2 | पत्त्याचा प्रकार | Address Type | Dropdown | Yes | `कायमचा` (Permanent), `कॉन्टॅक्ट` (Contact), `इतर` (Other) |
| 3 | पत्ता / इमारत / फ्लॅट / घर नं. | Address / Building / Flat / House No. | Textbox | Yes | Auto-populated from Google Maps; editable |
| 4 | रस्ता | Road | Textbox | No | Auto-populated from Google Maps; editable |
| 5 | लँडमार्क | Landmark | Textbox | No | Manual entry |
| 6 | ठिकाण | Location | Textbox | Yes | Auto-populated from Google Maps; editable |
| 7 | राज्य | State | Textbox | Yes | Auto-populated from Google Maps; editable |
| 8 | जिल्हा | District | Textbox | Yes | Auto-populated from Google Maps; editable |
| 9 | तालुका | Taluka | Textbox | Yes | Auto-populated from Google Maps; editable |
| 10 | शहर | City | Textbox | Yes | Auto-populated from Google Maps; editable |
| 11 | पिन कोड | Pin Code | Textbox | No | Auto-populated from Google Maps; editable |
| 12 | मोबाईल क्रमांक | Mobile Number | Textbox | Yes | Manual entry |
| 13 | दूरध्वनी क्रमांक | Telephone Number | Textbox | No | Manual entry |
| 14 | ई - मेल | E-mail | Textbox | No | Manual entry |
| 15 | संपर्क व कायमचा पत्ते सारखेच आहेत | Contact Same as Permanent | Checkbox | No | — |

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
