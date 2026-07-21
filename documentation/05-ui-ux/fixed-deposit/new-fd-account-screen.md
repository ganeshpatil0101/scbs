# Screen Spec — New FD Account (मुदत ठेव > नवीन खाते)

## Purpose

UI specification for opening a new fixed deposit account. Four-tab wizard (Tabs 2 and 3 optional — hidden unless enabled on Tab 1).

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | नवीन खाते | New Account |
| Breadcrumb | डॅशबोर्ड > मुदत ठेव > नवीन खाते | Dashboard > Fixed Deposit > New Account |
| Parent Module | मुदत ठेव | Fixed Deposit |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | खात्याची माहिती | Account Information |
| 2 | वारसदार | Nominee |
| 3 | संयुक्त खाते धारक | Joint Holder |
| 4 | इतर | Other |

## Reference Screenshots

| File | Tab |
| :--- | :--- |
| `screenshots/मुदत ठेव/डॅशबोर्ड-मुदत ठेव-नवीन खाते.png` | Tab 1 — full form |
| `screenshots/मुदत ठेव/डॅशबोर्ड-मुदत ठेव-नवीन खाते-1.png` | Tab 1 — Scheme dropdown open |
| `screenshots/मुदत ठेव/डॅशबोर्ड-मुदत ठेव-नवीन खाते-2.png` | Tab 2 — Nominee |
| `screenshots/मुदत ठेव/डॅशबोर्ड-मुदत ठेव-नवीन खाते-परिचयकर्ता.png` | Tab 3 — Joint Holder (shared pattern across deposit products) |
| `screenshots/मुदत ठेव/डॅशबोर्ड-मुदत ठेव-नवीन खाते-खाते-चालविण्याची-सूचना.png` | Tab 3 — Account Operation Instructions dropdown |
| User screenshot (Tab 4 — इतर) | Tab 4 — Other |

---

## Tab 1: खात्याची माहिती (Account Information)

### Section: खाते धारकाची माहिती (Account Holder Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | ग्राहक निवडा | Select Customer | Autocomplete | Yes | Replaces `ग्राहक क्र.` + `ग्राहक नाव`. Enter resolves by customer no. or name; e.g. `661 — Customer 1`. See [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |

**Customer summary (read-only Labels after resolve):** सभासद प्रकार, सभासद खाते क्र., वय (व्यवहार दिनांक पर्यंतचे वर्ष), ग्राहक शाखा, पॅन क्र., विशेष सूचना.

### Section: खात्याची माहिती (Account Details)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 2 | योजना निवडा | Select Scheme | Dropdown | Yes | Loaded dynamically from FD schemes (Settings > नवीन योजना). Sample: `मुदत ठेव`, `दामदुप्पट`, `दाम दुप्पट ठेव (कर्जातील)`, `पेंशन ठेव` |
| 3 | क्लोज / ओपन एंडेड | Closed / Open Ended | Label (read-only) | No | Auto-filled from scheme; e.g. `क्लोज एंडेड` |
| 4 | व्याज प्रकार | Interest Type | Label (read-only) | No | Auto-filled from scheme; e.g. `साधे व्याज` |
| 5 | कम्पाउंडिंग | Compounding | Label (read-only) | No | Auto-filled from scheme |
| 6 | एजंट शाखा निवडा | Select Agent Branch | Autocomplete | No | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 7 | एजंट निवडा | Select Agent | Autocomplete | No | Replaces `एजंट क्रमांक` + `शोध एजंट नाव`. Scoped to field 6. Sample: `1 — Agent 1`. Enter resolves by ID or name |
| 8 | खाते क्र. | Account No. | Label (read-only) | No | Auto-generated on save |
| 9 | खाते प्रकार | Account Type | Dropdown | Yes | Same as [New Scheme FD account types](../settings/schemes/new-scheme-screen.md): `सामान्य खाते`, `ज्येष्ठ नागरिक खाते`, `महिला`, `विधवा`, `अपंग`, `दुसरी संस्था`, `नोकर`, `स्वातंत्र्यसैनिक`, `अति ज्येष्ठ नागरिक` |
| 10 | व्याज दर स्लॅब | Interest Rate Slab | Dropdown | Yes | Loaded from selected scheme's duration/benefits grid (कालावधी + व्याज दर + खाते प्रकार rows). Default: `निवडा` |
| 11 | कालावधी (महिने) | Duration (Months) | Label (read-only) | Yes | Auto-filled from slab selection |
| 12 | कालावधी (दिवस) | Duration (Days) | Label (read-only) | Yes | Auto-filled from slab selection |
| 13 | चालू दिनांक | Current Date | Date | Yes | Default: system date |
| 14 | मुदत ठेव रक्कम (रु.) | FD Amount (Rs.) | Textbox | Yes | — |
| 15 | व्याज दर | Interest Rate | Label (read-only) | Yes | Auto-filled from slab; override requires admin role |
| 16 | व्याज चालू दिनांक | Interest Start Date | Date | Yes | — |
| 17 | मुदतपूर्ती रक्कम (रु.) | Maturity Amount (Rs.) | Label (read-only) | No | Calculated |
| 18 | परतीची दिनांक | Return Date | Label (read-only) | No | Calculated |
| 19 | पावती तारीख | Receipt Date | Label (read-only) | No | Calculated |
| 20 | स्थिती | Status | Dropdown | Yes | Default: `चालू` (Active). Values: `चालू`, `बंद` (Closed), `स्थगित` (Suspended) |
| 21 | आय.एफ.एस.सी. कोड | IFSC Code | Textbox | No | Enables bank payout |
| 22 | बँकेचे नाव | Bank Name | Label (read-only) | No | Auto-filled from IFSC |
| 23 | बँकेचे बचत खाते क्रमांक | Bank Savings Account No. | Textbox | No | — |

### Section: प्रगत सेटिंग्ज (Advanced Settings)

> Collapsed by default. Visible to users with accounting/admin role or when expanded manually.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 24 | विक्री एजंट शाखा निवडा | Select Sales Agent Branch | Autocomplete | No | Sample: `1 — Branch 1`. Enter resolves by ID or name |
| 25 | विक्री एजंट निवडा | Select Sales Agent | Autocomplete | No | Replaces `विक्री एजंट क्रमांक` + `विक्री एजंटचे नाव शोधा`. Sample: `1 — Agent 1` |
| 26 | पावती प्रीफिक्स | Receipt Prefix | Textbox | Yes | Receipt series |
| 27 | पावती क्रमांक | Receipt Number | Textbox | Yes | — |
| 28 | वास्तविक एफडी रक्कम | Actual FD Amount | Textbox | No | Multiple FD workflow |
| 29 | गुणक | Multiplier | Textbox | No | Default: `1` |

**Action (Multiple FD):** `+ टाका` (Add).

### Section: वारसदार पर्याय (Nominee Option)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 30 | वारसदार जोडा | Add Nominee | Checkbox | No | Unchecked by default. When checked, Tab 2 (Nominee) becomes visible in the tab bar; when unchecked, Tab 2 is hidden and skipped during Next/Back navigation. |

### Section: संयुक्त खातेदार पर्याय (Joint Holder Option)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 31 | संयुक्त खातेदार जोडा | Add Joint Holder | Checkbox | No | Unchecked by default. When checked, Tab 3 (Joint Holder) becomes visible in the tab bar; when unchecked, Tab 3 is hidden and skipped during Next/Back navigation. |

**Action:** `पुढे` (Next).

---

## Tab 2: वारसदार (Nominee)

> Hidden by default — shown only when field 30 (Tab 1) is checked.

> **Shared component:** Uses `app-nominee-form` + `app-nominee-grid`. Same field set as [Daily New Account Tab 2](../daily/new-daily-account-screen.md#tab-2-वारसदार-nominee). See [quick-add-customer-pattern.md](../shared/quick-add-customer-pattern.md).

### Section: वारसदार शोधा (Search Nominee)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | ग्राहक निवडा | Select Customer | Autocomplete | Yes | Nominee lookup. Enter resolves by customer no. or name; e.g. `662 — Customer 2`. Includes **+ नवीन ग्राहक जोडा** per [quick-add-customer-pattern.md](../shared/quick-add-customer-pattern.md). See [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |

### Section: वारसदार तपशील (Nominee Details)

> Visible only after a nominee customer is resolved in field 1.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 2 | नाते | Relation | Dropdown | Yes | Same as [Membership nominee relation](../membership/new-membership-screen.md) |
| 3 | टक्केवारी | Percentage | Textbox | No | e.g. `100` |
| 4 | नामांकन दिनांक | Nomination Date | Label (read-only) | No | System date |
| 5 | नामांकन करताना वय | Age at Nomination | Label (read-only) | No | Auto-calculated from resolved customer's date of birth |

**Action:** `टाका` (Add).

### Nominee Grid (`app-nominee-grid`)

Columns: निवडा, अनु. क्र., ग्राहक क्रमांक, ग्राहकाचे नाव, नाते, टक्केवारी, नामांकन करताना वय, नामांकन दिनांक.

**Actions:** `निश्चित करा` (Confirm), `रद्द करा` (Cancel).

**Navigation:** `मागे` (Back), `पुढे` (Next).

---

## Tab 3: संयुक्त खाते धारक (Joint Holder)

> Hidden by default — shown only when field 31 (Tab 1) is checked.

> **Shared component:** Adapted from [New Membership Tab 2](../membership/new-membership-screen.md#tab-2-परिचयकर्ता--संयुक्त-खातेदार-introducer--joint-holder) joint-holder sections; Introducer section omitted for deposit products per bank review. Uses `app-joint-holder-grid`. See [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md).

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

**Navigation:** `मागे` (Back), `पुढे` (Next).

---

## Tab 4: इतर (Other)

### Section: General

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शेरा | Remarks | Textbox | No | — |
| 2 | व्याज पुनर्निवेश | Interest Reinvestment | Checkbox | No | Enables field 3 |
| 3 | एस.आय. व्याज पुनर्गंतवणूक | S.I. Interest Reinvestment | Dropdown | No | Shown when field 2 checked. e.g. `मासिक` (Monthly) |

### Section: Renewal

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 4 | ऑटो नूतनीकरण | Auto Renewal | Checkbox | No | When checked, field 5 (`नूतनीकरण`) is disabled |
| 5 | नूतनीकरण | Renewal | Checkbox | No | Disabled when field 4 checked |
| 6 | मुद्दल + व्याज | Principal + Interest | Radio | No | Renewal type; group with fields 7–8. Enabled when field 5 checked |
| 7 | फक्त मुद्दल | Only Principal | Radio | No | Default when renewal enabled |
| 8 | केवळ व्याज | Only Interest | Radio | No | — |

### Section: Interest Transfer

Visible when field 9 checked.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 9 | व्याज हस्तांतरण | Interest Transfer | Checkbox | No | Enables fields 11–16 |
| 10 | इतर बँकेत निधी हस्तांतरण | Fund Transfer to Other Bank | Checkbox | No | — |
| 11 | जी.एल. निवडा | Select GL | Autocomplete | No | Replaces `जी.एल.हेड` + `जी.एल.निवडा`. Sample: `91 — FD Interest`. See [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |
| 12 | खातेधारक निवडा | Select Account Holder | Autocomplete | No | Replaces `खाते क्र.` + `खातेधारक निवडा` dropdown. Sample: `101 — Account Holder 1` |
| 13 | वारंवारता निवडा | Select Frequency | Dropdown | No | e.g. `महिन्यात` (Monthly) |
| 14 | दिवस / तारीख निवडा | Select Day / Date | Dropdown | No | e.g. `28` (day of month when frequency is monthly) |

### Section: Account Closing

Visible when field 15 checked.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 15 | खाते बंद करतेवेळी | At Account Closing | Checkbox | No | Enables fields 16–17 |
| 16 | जी.एल. निवडा | Select GL | Autocomplete | No | Replaces `जी.एल.हेड` + `जी.एल.निवडा` |
| 17 | खातेधारक निवडा | Select Account Holder | Autocomplete | No | Replaces `खाते क्र.` + `खातेधारक निवडा` dropdown |

### Section: प्रगत सेटिंग्ज (Advanced Settings)

> Collapsed by default.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 18 | एल. एफ. क्रमांक | L.F. Number | Textbox | No | — |

**Navigation:** `मागे` (Back). **Footer:** `पूर्ण` (Complete), `पूर्ववत` (Reset).

---

## Mockup

- [HTML mockup (Draft)](../mockups/fixed-deposit/new-fd-account-screen/) — Marathi layout for bank review

## Related Documents

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [fd-transaction-screen.md](fd-transaction-screen.md)
- [fd-account-management-screen.md](fd-account-management-screen.md)
- [../settings/schemes/new-scheme-screen.md](../settings/schemes/new-scheme-screen.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
- [../shared/quick-add-customer-pattern.md](../shared/quick-add-customer-pattern.md)
