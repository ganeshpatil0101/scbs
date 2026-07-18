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
