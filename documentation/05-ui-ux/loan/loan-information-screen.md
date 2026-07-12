# Screen Spec — Loan Information (कर्ज > कर्ज माहिती)

## Purpose

UI specification for viewing loan account details, recovery/arrears summary, and loan ledger. Three-tab read/query screen.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | कर्ज माहिती | Loan Information |
| Breadcrumb | डॅशबोर्ड > कर्ज > कर्ज माहिती | Dashboard > Loan > Loan Information |
| Parent Module | कर्ज | Loan |

**Auto-fill (header):** `संस्था` (Organization) — read-only `Label` from tenant session; not repeated in filter bar.

**Navigation:** Register `तपशील` action opens this screen with account pre-filled from [loan-account-register-screen.md](loan-account-register-screen.md).

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | खाते सारांश | Account Summary |
| 2 | ग्राहक माहिती | Customer Information |
| 3 | खातेवही | Ledger |

## Reference Screenshots

| File | Tab |
| :--- | :--- |
| `screenshots/कर्ज/डॅशबोर्ड -कर्ज -कर्ज-माहिती-1-02_07.png` | Tab 1 |
| `screenshots/कर्ज/डॅशबोर्ड -कर्ज -कर्ज-माहिती-2-02_07.png` | Tab 3 |

---

## Tab 1: खाते सारांश (Account Summary)

### Account Selection

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा निवडा | Select Branch | Autocomplete | Yes | Sample: `1 — कोतोली मुख्य कार्यालय` |
| 2 | योजना निवडा | Select Scheme | Dropdown | No | e.g. `जामीनकी कर्ज` |
| 3 | खातेधारक निवडा | Select Account Holder | Autocomplete | No | Primary lookup — resolves account when selected |
| 4 | खाते क्रमांक | Account Number | Textbox | No | Optional; auto-fills when Account Holder selected |
| 5 | योजना प्रकार | Scheme Type | Label | — | Read-only; e.g. `साधा हप्ता (व्याज सहित)` |

### Section: प्रगत सेटिंग्ज (Advanced Settings)

> Collapsed by default.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 6 | दिनांकापासून | From Date | Date | No | Optional date range for inquiry |

**Removed:** `संस्था निवडा` (Organization) — session header. `ग्राहक क्रमांक` (Customer Number) — redundant when Account Holder resolves.

**Actions:** `दाखवा`, `खाते तपशील`.

### Section: Account Summary Panel (खाते माहिती)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 7 | कर्ज रक्कम | Loan Amount | Label | — | Read-only |
| 8 | व्याज दर | Interest Rate | Label | — | Read-only |
| 9 | चालू दिनांक | Opening Date | Label | — | Read-only |
| 10 | कालावधी (महिने) | Duration (Months) | Label | — | Read-only |
| 11 | परतावा दिनांक | Repayment Date | Label | — | Read-only |
| 12 | पहिला हप्ता दिनांक | First Installment Date | Label | — | Read-only |
| 13 | हप्त्याची रक्कम | Installment Amount | Label | — | Read-only |
| 14 | एस. एफ. क्रमांक | S.F. Number | Label | — | Read-only |
| 15 | स्थिती | Status | Label | — | Read-only; e.g. `चालू` |
| 16 | अखेरचा जमा हप्ता | Last Credit Installment | Label | — | Read-only |
| 17 | मुद्दल शिल्लक(नावे) | Principal Balance (Debit) | Label | — | Read-only |
| 18 | ग्राहक कर्ज जोखिम मर्यादा | Customer Loan Risk Limit | Label | — | Read-only |

### Section: Upcoming Balance Panel (आगामी शिल्लक)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 19 | मुद्दल | Principal | Label | — | Read-only |
| 20 | व्याज | Interest | Label | — | Read-only |

### Section: Account Closing Interest Panel (खाते बंद व्याज)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 21 | व्याज | Interest | Label | — | Read-only |
| 22 | दंड व्याज | Penalty Interest | Label | — | Read-only |
| 23 | थकीत व्याज येणे(जमा) | Overdue Interest Receivable (Credit) | Label | — | Read-only |
| 24 | थकीत दंड व्याज येणे(जमा) | Overdue Penalty Interest Receivable (Credit) | Label | — | Read-only |

### Section: Arrears / Recovery Panel (थकबाकी / वसुली)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 25 | मुद्दल शिल्लक(नावे) | Principal Balance (Debit) | Label | — | Read-only |
| 26 | थकीत दिनांक | Overdue Date | Label | — | Read-only |
| 27 | पासून थकीत | Overdue Since | Label | — | Read-only |
| 28 | अपेक्षित हप्ते | Expected Installments | Label | — | Read-only |
| 29 | आलेले हप्ते | Received Installments | Label | — | Read-only |
| 30 | थकीत हप्ते | Overdue Installments | Label | — | Read-only |
| 31 | पोस्ट केलेले व्याज | Posted Interest | Label | — | Read-only |
| 32 | आलेले व्याज | Received Interest | Label | — | Read-only |
| 33 | एकूण वसुली | Total Recovery | Label | — | Read-only |
| 34 | थकीत रक्कम | Overdue Amount | Label | — | Read-only |
| 35 | थकीत व्याज | Overdue Interest | Label | — | Read-only |
| 36 | थकीत दंड व्याज | Overdue Penalty Interest | Label | — | Read-only |
| 37 | आगाऊ हप्ते | Advance Installments | Label | — | Read-only |
| 38 | आगाऊ वसुली | Advance Recovery | Label | — | Read-only |
| 39 | येणे मुद्दल(नावे) | Receivable Principal (Debit) | Label | — | Read-only |
| 40 | एन.पी.ए. स्थिती | NPA Status | Label | — | Read-only |
| 41 | आऊट ऑफ एनपीए अमाऊंट | Out of NPA Amount | Label | — | Read-only |
| 42 | एकूण थकबाकी | Total Arrears | Label | — | Read-only |
| 43 | खाते बंद रक्कम | Account Closing Amount | Label | — | Read-only |
| 44 | वितरणासाठी उपलब्ध कर्ज रक्कम | Loan Amount Available for Disbursement | Label | — | Read-only |

### Change History Grid

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | अनु. क्र. | Sr. No. |
| 2 | बदल तारीख | Change Date |
| 3 | तपशील | Details |
| 4 | बदल कर्ता | Changed By |

### Today's Recovery

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 45 | आजची एकूण वसुली | Today's Total Recovery | Label | No | Read-only |

**Links:** `कर्ज मागणी अर्ज माहिती`, `आजची वसुली यादी`.

**Recovery breakdown grid columns:** अनु. क्र., Balance Amount, Business & Service Tax, Current Penalty, Due Penalty, Provision Penalty, Overdue Penalty Interest, Current Interest, Due Interest, Interest Provision, Overdue Interest, Principal.

**Actions:** `देय नोट प्रिंट`, `पूर्ववत`, `पुढे`.

---

## Tab 2: ग्राहक माहिती (Customer Information)

`TODO` — tab referenced in navigation; no dedicated screenshot in `02_07` set.

---

## Tab 3: खातेवही (Ledger)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | या दिनांकापासून | From Date | Date | Yes | — |
| 2 | या दिनांकापर्यंत | To Date | Date | Yes | — |

**Actions:** `दाखवा`, `स्टेटमेंट प्रिंट`, `पासबुक`. **Display:** `ओपनिंग बॅलन्स` (with debit/credit indicator).

**Grid columns:** निवडा, अनु. क्र., दिनांक, चलन क्र., सूचना प्रकार, सूचना क्र., एकूण जमा, मुद्दल (नावे), मुद्दल (जमा), व्याज (नावे), व्याज (जमा), दंड व्याज (नावे/जमा), रिबेट (नावे/जमा), इतर शुल्क (नावे), इतर शुल्क (जमा), शिल्लक, तपशील, व्यवहार, वापरकर्ता, वेळ, सत्र, पासिंग युजर.

**Footer:** `एकूण नावे`, `एकूण जमा`, `निर्यात करा`, `देय नोट प्रिंट`, `पूर्ववत`, `चलन प्रिंट`, `ड्राफ्ट प्रिंट`.

**Navigation:** `मागे`.

---

## Mockup

- [HTML mockup (Draft)](../mockups/loan/loan-information-screen/) — Marathi layout for bank review

## Related Documents

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [loan-account-register-screen.md](loan-account-register-screen.md)
- [new-loan-screen.md](new-loan-screen.md)
- [new-deposit-loan-screen.md](new-deposit-loan-screen.md)
- [../savings/savings-transaction-screen.md](../savings/savings-transaction-screen.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
