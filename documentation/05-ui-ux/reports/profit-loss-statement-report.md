# Report Spec — Profit & Loss Statement (नफा-तोटा पत्रक)

## Purpose

Printable comparative income and expenditure statement for two fiscal years. **खर्च (Expenditure)** on the left, **उत्पन्न (Income)** on the right.

## Report Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Report Name | नफा-तोटा पत्रक | Profit & Loss Statement |
| Report Type | Print | — |
| Parent Module | लेखा / अहवाल | Accounting / Reports |
| Pages | 2 | — |

## Reference Screenshots

| File | Section |
| :--- | :--- |
| `screenshots/Reports/profit_loss_statement-page-1.png` | Main expenditure & income groups (page 1) |
| `screenshots/Reports/profit_loss_statement-page-2.png` | Remaining items, totals (page 2) |

---

## Print Header

| # | Marathi Label | English Label | Type | Notes |
| :---: | :--- | :--- | :--- | :--- |
| 1 | नफा-तोटा पत्रक | Profit & Loss Statement | Title | Centered |
| 2 | दिनांक | Date | Label | Report date, top-right |
| 3 | २०२५ — २०२६ | FY 2025–26 | Column header | Prior year |
| 4 | २०२६ — २०२७ | FY 2026–27 | Column header | Current year |

---

## Layout — Two-Column Comparative Table

Column order per side: prior-year amount | line item (with GL code) | current-year amount.

### Left Column — खर्च (Expenditure)

| # | Section / Line Item (Marathi) | English | Notes |
| :---: | :--- | :--- | :--- |
| 1 | चालू नफा | Current Profit | Brought from prior period when applicable |
| 2 | ठेवींवरील व्याज | Interest on Deposits | Group header |
| 3 | सेव्हिंग ठेव व्याज | Saving Deposit Interest | Sub-item |
| 4 | मुदत ठेव व्याज | Fixed Deposit Interest | Sub-item — GL `( ३७ )` |
| 5 | रिकारींग ठेव व्याज | Recurring Deposit Interest | Sub-item |
| 6 | दामदुप्पट व्याज | Damduppat Interest | Sub-item |
| 7 | व्यवस्थापकीय खर्च | Administrative Expenses | Group header |
| 8 | बँक चार्जेस | Bank Charges | GL `( १०४ )` |
| 9 | छपाई व स्टेशनरी | Printing & Stationery | — |
| 10 | नोकर पगार खर्च | Staff Salary | GL `( ११० )` |
| 11 | कोतोली ऑफिस भाडे | Office Rent | GL `( ११७ )` |
| 12 | लाईट बिल | Electricity Bill | GL `( १२६ )` |
| 13 | रीचार्ज व इंटरनेट बिल | Recharge & Internet Bill | GL `( १२७ )` |
| 14 | जाहिरात खर्च | Advertisement | GL `( १२८ )` |
| 15 | मानधन | Honorarium | GL `( १२९ )` |
| 16 | इतर खर्च | Other Expenses | Group header |
| 17 | पिग्मी एजंट कमिशन | Pygmy Agent Commission | GL `( १६ )` |
| 18 | पेट्रोल भत्ता | Petrol Allowance | — |
| 19 | किरकोळ खर्च | Miscellaneous Expenses | GL `( १३० )` |
| 20 | संगणक दुरुस्ती | Computer Maintenance | — |
| 21 | इतर भत्ता | Other Allowance | Group header |
| 22 | प्रवास भत्ता | Travel Allowance | Page 2 — GL `( १५३ )` |

### Right Column — उत्पन्न (Income)

| # | Section / Line Item (Marathi) | English | Notes |
| :---: | :--- | :--- | :--- |
| 1 | कर्जावरील व्याज | Interest on Loans | Group header |
| 2 | जामिनकि कर्ज व्याज | Surety Loan Interest | Sub-item |
| 3 | ठेव तारण कर्ज व्याज | Deposit Mortgage Loan Interest | Sub-item |
| 4 | पिग्मी ठेव तारण कर्ज व्याज | Pygmy Deposit Mortgage Loan Interest | Sub-item |
| 5 | गुंतवणुकीवरील व्याज | Interest on Investments | Group header |
| 6 | श्री हनुमान ग्रामीण… व्याज | Co-op society investment interest | — |
| 7 | केडीसीसी बँक गुंतवणुकी व्याज | KDCC Bank investment interest | — |
| 8 | उज्जीवन फायनान्स बँक व्याज | Ujjivan Finance Bank interest | — |
| 9 | साईनाथ मल्टिस्टेट… व्याज | Sainath Multistate interest | — |
| 10 | इतर उत्पन्न | Other Income | Group header |
| 11 | मुदतपूर्व एजंट कमिशन | Pre-term Agent Commission | GL `( ११ )` |
| 12 | कर्जदार कल्याण निधी | Borrower Welfare Fund | GL `( १२१ )` |
| 13 | ब वर्ग सभासद फी | B Class Member Fee | GL `( १२२ )` |
| 14 | प्रोसेस फी | Process Fee | GL `( १२३ )` |
| 15 | स्टेशनरी फी | Stationery Fee | GL `( १२४ )` |
| 16 | कर्ज मागणी अर्ज | Loan Application Form | GL `( १२५ )` |
| 17 | चालू तोटा | Current Loss | When applicable |
| 18 | बँकेचे व्याज मिळाले | Bank Interest Received | Group header |
| 19 | के.डी.सी.सी. बँक व्याज | KDCC Bank interest | — |
| 20 | साईनाथ मल्टिस्टेट… करंट खाते व्याज | Sainath Multistate current account interest | — |
| 21 | कोल्हापूर चालू खाते व्याज | Kolhapur current account interest | — |

---

## Totals Row (Page 2)

| Marathi | English | Rule |
| :--- | :--- | :--- |
| एकूण : | Total : | Expenditure total must equal income total for each fiscal year |

---

## Print Footer

| # | Marathi Label | English Label |
| :---: | :--- | :--- |
| 1 | प्रिंट दिनांक | Print Date |
| 2 | प्रिंट द्वारा | Printed By |
| 3 | पृ.क्र. | Page Number — `1 / 2`, `2 / 2` |

---

## Related Documents

- [overview.md](overview.md)
- [balance-sheet-report.md](balance-sheet-report.md)
- [trial-balance-report.md](trial-balance-report.md)
- [../accounting/overview.md](../accounting/overview.md)
