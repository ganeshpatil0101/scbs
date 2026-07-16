# Mockup — खाते व्यवस्थापन (मुदत ठेव)

| Property | Value |
|---|---|
| Spec | [fd-account-management-screen.md](../../../fixed-deposit/fd-account-management-screen.md) |
| Status | **Draft** |
| Created | 2026-07-16 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Notes

- Consolidates superseded Account Register + Renewal List screens (2 tabs).
- Organization shown as session header (not in filter bar on Tab 1).
- `अतिरिक्त शोध पर्याय` marked TODO per spec.
- Pink/blue row legend for loan and matured accounts on Tab 1.

## Review checklist

- [ ] All filter fields present with correct grouping
- [ ] Marathi labels clear for non-technical bank staff
- [ ] Tab 1 grid columns match spec (21 columns)
- [ ] Tab 2 renewal grid columns match spec (12 columns)
- [ ] Sidebar actions and totals present
- [ ] Responsive on mobile and desktop

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen fd-account-management-screen`.
