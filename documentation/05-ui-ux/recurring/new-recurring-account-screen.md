# Screen Spec — New Recurring Account (रिकरिंग > नवीन खाते)

## Purpose

UI specification for opening a new recurring deposit account. Three-tab wizard (Tab 3 optional — hidden unless enabled on Tab 1).

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | नवीन खाते | New Account |
| Breadcrumb | डॅशबोर्ड > रिकरिंग > नवीन खाते | Dashboard > Recurring > New Account |
| Parent Module | रिकरिंग | Recurring |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | खाते माहिती | Account Information |
| 2 | वारसदार | Nominee |
| 3 | संयुक्त खातेदार | Joint Holder |

## Reference Screenshots / Media

| File | Tab |
| :--- | :--- |
| `screenshots/रिकरिंग/डॅशबोर्ड_रिकरिंग_नवीन खाते.mp4` | All tabs (from video) |
| `screenshots/रिकरिंग/new-account-frames/frame_0000.jpg` | Tab 1 |
| `screenshots/रिकरिंग/new-account-frames/frame_0030.jpg` | Tab 2 — Nominee |
| `screenshots/रिकरिंग/डॅशबोर्ड-रिकरिंग-नवीन खाते-सूचक.png` | Tab 3 — Joint Holder (shared pattern across deposit products) |
| `screenshots/रिकरिंग/डॅशबोर्ड-रिकरिंग-नवीन खाते-खाते-चालविण्याची-सूचना.png` | Tab 3 — Account Operation Instructions dropdown |

---

## Tab 1: खाते माहिती (Account Information)

### Section: ग्राहक माहिती (Customer Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | ग्राहक निवडा | Select Customer | Autocomplete | Yes | Replaces `ग्राहक क्र.` + `ग्राहक नाव`. Enter resolves by customer no. or name; e.g. `661 — Customer 1`. See [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |

**Customer summary (read-only Labels after resolve):** सभासद खाते क्र., वय(वर्षे), सभासदत्व प्रकार, ग्राहक शाखा, विशेष सूचना.

### Section: खाते माहिती (Account Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 2 | योजना निवडा | Select Scheme | Dropdown | Yes | Loaded dynamically from Recurring schemes (Settings > नवीन योजना, Scheme Type = रिकरिंग). Sample: `रिकरिंग ठेव` |
| 3 | योजना / व्याज प्रकार | Scheme / Interest Type | Label (read-only) | No | Auto-filled from scheme |
| 4 | परिणामगणन | Compounding | Label (read-only) | No | Auto-filled from scheme; e.g. `वार्षिक` |
| 5 | खाते क्रमांक | Account Number | Label (read-only) | No | Auto-generated on save |
| 6 | एजंट शाखा निवडा | Select Agent Branch | Autocomplete | No | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 7 | एजंट निवडा | Select Agent | Autocomplete | No | Replaces `एजंट कोड` + `शोध एजंट नाव`. Scoped to field 6. Sample: `1 — Agent 1`. Enter resolves by ID or name |

### Section: खाते तपशील (Account Details)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 8 | खाते प्रकार | Account Type | Dropdown | Yes | Same as [New Scheme recurring account types](../settings/schemes/new-scheme-screen.md) Tab 2 benefits. Values: `TODO` — cross-check scheme |
| 9 | कालावधी निवडा | Select Duration | Dropdown | Yes | Loaded from selected scheme's duration/rate slab grid (e.g. `0-60`) |
| 10 | कालावधी(महिने) | Duration (Months) | Label (read-only) | Yes | Auto-filled from duration selection; e.g. `60` |
| 11 | व्याज दर(% वार्षिक) | Interest Rate (% p.a.) | Label (read-only) | Yes | Auto-filled from slab; e.g. `12.37`. Admin override requires admin role |
| 12 | खाते चालू दिनांक | Account Opening Date | Date | Yes | Default: system date |
| 13 | परतीची दिनांक | Maturity Date | Label (read-only) | Yes | Calculated from duration + open date |
| 14 | भरणा रक्कम | Installment Amount | Textbox | Yes | Core RD field |
| 15 | भरणा प्रकार निवडा | Select Deposit Type | Dropdown | Yes | e.g. `मासिक`. May default from scheme |
| 16 | परतीची रक्कम | Maturity Amount | Label (read-only) | No | Calculated; see Interest Multiplier |
| 17 | विशेष सूचना | Special Instructions | Textarea | No | Account-level note (distinct from customer summary) |
| 18 | स्थिती निवडा | Select Status | Dropdown | Yes | Default: `चालू`. Values: `चालू`, `बंद`, `स्थगित` |

### Section: प्रगत सेटिंग्ज (Advanced Settings)

> Collapsed by default. Visible to users with accounting/admin role or when expanded manually.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 19 | विक्री एजंट शाखा निवडा | Select Sales Agent Branch | Autocomplete | No | Sample: `1 — Branch 1`. Enter resolves by ID or name |
| 20 | विक्री एजंट निवडा | Select Sales Agent | Autocomplete | No | Replaces `विक्री एजंट क्रमांक` + `विक्री एजंटचे नाव शोधा`. Sample: `1 — Agent 1` |
| 21 | आय.एफ.एस.सी. कोड | IFSC Code | Textbox | No | Enables bank payout on maturity |
| 22 | बँकेचे नाव | Bank Name | Label (read-only) | No | Auto-filled from IFSC |
| 23 | बँकेचे बचत खाते क्रमांक | Bank Savings Account No. | Textbox | No | Maturity payout optional |

### Section: संयुक्त खातेदार पर्याय (Joint Holder Option)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 24 | संयुक्त खातेदार जोडा | Add Joint Holder | Checkbox | No | Unchecked by default. When checked, Tab 3 (Joint Holder) becomes visible in the tab bar; when unchecked, Tab 3 is hidden and skipped during Next/Back navigation. |

**Action:** `पुढे` (Next).

---

## Tab 2: वारसदार (Nominee)

Uses shared component `app-nominee-form` + `app-nominee-grid` — same field set and dropdown rules as [Daily New Account Tab 2](../daily/new-daily-account-screen.md#tab-2-वारसदार-nominee) (salutation, occupation, relation, Google Maps address).

**Actions:** `टाका`, `पुनर्निर्धारित करा`, `निकाला`.

---

## Tab 3: संयुक्त खातेदार (Joint Holder)

> Hidden by default — shown only when field 24 (Tab 1) is checked.

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

**Navigation:** `मागे` (Back). **Footer:** `जतन करा` (Save), `रीसेट` (Reset).

---

## Mockup

- [HTML mockup (Draft)](../mockups/recurring/new-recurring-account-screen/) — Marathi layout for bank review

## Related Documents

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [../settings/schemes/new-scheme-screen.md](../settings/schemes/new-scheme-screen.md)
- [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
