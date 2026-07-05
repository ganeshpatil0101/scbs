# Settings Module — UX Optimization Audit

Audit date: 2026-07-05. Reference implementation for `@optimize-ui-ux` on other `05-ui-ux/` domains.

## Summary

| Metric | Before | After |
| :--- | :---: | :---: |
| Menu screens | 13 | 6 |
| Field removals | — | 7 |
| Fields → Advanced | — | 20 |
| Fields simplified / auto-fill | — | 11 |
| Shared components identified | — | 5 |

## Consolidated Screen Map

| New screen | Replaces | Document |
| :--- | :--- | :--- |
| Staff & System Access | New Employee + New User | [master/staff-system-access-screen.md](master/staff-system-access-screen.md) |
| User Role | (unchanged) | [master/user-role-screen.md](master/user-role-screen.md) |
| GL Account Setup | New GL Group + New GL Head | [accounting/gl-account-setup-screen.md](accounting/gl-account-setup-screen.md) |
| Membership Configuration | Share Rules + Dividend Calculation | [membership/membership-configuration-screen.md](membership/membership-configuration-screen.md) |
| New Scheme (unified) | Daily / Savings / FD / Recurring / Loan scheme screens | [schemes/new-scheme-screen.md](schemes/new-scheme-screen.md) |
| Interest Rate Change | Interest Rate Change (history collapsed) | [loan/loan-interest-rate-change-screen.md](loan/loan-interest-rate-change-screen.md) |

## Action Checklist (all applied in specs)

### High priority

- [x] Remove Director/Staff radio from New User (was already marked skip)
- [x] Remove Category dropdown from Loan Scheme Tab 2
- [x] GL Head No. → read-only on all scheme screens
- [x] Customer No. + Name → single Customer Autocomplete on Staff screen
- [x] Merge New Employee + New User → Staff & System Access
- [x] Document shared Interest Posting component
- [x] Document shared Rate Slab Editor component
- [x] Merge GL Group + GL Head → GL Account Setup

### Medium priority

- [x] Unicode Name → Advanced on GL Group & GL Head
- [x] Short Name, Receipt Series, Broken Period → Advanced on FD
- [x] Monthly Billing Cycle Day hidden unless Credit Card loan type
- [x] Cash Deposit / Intra-Branch limits → Advanced on User tab
- [x] Merge Share Rules + Dividend → Membership Configuration
- [x] Unified New Scheme screen with Scheme Type selector
- [x] Remove Share Amount After Limit Transfer (no values)
- [x] Interest Rate Change history → collapsible section (not separate tab)

### Low priority

- [x] Recurring Salary Payment tab → Advanced tab
- [x] Interest Rate Agent Account → Advanced on Recurring
- [x] Moratorium / post-interest fields → Advanced on Loan scheme
- [x] Tooltips required on DP, OIR, Broken Period fields (noted in spec Notes)

## Deprecated Specs (reference only)

| Superseded spec | New spec |
| :--- | :--- |
| [master/new-employee-screen.md](master/new-employee-screen.md) | [master/staff-system-access-screen.md](master/staff-system-access-screen.md) |
| [master/new-user-screen.md](master/new-user-screen.md) | [master/staff-system-access-screen.md](master/staff-system-access-screen.md) |
| [accounting/new-gl-group-screen.md](accounting/new-gl-group-screen.md) | [accounting/gl-account-setup-screen.md](accounting/gl-account-setup-screen.md) |
| [accounting/new-gl-head-screen.md](accounting/new-gl-head-screen.md) | [accounting/gl-account-setup-screen.md](accounting/gl-account-setup-screen.md) |
| [membership/share-rules-screen.md](membership/share-rules-screen.md) | [membership/membership-configuration-screen.md](membership/membership-configuration-screen.md) |
| [membership/dividend-calculation-screen.md](membership/dividend-calculation-screen.md) | [membership/membership-configuration-screen.md](membership/membership-configuration-screen.md) |
| [schemes/daily-new-scheme-screen.md](schemes/daily-new-scheme-screen.md) | [schemes/new-scheme-screen.md](schemes/new-scheme-screen.md) |
| [schemes/savings-new-scheme-screen.md](schemes/savings-new-scheme-screen.md) | [schemes/new-scheme-screen.md](schemes/new-scheme-screen.md) |
| [schemes/fixed-deposit-new-scheme-screen.md](schemes/fixed-deposit-new-scheme-screen.md) | [schemes/new-scheme-screen.md](schemes/new-scheme-screen.md) |
| [schemes/recurring-new-scheme-screen.md](schemes/recurring-new-scheme-screen.md) | [schemes/new-scheme-screen.md](schemes/new-scheme-screen.md) |
| [schemes/loan-new-scheme-screen.md](schemes/loan-new-scheme-screen.md) | [schemes/new-scheme-screen.md](schemes/new-scheme-screen.md) |

## Related Documents

- [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md)
- [overview.md](overview.md)
- [../../AI_INDEX.md](../../AI_INDEX.md)
