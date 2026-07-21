# Mockup — नवीन खाते (डेली)

| Property | Value |
|---|---|
| Spec | [new-daily-account-screen.md](../../../daily/new-daily-account-screen.md) |
| Status | **Draft** |
| Created | 2026-07-16 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Notes

- Reference media in `screenshots/डेली/डॅशबोर्ड_डेली _नवीन खाते.mp4` and Tab 3 joint holder PNGs.
- Tab 3 hidden by default; shown when Tab 1's `संयुक्त खातेदार जोडा` checkbox is checked. Introducer section removed per bank review.
- प्रगत सेटिंग्ज collapsed by default on Tab 1.

## Review checklist

- [ ] All spec fields present with correct grouping
- [ ] Joint Holder tab appears only when checkbox checked
- [ ] Marathi labels clear for non-technical bank staff
- [ ] Required fields marked with *
- [ ] Responsive on mobile (single column) and desktop (two columns, centered)
- [ ] Grid columns match spec (nominee grid)
- [ ] Tab structure approved

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen new-daily-account-screen`.
