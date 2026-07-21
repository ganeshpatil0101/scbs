# Mockup — खाते रजिस्टर (बचत)

| Property | Value |
|---|---|
| Spec | [account-register-screen.md](../../../savings/account-register-screen.md) |
| Status | **Draft** |
| Created | 2026-07-12 |
| Updated | 2026-07-21 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Notes

- Reference: `screenshots/bachat/डॅशबोर्ड-बचत-खाते-रजिस्टर.png` (bank-provided 2026-07-21).
- Organization shown as session header (not in filter bar).
- Status filter: `चालू` / `बंद` / `स्थगित`.
- Checkbox `कर्ज संलग्नीत खाते` above grid; pink rows = loan-linked accounts.
- Sidebar: `तपशील`, `निर्यात करा`, `वगळा`, `खाते उतारा`.
- Bottom: `खाते बंद करा`, `पूर्ववत`.
- Legacy `अतिरिक्त शोध पर्याय` omitted (deferred — not in current CBS UI).

## Review checklist

- [ ] All filter fields present with correct grouping
- [ ] Loan-linked checkbox + pink legend clear
- [ ] Marathi labels clear for non-technical bank staff
- [ ] Grid columns match spec (19 columns)
- [ ] Sidebar and bottom actions present
- [ ] Responsive on mobile and desktop

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen account-register-screen`.
