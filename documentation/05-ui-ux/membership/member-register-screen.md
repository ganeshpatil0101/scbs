# Screen Spec — Member Register (सभासदत्व > सभासद रजिस्टर)

## Purpose

UI specification for searching and listing membership (share capital) accounts.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | सभासद रजिस्टर | Member Register |
| Breadcrumb | डॅशबोर्ड > सभासदत्व > सभासद रजिस्टर | Dashboard > Membership > Member Register |
| Parent Module | सभासदत्व | Membership |

**Auto-fill (header):** `संस्था` (Organization) — read-only `Label` from tenant session; not repeated in filter bar.

**Navigation (open gap):** Sidebar `तपशील` — **no Member Information screen spec exists yet** (deferred per [ux-optimization.md](ux-optimization.md)). Action retained in UI; navigation target TBD.

## Reference Screenshots

| File | Section |
| :--- | :--- |
| `screenshots/sabhsadatv/डॅशबोर्ड-सभासदत्व-सभासद रजिस्टर-02_07.png` | Full screen |

---

## प्राथमिक शोध (Primary Search)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा निवडा | Select Branch | Autocomplete | No | e.g. `1 — कोतोली मुख्य कार्यालय`. Enter resolves by ID or name |
| 2 | सभासदत्व | Membership Type | Dropdown | No | e.g. `सभासद` (Member) |
| 3 | शेअर क्रमांक (पासून) | Share Number (From) | Textbox | No | Range filter |
| 4 | शेअर क्रमांक (पर्यंत) | Share Number (To) | Textbox | No | Range filter |
| 5 | ग्राहक निवडा | Select Customer | Autocomplete | No | Enter resolves by customer no. or name. Replaces free-text Customer Name search |
| 6 | स्थिती निवडा | Select Status | Dropdown | No | e.g. `चालू` (Active) |

**Removed:** `संस्था` (Organization) — session header. **Removed (2026-07-22):** `अॅडव्हान्स शोध` (Advanced Search) link — no fields were ever captured; the primary search filters above are sufficient.

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

**Sidebar actions:** `तपशील` (Details — navigation target TBD), `निर्यात`, `काढा`.

**Footer action:** `पूर्ववत`.

---

## Mockup

| Property | Value |
| :--- | :--- |
| Path | [mockups/membership/member-register-screen/](../mockups/membership/member-register-screen/) |
| Status | **Draft** |
| Created | 2026-07-12 |

Open `index.html` in a browser for layout review before Angular implementation.

---

## Related Documents

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [new-membership-screen.md](new-membership-screen.md)
- [membership-transaction-screen.md](membership-transaction-screen.md)
- [shares-transfer-management-screen.md](shares-transfer-management-screen.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
