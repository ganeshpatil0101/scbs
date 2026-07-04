# Screen Spec — Member Register (सभासदत्व > सभासद रजिस्टर)

## Purpose

UI specification for searching and listing membership (share capital) accounts.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | सभासद रजिस्टर | Member Register |
| Breadcrumb | डॅशबोर्ड > सभासदत्व > सभासद रजिस्टर | Dashboard > Membership > Member Register |
| Parent Module | सभासदत्व | Membership |

## Reference Screenshots

| File | Section |
| :--- | :--- |
| `screenshots/sabhsadatv/डॅशबोर्ड-सभासदत्व-सभासद रजिस्टर-02_07.png` | Full screen |

---

## प्राथमिक शोध (Primary Search)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | संस्था | Organization | Dropdown | No | e.g. श्रद्धा नागरी सहकारी पतसंस्था मर्यादित, कोतोली |
| 2 | शाखा निवडा | Select Branch | Autocomplete | No | Sample: `1 — कोतोली मुख्य कार्यालय`. Enter resolves by ID or name |
| 3 | सभासदत्व | Membership Type | Dropdown | No | e.g. `सभासद` (Member) |
| 4 | शेअर क्रमांक (पासून) | Share Number (From) | Textbox | No | — |
| 5 | शेअर क्रमांक (पर्यंत) | Share Number (To) | Textbox | No | — |
| 6 | ग्राहकाचे नाव | Customer Name | Textbox | No | — |
| 7 | स्थिती निवडा | Select Status | Dropdown | No | e.g. `चालू` (Active) |

**Link:** `अॅडव्हान्स शोध` (Advanced Search).

**Action:** `दाखवा` (Show).

---

## Results Grid

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | अनु. क्र. | Sr. No. |
| 3 | सभासद क्रमांक | Member Number |
| 4 | ग्राहक क्रमांक | Customer Number |
| 5 | सभासदाचे नाव | Member Name |
| 6 | सभासदत्व | Membership |
| 7 | भाग भांडवल शिल्लक | Share Capital Balance |

**Sidebar actions:** `तपशील`, `निर्यात`, `काढा`.

**Footer action:** `पूर्ववत`.

---

## Related Documents

- [overview.md](overview.md)
- [new-membership-screen.md](new-membership-screen.md)
- [membership-transaction-screen.md](membership-transaction-screen.md)
- [shares-transfer-list-screen.md](shares-transfer-list-screen.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
