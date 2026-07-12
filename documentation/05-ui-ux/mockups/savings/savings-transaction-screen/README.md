# Mockup — व्यवहार (बचत)

| Property | Value |
|---|---|
| Spec | [savings-transaction-screen.md](../../../savings/savings-transaction-screen.md) |
| Status | **Draft** |
| Created | 2026-07-12 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Notes

- Reference screenshots `screenshots/bachat/डॅशबोर्ड-बचत-व्यवहार*.png` — Tabs 1–4.
- Tab 5 (केवायसी) is TODO stub per spec.
- Tab 1 uses summary panel for read-only calculated fields.
- Bank dropdown on Tab 2 marked TODO per spec.

## Review checklist

- [ ] All Tab 1 fields: header, lookup, editable, summary panel
- [ ] Tabs 2–4 layout matches spec
- [ ] Marathi labels clear for non-technical bank staff
- [ ] Required fields marked with *
- [ ] Ledger grid columns match spec (15 columns)
- [ ] Tab structure approved

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen savings-transaction-screen`.
