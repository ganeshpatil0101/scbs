# Screen Spec — Shares Transfer (सभासदत्व > शेअर्स ट्रान्सफर)

## Purpose

UI specification for transferring share certificates between members. Three-tab workflow.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | शेअर्स ट्रान्सफर | Shares Transfer |
| Breadcrumb | डॅशबोर्ड > सभासदत्व > शेअर्स ट्रान्सफर | Dashboard > Membership > Shares Transfer |
| Parent Module | सभासदत्व | Membership |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | शेअर्स ट्रान्सफर | Shares Transfer |
| 2 | साहित्य तपशील | Instrument Details |
| 3 | ट्रान्सफर | Transfer |

## Reference Media

| File | Tab |
| :--- | :--- |
| `screenshots/sabhsadatv/डॅशबोर्ड-सभासदत्व-शेअर्स ट्रान्सफर.mp4` | All tabs |

Extracted frames: `screenshots/sabhsadatv/shares-transfer-frames/`.

---

## Tab 1: शेअर्स ट्रान्सफर (Shares Transfer)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | अ वर्ग | Class A | Radio | No | Default selected |
| 2 | ब वर्ग | Class B | Radio | No | — |
| 3 | अर्ज दिनांक | Application Date | Date | Yes | — |
| 4 | ठराव क्र. | Resolution No. | Textbox | Yes | — |
| 5 | ठराव दिनांक | Resolution Date | Date | Yes | — |
| 6 | ट्रान्सफर दिनांक | Transfer Date | Date | Yes | — |
| 7 | सभासद क्र. (पासुन) | Member No. (From) | Textbox | Yes | — |
| 8 | सभासद नाव (पासुन) | Member Name (From) | Textbox | Yes | — |
| 9 | सभासद क्र. (पर्यंत) | Member No. (To) | Textbox | Yes | — |
| 10 | सभासद नाव (पर्यंत) | Member Name (To) | Textbox | Yes | — |
| 11 | शेरा | Remark | Textbox | No | — |
| 12 | प्रमाणपत्र क्र (पासुन) | Certificate No. (From) | Textbox | No | — |
| 13 | प्रमाणपत्र क्र (पर्यंत) | Certificate No. (To) | Textbox | No | — |

**Action:** `दाखले दाखवा` (Show Certificates).

### Certificate Grid

Columns: निवडा, अ.क्र., सर्टिफिकेट क्र., शेअर्स क्र., रक्कम.

**Select all:** `सर्व निवडा`.

### Transfer Fee Section (bottom of Tab 1)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 14 | एकूण शेअर रक्कम | Total Share Amount | Textbox | No | Read-only |
| 15 | रोख / ट्रान्सफर | Cash / Transfer | Radio | No | Payment mode for fee |
| 16 | स्क्रोल निवडा | Select Scroll | Dropdown | Yes | Default: `निवडा`. Values: `TODO` |
| 17 | ट्रान्सफर फी (रू.) | Transfer Fee (Rs.) | Textbox | No | — |

**Navigation:** `पुढे`. **Footer:** `पूर्ण`, `पूर्ववत`.

---

## Tab 2: साहित्य तपशील (Instrument Details)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | धनादेश प्रकार निवडा | Select Cheque Type | Dropdown | No | e.g. `स्लिप` |
| 2 | चेक रक्कम (रु.) | Cheque Amount (Rs.) | Textbox | No | — |
| 3 | रक्कम अक्षरी | Amount in Words | Textbox | No | — |
| 4 | चेक दिनांक | Cheque Date | Date | Yes | — |
| 5 | चेक क्र. | Cheque No. | Textbox | Yes | — |
| 6 | नाव | Name | Textbox | Yes | — |
| 7 | बँक निवडा | Select Bank | Dropdown | Yes | `TODO` |
| 8 | बँक शाखा | Bank Branch | Textbox | No | — |
| 9 | ड्रॉन ऑन बँक | Drawn on Bank | Textbox | No | — |
| 10 | ड्रॉन ऑन ब्रांच | Drawn on Branch | Textbox | No | — |

**Navigation:** `मागे`, `पुढे`, `पूर्ण`, `पूर्ववत`.

---

## Tab 3: ट्रान्सफर (Transfer)

`TODO` — transfer entry grid not captured in video frames; follow savings/accounting transfer pattern.

---

## Related Documents

- [overview.md](overview.md)
- [new-membership-screen.md](new-membership-screen.md)
- [../settings/membership/share-rules-screen.md](../settings/membership/share-rules-screen.md)
