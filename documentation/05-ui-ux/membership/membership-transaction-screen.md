# Screen Spec — Membership Transaction (सभासदत्व > सभासदत्व व्यवहार)

## Purpose

UI specification for share capital transactions (credit/debit, cash/transfer) including partial withdrawal and share allocation. Seven-tab workflow with mode-conditional visibility.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | सभासदत्व व्यवहार | Membership Transaction |
| Breadcrumb | डॅशबोर्ड > सभासदत्व > सभासदत्व व्यवहार | Dashboard > Membership > Membership Transaction |
| Parent Module | सभासदत्व | Membership |

## Tabs

| # | Marathi Tab | English Tab | Visibility |
| :---: | :--- | :--- | :--- |
| 1 | खात्याची माहिती | Account Information | Both |
| 2 | साहित्य तपशील | Instrument Details | **Transfer mode only** |
| 3 | ट्रान्सफर | Transfer | **Transfer mode only** |
| 4 | शेअर्स वाटप | Share Allocation | **Credit only** |
| 5 | वारसदाराची माहिती | Nominee Information | Both (scaffold) |
| 6 | शेअर्सची माहिती | Share Information | Both |
| 7 | के.वाय.सी. माहिती | KYC Information | Both (scaffold) |

**Mode selectors (Tab 1):** Radio `नावे / जमा` (Debit / Credit) and `रोख / ट्रान्सफर` (Cash / Transfer) — required. Matches [../loan/loan-transaction-screen.md](../loan/loan-transaction-screen.md) pattern.

**Tab order by mode:**

| Mode | Tab sequence after Tab 1 |
| :--- | :--- |
| Credit + Cash | 4 शेअर्स वाटप → 5 वारसदार → 6 शेअर्स → 7 KYC |
| Credit + Transfer | 2 साहित्य → 3 ट्रान्सफर → 4 शेअर्स वाटप → 5 → 6 → 7 |
| Debit + Cash | 5 → 6 → 7 (withdrawal grid on Tab 1) |
| Debit + Transfer | 2 साहित्य → 3 ट्रान्सफर → 5 → 6 → 7 |

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
| 1 | अ वर्ग | Class A | Radio | No | Default selected. Note: `सभासद` label used on other membership screens — may be different enum |
| 2 | नाममात्र सभासद | Nominal Member | Radio | No | — |
| 3 | व्हाऊचर नं | Voucher No. | Label | No | Read-only; e.g. `52` |
| 4 | नावे / जमा | Debit / Credit | Radio | Yes | — |
| 5 | रोख / ट्रान्सफर | Cash / Transfer | Radio | Yes | Controls Tab 2 and Tab 3 visibility |

### Account Fields

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 6 | शाखा निवडा | Select Branch | Autocomplete | Yes | e.g. `1 — कोतोली मुख्य कार्यालय` |
| 7 | जी.एल. निवडा | Select GL | Autocomplete | Yes | e.g. `1 — वसूल भाग भांडवल` |
| 8 | खातेधारक निवडा | Select Account Holder | Autocomplete | Yes | Enter resolves by ID or name |
| 9 | लेजर शिल्लक (जमा) | Ledger Balance (Credit) | Label | No | Read-only |
| 10 | न कटलेली शिल्लक | Uncleared Balance | Label | No | Read-only |
| 11 | व्यवहार रक्कम (रु.) | Transaction Amount (Rs.) | Textbox | Yes | — |
| 12 | अक्षरी रक्कम | Amount in Words | Label | No | Read-only |
| 13 | पॅनकार्ड - आधार | PAN - Aadhaar | Label | No | Read-only |
| 14 | व्यवहार तपशील | Transaction Details | Textbox | No | — |

### Debit-only: Withdrawal Mode (visible when mode = Debit)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 15 | आंशिक | Partial | Radio | No | — |
| 16 | खाते बंद करा | Close Account | Radio | No | — |

### Debit-only: Certificate Selection Grid (`app-certificate-selection-grid`)

Visible when mode = Debit.

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | सर्टिफिकेट क्रमांक | Certificate Number |
| 3 | रक्कम | Amount |

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 17 | एकूण रक्कम | Total Amount | Label | No | Read-only |

### Section: प्रगत सेटिंग्ज (Advanced Settings)

> Collapsed by default. Visible to users with accounting/admin role or when expanded manually.

| # | Marathi Label | English Label | Type | Required | Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 18 | ठराव दिनांक | Resolution Date | Date | No | Rare on every transaction |
| 19 | ठराव क्रमांक | Resolution Number | Textbox | No | — |
| 20 | विशेष सूचना | Special Instructions | Textbox | No | — |

**KYC preview:** `फोटो / सही दाखवा` with photo, signature, ID proof, address proof placeholders.

**Navigation:** `पुढे`.

---

## Tab 2: साहित्य तपशील (Instrument Details)

> **Shared component:** `app-cheque-tab`. Visible when Tab 1 mode = `ट्रान्सफर`.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | धनादेश प्रकार निवडा | Select Cheque Type | Dropdown | No | `स्लिप` (Slip), `चेक` (Cheque) |
| 2 | चेक रक्कम (रु.) | Cheque Amount (Rs.) | Textbox | No | — |
| 3 | रक्कम अक्षरी | Amount in Words | Textbox | No | — |
| 4 | चेक दिनांक | Cheque Date | Date | Yes | — |
| 5 | चेक क्र. | Cheque No. | Textbox | Yes | — |
| 6 | नाव | Name | Textbox | Yes | — |
| 7 | बँक निवडा | Select Bank | Dropdown | Yes | Default: `निवडा`. Values: `TODO` |
| 8 | बँक शाखा | Bank Branch | Textbox | No | — |
| 9 | ड्रॉन ऑन बँक | Drawn on Bank | Label | No | Read-only; derived from bank |
| 10 | ड्रॉन ऑन ब्रांच | Drawn on Branch | Label | No | Read-only; derived from bank |

**Navigation:** `मागे`, `पुढे`, `खाते बंद करा`, `पूर्ववत`.

---

## Tab 3: ट्रान्सफर (Transfer)

> **Shared component:** `app-transfer-tab`. Visible when Tab 1 mode = `ट्रान्सफर`.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा निवडा | Select Branch | Autocomplete | Yes | Enter resolves by ID or name |
| 2 | जी.एल. निवडा | Select GL | Autocomplete | Yes | — |
| 3 | खातेधारक निवडा | Select Account Holder | Autocomplete | No | — |
| 4 | शिल्लक | Balance | Label | No | Read-only |
| 5 | जमा / नावे | Credit / Debit | Radio | No | — |
| 6 | व्यवहार रक्कम (रु) | Transaction Amount (Rs.) | Textbox | Yes | — |
| 7 | एकूण व्यवहार रक्कम (रु) | Total Transaction Amount | Label | No | Read-only |

**Action:** `+ टाका` (Add).

**Grid columns:** निवडा, अनु क्र, जी.एल. हेड, खाते क्र., नाव, शिल्लक, व्यवहार रक्कम (रु).

**Grid actions:** `निर्धारित करा`, `डिलीट`. **Footer:** `व्यवहार रक्कम` summary.

**Navigation:** `मागे`, `पुढे`.

---

## Tab 4: शेअर्स वाटप (Share Allocation)

Visible when Tab 1 mode = `जमा` (Credit).

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

> **Shared component:** `app-nominee-form`. `TODO` — tab referenced in navigation; no dedicated screenshot in `02_07` set. Field set follows [new-membership-screen.md](new-membership-screen.md) Tab 3 (Nominee). Do not invent fields beyond that spec.

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
| 1 | एकूण रक्कम | Total Amount | Label | No | Read-only |

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
| 2 | एकूण रक्कम | Total Amount | Label | No | Read-only |

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
| 3 | एकूण रक्कम | Total Amount | Label | No | Read-only |

**Navigation:** `मागे`, `पुढील`.

---

## Tab 7: के.वाय.सी. माहिती (KYC Information)

> **Shared component:** `app-kyc-info-tab`. `TODO` — tab referenced in navigation; no dedicated screenshot in `02_07` set. Follow [../savings/savings-transaction-screen.md](../savings/savings-transaction-screen.md) KYC tab pattern.

---

## Mockup

| Property | Value |
| :--- | :--- |
| Path | [mockups/membership/membership-transaction-screen/](../mockups/membership/membership-transaction-screen/) |
| Status | **Draft** (2026-07-12) |

---

## Related Documents

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [new-membership-screen.md](new-membership-screen.md)
- [member-register-screen.md](member-register-screen.md)
- [shares-transfer-management-screen.md](shares-transfer-management-screen.md)
- [../savings/savings-transaction-screen.md](../savings/savings-transaction-screen.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
- [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md)
