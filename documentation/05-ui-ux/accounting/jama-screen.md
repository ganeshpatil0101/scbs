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
| 2 | रोख / बँक | Cash / Bank | Radio | No | Default: `रोख`. Controls Tab 2 enable/disable — see **Cross-Tab Behavior** below |
| 3 | बँक / रोख रक्कम निवडा | Select Bank / Cash Amount | Dropdown | Yes | **When `रोख`:** `रोख शिल्लक` (Cash Balance). **When `बँक`:** loaded from Bank Master — `SBI`, `HDFC`, `ICICI`, `Bank of Maharashtra`, `Other` |
| 4 | शिल्लक (नावे) | Balance (Debit) | Textbox | No | Read-only |
| 5 | तपशील | Details / Narration | Textarea | No | — |
| 6 | शुल्क गणना | Fee Calculation | Link | No | — |

### Section: जमा होणारे खाते (Account to be Credited)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 7 | शाखा निवडा | Select Branch | Autocomplete | Yes | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 8 | जी.एल. निवडा | Select GL | Autocomplete | Yes | Sample: `38 — Saving`, `91 — FD`, `42 — Loan`. Enter resolves by ID or name; shows display name |
| 9 | खातेधारक निवडा | Select Account Holder | Autocomplete | Yes | Sample: `101 — Account Holder 1`, `102 — Account Holder 2`, `103 — Account Holder 3`. Enter resolves by ID or name; shows display name |
| 10 | शिल्लक | Balance | Textbox | No | Read-only |
| 11 | न वटलेली शिल्लक | Uncleared Balance | Textbox | No | Read-only |

### Section: व्यवहार (Transaction)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 12 | जमा / नावे | Credit / Debit | Radio | Yes | Default: `जमा` |
| 13 | व्यवहार रक्कम (रु.) | Transaction Amount (Rs.) | Textbox | Yes | — |

**Action:** `जमा ₹` — add row to grid.

### Entry Grid

Columns: निवडा, अनु. क्र, जी.एल. हेड, खाते क्रमांक, खातेधारक, शिल्लक, व्यवहार रक्कम.

**Footer:** `अक्षरी रक्कम`, `एकूण … जमा`. **Actions:** `हटवा`, `पुढे`, `वर`.

---

## Cross-Tab Behavior

| Tab 1 — `रोख / बँक` (field 2) | Tab 2 — साहित्य तपशील |
| :--- | :--- |
| `रोख` (Cash) selected | All Tab 2 fields **disabled** |
| `बँक` (Bank) selected | All Tab 2 fields **enabled** |

Tab 2 is only meaningful for bank (instrument) receipts; cash receipts skip instrument capture.

---

## Tab 2: साहित्य तपशील (Instrument Details)

Enabled only when Tab 1 field 2 = `बँक`. All fields disabled when Tab 1 field 2 = `रोख`.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 14 | धनादेश प्रकार निवडा | Select Cheque Type | Dropdown | No | `स्लिप` (Slip) |
| 15 | चेक रक्कम (रु.) | Cheque Amount (Rs.) | Textbox | No | Read-only |
| 16 | रक्कम अक्षरी | Amount in Words | Textbox | No | Read-only |
| 17 | चेक दिनांक | Cheque Date | Date | Yes | — |
| 18 | चेक क्र. | Cheque No. | Textbox | Yes | — |
| 19 | नाव | Name | Textbox | Yes | — |
| 20 | बँक निवडा | Select Bank | Dropdown | Yes | `SBI`, `HDFC`, `ICICI`, `Bank of Maharashtra`, `Other` |
| 21 | बँक शाखा | Bank Branch | Textbox | No | — |
| 22 | ड्रॉन ऑन बँक | Drawn on Bank | Textbox | No | — |
| 23 | ड्रॉन ऑन ब्रांच | Drawn on Branch | Textbox | No | — |
| 24 | अंतर्गत चेक नंबर | Internal Cheque Number | Textbox | No | Read-only |

**Navigation:** `मागे`, `पुढे`, `पूर्ण`, `पूर्ववत`.

---

## Mockup

| Property | Value |
| :--- | :--- |
| HTML mockup | [mockups/accounting/jama-screen/index.html](../mockups/accounting/jama-screen/index.html) |
| Review guide | [mockups/accounting/jama-screen/README.md](../mockups/accounting/jama-screen/README.md) |
| Status | Draft |

## Related Documents

- [overview.md](overview.md)
- [nave-screen.md](nave-screen.md)
- [transfer-screen.md](transfer-screen.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
