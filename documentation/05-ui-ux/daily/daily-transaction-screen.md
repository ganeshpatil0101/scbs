# Screen Spec — Daily Transaction (डेली > व्यवहार)

## Purpose

UI specification for daily (pigmy) account transactions. Six-tab workflow.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | व्यवहार | Transaction |
| Breadcrumb | डॅशबोर्ड > डेली > व्यवहार | Dashboard > Daily > Transaction |
| Parent Module | डेली | Daily |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | खात्याची माहिती | Account Information |
| 2 | कर्ज माहिती | Loan Information |
| 3 | साहित्य तपशील | Instrument Details |
| 4 | ट्रान्सफर | Transfer |
| 5 | खातेवही | Ledger |
| 6 | केवायसी माहिती | KYC Information |

## Reference Screenshots

| File | Tab |
| :--- | :--- |
| `screenshots/डेली/डॅशबोर्ड_डेली_व्यवहार_1.png` | Tab 1 |
| `screenshots/डेली/डॅशबोर्ड_डेली_व्यवहार_2.png` | Tab 2 |
| `screenshots/डेली/डॅशबोर्ड_डेली_व्यवहार_3.png` | Tab 4 — Ledger |

---

## Tab 1: खात्याची माहिती (Account Information)

### Transaction Header

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | चलन क्रमांक | Challan Number | Label (read-only) | No | Auto-generated; e.g. `42` |
| 2 | नावे / जमा | Debit / Credit | Radio | Yes | — |
| 3 | रोख / ट्रान्सफर | Cash / Transfer | Radio | Yes | — |

### Account Lookup

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 4 | शाखा निवडा | Select Branch | Autocomplete | Yes | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 5 | जी.एल. निवडा | Select GL | Autocomplete | Yes | Sample: `38 — Pigmy`. Enter resolves by ID or name; shows display name |
| 6 | खातेधारक निवडा | Select Account Holder | Autocomplete | Yes | Sample: `101 — Account Holder 1`, `102 — Account Holder 2`, `103 — Account Holder 3`. Enter resolves by ID or name; shows display name |

### Editable Transaction Fields

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 7 | व्यवहार रक्कम (रु.) | Transaction Amount (Rs.) | Textbox | Yes | — |
| 8 | व्यवहार तपशील | Transaction Details | Textbox | No | — |
| 9 | कमिशन कपात | Commission Deduction | Textbox | No | — |

### Account Summary Panel (computed read-only Labels)

Displayed after account resolve. Replaces individual editable textboxes for calculated values.

| # | Marathi Label | English Label |
| :---: | :--- | :--- |
| 10 | खातेवही शिल्लक | Ledger Balance |
| 11 | न वटलेली शिल्लक | Uncleared Balance |
| 12 | अक्षरी रक्कम | Amount in Words |
| 13 | व्यवहारानंतरची शिल्लक | Balance After Transaction |
| 14 | परतीची दिनांक | Return Date |
| 15 | विशेष सूचना | Special Instructions |
| 16 | पॅनकार्ड - आधार क्र. | PAN - Aadhaar No. |
| 17 | स्पॉट कमिशन | Spot Commission |
| 18 | तरतूद | Provision |
| 19 | व्याज | Interest |
| 20 | एकूण | Total |
| 21 | टीडीएस (रु.) | TDS (Rs.) |
| 22 | एकूण टीडीएस देणे (रु.) | Total TDS Payable |
| 23 | शेवटची नावे दिनांक | Last Debit Date |
| 24 | एकूण दिवस | Total Days |
| 25 | खुली रक्कम | Open Amount |
| 26 | स्पॉट कमिशन रेट | Spot Commission Rate |
| 27 | सदस्य क्र. | Member No. |

**Links:** `कर्ज खाते माहिती`, `केवायसी माहिती`.

**KYC preview:** `फोटो / सही दाखवा` with photo, signature, ID, address proof placeholders.

**Action:** `पुढे` (Next).

---

## Tab 2: कर्ज माहिती (Loan Information)

### स्वतःची कर्ज माहिती (Self Loan Information)

**Action:** `शोध` (Search).

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | अनुक्रमांक | Sr. No. |
| 3 | खाते क्रमांक | Account Number |
| 4 | खाते | Account |
| 5 | नाव | Name |
| 6 | कर्ज रक्कम | Loan Amount |
| 7 | शिल्लक | Balance |
| 8 | मुद्दल | Principal |
| 9 | व्याज | Interest |
| 10 | येणे व्याज | Interest Receivable |
| 11 | दंड व्याज | Penalty Interest |
| 12 | येणे दंड व्याज | Penalty Interest Receivable |
| 13 | ओ.आय.आर | O.I.R |
| 14 | ओ.पी.आय.आर | O.P.I.R |
| 15 | इतर शुल्क | Other Charges |
| 16 | एकूण | Total |
| 17 | असत्यापित व्याज | Unverified Interest |
| 18 | व्यवहार रक्कम | Transaction Amount |

**Grid actions:** `निर्यात करा`, `हटवा`.

**Summary:** स्वतः थकीत. **Note:** सूचना: वरील कर्ज खात्यासाठी जमा व्यवहार झाले आहेत.

### कर्जाची माहिती जो जामीनदार आहे (Guarantor Loans)

Same search and similar columns (through एकूण). **Action:** `निर्यात करा`.

Tabs 3, 4, 6: `TODO` — not captured.

---

## Tab 5: खातेवही (Ledger)

Uses shared component `app-ledger-tab` — same 15-column ledger grid as Savings/FD/Recurring transaction screens.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | या दिनांकापासून | From Date | Date | Yes | — |
| 2 | या दिनांकापर्यंत | To Date | Date | Yes | — |

**Actions:** `दाखवा`, `स्टेटमेंट प्रिंट`, `पासबुक`.

### Ledger Grid Columns

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | अनु. क्र. | Sr. No. |
| 3 | दिनांक | Date |
| 4 | चलन क्र. | Voucher No. |
| 5 | सूचना प्रकार | Notice Type |
| 6 | सूचना क्र. | Notice No. |
| 7 | नावे | Debit |
| 8 | जमा | Credit |
| 9 | शिल्लक | Balance |
| 10 | तपशील | Details |
| 11 | व्यवहार | Transaction |
| 12 | वापरकर्ता | User |
| 13 | वेळ | Time |
| 14 | सत्र | Session |
| 15 | पासिंग यूजर | Passing User |

**Summary:** एकूण नावे, एकूण जमा. **Actions:** `निर्यात करा`, `चलन प्रिंट`, `ड्राफ्ट प्रिंट`.

---

## Mockup

- [HTML mockup (Draft)](../mockups/daily/daily-transaction-screen/) — Marathi layout for bank review

---

## Cross-Links

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [../savings/savings-transaction-screen.md](../savings/savings-transaction-screen.md)
- [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md)
