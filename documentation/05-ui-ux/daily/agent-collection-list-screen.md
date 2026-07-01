# Screen Spec — Agent Collection List (डेली > एजंट > एजंट कलेक्शन यादी)

## Purpose

UI specification for viewing and exporting historical agent collection records.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | एजंट कलेक्शन यादी | Agent Collection List |
| Breadcrumb | डॅशबोर्ड > डेली > एजंट > एजंट कलेक्शन यादी | Dashboard > Daily > Agent > Agent Collection List |
| Parent Module | डेली | Daily |

## Reference Screenshots

| File | Section |
| :--- | :--- |
| `screenshots/डेली/डॅशबोर्ड_डेली_एजंट_एजंट कलेक्शन यादी.png` | Full screen |

---

## Filter Section

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा निवडा | Select Branch | Autocomplete | Yes | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 2 | एजंट क्रमांक | Agent Number | Textbox | Yes | — |
| 3 | शोध एजंट नाव | Search Agent Name | Textbox | Yes | — |
| 4 | योजना निवडा | Select Scheme | Dropdown | No | Values: `TODO` |
| 5 | व्यवहार दिनांक पासून | Transaction Date From | Date | No | — |
| 6 | व्यवहार दिनांक पर्यंत | Transaction Date To | Date | No | — |

**Action:** `दाखवा` (Show).

---

## Results Grid

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

## Cross-Links

- [overview.md](overview.md)
- [agent-collection-screen.md](agent-collection-screen.md)
