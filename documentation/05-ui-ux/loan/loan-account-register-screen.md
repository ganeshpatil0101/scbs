# Screen Spec — Loan Account Register (कर्ज > खाते रजिस्टर)

## Purpose

UI specification for searching and listing loan accounts.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | खाते रजिस्टर | Account Register |
| Breadcrumb | डॅशबोर्ड > कर्ज > खाते रजिस्टर | Dashboard > Loan > Account Register |
| Parent Module | कर्ज | Loan |

**Auto-fill (header):** `संस्था` (Organization) — read-only `Label` from tenant session; not repeated in filter bar.

**Navigation:** Sidebar `तपशील` opens [loan-information-screen.md](loan-information-screen.md) with selected account pre-filled.

## Reference Screenshots

| File | Section |
| :--- | :--- |
| `screenshots/कर्ज/डॅशबोर्ड-कर्ज-खाते रजिस्टर-1-05-07.png` | Full screen |

---

## प्राथमिक शोध (Primary Search)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा निवडा | Select Branch | Autocomplete | No | e.g. `1 — कोतोली मुख्य कार्यालय`. Replaces Branch Code + Branch Name pair |
| 2 | जी.एल. निवडा | Select G.L. | Autocomplete | No | e.g. `61 — जामिनकी कर्ज` (Surety Loan) |
| 3 | स्थिती निवडा | Select Status | Dropdown | No | Default: `चालू` (Active). Values: `चालू`, `बंद` (Closed), `स्थगित` (Suspended) — same as [New Loan](new-loan-screen.md) |
| 4 | खाते क्र. (पासून) | Account No. (From) | Textbox | No | Range filter |
| 5 | खाते क्र. (पर्यंत) | Account No. (To) | Textbox | No | Range filter |
| 6 | खातेधारक निवडा | Select Account Holder | Autocomplete | No | Replaces free-text `खातेदाराचे नाव` |
| 7 | ग्राहक क्र. (पासून) | Customer No. (From) | Textbox | No | Range filter — excluded from autocomplete per entity-autocomplete-pattern |
| 8 | ग्राहक क्र. (पर्यंत) | Customer No. (To) | Textbox | No | Range filter |

**Removed:** `संघटना` (Organization) — session header.

**Action:** `दाखवा`.

> **Out of scope (deferred):** Legacy link `अतिरिक्त शोध पर्याय` exists in the old app but is not required for the current CBS UI — omitted from this spec (no stub, no TODO). Same as [Savings Account Register](../savings/account-register-screen.md).

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

## Mockup

- [HTML mockup (Draft)](../mockups/loan/loan-account-register-screen/) — Marathi layout for bank review

## Related Documents

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [loan-information-screen.md](loan-information-screen.md)
- [new-loan-screen.md](new-loan-screen.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
