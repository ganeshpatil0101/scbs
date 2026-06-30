# AI Index — CBS SaaS Platform Documentation

Top-level index of all project documentation. Add a link here whenever a new module or document is created.

## 00 — Project Overview
- [00-project-overview/vision.md](00-project-overview/vision.md) — Problem statement, vision, target market, competitive positioning
- [00-project-overview/business-goals.md](00-project-overview/business-goals.md) — Numbered, measurable business goals (BG-001 to BG-008)
- [00-project-overview/changelog.md] - ChangeLog
- [00-project-overview/glossary.md](00-project-overview/glossary.md) — TODO: not yet authored
- [00-project-overview/system-boundaries.md](00-project-overview/system-boundaries.md) — TODO: not yet authored

## 01 — Architecture
- [01-architecture/architecture-overview.md](01-architecture/architecture-overview.md) — Infra architecture, multi-tenancy decision, request flow, cost efficiency

## 05 — UI/UX — Mockups (HTML prototypes for bank review)

Layout-only HTML mockups generated from `*-screen.md` specs via `@generate-ui-mockup`. Tailwind CSS v4 (CDN), Marathi labels, centered responsive layout. Shareable in any browser; after approval, use `@generate-ui-screen` for Angular + full i18n.

- [05-ui-ux/mockups/_shared/mockup-base.css](05-ui-ux/mockups/_shared/mockup-base.css) — Shared Tailwind `@theme` tokens and component classes
- [05-ui-ux/mockups/settings/master/new-user-screen/](05-ui-ux/mockups/settings/master/new-user-screen/) — नवीन युजर (Draft)

## 05 — UI/UX — Customer
- [05-ui-ux/customer/overview.md](05-ui-ux/customer/overview.md) — Index of Customer screens
- [05-ui-ux/customer/customer-list-screen.md](05-ui-ux/customer/customer-list-screen.md) — ग्राहक यादी
- [05-ui-ux/customer/new-customer-screen.md](05-ui-ux/customer/new-customer-screen.md) — नवीन ग्राहक (3 tabs, from PNG + MP4)
- [05-ui-ux/customer/new-other-account-screen.md](05-ui-ux/customer/new-other-account-screen.md) — नवीन इतर खाते
- [05-ui-ux/customer/other-account-registration-screen.md](05-ui-ux/customer/other-account-registration-screen.md) — इतर खाते नोंदणी (from MP4)

## 05 — UI/UX — Membership
- [05-ui-ux/membership/overview.md](05-ui-ux/membership/overview.md) — Index of Membership screens
- [05-ui-ux/membership/new-membership-screen.md](05-ui-ux/membership/new-membership-screen.md) — नवीन सभासदत्व (3 tabs, from PNG + MP4)
- [05-ui-ux/membership/shares-transfer-screen.md](05-ui-ux/membership/shares-transfer-screen.md) — शेअर्स ट्रान्सफर (3 tabs, from MP4)

## 05 — UI/UX — Savings (Operational)
- [05-ui-ux/savings/overview.md](05-ui-ux/savings/overview.md)
- [05-ui-ux/savings/new-savings-account-screen.md](05-ui-ux/savings/new-savings-account-screen.md) — नवीन खाते (4 tabs)
- [05-ui-ux/savings/savings-transaction-screen.md](05-ui-ux/savings/savings-transaction-screen.md) — व्यवहार (5 tabs)
- [05-ui-ux/savings/manual-interest-calculation-screen.md](05-ui-ux/savings/manual-interest-calculation-screen.md) — मॅन्युअल व्याज आकारणी

## 05 — UI/UX — Fixed Deposit (Operational)
- [05-ui-ux/fixed-deposit/overview.md](05-ui-ux/fixed-deposit/overview.md)
- [05-ui-ux/fixed-deposit/new-fd-account-screen.md](05-ui-ux/fixed-deposit/new-fd-account-screen.md) — नवीन खाते (4 tabs)
- [05-ui-ux/fixed-deposit/fd-transaction-screen.md](05-ui-ux/fixed-deposit/fd-transaction-screen.md) — व्यवहार (5 tabs)
- [05-ui-ux/fixed-deposit/fd-account-register-screen.md](05-ui-ux/fixed-deposit/fd-account-register-screen.md) — खाते रजिस्टर
- [05-ui-ux/fixed-deposit/fd-manual-interest-calculation-screen.md](05-ui-ux/fixed-deposit/fd-manual-interest-calculation-screen.md) — मॅन्युअल व्याज आकारणी
- [05-ui-ux/fixed-deposit/account-renewal-list-screen.md](05-ui-ux/fixed-deposit/account-renewal-list-screen.md) — खाते नूतनीकरण यादी
- [05-ui-ux/fixed-deposit/deposit-loan-installment-payment-screen.md](05-ui-ux/fixed-deposit/deposit-loan-installment-payment-screen.md) — ठेव कर्ज हप्ता पेमेंट (from MP4)
- [05-ui-ux/fixed-deposit/fd-interest-multiplier-screen.md](05-ui-ux/fixed-deposit/fd-interest-multiplier-screen.md) — व्याज गुणक (from MP4)

## 05 — UI/UX — Loan (Operational)
- [05-ui-ux/loan/overview.md](05-ui-ux/loan/overview.md)
- [05-ui-ux/loan/new-loan-screen.md](05-ui-ux/loan/new-loan-screen.md) — नवीन कर्ज (6 tabs, from MP4)
- [05-ui-ux/loan/new-deposit-loan-screen.md](05-ui-ux/loan/new-deposit-loan-screen.md) — नवीन ठेव कर्ज (3 tabs, from MP4)

## 05 — UI/UX — Daily (Operational)
- [05-ui-ux/daily/overview.md](05-ui-ux/daily/overview.md)
- [05-ui-ux/daily/new-daily-account-screen.md](05-ui-ux/daily/new-daily-account-screen.md) — नवीन खाते (from MP4)
- [05-ui-ux/daily/new-agent-screen.md](05-ui-ux/daily/new-agent-screen.md) — नवीन एजंट (from MP4)
- [05-ui-ux/daily/daily-transaction-screen.md](05-ui-ux/daily/daily-transaction-screen.md) — व्यवहार (6 tabs)
- [05-ui-ux/daily/account-register-screen.md](05-ui-ux/daily/account-register-screen.md) — खाते रजिस्टर
- [05-ui-ux/daily/agent-collection-screen.md](05-ui-ux/daily/agent-collection-screen.md) — एजंट कलेक्शन
- [05-ui-ux/daily/agent-collection-list-screen.md](05-ui-ux/daily/agent-collection-list-screen.md) — एजंट कलेक्शन यादी
- [05-ui-ux/daily/agent-to-agent-transfer-screen.md](05-ui-ux/daily/agent-to-agent-transfer-screen.md) — एजंट ते एजंट ट्रान्सफर
- [05-ui-ux/daily/interest-multiplier-screen.md](05-ui-ux/daily/interest-multiplier-screen.md) — व्याज गुणक

## 05 — UI/UX — Recurring (Operational)
- [05-ui-ux/recurring/overview.md](05-ui-ux/recurring/overview.md)
- [05-ui-ux/recurring/new-recurring-account-screen.md](05-ui-ux/recurring/new-recurring-account-screen.md) — नवीन खाते (from MP4)
- [05-ui-ux/recurring/credit-transaction-screen.md](05-ui-ux/recurring/credit-transaction-screen.md) — जमा व्यवहार (from MP4)
- [05-ui-ux/recurring/account-register-screen.md](05-ui-ux/recurring/account-register-screen.md) — खाते रजिस्टर
- [05-ui-ux/recurring/manual-interest-assessment-screen.md](05-ui-ux/recurring/manual-interest-assessment-screen.md) — मॅन्युअल व्याज आकारणी
- [05-ui-ux/recurring/manual-interest-provision-screen.md](05-ui-ux/recurring/manual-interest-provision-screen.md) — मॅन्युअल व्याज तरतूद
- [05-ui-ux/recurring/interest-multiplier-screen.md](05-ui-ux/recurring/interest-multiplier-screen.md) — व्याज गुणक

## 05 — UI/UX — Accounting (Operational)
- [05-ui-ux/accounting/overview.md](05-ui-ux/accounting/overview.md)
- [05-ui-ux/accounting/jama-screen.md](05-ui-ux/accounting/jama-screen.md) — जमा (from MP4)
- [05-ui-ux/accounting/nave-screen.md](05-ui-ux/accounting/nave-screen.md) — नावे (from MP4)
- [05-ui-ux/accounting/transfer-screen.md](05-ui-ux/accounting/transfer-screen.md) — ट्रान्सफर (from MP4)
- [05-ui-ux/accounting/rokhapal-screen.md](05-ui-ux/accounting/rokhapal-screen.md) — रोखपाल (from MP4)
- [05-ui-ux/accounting/multi-gl-transaction-screen.md](05-ui-ux/accounting/multi-gl-transaction-screen.md) — एकाधिक जीएल व्यवहार (from MP4)
- [05-ui-ux/accounting/note-exchange-screen.md](05-ui-ux/accounting/note-exchange-screen.md) — नोटांची अदलाबदल

## 05 — UI/UX — Settings
- [05-ui-ux/settings/overview.md](05-ui-ux/settings/overview.md) — Settings UI index

### Settings — Schemes
- [05-ui-ux/settings/schemes/overview.md](05-ui-ux/settings/schemes/overview.md) — New Scheme screens (Daily, Savings, FD, Recurring, Loan)
- [05-ui-ux/settings/schemes/daily-new-scheme-screen.md](05-ui-ux/settings/schemes/daily-new-scheme-screen.md) — डेली > नवीन योजना (5 tabs)
- [05-ui-ux/settings/schemes/savings-new-scheme-screen.md](05-ui-ux/settings/schemes/savings-new-scheme-screen.md) — बचत > नवीन योजना (3 tabs)
- [05-ui-ux/settings/schemes/fixed-deposit-new-scheme-screen.md](05-ui-ux/settings/schemes/fixed-deposit-new-scheme-screen.md) — मुदत ठेव > नवीन योजना (6 tabs)
- [05-ui-ux/settings/schemes/recurring-new-scheme-screen.md](05-ui-ux/settings/schemes/recurring-new-scheme-screen.md) — रिकरिंग > नवीन योजना (7 tabs)
- [05-ui-ux/settings/schemes/loan-new-scheme-screen.md](05-ui-ux/settings/schemes/loan-new-scheme-screen.md) — कर्ज > नवीन योजना (6 tabs, from video)

### Settings — Master
- [05-ui-ux/settings/master/overview.md](05-ui-ux/settings/master/overview.md)
- [05-ui-ux/settings/master/new-employee-screen.md](05-ui-ux/settings/master/new-employee-screen.md) — नवीन कर्मचारी
- [05-ui-ux/settings/master/new-user-screen.md](05-ui-ux/settings/master/new-user-screen.md) — नवीन युजर
- [05-ui-ux/settings/master/user-role-screen.md](05-ui-ux/settings/master/user-role-screen.md) — युजर रोल

### Settings — Accounting
- [05-ui-ux/settings/accounting/overview.md](05-ui-ux/settings/accounting/overview.md)
- [05-ui-ux/settings/accounting/new-gl-group-screen.md](05-ui-ux/settings/accounting/new-gl-group-screen.md) — नवीन जी.एल ग्रुप
- [05-ui-ux/settings/accounting/new-gl-head-screen.md](05-ui-ux/settings/accounting/new-gl-head-screen.md) — नवीन जी. एल. हेड (from MP4)

### Settings — Membership
- [05-ui-ux/settings/membership/overview.md](05-ui-ux/settings/membership/overview.md)
- [05-ui-ux/settings/membership/dividend-calculation-screen.md](05-ui-ux/settings/membership/dividend-calculation-screen.md) — लाभांश आकारणी
- [05-ui-ux/settings/membership/share-rules-screen.md](05-ui-ux/settings/membership/share-rules-screen.md) — शेअर्स नियम

### Settings — Loan
- [05-ui-ux/settings/loan/overview.md](05-ui-ux/settings/loan/overview.md)
- [05-ui-ux/settings/loan/loan-interest-rate-change-screen.md](05-ui-ux/settings/loan/loan-interest-rate-change-screen.md) — व्याज दरात बदल

## Status
Project Overview now has vision.md and business-goals.md authored (problem statement, target market, business model, success metrics, competitive context). glossary.md and system-boundaries.md remain TODO. Architecture documentation exists. UI screen specs added from `screenshots/` (customer, membership, savings, fixed deposit, loan, daily, recurring, accounting, settings). Backend business modules have not been started yet.
