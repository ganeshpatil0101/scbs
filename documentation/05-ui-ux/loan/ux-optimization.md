# Loan Module — UX Optimization Audit

Audit date: 2026-07-12. Applied: 2026-07-12. Domain: `documentation/05-ui-ux/loan/`.

Patterns applied: [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md), [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md).

Reference implementation: [../investment/ux-optimization.md](../investment/ux-optimization.md).

## Summary

| Metric | Before | After |
| :--- | :---: | :---: |
| Menu screens | 8 | 6 |
| Transaction wizards | 2 | 1 (Credit/Debit mode + conditional tabs) |
| Interest bulk ops | 2 | 1 (2 tabs) |
| Autocomplete migrations | 1 partial | 6 screens |
| Fields → Auto-fill | — | 12+ |
| Fields → Advanced | — | 8 |

## Consolidated Screen Map

| New / kept screen | Replaces / action | Document |
| :--- | :--- | :--- |
| कर्ज व्यवहार (Loan Transaction) | Credit Transaction + Debit Transaction | [loan-transaction-screen.md](loan-transaction-screen.md) |
| व्याज व्यवस्थापन (Interest Management) | Scheduled Interest Assessment + Manual Interest Provision | [loan-interest-management-screen.md](loan-interest-management-screen.md) |
| नवीन कर्ज (New Loan) | Field cleanup only | [new-loan-screen.md](new-loan-screen.md) |
| नवीन ठेव कर्ज (New Deposit Loan) | Field cleanup only | [new-deposit-loan-screen.md](new-deposit-loan-screen.md) |
| कर्ज माहिती (Loan Information) | Field cleanup; Register → Detail navigation | [loan-information-screen.md](loan-information-screen.md) |
| खाते रजिस्टर (Account Register) | Field cleanup only | [loan-account-register-screen.md](loan-account-register-screen.md) |

Cross-module (unchanged): [../fixed-deposit/deposit-loan-installment-payment-screen.md](../fixed-deposit/deposit-loan-installment-payment-screen.md) stays under FD.

### Tab layout (Loan Transaction)

| Tab | Marathi | English | Visibility | Replaces |
| :---: | :--- | :--- | :--- | :--- |
| 1 | कर्ज माहिती | Loan Information | Both | Credit Tab 1 / Debit Tab 1 |
| 2 | इतर जमा / इतर कपात | Other Credits / Other Deductions | Both | Credit Tab 2 / Debit Tab 2 |
| 3 | हप्ते | Installments | Credit only | Credit Tab 3 |
| 3 | पूर्वीची कर्ज कपात | Previous Loan Deduction | Debit only | Debit Tab 3 |
| 4 | चेक तपशील | Cheque Details | Both | Credit Tab 4 / Debit Tab 4 |
| 5 | ट्रान्सफर | Transfer | Both | Credit Tab 5 / Debit Tab 5 |
| 6 | परतफेड वेळापत्रक | Repayment Schedule | Debit only | Debit Tab 6 |
| 6 / 7 | खातेवही | Ledger | Both | Credit Tab 6 / Debit Tab 7 |
| 7 | जामीनदार | Guarantor | Credit only | Credit Tab 7 |

**Mode selector:** Radio `जमा (Credit)` / `नावे (Debit)` on Tab 1 — matches Savings Transaction pattern.

### Tab layout (Interest Management)

| Tab | Marathi | English | Primary action | Replaces |
| :---: | :--- | :--- | :--- | :--- |
| 1 | व्याज तरतूद | Interest Provision | `तरतूद` | manual provision |
| 2 | व्याज आकारणी | Interest Assessment | `पोस्टिंग` | scheduled assessment |

---

## Decisions Applied (2026-07-12)

| # | Decision |
| :---: | :--- |
| 1 | Merge Credit + Debit Transaction → Loan Transaction with Credit/Debit mode and conditional tabs (user choice #1). |
| 2 | Merge Scheduled Interest Assessment + Manual Interest Provision → Interest Management (Investment pattern). |
| 3 | Keep New Loan and New Deposit Loan as separate wizards — different collateral workflows. |
| 4 | Keep Loan Information and Account Register separate — inquiry vs list (not FD list+list merge). |
| 5 | Register `तपशील` navigates to Loan Information with account pre-filled. |
| 6 | Deposit Loan Installment Payment remains under FD menu. |
| 7 | Leave `TODO` master data and uncaptured Nominee / Customer Information tabs as scaffolded gaps. |

---

## Action Checklist (all applied in specs)

### High priority

- [x] Consolidate Credit + Debit → loan-transaction-screen.md
- [x] Consolidate Interest Assessment + Provision → loan-interest-management-screen.md
- [x] Branch / GL / Account Holder → Autocomplete on Transaction, Interest, Register
- [x] Customer / Agent Autocomplete on New Loan and New Deposit Loan opening wizards
- [x] Organization → session header on Register and Loan Information
- [x] Superseded banners on four old specs

### Medium priority

- [x] New Loan: Auto-fill scheme type, member block, account no., computed installments
- [x] New Loan: bank payout, rebate, subsidy, fund transfer limit → प्रगत सेटिंग्ज
- [x] New Deposit Loan: bank block, L.F., rebate → प्रगत सेटिंग्ज
- [x] Loan Information: Account Summary + Arrears panels; simplify search filters
- [x] Transaction: Parent Employee, Sanctioning Officer, Interest Product → Advanced
- [x] Interest: Branch/GL Autocomplete; keep account From/To range

### Low priority

- [x] Loan Information Tab 1 renamed to **खाते सारांश** (Account Summary) to avoid name collision
- [x] Document shared `app-cheque-tab`, `app-transfer-tab`, `app-ledger-tab` on Loan Transaction
- [x] Co-borrower / co-applicant rows use Customer Autocomplete

---

## Open Gaps (TODO — not captured)

| Item | Handling |
| :--- | :--- |
| `परतफेड प्रकार`, `कपात प्रकार निवडा` on Loan Transaction | **Keep TODO** — bank will provide later |
| FD Deposit Loan Installment Tabs 2–6 | Keep TODO under FD (remove later) |

*(Resolved 2026-07-21: Status; Bank Master; Interest FY-end; scheme/slab/months dynamic; Staff Autocomplete; collateral + loan reason enums; SI frequency; omit Loan Info Tab 2; Deposit Loan nominee-as-Customer.)*

---

## Deprecated Specs (reference only)

| Superseded spec | New spec |
| :--- | :--- |
| [loan-credit-transaction-screen.md](loan-credit-transaction-screen.md) | [loan-transaction-screen.md](loan-transaction-screen.md) — Credit mode |
| [loan-debit-transaction-screen.md](loan-debit-transaction-screen.md) | [loan-transaction-screen.md](loan-transaction-screen.md) — Debit mode |
| [loan-scheduled-interest-assessment-screen.md](loan-scheduled-interest-assessment-screen.md) | [loan-interest-management-screen.md](loan-interest-management-screen.md) — Tab 2 |
| [loan-manual-interest-provision-screen.md](loan-manual-interest-provision-screen.md) | [loan-interest-management-screen.md](loan-interest-management-screen.md) — Tab 1 |

---

## Apply Status

| Phase | Status |
| :--- | :--- |
| Phase 1 — Audit | Complete |
| Phase 2 — Plan | Complete |
| Phase 3 — Apply to specs | **Complete (2026-07-12)** |
| Phase 4 — Mockups | **Complete (2026-07-12)** — 6 Draft HTML mockups under `../mockups/loan/` |

---

## Related Documents

- [overview.md](overview.md)
- [changelog.md](changelog.md)
- [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
- [../investment/ux-optimization.md](../investment/ux-optimization.md)
- [../fixed-deposit/ux-optimization.md](../fixed-deposit/ux-optimization.md)
- [../../AI_INDEX.md](../../AI_INDEX.md)
