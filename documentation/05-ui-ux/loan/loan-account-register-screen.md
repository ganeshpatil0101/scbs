# Screen Spec — Loan Account Register (कर्ज > खाते रजिस्टर)

## Purpose

UI specification for searching and listing loan accounts.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | खाते रजिस्टर | Account Register |
| Breadcrumb | डॅशबोर्ड > कर्ज > खाते रजिस्टर | Dashboard > Loan > Account Register |
| Parent Module | कर्ज | Loan |

## Reference Screenshots

| File | Section |
| :--- | :--- |
| `screenshots/कर्ज/डॅशबोर्ड-कर्ज-खाते रजिस्टर-1-05-07.png` | Full screen |

---

## प्राथमिक शोध (Primary Search)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | संघटना | Organization | Dropdown | No | Society name |
| 2 | शाखा कोड | Branch Code | Textbox | No | e.g. `1` |
| 3 | शाखेचे नाव | Branch Name | Dropdown | No | e.g. `कोतोली मुख्य कार्यालय` |
| 4 | जी.एल. निवडा | Select G.L. | Dropdown | No | e.g. `जामिनकी कर्ज` (Surety Loan) |
| 5 | मिती निवडा | Select Status | Dropdown | No | e.g. `चालू` (Active) |
| 6 | खाते क्र. (पासून) | Account No. (From) | Textbox | No | — |
| 7 | खाते क्र. (पर्यंत) | Account No. (To) | Textbox | No | — |
| 8 | खातेदाराचे नाव | Account Holder Name | Textbox | No | — |
| 9 | ग्राहक क्र. (पासून) | Customer No. (From) | Textbox | No | — |
| 10 | ग्राहक क्र. (पर्यंत) | Customer No. (To) | Textbox | No | — |

**Link:** `अतिरिक्त शोध पर्याय`. **Action:** `दाखवा`.

**Filter checkbox:** `परतीची दिनांक संपून गेलेली खाते` (Accounts whose return date has expired).

---

## Results Grid

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | अनुक्रमांक | Sr. No. |
| 3 | शाखेचे नाव | Branch Name |
| 4 | खाते क्रमांक | Account No. |
| 5 | नाव(ग्राहक क्र.) | Name (Customer No.) |
| 6 | चालू दिनांक | Open Date |
| 7 | कर्ज रक्कम | Loan Amount |
| 8 | व्याज दर | Interest Rate |
| 9 | तरतूद | Provision |
| 10 | आलेले व्याज | Interest Received |
| 11 | शिल्लक | Balance |
| 12 | स्थिती | Status |
| 13 | चालू व्याज | Current Interest |
| 14 | एल.एफ.क्र. | L.F. No. |
| 15 | एनपीए स्थिती | NPA Status |
| 16 | एनईएफटी / आरटीजीएस खाते क्र. | NEFT / RTGS Account No. |
| 17 | परतीची दिनांक संपून गेलेली | Return Date Expired |
| 18 | परतीची दिनांक | Return Date |
| 19 | व्याज फरक | Interest Difference |
| 20 | दंड व्याज दर | Penalty Interest Rate |
| 21 | निधी हस्तांतरण मर्यादा | Fund Transfer Limit |
| 22 | खाते बंद दिनांक | Account Close Date |
| 23 | ग्राहक कर्ज जोखीम मर्यादा | Customer Loan Risk Limit |

**Footer:** एकूण नोंदी, pagination.

**Report:** `रिपोर्ट यादी` dropdown — e.g. `Loan Schedule`. **Action:** `प्रिंट`.

**Sidebar actions:** `तपशील`, `निर्यात`, `काढा`, `खाते उतारा`.

**Bottom actions:** `खाते बंद`, `नूतनीकरण`, `पूर्वत`.

---

## Related Documents

- [overview.md](overview.md)
- [new-loan-screen.md](new-loan-screen.md)
- [loan-information-screen.md](loan-information-screen.md)
