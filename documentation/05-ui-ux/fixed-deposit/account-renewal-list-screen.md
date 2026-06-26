# Screen Spec — Account Renewal List (मुदत ठेव > खाते नूतनीकरण यादी)

## Purpose

UI specification for viewing fixed deposit account renewal history.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | खाते नूतनीकरण यादी | Account Renewal List |
| Breadcrumb | डॅशबोर्ड > मुदत ठेव > खाते नूतनीकरण यादी | Dashboard > Fixed Deposit > Account Renewal List |
| Parent Module | मुदत ठेव | Fixed Deposit |

## Reference Screenshots

| File | Section |
| :--- | :--- |
| `screenshots/मुदत ठेव/डॅशबोर्ड_मुदत ठेव_खाते नूतनीकरण यादी.png` | Full screen |

---

## Filter Section

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा कोड | Branch Code | Textbox | No | e.g. `1` |
| 2 | शाखेचे नाव | Branch Name | Dropdown | No | e.g. कोतोली मुख्य कार्यालय |
| 3 | योजना | Scheme | Dropdown | No | e.g. `सर्व` |
| 4 | खातेधारक | Account Holder | Textbox | No | — |
| 5 | खाते क्र. (पासून) | Account No. (From) | Textbox | No | — |
| 6 | खाते क्र. (पर्यंत) | Account No. (To) | Textbox | No | — |
| 7 | ग्राहक क्र. (पासून) | Customer No. (From) | Textbox | No | — |
| 8 | ग्राहक क्र. (पर्यंत) | Customer No. (To) | Textbox | No | — |
| 9 | तारीख नूतनीकरण (पासून) | Renewal Date (From) | Date | No | — |
| 10 | तारीख नूतनीकरण (पर्यंत) | Renewal Date (To) | Date | No | — |
| 11 | पावती क्रमांक | Receipt Number | Textbox | No | — |

**Action:** `दाखवा` (Show).

---

## Results Grid

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | अनु. क्र | Sr. No. |
| 2 | खाते शाखा | Account Branch |
| 3 | खाते क्र. | Account No. |
| 4 | खातेधारक | Account Holder |
| 5 | तारीख नूतनीकरण | Renewal Date |
| 6 | चालू दिनांक | Current Date |
| 7 | रक्कम | Amount |
| 8 | मुदतीअंती रक्कम | Maturity Amount |
| 9 | कालावधी महिने | Duration (Months) |
| 10 | कालावधी दिवसात | Duration (Days) |
| 11 | व्याज दर | Interest Rate |
| 12 | मुदतपूर्ती दिनांक | Maturity Date |

**Action:** `निर्यात करा` (Export).

---

## Cross-Links

- [overview.md](overview.md)
- [new-fd-account-screen.md](new-fd-account-screen.md)
