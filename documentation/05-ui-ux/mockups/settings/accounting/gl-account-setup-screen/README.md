# Mockup — जी.एल. खाते सेटअप

| Property | Value |
|---|---|
| Spec | [gl-account-setup-screen.md](../../../../settings/accounting/gl-account-setup-screen.md) |
| Status | **Draft** |
| Created | 2026-07-05 |
| Language | Marathi only (English via ngx-translate in Angular phase) |
| Replaces | new-gl-group-screen, new-gl-head-screen mockups |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Review checklist

- [ ] 2-tab wizard: Account Group → GL Head
- [ ] P&L vs Balance Sheet toggles correct sub-type radios
- [ ] Branch account fields hidden until Branch Account selected
- [ ] GL Head No. shown read-only (auto-generated)
- [ ] Account Group read-only on Tab 2 from Tab 1 input
- [ ] Advanced Settings collapsed by default on both tabs
- [ ] Required fields marked with *

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen gl-account-setup-screen`.
