# Screen Spec — Recurring New Scheme (रिकरिंग > नवीन योजना)

## Purpose

UI specification for creating a new **Recurring (रिकरिंग)** deposit scheme. Intended for AI agents implementing this screen.

## Scope

Single screen with **7 tabs**. Screenshots 2.2 and 5.2 are scroll continuations within tabs 2 and 5.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | नवीन योजना | New Scheme |
| Breadcrumb | डॅशबोर्ड > सेटिंग्ज > रिकरिंग > नवीन योजना | Dashboard > Settings > Recurring > New Scheme |
| Parent Module | रिकरिंग | Recurring |
| Related Screens | [daily-new-scheme-screen.md](daily-new-scheme-screen.md), [savings-new-scheme-screen.md](savings-new-scheme-screen.md), [fixed-deposit-new-scheme-screen.md](fixed-deposit-new-scheme-screen.md) | — |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | योजना नाव | Scheme Name |
| 2 | कालावधी | Duration |
| 3 | व्याज पोस्टिंग | Interest Posting |
| 4 | पगाराप्रमाणे भरणा | Payment as per Salary |
| 5 | खाते बंद | Account Close |
| 6 | चार्जेस | Charges |
| 7 | रिबेट | Rebate |

## Reference Screenshots

| Screenshot File | Tab / Section |
| :--- | :--- |
| `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-रिकरिंग-नवीन योजना-1.png` | Tab 1 — Scheme Name |
| `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-रिकरिंग-नवीन योजना-2.1.png` | Tab 2 — Duration (top) |
| `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-रिकरिंग-नवीन योजना-2.2.png` | Tab 2 — Duration (bottom: penalty & benefits) |
| `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-रिकरिंग-नवीन योजना-3.png` | Tab 3 — Interest Posting |
| `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-रिकरिंग-नवीन योजना-4.png` | Tab 4 — Payment as per Salary |
| `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-रिकरिंग-नवीन योजना-5.1.png` | Tab 5 — Account Close (pre-maturity) |
| `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-रिकरिंग-नवीन योजना-5.2.png` | Tab 5 — Account Close (commission & after-maturity) |
| `screenshots/settings/शबोर्ड-सेटिंग्ज-रिकरिंग-नवीन योजना-6.png` | Tab 6 — Charges (filename typo: missing `ड` in डॅशबोर्ड) |
| `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-रिकरिंग-नवीन योजना-7.png` | Tab 7 — Rebate |

---

## Tab 1: योजना नाव (Scheme Name)

### Fields

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | जीएल हेड क्र. | GL Head No. | Textbox | Yes | Shown: `163` |
| 2 | योजना नाव | Scheme Name | Textbox | Yes | — |
| 3 | ओपन एंडेड | Open Ended | Radio Button | No | Default selected |
| 4 | क्लोज एंडेड | Close Ended | Radio Button | No | — |
| 5 | फक्त सदस्यांना परवानगी द्या | Allow Only Members | Checkbox | No | — |
| 6 | मॅच्युरीटी रक्कमेप्रमाणे | As per Maturity Amount | Checkbox | No | — |
| 7 | सरळ व्याज | Simple Interest | Radio Button | No | Default selected; व्याज प्रकार group |
| 8 | चक्रवाढ व्याज | Compound Interest | Radio Button | No | — |
| 9 | मासिक | Monthly | Radio Button | No | Compound frequency |
| 10 | त्रैमासिक | Quarterly | Radio Button | No | — |
| 11 | अर्धवार्षिक | Half-Yearly | Radio Button | No | — |
| 12 | वार्षिक | Yearly | Radio Button | No | — |
| 13 | विना पोस्टींग कंम्पाउंडींग | Compounding Without Posting | Checkbox | No | — |
| 14 | तपशील | Details | Textbox | No | — |
| 15 | स्थिती | Status | Dropdown | Yes | Shown: `चालू` (Active). **TODO:** Other values |
| 16 | मॅच्युरीटीसाठी लॉकिंग कालावधी | Locking Period for Maturity | Checkbox | No | — |

### Navigation

| Marathi | English | Type |
| :--- | :--- | :--- |
| पुढे | Next | Button |

---

## Tab 2: कालावधी (Duration)

> Screenshots 2.1 (top) and 2.2 (bottom) are one scrollable tab.

### General Setting

| Marathi Label | English Label | Type | Required | Notes |
| :--- | :--- | :--- | :---: | :--- |
| Interest Rate Decimal Places | Interest Rate Decimal Places | Textbox | Yes | Shown value: `4` (label in English in UI) |

### Section: कार्यकाळ आणि व्याजदर (Tenure and Interest Rate)

#### Input Row

| # | Marathi Label | English Label | Type | Required |
| :---: | :--- | :--- | :--- | :---: |
| 1 | कालावधी | Duration | Textbox | Yes |
| 2 | व्याज दर (द.सा.द.शे.) | Interest Rate (p.a. %) | Textbox | Yes |
| 3 | व्याज दर एजंट खाते (द.सा.द.शे.) | Interest Rate Agent Account (p.a. %) | Textbox | Yes |
| — | + टाका | + Add | Button | — |

#### Grid Columns

| Marathi | English |
| :--- | :--- |
| निवडा | Select |
| अ.क्र. | Sr. No. |
| कालावधी महिने | Duration (Months) |
| व्याज दर | Interest Rate |
| एजंट व्याज दर | Agent Interest Rate |

### Bottom Fields (screenshot 2.2)

| # | Marathi Label | English Label | Type | Notes |
| :---: | :--- | :--- | :--- | :--- |
| 1 | बीन व्याजी (महिने) | Interest-Free (Months) | Textbox | — |
| 2 | दंड दर | Penalty Rate | Checkbox | Enables penalty fields when checked |
| 3 | खाते बंद | Account Closed | Radio Button | Default selected; penalty context group |
| 4 | व्यवहार | Transaction | Radio Button | — |
| 5 | दंड दर (द.सा.द.शे.) | Penalty Rate (p.a. %) | Textbox | Disabled until Penalty Rate checked |
| 6 | थकीत हप्ते | Overdue Installments | Textbox | Disabled until Penalty Rate checked |
| 7 | थकीत हप्ते वाढीव कालावधी (दिवस) | Overdue Installments Extended Period (Days) | Textbox | Disabled until Penalty Rate checked |
| 8 | महिना अखेर पर्यंत | Until Month End | Checkbox | — |

### Section: बेनिफिट्स (Benefits)

| # | Marathi Label | English Label | Type |
| :---: | :--- | :--- | :--- |
| 1 | अपंग | Disabled | Checkbox |
| 2 | महिला | Female | Checkbox |
| 3 | विधवा | Widow | Checkbox |
| 4 | ज्येष्ठ नागरिक | Senior Citizen | Checkbox |
| 5 | दुसरी संस्था | Other Institution | Checkbox |
| 6 | मजूर | Laborer | Checkbox |
| 7 | स्वातंत्र्य सैनिक | Freedom Fighter | Checkbox |

### Benefit Interest Rate

| Marathi Label | English Label | Type |
| :--- | :--- | :--- |
| व्याज दर (द.सा.द.शे.) | Interest Rate (p.a. %) | Textbox |

### Navigation

| Marathi | English |
| :--- | :--- |
| मागे | Back |

---

## Tab 3: व्याज पोस्टिंग (Interest Posting)

### Input Row

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | व्याज पोस्टिंग दिवस | Interest Posting Day | Dropdown | Yes | `निवडा`, `28`, `29`, `30`, `31` |
| 2 | व्याज पोस्टिंग महिना | Interest Posting Month | Dropdown | Yes | Placeholder: `निवडा`. **TODO:** Month values |
| — | + टाका | + Add | Button | — | — |

### Grid Columns

| Marathi | English |
| :--- | :--- |
| अ.क्र. | Sr. No. |
| पोस्टिंग दिनांक | Posting Date |

**TODO:** Confirm Select column and Remove button — not visible in screenshot.

---

## Tab 4: पगाराप्रमाणे भरणा (Payment as per Salary)

### Fields

| # | Marathi Label | English Label | Type | Notes |
| :---: | :--- | :--- | :--- | :--- |
| 1 | पगारानुसार मासिक भरणा | Monthly Payment as per Salary | Checkbox | Enables salary-range inputs |
| 2 | मूळ पगार (रू.) (पासुन) | Basic Salary (Rs.) (From) | Textbox | Numeric |
| 3 | मूळ पगार (रू.) (पर्यंत) | Basic Salary (Rs.) (To) | Textbox | Numeric |
| 4 | मासिक भरणा (रू.) | Monthly Payment (Rs.) | Textbox | Numeric |
| — | + टाका | + Add | Button | — |

### Grid Columns

| Marathi | English |
| :--- | :--- |
| निवडा | Select |
| अ.क्र. | Sr. No. |
| पगार | Salary |
| मासिक भरणा | Monthly Payment |

---

## Tab 5: खाते बंद (Account Close)

> Screenshots 5.1 and 5.2 are scroll sections of one tab.

### Section A: मुदत पूर्वी (Before Maturity)

#### Input Row

| # | Marathi Label | English Label | Type | Values / Notes |
| :---: | :--- | :--- | :--- | :--- |
| 1 | कालावधी | Duration | Textbox | — |
| 2 | कालावधी प्रकार | Duration Type | Dropdown | Shown: `महिने` (Months). **TODO:** Other values |
| 3 | व्याज दर (द.सा.द.शे.) | Interest Rate (p.a. %) | Textbox | — |
| — | + टाका | + Add | Button | — |

#### Grid Columns

| Marathi | English |
| :--- | :--- |
| निवडा | Select |
| अ.क्र. | Sr. No. |
| कालावधी | Duration |
| व्याज दर (द.सा.द.शे.) | Interest Rate (p.a.) |

### Section B: Commission Settings

| # | Marathi Label | English Label | Type | Notes |
| :---: | :--- | :--- | :--- | :--- |
| 1 | वर्तमान व्याज दराप्रमाणे गणना करा | Calculate as per Current Interest Rate | Checkbox | — |
| 2 | खाते धारक | Account Holder | Radio Button | Default; group: कमिशन कपात पासून |
| 3 | एजंट | Agent | Radio Button | — |

### Section C: मुदत पूर्वी कमिशन कपात व्याज दर (Pre-Maturity Commission Deduction Interest Rate)

#### Input Row

| # | Marathi Label | English Label | Type | Values / Notes |
| :---: | :--- | :--- | :--- | :--- |
| 1 | कालावधी | Duration | Textbox | — |
| 2 | कालावधी प्रकार | Duration Type | Dropdown | Shown: `महिने`. **TODO:** Other values |
| 3 | व्याज दर (द.सा.द.शे.) | Interest Rate (p.a. %) | Textbox | — |
| — | + टाका | + Add | Button | — |

#### Grid Columns

| Marathi | English |
| :--- | :--- |
| निवडा | Select |
| अ.क्र. | Sr. No. |
| कालावधी | Duration |
| व्याज दर (द.सा.द.शे.) | Interest Rate (p.a.) |

### Section D: मुदत नंतर (After Maturity)

| # | Marathi Label | English Label | Type | Values / Notes |
| :---: | :--- | :--- | :--- | :--- |
| 1 | व्याज दर (द.सा.द.शे.) | Interest Rate (p.a. %) | Textbox | — |
| 2 | मुदती नंतरचा लॉकिंग कालावधी | Locking Period After Maturity | Textbox | — |
| 3 | कालावधी प्रकार | Duration Type | Dropdown | Placeholder: `निवडा`. **TODO:** Values |
| 4 | परिपक्व खाते अपुरा शिल्लक व्याज दर | Matured Account Insufficient Balance Interest Rate | Checkbox | — |
| 5 | व्याज दर (द.सा.द.शे.) | Interest Rate (p.a. %) | Textbox | Associated with checkbox above |

### Navigation

| Marathi | English |
| :--- | :--- |
| मागे | Back |

---

## Tab 6: चार्जेस (Charges)

### Fields

| # | Marathi Label | English Label | Type | Dropdown Values |
| :---: | :--- | :--- | :--- | :--- |
| 1 | चार्जेस | Charges | Dropdown | See table |

#### Charges Dropdown Values

| Marathi | English |
| :--- | :--- |
| निवडा | Select |
| कर्जदार कल्याण निधी | Borrower Welfare Fund |
| पिग्मी कमिशन | Pigmy Commission |
| प्रोसेसिंग फी | Processing Fee |
| ब वर्ग सभासद फी | Class B Member Fee |
| स्टेशनरी फी | Stationery Fee |

### Grid Columns

| Marathi | English |
| :--- | :--- |
| अ.क्र. | Sr. No. |
| चार्जेस | Charges |

**TODO:** Confirm whether amount/percentage fields appear after selecting a charge.

---

## Tab 7: रिबेट (Rebate)

### Fields

| # | Marathi Label | English Label | Type | Notes |
| :---: | :--- | :--- | :--- | :--- |
| 1 | कॅश बँक रिबेट | Cash Bank Rebate | Checkbox | — |
| 2 | आगाऊ हप्ता (पासुन) | Advance Installment (From) | Textbox | — |
| 3 | आगाऊ हप्ता (पर्यंत) | Advance Installment (To) | Textbox | — |
| 4 | रिबेट | Rebate | Textbox | — |
| 5 | रू. | Rupees (Rs.) | Radio Button | Default selected; प्रकार group |
| 6 | टक्के | Percentage (%) | Radio Button | — |
| — | + टाका | + Add | Button | — |

### Grid Columns

| Marathi | English |
| :--- | :--- |
| निवडा | Select |
| अ. क्र. | Sr. No. |
| हप्ता पासुन | Installment From |
| हप्ता पर्यंत | Installment To |
| रिबेट रक्कम | Rebate Amount |
| प्रकार | Type |

**TODO:** Confirm Remove button and final Save action for this tab.

---

## Mockup

| Property | Value |
| :--- | :--- |
| HTML mockup | [mockups/settings/schemes/recurring-new-scheme-screen/index.html](../../mockups/settings/schemes/recurring-new-scheme-screen/index.html) |
| Review guide | [mockups/settings/schemes/recurring-new-scheme-screen/README.md](../../mockups/settings/schemes/recurring-new-scheme-screen/README.md) |
| Stack | Tailwind CSS v4 (CDN), Marathi labels only |
| Status | Draft — pending bank user review |

---

## Related Documents

- [overview.md](overview.md)
- [daily-new-scheme-screen.md](daily-new-scheme-screen.md)
- [savings-new-scheme-screen.md](savings-new-scheme-screen.md)
- [fixed-deposit-new-scheme-screen.md](fixed-deposit-new-scheme-screen.md)
- [changelog.md](changelog.md)
