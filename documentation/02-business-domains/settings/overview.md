# Settings — Business Domain Overview

## Purpose

Business rules, use cases, and workflows for **सेटिंग्ज (Settings)** — master data and product configuration that gates all operational modules. Mirrors the `05-ui-ux/settings/` sub-module structure.

## Scope

| Sub-area | UI path | Business domain path | Status |
| :--- | :--- | :--- | :---: |
| Master | [05-ui-ux/settings/master/](../05-ui-ux/settings/master/overview.md) | [master/](master/overview.md) | Done |
| Accounting | [05-ui-ux/settings/accounting/](../05-ui-ux/settings/accounting/overview.md) | [accounting/](accounting/overview.md) | Done |
| Schemes | [05-ui-ux/settings/schemes/](../05-ui-ux/settings/schemes/overview.md) | [schemes/](schemes/overview.md) | Done |
| Membership | [05-ui-ux/settings/membership/](../05-ui-ux/settings/membership/overview.md) | [membership/](membership/overview.md) | Done |
| Loan | [05-ui-ux/settings/loan/](../05-ui-ux/settings/loan/overview.md) | [loan/](loan/overview.md) | Done |

## Dependencies

- [glossary.md](../00-project-overview/glossary.md) — User, Role, Employee, Branch, Organization terms
- [system-boundaries.md](../00-project-overview/system-boundaries.md) — JWT auth, RBAC in scope for v1
- [Customer domain](../customer/overview.md) — for Staff & System Access, employee linked to Customer record

## Related Documents

- [../overview.md](../overview.md)
- [master/overview.md](master/overview.md)
- [accounting/overview.md](accounting/overview.md)
- [schemes/overview.md](schemes/overview.md)
- [membership/overview.md](membership/overview.md)
- [loan/overview.md](loan/overview.md)
- [master/default-role-templates.md](master/default-role-templates.md) — Tenant seed Roles (Clerk / Cashier / Manager)
- [../00-project-overview/tenant-setup.md](../00-project-overview/tenant-setup.md) — New tenant bootstrap checklist
- [../05-ui-ux/settings/overview.md](../05-ui-ux/settings/overview.md)
- [../AI_INDEX.md](../AI_INDEX.md)
