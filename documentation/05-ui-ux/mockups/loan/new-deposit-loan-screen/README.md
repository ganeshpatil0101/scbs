# Mockup — नवीन ठेव कर्ज

| Property | Value |
|---|---|
| Spec | [new-deposit-loan-screen.md](../../../loan/new-deposit-loan-screen.md) |
| Status | **Draft** |
| Created | 2026-07-12 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Notes

- 3-tab wizard: ठेव माहिती → कर्ज माहिती → एस.आय माहिती.
- Tab 1: Customer/Agent Autocomplete; dual deposit tables; surrender value calculation.
- Tab 2: Loan fields, approval, co-applicant Autocomplete; वारसदार section is `[TODO]` stub.
- Tab 3: GL / Account Holder Autocomplete.
- प्रगत सेटिंग्ज collapsed by default on Tab 2.
- Reference video frames under `screenshots/कर्ज/new-deposit-loan-frames/` not verified in repo.

## Review checklist

- [ ] Tab 1: Deposit tables (left + right) and surrender summary
- [ ] Tab 2: Loan info, approval, co-applicant grid
- [ ] Tab 2: Nominee TODO stub visible
- [ ] Tab 3: S.I. fields with Autocomplete
- [ ] Footer: पुढे / मागे / पूर्ण / पूर्ववत
- [ ] Marathi labels; required markers
- [ ] Responsive + sticky footer

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen new-deposit-loan-screen`.
