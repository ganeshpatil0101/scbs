# Screen Spec — Savings New Scheme (बचत > नवीन योजना)

> **Superseded (2026-07-05):** Consolidated into [new-scheme-screen.md](new-scheme-screen.md) (Scheme Type = बचत). Retained for field reference only.

## Purpose

UI specification for creating a new **Savings (बचत)** scheme. Intended for AI agents implementing this screen.

## Scope

Single screen with **3 tabs**. Multiple screenshots cover different tabs.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | नवीन योजना | New Scheme |
| Breadcrumb | डॅशबोर्ड > सेटिंग्ज > बचत > नवीन योजना | Dashboard > Settings > Savings > New Scheme |
| Parent Module | बचत | Savings |
| Related Screens | [daily-new-scheme-screen.md](daily-new-scheme-screen.md), [fixed-deposit-new-scheme-screen.md](fixed-deposit-new-scheme-screen.md), [recurring-new-scheme-screen.md](recurring-new-scheme-screen.md) | — |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | सेव्हिंग योजना | Saving Scheme |
| 2 | व्याज पोस्टिंग | Interest Posting |
| 3 | चार्जेस | Charges |

## Reference Screenshots

| Screenshot File | Tab / Section |
| :--- | :--- |
| `screenshots/settings/बचत_नवीन_योजना.png` | Tab 1 — Saving Scheme |
| `screenshots/settings/बचत_नवीन_योजना_1.png` | Tab 2 — Interest Posting (input row only) |
| `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-बचत-नवीन योजना-2.png` | Tab 3 — Charges |

---

## Tab 1: सेव्हिंग योजना (Saving Scheme)

### Fields

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | जीएल हेड क्र. | GL Head No. | Textbox | Yes | Shown value: `163` |
| 2 | योजनेचे नाव | Scheme Name | Textbox | Yes | — |
| 3 | योजनेचे प्रकार | Scheme Type | Dropdown | Yes | See values below |
| 4 | व्याज दर (द.सा.द.शे.) | Interest Rate (p.a. %) | Textbox | Yes | — |
| 5 | फक्त सदस्यांना परवानगी द्या | Allow Only Members | Checkbox | No | Default unchecked |

### Scheme Type Dropdown Values

| Marathi | English |
| :--- | :--- |
| निवडा | Select (placeholder) |
| कायम ठेव | Permanent Deposit |
| सेव्हिंग | Saving |
| करंट | Current |
| लवचिक ठेव | Flexible Deposit |

### Section: व्याज आकारणी (Interest Calculation)

| # | Marathi Label | English Label | Type | Required | Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | दिवसात | In Days | Radio Button | Yes | Default selected |
| 2 | महिन्यात | In Months | Radio Button | No | — |
| 3 | महिन्याची सुरुवात | Start of Month | Dropdown | Yes | Disabled when "In Days" selected. Placeholder: `निवडा`.values(1,2,....31) Values when enabled |

### Navigation

| Marathi | English | Type |
| :--- | :--- | :--- |
| पुढे | Next | Button |

---

## Tab 2: व्याज पोस्टिंग (Interest Posting)

### Input Row

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | व्याज पोस्टिंग दिवस | Interest Posting Day | Dropdown | Yes | Placeholder: `निवडा`. values(1,2,...31) |
| 2 | व्याज पोस्टिंग महिना | Interest Posting Month | Dropdown | Yes | Placeholder: `निवडा`. values(January,Feb....December) |
| — | + टाका | + Add | Button | — | — |


---

## Tab 3: चार्जेस (Charges)

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

---

## Mockup

| Property | Value |
| :--- | :--- |
| HTML mockup | [mockups/settings/schemes/savings-new-scheme-screen/index.html](../../mockups/settings/schemes/savings-new-scheme-screen/index.html) |
| Review guide | [mockups/settings/schemes/savings-new-scheme-screen/README.md](../../mockups/settings/schemes/savings-new-scheme-screen/README.md) |
| Stack | Tailwind CSS v4 (CDN), Marathi labels only |
| Status | Draft — pending bank user review |

---

## Related Documents

- [overview.md](overview.md)
- [daily-new-scheme-screen.md](daily-new-scheme-screen.md)
- [fixed-deposit-new-scheme-screen.md](fixed-deposit-new-scheme-screen.md)
- [recurring-new-scheme-screen.md](recurring-new-scheme-screen.md)
- [changelog.md](changelog.md)
