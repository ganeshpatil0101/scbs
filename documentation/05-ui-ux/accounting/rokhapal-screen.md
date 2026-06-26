# Screen Spec — Rokhapal / Cashier (लेखा > रोखपाल)

## Purpose

UI specification for cashier transactions with denomination tracking.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | रोखपाल | Cashier |
| Breadcrumb | डॅशबोर्ड > लेखा > रोखपाल | Dashboard > Accounting > Cashier |
| Parent Module | लेखा | Accounting |

## Reference Media

| File | Section |
| :--- | :--- |
| `screenshots/lekha/डॅशबोर्ड-लेखा-रोखपाल.mp4` | Full screen |

Extracted frames: `screenshots/lekha/rokhapal-frames/`.

---

## Section: व्यवहार (Transaction)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | व्यवहार प्रकार | Transaction Type | Radio | No | `नावे` (Debit) / `जमा` (Credit). Default: `जमा` |
| 2 | व्हाउचर क्र. | Voucher No. | Textbox | No | — |
| 3 | अपूर्ण स्क्रोल निवडा | Select Incomplete Scroll | Dropdown | No | `TODO` |
| 4 | शाखा क्र. | Branch No. | Textbox | Yes | e.g. `1` |
| 5 | शाखा निवडा | Select Branch | Dropdown | Yes | — |
| 6 | जि.एल.क्र. | GL No. | Textbox | Yes | — |
| 7 | जि.एल.निवडा | Select GL | Dropdown | No | `TODO` |
| 8 | खाते क्र. | Account No. | Textbox | Yes | — |
| 9 | खातेदार निवडा | Select Account Holder | Dropdown | Yes | `TODO` |
| 10 | शिल्लक | Balance | Textbox | No | Read-only |
| 11 | पॅनकार्ड - आधार क्र. | PAN - Aadhaar No. | Textbox | No | — |
| 12 | रक्कम (रु.) | Amount (Rs.) | Textbox | Yes | — |
| 13 | अक्षरी रक्कम | Amount in Words | Textbox | No | Read-only |
| 14 | दंडाची रक्कम (रु.) | Penalty Amount (Rs.) | Textbox | No | — |
| 15 | विशेष सुचना | Special Instructions | Textbox | No | — |
| 16 | रोखपाल तपशिल | Cashier Details | Textbox | No | — |
| 17 | स्क्रोल | Scroll | Textbox | No | e.g. `20` |

## Section: नोटांचा तपशिल (Denomination Details)

Section header visible; denomination grid fields: `TODO` (not captured in opening frame).

## Transaction History Filter

| # | Marathi Label | English Label | Type | Values / Notes |
| :---: | :--- | :--- | :--- | :--- |
| 18 | Filter | Last / Debit / All / Credit transactions | Radio | `शेवटचा व्यवहार`, `नावे व्यवहार`, `सर्व व्यवहार`, `जमा व्यवहार` |

**Action:** `दाखवा` (Show). **Footer:** `पूर्ण`, `पुनर्वत`.

---

## Related Documents

- [overview.md](overview.md)
- [note-exchange-screen.md](note-exchange-screen.md)
