# Report Spec — Purvani (पुरवणी)

## Purpose

Supplement report listing voucher-level transactions across GL heads for a date range. Supports daily format grouping with opening and closing debit/credit balance summary.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | पुरवणी | Purvani (Supplement) |
| Breadcrumb | डॅशबोर्ड > अहवाल > पुरवणी | Dashboard > Reports > Purvani |
| Parent Module | लेखा / अहवाल | Accounting / Reports |

## Reference Screenshots

| File | Section |
| :--- | :--- |
| `screenshots/Reports/purvani.png` | Filters, opening balance, grid, closing balance |

---

## शोध फिल्टर (Search Filters)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | फॉर्मेट निवडा | Select Format | Dropdown | Yes | e.g. `रोजानुसार` (Daily) |
| 2 | व्यवहार दिनांकापासून | Transaction Date From | Date | Yes | e.g. `01.04.2026` |
| 3 | ते व्यवहार दिनांकापर्यंत | To Transaction Date | Date | Yes | e.g. `03.07.2026` |
| 4 | जी.एल. प्रकार | G.L. Type | Autocomplete | No | GL group/type lookup |
| 5 | जी.एल. | G.L. | Autocomplete | No | GL Head lookup |

**Link:** `अतिरिक्त शोध पर्याय` (Additional Search Options).

**Actions:** `शोधा` (Search), `पूर्ववत` (Reset).

---

## Balance Summary (Above Grid)

| # | Marathi Label | English Label | Notes |
| :---: | :--- | :--- | :--- |
| 1 | सुरवातीची शिल्लक | Opening Balance | e.g. `११८८०००.०० नावे` (Debit) |

---

## Results Grid

| # | Marathi Column | English Column | Notes |
| :---: | :--- | :--- | :--- |
| 1 | अ.क्र. | Sr. No. | — |
| 2 | जी.एल. प्रकार | G.L. Type | Numeric GL type code |
| 3 | व्हाउचर क्र. | Voucher No. | — |
| 4 | खाते क्र. | Account No. | — |
| 5 | ग्राहकाचे नाव | Customer Name | Account holder or office name |
| 6 | रोख | Cash | — |
| 7 | ट्रान्सफर | Transfer | — |
| 8 | एकूण | Total | Cash + Transfer |
| 9 | दिनांक | Date | Transaction date |
| 10 | जी.एल. | G.L. | GL head name — e.g. `वसुल भाग भांडवल`, `मुदतपूर्व एजंट कमिशन` |

---

## Balance Summary (Below Grid)

| # | Marathi Label | English Label | Notes |
| :---: | :--- | :--- | :--- |
| 1 | शिल्लक | Closing Balance | e.g. `१२७२४१५.०० नावे` (Debit) |

**Footer action:** `रिपोर्ट` — generates printable purvani report.

---

## Related Documents

- [overview.md](overview.md)
- [daybook-report.md](daybook-report.md)
- [gl-wise-report.md](gl-wise-report.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
- [../accounting/overview.md](../accounting/overview.md)
