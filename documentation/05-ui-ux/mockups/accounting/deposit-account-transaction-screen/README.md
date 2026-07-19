# Mockup — ठेव खाते व्यवहार

| Property | Value |
|---|---|
| Spec | [deposit-account-transaction-screen.md](../../../accounting/deposit-account-transaction-screen.md) |
| Status | **Draft** |
| Created | 2026-07-18 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Review checklist

- [ ] मॉड्यूल निवडा radio switches visible fields correctly (बचत / मुदत ठेव / डेली / रिकरिंग)
- [ ] All 4 tabs present: खात्याची माहिती, साहित्य तपशील, ट्रान्सफर, ग्राहक तपशील
- [ ] Ledger and KYC tabs removed (no खातेवही, no केवायसी माहिती)
- [ ] Daily Loan Information tab removed — loan rows in Customer Details tab
- [ ] Customer Details: बचत/डेली as separate cards; रिकरिंग/मुदत ठेव/कर्ज as separate grids
- [ ] No फोटो / सही दाखवा link on Tab 1
- [ ] धनादेश प्रकार: स्लिप, चेक
- [ ] बँक निवडा is Autocomplete with Bank Master samples
- [ ] पूर्ण केवायसी shows address grid (not editable address fields)
- [ ] Marathi labels clear for non-technical bank staff
- [ ] Required fields marked with *
- [ ] Responsive on mobile and desktop
- [ ] Branch/GL/Account Holder use single Autocomplete controls

## Supersedes

This mockup replaces module-specific transaction mockups:

- [savings-transaction-screen](../../savings/savings-transaction-screen/)
- [fd-transaction-screen](../../fixed-deposit/fd-transaction-screen/)
- [daily-transaction-screen](../../daily/daily-transaction-screen/)
- [recurring-transaction-screen](../../recurring/recurring-transaction-screen/)

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen deposit-account-transaction-screen`.
