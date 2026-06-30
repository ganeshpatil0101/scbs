# Mockup — New User (नवीन युजर)

| Property | Value |
| :--- | :--- |
| Spec | [new-user-screen.md](../../../../settings/master/new-user-screen.md) |
| Status | **Draft** |
| Created | 2025-06-30 |
| Updated | 2025-06-30 — Tailwind CSS v4, Marathi-only, centered responsive layout |
| Language | Marathi only (English added via `ngx-translate` in Angular phase) |

## How to open

Open [`index.html`](index.html) in any web browser. Requires internet for Tailwind CDN and Google Fonts (Noto Sans Devanagari).

To share with bank reviewers: zip this folder and send via email, or host on static hosting.

## Layout notes

- Content is centered with `max-w-7xl` — modest gray margins on very wide screens.
- Desktop (`≥1024px`): **मूलभूत माहिती** (left) and **सेटिंग** (right) side by side; **संघटना युजर अधिकार** full width below.
- Mobile: sections stack vertically (single column).
- Sticky bottom action bar: रीसेट, पुढे (Tab 1) / मागे, जतन करा (Tab 2).

## Review checklist

- [ ] All Tab 1 spec fields present and grouped correctly (User Type → Basic Info → Settings → Organization Rights)
- [ ] Marathi labels clear for non-technical bank staff
- [ ] Required fields marked with `*`
- [ ] Rights grid columns match spec (निवडा, अ.क्र., संघटना, शाखा नाव) with काढा action
- [ ] Conditional fields (intra-branch limits) shown disabled — placement approved
- [ ] Responsive layout approved on mobile and desktop
- [ ] Tab 2 placeholder approach approved (simplified permission matrix)

## Known gaps

- Reference screenshot not in repo — mockup is spec-driven only
- Name dropdown values are `TODO` — shown with badge, not invented
- Tab 2 uses simplified placeholder; full matrix in [user-role-screen.md](../../../../settings/master/user-role-screen.md)

## Approval

When approved, change **Status** above to **Approved**, then run:

```text
/generate-ui-screen new-user-screen
```

## Related Documents

- [new-user-screen.md](../../../../settings/master/new-user-screen.md)
- [user-role-screen.md](../../../../settings/master/user-role-screen.md)
