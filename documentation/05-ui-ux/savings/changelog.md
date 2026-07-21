# Changelog — Savings Screens

| Version | Date | Changes | Reason | Author |
| :--- | :--- | :--- | :--- | :--- |
| 2.3.0 | 2026-07-21 | Account Register: omit legacy `अतिरिक्त शोध पर्याय` (deferred, no TODO stub) | Bank confirmation — not needed for current CBS UI | AI Agent |
| 2.2.0 | 2026-07-21 | Account Register: from bank screenshot — added `कर्ज संलग्नीत खाते` checkbox; sidebar `काढा`→`वगळा`; bottom `पूर्ववत`; mockup + screenshot saved | Bank-provided खाते रजिस्टर screenshot | AI Agent |
| 2.1.0 | 2026-07-21 | Status dropdown values set to `चालू` / `बंद` / `स्थगित` on New Account + Account Register; mockups updated | Bank confirmation — reuse FD/Daily/Recurring account status enum | AI Agent |
| 1.0.0 | 2025-06-25 | New Savings Account, Transaction, Manual Interest Calculation screen specs | Generated from `screenshots/bachat/` | AI Agent |
| 1.1.0 | 2026-07-01 | Consolidated Branch/GL/Account lookup fields into single Autocomplete per entity-autocomplete-pattern.md | Legacy dual-field UX replaced | AI Agent |
| 1.2.0 | 2026-07-05 | Account Register screen spec | New screenshot `05-07` in `screenshots/bachat/` | AI Agent |
| 1.3.0 | 2026-07-12 | UX optimization: Customer/Agent Autocomplete, session org header, Branch/Holder Autocomplete on Register, Transaction summary panel, Advanced Settings on New Account, Manual Interest Interest Date auto-fill; added ux-optimization.md | `@optimize-ui-ux` savings — 4→4 screens, field cleanup only per [ux-optimization.md](ux-optimization.md) | AI Agent |
| 1.4.0 | 2026-07-12 | HTML mockups (Draft) for all 4 screens under `mockups/savings/` | `@generate-ui-mockup` savings module | AI Agent |
| 1.5.0 | 2026-07-18 | New Savings Account Tab 1: removed Agent Branch, Agent, Account Category, Sales Agent Branch, Sales Agent; customer summary reduced to विशेष सूचना only; spec renumbered 1–13; mockup updated | Fields not required for this screen per bank review | AI Agent |
| 1.6.0 | 2026-07-18 | savings-transaction-screen.md superseded → [../accounting/deposit-account-transaction-screen.md](../accounting/deposit-account-transaction-screen.md); overview updated | Cross-module deposit transaction consolidation per [../accounting/ux-optimization.md](../accounting/ux-optimization.md) | AI Agent |
| 1.9.0 | 2026-07-21 | Joint Holder tab: removed Introducer section, renumbered fields; tab conditional on Tab 1 `संयुक्त खातेदार जोडा` checkbox (hidden by default); removed empty Approval tab (Tab 4); mockup updated | Bank review — optional joint holder | AI Agent |
| 2.0.0 | 2026-07-21 | Nominee tab: nominee is Customer lookup + quick-add popup; Tab 2 hidden by default behind `वारसदार जोडा` checkbox; removed duplicate contact/address/occupation fields; nominee TODO removed; mockup updated | Nominee-as-Customer redesign per [quick-add-customer-pattern.md](../shared/quick-add-customer-pattern.md) | AI Agent |
