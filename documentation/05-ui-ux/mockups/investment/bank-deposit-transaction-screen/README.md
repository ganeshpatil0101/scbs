# Mockup — व्यवहार (बँक ठेव)

| Property | Value |
|---|---|
| Spec | [bank-deposit-transaction-screen.md](../../../investment/bank-deposit-transaction-screen.md) |
| Status | **Draft** |
| Created | 2026-07-11 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Notes

- Reference screenshots under `screenshots/गुंतवणूक/` not verified in repo — mockup is spec-driven.
- Tabs **चेक तपशील** and **ट्रान्सफर** appear only when **रोख / ट्रान्सफर** = ट्रान्सफर (layout demo).
- Cheque **बँक निवडा**: Autocomplete from society Bank master (बँक व्यवस्थापन) — same as New Account interest-transfer bank.
- Tab 4 uses shared `app-ledger-tab` column set.

## Review checklist

- [ ] Tab 1: Branch / GL / Account Holder Autocomplete
- [ ] Tab 1: Account Summary Panel (read-only Labels)
- [ ] Tab 2 & 3 hidden until Transfer selected
- [ ] Tab 2: Cheque bank Autocomplete from society Bank master
- [ ] Tab 3: Transfer grid columns match spec
- [ ] Tab 4: Ledger filter + grid columns match `app-ledger-tab`
- [ ] Footer: मागे / पुढे / पूर्ण / पूर्ववत per tab
- [ ] Marathi labels; required markers
- [ ] Responsive + sticky footer

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen bank-deposit-transaction-screen`.
