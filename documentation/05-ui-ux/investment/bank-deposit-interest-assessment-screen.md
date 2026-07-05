# Screen Spec — Bank Deposit Interest Assessment (गुंतवणूक > बँक ठेव > व्याज आकारणी)

## Purpose

UI specification for calculating and posting interest on bank deposit accounts.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | व्याज आकारणी | Interest Assessment |
| Breadcrumb | डॅशबोर्ड > गुंतवणूक > बँक ठेव > व्याज आकारणी | Dashboard > Investment > Bank Deposit > Interest Assessment |
| Parent Module | गुंतवणूक > बँक ठेव | Investment > Bank Deposit |

## Reference Screenshots

| File | Section |
| :--- | :--- |
| `screenshots/गुंतवणूक/डॅशबोर्ड-गुंतवणूक-बँक ठेव-व्याज आकारणी.png` | Full screen |

---

## Filter Section

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा कोड | Branch Code | Textbox | Yes | e.g. `1` |
| 2 | शाखा निवडा | Select Branch | Dropdown | Yes | e.g. `कोतोली मुख्य कार्यालय` |
| 3 | बँक जीएल हेड नं | Bank G.L. Head No. | Textbox | No | — |
| 4 | बँक निवडा | Select Bank | Dropdown | Yes | Multi-select supported |
| 5 | पोस्ट दिनांक | Post Date | Date | Yes | — |
| 6 | खाते | Account | Textbox | No | — |
| 7 | खाते क्रमांकामधून | From Account Number | Textbox | No | — |
| 8 | खाते क्रमांक | Account Number | Textbox | No | — |

**Action:** `गणना करा` (Calculate).

---

## Results Grid

**Select all:** `सर्व निवडा`.

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | अ. क्र. | Sr. No. |
| 3 | खाते क्रमांक | Account Number |
| 4 | खाते नाव | Account Name |
| 5 | प्रारंभ तारीख | Start Date |
| 6 | व्याज तारीख | Interest Date |
| 7 | व्याज दर | Interest Rate |
| 8 | शिल्लक | Balance |
| 9 | तरतूद | Provision |
| 10 | व्याज | Interest |
| 11 | टीडीएस (रु.) | TDS (Rs.) |

**Summary:** एकूण शिल्लक, एकूण तरतूद, एकूण व्याज, एकूण टीडीएस.

**Actions:** `पोस्ट`, `पूर्ववत`.

---

## Related Documents

- [overview.md](overview.md)
- [bank-deposit-interest-provision-screen.md](bank-deposit-interest-provision-screen.md)
- [../savings/manual-interest-calculation-screen.md](../savings/manual-interest-calculation-screen.md)
