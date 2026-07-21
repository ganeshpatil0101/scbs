# Mockup — कर्ज व्यवहार

| Property | Value |
|---|---|
| Spec | [loan-transaction-screen.md](../../../loan/loan-transaction-screen.md) |
| Status | **Draft** |
| Created | 2026-07-12 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Notes

- Reference screenshots under `screenshots/कर्ज/` not verified in repo — mockup is spec-driven.
- **जमा / नावे** radio on Tab 1 (default: जमा) updates tab labels and mode-specific tabs 3, 6, 7.
- Credit: हप्ते → … → खातेवही (tab 6) → जामीनदार (tab 7).
- Debit: पूर्वीची कर्ज कपात → … → परतफेड वेळापत्रक (tab 6) → खातेवही (tab 7).
- `TODO` dropdowns remain for परतफेड प्रकार, कपात प्रकार.
- बँक निवडा = Bank Master Autocomplete (samples from deposit Instrument tab).
- प्रगत सेटिंग्ज collapsed by default on Tab 1 and Tab 3 (Credit).

## Review checklist

- [ ] Tab 1: Credit/Debit radio; Branch / GL / Account Holder Autocomplete
- [ ] Tab 1: Mode-specific summary panels (Credit vs Debit)
- [ ] Tab 2 label switches: इतर जमा / इतर कपात
- [ ] Tab 3–7: Correct content per mode
- [ ] Tab 4–5: Cheque and Transfer shared tabs
- [ ] Ledger grid columns match `app-ledger-tab` (loan variant)
- [ ] Footer: मागे / पुढे / पूर्ण / पूर्ववत
- [ ] Marathi labels; required markers
- [ ] Responsive + sticky footer

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen loan-transaction-screen`.
