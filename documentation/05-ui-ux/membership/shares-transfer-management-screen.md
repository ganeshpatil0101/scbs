# Screen Spec — Shares Transfer Management (सभासदत्व > शेअर्स ट्रान्सफर व्यवस्थापन)

> **Consolidates:** [shares-transfer-screen.md](shares-transfer-screen.md) + [shares-transfer-list-screen.md](shares-transfer-list-screen.md)

## Purpose

Single screen for transferring share certificates between members and reviewing completed transfer records. Tab 1 runs the three-step transfer wizard (transfer details, instrument, GL transfer for fee); Tab 2 lists historical transfers.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | शेअर्स ट्रान्सफर व्यवस्थापन | Shares Transfer Management |
| Breadcrumb | डॅशबोर्ड > सभासदत्व > शेअर्स ट्रान्सफर व्यवस्थापन | Dashboard > Membership > Shares Transfer Management |
| Parent Module | सभासदत्व | Membership |

## Tabs

| # | Marathi Tab | English Tab | Replaces |
| :---: | :--- | :--- | :--- |
| 1 | नवीन ट्रान्सफर | New Transfer | Shares Transfer |
| 2 | ट्रान्सफर यादी | Transfer List | Shares Transfer List |

## Reference Media

| File | Tab |
| :--- | :--- |
| `screenshots/sabhsadatv/डॅशबोर्ड-सभासदत्व-शेअर्स ट्रान्सफर.mp4` | Tab 1 — all inner tabs |
| `screenshots/sabhsadatv/डॅशबोर्ड-सभासदत्व-शेअर्स ट्रान्सफर-1-02_07.png` | Tab 1 — inner Tab 1 |
| `screenshots/sabhsadatv/डॅशबोर्ड-सभासदत्व-शेअर्स ट्रान्सफर-2-02_07.png` | Tab 1 — inner Tab 2 |
| `screenshots/sabhsadatv/डॅशबोर्ड-सभासदत्व-शेअर्स ट्रान्सफर-3-02_07.png` | Tab 1 — inner Tab 3 |
| `screenshots/sabhsadatv/डॅशबोर्ड-सभासदत्व-शेअर्स ट्रान्सफर यादी-1-02_07.png` | Tab 2 |

Extracted frames: `screenshots/sabhsadatv/shares-transfer-frames/`.

---

## Tab 1: नवीन ट्रान्सफर (New Transfer)

Three inner tabs: शेअर्स ट्रान्सफर → साहित्य तपशील → ट्रान्सफर. Inner Tab 2 and 3 visible when transfer fee payment mode = `ट्रान्सफर` (Transfer).

### Inner Tab 1: शेअर्स ट्रान्सफर (Shares Transfer)

#### Share Class

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | अ वर्ग | Class A | Radio | No | Default selected |
| 2 | ब वर्ग | Class B | Radio | No | — |

#### Transfer Details

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 3 | अर्ज दिनांक | Application Date | Date | Yes | — |
| 4 | ठराव क्र. | Resolution No. | Textbox | Yes | — |
| 5 | ठराव दिनांक | Resolution Date | Date | Yes | — |
| 6 | ट्रान्सफर दिनांक | Transfer Date | Date | Yes | — |
| 7 | सभासद निवडा (पासून) | Select Member (From) | Autocomplete | Yes | Enter resolves by member no. or name; e.g. `208 — Member 1`. Replaces Member No. + Name (From). See [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |
| 8 | सभासद निवडा (पर्यंत) | Select Member (To) | Autocomplete | Yes | Enter resolves by member no. or name; e.g. `209 — Member 2`. Replaces Member No. + Name (To) |
| 9 | शेरा | Remark | Textbox | No | — |
| 10 | प्रमाणपत्र क्र (पासुन) | Certificate No. (From) | Textbox | No | — |
| 11 | प्रमाणपत्र क्र (पर्यंत) | Certificate No. (To) | Textbox | No | — |

**Action:** `दाखले दाखवा` (Show Certificates).

#### Certificate Grid (`app-certificate-selection-grid`)

Columns: निवडा, अ.क्र., सर्टिफिकेट क्र., शेअर्स क्र., रक्कम.

**Select all:** `सर्व निवडा`.

#### Transfer Fee Section

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 12 | एकूण शेअर रक्कम | Total Share Amount | Label | No | Read-only; from grid |
| 13 | रोख / ट्रान्सफर | Cash / Transfer | Radio | No | Payment mode for fee |
| 14 | ट्रान्सफर फी (रू.) | Transfer Fee (Rs.) | Textbox | No | — |

**Removed (2026-07-22):** `स्क्रोल निवडा` (Select Scroll) — not required.

**Navigation:** `पुढे`. **Footer:** `पूर्ण`, `पूर्ववत`.

---

### Inner Tab 2: साहित्य तपशील (Instrument Details)

> **Shared component:** `app-cheque-tab`. Visible when fee payment mode = `ट्रान्सफर`.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | धनादेश प्रकार निवडा | Select Cheque Type | Dropdown | No | `स्लिप` (Slip), `चेक` (Cheque) |
| 2 | चेक रक्कम (रु.) | Cheque Amount (Rs.) | Textbox | No | — |
| 3 | रक्कम अक्षरी | Amount in Words | Textbox | No | — |
| 4 | चेक दिनांक | Cheque Date | Date | Yes | — |
| 5 | चेक क्र. | Cheque No. | Textbox | Yes | — |
| 6 | नाव | Name | Textbox | Yes | — |
| 7 | बँक निवडा | Select Bank | Autocomplete | Yes | From Bank Master. Sample: `1 — बँक ऑफ इंडिया`, `2 — स्टेट बँक ऑफ इंडिया`, `3 — बँक ऑफ महाराष्ट्र`, `4 — एचडीएफसी बँक`. Enter resolves by ID or name; resolved 2026-07-22 — see [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |
| 8 | बँक शाखा | Bank Branch | Textbox | No | — |
| 9 | ड्रॉन ऑन बँक | Drawn on Bank | Label | No | Read-only; derived from bank |
| 10 | ड्रॉन ऑन ब्रांच | Drawn on Branch | Label | No | Read-only; derived from bank |

**Navigation:** `मागे`, `पुढे`, `पूर्ण`, `पूर्ववत`.

---

### Inner Tab 3: ट्रान्सफर (Transfer)

> **Shared component:** `app-transfer-tab`. Visible when fee payment mode = `ट्रान्सफर`.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा निवडा | Select Branch | Autocomplete | Yes | e.g. `1 — कोतोली मुख्य कार्यालय` |
| 2 | जी.एल. निवडा | Select GL | Autocomplete | Yes | e.g. `1 — वसूल भाग भांडवल` |
| 3 | खातेधारक निवडा | Select Account Holder | Autocomplete | Yes | Enter resolves by ID or name |
| 4 | शिल्लक(जमा) | Balance (Credit) | Label | No | Read-only |
| 5 | जमा / नावे | Credit / Debit | Radio | No | — |
| 6 | व्यवहार रक्कम (रु) | Transaction Amount (Rs.) | Textbox | Yes | — |
| 7 | एकूण व्यवहार रक्कम (रु) | Total Transaction Amount | Label | No | Read-only |

**Action:** `+ टाका` (Add).

**Grid columns:** निवडा, अनु क्र, जी.एल.हेड, खाते क्र., नाव, शिल्लक, व्यवहार रक्कम (रु).

**Grid actions:** `निश्चित करा`, `हटवा`. **Footer:** `व्यवहार रक्कम` summary, `पूर्ण`, `पूर्ववत`.

---

## Tab 2: ट्रान्सफर यादी (Transfer List)

Search and list completed share transfer records.

### Section: Share Class

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | अ वर्ग | Class A | Radio | No | — |
| 2 | ब वर्ग | Class B | Radio | No | — |

### Section: Range Filters

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 3 | सभासद क्र. (पासून) | Member No. (From) | Textbox | No | Range filter — excluded from Autocomplete per entity-autocomplete-pattern |
| 4 | सभासद क्र. (पर्यंत) | Member No. (To) | Textbox | No | Range filter |
| 5 | प्रमाणपत्र क्र. (पासून) | Certificate No. (From) | Textbox | No | — |
| 6 | प्रमाणपत्र क्र. (पर्यंत) | Certificate No. (To) | Textbox | No | — |
| 7 | ट्रान्सफर दिनांक (पासून) | Transfer Date (From) | Date | No | — |
| 8 | ट्रान्सफर दिनांक (पर्यंत) | Transfer Date (To) | Date | No | — |

**Action:** `दाखवा` (Show).

### Results Grid

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | अ.क्र. | Sr. No. |
| 3 | ट्रान्सफर दिनांक | Transfer Date |
| 4 | ट्रान्सफर सभासद 'पासून' | Transfer Member 'From' |
| 5 | सभासद क्र. 'पासून' | Member No. 'From' |
| 6 | एकूण शेअर्स | Total Shares |
| 7 | सर्टिफिकेट क्र. | Certificate No. |
| 8 | शेअर्स रक्कम रू. | Share Amount Rs. |
| 9 | ट्रान्सफर सभासद 'पर्यंत' | Transfer Member 'To' |
| 10 | सभासद क्र. 'पर्यंत' | Member No. 'To' |
| 11 | ठराव क्र. | Resolution No. |
| 12 | ठराव दिनांक | Resolution Date |
| 13 | ट्रान्सफर फी रू. | Transfer Fee Rs. |
| 14 | शेरा | Remarks |

**Footer:** `एकूण नोंदी`, pagination (`पुढील >>`).

**Sidebar actions:** `निर्यात`, `काढा`.

**Footer action:** `पूर्ववत`.

---

## Mockup

| Property | Value |
| :--- | :--- |
| Path | [mockups/membership/shares-transfer-management-screen/](../mockups/membership/shares-transfer-management-screen/) |
| Status | **Draft** |
| Created | 2026-07-12 |

Open `index.html` in a browser for layout review before Angular implementation.

---

## Related Documents

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [new-membership-screen.md](new-membership-screen.md)
- [member-register-screen.md](member-register-screen.md)
- [../settings/membership/membership-configuration-screen.md](../settings/membership/membership-configuration-screen.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
- [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md)
