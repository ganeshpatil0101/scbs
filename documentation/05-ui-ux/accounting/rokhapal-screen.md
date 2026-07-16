# Screen Spec — Rokhapal / Cashier (लेखा > रोखपाल)

## Purpose

UI specification for cashier transactions with denomination tracking.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | रोखपाल | Cashier |
| Breadcrumb | डॅशबोर्ड > लेखा > रोखपाल | Dashboard > Accounting > Cashier |
| Parent Module | लेखा | Accounting |

## Reference Media

| File | Section |
| :--- | :--- |
| `screenshots/lekha/डॅशबोर्ड-लेखा-रोखपाल.mp4` | Full screen |
| `screenshots/lekha/rokhapal-frames/` | Extracted frames — transaction form, history grid, summary |

---

## Section: व्यवहार (Transaction)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | व्यवहार प्रकार | Transaction Type | Radio | No | `नावे` (Debit) / `जमा` (Credit). Default: `जमा` |
| 2 | व्हाउचर क्र. | Voucher No. | Textbox | No | — |
| 3 | अपूर्ण स्क्रोल निवडा | Select Incomplete Scroll | Dropdown | No | Loaded dynamically — open/incomplete scroll numbers for current cashier session. Optional; empty when none |
| 4 | शाखा निवडा | Select Branch | Autocomplete | Yes | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 5 | जी.एल. निवडा | Select GL | Autocomplete | Yes | Sample: `38 — Saving`, `91 — FD`, `42 — Loan`. Enter resolves by ID or name; shows display name |
| 6 | खातेधारक निवडा | Select Account Holder | Autocomplete | Yes | Sample: `101 — Account Holder 1`, `102 — Account Holder 2`, `103 — Account Holder 3`. Enter resolves by ID or name; shows display name |
| 7 | शिल्लक | Balance | Textbox | No | Read-only |
| 8 | पॅनकार्ड - आधार क्र. | PAN - Aadhaar No. | Textbox | No | — |
| 9 | रक्कम (रु.) | Amount (Rs.) | Textbox | Yes | — |
| 10 | अक्षरी रक्कम | Amount in Words | Textbox | No | Read-only |
| 11 | दंडाची रक्कम (रु.) | Penalty Amount (Rs.) | Textbox | No | — |
| 12 | विशेष सुचना | Special Instructions | Textbox | No | — |
| 13 | रोखपाल तपशिल | Cashier Details | Textbox | No | — |
| 14 | स्क्रोल | Scroll | Textbox | No | e.g. `20` |

## Section: नोटांचा तपशिल (Denomination Details)

Single-sided denomination grid for the current cash transaction (notes received on `जमा`, notes paid on `नावे`). Denomination row set matches [note-exchange-screen.md](note-exchange-screen.md).

**Rows (denominations):** `2000`, `1000`, `500`, `200`, `100`, `50`, `20`, `10`, `5`, `2`, `1`, `नाणी` (Coins).

| # | Marathi Column | English Column | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 15 | उपलब्ध | Available | Read-only | — | Cashier drawer stock per denomination |
| 16 | नोटांची संख्या | Number of Notes | Textbox | Yes | Per row when capturing denomination |
| 17 | रक्कम (रु.) | Amount (Rs.) | Read-only | — | Calculated: denomination × note count |

**Footer row:** `एकूण` (Total) — total note count and total amount.

**Actions (above history filter):** `पूर्ण`, `पुनर्वत`.

## Transaction History Filter

| # | Marathi Label | English Label | Type | Values / Notes |
| :---: | :--- | :--- | :--- | :--- |
| 18 | Filter | Last / Debit / All / Credit transactions | Radio | `शेवटचा व्यवहार`, `नावे व्यवहार`, `सर्व व्यवहार`, `जमा व्यवहार`. Default: `शेवटचा व्यवहार` |

**Action:** `दाखवा` (Show).

## Transaction History Grid

Columns: निवडा, अ.क्र., स्क्रोल, नावे, जमा, खाते माहिती, तपशील, युजर, नोटांचा तपशील.

**Action:** `काढा` (Remove).

## Cash Summary (below history grid)

| # | Marathi Label | English Label | Type | Values / Notes |
| :---: | :--- | :--- | :--- | :--- |
| 19 | सुरवातीची शिल्लक | Opening Balance | Label | Read-only |
| 20 | एकूण जमा | Total Credit | Label | Read-only |
| 21 | एकूण नावे | Total Debit | Label | Read-only |
| 22 | हातातील रोख शिल्लक | Cash in Hand Balance | Label | Read-only |

---

## Mockup

| Property | Value |
| :--- | :--- |
| HTML mockup | [mockups/accounting/rokhapal-screen/index.html](../mockups/accounting/rokhapal-screen/index.html) |
| Review guide | [mockups/accounting/rokhapal-screen/README.md](../mockups/accounting/rokhapal-screen/README.md) |
| Status | Draft |

## Related Documents

- [overview.md](overview.md)
- [note-exchange-screen.md](note-exchange-screen.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
