# Screen Spec — Shares Transfer List (सभासदत्व > शेअर्स ट्रान्सफर यादी)

> **Superseded (2026-07-12):** Consolidated into [shares-transfer-management-screen.md](shares-transfer-management-screen.md) — Tab 2 (Transfer List). Retained for field reference only.

## Purpose

UI specification for searching and listing completed share transfer records.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | शेअर्स ट्रान्सफर यादी | Shares Transfer List |
| Breadcrumb | डॅशबोर्ड > सभासदत्व > शेअर्स ट्रान्सफर यादी | Dashboard > Membership > Shares Transfer List |
| Parent Module | सभासदत्व | Membership |

## Reference Screenshots

| File | Section |
| :--- | :--- |
| `screenshots/sabhsadatv/डॅशबोर्ड-सभासदत्व-शेअर्स ट्रान्सफर यादी-1-02_07.png` | Full screen |

---

## Search Filters

### Share Class

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | अ वर्ग | Class A | Radio | No | — |
| 2 | ब वर्ग | Class B | Radio | No | — |

### Range Filters

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 3 | सभासद क्र. (पासून) | Member No. (From) | Textbox | No | — |
| 4 | सभासद क्र. (पर्यंत) | Member No. (To) | Textbox | No | — |
| 5 | प्रमाणपत्र क्र. (पासून) | Certificate No. (From) | Textbox | No | — |
| 6 | प्रमाणपत्र क्र. (पर्यंत) | Certificate No. (To) | Textbox | No | — |
| 7 | ट्रान्सफर दिनांक (पासून) | Transfer Date (From) | Date | No | — |
| 8 | ट्रान्सफर दिनांक (पर्यंत) | Transfer Date (To) | Date | No | — |

**Action:** `दाखवा` (Show).

---

## Results Grid

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | अ.क्र. | Sr. No. |
| 3 | ट्रान्सफर दिनांक | Transfer Date |
| 4 | ट्रान्सफर सभासद 'पासून' | Transfer Member 'From' |
| 5 | सभासद क्र. 'पासून' | Member No. 'From' |
| 6 | एकूण शेअर्स | Total Shares |
| 7 | सर्टिफिकेट क्र. | Certificate No. |
| 8 | शेअर्स रक्कम रू. | Share Amount Rs. |
| 9 | ट्रान्सफर सभासद 'पर्यंत' | Transfer Member 'To' |
| 10 | सभासद क्र. 'पर्यंत' | Member No. 'To' |
| 11 | ठराव क्र. | Resolution No. |
| 12 | ठराव दिनांक | Resolution Date |
| 13 | ट्रान्सफर फी रू. | Transfer Fee Rs. |
| 14 | शेरा | Remarks |

**Footer:** `एकूण नोंदी`, pagination (`पुढील >>`).

**Sidebar actions:** `निर्यात`, `काढा`.

**Footer action:** `पूर्ववत`.

---

## Related Documents

- [overview.md](overview.md)
- [shares-transfer-management-screen.md](shares-transfer-management-screen.md)
- [member-register-screen.md](member-register-screen.md)
