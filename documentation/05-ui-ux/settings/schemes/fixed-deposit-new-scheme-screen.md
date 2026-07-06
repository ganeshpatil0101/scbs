# Screen Spec — Fixed Deposit New Scheme (मुदत ठेव > नवीन योजना)

> **Superseded (2026-07-05):** Consolidated into [new-scheme-screen.md](new-scheme-screen.md) (Scheme Type = मुदत ठेव). Retained for field reference only.

## Purpose

UI specification for creating a new **Fixed Deposit / Term Deposit (मुदत ठेव)** scheme. Intended for AI agents implementing this screen.

## Scope

Single screen with **6 tabs**. Screenshots 2.2, 5.2, and 5.3 are scroll continuations within tabs 2 and 5.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | नवीन योजना | New Scheme |
| Breadcrumb | डॅशबोर्ड > सेटिंग्ज > मुदत ठेव > नवीन योजना | Dashboard > Settings > Fixed Deposit > New Scheme |
| Parent Module | मुदत ठेव | Fixed Deposit |
| Related Screens | [daily-new-scheme-screen.md](daily-new-scheme-screen.md), [savings-new-scheme-screen.md](savings-new-scheme-screen.md), [recurring-new-scheme-screen.md](recurring-new-scheme-screen.md) | — |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | योजना | Scheme |
| 2 | कालावधी | Duration |
| 3 | अतिरिक्त फायदे | Additional Benefits |
| 4 | व्याज पोस्टींग | Interest Posting |
| 5 | खाते बंद | Account Closing |
| 6 | चार्जेस | Charges |

## Reference Screenshots

| Screenshot File | Tab / Section |
| :--- | :--- |
| `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-मुदत ठेव-नवीन योजना-1.png` | Tab 1 — Scheme |
| `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-मुदत ठेव-नवीन योजना-2.1.png` | Tab 2 — Duration (top: input row) |
| `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-मुदत ठेव-नवीन योजना-2.2.png` | Tab 2 — Duration (bottom: benefits & interest rate) |
| `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-मुदत ठेव-नवीन योजना-3.png` | Tab 3 — Additional Benefits |
| `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-मुदत ठेव-नवीन योजना-4.png` | Tab 4 — Interest Posting |
| `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-मुदत ठेव-नवीन योजना-5.1.png` | Tab 5 — Account Closing (pre-maturity section) |
| `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-मुदत ठेव-नवीन योजना-5.2.png` | Tab 5 — Account Closing (commission section) |
| `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-मुदत ठेव-नवीन योजना-5.3.png` | Tab 5 — Account Closing (after-maturity & footer) |
| `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-मुदत ठेव-नवीन योजना-6.png` | Tab 6 — Charges |

---

## Tab 1: योजना (Scheme)

### Basic Fields

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | जीएल हेड क्र. | GL Head No. | Textbox | Yes | Shown: `163` |
| 2 | योजनेचे प्रकार | Scheme Type | Dropdown | Yes | Placeholder: `निवडा`. मुदत ठेव,दाम दुप्पट,कॅश सर्टिफिकेट,पेन्शन,ठेव कर्ज, Values |
| 3 | गुणक | Multiplier | Textbox | Yes | — |
| 4 | योजनेचे नाव | Scheme Name | Textbox | Yes | — |
| 5 | तपशील | Details | Textbox | No | — |
| 6 | पावती क्र. सिरीजची सुरूवात | Receipt No. Series Start | Textbox | Yes | — |
| 7 | पावती क्र. सिरीज नंबर | Receipt No. Series Number | Textbox | Yes | — |
| 8 | स्थिती | Status | Dropdown | Yes | Shown: `चालू` (Active) .`बंद` (Inactive), `स्थगित` (Stop) |
| 9 | ओपन एंडेड | Open Ended | Radio Button | No | Default selected |
| 10 | क्लोज एंडेड | Close Ended | Radio Button | No | — |
| 11 | फक्त सदस्यांना परवानगी द्या | Allow Only Members | Checkbox | No | — |

### Section: व्याज प्रकार (Interest Type)

| # | Marathi Label | English Label | Type | Notes |
| :---: | :--- | :--- | :--- | :--- |
| 1 | सरळ व्याज | Simple Interest | Radio Button | Default selected |
| 2 | चक्रवाढ व्याज | Compound Interest | Radio Button | — |

### Section: चक्रवाढ व्याज (Compound Interest Frequency)

> Disabled when Simple Interest is selected.

| Marathi | English | Type |
| :--- | :--- | :--- |
| मासिक | Monthly | Radio Button |
| त्रैमासिक | Quarterly | Radio Button |
| अर्धवार्षिक | Half-Yearly | Radio Button |
| वार्षिक | Yearly | Radio Button |

### Section: अॅडव्हान्स सेटिंग (Advance Setting)

| # | Marathi Label | English Label | Type | Notes |
| :---: | :--- | :--- | :--- | :--- |
| 1 | ऑटो रिन्यूअल | Auto Renewal | Checkbox | Enables dependent fields when checked |
| 2 | ऑटो नूतनीकरण प्रतीक्षा कालावधी (दिवस) | Auto Renewal Waiting Period (Days) | Textbox | Disabled until Auto Renewal checked |
| 3 | नूतनीकरण व्यवहारावर मुद्दल प्रभाव लागू | Apply Principal Effect on Renewal Transaction | Checkbox | — |
| 4 | नूतनीकरण लॉकिंग कालावधी (दिवस) | Renewal Locking Period (Days) | Textbox | Disabled until Auto Renewal checked |
| 5 | नूतनीकरण आजपासून | Renewal From Today | Checkbox | — |
| 6 | मुदती नंतरचा रिन्यूअल कालावधी (दिवस) | Renewal Period After Maturity (Days) | Textbox | Disabled until Auto Renewal checked |
| 7 | मुदती नंतरचा रिन्यूअल व्याज दर (द.सा.द.शे.) | Renewal Interest Rate After Maturity (p.a. %) | Textbox | Disabled until Auto Renewal checked |
| 8 | ब्रोकन पिरियड व्याज | Broken Period Interest | Checkbox | — |
| 9 | ३६० बेसिस | 360 Basis | Radio Button | Broken period basis group |
| 10 | ३६५ बेसिस | 365 Basis | Radio Button | — |

### Footer Field

| Marathi Label | English Label | Type | Required |
| :--- | :--- | :--- | :---: |
| किमान एफडी रक्कम | Minimum FD Amount | Textbox | No |

---

## Tab 2: कालावधी (Duration)

> Screenshots 2.1 (top) and 2.2 (bottom) are one scrollable tab.

### Input Row

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | डिस्काउंटेड | Discounted | Checkbox | No | — |
| 2 | कालावधी | Duration | Textbox | Yes | — |
| 3 | कालावधी प्रकार | Duration Type | Dropdown | Yes | Placeholder: `निवडा`. Values are Days/Months |
| 4 | मुदत रक्कम | Maturity Amount | Textbox | Yes | — |
| 5 | व्याज दर (द.सा.द.शे.) | Interest Rate (p.a. %) | Textbox | Yes | — |
| — | + टाका | + Add | Button | — | — |

### Formula Display (informational)

| Marathi | English |
| :--- | :--- |
| i = व्याज दर आणि डिस्काउंटेड व्याज दर | i = Interest Rate and Discounted Interest Rate |
| `(( i / 4 ) / ( ( ( 1 + i / 1200 ) ^ 2 ) + ( 1 + i / 1200 ) + 1 ) * 12 )` | Discounted rate formula |

### Grid Columns

| Marathi | English |
| :--- | :--- |
| निवडा | Select |
| अनु. क्र | Sr. No. |
| कालावधी | Duration |
| मुदत रक्कम | Maturity Amount |
| व्याज दर | Interest Rate |

**Grid action:** `काढा` (Remove)

### Section: बेनिफिट्स (Benefits) — bottom of Duration tab

| # | Marathi Label | English Label | Type |
| :---: | :--- | :--- | :--- |
| 1 | अपंग | Disabled | Checkbox |
| 2 | दुसरी संस्था | Other Institution | Checkbox |
| 3 | महिला | Female | Checkbox |
| 4 | कर्मचारी | Employee | Checkbox |
| 5 | विधवा | Widow | Checkbox |
| 6 | स्वातंत्र्य सैनिक | Freedom Fighter | Checkbox |
| 7 | ज्येष्ठ नागरिक | Senior Citizen | Checkbox |
| 8 | अति ज्येष्ठ नागरिक | Very Senior Citizen | Checkbox |

### Benefit Interest Rate

| Marathi Label | English Label | Type |
| :--- | :--- | :--- |
| व्याज दर (द.सा.द.शे.) | Interest Rate (p.a. %) | Textbox |

### Navigation

| Marathi | English |
| :--- | :--- |
| मागे | Back |
| पुढे | Next |

---

## Tab 3: अतिरिक्त फायदे (Additional Benefits)

### Input Row

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | खाते प्रकार | Account Type | Dropdown | Yes | See values below |
| 2 | कालावधी | Duration | Textbox | Yes | — |
| 3 | कालावधी प्रकार | Duration Type | Dropdown | Yes | Placeholder: `निवडा`. values are Days/Months/Years |
| 4 | व्याज दर (द.सा.द.शे.) | Interest Rate (p.a. %) | Textbox | Yes | — |

### Account Type Dropdown Values

| Marathi | English |
| :--- | :--- |
| निवडा | Select |
| सामान्य खाते | General Account |
| ज्येष्ठ नागरिक खाते | Senior Citizen Account |
| महिला | Women |
| विधवा | Widow |
| अपंग | Disabled |
| दुसरी संस्था | Other Institution |
| नोकर | Employee |
| स्वातंत्र्यसैनिक | Freedom Fighter |
| अति ज्येष्ठ नागरिक | Super Senior Citizen |

### Grid Columns

| Marathi | English |
| :--- | :--- |
| कालावधी | Duration |
| व्याज दर | Interest Rate |
| खाते प्रकार | Account Type |

**Grid action:** `काढा` (Remove)

---

## Tab 4: व्याज पोस्टिंग (Interest Posting)

### Input Row

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | व्याज पोस्टिंग दिवस | Interest Posting Day | Dropdown | Yes | values(1,2,...31) |
| 2 | व्याज पोस्टिंग महिना | Interest Posting Month | Dropdown | Yes |  Values(January, Feb.....December) |
| — | + टाका | + Add | Button | — | — |

### Grid Columns

| Marathi | English |
| :--- | :--- |
| निवडा | Select |
| अ.क्र. | Sr. No. |
| पोस्टिंग दिनांक | Posting Date |

**Grid action:** `काढा` (Remove)

---

## Tab 5: खाते बंद (Account Closing)

> Screenshots 5.1, 5.2, 5.3 are scroll sections of one tab.

### Section A: मुदत पूर्वी (Before Maturity)

#### Input Row

| # | Marathi Label | English Label | Type | Values / Notes |
| :---: | :--- | :--- | :--- | :--- |
| 1 | कालावधी | Duration | Textbox | — |
| 2 | कालावधी प्रकार | Duration Type | Dropdown | `निवडा`, `दिवस` (Days), `महिने` (Months) |
| 3 | व्याज दर (द.सा.द.शे.) | Interest Rate (p.a. %) | Textbox | — |
| — | + टाका | + Add | Button | — |

#### Grid Columns

| Marathi | English |
| :--- | :--- |
| निवडा | Select |
| अ.क्र. | Sr. No. |
| कालावधी | Duration |
| व्याज दर (द.सा.द.शे.) | Interest Rate (p.a.) |

### Section B: Commission Deduction

| # | Marathi Label | English Label | Type | Notes |
| :---: | :--- | :--- | :--- | :--- |
| 1 | वर्तमान व्याज दराप्रमाणे गणना करा | Calculate as per Current Interest Rate | Checkbox | — |
| 2 | खाते धारक | Account Holder | Radio Button | Default; group: कमिशन कपात पासून |
| 3 | एजंट | Agent | Radio Button | — |
| 4 | मुदत पूर्वी कमिशन कपात, ठेव कालावधी प्रमाणे | Pre-Maturity Commission Deduction per Deposit Period | Checkbox | — |

#### Commission Rate Input Row

| # | Marathi Label | English Label | Type | Values / Notes |
| :---: | :--- | :--- | :--- | :--- |
| 1 | कालावधी | Duration | Textbox | — |
| 2 | कालावधी प्रकार | Duration Type | Dropdown | Placeholder: `निवडा`. Values Days/Months|
| 3 | व्याज दर (द.सा.द.शे.) | Interest Rate (p.a. %) | Textbox | — |
| — | + टाका | + Add | Button | — |

#### Commission Grid Columns

| Marathi | English |
| :--- | :--- |
| निवडा | Select |
| अ.क्र. | Sr. No. |
| कालावधी | Duration |
| कालावधी (ठेव) | Duration (Deposit) |
| व्याज दर (द.सा.द.शे.) | Interest Rate (p.a.) |

### Section C: मुदत नंतर (After Maturity)

| # | Marathi Label | English Label | Type | Notes |
| :---: | :--- | :--- | :--- | :--- |
| 1 | मुदती नंतर अनेक नूतनीकरण व्याज चक्रवाढ न करता | Multiple Renewals After Maturity Without Compounding Interest | Checkbox | — |
| 2 | व्याज दर (द.सा.द.शे.) | Interest Rate (p.a. %) | Textbox | — |
| 3 | मुदती नंतरचा लॉकिंग कालावधी (दिवस) | Locking Period After Maturity (Days) | Textbox | — |
| 4 | मुदती नंतरचा व्याजदर फक्त खाते बंदला लागू | Post-Maturity Interest Rate Applies Only on Account Closure | Checkbox | — |

### Section D: परतीची रक्कम (Return Amount)

| Marathi | English | Type | Default |
| :--- | :--- | :--- | :--- |
| मॅच्युरिटी रक्कमेप्रमाणे | As per Maturity Amount | Radio Button | Selected |
| व्याज गणने प्रमाणे | As per Interest Calculation | Radio Button | — |

### Section E: व्याज ब्रेक/बंद वेळी (At Interest Break / Closure)

| Marathi | English | Type | Default |
| :--- | :--- | :--- | :--- |
| पोस्टिंग व्यवहार | Posting Transaction | Radio Button | Selected |
| पोस्टिंग शिवाय व्यवहार | Transaction Without Posting | Radio Button | — |

### Footer Actions

| Marathi | English | Type |
| :--- | :--- | :--- |
| मागे | Back | Button |
| पुढे | Next | Button |
| पूर्ण | Complete / Save | Button |
| पूर्ववत | Reset | Button |

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

**Grid action:** `काढा` (Remove)

---

## Mockup

> **Superseded mockup.** Use [new-scheme-screen mockup](../../mockups/settings/schemes/new-scheme-screen/index.html) (Scheme Type = मुदत ठेव) instead.

| Property | Value |
| :--- | :--- |
| HTML mockup | ~~mockups/settings/schemes/fixed-deposit-new-scheme-screen/~~ → [new-scheme-screen](../../mockups/settings/schemes/new-scheme-screen/index.html) |
| Stack | Tailwind CSS v4 (CDN), Marathi labels only |
| Status | Draft — pending bank user review |

---

## Related Documents

- [overview.md](overview.md)
- [daily-new-scheme-screen.md](daily-new-scheme-screen.md)
- [savings-new-scheme-screen.md](savings-new-scheme-screen.md)
- [recurring-new-scheme-screen.md](recurring-new-scheme-screen.md)
- [changelog.md](changelog.md)
