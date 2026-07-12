# Screen Spec — Recurring Account Register (रिकरिंग > खाते रजिस्टर)

## Purpose

UI specification for searching and listing recurring deposit accounts.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | खाते रजिस्टर | Account Register |
| Breadcrumb | डॅशबोर्ड > रिकरिंग > खाते रजिस्टर | Dashboard > Recurring > Account Register |
| Parent Module | रिकरिंग | Recurring |

**Auto-fill (header):** `संस्था` (Organization) — read-only `Label` from tenant session; not repeated in filter bar.

## Reference Screenshots

| File | Section |
| :--- | :--- |
| `screenshots/रिकरिंग/डॅशबोर्ड_रिकरिंग_खाते रजिस्टर.png` | Full screen |

---

## प्राथमिक शोध (Primary Search)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा निवडा | Select Branch | Autocomplete | No | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 2 | योजना निवडा | Select Scheme | Dropdown | No | Loaded dynamically from Recurring schemes (Settings > नवीन योजना). Replaces legacy `खाते निवडा`. e.g. `सर्व` |
| 3 | स्थिती निवडा | Select Status | Dropdown | No | e.g. `चालू` |
| 4 | खाते क्र. (पासून) | Account No. (From) | Textbox | No | Range filter — not consolidated per entity-autocomplete exclusions |
| 5 | खाते क्र. (पर्यंत) | Account No. (To) | Textbox | No | — |
| 6 | खातेधारक निवडा | Select Account Holder | Autocomplete | No | Replaces free-text `खातेधारकाचे नाव`. Sample: `101 — Account Holder 1`. See [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |
| 7 | ग्राहक क्र. (पासून) | Customer No. (From) | Textbox | No | Range filter |
| 8 | ग्राहक क्रमांक (पर्यंत) | Customer No. (To) | Textbox | No | — |

**Link:** `अतिरिक्त शोध पर्याय` — `TODO — not captured`.

**Action:** `दाखवा`.

---

## Results Grid

**Legend:** Pink — कर्ज असलेली खाती; Blue — मुदत संपलेली खाती.

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | अ.क्र. | Sr. No. |
| 3 | शाखा | Branch |
| 4 | खाते क्र. | Account No. |
| 5 | खाते | Account |
| 6 | ग्राहक क्रमांक | Customer No. |
| 7 | नाव | Name |
| 8 | चालू दिनांक | Open Date |
| 9 | व्याज दर | Interest Rate |
| 10 | तरतूद | Provision |
| 11 | दिलेले व्याज | Interest Paid |
| 12 | शिल्लक | Balance |
| 13 | एल. एफ. क्र. | L.F. No. |
| 14 | परतीची दिनांक | Return Date |
| 15 | परतीची रक्कम | Return Amount |
| 16 | कार्यकाळ | Tenure |
| 17 | हप्ता | Installment |
| 18 | अर्जाची दिनांक | Application Date |
| 19 | विनंती चॅनेल | Request Channel |
| 20 | खाते बंद तारीख | Account Close Date |

**Footer:** एकूण नोंदी, pagination (पहिले, मागील, पुढील).

**Sidebar actions:** `तपशील`, `निर्यात`, `काढा`, `खाते उतारा`.

---

## Mockup

- [HTML mockup (Draft)](../mockups/recurring/account-register-screen/) — Marathi layout for bank review

## Related Documents

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [new-recurring-account-screen.md](new-recurring-account-screen.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
