# Report Spec — Balance Sheet (ताळेबंद)

## Purpose

Printable comparative balance sheet showing **भाग व भांडवल देणी (Liabilities & Capital)** and **मालमत्ता व येणी (Assets & Receivables)** side by side for two fiscal years.

## Report Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Report Name | ताळेबंद | Balance Sheet |
| Report Type | Print | — |
| Parent Module | लेखा / अहवाल | Accounting / Reports |
| Pages | 2 | — |

## Reference Screenshots

| File | Section |
| :--- | :--- |
| `screenshots/Reports/Balance-Sheet-Page-1.png` | Main body — liabilities & assets (page 1) |
| `screenshots/Reports/Balance-Sheet-Page-2.png` | Continuation — assets, totals (page 2) |

---

## Print Header

| # | Marathi Label | English Label | Type | Notes |
| :---: | :--- | :--- | :--- | :--- |
| 1 | ताळेबंद | Balance Sheet | Title | Centered |
| 2 | दिनांक | Date | Label | Report date, top-right |
| 3 | २०२५ — २०२६ | FY 2025–26 | Column header | Prior year amount column |
| 4 | २०२६ — २०२७ | FY 2026–27 | Column header | Current year amount column |

---

## Layout — Two-Column Comparative Table

Each side has three amount/description columns: prior-year amount | line item | current-year amount. GL account codes appear in parentheses beside line items.

### Left Column — भाग व भांडवल देणी (Liabilities & Capital)

| # | Section / Line Item (Marathi) | English | Notes |
| :---: | :--- | :--- | :--- |
| 1 | अधिकृत भाग भांडवल | Authorized Share Capital | — |
| 2 | वसुल भाग भांडवल | Paid-up Share Capital | GL code e.g. `( १ )` |
| 3 | इतर निधी | Other Funds | Group header |
| 4 | रिझर्व फंड | Reserve Fund | Sub-item |
| 5 | ठेवी | Deposits | Group header with subtotal |
| 6 | पिग्मी ठेव | Pygmy Deposit | Sub-item |
| 7 | सेव्हिंग ठेव | Saving Deposit | Sub-item |
| 8 | मुदत ठेव | Fixed Deposit | Sub-item |
| 9 | रिकारींग ठेव | Recurring Deposit | Sub-item |
| 10 | दामदुप्पट | Damduppat (Double Money) | Sub-item |
| 11 | पेंशन ठेव | Pension Deposit | Sub-item |
| 12 | देणे व्याज | Interest Payable | Group header |
| 13 | इतर देणी व तरतुदी | Other Liabilities & Provisions | Group header |
| 14 | प्रवेश फी | Admission Fee | Sub-item |
| 15 | नफा | Profit | Shown on liability side when applicable |

### Right Column — मालमत्ता व येणी (Assets & Receivables)

| # | Section / Line Item (Marathi) | English | Notes |
| :---: | :--- | :--- | :--- |
| 1 | रोख व बँकेतील शिल्लक | Cash & Bank Balances | Group header |
| 2 | रोख शिल्लक | Cash Balance | Sub-item |
| 3 | के.डी.सी.सी. बँक | KDCC Bank | Bank sub-account |
| 4 | बँक ऑफ इंडिया | Bank of India | Bank sub-account |
| 5 | कुंभी कासरी सहकारी बँक | Kumbhi Kasari Co-op Bank | Bank sub-account |
| 6 | उज्जीवन स्मॉल फायनान्स बँक | Ujjivan Small Finance Bank | Bank sub-account |
| 7 | गुंतवणूक | Investments | Group header |
| 8 | कर्ज | Loans | Group header |
| 9 | जामिनकि कर्ज | Surety Loan | Sub-item |
| 10 | स्थावर तारण कर्ज | Immovable Mortgage Loan | Sub-item |
| 11 | पिग्मी ठेव तारण कर्ज | Pygmy Deposit Mortgage Loan | Sub-item |
| 12 | मालमत्ता | Fixed Assets | Group header |
| 13 | डेडस्टॉक खाते | Deadstock Account | Sub-item |
| 14 | फर्निचर अँड फिक्स्चर | Furniture & Fixtures | Sub-item |
| 15 | संगणक व प्रिंटर | Computer & Printer | Sub-item |
| 16 | सॉफ्टवेअर | Software | Page 2 — GL `( १०८ )` |
| 17 | इलेक्ट्रिक फिटिंग | Electric Fitting | Page 2 — GL `( १०९ )` |
| 18 | येणे व्याज | Interest Receivable | Group header |
| 19 | तोटा | Loss | Shown on asset side when applicable |
| 20 | संचित तोटे | Accumulated Losses | GL `( २० )` |

---

## Totals Row (Page 2)

| Marathi | English | Rule |
| :--- | :--- | :--- |
| एकूण : | Total : | Liability total must equal asset total for each fiscal year |

---

## Print Footer

| # | Marathi Label | English Label | Position |
| :---: | :--- | :--- | :--- |
| 1 | रिपोर्ट दिनांक | Report Date | Bottom-left |
| 2 | Print By | Printed By | Bottom-center (user name) |
| 3 | Page No | Page Number | Bottom-right — e.g. `1 / 2`, `2 / 2` |

---

## Related Documents

- [overview.md](overview.md)
- [trial-balance-report.md](trial-balance-report.md)
- [profit-loss-statement-report.md](profit-loss-statement-report.md)
- [../accounting/overview.md](../accounting/overview.md)
