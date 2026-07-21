# Mockup — एजंट कलेक्शन व्यवस्थापन (डेली)

| Property | Value |
|---|---|
| Spec | [agent-collection-management-screen.md](../../../daily/agent-collection-management-screen.md) |
| Status | **Draft** |
| Created | 2026-07-16 |
| Updated | 2026-07-21 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Notes

- **4 tabs:** एजंट संकलन → संक्षिप्त तपशील → ट्रान्स्फर → कलेक्शन यादी.
- Tab 2 / Tab 3 from bank screenshots `screenshots/डेली/डॅशबोर्ड-डेली-एजंट-कलेक्शन-संक्षिप्त-तपशील.png` and `…-ट्रान्स्फर.png` (2026-07-21).
- Cheque type: `स्लिप` / `चेक`. Bank = Autocomplete from Bank Master.
- Transfer: Branch / GL / Account Holder Autocomplete; grid actions `अनियमित करा`, `निटवा`.
- Distinct from Agent-to-Agent Transfer screen.
- Module nav lists current Daily screens only (superseded व्यवहार omitted).

## Review checklist

- [ ] All 4 tabs present with correct fields
- [ ] Brief Details required fields marked *
- [ ] Transfer Autocomplete + grid match screenshot
- [ ] Marathi labels clear for non-technical bank staff
- [ ] Wizard Next/Back between tabs 1–3
- [ ] Collection List tab independent
- [ ] Responsive on mobile and desktop

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen agent-collection-management-screen`.
