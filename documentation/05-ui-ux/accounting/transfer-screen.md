# Screen Spec — Accounting Transfer (लेखा > ट्रान्सफर)

## Purpose

UI specification for GL account-to-account transfer (debit one side, credit other).

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | ट्रान्सफर | Transfer |
| Breadcrumb | डॅशबोर्ड > लेखा > ट्रान्सफर | Dashboard > Accounting > Transfer |
| Parent Module | लेखा | Accounting |

## Reference Media

| File | Section |
| :--- | :--- |
| `screenshots/lekha/डॅशबोर्ड-लेखा-ट्रान्सफर.mp4` | Full screen |

Extracted frames: `screenshots/lekha/transfer-frames/`.

---

## Section: खाते व्यवहार (Account Transaction)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | चलन क्रमांक | Challan Number | Textbox | No | Read-only |

## Section: नावे खाते (Debit Account)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 2 | शाखा कोड | Branch Code | Textbox | Yes | Read-only |
| 3 | शाखा निवडा | Select Branch | Dropdown | Yes | — |
| 4 | जी.एल.हेड.क्र. | GL Head No. | Textbox | Yes | — |
| 5 | जी.एल.निवडा | Select GL | Textbox | No | — |
| 6 | खाते क्र. | Account No. | Textbox | Yes | — |
| 7 | खातेधारक शोधा | Search Account Holder | Textbox | Yes | — |
| 8 | खातेधारक निवडा | Select Account Holder | Dropdown | Yes | `TODO` |
| 9 | शिल्लक | Balance | Textbox | No | Read-only |
| 10 | न वटलेली शिल्लक | Uncleared Balance | Textbox | No | Read-only |
| 11 | व्यवहार रक्कम (रू.) | Transaction Amount (Rs.) | Textbox | Yes | — |

**Action:** `नावे ₹` — add debit row.

## Transfer Grid

Columns: निवडा, अनु. क्र, जी.एल., खाते क्रमांक, खाते धारकाचे नाव, शिल्लक, व्यवहार रक्कम.

**Actions:** `काढा`, `वर`. Credit-side entry: `TODO` (not shown in opening frame).

---

## Related Documents

- [overview.md](overview.md)
- [jama-screen.md](jama-screen.md)
- [nave-screen.md](nave-screen.md)
