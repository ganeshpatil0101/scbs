# Screen Spec — Multiple GL Transaction (लेखा > एकाधिक जीएल व्यवहार)

## Purpose

UI specification for posting transactions across multiple GL heads in one voucher.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | एकाधिक जीएल व्यवहार | Multiple GL Transaction |
| Breadcrumb | डॅशबोर्ड > लेखा > एकाधिक जीएल व्यवहार | Dashboard > Accounting > Multiple GL Transaction |
| Parent Module | लेखा | Accounting |

## Reference Media

| File | Section |
| :--- | :--- |
| `screenshots/lekha/डॅशबोर्ड-लेखा-एकाधिक जीएल व्यवहार.mp4` | Entry + current transaction grid |

Extracted frames: `screenshots/lekha/multi-gl-frames/`.

---

## Account Lookup

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा कोड | Branch Code | Textbox | No | Read-only |
| 2 | शाखा निवडा | Select Branch | Dropdown | No | — |
| 3 | जी.एल. हेड शोधा | Search GL Head | Textbox | No | — |
| 4 | जी.एल. हेड नं. | GL Head No. | Textbox | No | — |
| 5 | खाते धारक शोधा | Search Account Holder | Textbox | No | — |
| 6 | खाते क्र. | Account No. | Textbox | No | — |
| 7 | खाते धारक निवडा | Select Account Holder | Dropdown | No | `TODO` |
| 8 | न वटलेली शिल्लक | Uncleared Balance | Textbox | No | Read-only |
| 9 | लेजर शिल्लक | Ledger Balance | Label | No | — |
| 10 | अक्षरी रक्कम | Amount in Words | Textbox | No | Read-only |

**Utility buttons:** `खाते माहिती`, `खात्याचा हिशोब`, `पासबुक`, `चौकशी`.

## Transaction Entry

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 11 | व्यवहार प्रकार | Transaction Type | Radio | No | `नावे` (Debit) / `जमा` (Credit) |
| 12 | रक्कम रु. | Amount (Rs.) | Textbox | Yes | — |

**Action:** `+ भरा` (Fill/Add).

## Current Transaction Grid (करंट ट्रांझॅक्शन)

Columns: निवडा, अनु. क्र, जी.एल. हेड, खाते क्रमांक, खातेधारक, शिल्लक, नावे, जमा.

**Footer fields:** `एकूण नावे`, `एकूण जमा`, `फरक रक्कम`, `व्यवहार मोड` (dropdown, required), `व्हाउचर तपशील` (textarea).

**Links:** `केवायसी माहिती खात्याचा तपशील`, `व्यवहार तपशील`, `लेजर`.

**Actions:** `काढा`, `पूर्ण`, `पूर्ववत`, `वर`.

---

## Related Documents

- [overview.md](overview.md)
- [jama-screen.md](jama-screen.md)
- [nave-screen.md](nave-screen.md)
