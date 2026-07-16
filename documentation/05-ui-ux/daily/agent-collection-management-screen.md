# Screen Spec — Agent Collection Management (डेली > एजंट > एजंट कलेक्शन व्यवस्थापन)

> **Consolidates:** [agent-collection-screen.md](agent-collection-screen.md) + [agent-collection-list-screen.md](agent-collection-list-screen.md)

## Purpose

Single screen for recording new daily agent collections and viewing historical collection records. Tab 1 captures collections against member accounts; Tab 2 lists and exports past collections.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | एजंट कलेक्शन व्यवस्थापन | Agent Collection Management |
| Breadcrumb | डॅशबोर्ड > डेली > एजंट > एजंट कलेक्शन व्यवस्थापन | Dashboard > Daily > Agent > Agent Collection Management |
| Parent Module | डेली | Daily |

## Tabs

| # | Marathi Tab | English Tab | Replaces |
| :---: | :--- | :--- | :--- |
| 1 | नवीन कलेक्शन | New Collection | Agent Collection |
| 2 | कलेक्शन यादी | Collection List | Agent Collection List |

## Reference Screenshots

| File | Tab |
| :--- | :--- |
| `screenshots/डेली/डॅशबोर्ड_डेली _एजंट_एजंट कलेक्शन.png` | Tab 1 |
| `screenshots/डेली/डॅशबोर्ड_डेली_एजंट_एजंट कलेक्शन यादी.png` | Tab 2 |

---

## Tab 1: नवीन कलेक्शन (New Collection)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | चलन क्रमांक | Challan Number | Label (read-only) | No | Auto-generated; e.g. `42` |
| 2 | रोख / ट्रान्सफर | Cash / Transfer | Radio | Yes | — |
| 3 | शाखा निवडा | Select Branch | Autocomplete | No | Default: logged-in branch. Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 4 | एजंट निवडा | Select Agent | Autocomplete | Yes | Replaces `प्रतिनिधी क्र.` + `शोध एजंट नाव`. Sample: `1 — Agent 1`, `2 — Agent 2`. Enter resolves by ID or name; shows display name. See [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |
| 5 | कलेक्शन रक्कम (रु.) | Collection Amount (Rs.) | Textbox | Yes | — |
| 6 | एक दिवसीय / अनेक दिवस | One Day / Multiple Days | Radio | Yes | — |
| 7 | कलेक्शन दिनांक (पासून) | Collection Date (From) | Date | Yes | — |
| 8 | योजना निवडा | Select Scheme | Dropdown | No | Loaded dynamically from Daily schemes (Settings > नवीन योजना). Sample: `डेली १`, `डेली २`, `पिग्मी ठेव` |
| 9 | खाते क्रमांक (पासून) | Account No. (From) | Textbox | No | — |
| 10 | खाते क्रमांक (पर्यंत) | Account No. (To) | Textbox | No | — |
| 11 | मार्क पावती क्रमांक | Mark Receipt Number | Checkbox | No | — |
| 12 | खाते क्रमांक नुसार / लेजर फोलिओ क्रमांक नुसार | By Account No. / By L.F. No. | Radio | No | — |

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

> **Legacy wizard tabs (not captured):** Original Agent Collection screen had Tab 2 `संक्षिप्त तपशील` (Brief Details) and Tab 3 `ट्रान्स्फर` (Transfer) as post-grid steps. These are **not** the same as [Agent to Agent Transfer](agent-to-agent-transfer-screen.md). `TODO — not captured` until screenshots/MP4 available.

---

## Tab 2: कलेक्शन यादी (Collection List)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा निवडा | Select Branch | Autocomplete | Yes | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 2 | एजंट निवडा | Select Agent | Autocomplete | Yes | Replaces `एजंट क्रमांक` + `शोध एजंट नाव`. Sample: `1 — Agent 1`. Enter resolves by ID or name |
| 3 | योजना निवडा | Select Scheme | Dropdown | No | Loaded dynamically from Daily schemes (Settings > नवीन योजना). Sample: `डेली १`, `डेली २`, `पिग्मी ठेव` |
| 4 | व्यवहार दिनांक पासून | Transaction Date From | Date | No | — |
| 5 | व्यवहार दिनांक पर्यंत | Transaction Date To | Date | No | — |

**Action:** `दाखवा` (Show).

### Results Grid

**Select all:** `सर्व निवडा`.

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | अनु. क्र. | Sr. No. |
| 3 | एजंटचे नाव | Agent Name |
| 4 | व्यवहार दिनांक | Transaction Date |
| 5 | कलेक्शन रक्कम | Collection Amount |

**Sidebar actions:** `तपशील` (Details), `निर्यात करा` (Export).

**Footer:** एकूण (total collection amount).

---

## Mockup

- [HTML mockup (Draft)](../mockups/daily/agent-collection-management-screen/) — Marathi layout for bank review

---

## Cross-Links

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [new-agent-screen.md](new-agent-screen.md)
- [agent-to-agent-transfer-screen.md](agent-to-agent-transfer-screen.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
