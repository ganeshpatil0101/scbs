# Mockup — खाते रजिस्टर

| Property | Value |
|---|---|
| Spec | [loan-account-register-screen.md](../../../loan/loan-account-register-screen.md) |
| Status | **Draft** |
| Created | 2026-07-12 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Notes

- Reference screenshot `screenshots/कर्ज/डॅशबोर्ड-कर्ज-खाते रजिस्टर-1-05-07.png` not verified in repo — mockup is spec-driven.
- `संस्था` in header only (not in filter bar).
- Organization shown as session header.
- Status filter: `चालू` / `बंद` / `स्थगित` (label fixed from legacy `मिती`).
- Legacy `अतिरिक्त शोध पर्याय` omitted.

## Review checklist

- [ ] All 8 primary search fields with Autocomplete for Branch/GL/Account Holder
- [ ] Status dropdown (`मिती निवडा`) and account/customer range filters
- [ ] Filter checkbox: परतीची दिनांक संपून गेलेली खाते
- [ ] Results grid: all 23 columns (horizontal scroll on narrow screens)
- [ ] Sidebar actions: तपशील, निर्यात, काढा, खाते उतारा
- [ ] Bottom actions: खाते बंद, नूतनीकरण, पूर्वत
- [ ] Report dropdown + प्रिंट
- [ ] Marathi labels; org in header
- [ ] Responsive + sticky footer

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen loan-account-register-screen`.
