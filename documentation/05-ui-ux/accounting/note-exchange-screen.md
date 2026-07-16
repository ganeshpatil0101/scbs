# Screen Spec — Note Exchange (लेखा > नोटांची अदलाबदल)

## Purpose

UI specification for cashier denomination exchange (notes in / notes out).

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | नोटांची अदलाबदल | Note Exchange |
| Breadcrumb | डॅशबोर्ड > लेखा > नोटांची अदलाबदल | Dashboard > Accounting > Note Exchange |
| Parent Module | लेखा | Accounting |

## Reference Screenshots

| File | Section |
| :--- | :--- |
| `screenshots/lekha/डॅशबोर्ड-लेखा-नोटांची अदलाबदल.png` | Denomination grid |

---

## Denomination Grid

Rows for denominations: `2000`, `1000`, `500`, `200`, `100`, `50`, `20`, `10`, `5`, `2`, `1`, `नाणी` (Coins).

### Section: मध्ये (In)

| # | Marathi Column | English Column | Type |
| :---: | :--- | :--- | :--- |
| 1 | उपलब्ध | Available | Read-only |
| 2 | नोटांची संख्या | Number of Notes | Textbox (required per row) |
| 3 | रक्कम (रु.) | Amount (Rs.) | Read-only (calculated) |

### Section: बाहेर (Out)

| # | Marathi Column | English Column | Type |
| :---: | :--- | :--- | :--- |
| 4 | नोटांची संख्या | Number of Notes | Textbox |
| 5 | रक्कम (रु.) | Amount (Rs.) | Read-only |
| 6 | शिल्लक | Balance | Read-only |

**Footer row:** `एकूण` (Total) for In and Out counts and amounts.

## Summary Fields

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | फरक | Difference | Textbox | No | Read-only |
| 2 | Cashier's Narration | Cashier's Narration | Textbox | No | English label on UI |

**Action:** `कर` (Submit) — blue button.

---

## Mockup

| Property | Value |
| :--- | :--- |
| HTML mockup | [mockups/accounting/note-exchange-screen/index.html](../mockups/accounting/note-exchange-screen/index.html) |
| Review guide | [mockups/accounting/note-exchange-screen/README.md](../mockups/accounting/note-exchange-screen/README.md) |
| Status | Draft |

## Related Documents

- [overview.md](overview.md)
- [rokhapal-screen.md](rokhapal-screen.md)
