# Screen Spec — Recurring Manual Interest Assessment (रिकरिंग > मॅन्युअल व्याज > आकारणी)

## Purpose

UI specification for manually assessing and posting recurring deposit interest.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | मॅन्युअल व्याज > आकारणी | Manual Interest > Assessment |
| Breadcrumb | डॅशबोर्ड > रिकरिंग > मॅन्युअल व्याज > आकारणी | Dashboard > Recurring > Manual Interest > Assessment |
| Parent Module | रिकरिंग | Recurring |

## Reference Screenshots

| File | Section |
| :--- | :--- |
| `screenshots/रिकरिंग/डॅशबोर्ड_रिकरिंग_मॅन्युअल व्याज_आकारणी.png` | Full screen |

---

## Filter Section

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा कोड | Branch Code | Textbox | Yes | e.g. `1` |
| 2 | शाखा निवडा | Select Branch | Dropdown | Yes | e.g. कोतोली मुख्य कार्यालय |
| 3 | जी. एल. हेड | G.L. Head | Textbox | Yes | — |
| 4 | जी. एल. हेड निवडा | Select G.L. Head | Dropdown | Yes | Values: `TODO` |
| 5 | व्याज दिनांक निवडा | Select Interest Date | Dropdown | Yes | Values: `TODO` |
| 6 | ब्याज पोस्टींग दिनांक | Interest Posting Date | Date | Yes | — |
| 7 | खाते क्र. (पासून) | Account No. (From) | Textbox | No | — |
| 8 | खाते क्र. (पर्यंत) | Account No. (To) | Textbox | No | — |

**Link:** `प्रगत शोध` (Advanced Search).

**Action:** `व्याज आकारणी` (Interest Assessment).

---

## Results Grid

**Select all:** `सर्व निवडा`.

**Legend:** Pink — accounts in interest-free period (provision will be made).

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | अ.क्र. | Sr. No. |
| 3 | खाते क्र. | Account No. |
| 4 | खातेदार | Account Holder |
| 5 | खाते चालू दिनांक | Account Opening Date |
| 6 | शेवटची व्याज दिनांक | Last Interest Date |
| 7 | व्याज दर | Interest Rate |
| 8 | शिल्लक | Balance |
| 9 | तरतूद | Provision |
| 10 | व्याज | Interest |

**Action:** `निश्चित` (Confirm).

**Summary:** एकूण शिल्लक, एकूण तरतूद, एकूण व्याज, एकूण व्याज + एकूण तरतूद.

**Footer:** `प्रोसीडिंग`, `परत`.

---

## Cross-Links

- [overview.md](overview.md)
- [manual-interest-provision-screen.md](manual-interest-provision-screen.md)
- [../savings/manual-interest-calculation-screen.md](../savings/manual-interest-calculation-screen.md)
