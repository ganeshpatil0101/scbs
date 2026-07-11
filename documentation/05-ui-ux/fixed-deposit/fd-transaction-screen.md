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
| 1 | चलन क्रमांक | Challan Number | Label (read-only) | No | Auto-generated; e.g. `42` |
| 2 | नावे / जमा | Debit / Credit | Radio | Yes | — |
| 3 | रोख / ट्रान्सफर | Cash / Transfer | Radio | Yes | — |

### Account Lookup

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 4 | शाखा निवडा | Select Branch | Autocomplete | Yes | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 5 | जी.एल. निवडा | Select GL | Autocomplete | Yes | Sample: `91 — FD`. Enter resolves by ID or name; shows display name |
| 6 | खातेधारक निवडा | Select Account Holder | Autocomplete | Yes | Sample: `101 — Account Holder 1`, `102 — Account Holder 2`, `103 — Account Holder 3`. Enter resolves by ID or name; shows display name |

### Editable Transaction Fields

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 7 | व्याज दिनांक | Interest Date | Date | No | — |
| 8 | व्यवहार रक्कम (रुपये मध्ये) | Transaction Amount (Rs.) | Textbox | Yes | — |
| 9 | व्यवहार तपशील | Transaction Details | Textbox | No | — |

### Account Summary Panel (computed read-only Labels)

Displayed after account resolve. Replaces individual editable textboxes for calculated values.

| # | Marathi Label | English Label |
| :---: | :--- | :--- |
| 10 | अंतिम पोस्ट दिनांक | Last Post Date |
| 11 | पॅनकार्ड क्र. | PAN Card No. |
| 12 | शिल्लक व्याज | Balance Interest |
| 13 | अक्षरी रक्कम | Amount in Words |
| 14 | लेजर शिल्लक (जमा) | Ledger Balance (Credit) |
| 15 | न वटलेली शिल्लक | Uncleared Balance |
| 16 | व्यवहारानंतरची शिल्लक | Balance After Transaction |
| 17 | सदस्य क्र. | Member No. |

### Section: प्रगत सेटिंग्ज (Advanced Settings)

> Collapsed by default.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 18 | विशेष सूचना | Special Instructions | Textbox | No | — |
| 19 | स्पॉट कमिशन (रु.) | Spot Commission (Rs.) | Label (read-only) | No | — |
| 20 | स्पॉट कमिशन रेट | Spot Commission Rate | Label (read-only) | No | — |

**Link:** `कर्ज खाते माहिती`. **KYC:** `फोटो / सही दाखवा`. **Action:** `पुढे`.

---

## Tab 2: साहित्य तपशील (Instrument Details)

`TODO` — not captured in screenshots.

---

## Tab 3: ट्रान्सफर (Transfer)

Same field pattern as [savings-transaction-screen.md](../savings/savings-transaction-screen.md) Tab 3.

**Actions:** `+ टाका`, `निश्चित करा`, `हटवा`, `मागे`, `पुढे`.

---

## Tab 4: खातेवही (Ledger)

Uses shared component `app-ledger-tab` — same columns as savings ledger.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | या दिनांकापासून | From Date | Date | Yes | — |
| 2 | या दिनांकापर्यंत | To Date | Date | Yes | — |

**Actions:** `दाखवा`, `स्टेटमेंट प्रिंट`, `पासबुक`, `चलन प्रिंट`, `ड्राफ्ट प्रिंट`. **Display:** `ओपनिंग बॅलन्स`.

**Grid columns:** Same as savings ledger. **Footer:** `एकूण नावे`, `एकूण जमा`. **Action:** `मागे`.

---

## Tab 5: केवायसी माहिती (KYC Information)

`TODO` — not captured in screenshots. Uses shared component `app-kyc-info-tab` when captured.

---

## Related Documents

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [new-fd-account-screen.md](new-fd-account-screen.md)
- [../savings/savings-transaction-screen.md](../savings/savings-transaction-screen.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
