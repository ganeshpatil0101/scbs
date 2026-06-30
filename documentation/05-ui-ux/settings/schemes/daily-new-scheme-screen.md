# Screen Spec — Daily New Scheme (डेली > नवीन योजना)

## Purpose

UI specification for creating a new **Daily (डेली)** deposit scheme. Intended for AI agents implementing this screen.

## Scope

Single screen with **5 tabs**. All tabs belong to one wizard screen; screenshots are split across tabs and scroll sections.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | नवीन योजना | New Scheme |
| Breadcrumb | डॅशबोर्ड > सेटिंग्ज > डेली > नवीन योजना | Dashboard > Settings > Daily > New Scheme |
| Parent Module | डेली | Daily |
| Related Screens | [savings-new-scheme-screen.md](savings-new-scheme-screen.md), [fixed-deposit-new-scheme-screen.md](fixed-deposit-new-scheme-screen.md), [recurring-new-scheme-screen.md](recurring-new-scheme-screen.md) | — |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | योजना | Scheme |
| 2 | कालावधी (महिने) | Duration (Months) |
| 3 | व्याज पोस्टींग | Interest Posting |
| 4 | खाते बंद करा | Close Account |
| 5 | चार्जेस | Charges |

## Reference Screenshots

| Screenshot File | Tab / Section |
| :--- | :--- |
| `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-डेली-नवीन योजना-1.png` | Tab 1 — Scheme (includes validation alert for GL Head No.) |
| `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-डेली-नवीन योजना-2.png` | Tab 2 — Duration (Months) |
| `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-डेली-नवीन योजना-3.png` | Tab 3 — Interest Posting |
| `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-डेली-नवीन योजना-4.1.png` | Tab 4 — Close Account (section: मुदत पूर्वी) |
| `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-डेली-नवीन योजना-4.2.png` | Tab 4 — Close Account (commission & after-maturity sections) |
| `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-डेली-नवीन योजना-5.png` | Tab 5 — Charges |

---

## Tab 1: योजना (Scheme)

### Fields

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | जीएल हेड क्र. | GL Head No. | Textbox | Yes | Numeric. Validation alert: value must be ≤ 99 |
| 2 | योजना नाव | Scheme Name | Textbox | Yes | — |
| 3 | ओपन एंडेड | Open Ended | Radio Button | No | Default selected. Mutually exclusive with क्लोज एंडेड |
| 4 | क्लोज एंडेड | Close Ended | Radio Button | No | — |
| 5 | फक्त सदस्यांना परवानगी द्या | Allow Only Members | Checkbox | No | Default unchecked |
| 6 | सरळ व्याज | Simple Interest | Radio Button | No | Part of व्याज प्रकार group |
| 7 | चक्रवाढ व्याज | Compound Interest | Radio Button | No | Default selected |
| 8 | मासिक | Monthly | Radio Button | No | Compound frequency; default selected |
| 9 | त्रैमासिक | Quarterly | Radio Button | No | Compound frequency |
| 10 | अर्धवार्षिक | Half-Yearly | Radio Button | No | Compound frequency |
| 11 | वार्षिक | Yearly | Radio Button | No | Compound frequency |
| 12 | दैनिक | Daily | Radio Button | No | व्याज मोजणी group |
| 13 | पाक्षिक | Fortnightly | Radio Button | No | व्याज मोजणी group |
| 14 | मासिक | Monthly | Radio Button | No | व्याज मोजणी group; default selected |
| 15 | गणना दिवस (महिन्याच्या शेवटी 31 दिवस सेट करा) | Calculation Day (set 31 at month end) | Dropdown | Yes | Shown value: `31`. Capture full day list (1–31) |
| 16 | तपशील | Details | Textbox | No | — |
| 17 | स्थिती | Status | Dropdown | Yes | Shown value: `चालू` (Active), `बंद`, `स्थगित`, `कालबाह्य` |
| 18 | किमान शिल्लक (रु.) | Minimum Balance (Rs.) | Textbox | No | Currency |
| 19 | गुणक | Multiplier | Textbox | No | — |
| 20 | एका आठवड्यात एकूण नावे व्यवहार संख्या (कमाल संख्या) | Total Debit Transaction Count per Week (Max) | Textbox | No | — |
| 21 | एका आठवड्यातील नावे व्यवहार रक्कम मर्यादा (कमाल रक्कम) | Debit Transaction Amount Limit per Week (Max) | Textbox | No | Currency |

### Footer Note

| Marathi | English |
| :--- | :--- |
| टीप :- आठवड्याचा विचार रविवार ते शनिवार आहे. | Note: Week is considered Sunday to Saturday. |

### Validation Alert (from screenshot)

| Marathi Message | English Message |
| :--- | :--- |
| कृपया 99 क्रमांकापेक्षा कमी किंवा समान योजना क्रमांक प्रविष्ट करा. *जीएल हेड क्र. | Please enter a scheme number less than or equal to 99. *GL Head No. |

---

## Tab 2: कालावधी (महिने) — Duration (Months)

### Input Row (add to grid)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | कालावधी | Duration | Textbox | Yes | — |
| 2 | कालावधी प्रकार | Duration Type | Dropdown | Yes | Shown: `महिने` (Months). Capture other types (Days, Years, etc.) |
| 3 | व्याज दर (द.सा.द.शे.) | Interest Rate (p.a. %) | Textbox | Yes | Percentage |
| — | + टाका | + Add | Button | — | Adds row to grid |

### Grid Columns

| Marathi | English |
| :--- | :--- |
| निवडा | Select |
| अनु. क्र | Sr. No. |
| कालावधी | Duration |
| व्याज दर | Interest Rate |

**Grid action:** `काढा` (Remove) button — deletes selected rows.

### Additional Fields (below grid)

| # | Marathi Label | English Label | Type | Required | Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | बीन व्याजी (महिने) | Interest-Free (Months) | Checkbox + Textbox | No | Checkbox enables months textbox |
| 2 | मुदतपूर्व बंद दंड दर (द.सा.द.शे.) | Premature Closure Penalty Rate (p.a. %) | Checkbox + 2 Textboxes | No | Sub-fields: `(% वार्षिक)` (% Annual), `महिने` (Months) |
| 3 | व्याज आकारणी नावे व्यवहार करताना | Charge Interest on Debit Transaction | Checkbox | No | — |

---

## Tab 3: व्याज पोस्टींग — Interest Posting

### Input Row

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | व्याज पोस्टिंग दिवस | Interest Posting Day | Dropdown | Yes | List of month date like (1,2,3,...31)  |
| 2 | व्याज पोस्टिंग महिना | Interest Posting Month | Dropdown | Yes | List of month name like (January, Feb... December) |
| — | + टाका | + Add | Button | — | — |

### Grid Columns

| Marathi | English |
| :--- | :--- |
| निवडा | Select |
| अ. क्र. | Sr. No. |
| पोस्टिंग दिनांक | Posting Date |

### Navigation Buttons

| Marathi | English | Type |
| :--- | :--- | :--- |
| मागे | Back | Button |
| पुढे | Next | Button |

---

## Tab 4: खाते बंद करा — Close Account

> Screenshots 4.1 and 4.2 are two scroll sections of the same tab.

### Section A: मुदत पूर्वी (Before Maturity)

#### Input Row

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | कालावधी | Duration | Textbox | No | — |
| 2 | कालावधी प्रकार | Duration Type | Dropdown | No | Shown: `महिने` (Months). |
| 3 | व्याज दर (द.सा.द.शे.) | Interest Rate (p.a. %) | Textbox | No | — |
| — | + टाका | + Add | Button | — | — |

#### Grid Columns

| Marathi | English |
| :--- | :--- |
| निवडा | Select |
| अ.क्र. | Sr. No. |
| कालावधी | Duration |
| व्याज दर (द.सा.द.शे.) | Interest Rate (p.a.) |

### Section B: Commission Deduction

| # | Marathi Label | English Label | Type | Required | Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | मुदतपूर्व कमिशन कपात | Premature Commission Deduction | Checkbox | No | — |
| 2 | कमिशन कपात प्रत्येक नावे व्यवहार करताना | Commission Deduction on Each Debit Transaction | Checkbox | No | — |
| 3 | खाते धारक | Account Holder | Radio Button | No | Default selected; group: कमिशन कपात पासून |
| 4 | एजंट | Agent | Radio Button | No | — |

### Section C: मुदतपूर्व कमिशन कपात दर (Premature Commission Deduction Rate)

#### Input Row

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | कालावधी | Duration | Textbox | No | — |
| 2 | कालावधी प्रकार | Duration Type | Dropdown | No | Placeholder: `निवडा` (Select). Options are Days & Months |
| 3 | व्याज दर (द.सा.द.शे.) | Interest Rate (p.a. %) | Textbox | No | — |
| — | + टाका | + Add | Button | — | — |

#### Grid Columns

| Marathi | English |
| :--- | :--- |
| निवडा | Select |
| अ.क्र. | Sr. No. |
| कालावधी | Duration |
| व्याज दर (द.सा.द.शे.) | Interest Rate (p.a.) |

### Section D: मुदत नंतर (After Maturity)

| # | Marathi Label | English Label | Type | Required | Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | व्याज दर (द.सा.द.शे.) | Interest Rate (p.a. %) | Textbox | No | Appears disabled in screenshot |
| 2 | मुदती नंतरचा लॉकिंग कालावधी | Locking Period After Maturity | Textbox | No | Appears disabled |
| 3 | कालावधी प्रकार | Duration Type | Dropdown | No | Placeholder: `निवडा`. Days, Months, Years Values. Appears disabled |

---

## Tab 5: चार्जेस — Charges

### Fields

| # | Marathi Label | English Label | Type | Required | Dropdown Values |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | चार्जेस | Charges | Dropdown | No | See table below |

#### Charges Dropdown Values

| Marathi | English |
| :--- | :--- |
| निवडा | Select (placeholder) |
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

### Actions

| Marathi | English | Type |
| :--- | :--- | :--- |
| काढा | Remove | Button |
| Save (floppy icon) | Save | Button |

Confirm whether selecting a charge requires a separate Add action.

---

## Mockup

| Property | Value |
| :--- | :--- |
| HTML mockup | [mockups/settings/schemes/daily-new-scheme-screen/index.html](../../mockups/settings/schemes/daily-new-scheme-screen/index.html) |
| Review guide | [mockups/settings/schemes/daily-new-scheme-screen/README.md](../../mockups/settings/schemes/daily-new-scheme-screen/README.md) |
| Stack | Tailwind CSS v4 (CDN), Marathi labels only |
| Status | Draft — pending bank user review |

---

## Related Documents

- [overview.md](overview.md)
- [savings-new-scheme-screen.md](savings-new-scheme-screen.md)
- [fixed-deposit-new-scheme-screen.md](fixed-deposit-new-scheme-screen.md)
- [recurring-new-scheme-screen.md](recurring-new-scheme-screen.md)
- [changelog.md](changelog.md)
