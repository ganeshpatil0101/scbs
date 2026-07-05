# Report Spec — GL Wise Report (जनरल लेजर / जी.एल.)

## Purpose

Screen to view day-wise debit/credit/balance for a selected GL head over a date range, with printable report output.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | जनरल लेजर (जी.एल.) | General Ledger (G.L.) |
| Breadcrumb | डॅशबोर्ड > अहवाल > जनरल लेजर | Dashboard > Reports > General Ledger |
| Parent Module | लेखा / अहवाल | Accounting / Reports |

## Reference Screenshots

| File | Section |
| :--- | :--- |
| `screenshots/Reports/G.L.wise-report.png` | Filter bar, results grid, Report button |

---

## शोध फिल्टर (Search Filters)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | जी.एल. | G.L. | Autocomplete | Yes | Single GL Head lookup — e.g. `12 — एजंट भरणा` |
| 2 | व्यवहार दिनांकापासून | Transaction Date From | Date | Yes | e.g. `01.07.2026` |
| 3 | ते व्यवहार दिनांकापर्यंत | To Transaction Date | Date | Yes | e.g. `05.07.2026` |

**Actions:** `शोधा` (Search), `पूर्ववत` (Reset).

---

## Results Grid

| # | Marathi Column | English Column | Notes |
| :---: | :--- | :--- | :--- |
| 1 | अ.क्र. | Sr. No. | — |
| 2 | दिनांक | Date | One row per business date in range |
| 3 | जी.एल. | G.L. | GL head name |
| 4 | आरंभी शिल्लक | Opening Balance | Balance at start of day |
| 5 | नावे | Debit | Total debit for the day |
| 6 | जमा | Credit | Total credit for the day |
| 7 | शिल्लक | Balance | Closing balance for the day |

**Footer action:** `रिपोर्ट` — generates printable GL-wise report from current filter and grid data.

---

## Related Documents

- [overview.md](overview.md)
- [daybook-report.md](daybook-report.md)
- [purvani-report.md](purvani-report.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
- [../accounting/overview.md](../accounting/overview.md)
