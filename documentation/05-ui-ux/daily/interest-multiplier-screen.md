# Screen Spec — Daily Interest Multiplier (डेली > व्याज गुणक)

## Purpose

UI specification for calculating daily (pigmy) deposit interest and maturity amounts.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | व्याज गुणक | Interest Multiplier |
| Breadcrumb | डॅशबोर्ड > ठेवी > व्याज गुणक | Dashboard > Deposits > Interest Multiplier |
| Parent Module | डेली | Daily |

> **Note:** Breadcrumb in screenshot shows `ठेवी` (Deposits); screen is used for pigmy/daily scheme calculation.

## Reference Screenshots

| File | Section |
| :--- | :--- |
| `screenshots/डेली/डॅशबोर्ड_डेली_व्याज गुणक.png` | Full screen |

---

## Input Fields

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | योजना निवडा | Select Scheme | Dropdown | Yes | Loaded dynamically from Daily schemes (Settings > नवीन योजना). Sample: `डेली १`, `डेली २`, `पिग्मी ठेव` |
| 2 | सरळ / चक्रवाढ | Simple / Compound | Radio | No | — |
| 3 | मासिक / तिमाही / सहामाही / वार्षिक | Monthly / Quarterly / Half-yearly / Yearly | Radio | No | When compound selected |
| 4 | ठेव रक्कम (रु.) | Deposit Amount (Rs.) | Textbox | Yes | — |
| 5 | कालावधी (महिने) | Duration (Months) | Label (read-only) | Yes | Auto-filled from selected scheme; default `12` |
| 6 | व्याज दर (% पी.ए) | Interest Rate (% p.a.) | Label (read-only) | Yes | Auto-filled from selected scheme; default `6` |

**Formulas displayed:**
- मासिक संग्रह = ठेव रक्कम × 365/12
- एकूण रक्कम = मासिक संग्रह × कालावधी

### Output (Read-only)

| # | Marathi Label | English Label |
| :---: | :--- | :--- |
| 7 | एकूण रक्कम (रु.) | Total Amount (Rs.) |
| 8 | व्याज रक्कम (रु.) | Interest Amount (Rs.) |
| 9 | मुदतपूर्ती रक्कम | Maturity Amount |

**Actions:** `गणना करा` (Calculate), `पुनर्रचना करा` (Reset).

---

## दैनिक व्याज चार्ट (Daily Interest Chart) Grid

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | अ. क्र. | Sr. No. |
| 2 | ठेव रक्कम | Deposit Amount |
| 3 | मासिक व्याज | Monthly Interest |
| 4 | दिलेले व्याज | Interest Paid |
| 5 | मासिक शिल्लक | Monthly Balance |

**Action:** `निश्चित करा` (Confirm).

---

## Cross-Links

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [../settings/schemes/new-scheme-screen.md](../settings/schemes/new-scheme-screen.md)
