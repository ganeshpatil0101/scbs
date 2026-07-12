# Mockup — व्याज व्यवस्थापन (रिकरिंग)

| Property | Value |
|---|---|
| Spec | [recurring-interest-management-screen.md](../../../recurring/recurring-interest-management-screen.md) |
| Status | **Draft** |
| Created | 2026-07-12 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Notes

- Reference screenshots `screenshots/रिकरिंग/` not in repo — layout is spec-driven.
- `प्रगत शोध` shown as TODO link only.
- Tab 1 primary: `तरतूद`; Tab 2 primary: `निश्चित` + footer `प्रोसीडिंग`, `परत`.

## Review checklist

- [ ] All spec fields present with correct grouping
- [ ] Marathi labels clear for non-technical bank staff
- [ ] Required fields marked with *
- [ ] Tab-specific actions correct (तरतूद vs निश्चित)
- [ ] Grid columns match spec (10 columns)
- [ ] Pink legend for interest-free period approved

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen recurring-interest-management-screen`.
