# Mockup — नवीन खाते (मुदत ठेव)

| Property | Value |
|---|---|
| Spec | [new-fd-account-screen.md](../../../fixed-deposit/new-fd-account-screen.md) |
| Status | **Draft** |
| Created | 2026-07-16 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Notes

- Reference screenshots in `screenshots/मुदत ठेव/डॅशबोर्ड-मुदत ठेव-नवीन खाते*.png`.
- Tab 3 (परिचयकर्ता / संयुक्त खाते धारक) marked `TODO` per spec — tab shell only.
- Tab 4 conditional sections (व्याज हस्तांतरण, खाते बंद करतेवेळी) hidden until parent checkbox checked.
- प्रगत सेटिंग्ज collapsed by default on Tab 1 and Tab 4.

## Review checklist

- [ ] All spec fields present with correct grouping
- [ ] Marathi labels clear for non-technical bank staff
- [ ] Required fields marked with *
- [ ] Responsive on mobile (single column) and desktop (two columns, centered)
- [ ] Grid columns match spec (nominee grid)
- [ ] Tab structure approved

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen new-fd-account-screen`.
