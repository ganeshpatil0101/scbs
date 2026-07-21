# Daily Module — UX Optimization Audit

Audit date: 2026-07-11. Applied: 2026-07-11. Domain: `documentation/05-ui-ux/daily/`.

Patterns applied: [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md), [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md).

Reference implementation: [../settings/ux-optimization.md](../settings/ux-optimization.md).

## Summary

| Metric | Before | After |
| :--- | :---: | :---: |
| Menu screens | 8 | 7 |
| Agent Collection screens | 2 | 1 (2 tabs) |
| Agent lookup pairs merged | — | 4 screens |
| Customer lookup pairs merged | — | 2 screens |
| Fields → Auto-fill | — | 12+ |
| Fields → Advanced | — | 18+ |
| Transaction summary panel | — | 1 screen |

## Consolidated Screen Map

| New / kept screen | Replaces | Document |
| :--- | :--- | :--- |
| नवीन खाते (New Account) | (field cleanup) | [new-daily-account-screen.md](new-daily-account-screen.md) |
| नवीन एजंट (New Agent) | (field cleanup) | [new-agent-screen.md](new-agent-screen.md) |
| व्यवहार (Transaction) | (field cleanup) | [daily-transaction-screen.md](daily-transaction-screen.md) |
| खाते रजिस्टर (Account Register) | (field cleanup) | [account-register-screen.md](account-register-screen.md) |
| एजंट कलेक्शन व्यवस्थापन (Agent Collection Management) | Agent Collection + Agent Collection List | [agent-collection-management-screen.md](agent-collection-management-screen.md) |
| एजंट कडून एजंट कडे खाते ट्रान्सफर | (field cleanup) | [agent-to-agent-transfer-screen.md](agent-to-agent-transfer-screen.md) |
| व्याज गुणक (Interest Multiplier) | (field cleanup) | [interest-multiplier-screen.md](interest-multiplier-screen.md) |

### Tab layout (Agent Collection Management)

| Tab | Marathi | English | Replaces |
| :---: | :--- | :--- | :--- |
| 1 | नवीन कलेक्शन | New Collection | Agent Collection Tab 1 |
| 2 | कलेक्शन यादी | Collection List | Agent Collection List |

---

## Decisions Applied (2026-07-11)

| # | Decision |
| :---: | :--- |
| 1 | Merge Agent Collection + Collection List → one 2-tab screen |
| 2 | Missing tabs stay as `TODO` stubs — no invented fields |
| 3 | Agent added to entity-autocomplete-pattern (`एजंट निवडा`) |
| 4 | Customer No. + Name → Customer Autocomplete on New Account + New Agent |
| 5 | Organization → session Auto-fill header on Account Register |
| 6 | Sales Agent, limits, IFSC/bank, interest type → प्रगत सेटिंग्ज on New Account |
| 7 | Security Deposit / Machine Deduction / PF / Meghdoot → Advanced on New Agent |
| 8 | Transaction Tab 1 read-only calcs → computed summary panel |
| 9 | Scheme references → unified [new-scheme-screen.md](../settings/schemes/new-scheme-screen.md) |

---

## Action Checklist (all applied)

### High priority

- [x] Consolidate Agent Collection + Collection List → agent-collection-management-screen.md
- [x] Agent Autocomplete on New Account, Account Register, Collection Management, Agent Transfer
- [x] Customer Autocomplete on New Daily Account + New Agent
- [x] Organization → Auto-fill header on Account Register
- [x] Remove duplicate `शाखेचे नाव` on Account Register
- [x] Auto-fill Labels: account no., duration, rate, dates, challan no.
- [x] Superseded banners on old collection specs

### Medium priority

- [x] Sales Agent block → प्रगत सेटिंग्ज (New Account)
- [x] IFSC / bank / limits / interest type → Advanced (New Account)
- [x] Security Deposit / Machine Deduction / PF / Meghdoot → Advanced (New Agent)
- [x] Secondary commission rules → Advanced (New Agent Tab 2)
- [x] Daily Transaction Tab 1 → summary panel + editable essentials
- [x] Agent Transfer From/To → Agent Autocomplete
- [x] Scheme links → new-scheme-screen.md

### Low priority

- [x] Interest Multiplier: auto-fill duration/rate from scheme
- [x] Note breadcrumb `ठेवी` vs `डेली` on Interest Multiplier (audit only)
- [x] Ledger tab: note shared `app-ledger-tab` component

---

## Open Gaps (TODO — not captured)

| Screen | Missing tabs / sections | Media reference |
| :--- | :--- | :--- |
| New Daily Account | Tab 3 परिपक्वता subsection | `screenshots/डेली/डॅशबोर्ड_डेली _नवीन खाते.mp4`; joint holder in `…-संयुक्त.png` |
| Daily Transaction | Tabs 3, 4, 6 (साहित्य तपशील, ट्रान्सफर, केवायसी माहिती) | `screenshots/डेली/डॅशबोर्ड_डेली_व्यवहार_*.png` |
| Agent Collection (legacy wizard) | Tabs 2–3 (संक्षिप्त तपशील, ट्रान्स्फर) — distinct from Agent-to-Agent Transfer | `screenshots/डेली/डॅशबोर्ड_डेली _एजंट_एजंट कलेक्शन.png` |

Do not invent fields until screenshots/MP4 are available in repo.

---

## Deprecated Specs (reference only)

| Superseded spec | New spec |
| :--- | :--- |
| [agent-collection-screen.md](agent-collection-screen.md) | [agent-collection-management-screen.md](agent-collection-management-screen.md) — Tab 1 |
| [agent-collection-list-screen.md](agent-collection-list-screen.md) | [agent-collection-management-screen.md](agent-collection-management-screen.md) — Tab 2 |

---

## Apply Status

| Phase | Status |
| :--- | :--- |
| Phase 1 — Audit | Complete |
| Phase 2 — Plan | Complete |
| Phase 3 — Apply to specs | **Complete (2026-07-11)** |
| Phase 4 — Mockups | **Complete (2026-07-16)** |

**Cross-module consolidation (2026-07-18):** Daily Transaction screen further merged into unified [../accounting/deposit-account-transaction-screen.md](../accounting/deposit-account-transaction-screen.md). See [../accounting/ux-optimization.md](../accounting/ux-optimization.md).

---

## Related Documents

- [overview.md](overview.md)
- [agent-collection-management-screen.md](agent-collection-management-screen.md)
- [changelog.md](changelog.md)
- [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
- [../settings/ux-optimization.md](../settings/ux-optimization.md)
- [../../AI_INDEX.md](../../AI_INDEX.md)
