# Mockup — नवीन एजंट (डेली)

| Property | Value |
|---|---|
| Spec | [new-agent-screen.md](../../../daily/new-agent-screen.md) |
| Status | **Draft** |
| Created | 2026-07-16 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Notes

- Reference media in `screenshots/डेली/डॅशबोर्ड_डेली_एजंट_नवीन एजंट.mp4`.
- TDS कारण निवडा shown only when TDS = नाही.
- Security Deposit / Machine Deduction / PF sub-fields hidden until parent checkbox checked.
- प्रगत सेटिंग्ज collapsed by default on both tabs.

## Review checklist

- [ ] All spec fields present with correct grouping
- [ ] Marathi labels clear for non-technical bank staff
- [ ] Required fields marked with *
- [ ] Responsive on mobile (single column) and desktop (two columns, centered)
- [ ] Grid columns match spec (commission grid)
- [ ] Tab structure approved

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen new-agent-screen`.
