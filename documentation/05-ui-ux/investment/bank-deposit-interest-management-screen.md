# Screen Spec — Bank Deposit Interest Management (गुंतवणूक > बँक ठेव > व्याज व्यवस्थापन)

> **Consolidates:** [bank-deposit-interest-provision-screen.md](bank-deposit-interest-provision-screen.md) + [bank-deposit-interest-assessment-screen.md](bank-deposit-interest-assessment-screen.md)

## Purpose

Single screen for bulk interest provision (accrual) and interest assessment (posting) on bank deposit accounts. Shared filter and results grid; tab-specific primary action differs.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | व्याज व्यवस्थापन | Interest Management |
| Breadcrumb | डॅशबोर्ड > गुंतवणूक > बँक ठेव > व्याज व्यवस्थापन | Dashboard > Investment > Bank Deposit > Interest Management |
| Parent Module | गुंतवणूक > बँक ठेव | Investment > Bank Deposit |

## Tabs

| # | Marathi Tab | English Tab | Replaces | Primary action |
| :---: | :--- | :--- | :--- | :--- |
| 1 | व्याज तरतूद | Interest Provision | Interest Provision | `तरतूद` |
| 2 | व्याज आकारणी | Interest Assessment | Interest Assessment | `पोस्ट` |

## Reference Screenshots

| File | Tab |
| :--- | :--- |
| `screenshots/गुंतवणूक/डॅशबोर्ड-गुंतवणूक-बँक ठेव-व्याज तरतुद.png` | Tab 1 |
| `screenshots/गुंतवणूक/डॅशबोर्ड-गुंतवणूक-बँक ठेव-व्याज आकारणी.png` | Tab 2 |

---

## Shared Filter Section (both tabs)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा निवडा | Select Branch | Autocomplete | Yes | Enter resolves by ID or name; e.g. `1 — कोतोली मुख्य कार्यालय`. See [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |
| 2 | बँक निवडा | Select Bank | Autocomplete | Yes | Multi-select supported. Investment bank GL masters from [bank-deposit-bank-management-screen.md](bank-deposit-bank-management-screen.md) |
| 3 | पोस्ट दिनांक | Post Date | Date | Yes | — |
| 4 | खाते क्र. (पासून) | Account No. (From) | Textbox | No | Range filter start |
| 5 | खाते क्र. (पर्यंत) | Account No. (To) | Textbox | No | Range filter end |

**Removed:** Ambiguous lone `खाते` text filter from legacy assessment screen.

**Action:** `गणना करा` (Calculate).

---

## Shared Results Grid (both tabs)

**Select all:** `सर्व निवडा`.

| # | Marathi Column | English Column | Notes |
| :---: | :--- | :--- | :--- |
| 1 | निवडा | Select | — |
| 2 | अ. क्र. | Sr. No. | — |
| 3 | खाते क्रमांक | Account Number | — |
| 4 | खाते नाव | Account Name | — |
| 5 | प्रारंभ तारीख | Start Date | — |
| 6 | व्याज तारीख | Interest Date | — |
| 7 | व्याज दर | Interest Rate | — |
| 8 | शिल्लक | Balance | — |
| 9 | तरतूद | Provision | — |
| 10 | व्याज | Interest | — |
| 11 | टीडीएस (रु.) | TDS (Rs.) | Display-only; not editable before post |

**Summary:** एकूण शिल्लक, एकूण तरतूद, एकूण व्याज, एकूण टीडीएस.

**Shared action:** `पूर्ववत` (Revert).

---

## Tab 1: व्याज तरतूद (Interest Provision)

**Primary action:** `तरतूद` (Provision) — posts interest accrual for selected rows.

**Workflow:** Staff runs provision at period-end before assessment posting.

---

## Tab 2: व्याज आकारणी (Interest Assessment)

**Primary action:** `पोस्ट` (Post) — posts calculated interest to accounts.

**Workflow:** Staff runs assessment after provision to finalize interest posting.

---

## Mockup

- [HTML mockup (Draft)](../mockups/investment/bank-deposit-interest-management-screen/) — Marathi layout for bank review

## Related Documents

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [bank-deposit-new-account-screen.md](bank-deposit-new-account-screen.md)
- [../fixed-deposit/fd-manual-interest-calculation-screen.md](../fixed-deposit/fd-manual-interest-calculation-screen.md)
- [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
