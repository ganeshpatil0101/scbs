# Screen Spec — Recurring Transaction (रिकरिंग > व्यवहार)

> **Superseded (2026-07-18):** Merged into [../accounting/deposit-account-transaction-screen.md](../accounting/deposit-account-transaction-screen.md). Retained for field archaeology.

> **Previously consolidated:** [credit-transaction-screen.md](credit-transaction-screen.md) + debit mode shell (fields `TODO` until screenshots)

## Purpose

Single screen for recurring deposit installment credits and debit transactions (maturity payout / premature closure). Credit/Debit mode on Tab 1 controls which fields are shown. Matches [../daily/daily-transaction-screen.md](../daily/daily-transaction-screen.md) and [../savings/savings-transaction-screen.md](../savings/savings-transaction-screen.md) pattern.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | व्यवहार | Transaction |
| Breadcrumb | डॅशबोर्ड > रिकरिंग > व्यवहार | Dashboard > Recurring > Transaction |
| Parent Module | रिकरिंग | Recurring |

## Tabs

| # | Marathi Tab | English Tab | Visibility | Replaces |
| :---: | :--- | :--- | :--- | :--- |
| 1 | खात्याची माहिती | Account Information | Both | Credit Tab 1 / Debit Tab 1 |
| 2 | बँक तपशील | Bank Details | Both | Credit Tab 2 |
| 3 | ट्रान्सफर | Transfer | Both | Credit Tab 3 |
| 4 | खातेवही | Ledger | Both | Credit Tab 4 |
| 5 | केवायसी माहिती | KYC Information | Both | Credit Tab 5 |

**Mode selector (Tab 1):** Radio `नावे / जमा` — required. `जमा` = installment credit; `नावे` = maturity payout / premature closure.

## Reference Screenshots / Media

| File | Tab |
| :--- | :--- |
| `screenshots/रिकरिंग/डॅशबोर्ड_रिकरिंग_जमा व्यवहार.mp4` | All tabs (from video) |
| `screenshots/रिकरिंग/credit-transaction-frames/frame_0010.jpg` | Tab 1 — Credit |
| `screenshots/रिकरिंग/credit-transaction-frames/frame_0000.jpg` | Tab 5 — KYC |

---

## Tab 1: खात्याची माहिती (Account Information)

### Transaction Header

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | चलन क्रमांक | Challan Number | Label (read-only) | No | Auto-generated; e.g. `42` |
| 2 | नावे / जमा | Debit / Credit | Radio | Yes | `नावे` (Debit), `जमा` (Credit) |
| 3 | रोख / ट्रान्सफर | Cash / Transfer | Radio | Yes | — |

### Account Lookup

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 4 | शाखा निवडा | Select Branch | Autocomplete | Yes | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 5 | जी.एल. निवडा | Select GL | Autocomplete | Yes | Sample: `91 — FD` (Recurring). Enter resolves by ID or name; shows display name |
| 6 | खातेधारक निवडा | Select Account Holder | Autocomplete | Yes | Sample: `101 — Account Holder 1`, `102 — Account Holder 2`, `103 — Account Holder 3`. Enter resolves by ID or name; shows display name |

### Editable Transaction Fields

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 7 | व्यवहार रक्कम (रु.) | Transaction Amount (Rs.) | Textbox | Yes | — |
| 8 | व्यवहार तपशील | Transaction Details | Textbox | No | — |
| 9 | सवलत (रु.) | Discount (Rs.) | Textbox | No | Credit mode: rebate on installment |

### Account Summary Panel (computed read-only Labels)

Displayed after account resolve. Replaces individual editable textboxes for calculated values.

| # | Marathi Label | English Label | Visibility |
| :---: | :--- | :--- | :--- |
| 10 | खातेवही शिल्लक | Ledger Balance | Both |
| 11 | न वटलेली शिल्लक | Uncleared Balance | Both |
| 12 | अक्षरी रक्कम | Amount in Words | Both |
| 13 | एकूण दंड | Total Penalty | Credit |
| 14 | व्यवहारानंतरची शिल्लक (रु.) | Balance After Transaction | Both |
| 15 | सदस्य क्र. | Member No. | Both |
| 16 | पॅन | PAN | Both |
| 17 | विशेष सूचना | Special Instructions | Both |
| 18 | परतीची दिनांक | Return Date | Both |
| 19 | परतीची रक्कम | Return Amount | Both |
| 20 | स्पॉट कमिशन (रु.) | Spot Commission | Both |
| 21 | स्पॉट कमिशन रेट | Spot Commission Rate | Both |
| 22 | थकीत हप्ते | Overdue Installments | Credit |
| 23 | देय हप्ता दिनांक | Due Installment Date | Credit |

**Links:** `कर्ज खाते माहिती`. **KYC preview:** `फोटो / सही दाखवा`.

**Action:** `पुढे` (Next).

### Debit Mode (नावे) — Tab 1 extension

> `TODO — debit-specific fields not captured`. Expected: maturity payout amount, premature closure penalty, TDS deduction, payout mode. Capture from legacy app screenshots before mockup/Angular.

---

## Tab 2: बँक तपशील (Bank Details)

`TODO` — not captured. Reference [../savings/savings-transaction-screen.md](../savings/savings-transaction-screen.md) instrument/bank details pattern when screenshots available.

---

## Tab 3: ट्रान्सफर (Transfer)

`TODO` — not captured. Same transfer tab pattern as Savings/FD/Daily transaction screens.

---

## Tab 4: खातेवही (Ledger)

Uses shared component `app-ledger-tab` — same 15-column ledger grid as Savings/FD/Daily transaction screens.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | या दिनांकापासून | From Date | Date | Yes | — |
| 2 | या दिनांकापर्यंत | To Date | Date | Yes | — |

**Actions:** `दाखवा`, `स्टेटमेंट प्रिंट`, `पासबुक`.

`TODO` — full ledger grid columns deferred to shared component spec.

---

## Tab 5: केवायसी माहिती (KYC Information)

Uses shared component `app-kyc-info-tab`.

**Action:** `केवायसी दाखवा` (Show KYC).

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा | Branch | Display | No | Read-only |
| 2 | ग्राहक क्रमांक | Customer Number | Display | No | Read-only |
| 3 | ग्राहक नाव | Customer Name | Display | No | Read-only |
| 4 | मोबाईल क्रमांक | Mobile Number | Display | No | Read-only |
| 5 | आधार क्रमांक | Aadhaar Number | Display | No | Read-only |
| 6 | पॅन क्रमांक | PAN Number | Display | No | Read-only |

**Media:** फोटो, सही, ओळखपत्र पुरावा, पत्त्याचा पुरावा.

### पत्त्याची माहिती (Address)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 7 | पत्त्याचा प्रकार | Address Type | Dropdown | No | Values: `TODO` |
| 8 | इमारत / फ्लॅट / घर नं. | Building / Flat / House No. | Textbox | No | — |
| 9 | रस्ता | Road | Textbox | No | — |
| 10 | लँडमार्क | Landmark | Textbox | No | — |
| 11 | ठिकाण | Location | Textbox | No | — |
| 12 | राज्य | State | Textbox | No | — |
| 13 | जिल्हा | District | Textbox | No | — |
| 14 | तालुका | Taluka | Textbox | No | — |
| 15 | शहर | City | Textbox | No | — |
| 16 | पिन कोड | Pin Code | Textbox | No | — |
| 17 | ई-मेल | E-mail | Textbox | No | — |

**Actions:** `मागे`, `पूर्ण`, `पूर्वतवत`.

---

## Mockup

- [HTML mockup (Draft)](../mockups/recurring/recurring-transaction-screen/) — Marathi layout for bank review

## Related Documents

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [../daily/daily-transaction-screen.md](../daily/daily-transaction-screen.md)
- [../savings/savings-transaction-screen.md](../savings/savings-transaction-screen.md)
- [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
