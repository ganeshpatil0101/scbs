# Mockup — खाते रजिस्टर (रिकरिंग)

| Property | Value |
|---|---|
| Spec | [account-register-screen.md](../../../recurring/account-register-screen.md) |
| Status | **Draft** |
| Created | 2026-07-12 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Notes

- Status filter: `चालू` / `बंद` / `स्थगित`.
- Legacy `अतिरिक्त शोध पर्याय` omitted (deferred — not in current CBS UI).

## Review checklist

- [ ] All spec fields present with correct grouping
- [ ] Marathi labels clear for non-technical bank staff
- [ ] Organization header shown (not in filter bar)
- [ ] Responsive on mobile and desktop
- [ ] Grid columns match spec (20 columns)
- [ ] Legend colors approved

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen account-register-screen`.
