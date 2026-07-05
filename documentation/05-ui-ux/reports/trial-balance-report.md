# Report Spec — Trial Balance (तेरीज पत्रक)

## Purpose

Printable trial balance as on a given date. Lists all GL heads grouped under accounting categories with **नावे (Debit)** and **जमा (Credit)** balances. Closing page reconciles totals and shows profit/loss summary.

## Report Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Report Name | तेरीज पत्रक | Trial Balance |
| Report Type | Print | — |
| Parent Module | लेखा / अहवाल | Accounting / Reports |
| Pages | 3 | — |

## Reference Screenshots

| File | Section |
| :--- | :--- |
| `screenshots/Reports/Teriz-patrak-page-1.png` | देणी and येणी categories (page 1) |
| `screenshots/Reports/Teriz-patrak-page-2.png` | खर्च and उत्पन्न GL heads (page 2) |
| `screenshots/Reports/Teriz-patrak-page-3.png` | Grand totals, P&L summary, signatures (page 3) |

---

## Print Header

| # | Marathi Label | English Label | Type | Notes |
| :---: | :--- | :--- | :--- | :--- |
| 1 | तेरीज पत्रक | Trial Balance | Title | Centered |
| 2 | व्यवहार दिनांक | Transaction Date | Label | As-on date |
| 3 | दिनांक | Date | Label | Report date |

---

## Column Structure

| # | Marathi Column | English Column | Notes |
| :---: | :--- | :--- | :--- |
| 1 | अ.क्र. | Sr. No. | Sequential across all GL heads |
| 2 | जी.एल.हेड | G.L. Head | Name with GL code in parentheses |
| 3 | शिल्लक > नावे | Balance — Debit | Debit balance amount |
| 4 | शिल्लक > जमा | Balance — Credit | Credit balance amount |

Category group headers show subtotals in the नावे or जमा column as applicable.

---

## Section — देणी (Liabilities / Credit Balances) — Page 1

| # | Category (Marathi) | English | Example GL Heads |
| :---: | :--- | :--- | :--- |
| 1 | वसुल भाग भांडवल | Paid-up Share Capital | `( १ )` |
| 2 | इतर निधी | Other Funds | रिझर्व्ह फंड `( १४९ )` |
| 3 | ठेवी | Deposits | पिग्मी, सेव्हिंग, मुदत, रिकारींग, दामदुप्पट, पेंशन |
| 4 | देणे व्याज | Interest Payable | मुदत ठेव व्याज देणे `( ६० )` |
| 5 | इतर देणी व तरतुदी | Other Liabilities & Provisions | प्रवेश फी `( ५४ )` |

---

## Section — येणी (Assets / Debit Balances) — Page 1

| # | Category (Marathi) | English | Example GL Heads |
| :---: | :--- | :--- | :--- |
| 1 | रोख व बँकेतील शिल्लक | Cash & Bank Balances | रोख, KDCC, BOI, Kumbhi Kasari, Ujjivan, Sainath |
| 2 | गुंतवणूक | Investments | Various co-op societies, liquid funds |
| 3 | कर्ज | Loans | जामिनकि, स्थावर तारण, पिग्मी ठेव तारण |
| 4 | मालमत्ता | Fixed Assets | डेडस्टॉक, फर्निचर, संगणक, सॉफ्टवेअर, इलेक्ट्रिक फिटिंग |

---

## Section — Continuation — Page 2

| # | Category (Marathi) | English | Example GL Heads |
| :---: | :--- | :--- | :--- |
| 1 | येणे व्याज | Interest Receivable | Society interest `( १०१ )` |
| 2 | तोटा | Loss | संचित तोटे `( २० )` |
| 3 | खर्च > ठेवींवरील व्याज | Interest on Deposits | मुदत ठेव व्याज `( ५९ )` |
| 4 | खर्च > व्यवस्थापकीय खर्च | Administrative Expenses | बँक चार्जेस, पगार, स्टेशनरी, भाडे, लाईट, रीचार्ज, जाहिरात, मानधन |
| 5 | खर्च > इतर खर्च | Other Expenses | पिग्मी एजंट कमिशन, किरकोळ खर्च |
| 6 | खर्च > इतर भत्ता | Other Allowance | प्रवास भत्ता `( १५३ )` |
| 7 | उत्पन्न > कर्जावरील व्याज | Interest on Loans | जामिनकी, ठेव तारण, पिग्मी ठेव तारण |
| 8 | उत्पन्न > गुंतवणुकीवरील व्याज | Interest on Investments | KDCC, Ujjivan, Sainath |
| 9 | उत्पन्न > इतर उत्पन्न | Other Income | एजंट कमिशन, कल्याण निधी, सभासद फी, प्रोसेस फी, स्टेशनरी फी, कर्ज अर्ज |
| 10 | उत्पन्न > बँकेचे व्याज मिळाले | Bank Interest Received | Sainath current account `( १६४ )` |

---

## Grand Total Row (Page 3)

| Marathi | English | Rule |
| :--- | :--- | :--- |
| एकूण : | Total : | Total Debit must equal Total Credit |

---

## P&L Summary Box (Page 3)

| # | Marathi Label | English Label | Side |
| :---: | :--- | :--- | :--- |
| 1 | एकूण येणे | Total Receivable (Assets) | Left |
| 2 | एकूण खर्च | Total Expense | Left |
| 3 | एकूण | Total | Left |
| 4 | नफा | Profit | Left |
| 5 | एकूण देणे | Total Payable (Liabilities) | Right |
| 6 | एकूण उत्पन्न | Total Income | Right |
| 7 | एकूण | Total | Right |
| 8 | तोटा | Loss | Right |

---

## Signature Lines (Page 3)

| Position | Marathi | English |
| :--- | :--- | :--- |
| Left | लिपीक | Clerk |
| Center | व्यवस्थापक | Manager |
| Right | अध्यक्ष | Chairman |

## Print Footer

| # | Marathi Label | English Label |
| :---: | :--- | :--- |
| 1 | प्रिंट दिनांक | Print Date |
| 2 | प्रिंट द्वारा | Printed By |
| 3 | पु.क्र. / पृ.क्र. | Page Number — `1/3`, `2/3`, `3/3` |

---

## Related Documents

- [overview.md](overview.md)
- [balance-sheet-report.md](balance-sheet-report.md)
- [profit-loss-statement-report.md](profit-loss-statement-report.md)
- [daybook-report.md](daybook-report.md)
- [../accounting/overview.md](../accounting/overview.md)
