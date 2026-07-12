# Screen Spec — Loan Interest Management (कर्ज > व्याज व्यवस्थापन)

> **Consolidates:** [loan-manual-interest-provision-screen.md](loan-manual-interest-provision-screen.md) + [loan-scheduled-interest-assessment-screen.md](loan-scheduled-interest-assessment-screen.md)

## Purpose

Single screen for bulk interest provision (accrual) and interest assessment (posting) on loan accounts. Shared filter and results grid; tab-specific primary action differs. Follows [../investment/bank-deposit-interest-management-screen.md](../investment/bank-deposit-interest-management-screen.md) pattern.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | व्याज व्यवस्थापन | Interest Management |
| Breadcrumb | डॅशबोर्ड > कर्ज > व्याज व्यवस्थापन | Dashboard > Loan > Interest Management |
| Parent Module | कर्ज | Loan |

## Tabs

| # | Marathi Tab | English Tab | Replaces | Primary action |
| :---: | :--- | :--- | :--- | :--- |
| 1 | व्याज तरतूद | Interest Provision | Manual Interest Provision | `तरतूद` |
| 2 | व्याज आकारणी | Interest Assessment | Scheduled Interest Assessment | `पोस्टिंग` |

## Reference Screenshots

| File | Tab |
| :--- | :--- |
| `screenshots/कर्ज/डॅशबोर्ड-कर्ज-मॅन्युअल व्याज-तरतूद-1-05-07.png` | Tab 1 |
| `screenshots/कर्ज/डॅशबोर्ड-कर्ज-मॅन्युअल व्याज-आकारणी-1-05-07.png` | Tab 2 |

---

## Shared Filter Section (both tabs)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा निवडा | Select Branch | Autocomplete | Yes | e.g. `1 — कोतोली मुख्य कार्यालय`. See [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |
| 2 | जी.एल. निवडा | Select G.L. | Autocomplete | Yes | e.g. `61 — जामीनकी कर्ज` |
| 3 | व्याज दिनांक निवडा | Select Interest Date | Dropdown | Yes | e.g. `31.03.2026`. Full list: `TODO` |
| 4 | व्याज पोस्ट दिनांक | Interest Post Date | Date | Yes | — |
| 5 | खाते क्र. (पासून) | Account No. (From) | Textbox | No | Range filter — not consolidated per entity-autocomplete exclusions |
| 6 | खाते क्र. (पर्यंत) | Account No. (To) | Textbox | No | Range filter end |

**Action:** `व्याज गणना करा` (Calculate Interest).

---

## Shared Results Grid (both tabs)

**Select all:** `सर्व निवडा`.

| # | Marathi Column | English Column | Notes |
| :---: | :--- | :--- | :--- |
| 1 | निवडा | Select | — |
| 2 | अ. क्र. | Sr. No. | — |
| 3 | खाते क्र. | Account No. | — |
| 4 | खाते धारकाचे नाव | Account Holder Name | — |
| 5 | चालू दिनांक | Open Date | — |
| 6 | अंतिम पोस्ट दिनांक | Last Post Date | — |
| 7 | कर्ज शिल्लक | Loan Balance | — |
| 8 | व्याज दर | Interest Rate | — |
| 9 | तरतूद | Provision | — |
| 10 | व्याज | Interest | Editable |
| 11 | दंड तरतूद | Penalty Provision | — |
| 12 | दंड व्याज | Penalty Interest | Editable |

**Summary:** एकूण तरतूद, एकूण व्याज, एकूण दंड तरतूद, एकूण दंड व्याज, एकूण शिल्लक.

---

## Tab 1: व्याज तरतूद (Interest Provision)

**Primary action:** `तरतूद` (Provision) — posts interest accrual for selected rows.

**Grid action:** `निश्चित करा` (Confirm).

**Secondary action:** `पुनश्चरचना करा` (Reconstitute).

**Workflow:** Staff runs provision at period-end before assessment posting.

---

## Tab 2: व्याज आकारणी (Interest Assessment)

**Primary action:** `पोस्टिंग` (Post) — posts calculated interest to accounts.

**Tab-specific filter:**

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 7 | — | — | Checkbox | No | `परिपक्व कर्जासाठी अखेर दिनांकापर्यंत व्याज गणना` (Interest calculation until end date for matured loans) |

**Link:** `अॅडव्हान्स शोध` (Advance Search).

**Grid action:** `डिनिवड करा` (Deselect).

**Secondary action:** `पुनरावलोकन करा` (Review).

**Workflow:** Staff runs assessment after provision to finalize interest posting.

---

## Mockup

- [HTML mockup (Draft)](../mockups/loan/loan-interest-management-screen/) — Marathi layout for bank review

## Related Documents

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [../investment/bank-deposit-interest-management-screen.md](../investment/bank-deposit-interest-management-screen.md)
- [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
