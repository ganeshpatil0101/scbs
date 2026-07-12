# Mockup — कर्ज माहिती

| Property | Value |
|---|---|
| Spec | [loan-information-screen.md](../../../loan/loan-information-screen.md) |
| Status | **Draft** |
| Created | 2026-07-12 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Notes

- Reference screenshots under `screenshots/कर्ज/` not verified in repo — mockup is spec-driven.
- `संस्था` in header only (not in filter bar).
- Tab 2 (ग्राहक माहिती) rendered as TODO stub per spec.
- Tab 1 summary/arrears panels use read-only label styling (not editable inputs).

## Review checklist

- [ ] Tab 1: Branch/Scheme/Account Holder search, Advanced Settings collapsed
- [ ] Tab 1: Account summary, upcoming balance, closing interest, arrears panels (fields 7–44)
- [ ] Tab 1: Change history grid, today's recovery, links
- [ ] Tab 2: TODO stub visible
- [ ] Tab 3: Date filters, opening balance, full ledger grid columns
- [ ] Tab-specific footer actions per spec
- [ ] Marathi labels; org in header
- [ ] Responsive + sticky footer

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen loan-information-screen`.
