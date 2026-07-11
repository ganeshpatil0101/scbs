# Investment Module — UX Optimization Audit

Audit date: 2026-07-11. Applied: 2026-07-11. Domain: `documentation/05-ui-ux/investment/`.

Patterns applied: [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md), [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md).

Reference implementation: [../settings/ux-optimization.md](../settings/ux-optimization.md).

## Summary

| Metric | Before | After |
| :--- | :---: | :---: |
| Menu screens | 6 | 4 |
| Bank master CRUD | 2 | 1 (2 tabs) |
| Interest bulk ops | 2 | 1 (2 tabs) |
| Autocomplete migrations | 0 | 4 screens |
| Fields → Auto-fill | — | 10+ |
| Fields → Advanced | — | 4 |

## Consolidated Screen Map

| New / kept screen | Replaces | Document |
| :--- | :--- | :--- |
| बँक ठेव बँक व्यवस्थापन (Bank Deposit Bank Management) | New Bank + Bank List | [bank-deposit-bank-management-screen.md](bank-deposit-bank-management-screen.md) |
| व्याज व्यवस्थापन (Interest Management) | Interest Assessment + Interest Provision | [bank-deposit-interest-management-screen.md](bank-deposit-interest-management-screen.md) |
| नवीन खाते (New Account) | (field cleanup) | [bank-deposit-new-account-screen.md](bank-deposit-new-account-screen.md) |
| व्यवहार (Transaction) | (field cleanup) | [bank-deposit-transaction-screen.md](bank-deposit-transaction-screen.md) |

### Tab layout (Bank Management)

| Tab | Marathi | English | Replaces |
| :---: | :--- | :--- | :--- |
| 1 | बँक यादी | Bank List | bank-deposit-bank-list-screen.md |
| 2 | नवीन / संपादन बँक | New / Edit Bank | bank-deposit-new-bank-screen.md |

### Tab layout (Interest Management)

| Tab | Marathi | English | Primary action |
| :---: | :--- | :--- | :--- |
| 1 | व्याज तरतूद | Interest Provision | `तरतूद` |
| 2 | व्याज आकारणी | Interest Assessment | `पोस्ट` |

---

## Decisions Applied (2026-07-11)

| # | Decision |
| :---: | :--- |
| 1 | Merge New Bank + Bank List → Bank Deposit Bank Management (2 tabs). Do **not** merge with operational [bank-management-screen.md](../bank/bank-management-screen.md). |
| 2 | Merge Interest Provision + Interest Assessment → Interest Management (provision tab first, assessment second). |
| 3 | Keep New Account and Transaction as separate screens; field cleanup only. |
| 4 | Do not invent Account Register / inquiry screen — not in captured specs. |
| 5 | New Account field `खाते` → `खाते नाव` (Account Name). |
| 6 | GL Head No. on New Bank → Auto-fill Label on create. |
| 7 | Leave `TODO` dropdown values as scaffolded — do not invent master data. |

---

## Action Checklist (all applied)

### High priority

- [x] Consolidate New Bank + Bank List → bank-deposit-bank-management-screen.md
- [x] Consolidate Interest Assessment + Provision → bank-deposit-interest-management-screen.md
- [x] Bank / Branch / GL / Account Holder → Autocomplete on New Account, Transaction, Interest
- [x] New Account: Auto-fill account no., maturity dates/amounts, status, interest start date
- [x] Transaction Tab 1: Account Summary Panel for read-only balances
- [x] Transaction Tab 3: Account Holder Autocomplete (replaces search + select + account no.)
- [x] Interest: remove ambiguous `खाते` filter; clarify From/To account range
- [x] Superseded banners on four old specs

### Medium priority

- [x] New Account: पावती क्रमांक, व्याज प्रकार, व्याज गणना प्रकार, निधी → प्रगत सेटिंग्ज
- [x] Transaction Tab 2: conditional visibility when Transfer; cheque bank as TODO Autocomplete
- [x] Transaction Tab 4: note shared `app-ledger-tab`
- [x] Bank Management: cross-link to operational बँक व्यवस्थापन
- [x] Interest: TDS column display-only; multi-select bank retained

### Low priority

- [x] Cheque Tab 2: Drawn-on Bank/Branch simplified to Bank Autocomplete + branch textbox
- [x] Document upload action label standardized

---

## Open Gaps (TODO — not captured)

| Item | Handling |
| :--- | :--- |
| `निधी`, interest-transfer bank, cheque `बँक निवडा` values | Keep `TODO` in specs |
| Full `ठेव प्रकार` / `स्थिती` enums beyond samples | Keep examples; note gap |
| Account Register / inquiry screen | Not in captured set — add when screenshots available |
| Screenshots folder empty in repo | Specs remain source of truth |

---

## Deprecated Specs (reference only)

| Superseded spec | New spec |
| :--- | :--- |
| [bank-deposit-new-bank-screen.md](bank-deposit-new-bank-screen.md) | [bank-deposit-bank-management-screen.md](bank-deposit-bank-management-screen.md) — Tab 2 |
| [bank-deposit-bank-list-screen.md](bank-deposit-bank-list-screen.md) | [bank-deposit-bank-management-screen.md](bank-deposit-bank-management-screen.md) — Tab 1 |
| [bank-deposit-interest-assessment-screen.md](bank-deposit-interest-assessment-screen.md) | [bank-deposit-interest-management-screen.md](bank-deposit-interest-management-screen.md) — Tab 2 |
| [bank-deposit-interest-provision-screen.md](bank-deposit-interest-provision-screen.md) | [bank-deposit-interest-management-screen.md](bank-deposit-interest-management-screen.md) — Tab 1 |

---

## Apply Status

| Phase | Status |
| :--- | :--- |
| Phase 1 — Audit | Complete |
| Phase 2 — Plan | Complete |
| Phase 3 — Apply to specs | **Complete (2026-07-11)** |
| Phase 4 — Mockups | **Complete (2026-07-11)** — 4 Draft HTML mockups under `../mockups/investment/` |

---

## Related Documents

- [overview.md](overview.md)
- [changelog.md](changelog.md)
- [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
- [../bank/ux-optimization.md](../bank/ux-optimization.md)
- [../fixed-deposit/ux-optimization.md](../fixed-deposit/ux-optimization.md)
- [../../AI_INDEX.md](../../AI_INDEX.md)
