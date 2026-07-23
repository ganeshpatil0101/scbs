# Use Cases — Settings / Schemes

## Purpose

Actor goals for the New Scheme wizard. Each use case references business rules by ID.

---

### UC-001 — Create product scheme

**Actors:** Administrator (User with All Rights on New Scheme form)

**Preconditions:**
1. At least one **GL Head** exists in the GL master for the intended product ([BR-004](business-rules.md#br-004--gl-head-required-from-gl-master)).
2. Actor has All Rights on the New Scheme form ([BR-014](business-rules.md#br-014--new-scheme-form-uses-master-permission-levels)).

**Main Flow:**
1. Actor opens **New Scheme** (नवीन योजना).
2. Actor selects Scheme Type ([BR-001](business-rules.md#br-001--scheme-type-required)). System shows the tab set for that type ([BR-003](business-rules.md#br-003--tab-visibility-by-scheme-type)).
3. **Scheme Info:** Actor selects GL Head via Autocomplete ([BR-004](business-rules.md#br-004--gl-head-required-from-gl-master)), enters Scheme Name ([BR-007](business-rules.md#br-007--scheme-name-required)), selects Status ([BR-009](business-rules.md#br-009--scheme-status-required-with-defined-values)), optionally sets Allow Only Members ([BR-010](business-rules.md#br-010--allow-only-members-optional)), and completes type-specific Tab 1 fields (e.g. [BR-015](business-rules.md#br-015--savings-product-subtype-and-interest-rate-required), [BR-017](business-rules.md#br-017--open-ended-and-close-ended-mutually-exclusive), [BR-022](business-rules.md#br-022--fd-required-identity-fields), [BR-027](business-rules.md#br-027--loan-type-required)).
4. Actor clicks **Next** through visible tabs. For Duration & Rates (when shown), actor adds rate rows ([BR-020](business-rules.md#br-020--duration-and-rates-row-required-fields)). For Interest Posting, actor may add day/month rows ([BR-011](business-rules.md#br-011--interest-posting-day-and-month-on-add)). For Account Closing / Loan Specific / Advanced / Charges when shown, actor configures optional or required type-specific data ([BR-012](business-rules.md#br-012--shared-charge-types), [BR-021](business-rules.md#br-021--account-closing-tab-deposit-types-only), [BR-031](business-rules.md#br-031--loan-guarantor-total-is-sum)).
5. Actor clicks **Complete / Save**. System validates all visible tabs and persists the scheme atomically ([BR-013](business-rules.md#br-013--scheme-wizard-atomic-save-on-create)).

**Alternative Flow:**
- **A1 — Change Scheme Type:** Actor changes Scheme Type mid-wizard. System resets to Tab 1 and discards prior type state ([BR-002](business-rules.md#br-002--scheme-type-change-resets-wizard)).
- **A2 — Back navigation:** Actor clicks **Back**; prior tab values remain in wizard memory until Reset or successful Save.
- **A3 — Daily GL constraint:** For Daily, actor selects a GL Head with number ≤ 99 ([BR-005](business-rules.md#br-005--daily-scheme-gl-head-number--99)).
- **A4 — Shared GL:** Actor selects a GL Head already used by another scheme — allowed ([BR-006](business-rules.md#br-006--multiple-schemes-may-share-one-gl-head)).
- **A5 — Loan Credit Card:** When Loan Type is Credit Card, actor must set Monthly Billing Cycle Day ([BR-028](business-rules.md#br-028--credit-card-billing-cycle-day-conditional)).
- **A6 — Advanced (FD/Recurring/Loan):** Actor expands Advanced for receipt series, auto-renewal, salary/rebate, or loan application options as applicable.

**Exception Flow:**
- **E1 — Required field missing:** System blocks Next or Save with field-level validation.
- **E2 — Duplicate scheme name within type:** System rejects Save ([BR-008](business-rules.md#br-008--scheme-name-unique-within-scheme-type)).
- **E3 — Daily GL > 99:** System rejects resolve/Save ([BR-005](business-rules.md#br-005--daily-scheme-gl-head-number--99)).
- **E4 — GL Head not found:** Autocomplete returns no match; actor must create GL Head in Settings/Accounting first ([BR-004](business-rules.md#br-004--gl-head-required-from-gl-master)).
- **E5 — View Only:** Actor can view the wizard but cannot Save ([BR-014](business-rules.md#br-014--new-scheme-form-uses-master-permission-levels)).

**Post Conditions:**
1. A `scheme` record exists with selected type, name, status, GL Head, and type-specific parameters.
2. Related grid rows (duration rates, interest posting, closing slabs, charges, loan config) are persisted for visible tabs only.
3. No partial scheme exists from Next/Back alone ([BR-013](business-rules.md#br-013--scheme-wizard-atomic-save-on-create)).

**Referenced Business Rules:** BR-001 through BR-032 (as applicable to selected Scheme Type); BR-033–BR-034 when resolved

---

### UC-002 — Reset scheme wizard without saving

**Actors:** Administrator

**Preconditions:**
1. New Scheme wizard is open with in-progress data.

**Main Flow:**
1. Actor clicks **Reset** (पूर्ववत / रीसेट).
2. System clears all wizard tab state for the current session.
3. No scheme record is created or updated ([BR-013](business-rules.md#br-013--scheme-wizard-atomic-save-on-create)).

**Alternative Flow:**
- None.

**Exception Flow:**
- None.

**Post Conditions:**
1. Wizard returns to an empty/default create state (Scheme Type may reset to unset or prior default per UI implementation — must not persist).

**Referenced Business Rules:** BR-013

---

## Related Documents

- [overview.md](overview.md)
- [business-rules.md](business-rules.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [../../05-ui-ux/settings/schemes/new-scheme-screen.md](../../05-ui-ux/settings/schemes/new-scheme-screen.md)
