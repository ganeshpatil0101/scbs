# Screen Spec — Daily Account Register (डेली > खाते रजिस्टर)

## Purpose

UI specification for searching and listing daily deposit accounts.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | खाते रजिस्टर | Account Register |
| Breadcrumb | डॅशबोर्ड > डेली > खाते रजिस्टर | Dashboard > Daily > Account Register |
| Parent Module | डेली | Daily |

**Auto-fill (header):** `संस्था` (Organization) — read-only `Label` from tenant session; not repeated in filter bar.

## Reference Screenshots

| File | Section |
| :--- | :--- |
| `screenshots/डेली/डॅशबोर्ड_डेली_खाते रजिस्टर.png` | Full screen |

---

## प्राथमिक शोध (Primary Search)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा निवडा | Select Branch | Autocomplete | No | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 2 | योजना निवडा | Select Scheme | Dropdown | No | Loaded dynamically from Daily schemes (Settings > नवीन योजना). Sample: `डेली १`, `डेली २`, `पिग्मी ठेव` |
| 3 | एजंट निवडा | Select Agent | Autocomplete | No | Replaces `एजंट क्रमांक` + `एजंट निवडा`. Sample: `1 — Agent 1`. Enter resolves by ID or name |
| 4 | खाते क्र. (पासून) | Account No. (From) | Textbox | No | Range filter — not consolidated per entity-autocomplete exclusions |
| 5 | खाते क्र. (पर्यंत) | Account No. (To) | Textbox | No | — |
| 6 | ग्राहक क्र. (पासून) | Customer No. (From) | Textbox | No | Range filter |
| 7 | ग्राहक क्र. (पर्यंत) | Customer No. (To) | Textbox | No | — |
| 8 | खातेधारक | Account Holder | Textbox | No | — |
| 9 | स्थिती निवडा | Select Status | Dropdown | No | Default: `चालू` (Active). Values: `चालू`, `बंद` (Closed), `स्थगित` (Suspended) — same as [New Daily Account](new-daily-account-screen.md) / [Savings Account Register](../savings/account-register-screen.md) |

**Action:** `दाखवा` (Show).

> **Out of scope (deferred):** Legacy link `अतिरिक्त शोध पर्याय` exists in the old app but is not required for the current CBS UI — omitted from this spec (no stub, no TODO). Same as [Savings Account Register](../savings/account-register-screen.md).

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

## Mockup

- [HTML mockup (Draft)](../mockups/daily/account-register-screen/) — Marathi layout for bank review

---

## Cross-Links

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [new-daily-account-screen.md](new-daily-account-screen.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
