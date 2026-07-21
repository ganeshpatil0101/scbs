# Savings Module — UX Optimization Audit

Audit date: 2026-07-12. Applied: 2026-07-12. Domain: `documentation/05-ui-ux/savings/`.

Patterns applied: [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md), [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md).

Reference implementation: [../settings/ux-optimization.md](../settings/ux-optimization.md). Closest peer: [../fixed-deposit/ux-optimization.md](../fixed-deposit/ux-optimization.md).

## Summary

| Metric | Before | After |
| :--- | :---: | :---: |
| Menu screens | 4 | **4** (no merges) |
| Customer / Agent lookup pairs merged | — | 1 screen (New Account) |
| Fields → Auto-fill | — | 10+ |
| Fields → Advanced | — | 6 |
| Transaction summary panel | — | 1 screen |

Screenshots under `screenshots/bachat/` confirm only four operational screens — no तरतूद (provision) sibling, no renewal/dormant list. Screen count unchanged; field cleanup only.

## Consolidated Screen Map

| New / kept screen | Replaces | Document |
| :--- | :--- | :--- |
| नवीन खाते (New Account) | (field cleanup) | [new-savings-account-screen.md](new-savings-account-screen.md) |
| व्यवहार (Transaction) | (field cleanup) | [savings-transaction-screen.md](savings-transaction-screen.md) |
| खाते रजिस्टर (Account Register) | (field cleanup) | [account-register-screen.md](account-register-screen.md) |
| मॅन्युअल व्याज आकारणी (Manual Interest Calculation) | (field cleanup) | [manual-interest-calculation-screen.md](manual-interest-calculation-screen.md) |

---

## Decisions Applied (2026-07-12)

| # | Decision |
| :---: | :--- |
| 1 | Do not merge screens — only 4 menu items captured; no provision or renewal list sibling |
| 2 | Do not merge New Account ↔ Account Register |
| 3 | Do not create Interest Management — single manual interest screen (calculate + post) |
| 4 | Customer No. + Name → Customer Autocomplete on New Account |
| 5 | Agent / Sales Agent ID+Name → Agent Autocomplete |
| 6 | Organization → session Auto-fill header on Account Register |
| 7 | Branch Code + Branch Name → Branch Autocomplete on Register |
| 8 | Account Holder text → Account Holder Autocomplete on Register |
| 9 | Sales Agent, Debit Limit, Fund Transfer Limit, IFSC/bank payout → प्रगत सेटिंग्ज (New Account) |
| 10 | Transaction Tab 1 read-only calcs → computed summary panel |
| 11 | Manual Interest: duplicate Posting Date dropdown+date → Interest Date Auto-fill Label |
| 12 | Scheme references → unified [new-scheme-screen.md](../settings/schemes/new-scheme-screen.md) |
| 13 | Register sidebar `तपशील` — no separate Account Information screen (Membership deferral pattern) |

---

## Action Checklist (all applied)

### High priority

- [x] Customer Autocomplete on New Savings Account Tab 1
- [x] Agent Autocomplete on New Savings Account Tab 1
- [x] Organization → Auto-fill header on Account Register
- [x] Branch Code + Branch Name → Branch Autocomplete on Register
- [x] Account Holder text → Account Holder Autocomplete on Register
- [x] Auto-fill Labels: account no., interest rate, current date, member block after customer pick
- [x] Savings Transaction Tab 1 → summary panel + editable essentials
- [x] Manual Interest: Interest Date → Auto-fill Label (FD pattern)

### Medium priority

- [x] Sales Agent block → प्रगत सेटिंग्ज (New Account)
- [x] Debit Limit, Fund Transfer Limit, IFSC / Bank payout → Advanced (New Account)
- [x] Scheme links → new-scheme-screen.md
- [x] Nominee tab → reference shared `app-nominee-form` component
- [x] Ledger tab → note shared `app-ledger-tab` component
- [x] KYC tab → note shared `app-kyc-info-tab` component

### Low priority

- [x] Customer No. From/To range retained on Register (list filter pattern)
- [x] Cross-link Register to FD Account Management (superseded register pattern)

---

## Open Gaps (TODO — not captured)

| Screen | Missing tabs / sections | Media reference |
| :--- | :--- | :--- |
| New Savings Account | Tab 2 (वारसदार) | `screenshots/bachat/डॅशबोर्ड-बचत-नवीन खाते.png` (Tab 1); Tab 3 in `…-परिचयकर्ता.png` |
| Savings Transaction | Tab 5 (केवायसी माहिती) | `screenshots/bachat/डॅशबोर्ड-बचत-व्यवहार*.png` |
| Account Register | `अतिरिक्त शोध पर्याय` | `screenshots/bachat/डॅशबोर्ड-बचत-खाते रजिस्टर-1-05-07.png` |
| Manual Interest | `अॅडव्हान्स शोध` | `screenshots/bachat/डॅशबोर्ड-बचत-मॅन्युअल व्याज-आकारणी.png` |

Do not invent fields until screenshots are re-captured or video frames added.

---

## Deprecated Specs (reference only)

None — no screen merges in this optimization pass.

---

## Apply Status

| Phase | Status |
| :--- | :--- |
| Phase 1 — Audit | Complete |
| Phase 2 — Plan | Complete |
| Phase 3 — Apply to specs | **Complete (2026-07-12)** |
| Phase 4 — Mockups | **Draft (2026-07-12)** — see [mockups/savings/](../mockups/savings/) |

**Cross-module consolidation (2026-07-18):** Savings Transaction screen further merged into unified [../accounting/deposit-account-transaction-screen.md](../accounting/deposit-account-transaction-screen.md). See [../accounting/ux-optimization.md](../accounting/ux-optimization.md).

**Nominee-as-Customer (2026-07-21):** New Account Tab 2 uses Customer search + quick-add popup; tab hidden by default. See [new-savings-account-screen.md](new-savings-account-screen.md), [../shared/quick-add-customer-pattern.md](../shared/quick-add-customer-pattern.md).

---

## Nominee Tab — UX Enhancement Suggestions (2026-07-21)

| # | Suggestion | Priority |
| :---: | :--- | :---: |
| 1 | Show **नवीन ग्राहक** badge on nominee grid rows created via quick-add popup (vs existing customer) | Medium |
| 2 | Display running **एकूण टक्केवारी** total when multiple nominees are added; warn if not 100% | High |
| 3 | Non-blocking warning if nominee customer matches primary account holder or a joint holder | Medium |
| 4 | Disallow **स्वतः** (Self) as नाते when nominee customer record matches primary holder | Medium |

---

## Related Documents

- [overview.md](overview.md)
- [changelog.md](changelog.md)
- [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
- [../shared/quick-add-customer-pattern.md](../shared/quick-add-customer-pattern.md)
- [../fixed-deposit/ux-optimization.md](../fixed-deposit/ux-optimization.md)
- [../../AI_INDEX.md](../../AI_INDEX.md)
