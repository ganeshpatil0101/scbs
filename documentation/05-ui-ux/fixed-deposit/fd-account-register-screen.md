# Screen Spec — FD Account Register (मुदत ठेव > खाते रजिस्टर)

## Purpose

UI specification for searching and listing fixed deposit accounts.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | खाते रजिस्टर | Account Register |
| Breadcrumb | डॅशबोर्ड > मुदत ठेव > खाते रजिस्टर | Dashboard > Fixed Deposit > Account Register |
| Parent Module | मुदत ठेव | Fixed Deposit |

## Reference Screenshots

| File | Section |
| :--- | :--- |
| `screenshots/मुदत ठेव/डॅशबोर्ड_मुदत ठेव _खाते रजिस्टर.png` | Full screen |

---

## प्राथमिक शोध (Primary Search)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | संघटना | Organization | Dropdown | No | — |
| 2 | शाखा निवडा | Select Branch | Autocomplete | No | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 3 | शाखेचे नाव | Branch Name | Dropdown | No | e.g. कोतोली मुख्य कार्यालय |
| 4 | योजना निवडा | Select Scheme | Dropdown | No | e.g. `सर्व` |
| 5 | स्थिती निवडा | Select Status | Dropdown | No | e.g. `चालू` |
| 6 | खाते क्र. (पासून) | Account No. (From) | Textbox | No | — |
| 7 | खाते क्र. (पर्यंत) | Account No. (To) | Textbox | No | — |
| 8 | खातेधारक | Account Holder | Textbox | No | — |
| 9 | ग्राहक क्र. (पासून) | Customer No. (From) | Textbox | No | — |
| 10 | ग्राहक क्र. (पर्यंत) | Customer No. (To) | Textbox | No | — |

**Link:** `अतिरिक्त शोध पर्याय`. **Action:** `दाखवा`.

---

## Results Grid

**Legend:** Pink — कर्ज असलेली खाती; Blue — मुदत संपलेली खाती.

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | अनु. क्र | Sr. No. |
| 3 | शाखा | Branch |
| 4 | खाते क्र. | Account No. |
| 5 | खाते | Account |
| 6 | ग्राहक क्र. | Customer No. |
| 7 | खातेधारक | Account Holder |
| 8 | चालू दिनांक | Start Date |
| 9 | व्याज सुरु दिनांक | Interest Start Date |
| 10 | पावती क्रमांक | Receipt Number |
| 11 | व्याज दर | Interest Rate |
| 12 | मुदत ठेव रक्कम | FD Amount |
| 13 | तरतूद | Provision |
| 14 | दिलेले व्याज | Interest Paid |
| 15 | शिल्लक | Balance |
| 16 | एल. ए. क्रमांक | L.A. Number |
| 17 | छापील संख्या | Printed Count |
| 18 | मुदतपूर्ती दिनांक | Maturity Date |
| 19 | मुदतपूर्ती रक्कम | Maturity Amount |
| 20 | विनंती चॅनेल | Request Channel |
| 21 | खाते बंद दिनांक | Account Close Date |

**Footer:** एकूण नोंदी, pagination. **Totals:** एकूण एफडी शिल्लक, एकूण व्याज दिले, एकूण तरतूद व्याज.

**Sidebar actions:** `तपशील`, `निर्यात करा`, `काढा`, `खाते उतारा`.

---

## Cross-Links

- [overview.md](overview.md)
- [new-fd-account-screen.md](new-fd-account-screen.md)
