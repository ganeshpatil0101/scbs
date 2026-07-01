# Screen Spec — FD Transaction (मुदत ठेव > व्यवहार)

## Purpose

UI specification for fixed deposit account transactions. Five-tab workflow (same pattern as savings).

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | व्यवहार | Transaction |
| Breadcrumb | डॅशबोर्ड > मुदत ठेव > व्यवहार | Dashboard > Fixed Deposit > Transaction |
| Parent Module | मुदत ठेव | Fixed Deposit |

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
| `screenshots/मुदत ठेव/डॅशबोर्ड-मुदत ठेव-व्यवहार.png` | Tab 1 |
| `screenshots/मुदत ठेव/डॅशबोर्ड-मुदत ठेव-व्यवहार-1.png` | Tab 1 (duplicate view) |
| `screenshots/मुदत ठेव/डॅशबोर्ड-मुदत ठेव-व्यवहार-2.png` | Tab 3 — Transfer |
| `screenshots/मुदत ठेव/डॅशबोर्ड-मुदत ठेव-व्यवहार-3.png` | Tab 4 — Ledger |

---

## Tab 1: खात्याची माहिती (Account Information)

### Transaction Header

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | चलन क्रमांक | Challan Number | Textbox | No | Read-only |
| 2 | नावे / जमा | Debit / Credit | Radio | Yes | — |
| 3 | रोख / ट्रान्सफर | Cash / Transfer | Radio | Yes | — |

### Account Fields (FD-specific)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 4 | शाखा निवडा | Select Branch | Autocomplete | Yes | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 5 | जी.एल. निवडा | Select GL | Autocomplete | Yes | Sample: `91 — FD`. Enter resolves by ID or name; shows display name |
| 6 | खातेधारक निवडा | Select Account Holder | Autocomplete | Yes | Sample: `101 — Account Holder 1`, `102 — Account Holder 2`, `103 — Account Holder 3`. Enter resolves by ID or name; shows display name |
| 7 | अंतिम पोस्ट दिनांक | Last Post Date | Textbox | No | Read-only |
| 8 | पॅनकार्ड क्र. | PAN Card No. | Textbox | No | Read-only |
| 9 | व्याज दिनांक | Interest Date | Date | No | — |
| 10 | शिल्लक व्याज | Balance Interest | Textbox | No | Read-only |
| 11 | व्यवहार रक्कम (रुपये मध्ये) | Transaction Amount (Rs.) | Textbox | Yes | — |
| 12 | अक्षरी रक्कम | Amount in Words | Textbox | No | Read-only |
| 13 | लेजर शिल्लक (जमा) | Ledger Balance (Credit) | Textbox | No | Read-only |
| 14 | न वटलेली शिल्लक | Uncleared Balance | Textbox | No | Read-only |
| 15 | व्यवहारानंतरची शिल्लक | Balance After Transaction | Textbox | No | Read-only |
| 16 | व्यवहार तपशील | Transaction Details | Textbox | No | — |
| 17 | विशेष सूचना | Special Instructions | Textbox | No | — |
| 18 | स्पॉट कमिशन (रु.) | Spot Commission (Rs.) | Textbox | No | Read-only |
| 19 | स्पॉट कमिशन रेट | Spot Commission Rate | Textbox | No | Read-only |
| 20 | सदस्य क्र. | Member No. | Textbox | No | Read-only |

**Link:** `कर्ज खाते माहिती`. **KYC:** `फोटो / सही दाखवा`. **Action:** `पुढे`.

---

## Tab 3: ट्रान्सफर (Transfer)

Same field pattern as [savings-transaction-screen.md](../savings/savings-transaction-screen.md) Tab 3.

**Actions:** `+ टाका`, `निश्चित करा`, `हटवा`, `मागे`, `पुढे`.

---

## Tab 4: खातेवही (Ledger)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | या दिनांकापासून | From Date | Date | Yes | — |
| 2 | या दिनांकापर्यंत | To Date | Date | Yes | — |

**Actions:** `दाखवा`, `स्टेटमेंट प्रिंट`, `पासबुक`, `चलन प्रिंट`, `ड्राफ्ट प्रिंट`. **Display:** `ओपनिंग बॅलन्स`.

**Grid columns:** Same as savings ledger. **Footer:** `एकूण नावे`, `एकूण जमा`. **Action:** `मागे`.

Tabs 2, 5: `TODO` — not captured in screenshots.

---

## Related Documents

- [overview.md](overview.md)
- [new-fd-account-screen.md](new-fd-account-screen.md)
- [../savings/savings-transaction-screen.md](../savings/savings-transaction-screen.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
