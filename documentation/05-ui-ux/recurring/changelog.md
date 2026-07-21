# Changelog — Recurring Screens

| Version | Date | Changes | Reason | Author |
| :--- | :--- | :--- | :--- | :--- |
| 2.0.0 | 2026-07-21 | New Account: खाते प्रकार = FD account-type list; Register: Status = `चालू`/`बंद`/`स्थगित`; omit `अतिरिक्त शोध पर्याय`; mockups updated | Bank confirmation — reuse FD/Savings patterns | AI Agent |
| 1.0.0 | 2025-06-26 | New Account, Credit Transaction, Account Register, Manual Interest, Interest Multiplier screen specs | Generated from `screenshots/रिकरिंग/` PNGs + MP4s | AI Agent |
| 1.1.0 | 2026-07-01 | Consolidated Branch/GL/Account lookup fields into single Autocomplete per entity-autocomplete-pattern.md | Legacy dual-field UX replaced | AI Agent |
| 1.2.0 | 2026-07-12 | UX optimization: 6 → 5 screens. Merged Credit Transaction → व्यवहार (नावे/जमा); merged Manual Interest Assessment + Provision → व्याज व्यवस्थापन; Customer/Agent Autocomplete; Advanced Settings; transaction summary panel; register cleanup | @optimize-ui-ux per [ux-optimization.md](ux-optimization.md) | AI Agent |
| 1.3.0 | 2026-07-12 | HTML mockups (Draft) for all 5 current screens under `mockups/recurring/` | Bank review before Angular | AI Agent |
| 1.4.0 | 2026-07-18 | recurring-transaction-screen.md superseded → [../accounting/deposit-account-transaction-screen.md](../accounting/deposit-account-transaction-screen.md); overview updated | Cross-module deposit transaction consolidation per [../accounting/ux-optimization.md](../accounting/ux-optimization.md) | AI Agent |
| 1.7.0 | 2026-07-21 | Joint Holder tab: removed Introducer section, renumbered fields; tab conditional on Tab 1 `संयुक्त खातेदार जोडा` checkbox (hidden by default); removed empty Approval tab (Tab 4); mockup updated | Bank review — optional joint holder | AI Agent |
| 1.8.0 | 2026-07-21 | Nominee tab: nominee is Customer lookup + quick-add popup; Tab 2 hidden by default behind `वारसदार जोडा` checkbox; removed duplicate contact/address/occupation fields; mockup updated | Nominee-as-Customer redesign per [quick-add-customer-pattern.md](../shared/quick-add-customer-pattern.md) | AI Agent |
