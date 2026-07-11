# Mockup — बँक ठेव बँक व्यवस्थापन

| Property | Value |
|---|---|
| Spec | [bank-deposit-bank-management-screen.md](../../../investment/bank-deposit-bank-management-screen.md) |
| Status | **Draft** |
| Created | 2026-07-11 |
| Language | Marathi only (English via ngx-translate in Angular phase) |
| Replaces | bank-deposit-new-bank-screen, bank-deposit-bank-list-screen (superseded) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Notes

- Reference screenshots under `screenshots/गुंतवणूक/` were not verified in repo — mockup is spec-driven.
- Distinct from operational **बँक व्यवस्थापन** (`bank/bank-management-screen`).

## Review checklist

- [ ] Tab 1: बँक निवडा Autocomplete filter + दाखवा / + नवीन
- [ ] Tab 1: Grid columns — निवडा, अनु. क्र., खाते क्र., बँक नाव, तपशील
- [ ] Tab 2: Form opens via + नवीन (Create) or row/तपशील (Update)
- [ ] Tab 2: जीएल हेड क्र. read-only Auto-fill on Create
- [ ] Tab 2: बँक प्रकार dropdown values match spec
- [ ] Marathi labels clear for non-technical bank staff
- [ ] Required fields marked with *
- [ ] Responsive on mobile and desktop
- [ ] Sticky footer present

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen bank-deposit-bank-management-screen`.
