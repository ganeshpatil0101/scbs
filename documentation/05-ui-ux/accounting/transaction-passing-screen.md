# Screen Spec — Transaction Passing (लेखा > व्यवहार पासिंग)

## Purpose

UI specification for reviewing and passing (authorizing) pending transactions. Supports today's transactions and advanced search.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | व्यवहार पासिंग | Transaction Passing |
| Breadcrumb | डॅशबोर्ड > लेखा > व्यवहार पासिंग | Dashboard > Accounting > Transaction Passing |
| Parent Module | लेखा | Accounting |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | आजचे व्यवहार | Today's Transactions |
| 2 | अॅडव्हान्स शोध | Advanced Search |

## Reference Screenshots

| File | Tab / Section |
| :--- | :--- |
| `screenshots/lekha/डॅशबोर्ड -लेखा- व्यवहार पासिंग-05-07.png` | Tab 1 — filter + grid |

---

## Filter Section (Tab 1)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा कोड | Branch Code | Textbox | No | e.g. `1` |
| 2 | शाखा निवडा | Select Branch | Dropdown | No | e.g. `कोल्हापूर मुख्य कार्यालय` |
| 3 | जी.एल. हेड | G.L. Head | Textbox | No | e.g. `55` |
| 4 | जी.एल. निवडा | Select G.L. | Dropdown | No | e.g. `सेव्हिंग ठेव` |
| 5 | वापरकर्ता निवडा | Select User | Dropdown | No | Default: `सर्व` (All) |
| 6 | खाते क्रमांक | Account Number | Textbox | No | — |
| 7 | खातेधारक निवडा | Select Account Holder | Dropdown | No | — |
| 8 | खाते क्र. (पासून) | Account No. (From) | Textbox | No | — |
| 9 | खाते क्र. (पर्यंत) | Account No. (To) | Textbox | No | — |
| 10 | चलन क्रमांक (पासून) | Challan No. (From) | Textbox | No | — |
| 11 | चलन क्रमांक (पर्यंत) | Challan No. (To) | Textbox | No | — |
| 12 | व्यवहार रक्कम (पासून) | Transaction Amount (From) | Textbox | No | — |
| 13 | व्यवहार रक्कम (पर्यंत) | Transaction Amount (To) | Textbox | No | — |
| 14 | स्क्रोल क्र. (पासून) | Scroll No. (From) | Textbox | No | — |
| 15 | स्क्रोल क्र. (पर्यंत) | Scroll No. (To) | Textbox | No | — |
| 16 | व्यवहार प्रकार | Transaction Type | Radio | No | `सर्व`, `रोख` (Cash), `ट्रान्सफर` (Transfer), `क्लिअरिंग` (Clearing), `पासिंग न झालेले` (Not Passed) |

**Action:** `दाखवा`.

---

## Results Grid

**Select all:** `सर्व निवडा`.

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | दिनांक | Date |
| 3 | चलन क्रमांक | Challan No. |
| 4 | प्रकार | Type |
| 5 | जी.एल. क्र. | G.L. No. |
| 6 | जी.एल. नाव | G.L. Name |
| 7 | खाते क्र. | Account No. |
| 8 | खातेधारक | Account Holder |
| 9 | जमा / नावे | Credit / Debit |
| 10 | पासिंग रक्कम | Passing Amount |
| 11 | पासिंग तपशील | Passing Details |
| 12 | वापरकर्ता | User |
| 13 | पासिंग | Passing |
| 14 | तपशील | Details |
| 15 | साहित्य प्रकार | Instrument Type |
| 16 | साहित्य | Instrument |
| 17 | जारी केलेली दिनांक | Issued Date |
| 18 | ठेवपावती पहा | View FD Receipt |
| 19 | खातेवही | Ledger |
| 20 | खात्याची माहिती | Account Information |

**Summary:** `एकूण नावे`, `एकूण जमा`.

**Actions:** `रिपोर्ट करा`, `पूर्ण`, `पूर्ववत`.

---

## Tab 2: अॅडव्हान्स शोध (Advanced Search)

`TODO` — additional filter fields not captured in today's screenshot.

---

## Mockup

| Property | Value |
| :--- | :--- |
| HTML mockup | [mockups/accounting/transaction-passing-screen/index.html](../mockups/accounting/transaction-passing-screen/index.html) |
| Review guide | [mockups/accounting/transaction-passing-screen/README.md](../mockups/accounting/transaction-passing-screen/README.md) |
| Status | Draft |

## Related Documents

- [overview.md](overview.md)
- [transaction-verification-screen.md](transaction-verification-screen.md)
