# Mockup — व्याज दरात बदल

| Property | Value |
|---|---|
| Spec | [loan-interest-rate-change-screen.md](../../../../settings/loan/loan-interest-rate-change-screen.md) |
| Status | **Draft** |
| Created | 2026-07-05 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

Reference screenshot `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-कर्ज-व्याज दरात बदल-1.png` — verify layout if available locally.

## Review checklist

- [ ] Single-page form (no separate history tab)
- [ ] Past rate changes in collapsible section (collapsed by default)
- [ ] Scheme dropdown shows sample loan schemes (dynamic from Settings > नवीन योजना, Scheme Type = कर्ज)
- [ ] Apply rate radio options with correct default
- [ ] Export and Save actions in footer
- [ ] Required fields marked with *

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen loan-interest-rate-change-screen`.
