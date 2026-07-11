# Fixed Deposit Module — UX Optimization Audit

Audit date: 2026-07-11. Applied: 2026-07-11. Domain: `documentation/05-ui-ux/fixed-deposit/`.

Patterns applied: [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md), [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md).

Reference implementation: [../settings/ux-optimization.md](../settings/ux-optimization.md).

## Summary

| Metric | Before | After |
| :--- | :---: | :---: |
| Menu screens | 7 | 6 |
| Account inquiry screens | 2 | 1 (2 tabs) |
| Customer / Agent lookup pairs merged | — | 3 screens |
| Fields → Auto-fill | — | 15+ |
| Fields → Advanced | — | 12+ |
| Transaction summary panel | — | 1 screen |

## Consolidated Screen Map

| New / kept screen | Replaces | Document |
| :--- | :--- | :--- |
| नवीन खाते (New Account) | (field cleanup) | [new-fd-account-screen.md](new-fd-account-screen.md) |
| व्यवहार (Transaction) | (field cleanup) | [fd-transaction-screen.md](fd-transaction-screen.md) |
| खाते व्यवस्थापन (Account Management) | Account Register + Renewal List | [fd-account-management-screen.md](fd-account-management-screen.md) |
| मॅन्युअल व्याज आकारणी (Manual Interest) | (field cleanup) | [fd-manual-interest-calculation-screen.md](fd-manual-interest-calculation-screen.md) |
| ठेव कर्ज हप्ता पेमेंट (Deposit Loan Installment) | (field cleanup; stays in FD) | [deposit-loan-installment-payment-screen.md](deposit-loan-installment-payment-screen.md) |
| व्याज गुणक (Interest Multiplier) | (field cleanup) | [fd-interest-multiplier-screen.md](fd-interest-multiplier-screen.md) |

### Tab layout (Account Management)

| Tab | Marathi | English | Replaces |
| :---: | :--- | :--- | :--- |
| 1 | खाते रजिस्टर | Account Register | fd-account-register-screen.md |
| 2 | नूतनीकरण यादी | Renewal List | account-renewal-list-screen.md |

---

## Decisions Applied (2026-07-11)

| # | Decision |
| :---: | :--- |
| 1 | Merge Account Register + Renewal List → one 2-tab screen |
| 2 | Deposit Loan Installment stays under FD; cross-link to Loan New Deposit Loan |
| 3 | Do not merge Manual Interest ↔ Interest Multiplier |
| 4 | Customer No. + Name → Customer Autocomplete on New Account + DLIP |
| 5 | Agent / Sales Agent ID+Name → Agent Autocomplete |
| 6 | Organization → session Auto-fill header on Account Register tab |
| 7 | Receipt series, L.F. Number, Multiple FD, Sales Agent → प्रगत सेटिंग्ज |
| 8 | FD Transaction Tab 1 read-only calcs → computed summary panel |
| 9 | Scheme references → unified [new-scheme-screen.md](../settings/schemes/new-scheme-screen.md) |

---

## Action Checklist (all applied)

### High priority

- [x] Consolidate Account Register + Renewal List → fd-account-management-screen.md
- [x] Customer Autocomplete on New FD Account Tab 1 + Deposit Loan Installment Tab 1
- [x] Agent Autocomplete on New FD Account Tab 1
- [x] GL + Account Holder Autocomplete on New FD Account Tab 4
- [x] Organization → Auto-fill header on Account Register tab
- [x] Remove duplicate `शाखेचे नाव` on Register + Renewal tabs
- [x] Account Holder text → Account Holder Autocomplete on inquiry tabs
- [x] Auto-fill Labels: account no., duration, rate, maturity, dates
- [x] Superseded banners on old register + renewal specs

### Medium priority

- [x] Sales Agent block → प्रगत सेटिंग्ज (New Account)
- [x] Receipt Prefix/Number, Multiple FD → Advanced (New Account)
- [x] L.F. Number → Advanced (New Account Tab 4)
- [x] FD Transaction Tab 1 → summary panel + editable essentials
- [x] Manual Interest: Interest Date → Auto-fill Label
- [x] Interest Multiplier: conditional radio visibility notes
- [x] Scheme links → new-scheme-screen.md
- [x] DLIP ↔ Loan New Deposit Loan cross-links

### Low priority

- [x] Nominee tab → reference shared `app-nominee-form` component
- [x] Ledger tab → note shared `app-ledger-tab` component
- [x] Concession Rate column noted in Manual Interest grid (display only)

---

## Open Gaps (TODO — not captured)

| Screen | Missing tabs / sections | Media reference |
| :--- | :--- | :--- |
| New FD Account | Tab 3 (परिचयकर्ता / संयुक्त खाते धारक) | `screenshots/मुदत ठेव/डॅशबोर्ड-मुदत ठेव-नवीन खाते.png` |
| FD Transaction | Tabs 2, 5 (साहित्य तपशील, केवायसी माहिती) | `screenshots/मुदत ठेव/डॅशबोर्ड-मुदत ठेव-व्यवहार*.png` |
| Deposit Loan Installment | Tabs 2–6 (इतर कपात … केवायसी) | `screenshots/मुदत ठेव/डॅशबोर्ड_ठेव_ठेव कर्ज हप्ता पेमेंट.mp4` |
| Account Register | `अतिरिक्त शोध पर्याय` | `screenshots/मुदत ठेव/डॅशबोर्ड_मुदत ठेव _खाते रजिस्टर.png` |
| Manual Interest | `अॅडव्हान्स शोध` | `screenshots/मुदत ठेव/डॅशबोर्ड_मुदत ठेव_ मॅन्युअल व्याज_आकारणी.png` |

Do not invent fields until screenshots/MP4 are available in repo.

---

## Deprecated Specs (reference only)

| Superseded spec | New spec |
| :--- | :--- |
| [fd-account-register-screen.md](fd-account-register-screen.md) | [fd-account-management-screen.md](fd-account-management-screen.md) — Tab 1 |
| [account-renewal-list-screen.md](account-renewal-list-screen.md) | [fd-account-management-screen.md](fd-account-management-screen.md) — Tab 2 |

---

## Apply Status

| Phase | Status |
| :--- | :--- |
| Phase 1 — Audit | Complete |
| Phase 2 — Plan | Complete |
| Phase 3 — Apply to specs | **Complete (2026-07-11)** |
| Phase 4 — Mockups | Pending |

---

## Related Documents

- [overview.md](overview.md)
- [fd-account-management-screen.md](fd-account-management-screen.md)
- [changelog.md](changelog.md)
- [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
- [../settings/ux-optimization.md](../settings/ux-optimization.md)
- [../../AI_INDEX.md](../../AI_INDEX.md)
