# Screen Spec — Manual Interest Calculation (बचत > मॅन्युअल व्याज > आकारणी)

## Purpose

UI specification for manually calculating and posting savings interest.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | मॅन्युअल व्याज आकारणी | Manual Interest Calculation |
| Breadcrumb | डॅशबोर्ड > बचत > मॅन्युअल व्याज > आकारणी | Dashboard > Savings > Manual Interest > Calculation |
| Parent Module | बचत | Savings |

## Reference Screenshots

| File | Section |
| :--- | :--- |
| `screenshots/bachat/डॅशबोर्ड-बचत-मॅन्युअल व्याज-आकारणी.png` | Full screen |

---

## Filter Section

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा निवडा | Select Branch | Autocomplete | No | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 2 | खाते क्र. | Account No. | Textbox | No | e.g. `55` |
| 3 | खाते | Account | Dropdown | No | e.g. `सेव्हिंग ठेव` (Saving Deposit) |
| 4 | पोस्टिंग दिनांक निवडा | Select Posting Date | Dropdown | No | e.g. `31.03.2026` |
| 5 | पोस्टिंग दिनांक | Posting Date | Date | No | e.g. `31.03.2026` |
| 6 | खाते क्र. (पासून) | Account No. (From) | Textbox | No | — |
| 7 | खाते क्र. (पर्यंत) | Account No. (To) | Textbox | No | — |
| 8 | ॲडव्हान्स शोध | Advanced Search | Link | No | — |

**Action:** `व्याज गणना करा` (Calculate Interest) — blue button.

---

## Results Grid

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | अनु. क्र | Sr. No. |
| 3 | खाते क्रमांक | Account Number |
| 4 | सभासदाचे नाव | Member Name |
| 5 | चालू दिनांक | Current Date |
| 6 | अंतिम व्याज दिनांक | Final Interest Date |
| 7 | व्याज दर | Interest Rate |
| 8 | शिल्लक | Balance |
| 9 | तरतूद | Provision |
| 10 | व्याज | Interest |

**Select all:** `सर्व निवडा`. **Info note:** provision message when duration below scheme minimum.

**Grid action:** `निर्यात करा` (Export).

---

## Footer

| Field | Marathi | English |
| :--- | :--- | :--- |
| Totals | एकूण तरतूद, एकूण व्याज, एकूण शिल्लक, एकूण व्याज + एकूण तरतूद | Total Provision, Total Interest, Total Balance, Combined Total |

**Actions:** `पोस्ट` (Post), `पूर्ववत` (Reset).

---

## Related Documents

- [overview.md](overview.md)
- [savings-transaction-screen.md](savings-transaction-screen.md)
