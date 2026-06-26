# Screen Spec — Savings Transaction (बचत > व्यवहार)

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
| 1 | चलन क्रमांक | Challan Number | Textbox | No | Read-only; e.g. `42` |
| 2 | नावे / जमा | Debit / Credit | Radio | Yes | — |
| 3 | रोख / ट्रान्सफर | Cash / Transfer | Radio | Yes | — |

### Account Fields

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 4 | शाखा कोड | Branch Code | Textbox | Yes | Read-only |
| 5 | शाखा निवडा | Select Branch | Dropdown | Yes | — |
| 6 | जी.एल. हेड | GL Head | Textbox | Yes | Read-only |
| 7 | जी.एल. निवडा | Select GL | Dropdown | Yes | e.g. `सेव्हिंग ठेव` |
| 8 | खाते क्रमांक | Account Number | Textbox | Yes | — |
| 9 | खातेधारक शोधा | Search Account Holder | Textbox | Yes | — |
| 10 | खातेधारक निवडा | Select Account Holder | Dropdown | Yes | `TODO` |
| 11 | व्यवहार रक्कम (रु.) | Transaction Amount (Rs.) | Textbox | Yes | — |
| 12 | अक्षरी रक्कम | Amount in Words | Textbox | No | Read-only |
| 13 | टीडीएस (रु.) | TDS (Rs.) | Textbox | No | Read-only |
| 14 | एकूण टीडीएस येणे (रु.) | Total TDS Receivable | Textbox | No | Read-only |
| 15 | लेजर शिल्लक (जमा) | Ledger Balance (Credit) | Textbox | No | Read-only |
| 16 | न वटलेली शिल्लक | Uncleared Balance | Textbox | No | Read-only |
| 17 | व्यवहारानंतरची शिल्लक | Balance After Transaction | Textbox | No | Read-only |
| 18 | पॅन - आधार क्रमांक | PAN - Aadhaar No. | Textbox | No | Read-only |
| 19 | खाते चालवण्याची सूचना | Account Operating Instructions | Textbox | No | e.g. `स्वतः` |
| 20 | सदस्य क्र. | Member No. | Textbox | No | Read-only |
| 21 | विशेष सूचना | Special Instructions | Textbox | No | — |
| 22 | आंतर शाखेचा शुल्क | Inter-branch Charges | Textbox | No | — |
| 23 | व्यवहार तपशील | Transaction Details | Textbox | No | — |

**Link:** `कर्ज खाते माहिती` (Loan Account Information).

**KYC preview:** `फोटो / सही दाखवा` with photo, signature, ID proof, address proof placeholders.

**Actions:** `पूर्ण`, `पूर्ववत`, `पुढे`.

---

## Tab 2: साहित्य तपशील (Instrument Details)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | धनादेश प्रकार निवडा | Select Cheque Type | Dropdown | No | e.g. `स्लिप` (Slip). Other values: `TODO` |
| 2 | चेक रक्कम (रु.) | Cheque Amount (Rs.) | Textbox | No | Read-only |
| 3 | रक्कम अक्षरी | Amount in Words | Textbox | No | Read-only |
| 4 | चेक दिनांक | Cheque Date | Date | Yes | — |
| 5 | चेक क्र. | Cheque No. | Textbox | Yes | — |
| 6 | नाव | Name | Textbox | Yes | — |
| 7 | बँक निवडा | Select Bank | Dropdown | Yes | `TODO` |
| 8 | बँक शाखा | Bank Branch | Textbox | No | — |
| 9 | ड्रॉन ऑन बँक | Drawn on Bank | Textbox | No | — |
| 10 | ड्रॉन ऑन ब्रांच | Drawn on Branch | Textbox | No | — |
| 11 | अंतर्गत चेक नंबर | Internal Cheque Number | Textbox | No | Read-only |

**Navigation:** `मागे`, `पुढे`, `पूर्ण`, `पूर्ववत`.

---

## Tab 3: ट्रान्सफर (Transfer)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा कोड | Branch Code | Textbox | Yes | Read-only |
| 2 | शाखा निवडा | Select Branch | Dropdown | Yes | — |
| 3 | जी.एल.हेड.क्र. | GL Head No. | Textbox | Yes | — |
| 4 | जी.एल.निवडा | Select GL | Textbox | No | — |
| 5 | खाते क्र. | Account No. | Textbox | Yes | — |
| 6 | खातेधारक शोधा | Search Account Holder | Textbox | Yes | — |
| 7 | खातेधारक निवडा | Select Account Holder | Dropdown | Yes | — |
| 8 | शिल्लक(जमा) | Balance (Credit) | Textbox | No | Read-only |
| 9 | जमा / नावे | Credit / Debit | Radio | No | — |
| 10 | व्यवहार रक्कम (रु) | Transaction Amount (Rs.) | Textbox | Yes | — |
| 11 | एकूण व्यवहार रक्कम (रु) | Total Transaction Amount | Textbox | No | Read-only |

**Action:** `+ टाका` (Add). **Grid columns:** निवडा, अनु क्र, जी.एल.हेड, खाते क्र., नाव, शिल्लक, व्यवहार रक्कम.

**Grid actions:** `निर्यात करा`, `हटवा`. **Footer:** `व्यवहार रक्कम` summary.

---

## Tab 4: खातेवही (Ledger)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | या दिनांकापासून | From Date | Date | Yes | — |
| 2 | या दिनांकापर्यंत | To Date | Date | Yes | — |

**Actions:** `दाखवा`, `स्टेटमेंट प्रिंट`, `पासबुक`. **Display:** `ओपनिंग बॅलन्स`.

**Grid columns:** निवडा, अनु. क्र., दिनांक, चलन क्र., सूचना प्रकार, सूचना क्र., नावे, जमा, शिल्लक, तपशील, व्यवहार, वापरकर्ता, वेळ, सत्र, पासिंग युजर.

**Footer:** `एकूण नावे`, `एकूण जमा`, `चलन प्रिंट`, `ड्राफ्ट प्रिंट`, `निर्यात करा`.

---

## Tab 5: केवायसी माहिती (KYC Information)

`TODO` — tab referenced in navigation; no dedicated screenshot.

---

## Related Documents

- [overview.md](overview.md)
- [new-savings-account-screen.md](new-savings-account-screen.md)
- [../accounting/jama-screen.md](../accounting/jama-screen.md)
