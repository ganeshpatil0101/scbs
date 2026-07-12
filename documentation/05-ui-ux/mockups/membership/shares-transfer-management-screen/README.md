# Mockup — शेअर्स ट्रान्सफर व्यवस्थापन

| Property | Value |
|---|---|
| Spec | [shares-transfer-management-screen.md](../../../membership/shares-transfer-management-screen.md) |
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
- [ ] Grid columns match spec (certificate grid, transfer grid, 14-column list)
- [ ] Tab structure approved (2 top-level tabs; 3 inner tabs on नवीन ट्रान्सफर)
- [ ] Member Autocomplete for From/To (not separate ID + name fields)
- [ ] Inner tabs 2–3 visible only when fee payment mode = ट्रान्सफर
- [ ] Organization in header (not filter bar)

## Notes

- `स्क्रोल निवडा` and `बँक निवडा` marked **TODO** — master data not captured in spec.
- Consolidates former Shares Transfer + Shares Transfer List screens per UX optimization.
- Tab 2 list filters use range textboxes for member no. (not Autocomplete) per entity-autocomplete-pattern exclusions.

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen shares-transfer-management-screen`.
