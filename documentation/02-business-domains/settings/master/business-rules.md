# Business Rules — Settings / Master

## Purpose

Numbered business rules for Staff & System Access and User Role screens. Every rule cites its UI spec source. Rules marked **TODO** require business confirmation before implementation.

## Rule Index

| ID | Title | Type | Status |
| :--- | :--- | :--- | :---: |
| [BR-001](#br-001--customer-required-for-staff-registration) | Customer required for staff registration | Eligibility | Confirmed |
| [BR-002](#br-002--designation-required) | Designation required | Validation | Confirmed |
| [BR-003](#br-003--employee-type-director-or-employee) | Employee type Director or Employee | Validation | Confirmed |
| [BR-004](#br-004--employee-in-service-default-at-creation) | Employee in service default at creation | Workflow | Confirmed |
| [BR-005](#br-005--login-name-required) | Login name required | Validation | Confirmed |
| [BR-006](#br-006--password-and-confirm-password-must-match) | Password and confirm password must match | Validation | Confirmed |
| [BR-007](#br-007--user-status-required-with-defined-values) | User status required with defined values | Validation | Confirmed |
| [BR-008](#br-008--user-type-defaults-to-society) | User type defaults to Society | Workflow | Confirmed |
| [BR-009](#br-009--intra-branch-limits-conditional-on-checkbox) | Intra-branch limits conditional on checkbox | Eligibility | Confirmed |
| [BR-010](#br-010--login-name-uniqueness) | Login name uniqueness | Validation | Confirmed |
| [BR-011](#br-011--password-complexity) | Password complexity | Validation | Confirmed |
| [BR-012](#br-012--super-user-permission-bypass) | Super User permission bypass | Cross-cutting | Confirmed |
| [BR-013](#br-013--organization-and-branch-required-for-rights-row) | Organization and branch required for rights row | Validation | Confirmed |
| [BR-014](#br-014--role-name-required) | Role name required | Validation | Confirmed |
| [BR-015](#br-015--permission-grid-loaded-from-menu-registry) | Permission grid loaded from menu registry | Workflow | Confirmed |
| [BR-016](#br-016--exactly-one-permission-level-per-form-row) | Exactly one permission level per form row | Validation | Confirmed |
| [BR-017](#br-017--permission-levels-are-all-rights-view-only-no-rights) | Permission levels are All Rights / View Only / No Rights | Cross-cutting | Confirmed |
| [BR-018](#br-018--minimum-branch-rights-on-save) | Minimum branch rights on save | Eligibility | Confirmed |
| [BR-019](#br-019--staff-access-wizard-atomic-save-on-create) | Staff access wizard atomic save on create | Workflow | Confirmed |
| [BR-020](#br-020--staff-access-assigns-existing-role) | Staff access assigns existing Role | Eligibility | Confirmed |
| [BR-021](#br-021--blank-password-on-edit-keeps-existing) | Blank password on edit keeps existing | Workflow | Confirmed |
| [BR-022](#br-022--soft-warning-on-self-lockout-risk-permissions) | Soft warning on self-lockout risk permissions | Workflow | Confirmed |
| [BR-023](#br-023--unregistered-form-defaults-to-no-rights) | Unregistered form defaults to No Rights | Cross-cutting | Confirmed |

---

## Rules

### BR-001 — Customer required for staff registration

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [staff-system-access-screen.md](../../05-ui-ux/settings/master/staff-system-access-screen.md) — Tab 1, field #1 |

**Rule:** A staff member (Employee or Director) must be linked to an existing **Customer** record selected via the Customer Autocomplete. The system must not create a new Customer identity from this screen.

**Notes:** Cross-domain dependency on Customer module. See [glossary.md](../../00-project-overview/glossary.md) — Customer vs Employee distinction.

---

### BR-002 — Designation required

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [staff-system-access-screen.md](../../05-ui-ux/settings/master/staff-system-access-screen.md) — Tab 1, field #2 |

**Rule:** Designation (हुद्दा) is required. Allowed values: `मुख्य कार्यकारी अधिकारी`, `अध्यक्ष`, `उपाध्यक्ष`, `संचालक`. The placeholder `निवडा` is not a valid saved value.

---

### BR-003 — Employee type Director or Employee

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [staff-system-access-screen.md](../../05-ui-ux/settings/master/staff-system-access-screen.md) — Tab 1, fields #3–#4 |

**Rule:** Exactly one employee type must be selected: **Director** (संचालक) or **Employee** (कर्मचारी). Default at creation is **Director**.

---

### BR-004 — Employee in service default at creation

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [staff-system-access-screen.md](../../05-ui-ux/settings/master/staff-system-access-screen.md) — Tab 1 note (removed field) |

**Rule:** At staff creation, "currently in service" defaults to **Yes**. This field is not shown on create; it is editable only in edit mode.

---

### BR-005 — Login name required

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [staff-system-access-screen.md](../../05-ui-ux/settings/master/staff-system-access-screen.md) — Tab 2, field #5 |

**Rule:** Login Name (लॉगीन नाव) is required for every User account.

---

### BR-006 — Password and confirm password must match

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [staff-system-access-screen.md](../../05-ui-ux/settings/master/staff-system-access-screen.md) — Tab 2, fields #6–#7 |

**Rule:** Password and Confirm Password must be identical before the User account is saved.

---

### BR-007 — User status required with defined values

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [staff-system-access-screen.md](../../05-ui-ux/settings/master/staff-system-access-screen.md) — Tab 2, field #8 |

**Rule:** User Status (स्थिती) is required. Default is `सक्रिय` (Active). Allowed values: `सक्रिय`, `निष्क्रिय`, `स्थगित`, `सिस्टीम स्थगित`.

---

### BR-008 — User type defaults to Society

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [staff-system-access-screen.md](../../05-ui-ux/settings/master/staff-system-access-screen.md) — Tab 2 auto-fill note |

**Rule:** User Type is persisted as `सोसायटी` (Society) for all users created through this screen. The field is not displayed in the UI.

---

### BR-009 — Intra-branch limits conditional on checkbox

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [staff-system-access-screen.md](../../05-ui-ux/settings/master/staff-system-access-screen.md) — Tab 2 Advanced, fields #12–#14 |

**Rule:** Intra-branch Receipt Limit (#13) and Intra-branch Payable Limit (#14) are applicable only when Intra-branch Transaction (#12) is checked. When #12 is unchecked, #13 and #14 must not be persisted.

---

### BR-010 — Login name uniqueness

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [staff-system-access-screen.md](../../05-ui-ux/settings/master/staff-system-access-screen.md) — Tab 2, field #5; Standing Decision 2026-07-23 |

**Rule:** Login Name must be unique within the tenant. Reject save when another User in the same tenant already has the same Login Name (case-sensitive exact match unless later decided otherwise). On edit, uniqueness excludes the current User record.

**Notes:** Tenant scope follows DEC-001 (database-per-tenant). Cross-tenant uniqueness is not required.

---

### BR-011 — Password complexity

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [staff-system-access-screen.md](../../05-ui-ux/settings/master/staff-system-access-screen.md) — Tab 2, fields #6–#7; Standing Decision 2026-07-23 |

**Rule:** On create or password change, Password must be at least **8** characters and contain at least **one letter** and **one digit**. Special characters are optional. Password history / reuse checks are **not** required in Year 1. Password and Confirm Password must still match ([BR-006](#br-006--password-and-confirm-password-must-match)).

---

### BR-012 — Super User permission bypass

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | Confirmed |
| Source | [staff-system-access-screen.md](../../05-ui-ux/settings/master/staff-system-access-screen.md) — Tab 2, field #9; Standing Decision 2026-07-23 |

**Rule:** When Super User (सुपर युजर) is checked, the User receives **All Rights** on every application form, regardless of the assigned Role permission matrix. Branch access rights (Tab 3 / [BR-013](#br-013--organization-and-branch-required-for-rights-row), [BR-018](#br-018--minimum-branch-rights-on-save)) still apply — Super User does not grant access to branches not assigned to the User.

**Notes:** Use for break-glass administrators. Prefer Role templates for normal staff (Clerk/Cashier).

---

### BR-013 — Organization and branch required for rights row

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [staff-system-access-screen.md](../../05-ui-ux/settings/master/staff-system-access-screen.md) — Tab 3, fields #15–#16 |

**Rule:** Each branch rights row added to the grid must include a selected Organization (#15) and Branch (#16). Both fields are required before the row is added.

---

### BR-014 — Role name required

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [user-role-screen.md](../../05-ui-ux/settings/master/user-role-screen.md) — field #1 |

**Rule:** User Role name (युजर रोल) is required when defining or saving a Role.

---

### BR-015 — Permission grid loaded from menu registry

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [user-role-screen.md](../../05-ui-ux/settings/master/user-role-screen.md) — Permission Grid |

**Rule:** Permission grid rows (Menu + Form Name) are loaded dynamically from the application menu registry for all modules. The Accounting sample rows in the spec are layout reference only; the live grid must include every registered form.

---

### BR-016 — Exactly one permission level per form row

| Property | Value |
| :--- | :--- |
| Type | Validation |
| Status | Confirmed |
| Source | [user-role-screen.md](../../05-ui-ux/settings/master/user-role-screen.md) — Permission Grid columns #4–#6 |

**Rule:** For each form row in the permission grid, at most one of All Rights, View Only, or No Rights may be selected. Selecting one level must deselect the other two on that row.

---

### BR-017 — Permission levels are All Rights / View Only / No Rights

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | Confirmed |
| Source | [user-role-screen.md](../../05-ui-ux/settings/master/user-role-screen.md); [glossary.md](../../00-project-overview/glossary.md) — Role |

**Rule:** The platform defines exactly three permission levels per form:

| Level | Marathi | Effect |
| :--- | :--- | :--- |
| All Rights | सर्व अधिकार | Full create/read/update/delete on the form |
| View Only | फक्त बघण्यासाठी | Read-only; Save/Add/Remove/Post actions hidden |
| No Rights | अधिकार नाही | Route guard blocks navigation to the form |

Other domains must reference this rule — not redefine permission semantics.

---

### BR-018 — Minimum branch rights on save

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [staff-system-access-screen.md](../../05-ui-ux/settings/master/staff-system-access-screen.md) — Tab 3; Standing Decision 2026-07-23 |

**Rule:** At least one branch rights row (Organization + Branch) is required before Staff & System Access Save succeeds on create and on edit. Removing the last row must be blocked (or Save rejected) until another row exists.

**Single-branch tenant:** When the tenant has exactly one Branch (typical Year-1 Head Office / single-branch society), the system must auto-provide that Organization + Branch as the rights row on Tab 3 (pre-filled / auto-added). The actor may still review the grid; they should not be forced to look up the only branch manually.

**Notes:** Applies to Super Users as well ([BR-012](#br-012--super-user-permission-bypass)) — form bypass does not replace branch scope.

---

### BR-019 — Staff access wizard atomic save on create

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [staff-system-access-screen.md](../../05-ui-ux/settings/master/staff-system-access-screen.md) — wizard tabs / footer actions; Standing Decision 2026-07-23 |

**Rule:** On **create**, Staff & System Access persists Employee, User, branch rights, and role assignment only when the actor clicks **Save (जतन करा)** after all tabs are valid. **Next (पुढे)** and **Back (मागे)** change wizard step only and must not write partial records to the database. Client/wizard state may retain entered values until Reset or successful Save.

**Notes:** Edit of an existing record may Save after load without re-walking every tab, subject to the same field validations for changed data.

---

### BR-020 — Staff access assigns existing Role

| Property | Value |
| :--- | :--- |
| Type | Eligibility |
| Status | Confirmed |
| Source | [staff-system-access-screen.md](../../05-ui-ux/settings/master/staff-system-access-screen.md) — Tab 4; Standing Decision 2026-07-23 |

**Rule:** On Staff & System Access Tab 4, the actor must **select an existing Role** (reusable permission profile) to assign to the User. The actor may optionally create a new Role (same fields as the standalone User Role screen) and then assign it. The wizard must not persist per-user permission rows outside a Role entity.

**Notes:** Year-1 tenant seed includes Clerk, Cashier, and Manager Role templates — see [default-role-templates.md](default-role-templates.md) and [tenant-setup.md](../../../00-project-overview/tenant-setup.md).

---

### BR-021 — Blank password on edit keeps existing

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [staff-system-access-screen.md](../../05-ui-ux/settings/master/staff-system-access-screen.md) — Tab 2, fields #6–#7; Standing Decision 2026-07-23 |

**Rule:** On **edit** of an existing User, if Password and Confirm Password are both left blank, the system keeps the existing password hash unchanged. If either password field is non-blank, both must be filled, must match ([BR-006](#br-006--password-and-confirm-password-must-match)), and must meet complexity ([BR-011](#br-011--password-complexity)). On **create**, Password and Confirm Password remain required ([BR-005](#br-005--login-name-required) context — credentials required at creation).

**Notes:** Does not weaken create-time password requirements.

---

### BR-022 — Soft warning on self-lockout risk permissions

| Property | Value |
| :--- | :--- |
| Type | Workflow |
| Status | Confirmed |
| Source | [user-role-screen.md](../../05-ui-ux/settings/master/user-role-screen.md) — Permission Grid; Standing Decision 2026-07-23 |

**Rule:** When saving a Role, if the actor sets **No Rights** on `settings.staff-system-access` or `settings.user-role`, and that Role is assigned to the actor's own User, the system shows a **soft warning** about possible self-lockout. Save is still allowed. The system does not hard-block Save for Year 1.

**Notes:** Expand the warned form list when Dashboard (or other shell forms) are registered in the menu registry. Non-self Roles may still receive No Rights on these forms without warning (e.g. Clerk/Cashier seed templates).

---

### BR-023 — Unregistered form defaults to No Rights

| Property | Value |
| :--- | :--- |
| Type | Cross-cutting |
| Status | Confirmed |
| Source | [WF-003](workflows.md#wf-003--permission-enforcement-at-runtime); Standing Decision 2026-07-23 |

**Rule:** If a User navigates to a `form_code` that is missing from the application menu registry, or has no resolvable `role_permission` for the User's Role (and Super User is not set), the effective permission is **No Rights** — route guard blocks access. The application must not grant All Rights or View Only by default for unknown forms. Year 1 does **not** require failing application startup when a route lacks a registry entry; ops should log a diagnostic and keep seed/registry aligned with [default-role-templates.md](default-role-templates.md).

**Notes:** Super User still receives All Rights on **registered** forms per [BR-012](#br-012--super-user-permission-bypass). Unregistered `form_code` values remain deny-by-default for all users (including Super User) until the form is added to the menu registry.

---

## Related Documents

- [overview.md](overview.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [../../05-ui-ux/settings/master/staff-system-access-screen.md](../../05-ui-ux/settings/master/staff-system-access-screen.md)
- [../../05-ui-ux/settings/master/user-role-screen.md](../../05-ui-ux/settings/master/user-role-screen.md)
- [../../00-project-overview/glossary.md](../../00-project-overview/glossary.md)
