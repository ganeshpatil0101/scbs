# Screen Spec — Bank Management (बँक > बँक व्यवस्थापन)

> **Consolidates:** [bank-register-screen.md](bank-register-screen.md) + [new-bank-screen.md](new-bank-screen.md) + [check-register-screen.md](check-register-screen.md)

## Purpose

Single operational screen for society bank accounts and cheque processing. Each tab combines **list, create, and update** on one page — filter and grid at top; form or action panel below (or beside on desktop). Replaces three separate menu entries from the legacy app.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | बँक व्यवस्थापन | Bank Management |
| Breadcrumb | डॅशबोर्ड > बँक > बँक व्यवस्थापन | Dashboard > Bank > Bank Management |
| Parent Module | बँक | Bank |

**Auto-fill (header):** `संघटना` (Organization) — read-only `Label` from tenant session; not repeated in filter bars.

## Tabs

| # | Marathi Tab | English Tab | Replaces |
| :---: | :--- | :--- | :--- |
| 1 | बँक खाते | Bank Accounts | Bank Register + New Bank |
| 2 | चेक रजिस्टर | Cheque Register | Cheque Register |

## Page Layout (both tabs)

| Zone | Purpose |
| :--- | :--- |
| **A — Filters** | Primary search; optional **अतिरिक्त शोध पर्याय** on Tab 2 |
| **B — List grid** | Search results; row select drives update mode |
| **C — Form / action panel** | Create (empty form), Update (row loaded), or cheque processing controls |

**Mode rules:**

| Mode | Trigger | Panel C |
| :--- | :--- | :--- |
| List only | Initial load; `रद्द करा` | Collapsed or read-only placeholder |
| Create | `+ नवीन` (Tab 1) | Empty form; Status = `चालू` read-only |
| Update | Grid row select or `तपशील` | Form populated (Tab 1) or cheque actions enabled (Tab 2) |

---

## Tab 1: बँक खाते (Bank Accounts)

**Reference screenshots:** `screenshots/Bank/डॅशबोर्ड-बँक-बँक रजिस्टर.png`, `screenshots/Bank/डॅशबोर्ड-बँक-नवीन बँक.png`

### Section: प्राथमिक शोध (Primary Search)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा निवडा | Select Branch | Autocomplete | No | Enter resolves by ID or name; e.g. `1 — Branch 1` |
| 2 | खाते प्रकार | Account Type | Dropdown | No | Default: `सर्व` (All) |
| 3 | स्थिती निवडा | Select Status | Dropdown | No | Default: `चालू` (Active) |

**Actions:** `दाखवा` (Show), `+ नवीन` (New — switches Panel C to Create mode).

### Section: Results Grid (List)

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | अनु. क्र. | Sr. No. |
| 3 | जी.एल. हेड | G.L. Head |
| 4 | बँकेचे नाव | Bank Name |
| 5 | शाखा | Branch |
| 6 | बँक खाते क्र. | Bank Account No. |
| 7 | खाते दिनांक | Account Date |
| 8 | खाते प्रकार | Account Type |
| 9 | शिल्लक | Balance |

**Grid actions:** `तपशील` (loads Update in Panel C), `निर्यात करा`, `काढा` (Delete — confirm dialog).

**Row select:** Single row loads account into Panel C (Update mode).

### Section: खाते तपशील / नवीन खाते (Account Detail — Create / Update)

Visible when Create or Update mode active.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 4 | जी.एल. निवडा | Select GL | Autocomplete | Yes | Enter resolves by ID or name |
| 5 | बँकेचे नाव | Bank Name | Textbox | Yes | — |
| 6 | बँक खाते क्र. | Bank Account No. | Textbox | Yes | — |
| 7 | शाखा | Branch | Textbox | Yes | External bank branch |
| 8 | पत्ता | Address | Textbox | Yes | — |
| 9 | खाते प्रकार | Account Type | Dropdown | Yes | `TODO` — master values |
| 10 | खाते चालू दिनांक | Account Opening Date | Date | Yes | Default: today on Create |
| 11 | स्थिती | Status | Label / Dropdown | — | Create: read-only `चालू`. Update: editable Dropdown (`TODO`) |
| 12 | आय.एफ.एस.सी. कोड | IFSC Code | Textbox | No | — |

### Section: प्रगत सेटिंग्ज (Advanced Settings)

> Collapsed by default on Tab 1 form.

| # | Marathi Label | English Label | Type | Required | Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 13 | शाखांतर्गत व्यवहार हवा आहे | Internal Branch Transaction Required | Checkbox | No | — |
| 14 | किमान शिल्लक | Minimum Balance | Textbox | No | — |
| 15 | फंड ट्रान्सफरसाठी हवी | Required for Fund Transfer | Checkbox | No | — |

**Panel actions:** `जतन करा` (Save — Create or Update), `रद्द करा` (Cancel — collapse Panel C).

---

## Tab 2: चेक रजिस्टर (Cheque Register)

**Reference screenshot:** `screenshots/Bank/डॅशबोर्ड-बँक-चेक रजिस्टर.png`

**Create note:** New cheques are recorded via [../accounting/jama-screen.md](../accounting/jama-screen.md) and [../accounting/nave-screen.md](../accounting/nave-screen.md). This tab provides **list + update** (clearance, return processing) only.

### Section: प्राथमिक शोध (Primary Search)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 16 | व्यवहार प्रकार | Transaction Type | Radio | No | `सर्व`, `जमा`, `नावे` |
| 17 | शाखा निवडा | Select Branch | Autocomplete | Yes | Enter resolves by ID or name |
| 18 | बँक निवडा | Select Bank | Dropdown | No | From Bank Master — e.g. `बँक ऑफ इंडिया` |
| 19 | या दिनांकापासून | From Date | Date | No | — |
| 20 | या दिनांकापर्यंत | To Date | Date | No | — |
| 21 | स्थिती | Status | Radio | No | `सर्व`, `वटवलेले`, `न वटवलेले`, `चेक रिटर्न` |

**Link:** `अतिरिक्त शोध पर्याय` (collapsed by default).

**Action:** `दाखवा`.

### Section: अतिरिक्त शोध (Additional Search)

> Visible when **अतिरिक्त शोध पर्याय** expanded.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 22 | रक्कम (पासून) | Amount From | Textbox | No | — |
| 23 | रक्कम (पर्यंत) | Amount To | Textbox | No | — |
| 24 | ग्राहक क्र. | Customer No. | Textbox | No | — |
| 25 | चेक क्र. (पासून) | Cheque No. From | Textbox | No | — |
| 26 | मंजुरी दिनांक (पासून) | Approval Date From | Date | No | — |
| 27 | मंजुरी दिनांक (पर्यंत) | Approval Date To | Date | No | — |
| 28 | बँक पद्धत | Bank Method | Dropdown | No | `TODO` |

### Section: Results Grid (List)

**Select all:** `सर्व निवडा`. **Grid action:** `निर्यात`.

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | अनु. क्र. | Sr. No. |
| 3 | बँक | Bank |
| 4 | रक्कम | Amount |
| 5 | इश्यु दिनांक | Issue Date |
| 6 | जमा / नावे | Credit / Debit |
| 7 | चेक क्र. | Cheque No. |
| 8 | क्लिअरन्स दिनांक | Clearance Date |
| 9 | तपशील | Details |
| 10 | ड्रॉन ऑन बँक | Drawn on Bank |
| 11 | ड्रॉन ऑन शाखा | Drawn on Branch |
| 12 | च्या कारणास्तव | Reason |

**Summary row:** `एकूण` (Total amount).

### Section: चेक प्रक्रिया (Cheque Processing — Update)

> **Visible:** When one or more grid rows selected.

| # | Marathi Label | English Label | Type | Required | Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 29 | चेक रिटर्न शुल्क | Cheque Return Fee | Textbox | No | Required when action = Cheque Return |

**Actions:** `चेक रिटर्न`, `पूर्ण`, `पूर्ववत`.

---

## Screen Actions (global)

| Button | Marathi | English | Tab |
| :--- | :--- | :--- | :---: |
| Save | जतन करा | Save | 1 |
| Cancel | रद्द करा | Cancel | 1 |
| New | + नवीन | New | 1 |
| Show | दाखवा | Show | 1, 2 |
| Complete | पूर्ण | Complete | 2 |
| Revert | पूर्ववत | Revert | 2 |

---

## Mockup

| Property | Value |
| :--- | :--- |
| HTML mockup | [mockups/bank/bank-management-screen/index.html](../mockups/bank/bank-management-screen/index.html) |
| Review guide | [mockups/bank/bank-management-screen/README.md](../mockups/bank/bank-management-screen/README.md) |
| Stack | Tailwind CSS v4 (CDN), Marathi labels only |
| Status | Draft — pending bank user review |

---

## Related Documents

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
- [../accounting/jama-screen.md](../accounting/jama-screen.md)
- [../accounting/nave-screen.md](../accounting/nave-screen.md)
