# Mockup — खाते रजिस्टर (डेली)

| Property | Value |
|---|---|
| Spec | [account-register-screen.md](../../../daily/account-register-screen.md) |
| Status | **Draft** |
| Created | 2026-07-16 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Notes

- Reference screenshot: `screenshots/डेली/डॅशबोर्ड_डेली_खाते रजिस्टर.png`.
- Organization (`संस्था`) shown as read-only header from tenant session, not in filter bar.
- Status filter: `चालू` / `बंद` / `स्थगित`.
- Legacy `अतिरिक्त शोध पर्याय` omitted (deferred — not in current CBS UI).

## Review checklist

- [ ] All spec fields present with correct grouping
- [ ] Marathi labels clear for non-technical bank staff
- [ ] Required fields marked with *
- [ ] Responsive on mobile (single column) and desktop (two columns, centered)
- [ ] Grid columns match spec (17 columns)
- [ ] Tab structure approved

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen account-register-screen`.
