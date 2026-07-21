# Screen Spec — New Daily Account (डेली > नवीन खाते)

## Purpose

UI specification for opening a new daily (pigmy) deposit account. Three-tab wizard (Tabs 2 and 3 optional — hidden unless enabled on Tab 1).

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | नवीन खाते | New Account |
| Breadcrumb | डॅशबोर्ड > डेली > नवीन खाते | Dashboard > Daily > New Account |
| Parent Module | डेली | Daily |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | खात्याची माहिती | Account Information |
| 2 | वारसदार | Nominee |
| 3 | परिपक्वता / संयुक्त एसी धारक | Maturity / Joint AC Holder |

## Reference Screenshots / Media

| File | Tab |
| :--- | :--- |
| `screenshots/डेली/डॅशबोर्ड_डेली _नवीन खाते.mp4` | All tabs (from video) |
| `screenshots/डेली/new-account-frames/frame_0000.jpg` | Tab 1 |
| `screenshots/डेली/new-account-frames/frame_0040.jpg` | Tab 2 — Nominee |
| `screenshots/डेली/डॅशबोर्ड-डेली-नवीन खाते-संयुक्त.png` | Tab 3 — Joint AC Holder (shared pattern across deposit products) |
| `screenshots/डेली/डॅशबोर्ड-डेली-नवीन खाते-खाते-चालविण्याची-सूचना.png` | Tab 3 — Account Operation Instructions dropdown |

---

## Tab 1: खात्याची माहिती (Account Information)

### ग्राहक माहिती (Customer Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | ग्राहक निवडा | Select Customer | Autocomplete | Yes | Replaces `ग्राहक क्र.` + `ग्राहक नाव`. Enter resolves by customer no. or name; e.g. `661 — Customer 1`. See [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |

**Customer summary (read-only Labels after resolve):** सभासद क्रमांक, वय (वर्षे), सभासद शाखा नाव, सभासद प्रकार, विशेष सूचना.

### खात्याची माहिती (Account / Agent)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 2 | योजना निवडा | Select Scheme | Dropdown | Yes | Loaded dynamically from Daily schemes (Settings > नवीन योजना). Sample: `डेली १`, `डेली २`, `पिग्मी ठेव` |
| 3 | एजंट शाखा निवडा | Select Agent Branch | Autocomplete | Yes | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 4 | एजंट निवडा | Select Agent | Autocomplete | Yes | Replaces `एजंट क्रमांक` + `शोध एजंट नाव`. Sample: `1 — Agent 1`. Enter resolves by ID or name |
| 5 | खाते क्र. | Account No. | Label (read-only) | No | Auto-generated on save |

### खाते तपशील (Account Details)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 6 | कालावधी निवडा | Select Duration | Dropdown | Yes | Loaded from selected scheme's duration grid (Settings > नवीन योजना > कालावधी tab) |
| 7 | कालावधी (महिने) | Duration (Months) | Label (read-only) | Yes | Auto-filled from selected duration |
| 8 | कालावधी (दिवस) | Duration (Days) | Label (read-only) | Yes | Auto-filled from selected duration |
| 9 | व्याज दर (% पीए) | Interest Rate (% p.a.) | Label (read-only) | Yes | Auto-filled from selected duration |
| 10 | कमिशन दर | Commission Rate | Textbox | Yes | — |
| 11 | चालू दिनांक | Current Date | Label (read-only) | Yes | System date |
| 12 | मुदतपूर्ती दिनांक | Maturity Date | Date | No | — |
| 13 | दैनिक ठेव रक्कम | Daily Deposit Amount | Textbox | Yes | — |
| 14 | मुदतपूर्ती रक्कम | Maturity Amount | Textbox | No | — |
| 15 | विशेष सूचना | Special Instructions | Textbox | No | — |
| 16 | स्थिती निवडा | Select Status | Dropdown | No | Default: `चालू` (Active). Values: `चालू`, `बंद` (Closed), `स्थगित` (Suspended) |
| 17 | कर्जासाठी पिग्मी खाते | Pigmy Account for Loan | Checkbox | No | — |

### Section: प्रगत सेटिंग्ज (Advanced Settings)

> Collapsed by default. Visible to users with accounting/admin role or when expanded manually.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 18 | विक्री एजंट शाखा निवडा | Select Sales Agent Branch | Autocomplete | No | Sample: `1 — Branch 1`. Enter resolves by ID or name |
| 19 | विक्री एजंट निवडा | Select Sales Agent | Autocomplete | No | Replaces `विक्री एजंट क्रमांक` + `विक्री एजंटचे नाव शोधा`. Sample: `1 — Agent 1` |
| 20 | व्याज प्रकार | Interest Type | Dropdown | No | Default from scheme. `सरळ व्याज` (Simple Interest), `चक्रवाढ व्याज` (Compound Interest) |
| 21 | परिणामगणन | Compounding | Dropdown | No | Default from scheme. `दैनिक`, `पाक्षिक`, `मासिक`, `तिमाही`, `सहामाही`, `वार्षिक` |
| 22 | कलेक्शन रक्कम मर्यादा | Collection Amount Limit | Textbox | No | — |
| 23 | नावे मर्यादा | Debit Limit | Textbox | No | — |
| 24 | किमान शिल्लक | Minimum Balance | Textbox | No | — |
| 25 | आयएफएससी कोड | IFSC Code | Textbox | No | — |
| 26 | बँक नाव | Bank Name | Textbox | No | — |
| 27 | बँक बचत खाते नं | Bank Savings Account No. | Textbox | No | — |

### Section: वारसदार पर्याय (Nominee Option)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 28 | वारसदार जोडा | Add Nominee | Checkbox | No | Unchecked by default. When checked, Tab 2 (Nominee) becomes visible in the tab bar; when unchecked, Tab 2 is hidden and skipped during Next/Back navigation. |

### Section: संयुक्त खातेदार पर्याय (Joint Holder Option)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 29 | संयुक्त खातेदार जोडा | Add Joint Holder | Checkbox | No | Unchecked by default. When checked, Tab 3 (Joint AC Holder) becomes visible in the tab bar; when unchecked, Tab 3 is hidden and skipped during Next/Back navigation. |

**Action:** `पुढे` (Next).

---

## Tab 2: वारसदार (Nominee)

> Hidden by default — shown only when field 28 (Tab 1) is checked.

> **Shared component:** Uses `app-nominee-form` + `app-nominee-grid`. Nominee is a **Customer** from master — search or quick-add; no duplicate contact/address entry on this tab. See [quick-add-customer-pattern.md](../shared/quick-add-customer-pattern.md).

### Section: वारसदार शोधा (Search Nominee)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | ग्राहक निवडा | Select Customer | Autocomplete | Yes | Nominee lookup. Enter resolves by customer no. or name; e.g. `662 — Customer 2`. Includes **+ नवीन ग्राहक जोडा** per [quick-add-customer-pattern.md](../shared/quick-add-customer-pattern.md). See [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |

### Section: वारसदार तपशील (Nominee Details)

> Visible only after a nominee customer is resolved in field 1.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 2 | नाते | Relation | Dropdown | Yes | Same as [Membership nominee relation](../membership/new-membership-screen.md): `मुलगा`, `पुतण्या`, `मुली`, `मुलगा - पती`, `पति व मुलगा`, `वरील प्रमाणे`, `बायको`, `मैत्रीण`, `केअरटेकर`, `लहान भाऊ`, `स्वतः`, `पत्नी`, `पती` |
| 3 | टक्केवारी | Percentage | Textbox | No | e.g. `100` |
| 4 | नामांकन दिनांक | Nomination Date | Label (read-only) | No | System date |
| 5 | नामांकन करताना वय | Age at Nomination | Label (read-only) | No | Auto-calculated from resolved customer's date of birth |

**Actions:** `टाका` (Add), `निवड करा`, `काढा`.

### Nominee Grid (`app-nominee-grid`)

Columns: निवडा, अनु. क्र., ग्राहक क्रमांक, ग्राहकाचे नाव, नाते, टक्केवारी, नामांकन करताना वय, नामांकन दिनांक.

**Footer:** `पूर्ण`, `पूर्ववत`.

---

## Tab 3: परिपक्वता / संयुक्त एसी धारक (Maturity / Joint AC Holder)

> Hidden by default — shown only when field 29 (Tab 1) is checked.

> **Maturity:** Duration and maturity fields (`कालावधी`, `मुदतपूर्ती दिनांक`, `मुदतपूर्ती रक्कम`) are on **Tab 1 — खाते तपशील**. This tab is for joint holder + operating instructions only (legacy tab title retained).

> **Shared component:** Joint-holder sections adapted from [New Membership Tab 2](../membership/new-membership-screen.md#tab-2-परिचयकर्ता--संयुक्त-खातेदार-introducer--joint-holder); Introducer section omitted for deposit products per bank review. Uses `app-joint-holder-grid`. See [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md).

### Section: संयुक्त खातेदार (Joint Holder)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | पालक | Guardian | Checkbox | No | — |
| 2 | ग्राहक निवडा | Select Customer | Autocomplete | No | Enter resolves by customer no. or name. Replaces Customer Number + Customer Name input row |

**Action:** `+ जोड` (Add) — validates customer is selected before appending row to grid.

### Joint Holder Grid (`app-joint-holder-grid`)

Columns: निवडा, अ.क्र., ग्राहक क्रमांक, ग्राहकाचे नाव, पालक.

**Grid actions:** `निर्यात` (Export), `काढा` (Remove).

### Section: खाते चालविण्याची सूचना (Account Operation Instructions)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 3 | खाते चालविण्याची सूचना | Account Operation Instructions | Dropdown | Yes | Default: `स्वतः` (Self). `फक्त प्रमुख खातेदार` (Only Primary Holder), `फक्त संयुक्त खातेदार` (Only Joint Holder), `दोन्ही खातेदार आवश्यक` (Both Holders Required), `दोघांपैकी कोणीही` (Either Holder), `स्वतः` (Self) |

**Navigation:** `मागे` (Back). **Footer:** `जतन करा` (Save), `रीसेट` (Reset).

---

## Mockup

- [HTML mockup (Draft)](../mockups/daily/new-daily-account-screen/) — Marathi layout for bank review

---

## Cross-Links

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [../settings/schemes/new-scheme-screen.md](../settings/schemes/new-scheme-screen.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
- [../shared/quick-add-customer-pattern.md](../shared/quick-add-customer-pattern.md)
