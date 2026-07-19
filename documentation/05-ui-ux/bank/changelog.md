# Changelog — Bank Screens

| Version | Date | Changes | Reason | Author |
| :--- | :--- | :--- | :--- | :--- |
| 1.0.0 | 2026-07-05 | Bank Register, New Bank, Cheque Register screen specs | New screenshots in `screenshots/Bank/` | AI Agent |
| 2.0.0 | 2026-07-07 | UX optimization applied per [ux-optimization.md](ux-optimization.md). Consolidated 3 screens into [bank-management-screen.md](bank-management-screen.md) (2 tabs: बँक खाते, चेक रजिस्टर). Each tab: list + create/update on one page. Field simplifications: Organization auto-fill; Branch + GL Autocomplete; New Bank Advanced Settings section; Cheque Register tiered filters + conditional processing panel. Superseded banners on bank-register, new-bank, check-register specs. | Small field count; reduce menu hops; align with ui-simplification-patterns | AI Agent |
| 2.1.0 | 2026-07-08 | HTML mockup for [bank-management-screen.md](bank-management-screen.md) at [mockups/bank/bank-management-screen/](../mockups/bank/bank-management-screen/) | Bank user layout review before Angular | AI Agent |
| 2.1.1 | 2026-07-08 | Account Type dropdown values (सेव्हिंग खाते, करंट खाते, कॅश क्रेडिट / ओ.डी, संस्था) and Status values (स्थगित, बंद) captured in spec and mockup | Legacy app master data | AI Agent |
| 2.1.2 | 2026-07-08 | Bank Method dropdown values (न ई फ टि, आर टि जि एस, न ई फ टि/आर टि जि एस) captured in spec and mockup | Legacy app master data | AI Agent |
| 2.2.0 | 2026-07-19 | Cheque Register filter `बँक निवडा` → Autocomplete (Bank Master); shared Bank entity documented in entity-autocomplete-pattern.md | Align with cross-screen Bank Autocomplete standard | AI Agent |
