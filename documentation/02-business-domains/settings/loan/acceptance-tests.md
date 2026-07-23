# Acceptance Tests — Settings / Loan

## Purpose

Given/When/Then tests for Loan Interest Rate Change business rules.

---

### AT-001 — Scheme required

**Verifies:** [BR-001](business-rules.md#br-001--loan-scheme-required)

**Given** Interest Rate Change is open with no Scheme selected
**When** the actor clicks Save
**Then** Save is blocked with a validation error on Scheme

---

### AT-002 — Scheme dropdown lists Loan schemes only

**Verifies:** [BR-002](business-rules.md#br-002--scheme-list-from-loan-schemes-only)

**Given** the tenant has Savings and Loan schemes
**When** the Scheme dropdown loads
**Then** only Loan schemes appear

---

### AT-003 — Change Date required

**Verifies:** [BR-003](business-rules.md#br-003--change-date-required)

**Given** Scheme is selected and Change Date is blank
**When** the actor clicks Save
**Then** Save is blocked with a validation error on Change Date

---

### AT-004 — New Interest Rate required

**Verifies:** [BR-004](business-rules.md#br-004--new-interest-rate-required), [UC-001](use-cases.md#uc-001--change-loan-scheme-interest-rate) E1

**Given** Scheme and Change Date are set and New Interest Rate is blank
**When** the actor clicks Save
**Then** Save is blocked with a validation error on New Interest Rate

---

### AT-005 — New Penalty Rate optional

**Verifies:** [BR-005](business-rules.md#br-005--new-penalty-rate-optional)

**Given** required fields are set and New Penalty Rate is blank
**When** the actor clicks Save
**Then** Save succeeds
**And** the scheme interest rate is updated

---

### AT-006 — Apply All Accounts is default

**Verifies:** [BR-006](business-rules.md#br-006--apply-scope-mutually-exclusive)

**Given** a new Interest Rate Change form
**When** the screen loads
**Then** Apply New Rate to All Accounts is selected

---

### AT-007 — Scheme template always updated

**Verifies:** [BR-007](business-rules.md#br-007--scheme-template-always-updated-on-save)

**Given** Apply New Rate to New Accounts Only is selected and New Interest Rate is `12`
**When** the actor Saves successfully
**Then** the Loan scheme template interest rate becomes `12`

---

### AT-008 — Apply to all accounts updates existing accounts

**Verifies:** [BR-008](business-rules.md#br-008--apply-new-rate-to-all-accounts)

**Given** Apply to All Accounts is selected and existing accounts exist under the scheme
**When** the actor Saves a new rate
**Then** existing accounts under the scheme use the new interest rate from Change Date forward

---

### AT-009 — Apply to new accounts only keeps existing rates

**Verifies:** [BR-009](business-rules.md#br-009--apply-new-rate-to-new-accounts-only)

**Given** Apply to New Accounts Only is selected and existing accounts exist under the scheme
**When** the actor Saves a new rate
**Then** existing accounts retain prior rates
**And** a new account opened after Change Date uses the new template rate

---

### AT-010 — History row appended on Save

**Verifies:** [BR-010](business-rules.md#br-010--rate-change-appends-history-row)

**Given** a successful Save for a scheme
**When** the actor expands Past Rate Changes
**Then** a new history row includes the scheme and Change Date
**And** previous interest rate is recorded

---

### AT-011 — History collapsed by default

**Verifies:** [BR-011](business-rules.md#br-011--history-section-collapsed-by-default)

**Given** Interest Rate Change opens
**When** the screen loads
**Then** Past Rate Changes is collapsed

---

### AT-012 — View Only cannot Save

**Verifies:** [BR-012](business-rules.md#br-012--loan-interest-rate-change-uses-master-permission-levels)

**Given** the actor has View Only on Interest Rate Change
**When** the actor opens the screen
**Then** Save is hidden
**And** the scheme template rate is unchanged

---

### AT-013 — Duration slab scope — pending confirmation

**Verifies:** [BR-013](business-rules.md#br-013--rate-change-duration-slab-scope)

**Given** `TODO:` business confirms all-slabs vs selected-duration behaviour
**When** the actor Saves a rate change
**Then** duration/slab application follows the confirmed rule
**And** this test remains blocked until BR-013 is Confirmed

---

### AT-014 — Export contents — pending confirmation

**Verifies:** [BR-014](business-rules.md#br-014--export-contents)

**Given** `TODO:` business confirms Export format and contents
**When** the actor clicks Export
**Then** the export matches the confirmed definition
**And** this test remains blocked until BR-014 is Confirmed

---

## Related Documents

- [overview.md](overview.md)
- [business-rules.md](business-rules.md)
- [use-cases.md](use-cases.md)
- [workflows.md](workflows.md)
