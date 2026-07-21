# Changelog — Fixed Deposit Screens

| Version | Date | Changes | Reason | Author |
| :--- | :--- | :--- | :--- | :--- |
| 1.0.0 | 2025-06-25 | New FD Account, FD Transaction screen specs | Generated from `screenshots/मुदत ठेव/` | AI Agent |
| 1.1.0 | 2025-06-26 | Account Register, Manual Interest, Renewal List, Deposit Loan Installment, Interest Multiplier | New assets in `screenshots/मुदत ठेव/` | AI Agent |
| 1.2.0 | 2026-07-01 | Consolidated Branch/GL/Account lookup fields into single Autocomplete per entity-autocomplete-pattern.md | Legacy dual-field UX replaced | AI Agent |
| 1.3.0 | 2026-07-04 | New FD Account: Tab 1 dropdowns; Tab 2 nominee (mirrors Daily); Tab 4 Other from screenshot; Tab 3 joint holder deferred | User review of pending TODOs | AI Agent |
| 1.3.1 | 2026-07-04 | Manual Interest: interest date = last FY end; Deposit Loan: dynamic customer lookup | User review of pending TODOs | AI Agent |
| 1.4.0 | 2026-07-11 | UX optimization: 7 → 6 screens; Account Register + Renewal List → Account Management (2 tabs); Customer/Agent Autocomplete; Advanced Settings; Transaction summary panel; scheme links → new-scheme-screen.md | `@optimize-ui-ux` applied per [ux-optimization.md](ux-optimization.md) | AI Agent |
| 1.5.0 | 2026-07-16 | HTML mockups for all 6 current screens under `mockups/fixed-deposit/`; module nav cross-links; spec `## Mockup` sections; overview + AI_INDEX updated | `@generate-ui-mockup` Phase 4 complete per [ux-optimization.md](ux-optimization.md) | AI Agent |
| 1.6.0 | 2026-07-18 | fd-transaction-screen.md superseded → [../accounting/deposit-account-transaction-screen.md](../accounting/deposit-account-transaction-screen.md); overview updated | Cross-module deposit transaction consolidation per [../accounting/ux-optimization.md](../accounting/ux-optimization.md) | AI Agent |
| 1.9.0 | 2026-07-21 | Joint Holder tab: removed Introducer section, renumbered fields; tab conditional on Tab 1 `संयुक्त खातेदार जोडा` checkbox (hidden by default); mockup updated | Bank review — optional joint holder | AI Agent |
| 2.0.0 | 2026-07-21 | Nominee tab: nominee is Customer lookup + quick-add popup; Tab 2 hidden by default behind `वारसदार जोडा` checkbox; removed duplicate contact/address/occupation fields; nominee TODO placeholders removed; mockup updated | Nominee-as-Customer redesign per [quick-add-customer-pattern.md](../shared/quick-add-customer-pattern.md) | AI Agent |
