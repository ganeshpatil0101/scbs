# Accounting Module — UX Optimization Audit (Deposit Transaction Consolidation)

Audit date: 2026-07-18. Applied: 2026-07-18. Cross-domain consolidation under `documentation/05-ui-ux/accounting/`.

Patterns applied: [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md), [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md).

Reference implementation: [../settings/ux-optimization.md](../settings/ux-optimization.md).

## Summary

| Metric | Before | After |
| :--- | :---: | :---: |
| Deposit transaction screens (4 modules) | 4 | **1** |
| Tabs per transaction screen | 5–6 (varied) | **4** (identical all modules) |
| Conditional tabs | 1 (Daily Loan Info) | **0** |
| Ledger tab on transaction screen | 4 | **0** (deferred) |
| KYC tab on transaction screen | 4 | **0** (replaced by Customer Details) |

## Consolidated Screen Map

| New screen | Replaces | Document |
| :--- | :--- | :--- |
| ठेव खाते व्यवहार (Deposit Account Transaction) | Savings + FD + Daily + Recurring Transaction | [deposit-account-transaction-screen.md](deposit-account-transaction-screen.md) |

## Decisions Applied (2026-07-18)

| # | Decision |
| :---: | :--- |
| 1 | Merge 4 module transaction screens → one screen with **मॉड्यूल निवडा** radio (बचत / मुदत ठेव / डेली / रिकरिंग) |
| 2 | Unify Recurring "बँक तपशील" / "चेक तपशील" → **साहित्य तपशील** (confirmed identical fields via user screenshots) |
| 3 | **Remove खातेवही (Ledger)** tab — detailed per-module ledger deferred (`TODO`) |
| 4 | **Remove केवायसी माहिती (KYC)** tab — replaced by **ग्राहक तपशील (Customer Details)** |
| 5 | **Remove कर्ज माहिती (Loan Information)** tab (Daily) — loan rows in Customer Details tab |
| 6 | Customer Details bound to Tab 1 account holder — no separate customer picker |
| 7 | Loan recovery action from collection — deferred (`TODO`); display-only for now |
| 8 | Recurring debit-mode Tab 1 fields — still `TODO` (maturity payout, premature closure, TDS) |
| 9 | Remove redundant `कर्ज खाते माहिती` link on Tab 1 — staff use Tab 4 |
| 10 | Standardize **प्रगत सेटिंग्ज** across modules for spot commission, provision, open amount, etc. |

## Tab Structure (all modules — identical)

| # | Tab | Replaces |
| :---: | :--- | :--- |
| 1 | खात्याची माहिती | All modules Tab 1 |
| 2 | साहित्य तपशील | Instrument / Cheque / Bank Details tabs |
| 3 | ट्रान्सफर | All modules Transfer tab |
| 4 | ग्राहक तपशील | KYC tab + Daily Loan Info (informational) |

## Action Checklist (all applied in specs)

### High priority

- [x] Create deposit-account-transaction-screen.md with module radio + 4-tab structure
- [x] Superseded banners on savings, fd, daily, recurring transaction specs
- [x] Update module overview.md files (4 modules)
- [x] Customer Details tab: identity header + cross-product account grid
- [x] Instrument Details + Transfer tabs fully documented (screenshot evidence 2026-07-18)

### Medium priority

- [x] Canonical summary field names (Ledger Balance, PAN/Aadhaar)
- [x] Module-conditional editable fields (inter-branch, interest date, commission, discount)
- [x] Advanced Settings standardized (spot commission, provision, open amount, etc.)
- [x] Full KYC address block → collapsible section in Customer Details

### Low priority / Deferred

- [ ] Detailed per-module ledger view (`TODO`)
- [ ] Loan recovery action in Customer Details (`TODO`)
- [ ] Recurring debit-mode Tab 1 fields (`TODO`)
- [ ] Bank reviewer sign-off: आंतर शाखेचा शुल्क → Advanced? (flagged in spec)

## Deprecated Specs (reference only)

| Superseded spec | New spec |
| :--- | :--- |
| [../savings/savings-transaction-screen.md](../savings/savings-transaction-screen.md) | [deposit-account-transaction-screen.md](deposit-account-transaction-screen.md) |
| [../fixed-deposit/fd-transaction-screen.md](../fixed-deposit/fd-transaction-screen.md) | [deposit-account-transaction-screen.md](deposit-account-transaction-screen.md) |
| [../daily/daily-transaction-screen.md](../daily/daily-transaction-screen.md) | [deposit-account-transaction-screen.md](deposit-account-transaction-screen.md) |
| [../recurring/recurring-transaction-screen.md](../recurring/recurring-transaction-screen.md) | [deposit-account-transaction-screen.md](deposit-account-transaction-screen.md) |

## Apply Status

| Phase | Status |
| :--- | :--- |
| Phase 1 — Audit | Complete |
| Phase 2 — Plan | Complete |
| Phase 3 — Apply to specs | **Complete (2026-07-18)** |
| Phase 4 — Mockups | **Draft (2026-07-18)** |

## Related Documents

- [overview.md](overview.md)
- [deposit-account-transaction-screen.md](deposit-account-transaction-screen.md)
- [changelog.md](changelog.md)
- [../savings/ux-optimization.md](../savings/ux-optimization.md)
- [../fixed-deposit/ux-optimization.md](../fixed-deposit/ux-optimization.md)
- [../daily/ux-optimization.md](../daily/ux-optimization.md)
- [../recurring/ux-optimization.md](../recurring/ux-optimization.md)
- [../../AI_INDEX.md](../../AI_INDEX.md)
