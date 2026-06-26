# Screen Spec — FD Manual Interest Calculation (मुदत ठेव > मॅन्युअल व्याज आकारणी)

## Purpose

UI specification for manually calculating and posting fixed deposit interest.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | मॅन्युअल व्याज आकारणी | Manual Interest Calculation |
| Breadcrumb | डॅशबोर्ड > मुदत ठेव > मॅन्युअल व्याज आकारणी | Dashboard > Fixed Deposit > Manual Interest Calculation |
| Parent Module | मुदत ठेव | Fixed Deposit |

## Reference Screenshots

| File | Section |
| :--- | :--- |
| `screenshots/मुदत ठेव/डॅशबोर्ड_मुदत ठेव_ मॅन्युअल व्याज_आकारणी.png` | Full screen |

---

## Filter Section

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा कोड | Branch Code | Textbox | Yes | e.g. `1` |
| 2 | शाखा निवडा | Select Branch | Dropdown | Yes | e.g. कोतोली मुख्य कार्यालय |
| 3 | जी.एल. हेड निवडा | Select G.L. Head | Dropdown | Yes | Values: `TODO` |
| 4 | व्याज दिनांक निवडा | Select Interest Date | Dropdown | Yes | Values: `TODO` |
| 5 | व्याज पोस्ट दिनांक | Interest Post Date | Date | No | — |
| 6 | खाते क्र. पासून | Account No. From | Textbox | No | — |
| 7 | खाते क्र. पर्यंत | Account No. To | Textbox | No | — |
| 8 | स्थिती | Status | Dropdown | No | e.g. `सर्व` |

**Link:** `अॅडव्हान्स शोध` (Advance Search).

**Action:** `व्याज गणना करा` (Calculate Interest).

---

## Results Grid

**Select all:** `सर्व निवडा`.

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | अ. क्र. | Sr. No. |
| 3 | खाते क्र. | Account No. |
| 4 | खाते धारकाचे नाव | Account Holder Name |
| 5 | चालू दिनांक | Start Date |
| 6 | व्याज दिनांक | Interest Date |
| 7 | व्याज दर | Interest Rate |
| 8 | शिल्लक | Balance |
| 9 | तरतूद | Provision |
| 10 | वर्तमान व्याज | Current Interest |
| 11 | सवलत दर | Concession Rate |

**Action:** `उल्लेख करा` (Process).

**Summary:** एकूण शिल्लक, एकूण तरतूद, एकूण व्याज, एकूण व्याज + एकूण तरतूद.

**Footer:** `पोस्टिंग`, `पुनर्रचना करा`.

---

## Cross-Links

- [overview.md](overview.md)
- [../savings/manual-interest-calculation-screen.md](../savings/manual-interest-calculation-screen.md)
