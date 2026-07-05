# Screen Spec — Contra (लेखा > कॉन्ट्रा)

## Purpose

UI specification for contra (cash/bank offset) transactions — multi-line debit/credit entry with optional instrument and NEFT/RTGS details.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | कॉन्ट्रा | Contra |
| Breadcrumb | डॅशबोर्ड > लेखा > कॉन्ट्रा | Dashboard > Accounting > Contra |
| Parent Module | लेखा | Accounting |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | कॅश व्यवहार | Cash Transaction |
| 2 | साहित्य तपशील | Instrument Details |

## Reference Screenshots

| File | Tab |
| :--- | :--- |
| `screenshots/lekha/डॅशबोर्ड-लेखा-कॉन्ट्रा-1-05-07.png` | Tab 1 |
| `screenshots/lekha/डॅशबोर्ड-लेखा-कॉन्ट्रा-2-05-07.png` | Tab 2 |

---

## Tab 1: कॅश व्यवहार (Cash Transaction)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | चलन क्रमांक | Challan Number | Textbox | No | Read-only; e.g. `1` |
| 2 | कॅश / रोख रक्कम निवडा | Select Cash / Cash Amount | Dropdown | Yes | e.g. `रोख` (Cash) |
| 3 | किल्लक (नावे) | Balance (Debit) | Textbox | No | Read-only |
| 4 | तपशील | Details | Textbox | No | — |
| 5 | शाखा कोड | Branch Code | Textbox | Yes | e.g. `1` |
| 6 | शाखा निवडा | Select Branch | Dropdown | Yes | e.g. `कोतोली मुख्य कार्यालय` |
| 7 | जी. एल. क्र. | G.L. No. | Textbox | Yes | — |
| 8 | जी. एल. निवडा | Select G.L. | Dropdown | Yes | — |
| 9 | खाते क्र. | Account No. | Textbox | No | — |
| 10 | खातेदार | Account Holder | Dropdown | Yes | — |
| 11 | शिल्लक | Balance | Textbox | No | Read-only |
| 12 | व्यवहार रक्कम (रुपये मध्ये) | Transaction Amount (Rs.) | Textbox | Yes | — |
| 13 | व्यवहार प्रकार | Transaction Type | Radio | Yes | `जमा` (Credit), `नावे` (Debit) |

**Action:** `जमा` / `नावे` (Add row to grid).

**Entry grid columns:** निवडा, अनु. क्र., जी. एल. हेड, खाते क्रमांक, खातेदार, शिल्लक, व्यवहार रक्कम.

**Grid action:** `वगळा` (Remove).

**Summary:** `अक्षरी रक्कम`, `एकूण` (Total credit/debit).

**Navigation:** `पुढे`. **Actions:** `पूर्ण`, `पूर्ववत`.

---

## Tab 2: साहित्य तपशील (Instrument Details)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | धनादेश प्रकार निवडा | Select Cheque Type | Dropdown | No | e.g. `चेक` (Cheque). Other values: `TODO` |
| 2 | चेक रक्कम (रु.) | Cheque Amount (Rs.) | Textbox | No | — |
| 3 | रक्कम अक्षरी | Amount in Words | Textbox | No | Read-only |
| 4 | चेक दिनांक | Cheque Date | Date | Yes | — |
| 5 | चेक क्र. | Cheque No. | Textbox | Yes | — |
| 6 | नाव | Name | Textbox | Yes | — |
| 7 | बँक निवडा | Select Bank | Dropdown | Yes | Loaded from Bank Master — `SBI`, `HDFC`, `ICICI`, `Bank of Maharashtra`, `Other` |
| 8 | बँक शाखा | Bank Branch | Textbox | No | — |
| 9 | ड्रॉन ऑन बँक | Drawn on Bank | Textbox | No | — |
| 10 | ड्रॉन ऑन ब्रांच | Drawn on Branch | Textbox | No | — |
| 11 | एनईएफटी/आरटीजीएस | NEFT/RTGS | Checkbox | No | Enables fields 12–16 |
| 12 | हस्तांतरण प्रकार | Transfer Type | Radio | No | When field 11 checked: `एनईएफटी`, `आरटीजीएस`, `एनईएफटी/आरटीजीएस` |
| 13 | बँक | Bank | Textbox | Yes | When NEFT/RTGS enabled |
| 14 | बँक शाखा | Bank Branch | Textbox | Yes | When NEFT/RTGS enabled |
| 15 | आयएफएससी कोड | IFSC Code | Textbox | Yes | When NEFT/RTGS enabled |
| 16 | खाते क्रमांक | Account Number | Textbox | Yes | When NEFT/RTGS enabled |

**Navigation:** `मागे`. **Actions:** `पूर्ण`, `पूर्ववत`.

---

## Related Documents

- [overview.md](overview.md)
- [jama-screen.md](jama-screen.md)
- [transfer-screen.md](transfer-screen.md)
