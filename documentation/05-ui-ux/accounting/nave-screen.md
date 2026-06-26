# Screen Spec — Nave / Debit (लेखा > नावे)

## Purpose

UI specification for accounting debit (payment) entries.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | नावे | Debit / Payment |
| Breadcrumb | डॅशबोर्ड > लेखा > नावे | Dashboard > Accounting > Debit |
| Parent Module | लेखा | Accounting |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | पेमेंट | Payment |
| 2 | चेक माहिती | Cheque Information |

## Reference Media

| File | Section |
| :--- | :--- |
| `screenshots/lekha/डॅशबोर्ड-लेखा-नावे.mp4` | Tab 1 — Payment |

Extracted frames: `screenshots/lekha/nave-frames/`.

Same interest-transaction warning as [jama-screen.md](jama-screen.md).

---

## Tab 1: पेमेंट (Payment)

### Payment Source

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | व्हाउचर क्र. | Voucher No. | Textbox | No | Read-only; e.g. `42` |
| 2 | रोख / बँक | Cash / Bank | Radio | No | Default: `रोख` |
| 3 | बँक/कॅश निवडा | Select Bank/Cash | Dropdown | Yes | e.g. `रोख शिल्लक` |
| 4 | शिल्लक (नावे) | Balance (Debit) | Textbox | No | Read-only |
| 5 | तपशील | Details | Textbox | No | — |

### Section: नावे होणारी खाती (Accounts to be Debited)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 6 | शाखा कोड | Branch Code | Textbox | Yes | — |
| 7 | शाखा निवडा | Select Branch | Dropdown | Yes | — |
| 8 | जी.एल.हेड.क्र. | GL Head No. | Textbox | Yes | — |
| 9 | जी.एल.निवडा | Select GL | Textbox | No | — |
| 10 | खाते क्र. | Account No. | Textbox | Yes | — |
| 11 | खातेधारक शोधा | Search Account Holder | Textbox | Yes | — |
| 12 | खातेधारक निवडा | Select Account Holder | Dropdown | Yes | `TODO` |
| 13 | शिल्लक | Balance | Textbox | No | Read-only |
| 14 | न वाटलेली शिल्लक | Uncleared Balance | Textbox | No | Read-only |

### Section: व्यवहार (Transaction)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 15 | नावे / जमा | Debit / Credit | Radio | Yes | Default: `नावे` |
| 16 | व्यवहार रक्कम (रु.) | Transaction Amount (Rs.) | Textbox | Yes | — |

**Action:** `नावे` — add to grid. **Grid actions:** `निर्यात`, `काढा`, `वर`.

Tab 2: `TODO`.

---

## Related Documents

- [overview.md](overview.md)
- [jama-screen.md](jama-screen.md)
