# Use Cases — Settings / Loan

## Purpose

Actor goals for Loan Interest Rate Change.

---

### UC-001 — Change loan scheme interest rate

**Actors:** Administrator (User with All Rights on Interest Rate Change)

**Preconditions:**
1. At least one Loan scheme exists ([BR-002](business-rules.md#br-002--scheme-list-from-loan-schemes-only)).
2. Actor has All Rights on the form ([BR-012](business-rules.md#br-012--loan-interest-rate-change-uses-master-permission-levels)).

**Main Flow:**
1. Actor opens **Interest Rate Change** (व्याज दरात बदल).
2. Actor selects Scheme ([BR-001](business-rules.md#br-001--loan-scheme-required)), Change Date ([BR-003](business-rules.md#br-003--change-date-required)), New Interest Rate ([BR-004](business-rules.md#br-004--new-interest-rate-required)), optionally New Penalty Rate ([BR-005](business-rules.md#br-005--new-penalty-rate-optional)), and apply scope ([BR-006](business-rules.md#br-006--apply-scope-mutually-exclusive)).
3. Actor clicks **Save**.
4. System updates the scheme template ([BR-007](business-rules.md#br-007--scheme-template-always-updated-on-save)), applies account-scope rules ([BR-008](business-rules.md#br-008--apply-new-rate-to-all-accounts) or [BR-009](business-rules.md#br-009--apply-new-rate-to-new-accounts-only)), and appends a history row ([BR-010](business-rules.md#br-010--rate-change-appends-history-row)).

**Alternative Flow:**
- **A1 — New accounts only:** Actor selects Apply New Rate to New Accounts Only ([BR-009](business-rules.md#br-009--apply-new-rate-to-new-accounts-only)).
- **A2 — View history:** Actor expands Past Rate Changes ([BR-011](business-rules.md#br-011--history-section-collapsed-by-default)).
- **A3 — Export:** Actor clicks Export (contents per [BR-014](business-rules.md#br-014--export-contents) when confirmed).

**Exception Flow:**
- **E1 — Required field missing:** System blocks Save.
- **E2 — No Loan schemes:** Scheme dropdown empty; actor must create a Loan scheme first.
- **E3 — View Only:** Save hidden ([BR-012](business-rules.md#br-012--loan-interest-rate-change-uses-master-permission-levels)).

**Post Conditions:**
1. Loan scheme template rate reflects New Interest Rate (and penalty when provided).
2. Existing accounts updated or retained per apply scope.
3. History grid includes the new change row.

**Referenced Business Rules:** BR-001 through BR-012

---

## Related Documents

- [overview.md](overview.md)
- [business-rules.md](business-rules.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [../../05-ui-ux/settings/loan/loan-interest-rate-change-screen.md](../../05-ui-ux/settings/loan/loan-interest-rate-change-screen.md)
