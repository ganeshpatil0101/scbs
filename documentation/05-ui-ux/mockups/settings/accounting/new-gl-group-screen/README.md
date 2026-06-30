# Mockup — New GL Group (नवीन जी.एल ग्रुप)

| Property | Value |
| :--- | :--- |
| Spec | [new-gl-group-screen.md](../../../../settings/accounting/new-gl-group-screen.md) |
| Status | **Draft** |
| Created | 2025-06-30 |
| Language | Marathi only (English added via `ngx-translate` in Angular phase) |

## How to open

Open [`index.html`](index.html) in any web browser. Requires internet for Tailwind CDN and Google Fonts (Noto Sans Devanagari).

## Layout notes

- Single-section form: **प्राथमिक गट** with two radio groups and three text/dropdown fields.
- Compact centered layout (`max-w-3xl` within wide container).
- Sticky action bar: **पूर्ववत**, **पूर्ण** (per spec Actions table).

## Review checklist

- [ ] Radio groups: नफा तोटा/ताळेबंद and उत्पन्न/खर्च with correct defaults selected
- [ ] Required fields marked with `*` (गट प्रकार निवडा, गटाचे नाव)
- [ ] गट प्रकार dropdown shows default `इतर` with TODO badge for full list
- [ ] Optional युनिकोड field present
- [ ] Marathi labels clear for accounting staff
- [ ] Responsive layout approved on mobile and desktop

## Known gaps

- Reference screenshot not in repo — mockup is spec-driven only
- Full गट प्रकार dropdown list is `TODO` in spec — not invented

## Approval

When approved, change **Status** above to **Approved**, then run:

```text
/generate-ui-screen new-gl-group-screen
```

## Related Documents

- [new-gl-group-screen.md](../../../../settings/accounting/new-gl-group-screen.md)
- [new-gl-head-screen.md](../../../../settings/accounting/new-gl-head-screen.md)
