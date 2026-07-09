# Screen Spec — New Customer (ग्राहक > नवीन ग्राहक)

## Purpose

UI specification for registering a new customer. Three-tab wizard. Intended for AI agents implementing this screen.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | नवीन ग्राहक | New Customer |
| Breadcrumb | डॅशबोर्ड > ग्राहक > नवीन ग्राहक | Dashboard > Customer > New Customer |
| Parent Module | ग्राहक | Customer |

**Auto-fill (header):** `संस्था` (Organization) — read-only `Label` from tenant session.

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | ग्राहक तपशील | Customer Details |
| 2 | पत्ता | Address |
| 3 | केवायसी कागदपत्रे | KYC Documents |

## Reference Media

| File | Tab / Section |
| :--- | :--- |
| `screenshots/grahak_khatedar/डॅशबोर्ड-ग्राहक-नवीन ग्राहक-1.mp4` | Tab 1 — Customer Details (scroll + dropdowns) |
| `screenshots/grahak_khatedar/डॅशबोर्ड-ग्राहक-नवीन ग्राहक-2.mp4` | Tab 2 — Address |
| `screenshots/grahak_khatedar/डॅशबोर्ड-ग्राहक-नवीन ग्राहक-3.png` | Tab 3 — KYC Documents |

Extracted frames: `screenshots/grahak_khatedar/new-customer-1-frames/`, `new-customer-2-frames/`.

---

## Tab 1: ग्राहक तपशील (Customer Details)

### Top Field

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | ग्राहक प्रकार | Customer Type | Dropdown | No | `वैयक्तिक` (Individual), `मालमत्ता फर्म` (Proprietorship Firm), `एसजी` (Self Help Group), `दुसरी संस्था` (Other Institution) |

### Section: ग्राहक माहिती (Customer Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 2 | पॅन | PAN | Textbox | No | Phase 1: textbox only. `ई-पडताळणी` deferred to a later phase |
| 3 | आधार क्र. | Aadhaar No. | Textbox | No | Phase 1: textbox only. `ई-पडताळणी` deferred to a later phase |
| 4 | ग्राहक क्र. | Customer No. | Label | Yes | Auto-generated; read-only (e.g. `661`) |
| 5 | शाखा निवडा | Select Branch | Autocomplete | Yes | Editable; admin may pick another branch. Enter resolves by ID or name; e.g. `1 — Branch 1`. Default: logged-in branch |
| 6 | श्री. / सौ. | Salutation | Dropdown | No | Default: `श्री.`. Values: `श्री.`, `सौ.`, `श्रीमती`, `कुमारी.`, `चि.`, `मेसर्स`, blank. **Layout:** same row as Name (#7) |
| 7 | नाव (आडनाव - पहिले नाव - मधले नाव) | Name (Surname - First - Middle) | Textbox | Yes | Same row as Salutation (#6) |
| 8 | जन्म दिनांक | Date of Birth | Date | Yes | — |
| 9 | वय (वर्षे) | Age (Years) | Label | No | Auto-calculated from DOB |
| 10 | वय (महिने) | Age (Months) | Label | No | Read-only |
| 11 | व्यवसाय | Occupation | Dropdown | No | Default: `एन/ए` (N/A). Has `+` add button. Values: `एन/ए`, `पेन्शनर(निवृत्त)`, `गृहिणी`, `नोकर`, `शेती`, `व्यवसाय`, `शिक्षण`, `शिक्षक`, `डॉक्टर`, `इतर` |
| 12 | ग्राहक झाल्याची दिनांक | Customer Since Date | Label | No | Auto-fill; system date |
| 13 | स्थिती | Status | Dropdown | No | Default: `चालू` (Active). Values: `चालू`, `बंद`, `स्थगित`, `मृत`, `निलंबित`, `निवृत्त`, `वैद्यकीय`, `काढला` |
| 14 | देहावसान तारीख | Date of Death | Date | No | **Visible only when Status = `मृत`**. Hidden otherwise |

### Section: प्रगत सेटिंग्ज (Advanced Settings)

> Collapsed by default. Visible to users with accounting/admin role or when expanded manually.

| # | Marathi Label | English Label | Type | Required | Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 15 | शिक्षण | Education | Textbox | No | — |
| 16 | वडिलांचे नाव | Father's Name | Textbox | No | — |
| 17 | आईचे नाव | Mother's Name | Textbox | No | — |
| 18 | जोडीदाराचे नाव | Spouse's Name | Textbox | No | — |
| 19 | एसएमएस अलर्ट सक्रिय करा | Activate SMS Alert | Checkbox | No | — |
| 20 | व्हॉट्सॲप अलर्ट सक्रिय करा | Activate WhatsApp Alert | Checkbox | No | — |
| 21 | ईमेल अलर्ट सक्रिय करा | Activate Email Alert | Checkbox | No | — |
| 22 | वारसदार टाका | Add Nominee | Checkbox | No | When checked, show **वारसदार माहिती** form below (fields 23–29) |

### Section: वारसदार माहिती (Nominee Information)

> **Visible only when** `वारसदार टाका` (#22) is checked. Hidden otherwise. Compact subset for New Customer; full nominee grids remain on product account-opening screens (`app-nominee-form` pattern).

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 23 | श्री. / सौ. | Salutation | Dropdown | Yes | Same values as customer salutation (#6). Same row as Name (#24) |
| 24 | नाव (आडनाव - पहिले नाव - मधले नाव) | Name (Surname - First - Middle) | Textbox | Yes | Same row as Salutation (#23) |
| 25 | जन्म दिनांक | Date of Birth | Date | No | — |
| 26 | नाते | Relation | Dropdown | Yes | `मुलगा`, `मुली`, `पत्नी`, `पती`, `पुतण्या`, `लहान भाऊ`, `बायको`, `मैत्रीण`, `केअरटेकर`, `स्वतः`, `वरील प्रमाणे` — same list as [new-membership-screen.md](../membership/new-membership-screen.md) Tab 3 |
| 27 | मोबाईल क्रमांक | Mobile Number | Textbox | No | — |
| 28 | वारसदार टक्केवारी | Nominee Percentage | Textbox | No | — |
| 29 | पत्ता | Address | Textbox | No | Single-line address for phase 1 |

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

### Pattern: Document cards (Option A)

One **card per document** — upload on the card itself. No results grid, no row checkboxes, no shared footer file picker.

**Layout:** 2-column card grid on desktop (`≥640px`); single column on mobile.

### Card contents (each document)

| Element | Marathi | Behaviour |
| :--- | :--- | :--- |
| Title | Document name | e.g. `फोटो` |
| Mandatory badge | `आवश्यक` / `पर्यायी` | Red-tint for required; muted for optional |
| Document number | `दस्तावेज क्रमांक` | **Only** on Address Proof and Identity Proof. Hidden on Photo, Signature, Original Aadhaar Photo |
| File control | `फाईल निवडा` | Native file input on the card |
| Status | `अपलोड करा` / `अपलोड झाले` + file name | Updates after file selected (layout mockup may simulate) |
| View | `पहा` | Enabled only when a file is present; otherwise hidden/disabled |
| Remove | `काढा` | Clears file for that card only |

### Documents

| # | Marathi | English | Mandatory | Document number field |
| :---: | :--- | :--- | :---: | :--- |
| 1 | फोटो | Photo | Yes | No |
| 2 | सही | Signature | Yes | No |
| 3 | पत्ता पुरावा | Address Proof | Yes | Yes |
| 4 | ओळख पुरावा | Identity Proof | Yes | Yes |
| 5 | मूळ आधार फोटो | Original Aadhaar Photo | No | No |

**Progress hint (optional UI):** e.g. `आवश्यक: 0/4 पूर्ण` — count of mandatory cards with a file.

**Screen footer:** `पूर्ण` (Complete/Save), `पूर्ववत` / `रीसेट` (Reset) — same wizard footer as other tabs.

---

## Mockup

| Property | Value |
| :--- | :--- |
| HTML mockup | [mockups/customer/new-customer-screen/index.html](../mockups/customer/new-customer-screen/index.html) |
| Review guide | [mockups/customer/new-customer-screen/README.md](../mockups/customer/new-customer-screen/README.md) |
| Stack | Tailwind CSS v4 (CDN), Marathi labels only |
| Status | Draft — pending bank user review |

---

## Related Documents

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [customer-list-screen.md](customer-list-screen.md)
- [other-account-management-screen.md](other-account-management-screen.md)
- [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
- [../membership/new-membership-screen.md](../membership/new-membership-screen.md)
