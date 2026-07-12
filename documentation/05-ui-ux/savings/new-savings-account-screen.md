# Screen Spec — New Savings Account (बचत > नवीन खाते)

## Purpose

UI specification for opening a new savings account. Four-tab wizard.

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
| 3 | परिचयकर्ता / संयुक्त खाते धारक | Introducer / Joint Holder |
| 4 | मंजूरी | Approval |

## Reference Screenshots

| File | Tab |
| :--- | :--- |
| `screenshots/bachat/डॅशबोर्ड-बचत-नवीन खाते.png` | Tab 1 — Account Information |

---

## Tab 1: खात्याची माहिती (Account Information)

### Section: ग्राहक माहिती (Customer Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | ग्राहक निवडा | Select Customer | Autocomplete | Yes | Replaces `ग्राहक क्र.` + `ग्राहक नाव`. Enter resolves by customer no. or name; e.g. `661 — Customer 1`. See [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |

**Customer summary (read-only Labels after resolve):** सभासद क्रमांक, वय (वर्षे), ग्राहक शाखा नाव, सभासद प्रकार, विशेष सूचना.

### Section: खात्याची माहिती (Account Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 2 | योजना निवडा | Select Scheme | Dropdown | Yes | Loaded dynamically from Savings schemes (Settings > नवीन योजना, Scheme Type = बचत). Sample: `सेव्हिंग ठेव`. Values: `TODO` — cross-check scheme master |
| 3 | खाते क्र. | Account No. | Label (read-only) | No | Auto-generated on save; e.g. `113` |
| 4 | एजंट शाखा निवडा | Select Agent Branch | Autocomplete | No | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 5 | एजंट निवडा | Select Agent | Autocomplete | No | Replaces `एजंट क्रमांक` + `एजंट नाव शोध`. Scoped to field 4. Sample: `1 — Agent 1`. Enter resolves by ID or name |

### Section: खाते तपशील (Account Details)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 6 | व्याज दर (% पी ए) | Interest Rate (% p.a.) | Label (read-only) | Yes | Auto-filled from selected scheme; e.g. `4.00`. Admin override requires admin role |
| 7 | चालू दिनांक | Current Date | Date | Yes | Default: system date |
| 8 | विशेष सूचना | Special Instructions | Textbox | No | Account-level note (distinct from customer summary) |
| 9 | किमान शिल्लक | Minimum Balance | Textbox | Yes | e.g. `0.00`; may default from scheme |
| 10 | स्थिती निवडा | Select Status | Dropdown | No | Default: `चालू` (Active). Other values: `TODO` |
| 11 | खाते श्रेणी निवडा | Select Account Category | Dropdown | No | Default: `नियमित` (Regular). Other values: `TODO` |

### Section: प्रगत सेटिंग्ज (Advanced Settings)

> Collapsed by default. Visible to users with accounting/admin role or when expanded manually.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 12 | विक्री एजंट शाखा निवडा | Select Sales Agent Branch | Autocomplete | No | Sample: `1 — Branch 1`. Enter resolves by ID or name |
| 13 | विक्री एजंट निवडा | Select Sales Agent | Autocomplete | No | Replaces `विक्री एजंट क्रमांक` + `विक्री एजंटचे नाव शोधा`. Sample: `1 — Agent 1` |
| 14 | नावे मर्यादा | Debit Limit | Textbox | No | — |
| 15 | निधी हस्तांतरण मर्यादा | Fund Transfer Limit | Textbox | No | e.g. `0` |
| 16 | आय.एफ.एस.सी. कोड | IFSC Code | Textbox | No | Enables bank payout |
| 17 | बँकेचे नाव | Bank Name | Label (read-only) | No | Auto-filled from IFSC |
| 18 | बँकेचे बचत खाते क्रमांक | Bank Savings Account No. | Textbox | No | Optional payout account |

**Action:** `पुढे` (Next).

---

## Tab 2: वारसदार (Nominee)

Uses shared component `app-nominee-form` + `app-nominee-grid` — same field set and dropdown rules as [Daily New Account Tab 2](../daily/new-daily-account-screen.md#tab-2-वारसदार-nominee) (salutation, occupation, relation, Google Maps address).

`TODO` — tab not captured in screenshots. Capture before mockup.

---

## Tab 3: परिचयकर्ता / संयुक्त खाते धारक (Introducer / Joint Holder)

`TODO` — entire tab not captured. Capture from legacy app before mockup.

---

## Tab 4: मंजूरी (Approval)

`TODO` — entire tab not captured. Capture from legacy app before mockup.

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
