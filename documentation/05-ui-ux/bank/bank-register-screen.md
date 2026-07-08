# Screen Spec — Bank Register (बँक > बँक रजिस्टर)

> **Superseded (2026-07-07):** Consolidated into [bank-management-screen.md](bank-management-screen.md) — Tab 1 **बँक खाते**. Retained for field reference only.

## Purpose

UI specification for searching and listing society bank accounts (current accounts held at external banks).

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | बँक रजिस्टर | Bank Register |
| Breadcrumb | डॅशबोर्ड > बँक > बँक रजिस्टर | Dashboard > Bank > Bank Register |
| Parent Module | बँक | Bank |

## Reference Screenshots

| File | Section |
| :--- | :--- |
| `screenshots/Bank/डॅशबोर्ड-बँक-बँक रजिस्टर.png` | Full screen |

---

## प्राथमिक शोध (Primary Search)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | संघटना | Organization | Dropdown | Yes | Society name |
| 2 | शाखा कोड | Branch Code | Textbox | No | e.g. `1` |
| 3 | शाखेचे नाव | Branch Name | Dropdown | No | e.g. `कोतोली मुख्य कार्यालय` |
| 4 | खाते प्रकार | Account Type | Dropdown | No | Default: `सर्व` (All) |
| 5 | स्थिती निवडा | Select Status | Dropdown | No | e.g. `चालू` (Active) |

**Action:** `दाखवा`.

---

## Results Grid

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | अनु. क्र. | Sr. No. |
| 3 | जी.एल. हेड | G.L. Head |
| 4 | बँकेचे नाव | Bank Name |
| 5 | शाखा | Branch |
| 6 | बँक खाते क्र. | Bank Account No. |
| 7 | खाते दिनांक | Account Date |
| 8 | खाते प्रकार | Account Type |
| 9 | शिल्लक | Balance |

**Sidebar actions:** `तपशील`, `निर्यात करा`, `काढा`.

---

## Related Documents

- [bank-management-screen.md](bank-management-screen.md) — current spec
- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
