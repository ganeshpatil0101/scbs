# Screen Spec — Loan Transaction (कर्ज > कर्ज व्यवहार)

> **Consolidates:** [loan-credit-transaction-screen.md](loan-credit-transaction-screen.md) + [loan-debit-transaction-screen.md](loan-debit-transaction-screen.md)

## Purpose

Single screen for loan repayment (credit) and disbursement (debit) transactions. Credit/Debit mode on Tab 1 controls which workflow tabs are visible. Shared Cheque, Transfer, and Ledger tabs use cross-product components.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | कर्ज व्यवहार | Loan Transaction |
| Breadcrumb | डॅशबोर्ड > कर्ज > कर्ज व्यवहार | Dashboard > Loan > Loan Transaction |
| Parent Module | कर्ज | Loan |

## Tabs

| # | Marathi Tab | English Tab | Visibility | Replaces |
| :---: | :--- | :--- | :--- | :--- |
| 1 | कर्ज माहिती | Loan Information | Both | Credit Tab 1 / Debit Tab 1 |
| 2 | इतर जमा / इतर कपात | Other Credits / Other Deductions | Both | Credit Tab 2 / Debit Tab 2 |
| 3 | हप्ते | Installments | **Credit only** | Credit Tab 3 |
| 3 | पूर्वीची कर्ज कपात | Previous Loan Deduction | **Debit only** | Debit Tab 3 |
| 4 | चेक तपशील | Cheque Details | Both | Credit Tab 4 / Debit Tab 4 |
| 5 | ट्रान्सफर | Transfer | Both | Credit Tab 5 / Debit Tab 5 |
| 6 | परतफेड वेळापत्रक | Repayment Schedule | **Debit only** | Debit Tab 6 |
| 6 / 7 | खातेवही | Ledger | Both | Credit Tab 6 / Debit Tab 7 |
| 7 | जामीनदार | Guarantor | **Credit only** | Credit Tab 7 |

**Mode selector (Tab 1):** Radio `जमा (Credit)` / `नावे (Debit)` — required. Matches [../savings/savings-transaction-screen.md](../savings/savings-transaction-screen.md) pattern.

**Tab order by mode:**

| Mode | Tab sequence after Tab 2 |
| :--- | :--- |
| Credit | 3 हप्ते → 4 चेक → 5 ट्रान्सफर → 6 खातेवही → 7 जामीनदार |
| Debit | 3 पूर्वीची कर्ज कपात → 4 चेक → 5 ट्रान्सफर → 6 परतफेड वेळापत्रक → 7 खातेवही |

## Reference Screenshots

| File | Mode / Tab |
| :--- | :--- |
| `screenshots/कर्ज/डॅशबोर्ड-कर्ज-जमा व्यवहार-1-05-07.png` | Credit Tab 1 |
| `screenshots/कर्ज/डॅशबोर्ड-कर्ज-जमा व्यवहार-2-05-07.png` | Credit Tab 2 |
| `screenshots/कर्ज/डॅशबोर्ड-कर्ज-जमा व्यवहार-3-05-07.png` | Credit Tab 3 |
| `screenshots/कर्ज/डॅशबोर्ड-कर्ज-जमा व्यवहार-4-05-07.png` | Credit Tab 4 |
| `screenshots/कर्ज/डॅशबोर्ड-कर्ज-जमा व्यवहार-5-05-07.png` | Credit Tab 5 |
| `screenshots/कर्ज/डॅशबोर्ड-कर्ज-जमा व्यवहार-6-05-07.png` | Credit Tab 6 |
| `screenshots/कर्ज/डॅशबोर्ड-कर्ज-जमा व्यवहार-7-05-07.png` | Credit Tab 7 |
| `screenshots/कर्ज/डॅशबोर्ड- कर्ज- नावे व्यवहार-1-05-07.png` | Debit Tab 1 |
| `screenshots/कर्ज/डॅशबोर्ड- कर्ज- नावे व्यवहार-2-05-07.png` | Debit Tab 2 |
| `screenshots/कर्ज/डॅशबोर्ड- कर्ज- नावे व्यवहार-3-05-07.png` | Debit Tab 3 |
| `screenshots/कर्ज/डॅशबोर्ड- कर्ज- नावे व्यवहार-4-05-07.png` | Debit Tab 4 |
| `screenshots/कर्ज/डॅशबोर्ड- कर्ज- नावे व्यवहार-5-05-07.png` | Debit Tab 5 |
| `screenshots/कर्ज/डॅशबोर्ड- कर्ज- नावे व्यवहार-6-05-07.png` | Debit Tab 6 |
| `screenshots/कर्ज/डॅशबोर्ड- कर्ज- नावे व्यवहार-7-05-07.png` | Debit Tab 7 |

---

## Tab 1: कर्ज माहिती (Loan Information)

### Transaction Header

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | चलन क्रमांक | Challan Number | Label | No | Read-only |
| 2 | जमा / नावे | Credit / Debit | Radio | Yes | `जमा` (Credit), `नावे` (Debit) |
| 3 | व्यवहार प्रकार | Transaction Mode | Radio | Yes | `रोख` (Cash), `ट्रान्सफर` (Transfer) |

### Account Fields

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 4 | शाखा निवडा | Select Branch | Autocomplete | Yes | e.g. `1 — कोतोली मुख्य कार्यालय`. See [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |
| 5 | जी.एल. निवडा | Select G.L. | Autocomplete | Yes | e.g. `61 — जामिनकी कर्ज` |
| 6 | खातेधारक निवडा | Select Account Holder | Autocomplete | Yes | Replaces Account No. + Search + Select triple |
| 7 | लेजर शिल्लक (नावे) | Ledger Balance (Debit) | Label | No | Read-only |
| 8 | न वटलेली शिल्लक (जमा) | Uncleared Balance (Credit) | Label | No | Read-only |
| 9 | आगाऊ व्याज तारीख | Advance Interest Date | Date | Credit: Yes; Debit: No | — |
| 10 | पॅनकार्ड - आधार क्र. | PAN - Aadhaar No. | Label | No | Read-only |
| 11 | व्यवहार रक्कम (रु.) | Transaction Amount (Rs.) | Textbox | Yes | — |
| 12 | अक्षरी रक्कम | Amount in Words | Label | No | Read-only |
| 13 | व्यवहार तपशील | Transaction Details | Textbox | No | — |
| 14 | विशेष सूचना | Special Instructions | Textbox | No | — |
| 15 | सदस्य क्र. | Member No. | Label | No | Read-only |

### Credit-only fields (visible when mode = Credit)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 16 | परतफेड प्रकार | Repayment Type | Dropdown | Yes | `TODO` — placeholder `निवडा` |

### Debit-only fields (visible when mode = Debit)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 17 | जमा व्याज | Accrued Interest | Label | No | Read-only |
| 18 | मंजूर कर्ज रक्कम (रु.) | Sanctioned Loan Amount (Rs.) | Label | No | Read-only |
| 19 | वाटपासाठी उपलब्ध कर्ज रक्कम (रु.) | Available Loan Amount for Disbursement (Rs.) | Label | No | Read-only |
| 20 | आगाऊ व्याजाची रक्कम | Advance Interest Amount | Textbox | No | — |

### Section: Credit Loan Summary (visible when mode = Credit)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 21 | कर्ज रक्कम | Loan Amount | Label | No | Read-only |
| 22 | चालू दिनांक | Open Date | Label | No | Read-only |
| 23 | कालावधी | Tenure | Label | No | Read-only |
| 24 | शेवटची दिनांक | End Date | Label | No | Read-only |
| 25 | व्याज दर | Interest Rate | Label | No | Read-only |
| 26 | हप्त्याची रक्कम | Installment Amount | Label | No | Read-only |
| 27 | इतर जमा | Other Credits | Label | No | Read-only |
| 28 | आज अखेर येणे | Due Till Today | Label | No | Read-only |
| 29 | खाते बंद रक्कम | Account Closing Amount | Label | No | Read-only |
| 30 | एन.पी.ए. स्थिती | NPA Status | Label | No | Read-only |
| 31 | थकीत रक्कम | Overdue Amount | Label | No | Read-only |
| 32 | थकीत हप्ते | Overdue Installments | Label | No | Read-only |
| 33 | हप्ता तारीख | Installment Date | Label | No | Read-only |

### Section: Debit Disbursement Summary (visible when mode = Debit)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 34 | रोख रक्कम (रु.) | Cash Amount (Rs.) | Label | No | Read-only |
| 35 | इतर कपात (रु.) | Other Deductions (Rs.) | Label | No | Read-only |
| 36 | डिमांड कपात (रु.) | Demand Deduction (Rs.) | Label | No | Read-only |
| 37 | एकूण रक्कम (रु.) | Total Amount (Rs.) | Label | No | Read-only |

### Section: प्रगत सेटिंग्ज (Advanced Settings)

> Collapsed by default. Visible to users with accounting/admin role or when expanded manually.

| # | Marathi Label | English Label | Type | Required | Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 38 | कर्ज मंजुरी अधिकारी | Loan Sanctioning Officer | Label | No | Read-only |
| 39 | पालक कर्मचारी | Parent Employee | Label | No | Read-only |

**KYC preview:** `फोटो / सही दाखवा` with photo, signature, ID proof, address proof placeholders.

**Navigation:** `पुढे`. **Actions:** `पूर्ण`, `पूर्ववत`.

---

## Tab 2: इतर जमा / इतर कपात (Other Credits / Other Deductions)

Tab label: `इतर जमा` when Credit; `इतर कपात` when Debit.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | कपात प्रकार निवडा | Select Deduction Type | Dropdown | No | `TODO` — dropdown empty in screenshot |

**Actions:** `+टाका`, `कपात गणना पुन्हा`.

**Grid columns:** निवडा, अनु. क्र., खाते, रक्कम, जीएसटी.

**Grid actions:** Credit: `निर्यात करा`, `काढा`. Debit: `निश्चित करा`, `काढा`.

**Summary:** एकूण रक्कम, एकूण जी.एस.टी., एकूण रक्कम + जीएसटी.

**Navigation:** `मागे`, `पुढे`.

---

## Tab 3: हप्ते (Installments) — Credit only

### Summary Header

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शेवटची व्याज दिनांक | Last Interest Date | Label | No | Read-only |
| 2 | अंतिम व्याज तारखेपासून कालावधी | Period from Last Interest Date | Label | No | Read-only |
| 3 | व्यवहार रक्कम (रु.) | Transaction Amount (Rs.) | Label | No | Read-only |

### Allocation Grid

Rows: थकीत दंड व्याज येणे, थकीत व्याज देणे, इतर जमा, दंड व्याज, व्याज, मुदत रक्कम, एकूण.

**Columns:** (row label), चालू व्याज, थकीत व्याज, येणे, व्यवहार (editable), शिल्लक.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 4 | व्यवहारानंतरची शिल्लक (रु.) | Balance After Transaction (Rs.) | Label | No | Read-only |

### Section: प्रगत सेटिंग्ज (Advanced Settings)

| # | Marathi Label | English Label | Type | Required | Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 5 | व्याज प्रॉडक्ट | Interest Product | Textbox | No | Rarely edited by branch staff |

**Navigation:** `मागे`, `पुढे`. **Actions:** `पूर्ण`, `पूर्ववत`.

---

## Tab 3: पूर्वीची कर्ज कपात (Previous Loan Deduction) — Debit only

Lists the borrower's existing loan accounts with outstanding breakdown for deduction at disbursement.

**Action:** `शोधा` (Search). **Grid action:** `निर्यात करा` (Export).

| # | Marathi Column | English Column | Notes |
| :---: | :--- | :--- | :--- |
| 1 | निवडा | Select | — |
| 2 | अनु. क्र. | Sr. No. | — |
| 3 | खाते क्र. | Account No. | — |
| 4 | रक्कम | Amount | — |
| 5 | शिल्लक | Balance | — |
| 6 | मुद्दल | Principal | — |
| 7 | व्याज | Interest | — |
| 8 | येणे व्याज | Interest Receivable | — |
| 9 | दंड व्याज | Penalty Interest | — |
| 10 | येणे व्याज दंड व्याज | Receivable Penalty Interest | — |
| 11 | ओ.आय.आर. | O.I.R. | Advanced — technical |
| 12 | ओ.पी.आय.आर. | O.P.I.R. | Advanced — technical |
| 13 | इतर शुल्क | Other Charges | — |
| 14 | Rebate Amount | Rebate Amount | — |
| 15 | एकूण थकबाकी | Total Arrears | — |
| 16 | व्याज फरक | Interest Difference | Advanced — technical |
| 17 | Transaction Amount | Transaction Amount | — |

**Summary:** `एकूण रक्कम` (Total Amount).

**Navigation:** `मागे`, `पुढे`. **Actions:** `पूर्ण`, `पूर्ववत`.

---

## Tab 4: चेक तपशील (Cheque Details)

Shared component: `app-cheque-tab`. Visible when Transaction Mode = Cash or Transfer (same as Savings).

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | धनादेश प्रकार निवडा | Select Cheque Type | Dropdown | No | `स्लिप` (Slip), `चेक` (Cheque) |
| 2 | चेक रक्कम (रु.) | Cheque Amount (Rs.) | Textbox | No | Read-only on Credit; editable on Debit |
| 3 | रक्कम अक्षरी | Amount in Words | Label | No | Read-only |
| 4 | चेक दिनांक | Cheque Date | Date | Yes | — |
| 5 | चेक क्र. | Cheque No. | Textbox | Yes | — |
| 6 | नाव | Name | Textbox | Yes | — |
| 7 | बँक निवडा | Select Bank | Autocomplete | Yes | From Bank Master — same as [deposit-account-transaction-screen.md](../accounting/deposit-account-transaction-screen.md) Instrument tab. Sample: `1 — बँक ऑफ इंडिया`, `2 — स्टेट बँक ऑफ इंडिया`, `3 — बँक ऑफ महाराष्ट्र`, `4 — एचडीएफसी बँक`. Enter resolves by ID or name; see [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |
| 8 | बँक शाखा | Bank Branch | Textbox | No | — |
| 9 | ड्रॉन ऑन बँक | Drawn on Bank | Textbox | No | — |
| 10 | ड्रॉन ऑन ब्रांच | Drawn on Branch | Textbox | No | — |

**Navigation:** `मागे`, `पुढे`.

---

## Tab 5: ट्रान्सफर (Transfer)

Shared component: `app-transfer-tab`.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा निवडा | Select Branch | Autocomplete | Yes | — |
| 2 | जी.एल. निवडा | Select G.L. | Autocomplete | Yes | — |
| 3 | खातेधारक निवडा | Select Account Holder | Autocomplete | Yes | — |
| 4 | शिल्लक(जमा) | Balance (Credit) | Label | No | Read-only |
| 5 | जमा / नावे | Credit / Debit | Radio | No | — |
| 6 | व्यवहार रक्कम (रू) | Transaction Amount (Rs.) | Textbox | Yes | — |
| 7 | एकूण व्यवहार रक्कम (रू) | Total Transaction Amount (Rs.) | Label | No | Read-only |

**Action:** `+ टाका`. **Grid columns:** निवडा, अनु क्र, जी.एल. हेड, खाते क्र., नाव, शिल्लक, व्यवहार रक्कम.

**Grid actions:** Credit: `सुधारित करा`, `हटवा`. Debit: `निश्चित करा`, `हटवा`.

**Navigation:** `मागे`, `पुढे`.

---

## Tab 6: परतफेड वेळापत्रक (Repayment Schedule) — Debit only

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | वाटपापूर्वीची खाते शिल्लक | Account Balance Before Disbursement | Label | No | Read-only |
| 2 | वाटप रक्कम | Disbursement Amount | Label | No | Read-only |
| 3 | वाटपानंतरची खाते शिल्लक | Account Balance After Disbursement | Label | No | Read-only |
| 4 | वितरीत केल्यानंतरची हप्ता रक्कम | Installment Amount After Disbursement | Textbox | No | — |

**Action:** `परतफेड वेळापत्रक तयार करा`.

**Grid columns:** अ.क्र., हप्ता दिनांक, मुद्दल, व्याज, शुल्क, एकूण हप्ता, शिल्लक.

**Grid actions:** `निर्यात करा`, `बदल`.

**Summary row:** एकूण — मुद्दल, व्याज, शुल्क, एकूण हप्ता.

**Navigation:** `मागे`, `पुढे`.

---

## Tab 6 / 7: खातेवही (Ledger)

Shared component: `app-ledger-tab`.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | या दिनांकापासून | From Date | Date | Yes | — |
| 2 | या दिनांकापर्यंत | To Date | Date | Yes | — |

**Actions:** `दाखवा`, `स्टेटमेंट प्रिंट`, `पासबुक`. **Display:** `ओपनिंग बॅलन्स`.

**Grid columns:** निवडा, अनु. क्र., दिनांक, चलन क्र., सूचना प्रकार, सूचना क्र., एकूण जमा, मुद्दल (नावे), मुद्दल (जमा), व्याज (नावे), व्याज (जमा), दंड व्याज (नावे), दंड व्याज (जमा), रिबेट (नावे), रिबेट (जमा), इतर शुल्क (नावे), इतर शुल्क (जमा), शिल्लक, तपशील, व्यवहार, वापरकर्ता, वेळ, सत्र, पासिंग युजर.

**Summary:** एकूण नावे, एकूण जमा.

**Actions:** `चलन प्रिंट`, `ड्राफ्ट प्रिंट`, `निर्यात करा`.

### Loan Actions Sub-section (Credit only)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 3 | या दिनांकापासून | From Date | Date | No | Loan actions filter |
| 4 | या दिनांकापर्यंत | To Date | Date | No | — |

**Grid columns:** अ.क्र., Action Date, Action Taken, Contact Method, Action Details, Collected Amount, Fee Amount, Next Action, Next Action Date.

**Navigation:** `मागे`.

---

## Tab 7: जामीनदार (Guarantor) — Credit only

Read-only grid.

**Columns:** अनु. क्र., ग्राहक क्र., नाव, पत्ता, जिल्हा, तालुका, शहर, ठिकाण, पिन कोड, दुरध्वनी क्रमांक, मोबाईल क्रमांक.

**Navigation:** `मागे`. **Actions:** `पूर्ण`, `पूर्ववत`.

---

## Mockup

- [HTML mockup (Draft)](../mockups/loan/loan-transaction-screen/) — Marathi layout for bank review; Credit/Debit mode switches tab 3, 6, 7 labels and content

## Related Documents

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [loan-information-screen.md](loan-information-screen.md)
- [new-loan-screen.md](new-loan-screen.md)
- [../savings/savings-transaction-screen.md](../savings/savings-transaction-screen.md)
- [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
