# Settings — Master Sub-Area

## Purpose

Documents business rules and workflows for **मास्टर (Master)** settings: staff/employee registration, system user accounts, branch access rights, and role-based permissions. This sub-area is the Phase 1.7 template for all other business domains.

## Scope

Covers two UI screens (consolidated from four legacy screens):

| Screen | Spec | Business focus |
| :--- | :--- | :--- |
| कर्मचारी व सिस्टम प्रवेश (Staff & System Access) | [staff-system-access-screen.md](../../05-ui-ux/settings/master/staff-system-access-screen.md) | Register employee/director + grant login, branch rights, role |
| युजर रोल (User Role) | [user-role-screen.md](../../05-ui-ux/settings/master/user-role-screen.md) | Define reusable role + per-form permission matrix |

**Out of scope for this sub-area:** GL chart setup (Settings/Accounting), product schemes (Settings/Schemes), membership share rules (Settings/Membership).

## Responsibilities

- Link bank staff (Employee/Director) to an existing **Customer** identity record
- Create and maintain **User** login credentials and status
- Assign **Branch** access rights per Organization
- Define **Role** templates with All Rights / View Only / No Rights per application form
- Enforce permission model used by `*appHasPermission` across all modules (cross-cutting)

## Features

| Feature | Use case | Primary screen |
| :--- | :--- | :--- |
| Register staff with system access | UC-001 | Staff & System Access |
| Define role permission template | UC-002 | User Role |
| Assign branch rights to user | UC-001 Tab 3 | Staff & System Access |
| Configure transaction limits (advanced) | UC-001 Tab 2 Advanced | Staff & System Access |
| Seed default Roles (Clerk / Cashier / Manager) | Tenant bootstrap | [default-role-templates.md](default-role-templates.md) |

## Dependencies

| Dependency | Domain / doc | Why |
| :--- | :--- | :--- |
| Customer record | [Customer domain](../../customer/overview.md) | Tab 1 requires Customer Autocomplete |
| Branch master | Shared / Settings | Branch rights grid |
| Organization | Shared | Branch rights — society context |
| Application menu registry | Platform (Phase 2) | Permission grid row source |
| Tenant setup | [tenant-setup.md](../../00-project-overview/tenant-setup.md) | Bootstrap Roles + first admin |

## Owned Entities

| Entity | Description | DB doc status |
| :--- | :--- | :---: |
| `employee` | Staff/director linked to `customer_id` | TODO — `@design-database-schema shared` |
| `user` | Login identity (login name, password hash, status) | TODO |
| `role` | Named permission template | TODO |
| `role_permission` | Per-form permission level for a role | TODO |
| `user_branch_right` | Organization + branch access for a user | TODO |

## Open Decisions (TODO — confirm with business)

| # | Topic | Blocks |
| :---: | :--- | :--- |
| 1 | ~~Login name uniqueness (tenant-wide?)~~ — **Confirmed:** unique within tenant | BR-010 |
| 2 | ~~Password complexity / minimum length~~ — **Confirmed:** min 8, letter + digit, no history | BR-011 |
| 3 | ~~Super User bypasses role matrix or not~~ — **Confirmed:** All Rights on all forms; branch rights still enforced | BR-012 |
| 4 | ~~Minimum one branch right row required on save~~ — **Confirmed:** ≥1 required; single-branch tenant auto-assigns that branch | BR-018 |
| 5 | ~~Wizard partial save vs save-on-final-tab only~~ — **Confirmed:** create persists only on final Save (atomic) | BR-019 / WF-001 |
| 6 | ~~Tab 4 Role model~~ — **Confirmed:** select existing Role (optional create+assign); seed Clerk/Cashier/Manager | BR-020 |
| 7 | ~~Blank password on edit = keep existing~~ — **Confirmed:** blank keeps hash; non-blank must match + complexity | BR-021 |
| 8 | ~~Warn on No Rights for login-critical forms~~ — **Confirmed:** soft warning on self-lockout risk; Save allowed | BR-022 |
| 9 | ~~Unregistered form default permission~~ — **Confirmed:** No Rights (fail closed); do not block startup | BR-023 |
| 10 | Default role matrix cell values (Clerk/Cashier/Manager) | [default-role-templates.md](default-role-templates.md) — proposed; bank may adjust |

## Related Documents

- [business-rules.md](business-rules.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [default-role-templates.md](default-role-templates.md)
- [changelog.md](changelog.md)
- [../overview.md](../overview.md)
- [../../00-project-overview/tenant-setup.md](../../00-project-overview/tenant-setup.md)
- [../../05-ui-ux/settings/master/overview.md](../../05-ui-ux/settings/master/overview.md)
- [../../00-project-overview/glossary.md](../../00-project-overview/glossary.md)
- [../../AI_INDEX.md](../../AI_INDEX.md)
