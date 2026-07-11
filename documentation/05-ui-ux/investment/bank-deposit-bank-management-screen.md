# Screen Spec — Bank Deposit Bank Management (गुंतवणूक > बँक ठेव > बँक ठेव बँक व्यवस्थापन)

> **Consolidates:** [bank-deposit-bank-list-screen.md](bank-deposit-bank-list-screen.md) + [bank-deposit-new-bank-screen.md](bank-deposit-new-bank-screen.md)

## Purpose

Single screen for listing and maintaining investment bank G.L. head masters used by bank deposit accounts. Distinct from operational **बँक > बँक व्यवस्थापन** — see [../bank/bank-management-screen.md](../bank/bank-management-screen.md).

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | बँक ठेव बँक व्यवस्थापन | Bank Deposit Bank Management |
| Breadcrumb | डॅशबोर्ड > गुंतवणूक > बँक ठेव > बँक ठेव बँक व्यवस्थापन | Dashboard > Investment > Bank Deposit > Bank Deposit Bank Management |
| Parent Module | गुंतवणूक > बँक ठेव | Investment > Bank Deposit |

## Tabs

| # | Marathi Tab | English Tab | Replaces |
| :---: | :--- | :--- | :--- |
| 1 | बँक यादी | Bank List | Bank List |
| 2 | नवीन / संपादन बँक | New / Edit Bank | New Bank |

## Page Layout

| Zone | Purpose |
| :--- | :--- |
| **A — Filters** | Primary search on Tab 1 |
| **B — List grid** | Investment bank masters; row select drives Tab 2 Update mode |
| **C — Form panel** | Tab 2 Create or Update |

**Mode rules:**

| Mode | Trigger | Tab 2 |
| :--- | :--- | :--- |
| List only | Initial load on Tab 1 | — |
| Create | `+ नवीन` on Tab 1 | Empty form; GL Head = Auto-fill Label |
| Update | Grid row select or `तपशील` on Tab 1 | Form populated from selected row |

## Reference Screenshots

| File | Tab |
| :--- | :--- |
| `screenshots/गुंतवणूक/डॅशबोर्ड-गुंतवणूक-बँक ठेव-बँक यादी.png` | Tab 1 |
| `screenshots/गुंतवणूक/डॅशबोर्ड-गुंतवणूक-बँक ठेव-नवीन बँक.png` | Tab 2 |

---

## Tab 1: बँक यादी (Bank List)

### Section: प्राथमिक शोध (Primary Search)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | बँक निवडा | Select Bank | Autocomplete | No | Optional filter. Enter resolves by GL head ID or bank name; e.g. `167 — Bank Name`. See [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |

**Actions:** `दाखवा` (Show), `+ नवीन` (New — switches to Tab 2 Create mode).

### Section: Results Grid (List)

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | अनु. क्र. | Sr. No. |
| 3 | खाते क्र. | Account No. (G.L. code) |
| 4 | बँक नाव | Bank Name |

**Grid actions:** `तपशील` (loads Update on Tab 2).

**Row select:** Single row loads bank into Tab 2 (Update mode).

---

## Tab 2: नवीन / संपादन बँक (New / Edit Bank)

> **Visible:** When Create or Update mode active (navigated from Tab 1).

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 2 | जीएल हेड क्र. | G.L. Head No. | Label (read-only) | No | Auto-generated on Create. Shown after save; editable only when admin assigns pre-existing number on Update |
| 3 | बँकेचे नाव | Bank Name | Textbox | Yes | — |
| 4 | तपशील | Details | Textbox | No | — |
| 5 | बँक प्रकार | Bank Type | Dropdown | No | `इतर` (Other), `शेड्यूल्ड कमर्शियल बँक ठेव` (Scheduled Commercial Bank Deposit), `पोस्ट ऑफिस ठेव` (Post Office Deposit), `आर.बी.आय.` (RBI), `राज्य सहकारी बँक` (State Cooperative Bank), `जिल्हा सहकारी बँक` (District Cooperative Bank), `राष्ट्रीयकृत बँक` (Nationalized Bank), `प्रायव्हेट सहकारी बँक` (Private Cooperative Bank) |

**Panel actions:** `जतन करा` (Save — Create or Update), `रद्द करा` (Cancel — return to Tab 1), `पुन्हा टाका` (Reset — Create only).

---

## Cross-Domain Note

Operational society bank accounts (savings/current, cheque register) remain under [../bank/bank-management-screen.md](../bank/bank-management-screen.md). This screen registers **investment GL bank masters** only — used when opening bank deposit accounts via [bank-deposit-new-account-screen.md](bank-deposit-new-account-screen.md).

---

## Mockup

- [HTML mockup (Draft)](../mockups/investment/bank-deposit-bank-management-screen/) — Marathi layout for bank review

## Related Documents

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [bank-deposit-new-account-screen.md](bank-deposit-new-account-screen.md)
- [../bank/bank-management-screen.md](../bank/bank-management-screen.md)
- [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
