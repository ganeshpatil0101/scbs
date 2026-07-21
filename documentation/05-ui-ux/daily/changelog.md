# Changelog — Daily Screens

| Version | Date | Changes | Reason | Author |
| :--- | :--- | :--- | :--- | :--- |
| 2.1.0 | 2026-07-21 | Agent Collection Management: added Tab 2 संक्षिप्त तपशील + Tab 3 ट्रान्स्फर from screenshots; Collection List → Tab 4; removed TODO; mockup updated | Bank-provided Brief Details + Transfer screenshots | AI Agent |
| 2.0.1 | 2026-07-21 | New Account Tab 3: removed empty `परिपक्वता` TODO — maturity fields already on Tab 1; tab is joint holder only | Bank confirmation | AI Agent |
| 2.0.0 | 2026-07-21 | Account Register: Status = `चालू`/`बंद`/`स्थगित`; omit `अतिरिक्त शोध पर्याय`; mockup updated | Bank confirmation — reuse Savings/FD/Recurring patterns | AI Agent |
| 1.0.0 | 2025-06-26 | New Account, New Agent, Transaction, Agent Collection, Account Register, Interest Multiplier screen specs | Generated from `screenshots/डेली/` PNGs + MP4s | AI Agent |
| 1.1.0 | 2026-07-01 | Consolidated Branch/GL/Account lookup fields into single Autocomplete per entity-autocomplete-pattern.md | Legacy dual-field UX replaced | AI Agent |
| 1.2.0 | 2026-07-04 | New Daily Account: Tab 1 dropdowns; Tab 2 nominee fields + Google Maps address | User review of pending TODOs | AI Agent |
| 1.2.1 | 2026-07-04 | New Agent: Status, TDS reason, and scheme dropdown values | User review of pending TODOs | AI Agent |
| 1.2.2 | 2026-07-04 | Account Register, Agent Collection, Collection List, Interest Multiplier, Agent Transfer: scheme/agent dynamic loading | User review of pending TODOs | AI Agent |
| 1.3.0 | 2026-07-11 | UX optimization: Agent Collection + List → Agent Collection Management; Agent/Customer Autocomplete; Advanced Settings; Auto-fill; Transaction summary panel; Agent entity in entity-autocomplete-pattern | `@optimize-ui-ux` daily domain | AI Agent |
| 1.4.0 | 2026-07-16 | HTML mockups for all 7 current screens under `mockups/daily/`; module nav cross-links; spec `## Mockup` sections; overview + AI_INDEX updated | `@generate-ui-mockup` Phase 4 complete per [ux-optimization.md](ux-optimization.md) | AI Agent |
| 1.5.0 | 2026-07-18 | daily-transaction-screen.md superseded → [../accounting/deposit-account-transaction-screen.md](../accounting/deposit-account-transaction-screen.md); overview updated | Cross-module deposit transaction consolidation per [../accounting/ux-optimization.md](../accounting/ux-optimization.md) | AI Agent |
| 1.8.0 | 2026-07-21 | Joint Holder tab: removed Introducer section, renumbered fields; tab conditional on Tab 1 `संयुक्त खातेदार जोडा` checkbox (hidden by default); removed empty Approval tab (Tab 4); mockup updated; परिपक्वता subsection still TODO | Bank review — optional joint holder | AI Agent |
| 1.9.0 | 2026-07-21 | Nominee tab: nominee is Customer lookup + quick-add popup; Tab 2 hidden by default behind `वारसदार जोडा` checkbox; removed duplicate contact/address/occupation fields; nominee TODO placeholders removed; mockup updated | Nominee-as-Customer redesign per [quick-add-customer-pattern.md](../shared/quick-add-customer-pattern.md) | AI Agent |
