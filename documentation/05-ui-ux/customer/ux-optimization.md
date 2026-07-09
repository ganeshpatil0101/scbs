# Customer Module — UX Optimization Audit

Audit date: 2026-07-09. Applied: 2026-07-09. Domain: `documentation/05-ui-ux/customer/`.

Patterns applied: [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md), [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md).

Reference implementation: [../settings/ux-optimization.md](../settings/ux-optimization.md).

## Summary

| Metric | Before | After |
| :--- | :---: | :---: |
| Menu screens | 4 | 3 |
| Tabs (Other Account Management) | — | 2 |
| Duplicate branch controls removed | — | 4 screens |
| Fields → Auto-fill (Organization) | — | 3 screens |
| Fields → Advanced | — | 8 (New Customer) + Masters Passing + 14 grid cols |
| Conditional visibility | — | 1 (Date of Death) |
| Customer Autocomplete | — | Documented in entity pattern + Tab 1 |

## Consolidated Screen Map

| New / kept screen | Replaces | Document |
| :--- | :--- | :--- |
| ग्राहक यादी (Customer List) | (field cleanup) | [customer-list-screen.md](customer-list-screen.md) |
| नवीन ग्राहक (New Customer) | (field cleanup) | [new-customer-screen.md](new-customer-screen.md) |
| इतर खाते व्यवस्थापन (Other Account Management) | New Other Account + Other Account Registration | [other-account-management-screen.md](other-account-management-screen.md) |

### Tab layout (Other Account Management)

| Tab | Marathi | English | Functionality |
| :---: | :--- | :--- | :--- |
| 1 | नवीन खाते | New Account | Customer Autocomplete + account type → open |
| 2 | नोंदणी यादी | Registration List | Bulk list / status / remove |

---

## Decisions Applied (2026-07-09)

| # | Decision |
| :---: | :--- |
| 1 | Merge Other Accounts → one screen, 2 tabs |
| 2 | Organization = session header (same as Bank) |
| 3 | New Customer Branch = editable Autocomplete |
| 4 | Date of Death hidden until Status = `मृत` |
| 5 | Education + parents/spouse → प्रगत सेटिंग्ज |
| 6 | Alerts + Nominee → प्रगत सेटिंग्ज |
| 7 | Customer List default grid = identity + contact only |
| 8 | Tab 1 customer pick = Customer Autocomplete (not name + range) |
| 9 | Tab 1 title = `ग्राहक तपशील` |
| 10 | Customer added to entity-autocomplete-pattern |

---

## Action Checklist (all applied)

### High priority

- [x] Consolidate New Other Account + Other Account Registration → other-account-management-screen.md
- [x] Organization → Auto-fill header on list/filter screens
- [x] Branch Autocomplete + Branch Dropdown → single Autocomplete
- [x] New Customer: editable Branch Autocomplete
- [x] Date of Death: conditional visibility (Status = मृत)
- [x] Remove duplicate KYC Aadhaar photo row
- [x] Tab 1: Customer Autocomplete replaces Name + No. range
- [x] Superseded banners on old other-account specs

### Medium priority

- [x] Education / family names / alerts / nominee → प्रगत सेटिंग्ज
- [x] Masters Passing → Advance Search
- [x] Customer List secondary columns → Details / Export
- [x] Rename Tab 1 to ग्राहक तपशील
- [x] Extend entity-autocomplete-pattern for Customer
- [x] Fix broken dividend-calculation link → membership-configuration-screen
- [x] Renumber New Customer fields

### Low priority

- [x] Generate HTML mockups for current Customer screens (2026-07-09)
- [x] New Customer KYC → document cards (Option A) instead of grid (2026-07-10)

---

## Deprecated Specs (reference only)

| Superseded spec | New spec |
| :--- | :--- |
| [new-other-account-screen.md](new-other-account-screen.md) | [other-account-management-screen.md](other-account-management-screen.md) — Tab 1 |
| [other-account-registration-screen.md](other-account-registration-screen.md) | [other-account-management-screen.md](other-account-management-screen.md) — Tab 2 |

---

## Apply Status

| Phase | Status |
| :--- | :--- |
| Phase 1 — Audit | Complete |
| Phase 2 — Plan | Complete |
| Phase 3 — Apply to specs | **Complete (2026-07-09)** |
| Phase 4 — Mockups | **Complete (Draft, 2026-07-09)** |

---

## Related Documents

- [overview.md](overview.md)
- [other-account-management-screen.md](other-account-management-screen.md)
- [changelog.md](changelog.md)
- [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
- [../settings/ux-optimization.md](../settings/ux-optimization.md)
- [../../AI_INDEX.md](../../AI_INDEX.md)
