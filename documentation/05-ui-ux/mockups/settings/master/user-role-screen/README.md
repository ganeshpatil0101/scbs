# Mockup — User Role (युजर रोल)

| Property | Value |
| :--- | :--- |
| Spec | [user-role-screen.md](../../../../settings/master/user-role-screen.md) |
| Status | **Draft** |
| Created | 2025-06-30 |
| Language | Marathi only (English added via `ngx-translate` in Angular phase) |

## How to open

Open [`index.html`](index.html) in any web browser. Requires internet for Tailwind CDN and Google Fonts (Noto Sans Devanagari).

To share with bank reviewers: zip this folder and send via email, or host on static hosting.

## Layout notes

- Single-form screen (no tabs): role name field + scrollable permission matrix.
- Desktop: full-width permission grid with sticky column headers; bulk-select checkboxes in header row.
- Mobile: table scrolls horizontally; sticky action bar at bottom.
- Sample rows show **अकाउंटींग** menu forms from spec; remaining menus/forms marked `[TODO]`.

## Review checklist

- [ ] Role name field present with required `*` marker
- [ ] Permission grid columns match spec (अ.क्र., मेनु, फॉर्मचे नाव, सर्व अधिकार, फक्त बघण्यासाठी, अधिकार नाही)
- [ ] Header checkboxes for bulk column select visible and understandable
- [ ] Sample Accounting rows match spec (8 forms listed)
- [ ] Marathi labels clear for non-technical bank staff
- [ ] Responsive layout approved on mobile and desktop
- [ ] Sticky action bar (रीसेट, जतन करा) placement approved

## Known gaps

- Reference screenshot `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-मास्टर-युजर रोल.png` not in repo — mockup is spec-driven only
- Full form list per menu is `TODO` in spec — only partial Accounting sample shown; trailing row marks pending master data
- Checkbox mutual exclusivity (one permission level per row) not implemented — layout-only mockup

## Approval

When approved, change **Status** above to **Approved**, then run:

```text
/generate-ui-screen user-role-screen
```

## Related Documents

- [user-role-screen.md](../../../../settings/master/user-role-screen.md)
- [new-user-screen.md](../../../../settings/master/new-user-screen.md)
