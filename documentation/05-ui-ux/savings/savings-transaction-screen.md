# Screen Spec — Savings Transaction (बचत > व्यवहार)

> **Superseded (2026-07-18):** Merged into [../accounting/deposit-account-transaction-screen.md](../accounting/deposit-account-transaction-screen.md). Retained for field archaeology.

## Purpose

UI specification for savings account transactions (cash/transfer, credit/debit). Five-tab workflow.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | व्यवहार | Transaction |
| Breadcrumb | डॅशबोर्ड > बचत > व्यवहार | Dashboard > Savings > Transaction |
| Parent Module | बचत | Savings |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | खात्याची माहिती | Account Information |
| 2 | साहित्य तपशील | Instrument Details |
| 3 | ट्रान्सफर | Transfer |
| 4 | खातेवही | Ledger |
| 5 | केवायसी माहिती | KYC Information |

## Reference Screenshots

| File | Tab |
| :--- | :--- |
| `screenshots/bachat/डॅशबोर्ड-बचत-व्यवहार.png` | Tab 1 |
| `screenshots/bachat/डॅशबोर्ड-बचत-व्यवहार -1.png` | Tab 2 |
| `screenshots/bachat/डॅशबोर्ड-बचत-व्यवहार -2.png` | Tab 3 |
| `screenshots/bachat/डॅशबोर्ड-बचत-व्यवहार -3.png` | Tab 4 |

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
| 5 | जी.एल. निवडा | Select GL | Autocomplete | Yes | Sample: `38 — Saving`. Enter resolves by ID or name; shows display name |
| 6 | खातेधारक निवडा | Select Account Holder | Autocomplete | Yes | Sample: `101 — Account Holder 1`, `102 — Account Holder 2`, `103 — Account Holder 3`. Enter resolves by ID or name; shows display name |

### Editable Transaction Fields

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 7 | व्यवहार रक्कम (रु.) | Transaction Amount (Rs.) | Textbox | Yes | — |
| 8 | विशेष सूचना | Special Instructions | Textbox | No | — |
| 9 | आंतर शाखेचा शुल्क | Inter-branch Charges | Textbox | No | — |
| 10 | व्यवहार तपशील | Transaction Details | Textbox | No | — |

### Account Summary Panel (computed read-only Labels)

Displayed after account resolve. Replaces individual editable textboxes for calculated values.

| # | Marathi Label | English Label |
| :---: | :--- | :--- |
| 11 | अक्षरी रक्कम | Amount in Words |
| 12 | टीडीएस (रु.) | TDS (Rs.) |
| 13 | एकूण टीडीएस येणे (रु.) | Total TDS Receivable |
| 14 | लेजर शिल्लक (जमा) | Ledger Balance (Credit) |
| 15 | न वटलेली शिल्लक | Uncleared Balance |
| 16 | व्यवहारानंतरची शिल्लक | Balance After Transaction |
| 17 | पॅन - आधार क्रमांक | PAN - Aadhaar No. |
| 18 | खाते चालवण्याची सूचना | Account Operating Instructions |
| 19 | सदस्य क्र. | Member No. |

**Link:** `कर्ज खाते माहिती` (Loan Account Information).

**KYC preview:** `फोटो / सही दाखवा` with photo, signature, ID proof, address proof placeholders.

**Actions:** `पूर्ण`, `पूर्ववत`, `पुढे`.

---

## Tab 2: साहित्य तपशील (Instrument Details)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | धनादेश प्रकार निवडा | Select Cheque Type | Dropdown | No | e.g. `स्लिप` (Slip). Other values: `TODO` |
| 2 | चेक रक्कम (रु.) | Cheque Amount (Rs.) | Label (read-only) | No | From Tab 1 amount |
| 3 | रक्कम अक्षरी | Amount in Words | Label (read-only) | No | Computed |
| 4 | चेक दिनांक | Cheque Date | Date | Yes | — |
| 5 | चेक क्र. | Cheque No. | Textbox | Yes | — |
| 6 | नाव | Name | Textbox | Yes | — |
| 7 | बँक निवडा | Select Bank | Dropdown | Yes | `TODO` |
| 8 | बँक शाखा | Bank Branch | Textbox | No | — |
| 9 | ड्रॉन ऑन बँक | Drawn on Bank | Textbox | No | — |
| 10 | ड्रॉन ऑन ब्रांच | Drawn on Branch | Textbox | No | — |
| 11 | अंतर्गत चेक नंबर | Internal Cheque Number | Label (read-only) | No | System-generated |

**Navigation:** `मागे`, `पुढे`, `पूर्ण`, `पूर्ववत`.

---

## Tab 3: ट्रान्सफर (Transfer)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा निवडा | Select Branch | Autocomplete | Yes | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 2 | जी.एल. निवडा | Select GL | Autocomplete | Yes | Sample: `38 — Saving`. Enter resolves by ID or name; shows display name |
| 3 | खातेधारक निवडा | Select Account Holder | Autocomplete | Yes | Sample: `101 — Account Holder 1`, `102 — Account Holder 2`, `103 — Account Holder 3`. Enter resolves by ID or name; shows display name |
| 4 | शिल्लक(जमा) | Balance (Credit) | Label (read-only) | No | — |
| 5 | जमा / नावे | Credit / Debit | Radio | No | — |
| 6 | व्यवहार रक्कम (रु) | Transaction Amount (Rs.) | Textbox | Yes | — |
| 7 | एकूण व्यवहार रक्कम (रु) | Total Transaction Amount | Label (read-only) | No | Sum of grid rows |

**Action:** `+ टाका` (Add). **Grid columns:** निवडा, अनु क्र, जी.एल.हेड, खाते क्र., नाव, शिल्लक, व्यवहार रक्कम.

**Grid actions:** `निर्यात करा`, `हटवा`. **Footer:** `व्यवहार रक्कम` summary.

---

## Tab 4: खातेवही (Ledger)

Uses shared component `app-ledger-tab` — same columns across Savings/FD/Daily/Recurring.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | या दिनांकापासून | From Date | Date | Yes | — |
| 2 | या दिनांकापर्यंत | To Date | Date | Yes | — |

**Actions:** `दाखवा`, `स्टेटमेंट प्रिंट`, `पासबुक`. **Display:** `ओपनिंग बॅलन्स`.

**Grid columns:** निवडा, अनु. क्र., दिनांक, चलन क्र., सूचना प्रकार, सूचना क्र., नावे, जमा, शिल्लक, तपशील, व्यवहार, वापरकर्ता, वेळ, सत्र, पासिंग युजर.

**Footer:** `एकूण नावे`, `एकूण जमा`, `चलन प्रिंट`, `ड्राफ्ट प्रिंट`, `निर्यात करा`.

---

## Tab 5: केवायसी माहिती (KYC Information)

`TODO` — tab referenced in navigation; no dedicated screenshot. Uses shared component `app-kyc-info-tab` when captured.

---

## Mockup

- [HTML mockup (Draft)](../mockups/savings/savings-transaction-screen/) — Marathi layout for bank review

## Related Documents

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [new-savings-account-screen.md](new-savings-account-screen.md)
- [../accounting/jama-screen.md](../accounting/jama-screen.md)
- [../fixed-deposit/fd-transaction-screen.md](../fixed-deposit/fd-transaction-screen.md)
- [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
