# Mockup — ग्राहक यादी

| Property | Value |
|---|---|
| Spec | [customer-list-screen.md](../../../customer/customer-list-screen.md) |
| Status | **Draft** |
| Created | 2026-07-09 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Review checklist

- [ ] संस्था shown as read-only in header (not in filter bar)
- [ ] शाखा निवडा uses single Autocomplete (not ID + dropdown pair)
- [ ] Primary filters: Name, Customer No. From/To, Status
- [ ] अॅडव्हान्स शोध collapsed by default; Masters Passing inside
- [ ] Default grid columns only (9): Select through Mobile
- [ ] Additional columns noted as Details / Export only
- [ ] Marathi labels clear for non-technical bank staff
- [ ] Required fields marked with * (none required on this list filter)
- [ ] Responsive on mobile (single column) and desktop
- [ ] Sticky footer present

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen customer-list-screen`.
