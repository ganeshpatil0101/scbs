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

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | चलन क्रमांक | Challan Number | Textbox | No | Read-only |
| 2 | नावे / जमा | Debit / Credit | Radio | Yes | — |
| 3 | रोख / ट्रान्सफर | Cash / Transfer | Radio | Yes | — |
| 4 | शाखा कोड | Branch Code | Textbox | Yes | e.g. `1` |
| 5 | शाखा निवडा | Select Branch | Dropdown | Yes | e.g. `कोतोली मुख्य कार्यालय` |
| 6 | जी.एल. हेड | G.L. Head | Textbox | Yes | e.g. `134` |
| 7 | जी.एल. निवडा | Select G.L. | Dropdown | Yes | — |
| 8 | खाते क्रमांक | Account Number | Textbox | Yes | — |
| 9 | खातेधारक निवडा | Select Account Holder | Dropdown | Yes | Investment bank account |
| 10 | मागील पोस्ट दिनांक | Last Post Date | Textbox | No | Read-only |
| 11 | व्याज रक्कम (रु.) | Interest Amount (Rs.) | Textbox | No | Read-only |
| 12 | व्याज दिनांक | Interest Date | Date | No | — |
| 13 | मुद्दल रक्कम (रु.) | Principal Amount (Rs.) | Textbox | No | Read-only |
| 14 | लेजर शिल्लक (नावे) | Ledger Balance (Debit) | Textbox | No | Read-only |
| 15 | शिल्लक व्याज (रु.) | Balance Interest (Rs.) | Textbox | No | Read-only |
| 16 | न वटलेली शिल्लक | Uncleared Balance | Textbox | No | Read-only |
| 17 | व्यवहार रक्कम (रु.) | Transaction Amount (Rs.) | Textbox | Yes | — |
| 18 | अक्षरी रक्कम | Amount in Words | Textbox | No | Read-only |
| 19 | व्यवहार तपशील | Transaction Details | Textbox | No | — |

**Link:** `दस्तऐवज पहा` (View Document).

**Navigation:** `पुढे`. **Actions:** `पूर्ण`, `पूर्ववत`.

---

## Tab 2: चेक तपशील (Cheque Details)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | धनादेश प्रकार निवडा | Select Cheque Type | Dropdown | No | e.g. `स्लिप` (Slip) |
| 2 | चेक रक्कम (रु.) | Cheque Amount (Rs.) | Textbox | No | — |
| 3 | रक्कम अक्षरी | Amount in Words | Textbox | No | Read-only |
| 4 | चेक दिनांक | Cheque Date | Date | Yes | — |
| 5 | चेक क्र. | Cheque No. | Textbox | Yes | — |
| 6 | नाव | Name | Textbox | Yes | — |
| 7 | बँक निवडा | Select Bank | Dropdown | Yes | `TODO` |
| 8 | बँक शाखा | Bank Branch | Textbox | No | — |
| 9 | ड्रॉन ऑन बँक | Drawn on Bank | Textbox | No | — |
| 10 | ड्रॉन ऑन ब्रांच | Drawn on Branch | Textbox | No | — |

**Navigation:** `मागे`, `पुढे`.

---

## Tab 3: ट्रान्सफर (Transfer)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा कोड | Branch Code | Textbox | Yes | — |
| 2 | शाखा निवडा | Select Branch | Dropdown | Yes | — |
| 3 | जी.एल.हेड.क्र. | G.L. Head No. | Textbox | Yes | — |
| 4 | जी.एल.निवडा | Select G.L. | Dropdown | No | — |
| 5 | खाते क्र. | Account No. | Textbox | Yes | — |
| 6 | खातेधारक शोधा | Search Account Holder | Textbox | Yes | — |
| 7 | खातेधारक निवडा | Select Account Holder | Dropdown | Yes | — |
| 8 | शिल्लक | Balance | Textbox | No | Read-only |
| 9 | व्यवहार रक्कम (रु) | Transaction Amount (Rs.) | Textbox | Yes | — |
| 10 | एकूण व्यवहार रक्कम (रु) | Total Transaction Amount (Rs.) | Textbox | No | Read-only |

**Action:** `+टाका`. **Grid columns:** निवडा, अनु क्र, जी.एल.हेड, खाते क्र., नाव, शिल्लक, व्यवहार रक्कम.

**Grid actions:** `निर्यात करा`, `हटवा`.

**Navigation:** `मागे`, `पुढे`.

---

## Tab 4: खातेवही (Ledger)

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

## Related Documents

- [overview.md](overview.md)
- [bank-deposit-new-account-screen.md](bank-deposit-new-account-screen.md)
- [../savings/savings-transaction-screen.md](../savings/savings-transaction-screen.md)
