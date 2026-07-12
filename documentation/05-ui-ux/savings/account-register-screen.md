# Screen Spec — Savings Account Register (बचत > खाते रजिस्टर)

## Purpose

UI specification for searching and listing savings deposit accounts.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | खाते रजिस्टर | Account Register |
| Breadcrumb | डॅशबोर्ड > बचत > खाते रजिस्टर | Dashboard > Savings > Account Register |
| Parent Module | बचत | Savings |

**Auto-fill (header):** `संस्था` (Organization) — read-only `Label` from tenant session; not repeated in filter bar.

## Reference Screenshots

| File | Section |
| :--- | :--- |
| `screenshots/bachat/डॅशबोर्ड-बचत-खाते रजिस्टर-1-05-07.png` | Full screen |

---

## प्राथमिक शोध (Primary Search)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा निवडा | Select Branch | Autocomplete | No | Replaces `शाखा कोड` + `शाखेचे नाव`. Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 2 | योजना निवडा | Select Scheme | Dropdown | No | Loaded dynamically from Savings schemes (Settings > नवीन योजना). e.g. `सेव्हिंग ठेव` (Saving Deposit) |
| 3 | स्थिती निवडा | Select Status | Dropdown | No | e.g. `चालू` (Active) |
| 4 | खाते क्र. (पासून) | Account No. (From) | Textbox | No | Range filter — not consolidated per entity-autocomplete exclusions |
| 5 | खाते क्र. (पर्यंत) | Account No. (To) | Textbox | No | — |
| 6 | खातेधारक निवडा | Select Account Holder | Autocomplete | No | Replaces free-text `खाते धारकाचे नाव`. Sample: `101 — Account Holder 1`. See [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |
| 7 | ग्राहक क्र. (पासून) | Customer No. (From) | Textbox | No | Range filter |
| 8 | ग्राहक क्रमांक (पर्यंत) | Customer No. (To) | Textbox | No | — |

**Link:** `अतिरिक्त शोध पर्याय` — `TODO — not captured`.

**Action:** `दाखवा`.

**Sidebar `तपशील`:** Opens account detail in context — no separate Account Information screen spec (deferred; see [ux-optimization.md](ux-optimization.md)).

---

## Results Grid

**Legend:** Pink — कर्ज असलेली खाती (Accounts with loans).

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
| 13 | कमाल नावे मर्यादा | Max Debit Limit |
| 14 | एल. एफ. क्र. | L.F. No. |
| 15 | खाते श्रेणी | Account Category |
| 16 | आयएमपीएस / आरटीजीएस खाते क्रमांक | IMPS / RTGS Account No. |
| 17 | विनंती चॅनेल | Request Channel |
| 18 | निधी हस्तांतरण मर्यादा | Fund Transfer Limit |
| 19 | खाते बंद दिनांक | Account Close Date |

**Footer:** एकूण नोंदी, pagination (पहिले, मागील, पुढील).

**Sidebar actions:** `तपशील`, `निर्यात करा`, `काढा`, `खाते उतारा`.

**Bottom actions:** `खाते बंद करा`, `पुनर्वत`.

---

## Mockup

- [HTML mockup (Draft)](../mockups/savings/account-register-screen/) — Marathi layout for bank review

## Related Documents

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [new-savings-account-screen.md](new-savings-account-screen.md)
- [../fixed-deposit/fd-account-management-screen.md](../fixed-deposit/fd-account-management-screen.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
