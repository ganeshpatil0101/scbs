# Screen Spec — New Recurring Account (रिकरिंग > नवीन खाते)

## Purpose

UI specification for opening a new recurring deposit account. Four-tab wizard.

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
| 3 | सूचक/संयुक्त खातेदार | Introducer / Joint Holder |
| 4 | मंजुरी | Approval |

## Reference Screenshots / Media

| File | Tab |
| :--- | :--- |
| `screenshots/रिकरिंग/डॅशबोर्ड_रिकरिंग_नवीन खाते.mp4` | All tabs (from video) |
| `screenshots/रिकरिंग/new-account-frames/frame_0000.jpg` | Tab 1 |
| `screenshots/रिकरिंग/new-account-frames/frame_0030.jpg` | Tab 2 — Nominee |

---

## Tab 1: खाते माहिती (Account Information)

### ग्राहक माहिती (Customer Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | ग्राहक क्र. | Customer No. | Textbox | Yes | — |
| 2 | ग्राहक नाव | Customer Name | Textbox | No | Read-only |
| 3 | सभासद खाते क्र. | Member Account No. | Textbox | No | Read-only |
| 4 | वय(वर्षे) | Age (Years) | Textbox | No | Read-only |
| 5 | सभासदत्व प्रकार | Membership Type | Textbox | No | Read-only |
| 6 | ग्राहक शाखा | Customer Branch | Textbox | No | Read-only |
| 7 | विशेष सूचना | Special Instructions | Textbox | No | Read-only |

### खाते माहिती (Account Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 8 | योजना निवडा | Select Scheme | Dropdown | Yes | e.g. `रिकरिंग ठेव` |
| 9 | योजना / व्याज प्रकार | Scheme / Interest Type | Textbox | No | Read-only |
| 10 | परिणामगणन | Compounding | Textbox | No | Read-only; e.g. `वार्षिक` |
| 11 | खाते क्रमांक | Account Number | Textbox | Yes | Auto-generated |
| 12 | एजंट शाखा कोड | Agent Branch Code | Textbox | No | — |
| 13 | एजंट शाखा निवडा | Select Agent Branch | Dropdown | No | Values: `TODO` |
| 14 | एजंट कोड | Agent Code | Textbox | No | — |
| 15 | शोध एजंट नाव | Search Agent Name | Textbox | No | — |
| 16 | विक्री एजंट शाखा क्र. | Sales Agent Branch No. | Textbox | No | — |
| 17 | विक्री एजंट शाखा निवडा | Select Sales Agent Branch | Dropdown | No | Values: `TODO` |
| 18 | विक्री एजंट क्रमांक | Sales Agent Number | Textbox | No | — |
| 19 | विक्री एजंटचे नाव शोधा | Search Sales Agent Name | Textbox | No | — |

### खाते तपशील (Account Details)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 20 | खाते प्रकार | Account Type | Dropdown | Yes | Values: `TODO` |
| 21 | कालावधी निवडा | Select Duration | Dropdown | No | e.g. `0-60` |
| 22 | कालावधी(महिने) | Duration (Months) | Textbox | No | e.g. `60` |
| 23 | व्याज दर(% वार्षिक) | Interest Rate (% p.a.) | Textbox | Yes | e.g. `12.37` |
| 24 | खाते चालू दिनांक | Account Opening Date | Date | Yes | — |
| 25 | परतीची दिनांक | Maturity Date | Date | Yes | — |
| 26 | भरणा रक्कम | Installment Amount | Textbox | Yes | — |
| 27 | भरणा प्रकार निवडा | Select Deposit Type | Dropdown | Yes | e.g. `मासिक` |
| 28 | परतीची रक्कम | Maturity Amount | Textbox | No | Calculated |
| 29 | विशेष सूचना | Special Instructions | Textarea | No | — |
| 30 | स्थिती निवडा | Select Status | Dropdown | Yes | e.g. `चालू` |
| 31 | आय.एफ.एस.सी. कोड | IFSC Code | Textbox | No | — |
| 32 | बँकेचे नाव | Bank Name | Textbox | No | — |
| 33 | बँकेचे बचत खाते क्रमांक | Bank Savings Account No. | Textbox | No | — |

**Action:** `पुढे` (Next). Tabs 3–4: `TODO`.

---

## Tab 2: वारसदार (Nominee)

Same structure as [new-daily-account-screen.md](../daily/new-daily-account-screen.md) Tab 2 (nominee entry form + multiple nominees grid).

**Actions:** `टाका`, `पुनर्निर्धारित करा`, `निकाला`.

---

## Cross-Links

- [overview.md](overview.md)
- [../settings/schemes/recurring-new-scheme-screen.md](../settings/schemes/recurring-new-scheme-screen.md)
