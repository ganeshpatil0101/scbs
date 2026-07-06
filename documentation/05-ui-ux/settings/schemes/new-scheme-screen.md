# Screen Spec — New Scheme (सेटिंग्ज > योजना > नवीन योजना)

> **Consolidates:** [daily-new-scheme-screen.md](daily-new-scheme-screen.md), [savings-new-scheme-screen.md](savings-new-scheme-screen.md), [fixed-deposit-new-scheme-screen.md](fixed-deposit-new-scheme-screen.md), [recurring-new-scheme-screen.md](recurring-new-scheme-screen.md), [loan-new-scheme-screen.md](loan-new-scheme-screen.md)

## Purpose

Unified wizard for creating any deposit or loan scheme. A **Scheme Type** selector at the top shows only tabs and fields relevant to the selected product — eliminating five near-duplicate screens.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | नवीन योजना | New Scheme |
| Breadcrumb | डॅशबोर्ड > सेटिंग्ज > योजना > नवीन योजना | Dashboard > Settings > Schemes > New Scheme |
| Parent Module | योजना | Schemes |

## Scheme Type Selector (always visible)

| # | Marathi Label | English Label | Type | Required | Values |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | योजना प्रकार | Scheme Type | Dropdown | Yes | `बचत` (Savings), `डेली` (Daily), `मुदत ठेव` (FD), `रिकरिंग` (Recurring), `कर्ज` (Loan) |

Changing Scheme Type resets wizard to Tab 1 and shows the tab set from the matrix below.

## Tab Visibility Matrix

| Tab (Marathi) | English | Savings | Daily | FD | Recurring | Loan |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: |
| योजना माहिती | Scheme Info | ✓ | ✓ | ✓ | ✓ | ✓ |
| कालावधी व दर | Duration & Rates | — | ✓ | ✓ | ✓ | ✓ |
| व्याज पोस्टिंग | Interest Posting | ✓ | ✓ | ✓ | ✓ | ✓ (as व्याज दिनांक) |
| खाते बंद | Account Closing | — | ✓ | ✓ | ✓ | — |
| चार्जेस | Charges | ✓ | ✓ | ✓ | ✓ | ✓ (as शुल्क/कपात) |
| कर्ज विशेष | Loan Specific | — | — | — | — | ✓ |
| प्रगत | Advanced | — | — | ✓ | ✓ | ✓ |

---

## Tab 1: योजना माहिती (Scheme Info) — all types

### Common fields (all scheme types)

Each scheme **binds to one GL Head** from the GL master (created via [GL Account Setup](../accounting/gl-account-setup-screen.md)). The lookup is a single Autocomplete — not auto-generated.

| # | Marathi Label | English Label | Type | Required | Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 2 | जी.एल. निवडा | Select GL | Autocomplete | Yes | Single control: ID + name. Options loaded dynamically from **GL master** ([entity-autocomplete-pattern.md](../../shared/entity-autocomplete-pattern.md)). Enter resolves by ID or name; displays `id — name`. Replaces legacy `जीएल हेड क्र.` textbox. **Daily (डेली):** only GL Heads with number ≤ 99 are eligible (validation on resolve). |
| 3 | योजनेचे नाव | Scheme Name | Textbox | Yes | — |
| 4 | स्थिती | Status | Dropdown | Yes | `चालू`, `बंद`, `स्थगित` (+ `कालबाह्य` for Daily) |
| 5 | फक्त सदस्यांना परवानगी द्या | Allow Only Members | Checkbox | No | All types |

### Type-specific fields on Tab 1

| Field | Visible when |
| :--- | :--- |
| Scheme Type dropdown (product subtype), Interest Rate, Interest Calculation radios | Savings — see [savings-new-scheme-screen.md](savings-new-scheme-screen.md) Tab 1 |
| Open/Close Ended, Interest Type, Compound frequency, Calculation Day, Min Balance, Multiplier | Daily, FD, Recurring — per legacy spec Tab 1 |
| Loan Type, Installment Type, Interest Calculation, First Installment Date Type | Loan — see [loan-new-scheme-screen.md](loan-new-scheme-screen.md) Tab 1 |

**Loan simplifications on Tab 1:**

- **Removed:** Category dropdown (Tab 2 field, not required).
- **Hidden until Credit Card:** Monthly Billing Cycle Day.
- **Moved to Advanced tab:** Loan Application System, Post Interest on Credit After Loan End, Moratorium interest adjustment.

---

## Tab 2: कालावधी व दर (Duration & Rates)

Uses shared component **`app-rate-duration-grid`**.

| Scheme | Source spec | Notes |
| :--- | :--- | :--- |
| Daily | [daily-new-scheme-screen.md](daily-new-scheme-screen.md) Tab 2 | Interest-free months, premature penalty below grid |
| FD | [fixed-deposit-new-scheme-screen.md](fixed-deposit-new-scheme-screen.md) Tab 2 | Benefits checkboxes at bottom — **one** Benefits section only |
| Recurring | [recurring-new-scheme-screen.md](recurring-new-scheme-screen.md) Tab 2 | Agent interest rate → Advanced |
| Loan | [loan-new-scheme-screen.md](loan-new-scheme-screen.md) Tab 2 | Penalty sections; DP formula → plain-language toggle + tooltip |

**FD simplification:** Additional Benefits tab (old Tab 3) **removed** — merged into Tab 2 Benefits section.

---

## Tab 3: व्याज पोस्टिंग (Interest Posting)

Uses shared component **`app-interest-posting-grid`**.

Identical pattern for Savings, Daily, FD, Recurring, Loan:

- Interest Posting Day (1–31) + Interest Posting Month → Add → grid
- Loan Tab 3 additional OIR options → **Advanced** subsection

---

## Tab 4: खाते बंद (Account Closing) — Daily, FD, Recurring only

Uses shared component **`app-rate-slab-editor`** for:

- Before-maturity penalty slabs
- Pre-maturity commission rate slabs

Source: respective legacy spec Account Close / Account Closing tab. After-maturity fields unchanged.

---

## Tab 5: चार्जेस (Charges) — all types

Uses shared component **`app-charges-select`**.

Same dropdown values on every product:

| Marathi | English |
| :--- | :--- |
| कर्जदार कल्याण निधी | Borrower Welfare Fund |
| पिग्मी कमिशन | Pigmy Commission |
| प्रोसेसिंग फी | Processing Fee |
| ब वर्ग सभासद फी | Class B Member Fee |
| स्टेशनरी फी | Stationery Fee |

Loan Tab 6 adds Deduction/Fee radio and %/Amount grid — see [loan-new-scheme-screen.md](loan-new-scheme-screen.md) Tab 6.

---

## Tab 6: कर्ज विशेष (Loan Specific) — Loan only

Combines legacy Loan tabs 4–5:

| Section | Source |
| :--- | :--- |
| जामीनदार (Guarantor) | Loan spec Tab 4 |
| सोने/ठेव तारण (Gold / Deposit Security) | Loan spec Tab 5 |

---

## Tab 7: प्रगत (Advanced) — FD, Recurring, Loan

Collapsed by default. Fields moved from default view per [ux-optimization.md](../ux-optimization.md):

| Scheme | Advanced fields |
| :--- | :--- |
| FD | Details, Receipt No. Series, Broken Period 360/365, Auto Renewal block |
| Recurring | Interest Rate Decimal Places, Agent Interest Rate, Compounding Without Posting, **Salary Payment tab** (full tab moved here) |
| Loan | Moratorium, Post-interest-after-end, Compound without capitalization, Loan Application System |
| Recurring Tab 7 Rebate | Remains as subsection under Advanced for Recurring |

---

## Shared Components Reference

| Component | Document |
| :--- | :--- |
| GL Head lookup | [../../shared/entity-autocomplete-pattern.md](../../shared/entity-autocomplete-pattern.md) — `app-entity-autocomplete` with `entityType: gl` |
| UI simplification patterns | [../../shared/ui-simplification-patterns.md](../../shared/ui-simplification-patterns.md) |
| Full field lists per legacy type | Superseded specs linked at top of this document |

## Actions (all tabs)

| Button | Marathi | English |
| :--- | :--- | :--- |
| Save | पूर्ण / जतन करा | Complete / Save |
| Reset | पूर्ववत / रीसेट | Reset |
| Back | मागे | Back |
| Next | पुढे | Next |

---

## Mockup

| Property | Value |
| :--- | :--- |
| HTML mockup | [mockups/settings/schemes/new-scheme-screen/index.html](../../mockups/settings/schemes/new-scheme-screen/index.html) |
| Review guide | [mockups/settings/schemes/new-scheme-screen/README.md](../../mockups/settings/schemes/new-scheme-screen/README.md) |
| Stack | Tailwind CSS v4 (CDN), Marathi labels only |
| Status | Draft — pending bank user review |

---

## Related Documents

- [overview.md](overview.md)
- [ux-optimization.md](../ux-optimization.md)
- [../../shared/ui-simplification-patterns.md](../../shared/ui-simplification-patterns.md)
- [changelog.md](changelog.md)
