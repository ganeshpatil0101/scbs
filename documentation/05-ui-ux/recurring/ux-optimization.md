# Recurring Module — UX Optimization Audit

Audit date: 2026-07-12. Applied: 2026-07-12. Domain: `documentation/05-ui-ux/recurring/`.

Patterns applied: [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md), [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md).

Reference implementation: [../settings/ux-optimization.md](../settings/ux-optimization.md).

## Summary

| Metric | Before | After |
| :--- | :---: | :---: |
| Menu screens | 6 | **5** |
| Transaction screens | 1 (credit-only) | 1 unified `व्यवहार` (`नावे / जमा`) |
| Manual interest screens | 2 | 1 (2 tabs) |
| Customer / Agent lookup pairs merged | — | 2 screens |
| Fields → Auto-fill | — | 15+ |
| Fields → Advanced | — | 6+ |
| Transaction summary panel | — | 1 screen |

## Consolidated Screen Map

| New / kept screen | Replaces | Document |
| :--- | :--- | :--- |
| नवीन खाते (New Account) | (field cleanup) | [new-recurring-account-screen.md](new-recurring-account-screen.md) |
| व्यवहार (Transaction) | Credit Transaction + debit mode shell | [recurring-transaction-screen.md](recurring-transaction-screen.md) |
| खाते रजिस्टर (Account Register) | (field cleanup) | [account-register-screen.md](account-register-screen.md) |
| व्याज व्यवस्थापन (Interest Management) | Manual Interest Assessment + Provision | [recurring-interest-management-screen.md](recurring-interest-management-screen.md) |
| व्याज गुणक (Interest Multiplier) | (field cleanup) | [interest-multiplier-screen.md](interest-multiplier-screen.md) |

### Tab layout (Interest Management)

| Tab | Marathi | English | Replaces | Primary action |
| :---: | :--- | :--- | :--- | :--- |
| 1 | व्याज तरतूद | Interest Provision | manual-interest-provision-screen.md | `तरतूद` |
| 2 | व्याज आकारणी | Interest Assessment | manual-interest-assessment-screen.md | `निश्चित` / `प्रोसीडिंग` |

---

## Decisions Applied (2026-07-12)

| # | Decision |
| :---: | :--- |
| 1 | Rename `जमा व्यवहार` → unified `व्यवहार` with `नावे / जमा` radio (1A); debit Tab 1 fields `TODO` until screenshots |
| 2 | Merge Manual Interest Assessment + Provision → Interest Management (Loan/Investment pattern) |
| 3 | Do not merge New Account ↔ Account Register |
| 4 | Do not merge Interest Multiplier ↔ Manual Interest |
| 5 | Do not merge Account Register + renewal list (no renewal list spec exists) |
| 6 | Customer No. + Name → Customer Autocomplete on New Account |
| 7 | Agent / Sales Agent ID+Name → Agent Autocomplete |
| 8 | Organization → session Auto-fill header on Account Register |
| 9 | Credit Transaction Tab 1 read-only calcs → computed summary panel |
| 10 | Scheme references → unified [new-scheme-screen.md](../settings/schemes/new-scheme-screen.md) |

---

## Action Checklist (all applied)

### High priority

- [x] Consolidate Manual Interest Assessment + Provision → recurring-interest-management-screen.md
- [x] Rename Credit Transaction → recurring-transaction-screen.md with `नावे / जमा` mode
- [x] Customer Autocomplete on New Recurring Account Tab 1
- [x] Agent Autocomplete on New Recurring Account Tab 1
- [x] Organization → Auto-fill header on Account Register
- [x] Remove duplicate `शाखेचे नाव` on Register
- [x] Account Holder text → Account Holder Autocomplete on Register
- [x] Add `योजना निवडा` filter on Register (FD/Daily parity)
- [x] Credit Transaction Tab 1 → summary panel + editable essentials
- [x] Superseded banners on credit-transaction, manual-interest-assessment, manual-interest-provision

### Medium priority

- [x] Sales Agent block → प्रगत सेटिंग्ज (New Account)
- [x] IFSC / Bank payout fields → Advanced (New Account)
- [x] Auto-fill Labels: scheme type, compounding, account no., duration, rate, maturity
- [x] Manual Interest: Interest Date → Auto-fill Label (FD pattern)
- [x] Interest Multiplier: scheme-driven duration/rate auto-fill + conditional radios
- [x] Scheme links → new-scheme-screen.md
- [x] Nominee tab → reference shared `app-nominee-form` component

### Low priority

- [x] Ledger tab → note shared `app-ledger-tab` component
- [x] KYC tab → note shared `app-kyc-info-tab` component
- [x] Debit mode Tab 1 shell documented with `TODO` placeholder

---

## Open Gaps (TODO — not captured)

| Screen | Missing tabs / sections | Media reference |
| :--- | :--- | :--- |
| New Recurring Account | Tab 3 (सूचक/संयुक्त खातेदार), Tab 4 (मंजुरी) | `screenshots/रिकरिंग/डॅशबोर्ड_रिकरिंग_नवीन खाते.mp4` |
| Recurring Transaction | Tabs 2–4 (बँक तपशील, ट्रान्सफर, खातेवही) | `screenshots/रिकरिंग/डॅशबोर्ड_रिकरिंग_जमा व्यवहार.mp4` |
| Recurring Transaction | Debit Tab 1 fields (maturity payout / premature closure) | Not captured — mode shell only |
| Account Register | `अतिरिक्त शोध पर्याय` | `screenshots/रिकरिंग/डॅशबोर्ड_रिकरिंग_खाते रजिस्टर.png` |
| Interest Management | `प्रगत शोध` | `screenshots/रिकरिंग/डॅशबोर्ड_रिकरिंग_मॅन्युअल व्याज_आकारणी.png` |
| New Account Tab 1 | Account Type dropdown values | Cross-check scheme benefits |
| Transaction Tab 5 | Address Type dropdown values | KYC frame |

`screenshots/रिकरिंग/` is empty in repo — cannot verify fields from media. Do not invent fields until screenshots/MP4 are available.

---

## Deprecated Specs (reference only)

| Superseded spec | New spec |
| :--- | :--- |
| [credit-transaction-screen.md](credit-transaction-screen.md) | [recurring-transaction-screen.md](recurring-transaction-screen.md) |
| [manual-interest-assessment-screen.md](manual-interest-assessment-screen.md) | [recurring-interest-management-screen.md](recurring-interest-management-screen.md) — Tab 2 |
| [manual-interest-provision-screen.md](manual-interest-provision-screen.md) | [recurring-interest-management-screen.md](recurring-interest-management-screen.md) — Tab 1 |

---

## Apply Status

| Phase | Status |
| :--- | :--- |
| Phase 1 — Audit | Complete |
| Phase 2 — Plan | Complete |
| Phase 3 — Apply to specs | **Complete (2026-07-12)** |
| Phase 4 — Mockups | **Draft (2026-07-12)** — 5 HTML mockups under `mockups/recurring/` |

---

## Related Documents

- [overview.md](overview.md)
- [recurring-transaction-screen.md](recurring-transaction-screen.md)
- [recurring-interest-management-screen.md](recurring-interest-management-screen.md)
- [changelog.md](changelog.md)
- [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
- [../settings/ux-optimization.md](../settings/ux-optimization.md)
- [../../AI_INDEX.md](../../AI_INDEX.md)
