# Mockup — व्याज व्यवस्थापन (बँक ठेव)

| Property | Value |
|---|---|
| Spec | [bank-deposit-interest-management-screen.md](../../../investment/bank-deposit-interest-management-screen.md) |
| Status | **Draft** |
| Created | 2026-07-11 |
| Language | Marathi only (English via ngx-translate in Angular phase) |
| Replaces | bank-deposit-interest-provision-screen, bank-deposit-interest-assessment-screen (superseded) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Notes

- Reference screenshots under `screenshots/गुंतवणूक/` not verified in repo — mockup is spec-driven.
- Shared filter + results grid across both tabs; primary footer action changes: **तरतूद** (Tab 1) / **पोस्ट** (Tab 2).
- TDS column is display-only.

## Review checklist

- [ ] Shared filter: Branch Autocomplete, Bank Autocomplete (multi-select noted), Post Date, Account From/To
- [ ] No ambiguous lone `खाते` filter
- [ ] Grid columns match spec including TDS display-only
- [ ] Summary totals: शिल्लक, तरतूद, व्याज, टीडीएस
- [ ] Tab 1 primary action तरतूद; Tab 2 primary action पोस्ट
- [ ] Marathi labels; required markers
- [ ] Responsive + sticky footer

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen bank-deposit-interest-management-screen`.
