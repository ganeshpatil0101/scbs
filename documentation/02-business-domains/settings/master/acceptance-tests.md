# Acceptance Tests — Settings / Master

## Purpose

Given/When/Then tests verifying business rules and use cases for Master settings. Each test references `BR-NNN` and/or `UC-NNN`.

---

### AT-001 — Customer required on Tab 1

**Verifies:** [BR-001](business-rules.md#br-001--customer-required-for-staff-registration), [UC-001](use-cases.md#uc-001--register-staff-and-grant-system-access) E4

**Given** the Staff & System Access wizard is open on Tab 1
**When** the actor clicks Next without selecting a Customer
**Then** the system displays a validation error on the Customer field
**And** the wizard does not advance to Tab 2

---

### AT-002 — Designation must be selected

**Verifies:** [BR-002](business-rules.md#br-002--designation-required)

**Given** Tab 1 has a Customer selected
**When** Designation remains `निवडा` and the actor clicks Next
**Then** the system blocks advancement with a validation error on Designation

---

### AT-003 — Director selected by default

**Verifies:** [BR-003](business-rules.md#br-003--employee-type-director-or-employee)

**Given** a new Staff & System Access wizard on Tab 1
**When** the screen loads
**Then** the Director (संचालक) radio is selected by default
**And** the Employee (कर्मचारी) radio is not selected

---

### AT-004 — Password mismatch blocks save

**Verifies:** [BR-006](business-rules.md#br-006--password-and-confirm-password-must-match), [UC-001](use-cases.md#uc-001--register-staff-and-grant-system-access) E2

**Given** the actor completed Tabs 1–3 with valid data
**And** Tab 2 Password is `abc123` and Confirm Password is `abc124`
**When** the actor clicks Save on Tab 4
**Then** the system rejects save with a password mismatch error
**And** no User record is created

---

### AT-005 — User status default Active

**Verifies:** [BR-007](business-rules.md#br-007--user-status-required-with-defined-values)

**Given** a new Staff & System Access wizard on Tab 2
**When** the screen loads
**Then** Status dropdown default is `सक्रिय` (Active)

---

### AT-006 — Intra-branch limits hidden when checkbox unchecked

**Verifies:** [BR-009](business-rules.md#br-009--intra-branch-limits-conditional-on-checkbox)

**Given** Tab 2 Advanced Settings is expanded
**And** Intra-branch Transaction checkbox is unchecked
**When** the actor views the form
**Then** Intra-branch Receipt Limit and Intra-branch Payable Limit fields are not visible
**And** no intra-branch limit values are persisted on save

---

### AT-007 — Intra-branch limits visible when checkbox checked

**Verifies:** [BR-009](business-rules.md#br-009--intra-branch-limits-conditional-on-checkbox)

**Given** Tab 2 Advanced Settings is expanded
**When** the actor checks Intra-branch Transaction
**Then** Intra-branch Receipt Limit and Intra-branch Payable Limit fields become visible and editable

---

### AT-008 — Branch rights row requires Organization and Branch

**Verifies:** [BR-013](business-rules.md#br-013--organization-and-branch-required-for-rights-row)

**Given** Tab 3 Branch Rights is open
**When** the actor clicks Add without selecting Organization or Branch
**Then** the system displays validation errors
**And** no row is added to the rights grid

---

### AT-009 — Role name required

**Verifies:** [BR-014](business-rules.md#br-014--role-name-required), [UC-002](use-cases.md#uc-002--define-user-role-permission-template) E1

**Given** the User Role screen is open with a loaded permission grid
**When** the actor clicks Save with an empty Role name
**Then** the system blocks save with a validation error on Role name

---

### AT-010 — Permission grid loads from menu registry

**Verifies:** [BR-015](business-rules.md#br-015--permission-grid-loaded-from-menu-registry)

**Given** the application menu registry contains forms from Customer, Accounting, and Settings modules
**When** the User Role screen loads
**Then** the permission grid includes rows for all registered forms across modules
**And** rows are not limited to the Accounting sample list in the spec

---

### AT-011 — Mutually exclusive permission per row

**Verifies:** [BR-016](business-rules.md#br-016--exactly-one-permission-level-per-form-row)

**Given** a permission grid row with All Rights selected
**When** the actor selects View Only on the same row
**Then** All Rights is deselected on that row
**And** exactly one permission level remains selected

---

### AT-012 — View Only hides Save on Staff screen

**Verifies:** [BR-017](business-rules.md#br-017--permission-levels-are-all-rights--view-only--no-rights), [UC-001](use-cases.md#uc-001--register-staff-and-grant-system-access) E5

**Given** a User with View Only permission on Staff & System Access
**When** the User opens the screen
**Then** all fields are read-only or disabled
**And** the Save button is not visible

---

### AT-013 — No Rights blocks route

**Verifies:** [BR-017](business-rules.md#br-017--permission-levels-are-all-rights--view-only--no-rights)

**Given** a User with No Rights on Staff & System Access
**When** the User attempts to navigate to Staff & System Access
**Then** the route guard prevents access
**And** the form shell is not rendered

---

### AT-014 — Successful staff registration end-to-end

**Verifies:** [UC-001](use-cases.md#uc-001--register-staff-and-grant-system-access), [WF-001](workflows.md#wf-001--staff--system-access-registration-wizard)

**Given** a valid Customer record exists
**And** Branch and Organization master data exist
**When** an Administrator completes all four wizard tabs with valid data and matching passwords
**And** clicks Save
**Then** an Employee record is created linked to the Customer
**And** a User record is created with the entered Login Name and Status
**And** branch rights rows are persisted
**And** role permissions are assigned

---

### AT-015 — User type persisted as Society

**Verifies:** [BR-008](business-rules.md#br-008--user-type-defaults-to-society)

**Given** a successful Staff & System Access save
**When** the User record is queried
**Then** User Type equals `सोसायटी` (Society)
**And** User Type was not entered by the actor in the UI

---

### AT-016 — Login name uniqueness within tenant

**Verifies:** [BR-010](business-rules.md#br-010--login-name-uniqueness)

**Given** User A already exists with Login Name `clerk01` in the tenant
**When** an Administrator attempts to save a new User with Login Name `clerk01`
**Then** Save is rejected with a uniqueness validation error
**And** no second User with Login Name `clerk01` is created

---

### AT-017 — Password complexity minimum rules

**Verifies:** [BR-011](business-rules.md#br-011--password-complexity)

**Given** Tab 2 Login & Password is open for create (or password change)
**When** the actor enters Password `abc` (too short) or `abcdefgh` (no digit) or `12345678` (no letter)
**Then** Save is rejected with a password complexity validation error
**And** when the actor enters a valid password such as `clerk01a` (length ≥ 8, letter + digit) with matching Confirm Password
**Then** complexity validation passes (subject to other field rules)
---

### AT-018 — Super User bypasses role matrix

**Verifies:** [BR-012](business-rules.md#br-012--super-user-permission-bypass)

**Given** a User with Super User checked
**And** the User's Role assigns View Only (or No Rights) on a target form
**And** the User has at least one assigned branch right for the active branch context
**When** the User navigates to that form
**Then** the form opens with All Rights (full actions enabled)
**And** when the User has no branch right for a branch, Super User does not grant access to that branch's data

---

### AT-019 — Minimum one branch right; single-branch auto-assign

**Verifies:** [BR-018](business-rules.md#br-018--minimum-branch-rights-on-save)

**Given** Tab 3 Branch Rights has zero rows in the grid
**When** the actor attempts Save
**Then** Save is rejected with a validation error requiring at least one branch rights row

**Given** the tenant has exactly one Branch (e.g. Head Office only)
**When** the actor opens Tab 3 during Staff & System Access create
**Then** that Organization + Branch is already present as a rights row (auto-provided)
**And** Save is not blocked solely for missing branch rights

---

### AT-020 — Create wizard does not persist until final Save

**Verifies:** [BR-019](business-rules.md#br-019--staff-access-wizard-atomic-save-on-create), [WF-001](workflows.md#wf-001--staff--system-access-registration-wizard)

**Given** an Administrator is creating a new Staff & System Access record
**And** Tabs 1–3 have valid data entered
**When** the actor clicks Next (or Back) without clicking Save
**Then** no Employee or User record is persisted
**And** when the actor completes Tab 4 and clicks Save with all tabs valid
**Then** Employee, User, branch rights, and role assignment are persisted together

---

### AT-021 — Staff access assigns an existing Role

**Verifies:** [BR-020](business-rules.md#br-020--staff-access-assigns-existing-role)

**Given** seeded Roles Clerk, Cashier, and Manager exist for the tenant
**When** an Administrator completes Tab 4 by selecting Role `clerk` and Saves
**Then** the User is linked to the Clerk Role
**And** no per-user permission rows exist outside `role_permission`
**And** effective form permissions match the Clerk column in [default-role-templates.md](default-role-templates.md)

---

### AT-022 — Blank password on edit keeps existing

**Verifies:** [BR-021](business-rules.md#br-021--blank-password-on-edit-keeps-existing), [UC-003](use-cases.md#uc-003--edit-existing-staff-system-access) A1

**Given** an existing User with a stored password hash
**When** an Administrator edits Staff & System Access and leaves Password and Confirm Password blank
**And** clicks Save with other fields valid
**Then** Save succeeds
**And** the password hash is unchanged

---

### AT-023 — Soft warning on self-lockout risk; Save allowed

**Verifies:** [BR-022](business-rules.md#br-022--soft-warning-on-self-lockout-risk-permissions), [UC-002](use-cases.md#uc-002--define-user-role-permission-template) E3

**Given** the actor's User is assigned Role R
**And** the actor is editing Role R on the User Role screen
**When** the actor sets No Rights on Staff & System Access (or User Role) and clicks Save
**Then** the system displays a soft warning about self-lockout risk
**And** Save still succeeds if the actor proceeds

---

### AT-024 — Unregistered form defaults to No Rights

**Verifies:** [BR-023](business-rules.md#br-023--unregistered-form-defaults-to-no-rights), [WF-003](workflows.md#wf-003--permission-enforcement-at-runtime)

**Given** a User who is not Super User
**And** `form_code` `unknown.form` is not in the menu registry (or has no role_permission)
**When** the User attempts to navigate to that form
**Then** access is denied (No Rights behaviour)
**And** the application remains running (startup is not blocked solely by this gap)
---

## Related Documents

- [overview.md](overview.md)
- [business-rules.md](business-rules.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
- [../../08-testing/](../../08-testing/) — future integration test plan (Phase 4)
