# Mockup — व्यवहार (मुदत ठेव)

| Property | Value |
|---|---|
| Spec | [fd-transaction-screen.md](../../../fixed-deposit/fd-transaction-screen.md) |
| Status | **Draft** |
| Created | 2026-07-16 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Notes

- Reference screenshots in `screenshots/मुदत ठेव/डॅशबोर्ड-मुदत ठेव-व्यवहार*.png`.
- Tab 2 (साहित्य तपशील) and Tab 5 (केवायसी माहिती) marked `TODO` per spec.
- Tab 3 Transfer follows savings-transaction pattern.
- Tab 4 Ledger uses shared `app-ledger-tab` column set.

## Review checklist

- [ ] All spec fields present with correct grouping
- [ ] Marathi labels clear for non-technical bank staff
- [ ] Required fields marked with *
- [ ] Account summary panel shows computed read-only labels
- [ ] Tab structure approved
- [ ] Responsive on mobile and desktop

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen fd-transaction-screen`.
