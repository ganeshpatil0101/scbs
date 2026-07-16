# Mockup — व्याज गुणक (डेली)

| Property | Value |
|---|---|
| Spec | [interest-multiplier-screen.md](../../../daily/interest-multiplier-screen.md) |
| Status | **Draft** |
| Created | 2026-07-16 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Notes

- Reference screenshot: `screenshots/डेली/डॅशबोर्ड_डेली_व्याज गुणक.png`.
- Breadcrumb in screenshot shows `ठेवी` (Deposits) — noted in mockup header per spec audit.
- Compound frequency radios hidden until चक्रवाढ selected.
- Duration/rate auto-filled from selected scheme (read-only labels).

## Review checklist

- [ ] All spec fields present with correct grouping
- [ ] Marathi labels clear for non-technical bank staff
- [ ] Required fields marked with *
- [ ] Responsive on mobile (single column) and desktop (two columns, centered)
- [ ] Grid columns match spec (daily interest chart — 5 columns)
- [ ] Tab structure approved

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen interest-multiplier-screen`.
