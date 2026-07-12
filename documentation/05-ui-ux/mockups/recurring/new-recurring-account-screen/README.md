# Mockup — नवीन खाते (रिकरिंग)

| Property | Value |
|---|---|
| Spec | [new-recurring-account-screen.md](../../../recurring/new-recurring-account-screen.md) |
| Status | **Draft** |
| Created | 2026-07-12 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Notes

- Reference media `screenshots/रिकरिंग/` not in repo — layout is spec-driven.
- Tabs 3–4 are TODO stubs.
- Account Type dropdown marked TODO per spec.
- प्रगत सेटिंग्ज collapsed by default (`<details>`).

## Review checklist

- [ ] All Tab 1 fields present with correct grouping
- [ ] Customer summary panel after autocomplete
- [ ] Marathi labels clear for non-technical bank staff
- [ ] Required fields marked with *
- [ ] Nominee tab (Tab 2) key fields approved
- [ ] Advanced Settings placement approved

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen new-recurring-account-screen`.
