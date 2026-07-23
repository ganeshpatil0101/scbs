# Use Cases — Settings / Master

## Purpose

Actor goals for Master settings screens. Each use case references business rules by ID.

---

### UC-001 — Register staff and grant system access

**Actors:** Administrator (User with All Rights on Staff & System Access form)

**Preconditions:**
1. A **Customer** record exists for the person being registered as staff ([BR-001](business-rules.md#br-001--customer-required-for-staff-registration)).
2. Actor has All Rights on the Staff & System Access form ([BR-017](business-rules.md#br-017--permission-levels-are-all-rights--view-only--no-rights)).
3. Branch and Organization master data exist for branch rights assignment.

**Main Flow:**
1. Actor opens **Staff & System Access** (कर्मचारी व सिस्टम प्रवेश).
2. **Tab 1 — Employee Details:** Actor selects Customer via Autocomplete, selects Designation, selects Director or Employee type (default Director).
3. Actor clicks **Next** (पुढे).
4. **Tab 2 — Login & Password:** Actor enters Login Name, Password, Confirm Password, User Status (default Active). Optionally sets Super User and Advanced Settings limits.
5. Actor clicks **Next**.
6. **Tab 3 — Branch Rights:** Actor selects Organization and Branch, clicks **Add** (+ टाका) to add one or more rows to the rights grid. At least one row is required ([BR-018](business-rules.md#br-018--minimum-branch-rights-on-save)). If the tenant has only one Branch, that branch is auto-provided in the grid.
7. Actor clicks **Next**.
8. **Tab 4 — User Role:** Actor selects an existing Role (or creates a new Role via the permission matrix, then assigns it) ([BR-020](business-rules.md#br-020--staff-access-assigns-existing-role)).
9. Actor clicks **Save** (जतन करा). On create, this is the only persist point ([BR-019](business-rules.md#br-019--staff-access-wizard-atomic-save-on-create)).
10. System persists Employee, User, branch rights, and role assignment.

**Alternative Flow:**
- **A1 — Back navigation:** On Tab 2–4, actor clicks **Back** (मागे). Previously entered values on prior tabs remain in the wizard state until Reset or successful Save.
- **A2 — Advanced limits:** Actor expands **Advanced Settings** on Tab 2 and optionally sets cash voucher limits and intra-branch transaction limits ([BR-009](business-rules.md#br-009--intra-branch-limits-conditional-on-checkbox)).
- **A3 — Remove branch right:** Actor selects a row in the branch rights grid and clicks **Remove** (काढा).

**Exception Flow:**
- **E1 — Required field missing:** System blocks Next or Save and displays validation message for the missing required field.
- **E2 — Password mismatch:** System blocks Save when Password ≠ Confirm Password ([BR-006](business-rules.md#br-006--password-and-confirm-password-must-match)).
- **E3 — Duplicate login name:** System rejects Save when Login Name already exists for another User in the tenant ([BR-010](business-rules.md#br-010--login-name-uniqueness)).
- **E4 — Password complexity:** System rejects Save when Password fails length or letter+digit rules ([BR-011](business-rules.md#br-011--password-complexity)).
- **E5 — Customer not found:** Autocomplete returns no match; actor must create Customer in Customer module first ([BR-001](business-rules.md#br-001--customer-required-for-staff-registration)).
- **E6 — View Only permission:** Actor with View Only on this form can view all tabs but cannot Save ([BR-017](business-rules.md#br-017--permission-levels-are-all-rights--view-only--no-rights)).

**Post Conditions:**
1. Employee record exists linked to the selected Customer.
2. User account exists with configured login credentials and status.
3. Branch rights rows are persisted for the User.
4. Role permissions are assigned per Tab 4 / selected Role.

**Referenced Business Rules:** BR-001, BR-002, BR-003, BR-004, BR-005, BR-006, BR-007, BR-008, BR-009, BR-010, BR-011, BR-012, BR-013, BR-016, BR-017, BR-018, BR-019, BR-020

---

### UC-002 — Define user role permission template

**Actors:** Administrator (User with All Rights on User Role form)

**Preconditions:**
1. Application menu registry is populated with all module forms ([BR-015](business-rules.md#br-015--permission-grid-loaded-from-menu-registry)).
2. Actor has All Rights on the User Role form.

**Main Flow:**
1. Actor opens **User Role** (युजर रोल) — standalone screen or Tab 4 of Staff & System Access wizard.
2. Actor enters Role name ([BR-014](business-rules.md#br-014--role-name-required)).
3. System loads permission grid rows from the menu registry (Menu + Form Name for all modules).
4. For each form row (or via bulk header checkbox), actor selects exactly one permission level: All Rights, View Only, or No Rights ([BR-016](business-rules.md#br-016--exactly-one-permission-level-per-form-row)).
5. Actor clicks **Save**.
6. System persists Role and role_permission rows.

**Alternative Flow:**
- **A1 — Bulk column select:** Actor uses header checkbox on All Rights / View Only / No Rights column to apply that level to all visible rows, then adjusts individual rows.

**Exception Flow:**
- **E1 — Role name empty:** System blocks Save ([BR-014](business-rules.md#br-014--role-name-required)).
- **E2 — Multiple levels on one row:** System prevents or clears conflicting selections ([BR-016](business-rules.md#br-016--exactly-one-permission-level-per-form-row)).
- **E3 — Self-lockout risk:** When actor sets No Rights on Staff & System Access or User Role for a Role assigned to their own User, system shows a soft warning and still allows Save ([BR-022](business-rules.md#br-022--soft-warning-on-self-lockout-risk-permissions)).

**Post Conditions:**
1. Role record exists with the given name.
2. Every registered form has exactly one assigned permission level for this Role.

**Referenced Business Rules:** BR-014, BR-015, BR-016, BR-017, BR-022

---

### UC-003 — Edit existing staff system access

**Actors:** Administrator

**Preconditions:**
1. Employee and linked User record exist.
2. Actor has All Rights on Staff & System Access form.

**Main Flow:**
1. Actor opens existing Staff & System Access record in edit mode.
2. Actor modifies allowed fields across tabs (including "currently in service" which is editable in edit mode per [BR-004](business-rules.md#br-004--employee-in-service-default-at-creation)).
3. Actor clicks **Save**.
4. System updates Employee, User, branch rights, and role assignment.

**Alternative Flow:**
- **A1 — Password unchanged:** Actor leaves Password and Confirm Password blank on edit — system keeps the existing password ([BR-021](business-rules.md#br-021--blank-password-on-edit-keeps-existing)).
- **A2 — Password change:** Actor enters new Password and Confirm Password — must match and meet complexity ([BR-006](business-rules.md#br-006--password-and-confirm-password-must-match), [BR-011](business-rules.md#br-011--password-complexity)).

**Exception Flow:**
- Same validation exceptions as UC-001 (E1–E6).

**Post Conditions:**
1. Updated records reflect changes; audit trail updated (Phase 4 hardening).

**Referenced Business Rules:** BR-001 through BR-021 (as applicable to changed fields)

---

## Related Documents

- [overview.md](overview.md)
- [business-rules.md](business-rules.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [../../05-ui-ux/settings/master/staff-system-access-screen.md](../../05-ui-ux/settings/master/staff-system-access-screen.md)
- [../../05-ui-ux/settings/master/user-role-screen.md](../../05-ui-ux/settings/master/user-role-screen.md)
