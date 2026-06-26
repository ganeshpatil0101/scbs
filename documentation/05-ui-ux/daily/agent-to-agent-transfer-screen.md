# Screen Spec — Agent to Agent Transfer (डेली > एजंट > एजंट कडून एजंट कडे खाते ट्रान्सफर)

## Purpose

UI specification for transferring daily accounts from one agent to another.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | एजंट कडून एजंट कडे खाते ट्रान्सफर | Agent to Agent Account Transfer |
| Breadcrumb | डॅशबोर्ड > डेली > एजंट > एजंट कडून एजंट कडे खाते ट्रान्सफर | Dashboard > Daily > Agent > Agent to Agent Transfer |
| Parent Module | डेली | Daily |

## Reference Screenshots

| File | Section |
| :--- | :--- |
| `screenshots/डेली/डॅशबोर्ड_डेली_एजंट_एजंट कडून एजंट कडे खाते ट्रान्सफर.png` | Full screen |

---

## Form Fields

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | एजंट क्र. (कडून) | Agent No. (From) | Textbox + Dropdown | Yes | Values: `TODO` |
| 2 | एजंट क्र. (कडे) | Agent No. (To) | Textbox + Dropdown | Yes | Values: `TODO` |
| 3 | सर्व निवडा | Select All | Checkbox | No | — |

---

## Results Grid

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | अ. क्र. | Sr. No. |
| 3 | खाते | Account |
| 4 | खाते क्र. | Account No. |
| 5 | नाव | Name |
| 6 | शिल्लक | Balance |

**Action:** `निर्यात करा` (Export).

---

## Cross-Links

- [overview.md](overview.md)
- [new-agent-screen.md](new-agent-screen.md)
