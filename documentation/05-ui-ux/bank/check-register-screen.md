# Screen Spec — Cheque Register (बँक > चेक रजिस्टर)

> **Superseded (2026-07-07):** Consolidated into [bank-management-screen.md](bank-management-screen.md) — Tab 2 **चेक रजिस्टर**. Retained for field reference only.

## Purpose

UI specification for searching, listing, and processing cheques (cleared, uncleared, returned).

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | चेक रजिस्टर | Cheque Register |
| Breadcrumb | डॅशबोर्ड > बँक > चेक रजिस्टर | Dashboard > Bank > Cheque Register |
| Parent Module | बँक | Bank |

## Reference Screenshots

| File | Section |
| :--- | :--- |
| `screenshots/Bank/डॅशबोर्ड-बँक-चेक रजिस्टर.png` | Full screen |

---

## Filter Section

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | व्यवहार प्रकार | Transaction Type | Radio | No | `सर्व` (All), `जमा` (Credit), `नावे` (Debit) |
| 2 | शाखा क्र. | Branch No. | Textbox | Yes | e.g. `1` |
| 3 | शाखा निवडा | Select Branch | Dropdown | No | e.g. `कोतोली मुख्य कार्यालय` |
| 4 | बँक निवडा | Select Bank | Dropdown | No | Loaded from Bank Master — e.g. `बँक ऑफ इंडिया` |
| 5 | या दिनांकापासून | From Date | Date | No | — |
| 6 | या दिनांकापर्यंत | To Date | Date | No | — |
| 7 | रक्कम पासून | Amount From | Textbox | No | — |
| 8 | रक्कम पर्यंत | Amount To | Textbox | No | — |
| 9 | ग्राहक क्र. | Customer No. | Textbox | No | — |
| 10 | चेक क्र. पासून | Cheque No. From | Textbox | No | — |
| 11 | पासुन मंजुरीची तारीख | From Approval Date | Date | No | — |
| 12 | मंजुरीची तारीख | Approval Date | Date | No | — |
| 13 | बँक पद्धत निवडा | Select Bank Method | Dropdown | Yes | `TODO` |
| 14 | स्थिती | Status | Radio | No | `सर्व` (All), `वटवलेले` (Cleared), `न वटवलेले` (Uncleared), `चेक रिटर्न` (Cheque Return) |

**Action:** `दाखवा`.

---

## Results Grid

**Select all:** `सर्व निवडा`. **Grid action:** `निर्यात`.

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | अनु. क्र. | Sr. No. |
| 3 | बँक | Bank |
| 4 | रक्कम | Amount |
| 5 | इश्यु दिनांक | Issue Date |
| 6 | जमा / नावे | Credit / Debit |
| 7 | चेक क्र. | Cheque No. |
| 8 | क्लिअरन्स दिनांक | Clearance Date |
| 9 | तपशील | Details |
| 10 | ड्रॉन ऑन बँक | Drawn on Bank |
| 11 | ड्रॉन ऑन शाखा | Drawn on Branch |
| 12 | च्या कारणास्तव | Reason |

**Summary:** `एकूण` (Total amount).

**Footer fields:** `चेक रिटर्न शुल्क` (Cheque Return Fee).

**Actions:** `चेक रिटर्न`, `पूर्ण`, `पूर्ववत`.

---

## Related Documents

- [bank-management-screen.md](bank-management-screen.md) — current spec
- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [../accounting/jama-screen.md](../accounting/jama-screen.md)
- [../accounting/nave-screen.md](../accounting/nave-screen.md)
