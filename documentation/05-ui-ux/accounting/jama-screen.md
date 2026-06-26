# Screen Spec — Jama / Credit (लेखा > जमा)

## Purpose

UI specification for accounting credit (receipt) entries.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | जमा | Credit / Receipt |
| Breadcrumb | डॅशबोर्ड > लेखा > जमा | Dashboard > Accounting > Credit |
| Parent Module | लेखा | Accounting |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | पावती | Receipt |
| 2 | साहित्य तपशील | Instrument Details |

## Reference Media

| File | Section |
| :--- | :--- |
| `screenshots/lekha/डॅशबोर्ड-लेखा-जमा.mp4` | Tab 1 — Receipt |

Extracted frames: `screenshots/lekha/jama-frames/`.

**Warning label:** `कृपया या पृष्ठावर व्याज (ठेव\कर्ज) व्यवहार टाळा` (Avoid interest deposit/loan transactions on this page).

---

## Tab 1: पावती (Receipt)

### General

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | चलन क्रमांक | Challan Number | Textbox | Yes | Read-only; e.g. `42` |
| 2 | रोख / बँक | Cash / Bank | Radio | No | Default: `रोख` |
| 3 | बँक / रोख रक्कम निवडा | Select Bank / Cash Amount | Dropdown | Yes | e.g. `रोख शिल्लक` (Cash Balance). Other values: `TODO` |
| 4 | शिल्लक (नावे) | Balance (Debit) | Textbox | No | Read-only |
| 5 | तपशील | Details / Narration | Textarea | No | — |
| 6 | शुल्क गणना | Fee Calculation | Link | No | — |

### Section: जमा होणारे खाते (Account to be Credited)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 7 | शाखा कोड | Branch Code | Textbox | Yes | Read-only |
| 8 | शाखा निवडा | Select Branch | Dropdown | Yes | — |
| 9 | जी.एल.हेड.क्र. | GL Head No. | Textbox | Yes | — |
| 10 | जी.एल.निवडा | Select GL | Textbox | No | — |
| 11 | खाते क्र. | Account No. | Textbox | Yes | — |
| 12 | खातेधारक शोधा | Search Account Holder | Textbox | Yes | — |
| 13 | खातेधारक निवडा | Select Account Holder | Dropdown | Yes | `TODO` |
| 14 | शिल्लक | Balance | Textbox | No | Read-only |
| 15 | न वटलेली शिल्लक | Uncleared Balance | Textbox | No | Read-only |

### Section: व्यवहार (Transaction)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 16 | जमा / नावे | Credit / Debit | Radio | Yes | Default: `जमा` |
| 17 | व्यवहार रक्कम (रु.) | Transaction Amount (Rs.) | Textbox | Yes | — |

**Action:** `जमा ₹` — add row to grid.

### Entry Grid

Columns: निवडा, अनु. क्र, जी.एल. हेड, खाते क्रमांक, खातेधारक, शिल्लक, व्यवहार रक्कम.

**Footer:** `अक्षरी रक्कम`, `एकूण … जमा`. **Actions:** `हटवा`, `पुढे`, `वर`.

---

## Related Documents

- [overview.md](overview.md)
- [nave-screen.md](nave-screen.md)
- [transfer-screen.md](transfer-screen.md)
