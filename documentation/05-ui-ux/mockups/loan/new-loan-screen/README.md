# Mockup — नवीन कर्ज

| Property | Value |
|---|---|
| Spec | [new-loan-screen.md](../../../loan/new-loan-screen.md) |
| Status | **Draft** |
| Created | 2026-07-12 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Notes

- 6-tab wizard: कर्ज माहिती → कर्ज हप्ता पत्रक → जामीनदार → मंजुरी व तारण → कर्ज रेकॉर्ड → एस.आय माहिती.
- Tab 1: Customer/Agent Autocomplete; योजना निवडा marked `[TODO]`; विमा checkbox shows fields conditionally.
- Tab 4: तारण checkbox shows collateral fields conditionally.
- प्रगत सेटिंग्ज collapsed by default on Tab 1 and Tab 4.
- Reference video frames under `screenshots/कर्ज/new-loan-frames/` not verified in repo.

## Review checklist

- [ ] All 6 tabs with representative fields/grids
- [ ] Tab 1: Scheme dropdown TODO; insurance conditional fields
- [ ] Tab 2: Installment schedule grid + summary row
- [ ] Tab 3: Guarantor + co-borrower grids
- [ ] Tab 4: Approval, collateral, loan reason
- [ ] Tab 5: Previous loan record grids
- [ ] Tab 6: GL / Account Holder Autocomplete
- [ ] Footer: पुढे / मागे / पूर्ण / पूर्ववत
- [ ] Marathi labels; required markers
- [ ] Responsive + sticky footer

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen new-loan-screen`.
