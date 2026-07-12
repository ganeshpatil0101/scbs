# Mockup — व्याज गुणक (रिकरिंग)

| Property | Value |
|---|---|
| Spec | [interest-multiplier-screen.md](../../../recurring/interest-multiplier-screen.md) |
| Status | **Draft** |
| Created | 2026-07-12 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Notes

- Reference screenshot `screenshots/रिकरिंग/` not in repo — layout is spec-driven.
- Compounding frequency radios hidden until चक्रव्याज selected.

## Review checklist

- [ ] All spec fields present with correct grouping
- [ ] Marathi labels clear for non-technical bank staff
- [ ] Required fields marked with *
- [ ] Responsive on mobile (single column) and desktop (two columns, centered)
- [ ] Grid columns match spec
- [ ] Conditional radio visibility approved

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen interest-multiplier-screen`.
