# Screen Spec — Deposit Account Transaction (ठेव खाते व्यवहार)

> **Consolidates:** [../savings/savings-transaction-screen.md](../savings/savings-transaction-screen.md), [../fixed-deposit/fd-transaction-screen.md](../fixed-deposit/fd-transaction-screen.md), [../daily/daily-transaction-screen.md](../daily/daily-transaction-screen.md), [../recurring/recurring-transaction-screen.md](../recurring/recurring-transaction-screen.md)

## Purpose

Single transaction screen for deposit products: Savings, Fixed Deposit, Daily (Pigmy), and Recurring. **मॉड्यूल निवडा** (Select Module) radio at the top drives GL defaults and show/hide of module-specific fields. All four modules share the same **5-tab** workflow.

**Removed from legacy per-module screens (by design):**
- **केवायसी माहिती (KYC Information)** tab — replaced by **ग्राहक तपशील (Customer Details)** tab.
- **कर्ज माहिती (Loan Information)** tab (Daily only) — loan account summary absorbed into Customer Details tab; recovery action deferred (`TODO`).

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | ठेव खाते व्यवहार | Deposit Account Transaction |
| Breadcrumb | डॅशबोर्ड > ठेव खाते व्यवहार | Dashboard > Deposit Account Transaction |
| Parent Module | लेखा (cross-product) | Accounting (cross-product) |

## Tabs

| # | Marathi Tab | English Tab | Notes |
| :---: | :--- | :--- | :--- |
| 1 | खात्याची माहिती | Account Information | Module radio + transaction header + lookup + summary |
| 2 | साहित्य तपशील | Instrument Details | Common cheque/instrument fields (all modules) |
| 3 | ट्रान्सफर | Transfer | Common transfer grid (all modules) |
| 4 | ग्राहक तपशील | Customer Details | Cross-product customer + account summary (replaces KYC + Daily Loan Info) |
| 5 | खातेवही | Ledger | Shared `app-ledger-tab` — same 15-column grid as Dividend Transaction / Loan screens |

## Reference Screenshots / Media

| File | Module | Tab |
| :--- | :--- | :--- |
| `screenshots/bachat/डॅशबोर्ड-बचत-व्यवहार.png` | Savings | Tab 1 |
| `screenshots/bachat/डॅशबोर्ड-बचत-व्यवहार -1.png` | Savings | Tab 2 — Instrument |
| `screenshots/bachat/डॅशबोर्ड-बचत-व्यवहार -2.png` | Savings | Tab 3 — Transfer |
| `screenshots/मुदत ठेव/डॅशबोर्ड-मुदत ठेव-व्यवहार.png` | FD | Tab 1 |
| `screenshots/मुदत ठेव/डॅशबोर्ड-मुदत ठेव-व्यवहार-2.png` | FD | Tab 3 — Transfer |
| `screenshots/डेली/डॅशबोर्ड_डेली_व्यवहार_1.png` | Daily | Tab 1 |
| User capture 2026-07-18 | Daily | Tab 2 — Instrument (साहित्य तपशील) |
| User capture 2026-07-18 | Daily | Tab 3 — Transfer |
| `screenshots/रिकरिंग/credit-transaction-frames/frame_0010.jpg` | Recurring | Tab 1 — Credit |
| User capture 2026-07-18 | Recurring | Tab 2 — Instrument (legacy label: चेक तपशील / बँक तपशील) |
| User capture 2026-07-18 | Recurring | Tab 3 — Transfer |

---

## Tab 1: खात्याची माहिती (Account Information)

### Transaction Header

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | मॉड्यूल निवडा | Select Module | Radio | Yes | `बचत` (Savings), `मुदत ठेव` (FD), `डेली` (Daily), `रिकरिंग` (Recurring). Drives GL filter + conditional fields |
| 2 | चलन क्रमांक | Challan Number | Label (read-only) | No | Auto-generated; e.g. `42` |
| 3 | नावे / जमा | Debit / Credit | Radio | Yes | `जमा` (Credit), `नावे` (Debit). Recurring debit-mode extra fields: `TODO` — maturity payout, premature closure, TDS, payout mode |
| 4 | रोख / ट्रान्सफर | Cash / Transfer | Radio | Yes | — |

### Account Lookup

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 5 | शाखा निवडा | Select Branch | Autocomplete | Yes | Sample: `1 — Branch 1`. Enter resolves by ID or name |
| 6 | जी.एल. निवडा | Select GL | Autocomplete | Yes | Filtered by module: `38 — Saving` (बचत), `91 — FD` (मुदत ठेव), `38 — Pigmy` (डेली), `91 — FD` (रिकरिंग sample). Enter resolves by ID or name |
| 7 | खातेधारक निवडा | Select Account Holder | Autocomplete | Yes | Sample: `101 — Account Holder 1`. Resolving loads summary panel + Tab 4 customer data |

### Editable Transaction Fields

| # | Marathi Label | English Label | Type | Required | Visibility | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- | :--- |
| 8 | व्यवहार रक्कम (रु.) | Transaction Amount (Rs.) | Textbox | Yes | All | — |
| 9 | व्यवहार तपशील | Transaction Details | Textbox | No | All | — |
| 10 | विशेष सूचना | Special Instructions | Textbox | No | All | Single editable field; remove duplicate read-only copies from summary |
| 11 | आंतर शाखेचा शुल्क | Inter-branch Charges | Textbox | No | बचत | Proposed for Advanced — bank reviewer sign-off during mockup |
| 12 | व्याज दिनांक | Interest Date | Date | No | मुदत ठेव | — |
| 13 | कमिशन कपात | Commission Deduction | Textbox | No | डेली | — |
| 14 | सवलत (रु.) | Discount (Rs.) | Textbox | No | रिकरिंग | Credit mode only |

**Removed link:** `कर्ज खाते माहिती` — redundant; staff use Tab 4 (Customer Details) for loan accounts.

**Actions:** `पूर्ण`, `पूर्ववत`, `पुढे`.

### Account Summary Panel (computed read-only Labels)

Displayed after account resolve. Field visibility driven by **मॉड्यूल निवडा** and **नावे / जमा** where noted.

| # | Marathi Label | English Label | Visibility |
| :---: | :--- | :--- | :--- |
| 15 | खातेवही शिल्लक | Ledger Balance | All |
| 16 | न वटलेली शिल्लक | Uncleared Balance | All |
| 17 | अक्षरी रक्कम | Amount in Words | All |
| 18 | व्यवहारानंतरची शिल्लक | Balance After Transaction | All |
| 19 | सदस्य क्र. | Member No. | All |
| 20 | पॅन / आधार क्रमांक | PAN / Aadhaar No. | All |
| 21 | टीडीएस (रु.) | TDS (Rs.) | बचत, डेली |
| 22 | एकूण टीडीएस येणे (रु.) | Total TDS Receivable | बचत |
| 23 | एकूण टीडीएस देणे (रु.) | Total TDS Payable | डेली |
| 24 | खाते चालवण्याची सूचना | Account Operating Instructions | बचत |
| 25 | अंतिम पोस्ट दिनांक | Last Post Date | मुदत ठेव |
| 26 | शिल्लक व्याज | Balance Interest | मुदत ठेव |
| 27 | व्याज | Interest | डेली |
| 28 | एकूण | Total | डेली |
| 29 | परतीची दिनांक | Return Date | डेली, रिकरिंग |
| 30 | परतीची रक्कम | Return Amount | रिकरिंग |
| 31 | एकूण दंड | Total Penalty | रिकरिंग (Credit) |
| 32 | थकीत हप्ते | Overdue Installments | रिकरिंग (Credit) |
| 33 | देय हप्ता दिनांक | Due Installment Date | रिकरिंग (Credit) |

### Section: प्रगत सेटिंग्ज (Advanced Settings)

> Collapsed by default. Visible when expanded.

| # | Marathi Label | English Label | Type | Visibility | Notes |
| :---: | :--- | :--- | :--- | :--- | :--- |
| 34 | स्पॉट कमिशन (रु.) | Spot Commission (Rs.) | Label (read-only) | मुदत ठेव, डेली, रिकरिंग | — |
| 35 | स्पॉट कमिशन रेट | Spot Commission Rate | Label (read-only) | मुदत ठेव, डेली, रिकरिंग | — |
| 36 | तरतूद | Provision | Label (read-only) | डेली | — |
| 37 | खुली रक्कम | Open Amount | Label (read-only) | डेली | — |
| 38 | एकूण दिवस | Total Days | Label (read-only) | डेली | — |
| 39 | शेवटची नावे दिनांक | Last Debit Date | Label (read-only) | डेली | — |

---

## Tab 2: साहित्य तपशील (Instrument Details)

Common across all modules. Recurring legacy label "बँक तपशील" / "चेक तपशील" unified here.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | धनादेश प्रकार निवडा | Select Cheque Type | Dropdown | No | Values: `स्लिप` (Slip), `चेक` (Cheque). Default: `स्लिप` |
| 2 | चेक रक्कम (रु.) | Cheque Amount (Rs.) | Label (read-only) | No | From Tab 1 amount |
| 3 | रक्कम अक्षरी | Amount in Words | Label (read-only) | No | Computed |
| 4 | चेक दिनांक | Cheque Date | Date | Yes | — |
| 5 | चेक क्र. | Cheque No. | Textbox | Yes | — |
| 6 | नाव | Name | Textbox | Yes | — |
| 7 | बँक निवडा | Select Bank | Autocomplete | Yes | From Bank Master. Sample: `1 — बँक ऑफ इंडिया`, `2 — स्टेट बँक ऑफ इंडिया`, `3 — बँक ऑफ महाराष्ट्र`, `4 — एचडीएफसी बँक`. Enter resolves by ID or name; see [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |
| 8 | बँक शाखा | Bank Branch | Textbox | No | — |
| 9 | ड्रॉन ऑन बँक | Drawn on Bank | Textbox | No | — |
| 10 | ड्रॉन ऑन ब्रांच | Drawn on Branch | Textbox | No | — |
| 11 | अंतर्गत चेक नंबर | Internal Cheque Number | Label (read-only) | No | System-generated |

**Navigation:** `मागे`, `पुढे`, `पूर्ण`, `पूर्ववत`.

---

## Tab 3: ट्रान्सफर (Transfer)

Common across all modules. Same field pattern as [savings-transaction-screen.md](../savings/savings-transaction-screen.md) Tab 3.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा निवडा | Select Branch | Autocomplete | Yes | Sample: `1 — Branch 1` |
| 2 | जी.एल. निवडा | Select GL | Autocomplete | Yes | Filtered by context |
| 3 | खातेधारक निवडा | Select Account Holder | Autocomplete | Yes | Sample: `101 — Account Holder 1` |
| 4 | शिल्लक(जमा) | Balance (Credit) | Label (read-only) | No | — |
| 5 | जमा / नावे | Credit / Debit | Radio | No | — |
| 6 | व्यवहार रक्कम (रु) | Transaction Amount (Rs.) | Textbox | Yes | — |
| 7 | एकूण व्यवहार रक्कम (रु) | Total Transaction Amount | Label (read-only) | No | Sum of grid rows |

**Action:** `+ टाका` (Add). **Grid columns:** निवडा, अनु क्र, जी.एल.हेड, खाते क्र., नाव, शिल्लक, व्यवहार रक्कम.

**Grid actions:** `निर्यात करा`, `हटवा`, `निश्चित करा` (FD legacy). **Footer:** `व्यवहार रक्कम` summary.

**Navigation:** `मागे`, `पुढे`.

---

## Tab 4: ग्राहक तपशील (Customer Details)

Replaces legacy **केवायसी माहिती** tab and Daily **कर्ज माहिती** informational content. Auto-loads when Tab 1 **खातेधारक निवडा** resolves — no separate customer picker on this tab.

### Customer Identity (read-only)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | ग्राहक नाव | Customer Name | Label (read-only) | No | From resolved account holder |
| 2 | ग्राहक क्रमांक | Customer Number | Label (read-only) | No | — |
| 3 | मोबाईल क्रमांक | Mobile Number | Label (read-only) | No | — |
| 4 | पॅन / आधार क्रमांक | PAN / Aadhaar No. | Label (read-only) | No | — |
| 5 | शाखा | Branch | Label (read-only) | No | — |

### Cross-Product Account Summary

Layout varies by product — not one combined grid.

#### बचत आणि डेली (Savings and Daily) — account cards

One **paper-style card** per account. Compact fields only.

| # | Marathi Label | English Label | Notes |
| :---: | :--- | :--- | :--- |
| 6 | खाते क्र. | Account No. | Per card |
| 7 | शिल्लक | Balance | Per card |
| 8 | स्थिती | Status | Badge on card header |
| 9 | परतीची दिनांक | Return Date | Daily cards only, when applicable |

#### रिकरिंग (Recurring) — separate grid

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 10 | खाते क्र. | Account No. |
| 11 | शिल्लक | Balance |
| 12 | देय हप्ता दिनांक | Due Installment Date |
| 13 | देय रक्कम | Due Amount |
| 14 | स्थिती | Status |

#### मुदत ठेव (Fixed Deposit) — separate grid

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 15 | खाते क्र. | Account No. |
| 16 | मुद्दल | Principal |
| 17 | परिपक्वता दिनांक | Maturity Date |
| 18 | परिपक्वता रक्कम | Maturity Amount |
| 19 | स्थिती | Status |

#### कर्ज (Loan) — separate grid

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 20 | खाते क्र. | Account No. |
| 21 | थकबाकी | Outstanding Balance |
| 22 | थकीत रक्कम | Overdue Amount |
| 23 | स्थिती | Status |

**Loan rows:** Display outstanding balance and overdue amount. **`TODO`:** "recover from this collection" action (replaces Daily कर्ज माहिती recovery workflow) — deferred.

### Section: पूर्ण केवायसी (Full KYC) — collapsible

> Collapsed by default. Read-only **address list** for the resolved customer — same grid columns as [new-customer-screen.md](../customer/new-customer-screen.md) Tab 2 Address Grid. No editable address form on this screen.

#### Address Grid Columns (read-only)

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 24 | निवडा | Select |
| 25 | अनु. क्र | Sr. No. |
| 26 | पत्त्याचा प्रकार | Address Type |
| 27 | पत्ता | Address |
| 28 | जिल्हा | District |
| 29 | ब्लॉक | Block |
| 30 | शहर | City |
| 31 | ठिकाण | Location |
| 32 | पिन कोड | Pin Code |
| 33 | दूरध्वनी क्रमांक | Telephone Number |

**Address Type values** (display only): `कायमचा` (Permanent), `कॉन्टॅक्ट` (Contact), `इतर` (Other) — per New Customer Tab 2.

**Actions:** `मागे`, `पूर्ण`, `पूर्ववत`.

---

## Tab 5: खातेवही (Ledger)

> **Shared component:** `app-ledger-tab`. Same 15-column grid as [dividend-transaction-screen.md](../membership/dividend-transaction-screen.md) Tab 5 and Loan transaction screens. Reused here — resolved from `TODO` (2026-07-22).

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | या दिनांकापासून | From Date | Date | Yes | — |
| 2 | या दिनांकापर्यंत | To Date | Date | Yes | — |

**Actions:** `दाखवा`, `स्टेटमेंट प्रिंट`, `पासबुक`. **Display:** `ओपनिंग बॅलन्स`.

**Grid columns:** निवडा, अनु. क्र., दिनांक, चलन क्र., सूचना प्रकार, सूचना क्र., नावे, जमा, शिल्लक, तपशील, व्यवहार, वापरकर्ता, वेळ, सत्र, पासिंग यूजर.

**Footer:** `एकूण नावे`, `एकूण जमा`, `चलन प्रिंट`, `ड्राफ्ट प्रिंट`, `निर्यात करा`.

**Navigation:** `मागे`, `पूर्ण`, `पूर्ववत`.

---

## Deferred Items (TODO — out of scope for this spec pass)

| Item | Notes |
| :--- | :--- |
| Loan recovery from collection | Daily pigmy loan recovery action; display-only in Customer Details for now |
| Recurring debit-mode Tab 1 fields | Maturity payout, premature closure, TDS, payout mode — not captured in screenshots |

---

## Mockup

- [HTML mockup (Draft)](../mockups/accounting/deposit-account-transaction-screen/) — Marathi layout for bank review

---

## Related Documents

- [ux-optimization.md](ux-optimization.md)
- [overview.md](overview.md)
- [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
- [../bank/bank-management-screen.md](../bank/bank-management-screen.md)
- [../customer/new-customer-screen.md](../customer/new-customer-screen.md)
- [../savings/savings-transaction-screen.md](../savings/savings-transaction-screen.md)
- [../fixed-deposit/fd-transaction-screen.md](../fixed-deposit/fd-transaction-screen.md)
- [../daily/daily-transaction-screen.md](../daily/daily-transaction-screen.md)
- [../recurring/recurring-transaction-screen.md](../recurring/recurring-transaction-screen.md)
- [../membership/dividend-transaction-screen.md](../membership/dividend-transaction-screen.md) — Ledger tab pattern source
