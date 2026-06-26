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
| 4 | शाखा कोड | Branch Code | Textbox | Yes | Read-only |
| 5 | शाखा निवडा | Select Branch | Dropdown | Yes | — |
| 6 | जी एल हेड | GL Head | Textbox | Yes | Read-only |
| 7 | जी.एल.निवडा | Select GL | Textbox | No | e.g. `मुदत ठेव` |
| 8 | खाते क्रमांक | Account Number | Textbox | Yes | — |
| 9 | खातेधारक शोधा | Search Account Holder | Textbox | Yes | — |
| 10 | खातेधारक निवडा | Select Account Holder | Dropdown | Yes | — |
| 11 | अंतिम पोस्ट दिनांक | Last Post Date | Textbox | No | Read-only |
| 12 | पॅनकार्ड क्र. | PAN Card No. | Textbox | No | Read-only |
| 13 | व्याज दिनांक | Interest Date | Date | No | — |
| 14 | शिल्लक व्याज | Balance Interest | Textbox | No | Read-only |
| 15 | व्यवहार रक्कम (रुपये मध्ये) | Transaction Amount (Rs.) | Textbox | Yes | — |
| 16 | अक्षरी रक्कम | Amount in Words | Textbox | No | Read-only |
| 17 | लेजर शिल्लक (जमा) | Ledger Balance (Credit) | Textbox | No | Read-only |
| 18 | न वटलेली शिल्लक | Uncleared Balance | Textbox | No | Read-only |
| 19 | व्यवहारानंतरची शिल्लक | Balance After Transaction | Textbox | No | Read-only |
| 20 | व्यवहार तपशील | Transaction Details | Textbox | No | — |
| 21 | विशेष सूचना | Special Instructions | Textbox | No | — |
| 22 | स्पॉट कमिशन (रु.) | Spot Commission (Rs.) | Textbox | No | Read-only |
| 23 | स्पॉट कमिशन रेट | Spot Commission Rate | Textbox | No | Read-only |
| 24 | सदस्य क्र. | Member No. | Textbox | No | Read-only |

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
