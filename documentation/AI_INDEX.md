# AI Index — CBS SaaS Platform Documentation

Top-level index of all project documentation. Add a link here whenever a new module or document is created.

## 00 — Project Overview
- [00-project-overview/vision.md](00-project-overview/vision.md) — Problem statement, vision, target market, competitive positioning
- [00-project-overview/business-goals.md](00-project-overview/business-goals.md) — Numbered, measurable business goals (BG-001 to BG-008)
- [00-project-overview/changelog.md] - ChangeLog
- [00-project-overview/glossary.md](00-project-overview/glossary.md) — Platform, commercial, accounting, membership, and product term definitions
- [00-project-overview/system-boundaries.md](00-project-overview/system-boundaries.md) — In-scope / out-of-scope / deferred features for v1 and future phases

## 01 — Architecture
- [01-architecture/architecture-overview.md](01-architecture/architecture-overview.md) — Infra architecture (AWS `ap-south-1`), multi-tenancy decision, request flow, cost efficiency

## 05 — UI/UX — Shared Patterns
- [05-ui-ux/shared/entity-autocomplete-pattern.md](05-ui-ux/shared/entity-autocomplete-pattern.md) — Branch / GL / Account Holder / Customer Autocomplete standard
- [05-ui-ux/shared/ui-simplification-patterns.md](05-ui-ux/shared/ui-simplification-patterns.md) — UX simplification patterns for non-technical bank staff

## 05 — UI/UX — Mockups (HTML prototypes for bank review)

Layout-only HTML mockups generated from `*-screen.md` specs via `@generate-ui-mockup`. Tailwind CSS v4 (CDN), Marathi labels, centered responsive layout. Shareable in any browser; after approval, use `@generate-ui-screen` for Angular + full i18n.

- [05-ui-ux/mockups/shared/mockup-base.css](05-ui-ux/mockups/shared/mockup-base.css) — Shared Tailwind `@theme` tokens and component classes

**Bank mockups (2026-07-08 UX consolidation — 1 screen):**

- [05-ui-ux/mockups/bank/bank-management-screen/](05-ui-ux/mockups/bank/bank-management-screen/) — बँक व्यवस्थापन (Draft)

**Customer mockups (2026-07-09 UX consolidation — 3 screens):**

- [05-ui-ux/mockups/customer/customer-list-screen/](05-ui-ux/mockups/customer/customer-list-screen/) — ग्राहक यादी (Draft)
- [05-ui-ux/mockups/customer/new-customer-screen/](05-ui-ux/mockups/customer/new-customer-screen/) — नवीन ग्राहक (Draft)
- [05-ui-ux/mockups/customer/other-account-management-screen/](05-ui-ux/mockups/customer/other-account-management-screen/) — इतर खाते व्यवस्थापन (Draft)

**Investment mockups (2026-07-11 UX consolidation — 4 screens):**

- [05-ui-ux/mockups/investment/bank-deposit-bank-management-screen/](05-ui-ux/mockups/investment/bank-deposit-bank-management-screen/) — बँक ठेव बँक व्यवस्थापन (Draft)
- [05-ui-ux/mockups/investment/bank-deposit-new-account-screen/](05-ui-ux/mockups/investment/bank-deposit-new-account-screen/) — नवीन खाते (Draft)
- [05-ui-ux/mockups/investment/bank-deposit-transaction-screen/](05-ui-ux/mockups/investment/bank-deposit-transaction-screen/) — व्यवहार (Draft)
- [05-ui-ux/mockups/investment/bank-deposit-interest-management-screen/](05-ui-ux/mockups/investment/bank-deposit-interest-management-screen/) — व्याज व्यवस्थापन (Draft)

**Loan mockups (2026-07-12 UX consolidation — 6 screens):**

- [05-ui-ux/mockups/loan/new-loan-screen/](05-ui-ux/mockups/loan/new-loan-screen/) — नवीन कर्ज (Draft)
- [05-ui-ux/mockups/loan/new-deposit-loan-screen/](05-ui-ux/mockups/loan/new-deposit-loan-screen/) — नवीन ठेव कर्ज (Draft)
- [05-ui-ux/mockups/loan/loan-information-screen/](05-ui-ux/mockups/loan/loan-information-screen/) — कर्ज माहिती (Draft)
- [05-ui-ux/mockups/loan/loan-account-register-screen/](05-ui-ux/mockups/loan/loan-account-register-screen/) — खाते रजिस्टर (Draft)
- [05-ui-ux/mockups/loan/loan-transaction-screen/](05-ui-ux/mockups/loan/loan-transaction-screen/) — कर्ज व्यवहार (Draft)
- [05-ui-ux/mockups/loan/loan-interest-management-screen/](05-ui-ux/mockups/loan/loan-interest-management-screen/) — व्याज व्यवस्थापन (Draft)

**Settings mockups (2026-07-05 UX consolidation — 6 screens):**

- [05-ui-ux/mockups/settings/master/staff-system-access-screen/](05-ui-ux/mockups/settings/master/staff-system-access-screen/) — कर्मचारी व सिस्टम प्रवेश (Draft)
- [05-ui-ux/mockups/settings/master/user-role-screen/](05-ui-ux/mockups/settings/master/user-role-screen/) — युजर रोल (Draft)
- [05-ui-ux/mockups/settings/accounting/gl-account-setup-screen/](05-ui-ux/mockups/settings/accounting/gl-account-setup-screen/) — जी.एल. खाते सेटअप (Draft)
- [05-ui-ux/mockups/settings/membership/membership-configuration-screen/](05-ui-ux/mockups/settings/membership/membership-configuration-screen/) — सभासदत्व सेटिंग्ज (Draft)
- [05-ui-ux/mockups/settings/schemes/new-scheme-screen/](05-ui-ux/mockups/settings/schemes/new-scheme-screen/) — नवीन योजना unified (Draft)
- [05-ui-ux/mockups/settings/loan/loan-interest-rate-change-screen/](05-ui-ux/mockups/settings/loan/loan-interest-rate-change-screen/) — व्याज दरात बदल (Draft)

## 05 — UI/UX — Customer

**UX optimized (2026-07-09):** 4 screens → 3. Audit: [05-ui-ux/customer/ux-optimization.md](05-ui-ux/customer/ux-optimization.md)

- [05-ui-ux/customer/overview.md](05-ui-ux/customer/overview.md) — Index of Customer screens (current)
- [05-ui-ux/customer/ux-optimization.md](05-ui-ux/customer/ux-optimization.md) — UX audit and action checklist
- [05-ui-ux/customer/customer-list-screen.md](05-ui-ux/customer/customer-list-screen.md) — ग्राहक यादी
- [05-ui-ux/customer/new-customer-screen.md](05-ui-ux/customer/new-customer-screen.md) — नवीन ग्राहक (3 tabs)
- [05-ui-ux/customer/other-account-management-screen.md](05-ui-ux/customer/other-account-management-screen.md) — इतर खाते व्यवस्थापन (2 tabs)
- ~~new-other-account-screen.md~~ / ~~other-account-registration-screen.md~~ → superseded by other-account-management-screen.md

## 05 — UI/UX — Membership
- [05-ui-ux/membership/overview.md](05-ui-ux/membership/overview.md) — Index of Membership screens
- [05-ui-ux/membership/new-membership-screen.md](05-ui-ux/membership/new-membership-screen.md) — नवीन सभासदत्व (3 tabs, from PNG + MP4)
- [05-ui-ux/membership/member-register-screen.md](05-ui-ux/membership/member-register-screen.md) — सभासद रजिस्टर (from PNG `02_07`)
- [05-ui-ux/membership/membership-transaction-screen.md](05-ui-ux/membership/membership-transaction-screen.md) — सभासदत्व व्यवहार (7 tabs, from PNG `02_07`)
- [05-ui-ux/membership/dividend-transaction-screen.md](05-ui-ux/membership/dividend-transaction-screen.md) — लाभांश व्यवहार (6 tabs, from PNG `02_07`)
- [05-ui-ux/membership/shares-transfer-screen.md](05-ui-ux/membership/shares-transfer-screen.md) — शेअर्स ट्रान्सफर (3 tabs, from MP4 + PNG `02_07`)
- [05-ui-ux/membership/shares-transfer-list-screen.md](05-ui-ux/membership/shares-transfer-list-screen.md) — शेअर्स ट्रान्सफर यादी (from PNG `02_07`)

## 05 — UI/UX — Savings (Operational)
- [05-ui-ux/savings/overview.md](05-ui-ux/savings/overview.md)
- [05-ui-ux/savings/new-savings-account-screen.md](05-ui-ux/savings/new-savings-account-screen.md) — नवीन खाते (4 tabs)
- [05-ui-ux/savings/savings-transaction-screen.md](05-ui-ux/savings/savings-transaction-screen.md) — व्यवहार (5 tabs)
- [05-ui-ux/savings/account-register-screen.md](05-ui-ux/savings/account-register-screen.md) — खाते रजिस्टर (from PNG `05-07`)
- [05-ui-ux/savings/manual-interest-calculation-screen.md](05-ui-ux/savings/manual-interest-calculation-screen.md) — मॅन्युअल व्याज आकारणी

## 05 — UI/UX — Fixed Deposit (Operational)

**UX optimized (2026-07-11):** 7 screens → 6. Audit: [05-ui-ux/fixed-deposit/ux-optimization.md](05-ui-ux/fixed-deposit/ux-optimization.md)

- [05-ui-ux/fixed-deposit/overview.md](05-ui-ux/fixed-deposit/overview.md) — Index of Fixed Deposit screens (current)
- [05-ui-ux/fixed-deposit/ux-optimization.md](05-ui-ux/fixed-deposit/ux-optimization.md) — UX audit and action checklist
- [05-ui-ux/fixed-deposit/new-fd-account-screen.md](05-ui-ux/fixed-deposit/new-fd-account-screen.md) — नवीन खाते (4 tabs)
- [05-ui-ux/fixed-deposit/fd-transaction-screen.md](05-ui-ux/fixed-deposit/fd-transaction-screen.md) — व्यवहार (5 tabs)
- [05-ui-ux/fixed-deposit/fd-account-management-screen.md](05-ui-ux/fixed-deposit/fd-account-management-screen.md) — खाते व्यवस्थापन (2 tabs)
- [05-ui-ux/fixed-deposit/fd-manual-interest-calculation-screen.md](05-ui-ux/fixed-deposit/fd-manual-interest-calculation-screen.md) — मॅन्युअल व्याज आकारणी
- [05-ui-ux/fixed-deposit/deposit-loan-installment-payment-screen.md](05-ui-ux/fixed-deposit/deposit-loan-installment-payment-screen.md) — ठेव कर्ज हप्ता पेमेंट (from MP4)
- [05-ui-ux/fixed-deposit/fd-interest-multiplier-screen.md](05-ui-ux/fixed-deposit/fd-interest-multiplier-screen.md) — व्याज गुणक (from MP4)
- ~~fd-account-register-screen.md~~ / ~~account-renewal-list-screen.md~~ → superseded by fd-account-management-screen.md

## 05 — UI/UX — Loan (Operational)

**UX optimized (2026-07-12):** 8 screens → 6. Audit: [05-ui-ux/loan/ux-optimization.md](05-ui-ux/loan/ux-optimization.md)

- [05-ui-ux/loan/overview.md](05-ui-ux/loan/overview.md) — Index of Loan screens (current + superseded)
- [05-ui-ux/loan/ux-optimization.md](05-ui-ux/loan/ux-optimization.md) — UX audit and action checklist
- [05-ui-ux/loan/new-loan-screen.md](05-ui-ux/loan/new-loan-screen.md) — नवीन कर्ज (6 tabs)
- [05-ui-ux/loan/new-deposit-loan-screen.md](05-ui-ux/loan/new-deposit-loan-screen.md) — नवीन ठेव कर्ज (3 tabs)
- [05-ui-ux/loan/loan-information-screen.md](05-ui-ux/loan/loan-information-screen.md) — कर्ज माहिती (3 tabs)
- [05-ui-ux/loan/loan-account-register-screen.md](05-ui-ux/loan/loan-account-register-screen.md) — खाते रजिस्टर
- [05-ui-ux/loan/loan-transaction-screen.md](05-ui-ux/loan/loan-transaction-screen.md) — कर्ज व्यवहार (consolidated; Credit/Debit mode)
- [05-ui-ux/loan/loan-interest-management-screen.md](05-ui-ux/loan/loan-interest-management-screen.md) — व्याज व्यवस्थापन (consolidated; 2 tabs)
- ~~loan-credit-transaction-screen.md~~ / ~~loan-debit-transaction-screen.md~~ → superseded by loan-transaction-screen.md
- ~~loan-scheduled-interest-assessment-screen.md~~ / ~~loan-manual-interest-provision-screen.md~~ → superseded by loan-interest-management-screen.md

## 05 — UI/UX — Bank (Operational)

**UX optimized (2026-07-07):** 3 screens → 1. Audit: [05-ui-ux/bank/ux-optimization.md](05-ui-ux/bank/ux-optimization.md)

- [05-ui-ux/bank/overview.md](05-ui-ux/bank/overview.md)
- [05-ui-ux/bank/ux-optimization.md](05-ui-ux/bank/ux-optimization.md) — UX audit and action checklist
- [05-ui-ux/bank/bank-management-screen.md](05-ui-ux/bank/bank-management-screen.md) — बँक व्यवस्थापन (consolidated; 2 tabs)
- ~~bank-register-screen.md~~ / ~~new-bank-screen.md~~ / ~~check-register-screen.md~~ → superseded by bank-management-screen.md

## 05 — UI/UX — Investment (Operational)

**UX optimized (2026-07-11):** 6 screens → 4. Audit: [05-ui-ux/investment/ux-optimization.md](05-ui-ux/investment/ux-optimization.md)

- [05-ui-ux/investment/overview.md](05-ui-ux/investment/overview.md)
- [05-ui-ux/investment/ux-optimization.md](05-ui-ux/investment/ux-optimization.md) — UX audit and action checklist
- [05-ui-ux/investment/bank-deposit-bank-management-screen.md](05-ui-ux/investment/bank-deposit-bank-management-screen.md) — बँक ठेव बँक व्यवस्थापन (consolidated; 2 tabs)
- [05-ui-ux/investment/bank-deposit-new-account-screen.md](05-ui-ux/investment/bank-deposit-new-account-screen.md) — बँक ठेव > नवीन खाते
- [05-ui-ux/investment/bank-deposit-transaction-screen.md](05-ui-ux/investment/bank-deposit-transaction-screen.md) — बँक ठेव > व्यवहार (4 tabs)
- [05-ui-ux/investment/bank-deposit-interest-management-screen.md](05-ui-ux/investment/bank-deposit-interest-management-screen.md) — व्याज व्यवस्थापन (consolidated; 2 tabs)
- ~~bank-deposit-new-bank-screen.md~~ / ~~bank-deposit-bank-list-screen.md~~ → superseded by bank-deposit-bank-management-screen.md
- ~~bank-deposit-interest-assessment-screen.md~~ / ~~bank-deposit-interest-provision-screen.md~~ → superseded by bank-deposit-interest-management-screen.md

## 05 — UI/UX — Daily (Operational)

**UX optimized (2026-07-11):** 8 screens → 7. Audit: [05-ui-ux/daily/ux-optimization.md](05-ui-ux/daily/ux-optimization.md)

- [05-ui-ux/daily/overview.md](05-ui-ux/daily/overview.md) — Index of Daily screens (current)
- [05-ui-ux/daily/ux-optimization.md](05-ui-ux/daily/ux-optimization.md) — UX audit and action checklist
- [05-ui-ux/daily/new-daily-account-screen.md](05-ui-ux/daily/new-daily-account-screen.md) — नवीन खाते (from MP4)
- [05-ui-ux/daily/new-agent-screen.md](05-ui-ux/daily/new-agent-screen.md) — नवीन एजंट (from MP4)
- [05-ui-ux/daily/daily-transaction-screen.md](05-ui-ux/daily/daily-transaction-screen.md) — व्यवहार (6 tabs)
- [05-ui-ux/daily/account-register-screen.md](05-ui-ux/daily/account-register-screen.md) — खाते रजिस्टर
- [05-ui-ux/daily/agent-collection-management-screen.md](05-ui-ux/daily/agent-collection-management-screen.md) — एजंट कलेक्शन व्यवस्थापन (2 tabs)
- [05-ui-ux/daily/agent-to-agent-transfer-screen.md](05-ui-ux/daily/agent-to-agent-transfer-screen.md) — एजंट ते एजंट ट्रान्सफर
- [05-ui-ux/daily/interest-multiplier-screen.md](05-ui-ux/daily/interest-multiplier-screen.md) — व्याज गुणक
- ~~agent-collection-screen.md~~ / ~~agent-collection-list-screen.md~~ → superseded by agent-collection-management-screen.md

## 05 — UI/UX — Recurring (Operational)
- [05-ui-ux/recurring/overview.md](05-ui-ux/recurring/overview.md)
- [05-ui-ux/recurring/new-recurring-account-screen.md](05-ui-ux/recurring/new-recurring-account-screen.md) — नवीन खाते (from MP4)
- [05-ui-ux/recurring/credit-transaction-screen.md](05-ui-ux/recurring/credit-transaction-screen.md) — जमा व्यवहार (from MP4)
- [05-ui-ux/recurring/account-register-screen.md](05-ui-ux/recurring/account-register-screen.md) — खाते रजिस्टर
- [05-ui-ux/recurring/manual-interest-assessment-screen.md](05-ui-ux/recurring/manual-interest-assessment-screen.md) — मॅन्युअल व्याज आकारणी
- [05-ui-ux/recurring/manual-interest-provision-screen.md](05-ui-ux/recurring/manual-interest-provision-screen.md) — मॅन्युअल व्याज तरतूद
- [05-ui-ux/recurring/interest-multiplier-screen.md](05-ui-ux/recurring/interest-multiplier-screen.md) — व्याज गुणक

## 05 — UI/UX — Reports
- [05-ui-ux/reports/overview.md](05-ui-ux/reports/overview.md) — Index of daily-use operational and statutory reports
- [05-ui-ux/reports/balance-sheet-report.md](05-ui-ux/reports/balance-sheet-report.md) — ताळेबंद (2 pages, from PNG `Reports/`)
- [05-ui-ux/reports/daybook-report.md](05-ui-ux/reports/daybook-report.md) — रोज किर्द (3 pages, from PNG `Reports/`)
- [05-ui-ux/reports/gl-wise-report.md](05-ui-ux/reports/gl-wise-report.md) — जनरल लेजर (screen + print, from PNG `Reports/`)
- [05-ui-ux/reports/loan-statement-report.md](05-ui-ux/reports/loan-statement-report.md) — कर्ज खाते उतार (from PNG `Reports/`)
- [05-ui-ux/reports/profit-loss-statement-report.md](05-ui-ux/reports/profit-loss-statement-report.md) — नफा-तोटा पत्रक (2 pages, from PNG `Reports/`)
- [05-ui-ux/reports/purvani-report.md](05-ui-ux/reports/purvani-report.md) — पुरवणी (screen + print, from PNG `Reports/`)
- [05-ui-ux/reports/trial-balance-report.md](05-ui-ux/reports/trial-balance-report.md) — तेरीज पत्रक (3 pages, from PNG `Reports/`)

## 05 — UI/UX — Accounting (Operational)
- [05-ui-ux/accounting/overview.md](05-ui-ux/accounting/overview.md)
- [05-ui-ux/accounting/jama-screen.md](05-ui-ux/accounting/jama-screen.md) — जमा (from MP4)
- [05-ui-ux/accounting/nave-screen.md](05-ui-ux/accounting/nave-screen.md) — नावे (from MP4)
- [05-ui-ux/accounting/transfer-screen.md](05-ui-ux/accounting/transfer-screen.md) — ट्रान्सफर (from MP4)
- [05-ui-ux/accounting/rokhapal-screen.md](05-ui-ux/accounting/rokhapal-screen.md) — रोखपाल (from MP4)
- [05-ui-ux/accounting/multi-gl-transaction-screen.md](05-ui-ux/accounting/multi-gl-transaction-screen.md) — एकाधिक जीएल व्यवहार (from MP4)
- [05-ui-ux/accounting/note-exchange-screen.md](05-ui-ux/accounting/note-exchange-screen.md) — नोटांची अदलाबदल
- [05-ui-ux/accounting/contra-screen.md](05-ui-ux/accounting/contra-screen.md) — कॉन्ट्रा (2 tabs, from PNG `05-07`)
- [05-ui-ux/accounting/transaction-passing-screen.md](05-ui-ux/accounting/transaction-passing-screen.md) — व्यवहार पासिंग (from PNG `05-07`)
- [05-ui-ux/accounting/transaction-verification-screen.md](05-ui-ux/accounting/transaction-verification-screen.md) — व्यवहार तपासणी (from PNG `05-07`)

## 05 — UI/UX — Settings

**UX optimized (2026-07-05):** 13 screens → 6. Audit: [05-ui-ux/settings/ux-optimization.md](05-ui-ux/settings/ux-optimization.md)

- [05-ui-ux/settings/overview.md](05-ui-ux/settings/overview.md) — Settings UI index (current screens)
- [05-ui-ux/settings/ux-optimization.md](05-ui-ux/settings/ux-optimization.md) — UX audit and action checklist
- [05-ui-ux/settings/changelog.md](05-ui-ux/settings/changelog.md)

### Settings — Master
- [05-ui-ux/settings/master/overview.md](05-ui-ux/settings/master/overview.md)
- [05-ui-ux/settings/master/staff-system-access-screen.md](05-ui-ux/settings/master/staff-system-access-screen.md) — कर्मचारी व सिस्टम प्रवेश (consolidated)
- [05-ui-ux/settings/master/user-role-screen.md](05-ui-ux/settings/master/user-role-screen.md) — युजर रोल
- ~~new-employee-screen.md~~ → superseded by staff-system-access-screen.md
- ~~new-user-screen.md~~ → superseded by staff-system-access-screen.md

### Settings — Accounting
- [05-ui-ux/settings/accounting/overview.md](05-ui-ux/settings/accounting/overview.md)
- [05-ui-ux/settings/accounting/gl-account-setup-screen.md](05-ui-ux/settings/accounting/gl-account-setup-screen.md) — जी.एल. खाते सेटअप (consolidated)
- ~~new-gl-group-screen.md~~ / ~~new-gl-head-screen.md~~ → superseded by gl-account-setup-screen.md

### Settings — Membership
- [05-ui-ux/settings/membership/overview.md](05-ui-ux/settings/membership/overview.md)
- [05-ui-ux/settings/membership/membership-configuration-screen.md](05-ui-ux/settings/membership/membership-configuration-screen.md) — सभासदत्व सेटिंग्ज (consolidated)
- ~~share-rules-screen.md~~ / ~~dividend-calculation-screen.md~~ → superseded by membership-configuration-screen.md

### Settings — Schemes
- [05-ui-ux/settings/schemes/overview.md](05-ui-ux/settings/schemes/overview.md)
- [05-ui-ux/settings/schemes/new-scheme-screen.md](05-ui-ux/settings/schemes/new-scheme-screen.md) — नवीन योजना (unified; all product types)
- ~~daily/savings/fd/recurring/loan-new-scheme-screen.md~~ → superseded by new-scheme-screen.md

### Settings — Loan
- [05-ui-ux/settings/loan/overview.md](05-ui-ux/settings/loan/overview.md)
- [05-ui-ux/settings/loan/loan-interest-rate-change-screen.md](05-ui-ux/settings/loan/loan-interest-rate-change-screen.md) — व्याज दरात बदल (simplified)

## Status
Project Overview is complete: vision.md, business-goals.md, glossary.md, and system-boundaries.md. Architecture documentation exists. UI screen specs added from `screenshots/` (customer, membership, savings, fixed deposit, loan, daily, recurring, accounting, settings). **Settings module UX-optimized (2026-07-05):** 6 consolidated screens per [05-ui-ux/settings/ux-optimization.md](05-ui-ux/settings/ux-optimization.md). **Customer module UX-optimized (2026-07-09):** 4 → 3 screens per [05-ui-ux/customer/ux-optimization.md](05-ui-ux/customer/ux-optimization.md). **Daily module UX-optimized (2026-07-11):** 8 → 7 screens per [05-ui-ux/daily/ux-optimization.md](05-ui-ux/daily/ux-optimization.md). **Fixed Deposit module UX-optimized (2026-07-11):** 7 → 6 screens per [05-ui-ux/fixed-deposit/ux-optimization.md](05-ui-ux/fixed-deposit/ux-optimization.md). Report specs added from `screenshots/Reports/`. Reusable UX skill: `.cursor/skills/optimize-ui-ux/`. Backend business modules have not been started yet.
