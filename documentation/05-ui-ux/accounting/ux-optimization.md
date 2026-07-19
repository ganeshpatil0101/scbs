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
- [manual-interest-management-screen.md](manual-interest-management-screen.md)
- [changelog.md](changelog.md)
- [../savings/ux-optimization.md](../savings/ux-optimization.md)
- [../fixed-deposit/ux-optimization.md](../fixed-deposit/ux-optimization.md)
- [../daily/ux-optimization.md](../daily/ux-optimization.md)
- [../recurring/ux-optimization.md](../recurring/ux-optimization.md)
- [../../AI_INDEX.md](../../AI_INDEX.md)

---

# Manual Interest Management Consolidation

Audit date: 2026-07-19. Applied: 2026-07-19. Cross-domain consolidation under `documentation/05-ui-ux/accounting/`.

Patterns applied: [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md), [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md).

Reference precedent (tabs): [../recurring/recurring-interest-management-screen.md](../recurring/recurring-interest-management-screen.md), [../loan/loan-interest-management-screen.md](../loan/loan-interest-management-screen.md), [../investment/bank-deposit-interest-management-screen.md](../investment/bank-deposit-interest-management-screen.md).

## Summary

| Metric | Before | After |
| :--- | :---: | :---: |
| Manual interest screens (4 modules × 2 actions) | 8 legacy entries | **1** |
| UI mode for provision vs assessment | Separate menus / tabs (Recurring) | **कार्यवाही निवडा** radio (तरतूद / आकारणी) |
| Module selection | Per-module menu | **मॉड्यूल निवडा** radio (बचत / मुदत ठेव / डेली / रिकरिंग) |
| Branch / GL lookup | Legacy dual ID + dropdown pairs | Single Autocomplete per entity |

## Consolidated Screen Map

| New screen | Replaces | Document |
| :--- | :--- | :--- |
| मॅन्युअल व्याज व्यवस्थापन (Manual Interest Management) | Savings + FD + Daily + Recurring manual interest provision + assessment | [manual-interest-management-screen.md](manual-interest-management-screen.md) |

## Decisions Applied (2026-07-19)

| # | Decision |
| :---: | :--- |
| 1 | Merge 4 module × 2 action screens → one screen with **मॉड्यूल निवडा** + **कार्यवाही निवडा** radio groups (intentional deviation from Loan/Investment/Recurring tab precedent) |
| 2 | Standardize grid-populate button → **व्याज गणना करा** (legacy डेली/रिकरिंग used `व्याज आकारणी` for same action) |
| 3 | **Remove** legacy **प्रगत शोध** / Advanced Search link — not required on consolidated screen |
| 4 | **व्याज दिनांक** read-only auto FY-end on all modules (replaces legacy dropdown on Savings) |
| 5 | **जी.एल. निवडा** Autocomplete on all modules — default `55 — सेव्हिंग ठेव` for बचत; legacy बचत **खाते क्र.** + **खाते** dropdown removed |
| 6 | मुदत ठेव-only: **स्थिती** dropdown + **सवलत दर** grid column + **वर्तमान व्याज** label |
| 7 | डेली / रिकरिंग: pink legend for interest-free-period accounts |
| 8 | Footer totals identical all modules: एकूण शिल्लक, एकूण तरतूद, एकूण व्याज, एकूण व्याज + एकूण तरतूद |
| 9 | Primary posting button varies by module × action — documented in footer matrix |
| 10 | New तरतूद screenshots captured for बचत, मुदत ठेव, डेली (2026-07-19); डेली आकारणी screenshot added same day |

## Action Checklist

### High priority

- [x] Create manual-interest-management-screen.md with dual radio groups
- [x] Superseded banners on savings, fd, recurring interest specs
- [x] Update module overview.md files (4 modules)
- [x] Save new screenshots to `screenshots/bachat/`, `screenshots/मुदत ठेव/`, `screenshots/डेली/`
- [x] Reference Screenshots table (8 files)

### Low priority / Deferred

- [ ] डेली आकारणी primary posting button label (`TODO` — cropped in both Daily screenshots)
- [ ] FD Status dropdown values (`TODO`)
- [ ] HTML mockup (`/generate-ui-mockup manual-interest-management-screen`)

## Deprecated Specs (reference only)

| Superseded spec | New spec |
| :--- | :--- |
| [../savings/manual-interest-calculation-screen.md](../savings/manual-interest-calculation-screen.md) | [manual-interest-management-screen.md](manual-interest-management-screen.md) |
| [../fixed-deposit/fd-manual-interest-calculation-screen.md](../fixed-deposit/fd-manual-interest-calculation-screen.md) | [manual-interest-management-screen.md](manual-interest-management-screen.md) |
| [../recurring/recurring-interest-management-screen.md](../recurring/recurring-interest-management-screen.md) | [manual-interest-management-screen.md](manual-interest-management-screen.md) |

## Apply Status (Manual Interest)

| Phase | Status |
| :--- | :--- |
| Phase 1 — Audit | Complete |
| Phase 2 — Plan | Complete |
| Phase 3 — Apply to specs | **Complete (2026-07-19)** |
| Phase 4 — Mockups | **Draft (2026-07-19)** — [manual-interest-management-screen](../mockups/accounting/manual-interest-management-screen/) |
