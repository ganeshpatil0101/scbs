# Screen Spec — Recurring Interest Management (रिकरिंग > व्याज व्यवस्थापन)

> **Consolidates:** [manual-interest-provision-screen.md](manual-interest-provision-screen.md) + [manual-interest-assessment-screen.md](manual-interest-assessment-screen.md)

## Purpose

Single screen for bulk interest provision (accrual) and interest assessment (posting) on recurring deposit accounts. Shared filter and results grid; tab-specific primary action differs. Follows [../investment/bank-deposit-interest-management-screen.md](../investment/bank-deposit-interest-management-screen.md) pattern.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | व्याज व्यवस्थापन | Interest Management |
| Breadcrumb | डॅशबोर्ड > रिकरिंग > व्याज व्यवस्थापन | Dashboard > Recurring > Interest Management |
| Parent Module | रिकरिंग | Recurring |

## Tabs

| # | Marathi Tab | English Tab | Replaces | Primary action |
| :---: | :--- | :--- | :--- | :--- |
| 1 | व्याज तरतूद | Interest Provision | Manual Interest Provision | `तरतूद` |
| 2 | व्याज आकारणी | Interest Assessment | Manual Interest Assessment | `निश्चित` |

## Reference Screenshots

| File | Tab |
| :--- | :--- |
| `screenshots/रिकरिंग/डॅशबोर्ड_रिकरिंग_मॅन्युअल व्याज_तरतुद.png` | Tab 1 |
| `screenshots/रिकरिंग/डॅशबोर्ड_रिकरिंग_मॅन्युअल व्याज_आकारणी.png` | Tab 2 |

---

## Shared Filter Section (both tabs)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा निवडा | Select Branch | Autocomplete | Yes | e.g. `1 — Branch 1`. See [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |
| 2 | जी.एल. निवडा | Select GL | Autocomplete | Yes | e.g. `91 — FD` (Recurring). Enter resolves by ID or name |
| 3 | व्याज दिनांक | Interest Date | Label (read-only) | Yes | Auto-filled: last financial year-end date only (e.g. `31.03.2026`). System-provided; not a multi-value master list |
| 4 | ब्याज पोस्टींग दिनांक | Interest Posting Date | Date | Yes | User-editable post date |
| 5 | खाते क्र. (पासून) | Account No. (From) | Textbox | No | Range filter — not consolidated per entity-autocomplete exclusions |
| 6 | खाते क्र. (पर्यंत) | Account No. (To) | Textbox | No | Range filter end |

**Link:** `प्रगत शोध` (Advanced Search) — `TODO — not captured`.

**Action:** `व्याज आकारणी` (Interest Assessment / Calculate).

---

## Shared Results Grid (both tabs)

**Select all:** `सर्व निवडा`.

**Legend:** Pink — accounts in interest-free period (provision will be made).

| # | Marathi Column | English Column | Notes |
| :---: | :--- | :--- | :--- |
| 1 | निवडा | Select | — |
| 2 | अ.क्र. | Sr. No. | — |
| 3 | खाते क्र. | Account No. | — |
| 4 | खातेदार | Account Holder | — |
| 5 | खाते चालू दिनांक | Account Opening Date | — |
| 6 | शेवटची व्याज दिनांक | Last Interest Date | — |
| 7 | व्याज दर | Interest Rate | — |
| 8 | शिल्लक | Balance | — |
| 9 | तरतूद | Provision | — |
| 10 | व्याज | Interest | — |

**Summary:** एकूण शिल्लक, एकूण तरतूद, एकूण व्याज, एकूण व्याज + एकूण तरतूद.

---

## Tab 1: व्याज तरतूद (Interest Provision)

**Primary action:** `तरतूद` (Provision) — posts interest accrual for selected rows.

**Grid action:** `निर्यात` (Export).

**Workflow:** Staff runs provision at period-end before assessment posting.

---

## Tab 2: व्याज आकारणी (Interest Assessment)

**Primary action:** `निश्चित` (Confirm) — posts calculated interest to accounts.

**Footer:** `प्रोसीडिंग`, `परत`.

**Workflow:** Staff runs assessment after provision to finalize interest posting.

---

## Mockup

- [HTML mockup (Draft)](../mockups/recurring/recurring-interest-management-screen/) — Marathi layout for bank review

## Related Documents

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [../investment/bank-deposit-interest-management-screen.md](../investment/bank-deposit-interest-management-screen.md)
- [../loan/loan-interest-management-screen.md](../loan/loan-interest-management-screen.md)
- [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
