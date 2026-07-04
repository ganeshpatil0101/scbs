# Screen Spec — Dividend Transaction (सभासदत्व > लाभांश व्यवहार)

## Purpose

UI specification for posting dividend payment transactions against member dividend warrants. Six-tab workflow (cash/transfer, debit/credit).

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | लाभांश व्यवहार | Dividend Transaction |
| Breadcrumb | डॅशबोर्ड > सभासदत्व > लाभांश व्यवहार | Dashboard > Membership > Dividend Transaction |
| Parent Module | सभासदत्व | Membership |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | खात्याची माहिती | Account Information |
| 2 | व्यवहार | Transaction |
| 3 | चेक तपशील | Cheque Details |
| 4 | ट्रान्सफर | Transfer |
| 5 | खातेवही | Ledger |
| 6 | केवायसी माहिती | KYC Information |

## Reference Screenshots

| File | Tab |
| :--- | :--- |
| `screenshots/sabhsadatv/डॅशबोर्ड-सभासदत्व-लाभांश व्यवहार-02_07.png` | Tab 1 |
| `screenshots/sabhsadatv/डॅशबोर्ड-सभासदत्व-लाभांश व्यवहार-1-02_07.png` | Tab 2 |
| `screenshots/sabhsadatv/डॅशबोर्ड-सभासदत्व-लाभांश व्यवहार-2-02_07.png` | Tab 3 |
| `screenshots/sabhsadatv/डॅशबोर्ड-सभासदत्व-लाभांश व्यवहार-3-02_07.png` | Tab 4 |
| `screenshots/sabhsadatv/डॅशबोर्ड-सभासदत्व-लाभांश व्यवहार-4-02_07.png` | Tab 5 |

---

## Tab 1: खात्याची माहिती (Account Information)

### Member Type

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | सभासद | Member | Radio | No | Default selected |
| 2 | नाममात्र सभासद | Nominal Member | Radio | No | — |

### Member Lookup

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 3 | सभासद क्रमांक | Member Number | Textbox | Yes | — |
| 4 | ग्राहकाचे नाव | Customer Name | Textbox | Yes | Read-only after lookup |

### Dividend Warrant Grid

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | अनु. क्र. | Sr. No. |
| 3 | वॉरंट नंबर | Warrant Number |
| 4 | रक्कम | Amount |
| 5 | वाटप दिनांक | Distribution Date |
| 6 | वटल्याचा दिनांक | Encashment Date |

### Summary

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 5 | एकूण लाभांश (रु.) | Total Dividend (Rs.) | Textbox | No | Read-only |
| 6 | लाभांश देय (रु.) | Dividend Payable (Rs.) | Textbox | No | Read-only |

**KYC preview:** `फोटो / सही दाखवा` with photo, signature, ID proof, address proof placeholders.

**Navigation:** `पुढे`.

---

## Tab 2: व्यवहार (Transaction)

### Transaction Header

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | चलन क्रमांक | Challan Number | Textbox | No | Read-only; e.g. `52` |
| 2 | नावे / जमा | Debit / Credit | Radio | Yes | — |
| 3 | रोख / ट्रान्सफर | Cash / Transfer | Radio | Yes | — |

### Account Fields

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 4 | शाखा निवडा | Select Branch | Autocomplete | Yes | Sample: `1 — कोतोली मुख्य कार्यालय`. Enter resolves by ID or name |
| 5 | जी.एल. निवडा | Select GL | Autocomplete | Yes | Sample: `3 — देणे लाभांश`. Enter resolves by ID or name |
| 6 | खातेधारक निवडा | Select Account Holder | Autocomplete | Yes | Enter resolves by ID or name; shows display name |
| 7 | शिल्लक | Balance | Textbox | No | Read-only |
| 8 | न वटलेली शिल्लक | Uncleared Balance | Textbox | No | Read-only |
| 9 | व्यवहार रक्कम (रु.) | Transaction Amount (Rs.) | Textbox | Yes | — |
| 10 | पॅन | PAN | Textbox | No | Read-only |
| 11 | आधार क्रमांक | Aadhaar Number | Textbox | No | Read-only |
| 12 | अक्षरी रक्कम | Amount in Words | Textbox | No | Read-only |
| 13 | व्यवहार तपशील | Transaction Details | Textbox | No | — |

**Navigation:** `मागे`, `पुढे`, `पूर्ण`, `पूर्ववत`.

---

## Tab 3: चेक तपशील (Cheque Details)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | धनादेश प्रकार निवडा | Select Cheque Type | Dropdown | No | e.g. `चेक` (Cheque). Other values: `TODO` |
| 2 | चेक रक्कम (रु.) | Cheque Amount (Rs.) | Textbox | No | — |
| 3 | रक्कम अक्षरी | Amount in Words | Textbox | No | — |
| 4 | चेक दिनांक | Cheque Date | Date | Yes | — |
| 5 | चेक क्र. | Cheque No. | Textbox | Yes | — |
| 6 | नाव | Name | Textbox | Yes | — |
| 7 | बँक निवडा | Select Bank | Dropdown | Yes | Default: `निवडा`. Values: `TODO` |
| 8 | बँक शाखा | Bank Branch | Textbox | No | — |
| 9 | ड्रॉन ऑन बँक | Drawn on Bank | Textbox | No | Read-only |
| 10 | ड्रॉन ऑन ब्रांच | Drawn on Branch | Textbox | No | Read-only |
| 11 | एनईएफटी/आरटीजीएस | NEFT/RTGS | Checkbox | No | — |

**Navigation:** `मागे`, `पुढे`, `पूर्ण`, `पूर्ववत`.

---

## Tab 4: ट्रान्सफर (Transfer)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा निवडा | Select Branch | Autocomplete | Yes | Enter resolves by ID or name |
| 2 | जी.एल. निवडा | Select GL | Autocomplete | Yes | e.g. `1 — वसूल भाग भांडवल` |
| 3 | खातेधारक निवडा | Select Account Holder | Autocomplete | No | — |
| 4 | शिल्लक(जमा) | Balance (Credit) | Textbox | No | Read-only |
| 5 | व्यवहार रक्कम (रु) | Transaction Amount (Rs.) | Textbox | Yes | — |
| 6 | एकूण व्यवहार रक्कम (रु) | Total Transaction Amount | Textbox | No | Read-only |

**Action:** `+ टाका` (Add).

**Grid columns:** निवडा, अनु. क्र., जी.एल. हेड, खाते क्र., नाव, शिल्लक, व्यवहार रक्कम (रु).

**Grid actions:** `नियमित करा`, `हटवा`. **Footer:** `व्यवहार रक्कम` summary.

**Navigation:** `मागे`, `पुढे`.

---

## Tab 5: खातेवही (Ledger)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | या दिनांकापासून | From Date | Date | Yes | — |
| 2 | या दिनांकापर्यंत | To Date | Date | Yes | — |

**Actions:** `दाखवा`, `स्टेटमेंट प्रिंट`, `पासबुक`. **Display:** `ओपनिंग बॅलन्स`.

**Grid columns:** निवडा, अनु. क्र., दिनांक, चलन क्र., सूचना प्रकार, सूचना क्र., नावे, जमा, शिल्लक, तपशील, व्यवहार, वापरकर्ता, वेळ, सत्र, पासिंग यूजर.

**Footer:** `एकूण नावे`, `एकूण जमा`, `चलन प्रिंट`, `ड्राफ्ट प्रिंट`, `निर्यात करा`.

**Navigation:** `मागे`, `पुढे`.

---

## Tab 6: केवायसी माहिती (KYC Information)

`TODO` — tab referenced in navigation; no dedicated screenshot in `02_07` set. Follow savings transaction KYC tab pattern.

---

## Related Documents

- [overview.md](overview.md)
- [member-register-screen.md](member-register-screen.md)
- [../settings/membership/dividend-calculation-screen.md](../settings/membership/dividend-calculation-screen.md)
- [../savings/savings-transaction-screen.md](../savings/savings-transaction-screen.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
