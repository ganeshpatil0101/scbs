# Mockup — नवीन खाते (बचत)

| Property | Value |
|---|---|
| Spec | [new-savings-account-screen.md](../../../savings/new-savings-account-screen.md) |
| Status | **Draft** |
| Created | 2026-07-12 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Notes

- Reference screenshots: Tab 1 `screenshots/bachat/डॅशबोर्ड-बचत-नवीन खाते.png`; Tab 3 `…-परिचयकर्ता.png`, `…-खाते-चालविण्याची-सूचना.png`.
- Tab 2 (Nominee) hidden by default; shown when Tab 1's `वारसदार जोडा` checkbox is checked. Nominee = Customer search + **+ नवीन ग्राहक जोडा** quick-add popup per [quick-add-customer-pattern.md](../../../shared/quick-add-customer-pattern.md).
- Tab 3 (Joint Holder) hidden by default; shown when Tab 1's `संयुक्त खातेदार जोडा` checkbox is checked. Introducer section removed per bank review.
- Status dropdown: `चालू` / `बंद` / `स्थगित` (confirmed 2026-07-21). Scheme loaded dynamically from master — sample `सेव्हिंग ठेव` (not a fixed enum).
- Removed fields (2026-07-18): Agent Branch, Agent, Account Category, Sales Agent Branch, Sales Agent; customer summary limited to विशेष सूचना only.
- प्रगत सेटिंग्ज collapsed by default (`<details>`).

## Review checklist

- [ ] All Tab 1 fields present with correct grouping (15 spec fields)
- [ ] `वारसदार जोडा` checkbox shows/hides Nominee tab
- [ ] Nominee tab: customer autocomplete + quick-add popup + simplified grid
- [ ] Customer summary shows विशेष सूचना only after autocomplete
- [ ] Joint Holder tab appears only when checkbox checked
- [ ] Marathi labels clear for non-technical bank staff
- [ ] Required fields marked with *
- [ ] Advanced Settings placement approved
- [ ] Tab 3 joint holder fields and operating instructions approved

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen new-savings-account-screen`.
