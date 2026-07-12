# Screen Spec — Loan Scheduled Interest Assessment (कर्ज > शेड्युल व्याज > आवर्ती)

> **Superseded (2026-07-12):** Consolidated into [loan-interest-management-screen.md](loan-interest-management-screen.md) — Tab 2 **व्याज आकारणी**. Retained for field reference only.

## Purpose

UI specification for calculating and posting scheduled (recurring) loan interest, including penalty interest and provision.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | शेड्युल व्याज > आवर्ती | Scheduled Interest > Recurring |
| Breadcrumb | डॅशबोर्ड > कर्ज > शेड्युल व्याज > आवर्ती | Dashboard > Loan > Scheduled Interest > Recurring |
| Parent Module | कर्ज | Loan |

## Reference Screenshots

| File | Section |
| :--- | :--- |
| `screenshots/कर्ज/डॅशबोर्ड-कर्ज-मॅन्युअल व्याज-आकारणी-1-05-07.png` | Full screen |

---

## Filter Section

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा कोड | Branch Code | Textbox | Yes | e.g. `1` |
| 2 | शाखा निवडा | Select Branch | Dropdown | Yes | e.g. `कोतोली मुख्य कार्यालय` |
| 3 | जीएल हेड क्र. | G.L. Head No. | Textbox | Yes | e.g. `61` |
| 4 | जी.एल. हेड निवडा | Select G.L. Head | Dropdown | Yes | e.g. `जामीनकी कर्ज` |
| 5 | व्याज दिनांक निवडा | Select Interest Date | Dropdown | Yes | e.g. `31.03.2026`. Full list: `TODO` |
| 6 | व्याज पोस्ट दिनांक | Interest Post Date | Date | Yes | — |
| 7 | खाते क्र. पासून | Account No. (From) | Textbox | No | — |
| 8 | खाते क्र. पर्यंत | Account No. (To) | Textbox | No | — |

**Link:** `अॅडव्हान्स शोध`.

**Checkbox:** `परिपक्व कर्जासाठी अखेर दिनांकापर्यंत व्याज गणना` (Interest calculation until end date for matured loans).

**Action:** `व्याज गणना करा` (Calculate Interest).

---

## Results Grid

**Select all:** `सर्व निवडा`. **Grid action:** `डिनिवड करा` (Deselect).

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | अ. क्र. | Sr. No. |
| 3 | खाते क्र. | Account No. |
| 4 | खाते धारकाचे नाव | Account Holder Name |
| 5 | चालू दिनांक | Open Date |
| 6 | अंतिम पोस्ट दिनांक | Last Post Date |
| 7 | कर्ज शिल्लक | Loan Balance |
| 8 | व्याज दर | Interest Rate |
| 9 | तरतूद | Provision |
| 10 | व्याज | Interest |
| 11 | दंड तरतूद | Penalty Provision |
| 12 | दंड व्याज | Penalty Interest |

Fields 10 and 12 are editable in the grid.

**Summary:** एकूण तरतूद, एकूण व्याज, एकूण दंड तरतूद, एकूण दंड व्याज, एकूण शिल्लक.

**Actions:** `पोस्टिंग`, `पुनरावलोकन करा`.

---

## Related Documents

- [overview.md](overview.md)
- [loan-manual-interest-provision-screen.md](loan-manual-interest-provision-screen.md)
- [../recurring/recurring-interest-management-screen.md](../recurring/recurring-interest-management-screen.md)
