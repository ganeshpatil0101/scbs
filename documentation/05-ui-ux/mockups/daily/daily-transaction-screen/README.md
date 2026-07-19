# Mockup — व्यवहार (डेली)

> **Superseded (2026-07-18):** Use unified mockup [deposit-account-transaction-screen](../../accounting/deposit-account-transaction-screen/) instead. Spec: [deposit-account-transaction-screen.md](../../../accounting/deposit-account-transaction-screen.md).

| Property | Value |
|---|---|
| Spec | ~~[daily-transaction-screen.md](../../../daily/daily-transaction-screen.md)~~ → [deposit-account-transaction-screen.md](../../../accounting/deposit-account-transaction-screen.md) |
| Status | **Superseded** |
| Created | 2026-07-16 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Notes

- Reference screenshots in `screenshots/डेली/डॅशबोर्ड_डेली_व्यवहार_*.png`.
- Tabs 3, 4, 6 (साहित्य तपशील, ट्रान्सफर, केवायसी माहिती) marked `TODO` per spec — tab shell only.
- Tab 1 account summary panel shows computed read-only labels (fields 10–27).
- Tab 5 Ledger uses shared `app-ledger-tab` column set (15 columns).

## Review checklist

- [ ] All spec fields present with correct grouping
- [ ] Marathi labels clear for non-technical bank staff
- [ ] Required fields marked with *
- [ ] Responsive on mobile (single column) and desktop (two columns, centered)
- [ ] Grid columns match spec
- [ ] Tab structure approved

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen daily-transaction-screen`.
