# Screen Spec — Agent Collection Management (डेली > एजंट > एजंट कलेक्शन व्यवस्थापन)

> **Consolidates:** [agent-collection-screen.md](agent-collection-screen.md) + [agent-collection-list-screen.md](agent-collection-list-screen.md)

## Purpose

Single screen for recording daily agent collections (wizard: collection grid → brief instrument details → transfer posting) and viewing historical collection records.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | एजंट कलेक्शन व्यवस्थापन | Agent Collection Management |
| Breadcrumb | डॅशबोर्ड > डेली > एजंट > एजंट कलेक्शन व्यवस्थापन | Dashboard > Daily > Agent > Agent Collection Management |
| Parent Module | डेली | Daily |

## Tabs

| # | Marathi Tab | English Tab | Replaces / Notes |
| :---: | :--- | :--- | :--- |
| 1 | एजंट संकलन | Agent Collection | Agent Collection — capture grid |
| 2 | संक्षिप्त तपशील | Brief Details | Post-grid instrument / cheque details (not Agent-to-Agent Transfer) |
| 3 | ट्रान्स्फर | Transfer | Posting transfer lines for the collection |
| 4 | कलेक्शन यादी | Collection List | Agent Collection List |

## Reference Screenshots

| File | Tab |
| :--- | :--- |
| `screenshots/डेली/डॅशबोर्ड_डेली _एजंट_एजंट कलेक्शन.png` | Tab 1 |
| `screenshots/डेली/डॅशबोर्ड-डेली-एजंट-कलेक्शन-संक्षिप्त-तपशील.png` | Tab 2 — bank-provided 2026-07-21 |
| `screenshots/डेली/डॅशबोर्ड-डेली-एजंट-कलेक्शन-ट्रान्स्फर.png` | Tab 3 — bank-provided 2026-07-21 |
| `screenshots/डेली/डॅशबोर्ड_डेली_एजंट_एजंट कलेक्शन यादी.png` | Tab 4 |

---

## Tab 1: एजंट संकलन (Agent Collection)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | चलन क्रमांक | Challan Number | Label (read-only) | No | Auto-generated; e.g. `42` |
| 2 | रोख / ट्रान्सफर | Cash / Transfer | Radio | Yes | — |
| 3 | शाखा निवडा | Select Branch | Autocomplete | No | Default: logged-in branch. Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 4 | एजंट निवडा | Select Agent | Autocomplete | Yes | Replaces `प्रतिनिधी क्र.` + `शोध एजंट नाव`. Sample: `1 — Agent 1`, `2 — Agent 2`. Enter resolves by ID or name; shows display name. See [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |
| 5 | कलेक्शन रक्कम (रु.) | Collection Amount (Rs.) | Textbox | Yes | — |
| 6 | एक दिवसीय / अनेक दिवस | One Day / Multiple Days | Radio | Yes | — |
| 7 | कलेक्शन दिनांक (पासून) | Collection Date (From) | Date | Yes | — |
| 8 | योजना निवडा | Select Scheme | Dropdown | No | Loaded dynamically from Daily schemes (Settings > नवीन योजना). Sample: `डेली १`, `डेली २`, `पिग्मी ठेव` |
| 9 | खाते क्रमांक (पासून) | Account No. (From) | Textbox | No | — |
| 10 | खाते क्रमांक (पर्यंत) | Account No. (To) | Textbox | No | — |
| 11 | मार्क पावती क्रमांक | Mark Receipt Number | Checkbox | No | — |
| 12 | खाते क्रमांक नुसार / लेजर फोलिओ क्रमांक नुसार | By Account No. / By L.F. No. | Radio | No | — |

**Action:** `बघा` (View) — loads collection grid.

### Collection Grid Columns

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | अनु. क्र. | Sr. No. |
| 3 | खात्याचे नाव | Account Name |
| 4 | खाते क्रमांक | Account Number |
| 5 | खातेधारक | Account Holder |
| 6 | शिल्लक | Balance |
| 7–16 | १ ला दिवस … १० वा दिवस | Day 1 … Day 10 |
| 17 | एकूण | Total |
| 18 | एल. एफ. क्रमांक | L.F. Number |
| 19 | आर डी दंड | RD Penalty |
| 20 | आर डी सवलत | RD Discount |
| 21 | एजंट कमिशन | Agent Commission |
| 22 | एजंट कमिशन रेट | Agent Commission Rate |
| 23 | हप्ता संख्या | Installment Count |
| 24 | चालू दिनांक | Current Date |

**Select all:** `सर्व निवडा`.

**Actions:** `निर्मीती करा` (Create), `रक्कम शुन्यवर सेट करा` (Set Amount to Zero).

**Footer summary:** एकूण रक्कम, एकूण एजंट कमिशन, एकूण निवडलेल्या नोंदी.

**Navigation:** `पुढे` → Tab 2 (संक्षिप्त तपशील).

---

## Tab 2: संक्षिप्त तपशील (Brief Details)

Instrument / cheque details for the collection. Same field set as [deposit-account-transaction-screen.md](../accounting/deposit-account-transaction-screen.md) Tab 2 (साहित्य तपशील), with amounts editable on this screen per screenshot.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | धनादेश प्रकार निवडा | Select Cheque Type | Dropdown | No | Default: `स्लिप` (Slip). Values: `स्लिप`, `चेक` (Cheque) — same as deposit transaction Instrument tab |
| 2 | चेक रक्कम (रु.) | Cheque Amount (Rs.) | Textbox | No | May default from Tab 1 collection total |
| 3 | रक्कम अक्षरी | Amount in Words | Textbox | No | May auto-fill from field 2 |
| 4 | चेक दिनांक | Cheque Date | Date | Yes | Default: system date |
| 5 | चेक क्र. | Cheque No. | Textbox | Yes | — |
| 6 | नाव | Name | Textbox | Yes | — |
| 7 | बँक निवडा | Select Bank | Autocomplete | Yes | From Bank Master. Sample: `1 — बँक ऑफ इंडिया`, `2 — स्टेट बँक ऑफ इंडिया`, `3 — बँक ऑफ महाराष्ट्र`, `4 — एचडीएफसी बँक`. See [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |
| 8 | बँक शाखा | Bank Branch | Textbox | No | — |
| 9 | ड्रॉन ऑन बँक | Drawn on Bank | Textbox | No | — |
| 10 | ड्रॉन ऑन ब्रांच | Drawn on Branch | Textbox | No | — |

**Navigation:** `मागे`, `पुढे`. **Footer:** `पूर्ण`, `पूर्वत`.

---

## Tab 3: ट्रान्स्फर (Transfer)

GL / account posting lines for the collection. **Not** the same as [agent-to-agent-transfer-screen.md](agent-to-agent-transfer-screen.md). Pattern aligned with [deposit-account-transaction-screen.md](../accounting/deposit-account-transaction-screen.md) Tab 3, fields from bank screenshot 2026-07-21.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा निवडा | Select Branch | Autocomplete | Yes | Replaces legacy `शाखा कोड` + `शाखा निवडा`. Sample: `1 — कोतोली मुख्य कार्यालय`. Enter resolves by ID or name |
| 2 | जी.एल. निवडा | Select GL | Autocomplete | Yes | Replaces legacy `जी. एल. हेड. क्र.` + `जी एल निवडा`. Sample: `38 — पिग्मी ठेव`. Enter resolves by ID or name |
| 3 | खातेधारक निवडा | Select Account Holder | Autocomplete | Yes | Replaces `खातेधारक शोधा` + `खातेधारक निवडा`. Sample: `101 — लकडे प्रवीण पांडुरंग`. Enter resolves by ID or name |
| 4 | खाते क्र. | Account No. | Textbox | Yes | May auto-fill when account holder resolves |
| 5 | शिल्लक (जमा) | Balance (Credit) | Label (read-only) | No | From resolved account; e.g. `52500` |
| 6 | व्यवहार रक्कम (रु.) | Transaction Amount (Rs.) | Textbox | Yes | — |
| 7 | एकूण व्यवहार रक्कम (रु.) | Total Transaction Amount (Rs.) | Label (read-only) | No | Sum of grid rows / collection total; e.g. `1000` |

**Action:** `+ टाका` (Add) — appends row to transfer grid.

### Transfer Grid

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | अनु.क्र. | Sr. No. |
| 3 | जी. एल. हेड | G.L. Head |
| 4 | खाते क्र. | Account No. |
| 5 | नाव | Name |
| 6 | शिल्लक | Balance |
| 7 | व्यवहार रक्कम (रु.) | Transaction Amount (Rs.) |

**Grid actions:** `अनियमित करा` (Make Irregular), `निटवा` (Clear / Remove selected).

**Footer summary:** `व्यवहार रक्कम` (transaction amount total).

**Navigation:** `मागे`.

---

## Tab 4: कलेक्शन यादी (Collection List)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा निवडा | Select Branch | Autocomplete | Yes | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 2 | एजंट निवडा | Select Agent | Autocomplete | Yes | Replaces `एजंट क्रमांक` + `शोध एजंट नाव`. Sample: `1 — Agent 1`. Enter resolves by ID or name |
| 3 | योजना निवडा | Select Scheme | Dropdown | No | Loaded dynamically from Daily schemes (Settings > नवीन योजना). Sample: `डेली १`, `डेली २`, `पिग्मी ठेव` |
| 4 | व्यवहार दिनांक पासून | Transaction Date From | Date | No | — |
| 5 | व्यवहार दिनांक पर्यंत | Transaction Date To | Date | No | — |

**Action:** `दाखवा` (Show).

### Results Grid

**Select all:** `सर्व निवडा`.

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | अनु. क्र. | Sr. No. |
| 3 | एजंटचे नाव | Agent Name |
| 4 | व्यवहार दिनांक | Transaction Date |
| 5 | कलेक्शन रक्कम | Collection Amount |

**Sidebar actions:** `तपशील` (Details), `निर्यात करा` (Export).

**Footer:** एकूण (total collection amount).

---

## Mockup

- [HTML mockup (Draft)](../mockups/daily/agent-collection-management-screen/) — Marathi layout for bank review

---

## Cross-Links

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [new-agent-screen.md](new-agent-screen.md)
- [agent-to-agent-transfer-screen.md](agent-to-agent-transfer-screen.md)
- [../accounting/deposit-account-transaction-screen.md](../accounting/deposit-account-transaction-screen.md) — shared instrument / transfer field patterns
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
