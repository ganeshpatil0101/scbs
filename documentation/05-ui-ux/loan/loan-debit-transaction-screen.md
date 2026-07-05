# Screen Spec — Loan Debit Transaction (कर्ज > नावे व्यवहार)

## Purpose

UI specification for loan disbursement (debit) transactions — deductions, cheque/transfer, repayment schedule, and ledger.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | नावे व्यवहार | Debit Transaction |
| Breadcrumb | डॅशबोर्ड > कर्ज > नावे व्यवहार | Dashboard > Loan > Debit Transaction |
| Parent Module | कर्ज | Loan |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | कर्ज माहिती | Loan Information |
| 2 | इतर कपात | Other Deductions |
| 3 | पूर्वीची कर्ज कपात | Previous Loan Deduction |
| 4 | चेक तपशील | Cheque Details |
| 5 | ट्रान्सफर | Transfer |
| 6 | परतफेड वेळापत्रक | Repayment Schedule |
| 7 | खातेवही | Ledger |

## Reference Screenshots

| File | Tab |
| :--- | :--- |
| `screenshots/कर्ज/डॅशबोर्ड- कर्ज- नावे व्यवहार-1-05-07.png` | Tab 1 |
| `screenshots/कर्ज/डॅशबोर्ड- कर्ज- नावे व्यवहार-2-05-07.png` | Tab 2 |
| `screenshots/कर्ज/डॅशबोर्ड- कर्ज- नावे व्यवहार-3-05-07.png` | Tab 3 |
| `screenshots/कर्ज/डॅशबोर्ड- कर्ज- नावे व्यवहार-4-05-07.png` | Tab 4 |
| `screenshots/कर्ज/डॅशबोर्ड- कर्ज- नावे व्यवहार-5-05-07.png` | Tab 5 |
| `screenshots/कर्ज/डॅशबोर्ड- कर्ज- नावे व्यवहार-6-05-07.png` | Tab 6 |
| `screenshots/कर्ज/डॅशबोर्ड- कर्ज- नावे व्यवहार-7-05-07.png` | Tab 7 |

---

## Tab 1: कर्ज माहिती (Loan Information)

### Transaction Header

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | चलन क्रमांक | Challan Number | Textbox | No | Read-only |
| 2 | व्यवहार प्रकार | Transaction Mode | Radio | Yes | `रोख` (Cash), `ट्रान्सफर` (Transfer) |

### Account Fields

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 3 | शाखा कोड | Branch Code | Textbox | Yes | e.g. `1` |
| 4 | शाखा निवडा | Select Branch | Dropdown | Yes | e.g. `कोतोली मुख्य कार्यालय` |
| 5 | जी.एल. हेड | G.L. Head | Textbox | Yes | e.g. `61` |
| 6 | जी.एल. निवडा | Select G.L. | Dropdown | Yes | e.g. `जामिनकी कर्ज` |
| 7 | खाते क्रमांक | Account Number | Textbox | Yes | — |
| 8 | खातेधारक शोधा | Search Account Holder | Textbox | Yes | — |
| 9 | खातेधारक निवडा | Select Account Holder | Dropdown | Yes | — |
| 10 | खातेवही शिल्लक | Ledger Balance | Textbox | No | Read-only |
| 11 | न वटलेली शिल्लक | Uncleared Balance | Textbox | No | Read-only |
| 12 | जमा व्याज | Accrued Interest | Textbox | No | Read-only |
| 13 | पॅन क्र. | PAN No. | Textbox | No | Read-only |
| 14 | मंजूर कर्ज रक्कम (रु.) | Sanctioned Loan Amount (Rs.) | Textbox | No | Read-only |
| 15 | वाटपासाठी उपलब्ध कर्ज रक्कम (रु.) | Available Loan Amount for Disbursement (Rs.) | Textbox | No | Read-only |
| 16 | व्यवहार रक्कम (रु.) | Transaction Amount (Rs.) | Textbox | Yes | — |
| 17 | अक्षरी रक्कम | Amount in Words | Textbox | No | Read-only |
| 18 | व्यवहार तपशील | Transaction Details | Textbox | No | — |
| 19 | विशेष सूचना | Special Instructions | Textbox | No | — |
| 20 | आगाऊ व्याज तारीख | Advance Interest Date | Date | No | — |
| 21 | आगाऊ व्याजाची रक्कम | Advance Interest Amount | Textbox | No | — |
| 22 | सदस्य क्र. | Member No. | Textbox | No | Read-only |

### Summary (व्यवहार तपशील)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 23 | रोख रक्कम (रु.) | Cash Amount (Rs.) | Textbox | No | Read-only |
| 24 | इतर कपात (रु.) | Other Deductions (Rs.) | Textbox | No | Read-only |
| 25 | डिमांड कपात (रु.) | Demand Deduction (Rs.) | Textbox | No | Read-only |
| 26 | एकूण रक्कम (रु.) | Total Amount (Rs.) | Textbox | No | Read-only |

**KYC preview:** `फोटो / सही दाखवा`.

**Navigation:** `पुढे`. **Actions:** `पूर्ण`, `पूर्ववत`.

---

## Tab 2: इतर कपात (Other Deductions)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | कपात प्रकार निवडा | Select Deduction Type | Dropdown | No | `TODO` — dropdown empty in screenshot |

**Actions:** `+ टाका`, `कपात गणना पुन्हा`.

**Grid columns:** निवडा, अनु. क्र., खाते, रक्कम, जीएसटी.

**Grid actions:** `निश्चित करा`, `काढा`.

**Summary:** एकूण रक्कम, एकूण जी.एस.टी., एकूण रक्कम + जीएसटी.

**Navigation:** `मागे`, `पुढे`. **Actions:** `पूर्ण`, `पूर्ववत`.

---

## Tab 3: पूर्वीची कर्ज कपात (Previous Loan Deduction)

Lists the borrower's existing loan accounts with outstanding breakdown for deduction at disbursement. Distinct from Tab 2 — no deduction-type dropdown; search loads prior loans into the grid.

**Action:** `शोधा` (Search). **Grid action:** `निर्यात करा` (Export).

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | अनु. क्र. | Sr. No. |
| 3 | खाते क्र. | Account No. |
| 4 | रक्कम | Amount |
| 5 | शिल्लक | Balance |
| 6 | मुद्दल | Principal |
| 7 | व्याज | Interest |
| 8 | येणे व्याज | Interest Receivable |
| 9 | दंड व्याज | Penalty Interest |
| 10 | येणे व्याज दंड व्याज | Receivable Penalty Interest |
| 11 | ओ.आय.आर. | O.I.R. |
| 12 | ओ.पी.आय.आर. | O.P.I.R. |
| 13 | इतर शुल्क | Other Charges |
| 14 | Rebate Amount | Rebate Amount |
| 15 | एकूण थकबाकी | Total Arrears |
| 16 | व्याज फरक | Interest Difference |
| 17 | Transaction Amount | Transaction Amount |

**Summary:** `एकूण रक्कम` (Total Amount).

**Navigation:** `मागे`, `पुढे`. **Actions:** `पूर्ण`, `पूर्ववत`.

---

## Tab 4: चेक तपशील (Cheque Details)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | धनादेश प्रकार निवडा | Select Cheque Type | Dropdown | No | e.g. `स्लिप` (Slip) |
| 2 | चेक रक्कम (रु.) | Cheque Amount (Rs.) | Textbox | No | — |
| 3 | रक्कम अक्षरी | Amount in Words | Textbox | No | Read-only |
| 4 | चेक दिनांक | Cheque Date | Date | Yes | — |
| 5 | चेक क्र. | Cheque No. | Textbox | Yes | — |
| 6 | नाव | Name | Textbox | Yes | — |
| 7 | बँक निवडा | Select Bank | Dropdown | Yes | `TODO` |
| 8 | बँक शाखा | Bank Branch | Textbox | No | — |
| 9 | ड्रॉन ऑन बँक | Drawn on Bank | Textbox | No | — |
| 10 | ड्रॉन ऑन ब्रांच | Drawn on Branch | Textbox | No | — |

**Navigation:** `मागे`, `पुढे`. **Actions:** `पूर्ण`, `पूर्ववत`.

---

## Tab 5: ट्रान्सफर (Transfer)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा कोड | Branch Code | Textbox | Yes | — |
| 2 | शाखा निवडा | Select Branch | Dropdown | Yes | — |
| 3 | जी.एल.हेड.क्र. | G.L. Head No. | Textbox | Yes | — |
| 4 | जी.एल.निवडा | Select G.L. | Dropdown | Yes | — |
| 5 | खाते क्र. | Account No. | Textbox | Yes | — |
| 6 | खातेधारक शोधा | Search Account Holder | Textbox | Yes | — |
| 7 | खातेधारक निवडा | Select Account Holder | Dropdown | Yes | — |
| 8 | शिल्लक | Balance | Textbox | No | Read-only |
| 9 | जमा / नावे | Credit / Debit | Radio | No | — |
| 10 | व्यवहार रक्कम (रु) | Transaction Amount (Rs.) | Textbox | Yes | — |
| 11 | एकूण व्यवहार रक्कम (रु) | Total Transaction Amount (Rs.) | Textbox | No | Read-only |

**Action:** `+ टाका`. **Grid columns:** निवडा, अनु क्र, जी.एल. हेड, खाते क्र., नाव, शिल्लक, व्यवहार रक्कम.

**Grid actions:** `निश्चित करा`, `हटवा`.

**Navigation:** `मागे`, `पुढे`. **Actions:** `पूर्ण`, `पूर्ववत`.

---

## Tab 6: परतफेड वेळापत्रक (Repayment Schedule)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | वाटपापूर्वीची खाते शिल्लक | Account Balance Before Disbursement | Textbox | No | Read-only |
| 2 | वाटप रक्कम | Disbursement Amount | Textbox | No | Read-only |
| 3 | वाटपानंतरची खाते शिल्लक | Account Balance After Disbursement | Textbox | No | Read-only |
| 4 | वितरीत केल्यानंतरची हप्ता रक्कम | Installment Amount After Disbursement | Textbox | No | — |

**Action:** `परतफेड वेळापत्रक तयार करा`.

**Grid columns:** अ.क्र., हप्ता दिनांक, मुद्दल, व्याज, शुल्क, एकूण हप्ता, शिल्लक.

**Grid actions:** `निर्यात करा`, `बदल`.

**Summary row:** एकूण — मुद्दल, व्याज, शुल्क, एकूण हप्ता.

**Navigation:** `मागे`, `पुढे`.

---

## Tab 7: खातेवही (Ledger)

Same structure as [loan-credit-transaction-screen.md](loan-credit-transaction-screen.md) Tab 6 (without Loan Actions sub-section in captured screenshot).

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | या दिनांकापासून | From Date | Date | Yes | — |
| 2 | या दिनांकापर्यंत | To Date | Date | Yes | — |

**Actions:** `दाखवा`, `स्टेटमेंट प्रिंट`, `पासबुक`, `निर्यात करा`, `चलन प्रिंट`, `ड्राफ्ट प्रिंट`.

**Navigation:** `मागे`, `पुढे`.

---

## Related Documents

- [overview.md](overview.md)
- [loan-credit-transaction-screen.md](loan-credit-transaction-screen.md)
- [new-loan-screen.md](new-loan-screen.md)
