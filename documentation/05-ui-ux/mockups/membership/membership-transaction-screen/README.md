# Mockup — सभासदत्व व्यवहार

| Property | Value |
|---|---|
| Spec | [membership-transaction-screen.md](../../../membership/membership-transaction-screen.md) |
| Status | **Draft** |
| Created | 2026-07-12 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Review checklist

- [ ] All spec fields present with correct grouping
- [ ] Marathi labels clear for non-technical bank staff
- [ ] Required fields marked with *
- [ ] Responsive on mobile (single column) and desktop (two columns, centered)
- [ ] Grid columns match spec (Tab 1 certificate grid, Tab 3 transfer, Tab 6 three share grids)
- [ ] Tab structure approved — visibility notes on tab bar match mode rules
- [ ] Debit withdrawal section hidden by default (जमा mode); visible when नावे selected
- [ ] प्रगत सेटिंग्ज collapsed by default
- [ ] KYC preview placeholder toggles on Tab 1
- [ ] Tab 5 (Nominee) shows scaffold note only

## Tab visibility (production)

| Tab | Visible when |
|---|---|
| 1 खात्याची माहिती | Always |
| 2 साहित्य तपशील | Transfer mode |
| 3 ट्रान्सफर | Transfer mode |
| 4 शेअर्स वाटप | Credit (जमा) mode |
| 5 वारसदाराची माहिती | Always (scaffold) |
| 6 शेअर्सची माहिती | Always |

**Mockup note:** All 6 tabs are shown in the tab bar for layout review; amber sublabels indicate conditional visibility.

## Notes

- Tab 5 defers to `app-nominee-form` per [new-membership-screen.md](../../../membership/new-membership-screen.md) Tab 3.
- **Removed (2026-07-22):** Tab 7 (KYC Information) — was a scaffold referencing the now-superseded Savings KYC pattern.
- **Resolved (2026-07-22):** `बँक निवडा` → Autocomplete from Bank Master; `शेअर्स सिरीज` → अ वर्ग / ब वर्ग (reused Share Class enum).

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen membership-transaction-screen`.
