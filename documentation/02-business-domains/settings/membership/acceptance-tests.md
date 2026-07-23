# Acceptance Tests — Settings / Membership

## Purpose

Given/When/Then tests for Membership Configuration business rules.

---

### AT-001 — Member class default Member

**Verifies:** [BR-001](business-rules.md#br-001--member-class-filter-mutually-exclusive)

**Given** Membership Configuration opens
**When** the shared filter loads
**Then** Member is selected by default
**And** Nominal Member is not selected

---

### AT-002 — Share rule required fields block Save

**Verifies:** [BR-002](business-rules.md#br-002--share-rule-required-fields), [UC-001](use-cases.md#uc-001--save-or-remove-share-rules) E1

**Given** Tab Share Rules with Face Value blank
**When** the actor clicks Save
**Then** the system blocks Save with a validation error on Face Value

---

### AT-003 — Share Series unique within Member class

**Verifies:** [BR-003](business-rules.md#br-003--share-series-unique-within-member-class)

**Given** Member class already has series `A`
**When** the actor saves another Member-class rule with series `A`
**Then** Save is rejected
**And** saving series `A` under Nominal Member is allowed

---

### AT-004 — Save adds grid row

**Verifies:** [BR-004](business-rules.md#br-004--share-rule-save-persists-grid-row)

**Given** valid share-rule fields for Member class
**When** the actor clicks Save
**Then** a new row appears in the rules grid with the entered Series and Face Value

---

### AT-005 — Remove deletes selected rows

**Verifies:** [BR-005](business-rules.md#br-005--share-rule-remove-deletes-selected-rows)

**Given** a selected share-rule grid row
**When** the actor clicks Remove
**Then** the row is removed from the grid and persistence

---

### AT-006 — Limit Transfer field not shown

**Verifies:** [BR-006](business-rules.md#br-006--share-amount-after-limit-transfer-removed)

**Given** Tab Share Rules is open
**When** the actor views the form
**Then** Share Amount After Limit Transfer is not present

---

### AT-007 — Dividend Year required for Calculate

**Verifies:** [BR-007](business-rules.md#br-007--dividend-year-required)

**Given** Tab Dividend with Year = `निवडा`
**When** the actor clicks Calculate Dividend
**Then** Calculate is blocked with a validation error on Year

---

### AT-008 — Debit Account Head required

**Verifies:** [BR-008](business-rules.md#br-008--dividend-debit-account-head-required)

**Given** Tab Dividend with Debit Account Head cleared
**When** the actor clicks Calculate Dividend
**Then** Calculate is blocked with a validation error on Account Head

---

### AT-009 — Branch filter optional

**Verifies:** [BR-009](business-rules.md#br-009--dividend-branch-filter-optional)

**Given** Year and Debit Head are set and Branch is empty
**When** the actor clicks Calculate Dividend
**Then** a preview runs without requiring Branch

---

### AT-010 — Percentage optional

**Verifies:** [BR-010](business-rules.md#br-010--dividend-percentage-optional)

**Given** Year and Debit Head are set and Percentage is blank
**When** the actor clicks Calculate Dividend
**Then** Calculate proceeds without a Percentage validation error

---

### AT-011 — Calculate does not post dividends

**Verifies:** [BR-011](business-rules.md#br-011--dividend-calculate-is-preview-only), [UC-002](use-cases.md#uc-002--preview-dividend-calculation)

**Given** a successful Calculate Dividend preview
**When** the actor inspects accounting vouchers / dividend obligations
**Then** no new voucher or payment obligation was created by Calculate

---

### AT-012 — Dividend settings labels not editable

**Verifies:** [BR-012](business-rules.md#br-012--dividend-settings-labels-read-only)

**Given** Tab Dividend Calculation is open
**When** the actor views the settings label section
**Then** the labels are display-only (not editable inputs)

---

### AT-013 — View Only cannot Save

**Verifies:** [BR-013](business-rules.md#br-013--membership-configuration-uses-master-permission-levels)

**Given** the actor has View Only on Membership Configuration
**When** the actor opens the screen
**Then** Save, Remove, and Calculate are hidden
**And** no share rule is created

---

### AT-014 — Debit Account Head source — pending confirmation

**Verifies:** [BR-014](business-rules.md#br-014--dividend-debit-account-head-value-source)

**Given** `TODO:` business confirms fixed vs GL-dynamic Debit Head options
**When** the Debit Account Head dropdown loads
**Then** options follow the confirmed source
**And** this test remains blocked until BR-014 is Confirmed

---

### AT-015 — Share rule Branch semantics — pending confirmation

**Verifies:** [BR-015](business-rules.md#br-015--share-rule-grid-branch-semantics)

**Given** `TODO:` business confirms how Branch is assigned on share-rule rows
**When** a share rule is saved
**Then** the Branch column follows the confirmed rule
**And** this test remains blocked until BR-015 is Confirmed

---

## Related Documents

- [overview.md](overview.md)
- [business-rules.md](business-rules.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
