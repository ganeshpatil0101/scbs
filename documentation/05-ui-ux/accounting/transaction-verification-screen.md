# Screen Spec — Transaction Verification (लेखा > व्यवहार तपासणी)

## Purpose

UI specification for verifying and reviewing posted transactions — today's activity and full historical search.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | व्यवहार तपासणी | Transaction Verification |
| Breadcrumb | डॅशबोर्ड > लेखा > व्यवहार तपासणी | Dashboard > Accounting > Transaction Verification |
| Parent Module | लेखा | Accounting |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | आजचे व्यवहार | Today's Transactions |
| 2 | सर्व व्यवहार | All Transactions |

## Reference Screenshots

| File | Tab |
| :--- | :--- |
| `screenshots/lekha/डॅशबोर्ड-लेखा-व्यवहार तपासणी-1-05-07.png` | Tab 2 |

---

## प्राथमिक शोध (Primary Search)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा कोड | Branch Code | Textbox | No | e.g. `1` |
| 2 | शाखा निवडा | Select Branch | Dropdown | No | e.g. `कोतोली मुख्य कार्यालय` |
| 3 | जि.एल.क्र. | G.L. No. | Textbox | No | — |
| 4 | जि.एल.निवडा | Select G.L. | Dropdown | No | — |
| 5 | खाते क्रमांक | Account Number | Textbox | No | — |
| 6 | खातेधारक निवडा | Select Account Holder | Dropdown | No | — |
| 7 | व्यवहार दिनांक (पासून) | Transaction Date (From) | Date | No | — |
| 8 | व्यवहार दिनांक (पर्यंत) | Transaction Date (To) | Date | No | — |

**Link:** `अ‍ॅडव्हान्स शोध`. **Action:** `दाखवा`.

---

## Results Grid

**Select all:** `सर्व निवडा`.

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | दिनांक | Date |
| 3 | चलन क्रमांक | Challan No. |
| 4 | प्रकार | Type |
| 5 | जि.एल. | G.L. No. |
| 6 | जि.एल.नाव | G.L. Name |
| 7 | खाते क्रमांक | Account No. |
| 8 | खाते धारक | Account Holder |
| 9 | नावे | Debit |
| 10 | जमा | Credit |
| 11 | तपशील | Details |
| 12 | वापरकर्ता | User |
| 13 | सत्र | Session |
| 14 | वेळ | Time |
| 15 | खरेदी क्र. | Purchase No. |
| 16 | साहित्य प्रकार | Instrument Type |
| 17 | साहित्य नंबर | Instrument Number |
| 18 | जारी केलेली दिनांक | Issued Date |
| 19 | पासिंग तपशील | Passing Details |
| 20 | मोठा तपशील | Detailed Description |
| 21 | पासिंग वापरकर्ता | Passing User |
| 22 | पासिंग वेळ | Passing Time |

**Summary:** `एकूण नावे`, `एकूण जमा`.

**Sidebar action:** `निर्यात करा`, `शिका`.

**Actions:** `चलन प्रिंट`, `ड्राफ्ट प्रिंट`.

---

## Mockup

| Property | Value |
| :--- | :--- |
| HTML mockup | [mockups/accounting/transaction-verification-screen/index.html](../mockups/accounting/transaction-verification-screen/index.html) |
| Review guide | [mockups/accounting/transaction-verification-screen/README.md](../mockups/accounting/transaction-verification-screen/README.md) |
| Status | Draft |

## Related Documents

- [overview.md](overview.md)
- [transaction-passing-screen.md](transaction-passing-screen.md)
