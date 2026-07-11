# Screen Spec — Bank Deposit Transaction (गुंतवणूक > बँक ठेव > व्यवहार)

## Purpose

UI specification for bank deposit account transactions (debit/credit, cash/transfer).

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | व्यवहार | Transaction |
| Breadcrumb | डॅशबोर्ड > गुंतवणूक > बँक ठेव > व्यवहार | Dashboard > Investment > Bank Deposit > Transaction |
| Parent Module | गुंतवणूक > बँक ठेव | Investment > Bank Deposit |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | खात्याची माहिती | Account Information |
| 2 | चेक तपशील | Cheque Details |
| 3 | ट्रान्सफर | Transfer |
| 4 | खातेवही | Ledger |

## Reference Screenshots

| File | Tab |
| :--- | :--- |
| `screenshots/गुंतवणूक/डॅशबोर्ड -गुंतवणूक - बँक ठेव - व्यवहार-1.png` | Tab 1 |
| `screenshots/गुंतवणूक/डॅशबोर्ड -गुंतवणूक - बँक ठेव - व्यवहार-2.png` | Tab 2 |
| `screenshots/गुंतवणूक/डॅशबोर्ड -गुंतवणूक - बँक ठेव - व्यवहार-3.png` | Tab 3 |
| `screenshots/गुंतवणूक/डॅशबोर्ड -गुंतवणूक - बँक ठेव - व्यवहार-4.png` | Tab 4 |

---

## Tab 1: खात्याची माहिती (Account Information)

### Transaction Header

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | चलन क्रमांक | Challan Number | Label (read-only) | No | Auto-generated |
| 2 | नावे / जमा | Debit / Credit | Radio | Yes | — |
| 3 | रोख / ट्रान्सफर | Cash / Transfer | Radio | Yes | Drives Tab 2 and Tab 3 visibility |

### Account Lookup

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 4 | शाखा निवडा | Select Branch | Autocomplete | Yes | Enter resolves by ID or name; e.g. `1 — कोतोली मुख्य कार्यालय`. See [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |
| 5 | जी.एल. निवडा | Select GL | Autocomplete | Yes | Investment bank deposit GL scope. Enter resolves by ID or name |
| 6 | खातेधारक निवडा | Select Account Holder | Autocomplete | Yes | Replaces `खाते क्रमांक` + dropdown. Enter resolves by account no. or name |

### Editable Transaction Fields

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 7 | व्याज दिनांक | Interest Date | Date | No | — |
| 8 | व्यवहार रक्कम (रु.) | Transaction Amount (Rs.) | Textbox | Yes | — |
| 9 | व्यवहार तपशील | Transaction Details | Textbox | No | — |

### Account Summary Panel (computed read-only Labels)

Displayed after account resolve. Replaces individual editable textboxes for calculated values.

| # | Marathi Label | English Label |
| :---: | :--- | :--- |
| 10 | मागील पोस्ट दिनांक | Last Post Date |
| 11 | व्याज रक्कम (रु.) | Interest Amount (Rs.) |
| 12 | मुद्दल रक्कम (रु.) | Principal Amount (Rs.) |
| 13 | लेजर शिल्लक (नावे) | Ledger Balance (Debit) |
| 14 | शिल्लक व्याज (रु.) | Balance Interest (Rs.) |
| 15 | न वटलेली शिल्लक | Uncleared Balance |
| 16 | अक्षरी रक्कम | Amount in Words |

**Link:** `दस्तऐवज पहा` (View Document).

**Navigation:** `पुढे`. **Actions:** `पूर्ण`, `पूर्ववत`.

---

## Tab 2: चेक तपशील (Cheque Details)

> **Visible:** When **रोख / ट्रान्सफर** = Transfer and cheque instrument required.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | धनादेश प्रकार निवडा | Select Cheque Type | Dropdown | No | e.g. `स्लिप` (Slip) |
| 2 | चेक रक्कम (रु.) | Cheque Amount (Rs.) | Textbox | No | — |
| 3 | रक्कम अक्षरी | Amount in Words | Label (read-only) | No | Auto-filled from cheque amount |
| 4 | चेक दिनांक | Cheque Date | Date | Yes | — |
| 5 | चेक क्र. | Cheque No. | Textbox | Yes | — |
| 6 | नाव | Name | Textbox | Yes | — |
| 7 | बँक निवडा | Select Bank | Autocomplete | Yes | Values: `TODO` — scaffold from master data service |
| 8 | बँक शाखा | Bank Branch | Textbox | No | External bank branch |

**Removed:** Redundant `ड्रॉन ऑन बँक` / `ड्रॉन ऑन ब्रांच` — covered by Bank Autocomplete + branch textbox.

**Navigation:** `मागे`, `पुढे`.

---

## Tab 3: ट्रान्सफर (Transfer)

> **Visible:** When **रोख / ट्रान्सफर** = Transfer.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा निवडा | Select Branch | Autocomplete | Yes | Enter resolves by ID or name |
| 2 | जी.एल. निवडा | Select GL | Autocomplete | No | Enter resolves by ID or name |
| 3 | खातेधारक निवडा | Select Account Holder | Autocomplete | Yes | Replaces `खाते क्र.` + `खातेधारक शोधा` + `खातेधारक निवडा` |
| 4 | शिल्लक | Balance | Label (read-only) | No | After account resolve |
| 5 | व्यवहार रक्कम (रु) | Transaction Amount (Rs.) | Textbox | Yes | — |
| 6 | एकूण व्यवहार रक्कम (रु) | Total Transaction Amount (Rs.) | Label (read-only) | No | Sum of grid rows |

**Action:** `+टाका`. **Grid columns:** निवडा, अनु क्र, जी.एल.हेड, खाते क्र., नाव, शिल्लक, व्यवहार रक्कम.

**Grid actions:** `निर्यात करा`, `हटवा`.

**Navigation:** `मागे`, `पुढे`.

---

## Tab 4: खातेवही (Ledger)

> Uses shared component **`app-ledger-tab`** — same columns and actions as FD/Savings transaction ledger tabs.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | या दिनांकापासून | From Date | Date | Yes | — |
| 2 | या दिनांकापर्यंत | To Date | Date | Yes | — |

**Actions:** `दाखवा`, `स्टेटमेंट प्रिंट`, `पासबुक`. **Display:** `ओपनिंग बॅलन्स`.

**Grid columns:** निवडा, अनु. क्र, दिनांक, चलन क्र., सूचना प्रकार, सूचना क्र., नावे, जमा, शिल्लक, तपशील, व्यवहार, वापरकर्ता, वेळ, सत्र, पासिंग युजर.

**Summary:** एकूण नावे, एकूण जमा.

**Actions:** `चलन प्रिंट`, `ड्राफ्ट प्रिंट`.

**Navigation:** `मागे`.

---

## Mockup

- [HTML mockup (Draft)](../mockups/investment/bank-deposit-transaction-screen/) — Marathi layout for bank review

## Related Documents

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [bank-deposit-new-account-screen.md](bank-deposit-new-account-screen.md)
- [../fixed-deposit/fd-transaction-screen.md](../fixed-deposit/fd-transaction-screen.md)
- [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
