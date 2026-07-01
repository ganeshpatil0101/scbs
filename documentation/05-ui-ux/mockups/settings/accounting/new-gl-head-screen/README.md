# Mockup — New GL Head (नवीन जी. एल. हेड)

| Property | Value |
| :--- | :--- |
| Spec | [new-gl-head-screen.md](../../../../settings/accounting/new-gl-head-screen.md) |
| Status | **Draft** |
| Created | 2025-06-30 |
| Language | Marathi only (English added via `ngx-translate` in Angular phase) |

## How to open

Open [`index.html`](index.html) in any web browser. Requires internet for Tailwind CDN and Google Fonts (Noto Sans Devanagari).

## Layout notes

- Desktop (`≥1024px`): primary fields (left) and **प्राथमिक गट** (right) side by side.
- Mobile: sections stack vertically.
- **खाते गट** dropdown includes all values captured in spec (video frames f_000–f_010); trailing `[TODO]` for scroll-below values.
- **जी. एल. हेड क्र.** shown read-only with sample auto-generated value `163`.
- **संघटना** shown disabled (read-only when member account selected — layout placeholder).
- Sticky action bar: **पूर्ववत**, **पूर्ण** (per spec Actions table).

## Review checklist

- [ ] All 17 spec fields present with correct grouping
- [ ] Branch field uses single Autocomplete with sample values (`1 — Branch 1`, etc.)
- [ ] Required fields marked with `*`
- [ ] Account Group dropdown values match spec capture list
- [ ] Primary Group subsections: शिल्लक प्रकार, खाते श्रेणी, संघटना/शाखा
- [ ] TODO badges on unresolved dropdowns (खाते प्रकार, स्थिती)
- [ ] Marathi labels clear for accounting staff
- [ ] Responsive layout approved on mobile and desktop

## Known gaps

- Reference video/frames not in repo — mockup is spec-driven only
- Additional Account Group values below scroll: `TODO` in spec
- Conditional enable/disable (member account → organization read-only) not wired — layout-only mockup

## Approval

When approved, change **Status** above to **Approved**, then run:

```text
/generate-ui-screen new-gl-head-screen
```

## Related Documents

- [new-gl-head-screen.md](../../../../settings/accounting/new-gl-head-screen.md)
- [new-gl-group-screen.md](../../../../settings/accounting/new-gl-group-screen.md)
