# Screen Spec — FD Account Management (मुदत ठेव > खाते व्यवस्थापन)

> **Consolidates:** [fd-account-register-screen.md](fd-account-register-screen.md) + [account-renewal-list-screen.md](account-renewal-list-screen.md)

## Purpose

Single screen for searching fixed deposit accounts and viewing renewal history. Tab 1 lists all FD accounts with balances and status; Tab 2 lists renewal events for filtered accounts.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | खाते व्यवस्थापन | Account Management |
| Breadcrumb | डॅशबोर्ड > मुदत ठेव > खाते व्यवस्थापन | Dashboard > Fixed Deposit > Account Management |
| Parent Module | मुदत ठेव | Fixed Deposit |

**Auto-fill (header):** `संस्था` (Organization) — read-only `Label` from tenant session; not repeated in filter bar on Tab 1.

## Tabs

| # | Marathi Tab | English Tab | Replaces |
| :---: | :--- | :--- | :--- |
| 1 | खाते रजिस्टर | Account Register | FD Account Register |
| 2 | नूतनीकरण यादी | Renewal List | Account Renewal List |

## Reference Screenshots

| File | Tab |
| :--- | :--- |
| `screenshots/मुदत ठेव/डॅशबोर्ड_मुदत ठेव _खाते रजिस्टर.png` | Tab 1 |
| `screenshots/मुदत ठेव/डॅशबोर्ड_मुदत ठेव_खाते नूतनीकरण यादी.png` | Tab 2 |

---

## Tab 1: खाते रजिस्टर (Account Register)

### प्राथमिक शोध (Primary Search)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा निवडा | Select Branch | Autocomplete | No | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 2 | योजना निवडा | Select Scheme | Dropdown | No | Loaded dynamically from FD schemes (Settings > नवीन योजना). e.g. `सर्व` |
| 3 | स्थिती निवडा | Select Status | Dropdown | No | e.g. `चालू` |
| 4 | खाते क्र. (पासून) | Account No. (From) | Textbox | No | Range filter — not consolidated per entity-autocomplete exclusions |
| 5 | खाते क्र. (पर्यंत) | Account No. (To) | Textbox | No | — |
| 6 | खातेधारक निवडा | Select Account Holder | Autocomplete | No | Replaces free-text `खातेधारक`. Sample: `101 — Account Holder 1`. See [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |
| 7 | ग्राहक क्र. (पासून) | Customer No. (From) | Textbox | No | Range filter |
| 8 | ग्राहक क्र. (पर्यंत) | Customer No. (To) | Textbox | No | — |

**Link:** `अतिरिक्त शोध पर्याय` — `TODO — not captured`.

**Action:** `दाखवा` (Show).

### Results Grid

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

## Tab 2: नूतनीकरण यादी (Renewal List)

### Filter Section

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा निवडा | Select Branch | Autocomplete | No | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 2 | योजना | Scheme | Dropdown | No | Loaded dynamically from FD schemes (Settings > नवीन योजना). e.g. `सर्व` |
| 3 | खातेधारक निवडा | Select Account Holder | Autocomplete | No | Replaces free-text `खातेधारक`. Sample: `101 — Account Holder 1` |
| 4 | खाते क्र. (पासून) | Account No. (From) | Textbox | No | Range filter |
| 5 | खाते क्र. (पर्यंत) | Account No. (To) | Textbox | No | — |
| 6 | ग्राहक क्र. (पासून) | Customer No. (From) | Textbox | No | Range filter |
| 7 | ग्राहक क्र. (पर्यंत) | Customer No. (To) | Textbox | No | — |
| 8 | तारीख नूतनीकरण (पासून) | Renewal Date (From) | Date | No | Unique to this tab |
| 9 | तारीख नूतनीकरण (पर्यंत) | Renewal Date (To) | Date | No | — |
| 10 | पावती क्रमांक | Receipt Number | Textbox | No | — |

**Action:** `दाखवा` (Show).

### Results Grid

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | अनु. क्र | Sr. No. |
| 2 | खाते शाखा | Account Branch |
| 3 | खाते क्र. | Account No. |
| 4 | खातेधारक | Account Holder |
| 5 | तारीख नूतनीकरण | Renewal Date |
| 6 | चालू दिनांक | Current Date |
| 7 | रक्कम | Amount |
| 8 | मुदतीअंती रक्कम | Maturity Amount |
| 9 | कालावधी महिने | Duration (Months) |
| 10 | कालावधी दिवसात | Duration (Days) |
| 11 | व्याज दर | Interest Rate |
| 12 | मुदतपूर्ती दिनांक | Maturity Date |

**Action:** `निर्यात करा` (Export).

---

## Related Documents

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [new-fd-account-screen.md](new-fd-account-screen.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
- [../../AI_INDEX.md](../../AI_INDEX.md)
