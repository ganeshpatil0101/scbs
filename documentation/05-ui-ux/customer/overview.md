# Customer Screens Overview

## Purpose

Index of UI screen specifications under **ग्राहक (Customer)**. Each linked document is self-contained for AI agents generating frontend screens.

**UX optimized (2026-07-09):** 4 menu screens → 3. Audit: [ux-optimization.md](ux-optimization.md).

Branch and Customer lookups use a single **Autocomplete** field — see [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md).

## Current Screens

| Screen (Marathi) | Screen (English) | Document |
| :--- | :--- | :--- |
| ग्राहक यादी | Customer List | [customer-list-screen.md](customer-list-screen.md) |
| नवीन ग्राहक | New Customer | [new-customer-screen.md](new-customer-screen.md) |
| इतर खाते व्यवस्थापन | Other Account Management | [other-account-management-screen.md](other-account-management-screen.md) |

### Tabs (Other Account Management)

| Tab (Marathi) | Tab (English) | Functionality |
| :--- | :--- | :--- |
| नवीन खाते | New Account | Select customer + account type → open |
| नोंदणी यादी | Registration List | Bulk list + status update + remove |

## Superseded Screens

| Superseded spec | Consolidated into |
| :--- | :--- |
| [new-other-account-screen.md](new-other-account-screen.md) | [other-account-management-screen.md](other-account-management-screen.md) — Tab 1 |
| [other-account-registration-screen.md](other-account-registration-screen.md) | [other-account-management-screen.md](other-account-management-screen.md) — Tab 2 |

## Screenshot Location

```text
screenshots/grahak_khatedar/
```

## Common Patterns

- **Breadcrumb root:** `डॅशबोर्ड > ग्राहक > <Screen>`
- **Required-field legend:** `(*) आवश्यक फील्ड दर्शविते`
- **Organization:** session auto-fill in header (not in filter bars)
- **Branch / Customer:** single Autocomplete per [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)

## Mockups (Draft)

| Screen | Mockup |
| :--- | :--- |
| ग्राहक यादी | [mockups/customer/customer-list-screen/](../mockups/customer/customer-list-screen/) |
| नवीन ग्राहक | [mockups/customer/new-customer-screen/](../mockups/customer/new-customer-screen/) |
| इतर खाते व्यवस्थापन | [mockups/customer/other-account-management-screen/](../mockups/customer/other-account-management-screen/) |

## Related Documents

- [ux-optimization.md](ux-optimization.md)
- [changelog.md](changelog.md)
- [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md)
- [../membership/overview.md](../membership/overview.md)
- [../../02-business-domains/customer/overview.md](../../02-business-domains/customer/overview.md) — Business rules, use cases, workflows, acceptance tests
- [../../AI_INDEX.md](../../AI_INDEX.md)
