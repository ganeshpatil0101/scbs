# Screen Spec — Loan Credit Transaction (कर्ज > जमा व्यवहार)

## Purpose

UI specification for loan repayment (credit) transactions — installment allocation, other credits, transfer, ledger, and guarantor view.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | जमा व्यवहार | Credit Transaction |
| Breadcrumb | डॅशबोर्ड > कर्ज > जमा व्यवहार | Dashboard > Loan > Credit Transaction |
| Parent Module | कर्ज | Loan |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | कर्ज माहिती | Loan Information |
| 2 | इतर जमा | Other Credits |
| 3 | हप्ते | Installments |
| 4 | चेक तपशील | Cheque Details |
| 5 | ट्रान्सफर | Transfer |
| 6 | खातेवही | Ledger |
| 7 | जामीनदार | Guarantor |

## Reference Screenshots

| File | Tab |
| :--- | :--- |
| `screenshots/कर्ज/डॅशबोर्ड-कर्ज-जमा व्यवहार-1-05-07.png` | Tab 1 |
| `screenshots/कर्ज/डॅशबोर्ड-कर्ज-जमा व्यवहार-2-05-07.png` | Tab 2 |
| `screenshots/कर्ज/डॅशबोर्ड-कर्ज-जमा व्यवहार-3-05-07.png` | Tab 3 |
| `screenshots/कर्ज/डॅशबोर्ड-कर्ज-जमा व्यवहार-4-05-07.png` | Tab 4 |
| `screenshots/कर्ज/डॅशबोर्ड-कर्ज-जमा व्यवहार-5-05-07.png` | Tab 5 |
| `screenshots/कर्ज/डॅशबोर्ड-कर्ज-जमा व्यवहार-6-05-07.png` | Tab 6 |
| `screenshots/कर्ज/डॅशबोर्ड-कर्ज-जमा व्यवहार-7-05-07.png` | Tab 7 |

---

## Tab 1: कर्ज माहिती (Loan Information)

### Transaction Header

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | चलन क्रमांक | Challan Number | Textbox | No | Read-only |
| 2 | व्यवहार प्रकार | Transaction Mode | Radio | Yes | `रोख` (Cash), `ट्रान्सफर` (Transfer) |

### Account Fields

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 3 | शाखा कोड | Branch Code | Textbox | Yes | e.g. `1` |
| 4 | शाखा निवडा | Select Branch | Dropdown | Yes | e.g. `कोतोली मुख्य कार्यालय` |
| 5 | जी.एल. हेड | G.L. Head | Textbox | Yes | e.g. `61` |
| 6 | जी.एल. निवडा | Select G.L. | Dropdown | Yes | e.g. `जामिनकी कर्ज` |
| 7 | खाते क्रमांक | Account Number | Textbox | Yes | — |
| 8 | खातेधारक शोधा | Search Account Holder | Textbox | Yes | — |
| 9 | खातेधारक निवडा | Select Account Holder | Dropdown | Yes | — |
| 10 | लेजर शिल्लक (नावे) | Ledger Balance (Debit) | Textbox | No | Read-only |
| 11 | न वटलेली शिल्लक (जमा) | Uncleared Balance (Credit) | Textbox | No | Read-only |
| 12 | आगाऊ व्याज तारीख | Advance Interest Date | Date | Yes | — |
| 13 | पॅनकार्ड - आधार क्र. | PAN - Aadhaar No. | Textbox | No | Read-only |
| 14 | कर्ज मंजुरी अधिकारी | Loan Sanctioning Officer | Textbox | No | Read-only |
| 15 | पालक कर्मचारी | Parent Employee | Textbox | No | Read-only |
| 16 | व्यवहार रक्कम (रु.) | Transaction Amount (Rs.) | Textbox | Yes | — |
| 17 | अक्षरी रक्कम | Amount in Words | Textbox | No | Read-only |
| 18 | व्यवहार तपशील | Transaction Details | Textbox | No | — |
| 19 | विशेष सूचना | Special Instructions | Textbox | No | — |
| 20 | सदस्य क्र. | Member No. | Textbox | No | Read-only |

### Loan Summary (व्यवहार तपशील)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 21 | कर्ज रक्कम | Loan Amount | Textbox | No | Read-only |
| 22 | चालू दिनांक | Open Date | Textbox | No | Read-only |
| 23 | कालावधी | Tenure | Textbox | No | Read-only |
| 24 | शेवटची दिनांक | End Date | Textbox | No | Read-only |
| 25 | व्याज दर | Interest Rate | Textbox | No | Read-only |
| 26 | हप्त्याची रक्कम | Installment Amount | Textbox | No | Read-only |
| 27 | इतर जमा | Other Credits | Textbox | No | Read-only |
| 28 | आज अखेर येणे | Due Till Today | Textbox | No | Read-only |
| 29 | खाते बंद रक्कम | Account Closing Amount | Textbox | No | Read-only |
| 30 | एन.पी.ए. स्थिती | NPA Status | Textbox | No | Read-only |
| 31 | परतफेड प्रकार | Repayment Type | Dropdown | Yes | `TODO` — placeholder `निवडा` in screenshot |
| 32 | थकीत रक्कम | Overdue Amount | Textbox | No | Read-only |
| 33 | थकीत हप्ते | Overdue Installments | Textbox | No | Read-only |
| 34 | हप्ता तारीख | Installment Date | Date | No | Read-only |

**KYC preview:** `फोटो / सही दाखवा` with photo, signature, ID proof, address proof placeholders.

**Navigation:** `पुढे`. **Actions:** `पूर्ण`, `पूर्ववत`.

---

## Tab 2: इतर जमा (Other Credits)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | कपात प्रकार निवडा | Select Deduction Type | Dropdown | No | `TODO` — dropdown empty in screenshot |

**Actions:** `+टाका`, `कपात गणना पुन्हा`.

**Grid columns:** निवडा, अनु. क्र., खाते, रक्कम, जीएसटी.

**Grid actions:** `निर्यात करा`, `काढा`.

**Summary:** एकूण रक्कम, एकूण जी.एस.टी., एकूण रक्कम + जीएसटी.

**Navigation:** `मागे`, `पुढे`.

---

## Tab 3: हप्ते (Installments)

### Summary Header

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शेवटची व्याज दिनांक | Last Interest Date | Label | No | Read-only |
| 2 | अंतिम व्याज तारखेपासून कालावधी | Period from Last Interest Date | Label | No | Read-only |
| 3 | व्यवहार रक्कम (रु.) | Transaction Amount (Rs.) | Label | No | Read-only |

### Allocation Grid

Rows: थकीत दंड व्याज येणे, थकीत व्याज देणे, इतर जमा, दंड व्याज, व्याज, मुदत रक्कम, एकूण.

**Columns:** (row label), चालू व्याज, थकीत व्याज, येणे, व्यवहार (editable), शिल्लक.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 4 | व्यवहारानंतरची शिल्लक (रु.) | Balance After Transaction (Rs.) | Textbox | No | Read-only |
| 5 | व्याज प्रॉडक्ट | Interest Product | Textbox | No | — |

**Navigation:** `मागे`, `पुढे`. **Actions:** `पूर्ण`, `पूर्ववत`.

---

## Tab 4: चेक तपशील (Cheque Details)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | धनादेश प्रकार निवडा | Select Cheque Type | Dropdown | No | e.g. `स्लिप` (Slip) |
| 2 | चेक रक्कम (रु.) | Cheque Amount (Rs.) | Textbox | No | Read-only |
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

## Tab 5: ट्रान्सफर (Transfer)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा कोड | Branch Code | Textbox | Yes | — |
| 2 | शाखा निवडा | Select Branch | Dropdown | Yes | — |
| 3 | जी.एल. हेड क्र. | G.L. Head No. | Textbox | Yes | — |
| 4 | जी.एल. निवडा | Select G.L. | Dropdown | Yes | — |
| 5 | खाते क्र. | Account No. | Textbox | Yes | — |
| 6 | खातेधारक शोधा | Search Account Holder | Textbox | Yes | — |
| 7 | खातेधारक निवडा | Select Account Holder | Dropdown | Yes | — |
| 8 | शिल्लक(जमा) | Balance (Credit) | Textbox | No | Read-only |
| 9 | जमा / नावे | Credit / Debit | Radio | No | — |
| 10 | व्यवहार रक्कम (रू) | Transaction Amount (Rs.) | Textbox | Yes | — |
| 11 | एकूण व्यवहार रक्कम (रू) | Total Transaction Amount (Rs.) | Textbox | No | Read-only |

**Action:** `+ टाका`. **Grid columns:** निवडा, अनु क्र, जी.एल. हेड, खाते क्र., नाव, शिल्लक, व्यवहार रक्कम.

**Grid actions:** `सुधारित करा`, `हटवा`.

**Navigation:** `मागे`, `पुढे`.

---

## Tab 6: खातेवही (Ledger)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | या दिनांकापासून | From Date | Date | Yes | — |
| 2 | या दिनांकापर्यंत | To Date | Date | Yes | — |

**Actions:** `दाखवा`, `स्टेटमेंट प्रिंट`, `पासबुक`. **Display:** `ओपनिंग बॅलन्स`.

**Grid columns:** निवडा, अनु. क्र., दिनांक, चलन क्र., सूचना प्रकार, सूचना क्र., एकूण जमा, मुद्दल (नावे), मुद्दल (जमा), व्याज (नावे), व्याज (जमा), दंड व्याज (नावे), दंड व्याज (जमा), रिबेट (नावे), रिबेट (जमा), इतर शुल्क (नावे), इतर शुल्क (जमा), शिल्लक, तपशील, व्यवहार, वापरकर्ता, वेळ, सत्र, पासिंग युजर.

**Summary:** एकूण नावे, एकूण जमा.

**Actions:** `चलन प्रिंट`, `ड्राफ्ट प्रिंट`, `निर्यात करा`.

### Loan Actions Sub-section

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 3 | या दिनांकापासून | From Date | Date | No | Loan actions filter |
| 4 | या दिनांकापर्यंत | To Date | Date | No | — |

**Grid columns:** अ.क्र., Action Date, Action Taken, Contact Method, Action Details, Collected Amount, Fee Amount, Next Action, Next Action Date.

**Navigation:** `मागे`.

---

## Tab 7: जामीनदार (Guarantor)

Read-only grid.

**Columns:** अनु. क्र., ग्राहक क्र., नाव, पत्ता, जिल्हा, तालुका, शहर, ठिकाण, पिन कोड, दुरध्वनी क्रमांक, मोबाईल क्रमांक.

**Navigation:** `मागे`. **Actions:** `पूर्ण`, `पूर्ववत`.

---

## Related Documents

- [overview.md](overview.md)
- [loan-debit-transaction-screen.md](loan-debit-transaction-screen.md)
- [loan-information-screen.md](loan-information-screen.md)
