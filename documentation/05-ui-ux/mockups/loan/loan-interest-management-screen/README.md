# Mockup — व्याज व्यवस्थापन (कर्ज)

| Property | Value |
|---|---|
| Spec | [loan-interest-management-screen.md](../../../loan/loan-interest-management-screen.md) |
| Status | **Draft** |
| Created | 2026-07-12 |
| Language | Marathi only (English via ngx-translate in Angular phase) |
| Consolidates | loan-manual-interest-provision-screen, loan-scheduled-interest-assessment-screen |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Notes

- Reference screenshots under `screenshots/कर्ज/` not verified in repo — mockup is spec-driven.
- Shared filter + results grid across both tabs; primary footer action changes: **तरतूद** (Tab 1) / **पोस्टिंग** (Tab 2).
- व्याज दिनांक निवडा full list marked TODO per spec.
- Tab 2 adds matured-loan checkbox and अॅडव्हान्स शोध link.

## Review checklist

- [ ] Shared filter: Branch/GL Autocomplete, Interest Date (TODO list), Post Date, Account From/To
- [ ] Tab 2 extras: परिपक्व कर्जासाठी checkbox, अॅडव्हान्स शोध link
- [ ] Grid: all 12 columns; व्याज and दंड व्याज editable
- [ ] Summary totals: तरतूद, व्याज, दंड तरतूद, दंड व्याज, शिल्लक
- [ ] Tab 1: primary तरतूद, secondary पुनश्चरचना करा, grid निश्चित करा
- [ ] Tab 2: primary पोस्टिंग, secondary पुनरावलोकन करा, grid डिनिवड करा
- [ ] Marathi labels; required markers
- [ ] Responsive + sticky footer

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen loan-interest-management-screen`.
