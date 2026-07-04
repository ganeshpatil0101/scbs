# Screen Spec — Agent Collection (डेली > एजंट > एजंट कलेक्शन)

## Purpose

UI specification for recording daily agent collections against member accounts.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | एजंट कलेक्शन | Agent Collection |
| Breadcrumb | डॅशबोर्ड > डेली > एजंट > एजंट कलेक्शन | Dashboard > Daily > Agent > Agent Collection |
| Parent Module | डेली | Daily |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | एजंट संकलन | Agent Collection |
| 2 | संक्षिप्त तपशील | Brief Details |
| 3 | ट्रान्स्फर | Transfer |

## Reference Screenshots

| File | Tab |
| :--- | :--- |
| `screenshots/डेली/डॅशबोर्ड_डेली _एजंट_एजंट कलेक्शन.png` | Tab 1 |

---

## Tab 1: एजंट संकलन (Agent Collection)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | चलन क्रमांक | Challan Number | Textbox | No | Read-only; e.g. `42` |
| 2 | रोख / ट्रान्सफर | Cash / Transfer | Radio | Yes | — |
| 3 | शाखा निवडा | Select Branch | Autocomplete | No | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 4 | प्रतिनिधी क्र. | Representative No. | Textbox | Yes | — |
| 5 | शोध एजंट नाव | Search Agent Name | Textbox | Yes | — |
| 6 | कलेक्शन रक्कम (रु.) | Collection Amount (Rs.) | Textbox | Yes | — |
| 7 | एक दिवसीय / अनेक दिवस | One Day / Multiple Days | Radio | Yes | — |
| 8 | कलेक्शन दिनांक (पासून) | Collection Date (From) | Date | Yes | — |
| 9 | योजना निवडा | Select Scheme | Dropdown | No | Loaded dynamically from Daily schemes (Settings > नवीन योजना). Sample: `डेली १`, `डेली २`, `पिग्मी ठेव` |
| 10 | खाते क्रमांक (पासून) | Account No. (From) | Textbox | No | — |
| 11 | खाते क्रमांक (पर्यंत) | Account No. (To) | Textbox | No | — |
| 12 | मार्क पावती क्रमांक | Mark Receipt Number | Checkbox | No | — |
| 13 | खाते क्रमांक नुसार / लेजर फोलिओ क्रमांक नुसार | By Account No. / By L.F. No. | Radio | No | — |

**Action:** `बघा` (View) — loads collection grid.

### Collection Grid Columns

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | अनु. क्र. | Sr. No. |
| 3 | खात्याचे नाव | Account Name |
| 4 | खाते क्रमांक | Account Number |
| 5 | खातेधारक | Account Holder |
| 6 | शिल्लक | Balance |
| 7–16 | १ ला दिवस … १० वा दिवस | Day 1 … Day 10 |
| 17 | एकूण | Total |
| 18 | एल. एफ. क्रमांक | L.F. Number |
| 19 | आर डी दंड | RD Penalty |
| 20 | आर डी सवलत | RD Discount |
| 21 | एजंट कमिशन | Agent Commission |
| 22 | एजंट कमिशन रेट | Agent Commission Rate |
| 23 | हप्ता संख्या | Installment Count |
| 24 | चालू दिनांक | Current Date |

**Select all:** `सर्व निवडा`.

**Actions:** `निर्मीती करा` (Create), `रक्कम शुन्यवर सेट करा` (Set Amount to Zero).

**Footer summary:** एकूण रक्कम, एकूण एजंट कमिशन, एकूण निवडलेल्या नोंदी.

Tabs 2–3: `TODO` — not captured.

---

## Cross-Links

- [overview.md](overview.md)
- [new-agent-screen.md](new-agent-screen.md)
- [agent-collection-list-screen.md](agent-collection-list-screen.md)
