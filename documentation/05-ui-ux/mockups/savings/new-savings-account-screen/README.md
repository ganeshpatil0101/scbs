# Mockup — नवीन खाते (बचत)

| Property | Value |
|---|---|
| Spec | [new-savings-account-screen.md](../../../savings/new-savings-account-screen.md) |
| Status | **Draft** |
| Created | 2026-07-12 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Notes

- Reference screenshot `screenshots/bachat/डॅशबोर्ड-बचत-नवीन खाते.png` — Tab 1 only.
- Tabs 2–4 are TODO stubs per spec.
- Scheme / Status dropdowns show `[TODO]` for uncaptured values.
- Removed fields (2026-07-18): Agent Branch, Agent, Account Category, Sales Agent Branch, Sales Agent; customer summary limited to विशेष सूचना only.
- प्रगत सेटिंग्ज collapsed by default (`<details>`).

## Review checklist

- [ ] All Tab 1 fields present with correct grouping (13 spec fields)
- [ ] Customer summary shows विशेष सूचना only after autocomplete
- [ ] Marathi labels clear for non-technical bank staff
- [ ] Required fields marked with *
- [ ] Advanced Settings placement approved
- [ ] Side-by-side layout on desktop approved

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen new-savings-account-screen`.
