# Report Spec — Daybook (रोज किर्द)

## Purpose

Daily cash-and-transfer ledger for a single business date. Double-column layout: **जमा (Credit/Receipts)** on the left, **नावे (Debit/Payments)** on the right. Transactions are grouped under GL head categories.

## Report Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Report Name | रोज किर्द | Daybook |
| Report Type | Print | — |
| Parent Module | लेखा / अहवाल | Accounting / Reports |
| Pages | 3 | — |

## Reference Screenshots

| File | Section |
| :--- | :--- |
| `screenshots/Reports/Daybook-page-1.png` | GL groups 1–54, opening transactions (page 1) |
| `screenshots/Reports/Daybook-page-2.png` | GL groups 55–131, continued entries (page 2) |
| `screenshots/Reports/Daybook-page-3.png` | Final GL group, grand totals, cash summary (page 3) |

---

## Print Header

| # | Marathi Label | English Label | Type | Notes |
| :---: | :--- | :--- | :--- | :--- |
| 1 | रोज किर्द | Daybook | Title | Centered |
| 2 | दिनांक | Date | Label | Business date of the daybook |

---

## Column Structure (Both Sides)

Each half (जमा / नावे) shares identical columns:

| # | Marathi Column | English Column | Notes |
| :---: | :--- | :--- | :--- |
| 1 | व्हा क्र. | Voucher No. | Transaction voucher number |
| 2 | खाते क्र. | Account No. | Account number |
| 3 | जी.एल.क्र./जी. | G.L. No. | General Ledger code |
| 4 | *(name / particulars)* | Particulars | Account holder name; check no. when applicable |
| 5 | रोख | Cash | Cash amount |
| 6 | ट्रान्सफर | Transfer | Transfer amount |
| 7 | एकूण | Total | Cash + Transfer |

---

## GL Group Headers

Each section begins with a category header in the format `( <GL code> ) <GL head name>`. Examples captured in screenshots:

| GL Code | Marathi | English | Page |
| :---: | :--- | :--- | :---: |
| १ | वसूल भाग भांडवल | Paid-up Share Capital | 1 |
| ११ | मुदतपूर्व एजंट कमिशन | Pre-mature Agent Commission | 1 |
| १२ | एजंट भरणा | Agent Deposit | 1 |
| ३८ | पिग्मी ठेव | Pygmy Deposit | 1 |
| ५४ | प्रवेश फी | Entrance Fee | 1 |
| ५५ | सेव्हिंग ठेव | Saving Deposit | 1–2 |
| ६७ | स्थावर तारण कर्ज | Immovable Mortgage Loan | 2 |
| १०२ | के.डी.सी.सी.बँक चालू | KDCC Bank Current | 2 |
| ११८ | दाम दुप्पट ठेव (कर्जातील) | Double Money Deposit (Loan-related) | 2 |
| १२१ | कर्जदार कल्याण निधी | Borrower Welfare Fund | 2 |
| १२२ | ब वर्ग सभासद फी | B Class Member Fee | 2 |
| १२३ | प्रोसेस फी | Process Fee | 2 |
| १३१ | उज्जीवन स्मॉल फायनान्स बँक लि. कोल्हापूर | Ujjivan Small Finance Bank Ltd. Kolhapur | 2 |
| १२४ | स्टेशनरी फी | Stationery Fee | 3 |

Each GL group ends with an **एकूण** subtotal row (Cash | Transfer | Total).

---

## Grand Totals (Page 3)

| Side | Marathi | English |
| :--- | :--- | :--- |
| जमा | एकूण | Grand total — receipts |
| नावे | एकूण | Grand total — payments |

---

## Cash Summary Block (Page 3)

| # | Marathi Label | English Label | Notes |
| :---: | :--- | :--- | :--- |
| 1 | रोख आरंभी शिल्लक | Opening Cash Balance | Amount in words below |
| 2 | एकूण जमा रक्कम | Total Credit (Cash) Amount | Left side |
| 3 | शिल्लक | Balance | Amount in words — e.g. `रु. एक लाख एकोणतीस हजार दोनशे दोन फक्त` |
| 4 | एकूण नावे रक्कम | Total Debit Amount | Right side |
| 5 | शिल्लक | Closing Cash Balance | Right side |

---

## Footer Note

| Marathi | English |
| :--- | :--- |
| सामान्य आणि खातेनुसार जी.एल हेड साठी तपशील खातेवार मध्ये दाखवता आहे. | Details for general and account-wise G.L. heads are shown in the account-wise details section. |

## Signature Lines (Page 3)

| Position | Marathi | English |
| :--- | :--- | :--- |
| Left | लिपीक | Clerk |
| Center / Right | व्यवस्थापक | Manager |

## Print Footer

| # | Marathi Label | English Label |
| :---: | :--- | :--- |
| 1 | प्रिंट दिनांक | Print Date |
| 2 | प्रिंट द्वारा | Printed By |
| 3 | Page No | Page Number — `1 / 3`, `2 / 3`, `3 / 3` |

---

## Related Documents

- [overview.md](overview.md)
- [purvani-report.md](purvani-report.md)
- [gl-wise-report.md](gl-wise-report.md)
- [../accounting/overview.md](../accounting/overview.md)
