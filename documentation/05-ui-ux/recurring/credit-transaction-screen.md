# Screen Spec — Recurring Credit Transaction (रिकरिंग > जमा व्यवहार)

## Purpose

UI specification for recurring deposit credit (installment) transactions. Five-tab workflow.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | जमा व्यवहार | Credit Transaction |
| Breadcrumb | डॅशबोर्ड > रिकरिंग > जमा व्यवहार | Dashboard > Recurring > Credit Transaction |
| Parent Module | रिकरिंग | Recurring |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | खात्याची माहिती | Account Information |
| 2 | बँक तपशील | Bank Details |
| 3 | ट्रान्सफर | Transfer |
| 4 | खातेवही | Ledger |
| 5 | केवायसी माहिती | KYC Information |

## Reference Screenshots / Media

| File | Tab |
| :--- | :--- |
| `screenshots/रिकरिंग/डॅशबोर्ड_रिकरिंग_जमा व्यवहार.mp4` | All tabs (from video) |
| `screenshots/रिकरिंग/credit-transaction-frames/frame_0010.jpg` | Tab 1 |
| `screenshots/रिकरिंग/credit-transaction-frames/frame_0000.jpg` | Tab 5 — KYC |

---

## Tab 1: खात्याची माहिती (Account Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | चलन क्रमांक | Challan Number | Textbox | No | Read-only; e.g. `42` |
| 2 | रोख / ट्रान्सफर | Cash / Transfer | Radio | Yes | — |
| 3 | शाखा कोड | Branch Code | Textbox | Yes | e.g. `1` |
| 4 | शाखा निवडा | Select Branch | Dropdown | Yes | e.g. कोतोली मुख्य कार्यालय |
| 5 | जी.एल. हेड | GL Head | Textbox | Yes | e.g. `91` |
| 6 | जी.एल. निवडा | Select GL | Dropdown | Yes | e.g. `रिकरिंग ठेव` |
| 7 | खाते क्रमांक | Account Number | Textbox | Yes | — |
| 8 | खातेधारक शोधा | Search Account Holder | Textbox | Yes | — |
| 9 | खातेधारक निवडा | Select Account Holder | Dropdown | Yes | Values: `TODO` |
| 10 | खातेवही शिल्लक | Ledger Balance | Textbox | No | Read-only |
| 11 | न वटलेली शिल्लक | Uncleared Balance | Textbox | No | Read-only |
| 12 | व्यवहार रक्कम (रु.) | Transaction Amount (Rs.) | Textbox | No | — |
| 13 | अक्षरी रक्कम | Amount in Words | Textbox | No | Read-only |
| 14 | एकूण दंड | Total Penalty | Textbox | No | Read-only |
| 15 | व्यवहारानंतरची शिल्लक (रु.) | Balance After Transaction | Textbox | No | Read-only |
| 16 | सदस्य क्र. | Member No. | Textbox | No | Read-only |
| 17 | व्यवहार तपशील | Transaction Details | Textbox | No | — |
| 18 | पॅन | PAN | Textbox | No | Read-only |
| 19 | विशेष सूचना | Special Instructions | Textbox | No | Read-only |
| 20 | सवलत (रु.) | Discount (Rs.) | Textbox | No | — |
| 21 | परतीची दिनांक | Return Date | Textbox | No | Read-only |
| 22 | परतीची रक्कम | Return Amount | Textbox | No | Read-only |
| 23 | स्पॉट कमिशन (रु.) | Spot Commission | Textbox | No | Read-only |
| 24 | स्पॉट कमिशन रेट | Spot Commission Rate | Textbox | No | Read-only |
| 25 | थकीत हप्ते | Overdue Installments | Textbox | No | Read-only |
| 26 | देय हप्ता दिनांक | Due Installment Date | Textbox | No | Read-only |

**Link:** `कर्ज खाते माहिती`. **KYC preview:** `फोटो / सही दाखवा`.

**Action:** `पुढे` (Next). Tabs 2–4: `TODO`.

---

## Tab 5: केवायसी माहिती (KYC Information)

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

## Cross-Links

- [overview.md](overview.md)
- [../savings/savings-transaction-screen.md](../savings/savings-transaction-screen.md)
