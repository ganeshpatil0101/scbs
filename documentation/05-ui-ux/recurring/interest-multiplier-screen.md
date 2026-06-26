# Screen Spec — Recurring Interest Multiplier (रिकरिंग > व्याज गुणक)

## Purpose

UI specification for calculating recurring deposit maturity amounts and interest breakdown.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | व्याज गुणक | Interest Multiplier |
| Breadcrumb | डॅशबोर्ड > रिकरिंग > व्याज गुणक | Dashboard > Recurring > Interest Multiplier |
| Parent Module | रिकरिंग | Recurring |

## Reference Screenshots

| File | Section |
| :--- | :--- |
| `screenshots/रिकरिंग/डॅशबोर्ड_रिकरिंग_व्याज गुणक.png` | Full screen |

---

## Input Fields

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | योजना निवडा | Select Scheme | Dropdown | Yes | e.g. `रिकरिंग ठेव` |
| 2 | सरळ / चक्रव्याज | Simple / Compound | Radio | No | — |
| 3 | मासिक / तिमाही / सहामाही / वार्षिक | Compounding Frequency | Radio | No | e.g. `वार्षिक` |
| 4 | मासिक ठेव रक्कम (रु.) | Monthly Deposit Amount (Rs.) | Textbox | Yes | — |
| 5 | कालावधी (महिने) | Duration (Months) | Textbox | Yes | Default: `60` |
| 6 | व्याज दर (% पीए) | Interest Rate (% p.a.) | Textbox | Yes | Default: `12.37` |

### Output (Read-only)

| # | Marathi Label | English Label |
| :---: | :--- | :--- |
| 7 | ठेव रक्कम (रु.) | Deposit Amount (Rs.) |
| 8 | व्याज रक्कम (रु.) | Interest Amount (Rs.) |
| 9 | मुदतपूर्ती रक्कम | Maturity Amount |

**Actions:** `गणना करा` (Calculate), `पुनर्रचना करा` (Reset).

---

## व्याज प्रकार (Interest Breakdown) Grid

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | अ. क्र. | Sr. No. |
| 2 | ठेव रक्कम | Deposit Amount |
| 3 | मासिक व्याज | Monthly Interest |
| 4 | पोस्टिंग व्याज | Posting Interest |
| 5 | मासिक शिल्लक | Monthly Balance |

**Action:** `निर्यात करा` (Export).

---

## Cross-Links

- [overview.md](overview.md)
- [new-recurring-account-screen.md](new-recurring-account-screen.md)
