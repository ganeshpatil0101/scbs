# Mockup — नवीन सभासदत्व

| Property | Value |
|---|---|
| Spec | [new-membership-screen.md](../../../membership/new-membership-screen.md) |
| Status | **Draft** |
| Created | 2026-07-12 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Review checklist

- [ ] All spec fields present with correct grouping
- [ ] Marathi labels clear for non-technical bank staff
- [ ] Required fields marked with *
- [ ] Responsive on mobile (single column) and desktop (two columns, centered)
- [ ] Grid columns match spec (संयुक्त खातेदार यादी)
- [ ] Tab structure approved (भाग माहिती → परिचयकर्ता/संयुक्त खातेदार → वारसदार)
- [ ] Organization in header (not form fields)
- [ ] प्रगत सेटिंग्ज collapsed by default on Tab 1 and Tab 3
- [ ] Autocomplete fields for शाखा, ग्राहक, जी.एल., खातेधारक

## Notes

- `स्थिती`, `संचालक`, `वार्षिक अहवाल`, `स्थान`, `जिल्हा`, `तालुका`, `शहर` marked TODO per spec.
- Tab 3 uses geographic dropdowns (not Google Maps) per membership spec; differs from FD/Savings nominee pattern.
- Reference screenshots: `screenshots/sabhsadatv/डॅशबोर्ड-सभासदत्व-नवीन सभासदत्व-*.png`

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen new-membership-screen`.
