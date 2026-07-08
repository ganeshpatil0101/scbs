# Mockup — बँक व्यवस्थापन

| Property | Value |
|---|---|
| Spec | [bank-management-screen.md](../../../../bank/bank-management-screen.md) |
| Status | **Draft** |
| Created | 2026-07-08 |
| Language | Marathi only (English via ngx-translate in Angular phase) |
| Replaces | bank-register-screen, new-bank-screen, check-register-screen mockups |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Review checklist

- [ ] Tab 1: प्राथमिक शोध filters match spec (Branch Autocomplete, Account Type, Status)
- [ ] Tab 1: Grid columns match spec; row select / तपशील opens form panel
- [ ] Tab 1: + नवीन opens empty form; Status read-only `चालू` on create
- [ ] Tab 1: जी.एल. निवडा uses single Autocomplete (not ID + select pair)
- [ ] Tab 1: प्रगत सेटिंग्ज collapsed by default
- [ ] Tab 1: संघटना shown as read-only in header (not in filter bar)
- [ ] Tab 2: Primary filters + अतिरिक्त शोध पर्याय toggle
- [ ] Tab 2: Additional search collapsed by default
- [ ] Tab 2: Cheque processing panel visible only when row(s) selected
- [ ] Tab 2: TODO dropdowns marked with badge
- [ ] Marathi labels clear for non-technical bank staff
- [ ] Required fields marked with *
- [ ] Responsive on mobile (single column) and desktop (two columns where applicable)
- [ ] Sticky footer present

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen bank-management-screen`.
