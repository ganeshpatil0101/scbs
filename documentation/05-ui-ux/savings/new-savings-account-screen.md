# Screen Spec — New Savings Account (बचत > नवीन खाते)

## Purpose

UI specification for opening a new savings account. Three-tab wizard (Tabs 2 and 3 optional — hidden unless enabled on Tab 1).

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | नवीन खाते | New Account |
| Breadcrumb | डॅशबोर्ड > बचत > नवीन खाते | Dashboard > Savings > New Account |
| Parent Module | बचत | Savings |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | खात्याची माहिती | Account Information |
| 2 | वारसदार | Nominee |
| 3 | संयुक्त खाते धारक | Joint Holder |

## Reference Screenshots

| File | Tab |
| :--- | :--- |
| `screenshots/bachat/डॅशबोर्ड-बचत-नवीन खाते.png` | Tab 1 — Account Information |
| `screenshots/bachat/डॅशबोर्ड-बचत-नवीन खाते-परिचयकर्ता.png` | Tab 3 — Joint Holder (shared pattern across deposit products) |
| `screenshots/bachat/डॅशबोर्ड-बचत-नवीन खाते-खाते-चालविण्याची-सूचना.png` | Tab 3 — Account Operation Instructions dropdown |

---

## Tab 1: खात्याची माहिती (Account Information)

### Section: ग्राहक माहिती (Customer Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | ग्राहक निवडा | Select Customer | Autocomplete | Yes | Replaces `ग्राहक क्र.` + `ग्राहक नाव`. Enter resolves by customer no. or name; e.g. `661 — Customer 1`. See [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |

**Customer summary (read-only Label after resolve):** विशेष सूचना.

### Section: खात्याची माहिती (Account Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 2 | योजना निवडा | Select Scheme | Dropdown | Yes | Loaded dynamically from Savings schemes (Settings > नवीन योजना, Scheme Type = बचत). Sample: `सेव्हिंग ठेव`. Values: `TODO` — cross-check scheme master |
| 3 | खाते क्र. | Account No. | Label (read-only) | No | Auto-generated on save; e.g. `113` |

### Section: खाते तपशील (Account Details)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 4 | व्याज दर (% पी ए) | Interest Rate (% p.a.) | Label (read-only) | Yes | Auto-filled from selected scheme; e.g. `4.00`. Admin override requires admin role |
| 5 | चालू दिनांक | Current Date | Date | Yes | Default: system date |
| 6 | विशेष सूचना | Special Instructions | Textbox | No | Account-level note (distinct from customer summary) |
| 7 | किमान शिल्लक | Minimum Balance | Textbox | Yes | e.g. `0.00`; may default from scheme |
| 8 | स्थिती निवडा | Select Status | Dropdown | No | Default: `चालू` (Active). Other values: `TODO` |

### Section: प्रगत सेटिंग्ज (Advanced Settings)

> Collapsed by default. Visible to users with accounting/admin role or when expanded manually.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 9 | नावे मर्यादा | Debit Limit | Textbox | No | — |
| 10 | निधी हस्तांतरण मर्यादा | Fund Transfer Limit | Textbox | No | e.g. `0` |
| 11 | आय.एफ.एस.सी. कोड | IFSC Code | Textbox | No | Enables bank payout |
| 12 | बँकेचे नाव | Bank Name | Label (read-only) | No | Auto-filled from IFSC |
| 13 | बँकेचे बचत खाते क्रमांक | Bank Savings Account No. | Textbox | No | Optional payout account |

### Section: वारसदार पर्याय (Nominee Option)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 14 | वारसदार जोडा | Add Nominee | Checkbox | No | Unchecked by default. When checked, Tab 2 (Nominee) becomes visible in the tab bar; when unchecked, Tab 2 is hidden and skipped during Next/Back navigation. |

### Section: संयुक्त खातेदार पर्याय (Joint Holder Option)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 15 | संयुक्त खातेदार जोडा | Add Joint Holder | Checkbox | No | Unchecked by default. When checked, Tab 3 (Joint Holder) becomes visible in the tab bar; when unchecked, Tab 3 is hidden and skipped during Next/Back navigation. |

**Action:** `पुढे` (Next).

---

## Tab 2: वारसदार (Nominee)

> Hidden by default — shown only when field 14 (Tab 1) is checked.

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

**Actions:** `टाका` (Add), `निवड करा`, `काढा`.

### Nominee Grid (`app-nominee-grid`)

Columns: निवडा, अनु. क्र., ग्राहक क्रमांक, ग्राहकाचे नाव, नाते, टक्केवारी, नामांकन करताना वय, नामांकन दिनांक.

**Navigation:** `मागे` (Back), `पुढे` (Next).

---

## Tab 3: संयुक्त खाते धारक (Joint Holder)

> Hidden by default — shown only when field 15 (Tab 1) is checked.

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

- [HTML mockup (Draft)](../mockups/savings/new-savings-account-screen/) — Marathi layout for bank review

## Related Documents

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [../settings/schemes/new-scheme-screen.md](../settings/schemes/new-scheme-screen.md)
- [../customer/new-customer-screen.md](../customer/new-customer-screen.md)
- [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
- [../shared/quick-add-customer-pattern.md](../shared/quick-add-customer-pattern.md)
