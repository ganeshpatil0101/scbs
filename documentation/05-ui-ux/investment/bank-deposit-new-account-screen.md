# Screen Spec — Bank Deposit New Account (गुंतवणूक > बँक ठेव > नवीन खाते)

## Purpose

UI specification for opening a new bank deposit / investment account (FD-style deposit with external bank).

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | नवीन खाते | New Account |
| Breadcrumb | डॅशबोर्ड > गुंतवणूक > बँक ठेव > नवीन खाते | Dashboard > Investment > Bank Deposit > New Account |
| Parent Module | गुंतवणूक > बँक ठेव | Investment > Bank Deposit |

## Reference Screenshots

| File | Section |
| :--- | :--- |
| `screenshots/गुंतवणूक/डॅशबोर्ड  गुंतवणूक  बँक ठेव नवीन खाते-1.png` | Full screen |

---

## Form Fields

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | बँक (जीएल खाते) | Bank (GL Account) | Textbox | Yes | G.L. code — e.g. `134` |
| 2 | बँक निवडा (जी.एल. हेड) | Select Bank (G.L. Head) | Dropdown | Yes | From investment bank list |
| 3 | खाते क्रमांक. | Account Number | Textbox | Yes | Internal account no. |
| 4 | खाते | Account | Textbox | Yes | — |
| 5 | बँक खाते क्र. | Bank Account No. | Textbox | Yes | — |
| 6 | निधी | Fund | Dropdown | No | Default: `निवडा`. Values: `TODO` |
| 7 | ठेव प्रकार | Deposit Type | Dropdown | Yes | e.g. `मुदत ठेव` (Fixed Deposit) |
| 8 | व्याज प्रकार | Interest Type | Radio | No | `सरळ` (Simple), `चक्रव्याज` (Compound) |
| 9 | व्याज गणना प्रकार | Interest Calculation Type | Dropdown | Yes | e.g. `महिने` (Months) |
| 10 | चालू दिनांक | Open Date | Date | Yes | — |
| 11 | कालावधी (महिने) | Duration (Months) | Textbox | Yes | — |
| 12 | कालावधी (दिवस) | Duration (Days) | Textbox | Yes | — |
| 13 | व्याज सुरु दिनांक | Interest Start Date | Date | Yes | — |
| 14 | रक्कम (रू.) | Amount (Rs.) | Textbox | Yes | — |
| 15 | व्याज दर (% वार्षिक) | Interest Rate (% p.a.) | Textbox | Yes | — |
| 16 | पावती क्रमांक | Receipt Number | Textbox | Yes | — |
| 17 | परतीची दिनांक | Maturity / Return Date | Date | Yes | — |
| 18 | परतीची रक्कम (रू.) | Maturity / Return Amount (Rs.) | Textbox | Yes | — |
| 19 | स्थिती | Status | Dropdown | Yes | e.g. `चालू` (Active) |
| 20 | तपशील | Details | Textbox | No | — |
| 21 | व्याज हस्तांतरणासाठी बँक निवडा | Select Bank for Interest Transfer | Dropdown | No | Default: `निवडा`. Values: `TODO` |

### Document Upload

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 22 | दस्तऐवज अपलोड करा | Upload Document | File | No | — |

**Action:** `दस्तऐवज अपडेट करा`.

**Actions:** `पूर्ण`, `पूर्ववत`.

---

## Related Documents

- [overview.md](overview.md)
- [bank-deposit-transaction-screen.md](bank-deposit-transaction-screen.md)
- [bank-deposit-bank-list-screen.md](bank-deposit-bank-list-screen.md)
