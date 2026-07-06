# Mockup — नवीन योजना (एकीकृत)

| Property | Value |
|---|---|
| Spec | [new-scheme-screen.md](../../../../settings/schemes/new-scheme-screen.md) |
| Status | **Draft** |
| Created | 2026-07-05 |
| Language | Marathi only (English via ngx-translate in Angular phase) |
| Replaces | daily/savings/fd/recurring/loan-new-scheme-screen mockups |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Review checklist

- [ ] Scheme Type dropdown changes visible tabs per matrix
- [ ] Savings: 3 tabs (Info, Interest Posting, Charges)
- [ ] Daily/FD/Recurring: includes Duration & Rates, Account Closing where applicable
- [ ] Loan: includes Loan Specific tab; no Account Closing tab
- [ ] FD/Recurring/Loan: Advanced tab present
- [ ] जी.एल. निवडा uses single Autocomplete (GL master lookup), not read-only / not textbox
- [ ] GL suggestions appropriate to selected Scheme Type (Daily: ≤ 99 eligible)
- [ ] Shared component placeholders noted (posting grid, rate slab, charges)
- [ ] Type-specific fields on Tab 1 (Savings vs Loan sections)

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen new-scheme-screen`.
