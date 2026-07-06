# Mockup — कर्मचारी व सिस्टम प्रवेश

| Property | Value |
|---|---|
| Spec | [staff-system-access-screen.md](../../../../settings/master/staff-system-access-screen.md) |
| Status | **Draft** |
| Created | 2026-07-05 |
| Language | Marathi only (English via ngx-translate in Angular phase) |
| Replaces | new-user-screen, new-employee-screen mockups |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Review checklist

- [ ] All spec fields present with correct grouping (4-tab wizard)
- [ ] Marathi labels clear for non-technical bank staff
- [ ] Required fields marked with *
- [ ] Customer lookup uses single Autocomplete (not ID + name pair)
- [ ] Advanced Settings collapsed by default on Tab 2
- [ ] Intra-branch limits hidden until checkbox checked
- [ ] Tab 4 permission matrix matches User Role screen pattern
- [ ] Responsive on mobile and desktop

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen staff-system-access-screen`.
