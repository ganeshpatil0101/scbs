# Screen Spec — New Bank (बँक > नवीन बँक)

> **Superseded (2026-07-07):** Consolidated into [bank-management-screen.md](bank-management-screen.md) — Tab 1 **बँक खाते** (Create / Update panel). Retained for field reference only.

## Purpose

UI specification for registering a new society bank account (GL-linked external bank account).

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | नवीन बँक | New Bank |
| Breadcrumb | डॅशबोर्ड > बँक > नवीन बँक | Dashboard > Bank > New Bank |
| Parent Module | बँक | Bank |

## Reference Screenshots

| File | Section |
| :--- | :--- |
| `screenshots/Bank/डॅशबोर्ड-बँक-नवीन बँक.png` | Full screen |

---

## Form Fields

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | जी.एल. हेड क्रमांक | G.L. Head Number | Textbox | Yes | — |
| 2 | बँकेचे नाव | Bank Name | Textbox | Yes | — |
| 3 | बँक खाते क्र. | Bank Account No. | Textbox | Yes | — |
| 4 | शाखा | Branch | Textbox | Yes | — |
| 5 | पत्ता | Address | Textbox | Yes | — |
| 6 | खाते प्रकार | Account Type | Dropdown | Yes | `TODO` — placeholder shown in screenshot |
| 7 | खाते चालू दिनांक | Account Opening Date | Date | Yes | — |
| 8 | स्थिती | Status | Dropdown | Yes | `TODO` |
| 9 | शाखांतर्गत व्यवहार हवा आहे | Internal Branch Transaction Required | Checkbox | No | — |
| 10 | आय.एफ.एस.सी. कोड | IFSC Code | Textbox | No | — |
| 11 | किमान शिल्लक | Minimum Balance | Textbox | No | — |
| 12 | फंड ट्रान्सफरसाठी हवी | Required for Fund Transfer | Checkbox | No | — |

**Actions:** `पूर्ण`, `पूर्ववत`.

---

## Related Documents

- [bank-management-screen.md](bank-management-screen.md) — current spec
- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
