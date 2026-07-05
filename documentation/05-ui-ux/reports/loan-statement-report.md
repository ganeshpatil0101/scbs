# Report Spec — Loan Account Statement (कर्ज खाते उतार)

## Purpose

Printable statement for a single loan account showing account metadata, transaction ledger (principal, interest, penalty, overdue interest, other charges), and outstanding receivable summary.

## Report Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Report Name | कर्ज खाते उतार | Loan Account Statement |
| Report Type | Print | — |
| Parent Module | कर्ज | Loan |
| Pages | 1 | — |

## Reference Screenshots

| File | Section |
| :--- | :--- |
| `screenshots/Reports/LoanStatement-by-customer.png` | Full statement — header, ledger, summary |

---

## Print Header — Account Details

| # | Marathi Label | English Label | Type | Notes |
| :---: | :--- | :--- | :--- | :--- |
| 1 | कर्ज खाते उतार | Loan Account Statement | Title | — |
| 2 | दिनांक | Date | Label | Statement period — `दिनांक: <from> ते: <to>` |
| 3 | जी. एल. हेड | G.L. Head | Label | e.g. `जामिनकि कर्ज` |
| 4 | खाते क्र. | Account No. | Label | e.g. `६१ / १` |
| 5 | नाव | Name | Label | Account holder name |
| 6 | ग्राहक क्र. | Customer No. | Label | — |
| 7 | मंजूरी अधिकारी | Sanctioning Officer | Label | — |
| 8 | पत्ता | Address | Label | — |
| 9 | मुदत | Term | Label | e.g. `३६ महिने` |
| 10 | कर्ज रक्कम | Loan Amount | Label | Sanctioned amount |
| 11 | हप्ता रक्कम | Installment Amount | Label | — |
| 12 | मोबाइल क्र. | Mobile No. | Label | — |
| 13 | खाते दिनांक | Account Date | Label | Account open date |
| 14 | पहिला हप्ता दिनांक | First Installment Date | Label | — |
| 15 | व्याज दर | Interest Rate | Label | e.g. `१५.०० %` |
| 16 | शेअर्स शिल्लक | Share Balance | Label | — |
| 17 | स्थिती | Status | Label | e.g. `चालू` |
| 18 | थकीत रक्कम | Overdue Amount | Label | — |

---

## Transaction Ledger Grid

| # | Marathi Column | English Column | Sub-columns |
| :---: | :--- | :--- | :--- |
| 1 | अ. क्र. | Sr. No. | — |
| 2 | दिनांक | Date | — |
| 3 | तपशील | Particulars | e.g. `आरंभी शिल्लक :` |
| 4 | एकूण जमा | Total Deposit | Payment received |
| 5 | मुद्दल | Principal | जमा (Credit) \| नावे (Debit) |
| 6 | व्याज | Interest | जमा \| नावे |
| 7 | दंड व्याज | Penalty Interest | जमा \| नावे |
| 8 | थकीत व्याज येणे | Overdue Interest Receivable | जमा \| नावे |
| 9 | इतर खर्च/कपात | Other Expenses/Deduction | जमा \| नावे |
| 10 | शिल्लक | Balance | Principal balance; suffix `नाव` (Debit) |

**Total row:** `एकूण` — sums deposit, principal, interest columns.

---

## Receivable Summary (येणे)

Summary table below the ledger:

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | मुद्दल | Principal |
| 2 | व्याज | Interest |
| 3 | दंड व्याज | Penalty Interest |
| 4 | व्याज सवलत | Interest Discount |
| 5 | थकीत व्याज येणे | Overdue Interest Receivable |
| 6 | इतर खर्च/कपात | Other Expenses/Deduction |
| 7 | एकूण | Total Receivable |

---

## Signature Lines

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
| 3 | पृ.क्र. | Page No. — e.g. `1 / 1` |

---

## Related Documents

- [overview.md](overview.md)
- [../loan/overview.md](../loan/overview.md)
- [../loan/loan-account-register-screen.md](../loan/loan-account-register-screen.md)
