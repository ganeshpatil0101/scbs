# Screen Spec — Deposit Loan Installment Payment (ठेव > ठेव कर्ज हप्ता पेमेंट)

## Purpose

UI specification for processing installment payments on loans against deposits.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | ठेव कर्ज हप्ता पेमेंट | Deposit Loan Installment Payment |
| Breadcrumb | डॅशबोर्ड > ठेव > ठेव कर्ज हप्ता पेमेंट | Dashboard > Deposit > Deposit Loan Installment Payment |
| Parent Module | मुदत ठेव | Fixed Deposit |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | व्याज | Interest |
| 2 | इतर कपात | Other Deductions |
| 3 | कर्ज माहिती | Loan Information |
| 4 | साहित्य तपशील / तारण तपशील | Collateral Details |
| 5 | ट्रान्सफर | Transfer |
| 6 | केवायसी माहिती | KYC Information |

## Reference Screenshots / Media

| File | Tab |
| :--- | :--- |
| `screenshots/मुदत ठेव/डॅशबोर्ड_ठेव_ठेव कर्ज हप्ता पेमेंट.mp4` | Tab 1 (from video) |
| `screenshots/मुदत ठेव/deposit-loan-installment-frames/frame_0000.jpg` | Tab 1 |

---

## Tab 1: व्याज (Interest)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | रोख / ट्रान्सफर | Cash / Transfer | Radio | Yes | — |
| 2 | जी.एल.क्र. | G.L. No. | Textbox | Yes | — |
| 3 | जी.एल.निवडा | Select G.L. | Dropdown | Yes | Values: `TODO` |
| 4 | खाते क्रमांक | Account Number | Textbox | No | — |
| 5 | खातेधारक निवडा | Select Account Holder | Dropdown | No | Values: `TODO` |
| 6 | ग्राहक क्र. | Customer No. | Textbox | No | — |
| 7 | ग्राहक निवडा | Select Customer | Dropdown | No | Values: `TODO` |
| 8 | दिनांक | Date | Date | Yes | System date |

**Note:** कृपया खाते क्रमांक किंवा ग्राहक क्रमांक प्रविष्ट करा.

**Action:** `व्याज गणना करा` (Calculate Interest).

### Results Grid

**Select all:** `सर्व निवडा`.

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | अ. क्र. | Sr. No. |
| 3 | खाते क्र. | Account No. |
| 4 | ग्राहक क्र. | Customer No. |
| 5 | खातेधारक | Account Holder |
| 6 | नाव 2 | Name 2 |
| 7 | बँकेचे बचत खाते क्रमांक | Bank Savings Account No. |
| 8 | आय.एफ.एस.सी. कोड | IFSC Code |
| 9 | चालू दिनांक | Start Date |
| 10 | शेवटची तारीख | Last Date |
| 11 | व्याज दिनांक | Interest Date |
| 12 | व्याज दर | Interest Rate |
| 13 | शिल्लक | Balance |
| 14 | मुद्दल हप्ता | Principal Installment |
| 15 | वर्तमान व्याज | Current Interest |
| 16 | एकूण हप्ता | Total Installment |

**Action:** `निर्धारित करा` (Set/Determine).

**Summary:** एकूण तरतूद, एकूण व्याज, एकूण रक्कम.

**Footer:** `पुढे`, `पूर्ण`, `पूर्वत`.

Tabs 2–6: `TODO` — not captured in video.

---

## Cross-Links

- [overview.md](overview.md)
- [../loan/new-deposit-loan-screen.md](../loan/new-deposit-loan-screen.md)
