# Screen Spec — Membership Transaction (सभासदत्व > सभासदत्व व्यवहार)

## Purpose

UI specification for share capital transactions (credit/debit, cash/transfer) including partial withdrawal and share allocation. Seven-tab workflow.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | सभासदत्व व्यवहार | Membership Transaction |
| Breadcrumb | डॅशबोर्ड > सभासदत्व > सभासदत्व व्यवहार | Dashboard > Membership > Membership Transaction |
| Parent Module | सभासदत्व | Membership |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | खात्याची माहिती | Account Information |
| 2 | साहित्य तपशील | Instrument Details |
| 3 | ट्रान्सफर | Transfer |
| 4 | शेअर्स वाटप | Share Allocation |
| 5 | वारसदाराची माहिती | Nominee Information |
| 6 | शेअर्सची माहिती | Share Information |
| 7 | के.वाय.सी. माहिती | KYC Information |

## Reference Screenshots

| File | Tab |
| :--- | :--- |
| `screenshots/sabhsadatv/डॅशबोर्ड-सभासदत्व-सभासदत्व व्यवहार-1-02_07.png` | Tab 1 |
| `screenshots/sabhsadatv/डॅशबोर्ड-सभासदत्व-सभासदत्व व्यवहार-2-02_07.png` | Tab 2 |
| `screenshots/sabhsadatv/डॅशबोर्ड-सभासदत्व-सभासदत्व व्यवहार-3-02_07.png` | Tab 3 |
| `screenshots/sabhsadatv/डॅशबोर्ड-सभासदत्व-सभासदत्व व्यवहार-4-02_07.png` | Tab 4 |
| `screenshots/sabhsadatv/डॅशबोर्ड-सभासदत्व-सभासदत्व व्यवहार-5-02_07.png` | Tab 6 |

---

## Tab 1: खात्याची माहिती (Account Information)

### Member Type and Transaction Header

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | अ वर्ग | Class A | Radio | No | Default selected |
| 2 | नाममात्र सभासद | Nominal Member | Radio | No | — |
| 3 | व्हाऊचर नं | Voucher No. | Textbox | No | Read-only; e.g. `52` |
| 4 | नावे / जमा | Debit / Credit | Radio | Yes | — |
| 5 | रोख / ट्रान्सफर | Cash / Transfer | Radio | Yes | — |

### Account Fields

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 6 | शाखा निवडा | Select Branch | Autocomplete | Yes | Sample: `1 — कोतोली मुख्य कार्यालय` |
| 7 | जी.एल. निवडा | Select GL | Autocomplete | Yes | Sample: `1 — वसूल भाग भांडवल` |
| 8 | खातेधारक निवडा | Select Account Holder | Autocomplete | Yes | Enter resolves by ID or name |
| 9 | लेजर शिल्लक (जमा) | Ledger Balance (Credit) | Textbox | No | Read-only |
| 10 | न कटलेली शिल्लक | Uncleared Balance | Textbox | No | Read-only |
| 11 | व्यवहार रक्कम (रु.) | Transaction Amount (Rs.) | Textbox | Yes | — |
| 12 | अक्षरी रक्कम | Amount in Words | Textbox | No | Read-only |
| 13 | पॅनकार्ड - आधार | PAN - Aadhaar | Textbox | No | Read-only |
| 14 | व्यवहार तपशील | Transaction Details | Textbox | No | — |
| 15 | ठराव दिनांक | Resolution Date | Date | No | — |
| 16 | ठराव क्रमांक | Resolution Number | Textbox | No | — |
| 17 | विशेष सूचना | Special Instructions | Textbox | No | — |

### Withdrawal Mode

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 18 | आंशिक | Partial | Radio | No | — |
| 19 | खाते बंद करा | Close Account | Radio | No | — |

### Certificate Selection Grid

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | सर्टिफिकेट क्रमांक | Certificate Number |
| 3 | रक्कम | Amount |

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 20 | एकूण रक्कम | Total Amount | Textbox | No | Read-only |

**KYC preview:** `फोटो / सही दाखवा` with photo, signature, ID proof, address proof placeholders.

**Navigation:** `पुढे`.

---

## Tab 2: साहित्य तपशील (Instrument Details)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | धनादेश प्रकार निवडा | Select Cheque Type | Dropdown | No | e.g. `स्लिप` (Slip). Other values: `TODO` |
| 2 | चेक रक्कम (रु.) | Cheque Amount (Rs.) | Textbox | No | — |
| 3 | रक्कम अक्षरी | Amount in Words | Textbox | No | — |
| 4 | चेक दिनांक | Cheque Date | Date | Yes | — |
| 5 | चेक क्र. | Cheque No. | Textbox | Yes | — |
| 6 | नाव | Name | Textbox | Yes | — |
| 7 | बँक निवडा | Select Bank | Dropdown | Yes | Default: `निवडा`. Values: `TODO` |
| 8 | बँक शाखा | Bank Branch | Textbox | No | — |
| 9 | ड्रॉन ऑन बँक | Drawn on Bank | Textbox | No | — |
| 10 | ड्रॉन ऑन ब्रांच | Drawn on Branch | Textbox | No | — |

**Navigation:** `मागे`, `पुढे`, `खाते बंद करा`, `पूर्ववत`.

---

## Tab 3: ट्रान्सफर (Transfer)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा निवडा | Select Branch | Autocomplete | Yes | Enter resolves by ID or name |
| 2 | जी.एल. निवडा | Select GL | Autocomplete | Yes | — |
| 3 | खातेधारक निवडा | Select Account Holder | Autocomplete | No | — |
| 4 | शिल्लक | Balance | Textbox | No | Read-only |
| 5 | जमा / नावे | Credit / Debit | Radio | No | — |
| 6 | व्यवहार रक्कम (रु) | Transaction Amount (Rs.) | Textbox | Yes | — |
| 7 | एकूण व्यवहार रक्कम (रु) | Total Transaction Amount | Textbox | No | Read-only |

**Action:** `+ टाका` (Add).

**Grid columns:** निवडा, अनु क्र, जी.एल. हेड, खाते क्र., नाव, शिल्लक, व्यवहार रक्कम (रु).

**Grid actions:** `निर्धारित करा`, `डिलीट`. **Footer:** `व्यवहार रक्कम` summary.

**Navigation:** `मागे`, `पुढे`.

---

## Tab 4: शेअर्स वाटप (Share Allocation)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | इश्यू दिनांक | Issue Date | Date | Yes | — |
| 2 | शेअर्स सिरीज | Share Series | Dropdown | No | Default: `निवडा`. Values: `TODO` |
| 3 | सर्टिफिकेट क्रमांक | Certificate Number | Textbox | Yes | — |
| 4 | ठेव रक्कम (रु) | Deposit Amount (Rs.) | Textbox | Yes | — |
| 5 | प्रति शेअर(रु.) | Per Share (Rs.) | Textbox | Yes | — |
| 6 | एकूण शेअर्स | Total Shares | Textbox | Yes | — |
| 7 | शेअर्स क्रमांक(पासून) | Share Number (From) | Textbox | Yes | — |
| 8 | शेअर्स क्रमांक(पर्यंत) | Share Number (To) | Textbox | Yes | — |

**Action:** `पूर्ण` (Complete).

**Navigation:** `मागे`, `पुढे`.

---

## Tab 5: वारसदाराची माहिती (Nominee Information)

`TODO` — tab referenced in navigation; no dedicated screenshot in `02_07` set. Follow [new-membership-screen.md](new-membership-screen.md) Tab 3 (Nominee) field set.

---

## Tab 6: शेअर्सची माहिती (Share Information)

### Section: इश्यू शेअर्स (Issued Shares)

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | अनु. क्र. | Sr. No. |
| 2 | दिनांक | Date |
| 3 | सर्टिफिकेट क्रमांक | Certificate Number |
| 4 | संख्या | Quantity |
| 5 | पासून-पर्यंत | From-To |
| 6 | रक्कम | Amount |

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | एकूण रक्कम | Total Amount | Textbox | No | Read-only |

### Section: ट्रान्सफर/परत केलेले शेअर्स (Transferred/Returned Shares)

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | अनु. क्र. | Sr. No. |
| 2 | दिनांक | Date |
| 3 | सर्टिफिकेट क्रमांक | Certificate Number |
| 4 | संख्या | Quantity |
| 5 | पासून-पर्यंत | From-To |
| 6 | रक्कम | Amount |
| 7 | प्रकार | Type |
| 8 | ट्रान्स्फर पी | Transfer P |

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 2 | एकूण रक्कम | Total Amount | Textbox | No | Read-only |

### Section: अंशतः शेअर्स काढणे (Partial Share Withdrawal)

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | अनु. क्र. | Sr. No. |
| 2 | खाते क्रमांक | Account Number |
| 3 | नाव | Name |
| 4 | सर्टिफिकेट क्रमांक | Certificate Number |
| 5 | मालिका | Series |
| 6 | रक्कम | Amount |
| 7 | दिनांक | Date |

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 3 | एकूण रक्कम | Total Amount | Textbox | No | Read-only |

**Navigation:** `मागे`, `पुढील`.

---

## Tab 7: के.वाय.सी. माहिती (KYC Information)

`TODO` — tab referenced in navigation; no dedicated screenshot in `02_07` set.

---

## Related Documents

- [overview.md](overview.md)
- [new-membership-screen.md](new-membership-screen.md)
- [member-register-screen.md](member-register-screen.md)
- [shares-transfer-screen.md](shares-transfer-screen.md)
- [../savings/savings-transaction-screen.md](../savings/savings-transaction-screen.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
