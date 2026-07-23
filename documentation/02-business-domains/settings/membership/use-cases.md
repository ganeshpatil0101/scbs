# Use Cases — Settings / Membership

## Purpose

Actor goals for Membership Configuration. Each use case references business rules by ID.

---

### UC-001 — Save or remove share rules

**Actors:** Administrator (User with All Rights on Membership Configuration)

**Preconditions:**
1. Actor has All Rights on Membership Configuration ([BR-013](business-rules.md#br-013--membership-configuration-uses-master-permission-levels)).

**Main Flow:**
1. Actor opens **Membership Configuration** and selects Tab **Share Rules**.
2. Actor selects Member or Nominal Member ([BR-001](business-rules.md#br-001--member-class-filter-mutually-exclusive)).
3. Actor enters required share-rule fields ([BR-002](business-rules.md#br-002--share-rule-required-fields)).
4. Actor clicks **Complete / Save**. System validates series uniqueness within the class ([BR-003](business-rules.md#br-003--share-series-unique-within-member-class)) and persists a grid row ([BR-004](business-rules.md#br-004--share-rule-save-persists-grid-row)).

**Alternative Flow:**
- **A1 — Remove:** Actor selects one or more grid rows and clicks **Remove** ([BR-005](business-rules.md#br-005--share-rule-remove-deletes-selected-rows)).
- **A2 — Nominal Member rules:** Actor switches filter to Nominal Member and saves a series for that class independently of Member-class series.

**Exception Flow:**
- **E1 — Required field missing:** System blocks Save.
- **E2 — Duplicate series in class:** System rejects Save ([BR-003](business-rules.md#br-003--share-series-unique-within-member-class)).
- **E3 — View Only:** Save/Remove hidden ([BR-013](business-rules.md#br-013--membership-configuration-uses-master-permission-levels)).

**Post Conditions:**
1. Share-rule grid reflects persisted rows for the selected Member class.
2. Operational New Membership can consume these limits (downstream).

**Referenced Business Rules:** BR-001, BR-002, BR-003, BR-004, BR-005, BR-006, BR-013

---

### UC-002 — Preview dividend calculation

**Actors:** Administrator (All Rights on Membership Configuration)

**Preconditions:**
1. Member capital data exists for the selected class (operational membership data).
2. Actor has All Rights on the form ([BR-013](business-rules.md#br-013--membership-configuration-uses-master-permission-levels)).

**Main Flow:**
1. Actor opens Tab **Dividend Calculation**.
2. Actor selects Member class ([BR-001](business-rules.md#br-001--member-class-filter-mutually-exclusive)), required Year ([BR-007](business-rules.md#br-007--dividend-year-required)), and Debit Account Head ([BR-008](business-rules.md#br-008--dividend-debit-account-head-required)); optionally Branch and Percentage ([BR-009](business-rules.md#br-009--dividend-branch-filter-optional), [BR-010](business-rules.md#br-010--dividend-percentage-optional)).
3. Actor clicks **Calculate Dividend**.
4. System displays results grid and totals as a preview only ([BR-011](business-rules.md#br-011--dividend-calculate-is-preview-only)).

**Alternative Flow:**
- **A1 — Branch scoped:** With Branch selected, results include only that branch’s members.

**Exception Flow:**
- **E1 — Year or Debit Head missing:** System blocks Calculate.
- **E2 — View Only:** Calculate hidden ([BR-013](business-rules.md#br-013--membership-configuration-uses-master-permission-levels)).

**Post Conditions:**
1. Preview grid and totals are shown on screen.
2. No dividend voucher or payment obligation is created ([BR-011](business-rules.md#br-011--dividend-calculate-is-preview-only)).

**Referenced Business Rules:** BR-001, BR-007, BR-008, BR-009, BR-010, BR-011, BR-012, BR-013

---

## Related Documents

- [overview.md](overview.md)
- [business-rules.md](business-rules.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [../../05-ui-ux/settings/membership/membership-configuration-screen.md](../../05-ui-ux/settings/membership/membership-configuration-screen.md)
