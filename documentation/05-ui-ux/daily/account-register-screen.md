# Screen Spec — Daily Account Register (डेली > खाते रजिस्टर)

## Purpose

UI specification for searching and listing daily deposit accounts.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | खाते रजिस्टर | Account Register |
| Breadcrumb | डॅशबोर्ड > डेली > खाते रजिस्टर | Dashboard > Daily > Account Register |
| Parent Module | डेली | Daily |

## Reference Screenshots

| File | Section |
| :--- | :--- |
| `screenshots/डेली/डॅशबोर्ड_डेली_खाते रजिस्टर.png` | Full screen |

---

## प्राथमिक शोध (Primary Search)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | संघटना | Organization | Dropdown | No | e.g. श्रद्धा नागरी सहकारी पतसंस्था |
| 2 | शाखा निवडा | Select Branch | Autocomplete | No | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 3 | शाखेचे नाव | Branch Name | Dropdown | No | e.g. कोतोली मुख्य कार्यालय |
| 4 | योजना निवडा | Select Scheme | Dropdown | No | Loaded dynamically from Daily schemes (Settings > नवीन योजना). Sample: `डेली १`, `डेली २`, `पिग्मी ठेव` |
| 5 | एजंट क्रमांक | Agent Number | Textbox | No | — |
| 6 | एजंट निवडा | Select Agent | Dropdown | No | Loaded dynamically from registered Daily agents for selected branch |
| 7 | खाते क्र. (पासून) | Account No. (From) | Textbox | No | — |
| 8 | खाते क्र. (पर्यंत) | Account No. (To) | Textbox | No | — |
| 9 | ग्राहक क्र. (पासून) | Customer No. (From) | Textbox | No | — |
| 10 | ग्राहक क्र. (पर्यंत) | Customer No. (To) | Textbox | No | — |
| 11 | खातेधारक | Account Holder | Textbox | No | — |
| 12 | स्थिती निवडा | Select Status | Dropdown | No | e.g. `चालू` |

**Link:** `अतिरिक्त शोध पर्याय` (Additional Search Options).

**Action:** `दाखवा` (Show).

---

## Results Grid

**Legend:** Pink — कर्ज असलेली खाती; Light blue — मुदत संपलेली खाती.

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | अनु. क्र. | Sr. No. |
| 3 | शाखा | Branch |
| 4 | खाते क्र. | Account No. |
| 5 | खाते | Account |
| 6 | ग्राहक क्र. | Customer No. |
| 7 | खातेधारक | Account Holder |
| 8 | चालू दिनांक | Opening Date |
| 9 | व्याज दर | Interest Rate |
| 10 | तरतूद | Provision |
| 11 | दिलेले व्याज | Interest Paid |
| 12 | शिल्लक | Balance |
| 13 | पत. पत्र. क्रमांक | Credit Letter No. |
| 14 | नावे मर्यादा | Debit Limit |
| 15 | विनंती चॅनेल | Request Channel |
| 16 | खाते बंद दिनांक | Account Close Date |
| 17 | मुदतपूर्ती दिनांक | Maturity Date |

**Sidebar actions:** `तपशील`, `निर्यात करा`, `काढा`, `खाते उतारा`.

---

## Cross-Links

- [overview.md](overview.md)
- [new-daily-account-screen.md](new-daily-account-screen.md)
