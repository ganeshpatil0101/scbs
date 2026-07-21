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

## Section: खात्याची माहिती (Account Details)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | बँक निवडा | Select Bank | Autocomplete | Yes | Replaces `बँक (जीएल खाते)` + `बँक निवडा (जी.एल. हेड)`. From investment bank masters — [bank-deposit-bank-management-screen.md](bank-deposit-bank-management-screen.md). Enter resolves by GL head ID or name; e.g. `134 — Bank Name`. See [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |
| 2 | खाते क्रमांक. | Account Number | Label (read-only) | No | Auto-generated on save |
| 3 | खाते नाव | Account Name | Textbox | Yes | Account title; aligns with interest grid `खाते नाव` |
| 4 | बँक खाते क्र. | Bank Account No. | Textbox | Yes | External bank's actual account number |
| 5 | ठेव प्रकार | Deposit Type | Dropdown | Yes | Default: `निवडा`. Values: `0` मुदत ठेव, `1` कॉल ठेव, `2` एमआयएस ठेव, `3` आवर्ती ठेव मासिक, `4` आवर्ती ठेव तिमाही, `5` आवर्ती ठेव सहामाही, `6` आवर्ती ठेव वार्षिक |
| 6 | चालू दिनांक | Open Date | Date | Yes | Default: system date |
| 7 | कालावधी (महिने) | Duration (Months) | Textbox | Yes | — |
| 8 | कालावधी (दिवस) | Duration (Days) | Textbox | Yes | Default: `0` |
| 9 | रक्कम (रू.) | Amount (Rs.) | Textbox | Yes | Principal |
| 10 | व्याज दर (% वार्षिक) | Interest Rate (% p.a.) | Textbox | Yes | — |
| 11 | व्याज सुरु दिनांक | Interest Start Date | Label (read-only) | No | Auto-filled = Open Date; override requires admin role |
| 12 | परतीची दिनांक | Maturity / Return Date | Label (read-only) | No | Calculated from open date + duration |
| 13 | परतीची रक्कम (रू.) | Maturity / Return Amount (Rs.) | Label (read-only) | No | Calculated from amount, rate, duration, interest type |
| 14 | स्थिती | Status | Label / Dropdown | — | Create: read-only `चालू` (Active). Update: `चालू`, `बंद`, `स्थगित` — same as FD / Savings / Daily |
| 15 | तपशील | Details | Textbox | No | Optional notes |
| 16 | व्याज हस्तांतरणासाठी बँक निवडा | Select Bank for Interest Transfer | Autocomplete | No | From society Bank master — [../bank/bank-management-screen.md](../bank/bank-management-screen.md). Enter resolves by ID or name; e.g. `1 — बँक ऑफ इंडिया`. See [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |

### Section: प्रगत सेटिंग्ज (Advanced Settings)

> Collapsed by default. Visible to users with accounting/admin role or when expanded manually.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 17 | व्याज प्रकार | Interest Type | Radio | No | `सरळ` (Simple), `चक्रव्याज` (Compound) |
| 18 | व्याज गणना प्रकार | Interest Calculation Type | Dropdown | Yes | Default: `निवडा`. Values: `1` दिवस, `2` महिने |
| 19 | पावती क्रमांक | Receipt Number | Textbox | Yes | Receipt series |

**Removed:** `निधी` (Fund) — not required for bank deposit new account.

### Document Upload

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 20 | दस्तऐवज अपलोड करा | Upload Document | File | No | Optional deposit proof |

**Action:** `दस्तऐवज अपडेट करा`.

**Actions:** `पूर्ण`, `पूर्ववत`.

---

## Mockup

- [HTML mockup (Draft)](../mockups/investment/bank-deposit-new-account-screen/) — Marathi layout for bank review

## Related Documents

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [bank-deposit-transaction-screen.md](bank-deposit-transaction-screen.md)
- [bank-deposit-bank-management-screen.md](bank-deposit-bank-management-screen.md)
- [../bank/bank-management-screen.md](../bank/bank-management-screen.md)
- [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
