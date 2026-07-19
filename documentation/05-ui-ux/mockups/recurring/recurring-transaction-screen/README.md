# Mockup — व्यवहार (रिकरिंग)

> **Superseded (2026-07-18):** Use unified mockup [deposit-account-transaction-screen](../../accounting/deposit-account-transaction-screen/) instead. Spec: [deposit-account-transaction-screen.md](../../../accounting/deposit-account-transaction-screen.md).

| Property | Value |
|---|---|
| Spec | ~~[recurring-transaction-screen.md](../../../recurring/recurring-transaction-screen.md)~~ → [deposit-account-transaction-screen.md](../../../accounting/deposit-account-transaction-screen.md) |
| Status | **Superseded** |
| Created | 2026-07-12 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Notes

- Reference media `screenshots/रिकरिंग/` not in repo — layout is spec-driven.
- Tabs 2–3 are TODO stubs; Tab 4 ledger grid deferred to shared component.
- Debit mode Tab 1 shows TODO placeholder until screenshots captured.

## Review checklist

- [ ] नावे / जमा mode and credit-only fields visibility approved
- [ ] Summary panel grouping clear for staff
- [ ] Marathi labels clear for non-technical bank staff
- [ ] Required fields marked with *
- [ ] Tab navigation and footer actions approved
- [ ] KYC tab fields match spec

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen recurring-transaction-screen`.
