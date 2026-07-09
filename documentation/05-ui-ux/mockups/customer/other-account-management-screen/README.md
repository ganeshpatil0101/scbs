# Mockup — इतर खाते व्यवस्थापन

| Property | Value |
|---|---|
| Spec | [other-account-management-screen.md](../../../customer/other-account-management-screen.md) |
| Status | **Draft** |
| Created | 2026-07-09 |
| Language | Marathi only (English via ngx-translate in Angular phase) |
| Replaces | new-other-account-screen, other-account-registration-screen |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Review checklist

- [ ] 2 tabs: नवीन खाते / नोंदणी यादी
- [ ] संस्था read-only in header
- [ ] Tab 1: Branch Autocomplete + Customer Autocomplete + Account-by-Customer
- [ ] Tab 1: Selected customer summary (read-only labels)
- [ ] Tab 2: Primary search with Branch Autocomplete + range filters
- [ ] Tab 2: Grid columns match spec; सर्व निवडा + काढा
- [ ] Tab 2: खाते स्थिती panel visible only when row(s) selected
- [ ] Marathi labels clear for non-technical bank staff
- [ ] Required fields marked with *
- [ ] Responsive on mobile and desktop
- [ ] Sticky footer present

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen other-account-management-screen`.
