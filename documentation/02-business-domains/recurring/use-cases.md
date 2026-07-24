# Use Cases — Recurring (Recurring Deposit)

## Purpose

Actor goals for the Recurring module screens. Each use case references business rules by ID.

---

### UC-001 — Open a new Recurring Deposit account

**Actors:** Clerk / Administrator (User with All Rights on New Recurring Account form)

**Preconditions:**
1. Actor has All Rights on New Recurring Account ([BR-025](business-rules.md#br-025--recurring-screens-use-master-permission-levels)).
2. A Customer record already exists for the intended account holder ([BR-001](business-rules.md#br-001--customer-must-exist-before-recurring-account-can-be-opened)).
3. At least one active Recurring scheme exists in Settings ([BR-002](business-rules.md#br-002--scheme-required-and-loaded-from-recurring-scheme-master)).

**Main Flow:**
1. Actor opens **नवीन खाते (New Account)** under रिकरिंग (Recurring).
2. **Tab 1 — खाते माहिती (Account Information):** Actor resolves the Customer via Autocomplete ([BR-001](business-rules.md#br-001--customer-must-exist-before-recurring-account-can-be-opened)); system displays the Customer summary read-only.
3. Actor selects Scheme ([BR-002](business-rules.md#br-002--scheme-required-and-loaded-from-recurring-scheme-master)); Scheme/Interest Type and Compounding auto-fill read-only ([BR-003](business-rules.md#br-003--scheme-derived-attributes-auto-filled-read-only)). Optionally resolves Agent Branch/Agent ([BR-004](business-rules.md#br-004--agent-and-sales-agent-optional-agent-scoped-to-agent-branch)).
4. Actor selects Account Type ([BR-006](business-rules.md#br-006--account-type-required-with-defined-values)) and Duration; Duration (Months) and Interest Rate auto-fill from the scheme slab ([BR-007](business-rules.md#br-007--duration-selected-from-scheme-grid-duration-and-rate-auto-filled)). Maturity Date is calculated ([BR-010](business-rules.md#br-010--maturity-date-system-calculated)).
5. Actor confirms Account Opening Date (defaults to system date, [BR-009](business-rules.md#br-009--account-opening-date-defaults-to-system-date)), enters Installment Amount ([BR-011](business-rules.md#br-011--installment-amount-required)), selects Deposit Type ([BR-012](business-rules.md#br-012--deposit-type-required-frequency-values-todo), TODO values), and Status (default Active, [BR-014](business-rules.md#br-014--account-status-default-and-shared-values-across-deposit-products)). System computes Maturity Amount read-only ([BR-013](business-rules.md#br-013--maturity-amount-system-computed-from-scheme-interest-formula)).
6. Optionally, actor expands **प्रगत सेटिंग्ज (Advanced Settings)** ([BR-015](business-rules.md#br-015--advanced-settings-visibility-role-undefined)) to set Sales Agent ([BR-004](business-rules.md#br-004--agent-and-sales-agent-optional-agent-scoped-to-agent-branch)) or IFSC Code for bank payout ([BR-016](business-rules.md#br-016--ifsc-code-enables-bank-payout-auto-fill)).
7. Actor optionally checks Add Nominee and/or Add Joint Holder to reveal Tabs 2/3 ([BR-017](business-rules.md#br-017--nominee-section-conditional-on-add-nominee-checkbox), [BR-018](business-rules.md#br-018--joint-holder-section-conditional-on-add-joint-holder-checkbox)) and clicks **पुढे (Next)**.
8. **Tab 2 — वारसदार (Nominee)**, if enabled: Actor resolves a nominee Customer via Autocomplete or quick-add ([BR-019](business-rules.md#br-019--nominee-lookup-resolves-to-existing-or-quick-added-customer)), selects Relation from the canonical list ([BR-020](business-rules.md#br-020--nominee-relation-reuses-canonical-membership-list)), optionally enters Percentage ([BR-021](business-rules.md#br-021--nominee-percentage-optional-nomination-date-and-age-system-derived)), and clicks **टाका (Add)** to append to the nominee grid.
9. **Tab 3 — संयुक्त खातेदार (Joint Holder)**, if enabled: Actor optionally checks Guardian, resolves a joint holder Customer, and clicks **+ जोड (Add)** ([BR-022](business-rules.md#br-022--joint-holder-guardian-and-customer-fields-add-validates-selection)); selects Account Operation Instructions ([BR-023](business-rules.md#br-023--account-operation-instructions-required-with-defined-values)).
10. Actor clicks **जतन करा (Save)** — the only persist point on create ([BR-024](business-rules.md#br-024--new-recurring-account-wizard-atomic-save-on-create)).
11. System persists the Account (with auto-generated Account No., [BR-005](business-rules.md#br-005--account-no-auto-generated)), Nominee(s), and Joint Holder(s).

**Alternative Flow:**
- **A1 — Back navigation:** On Tab 2–3, actor clicks **मागे (Back)**. Prior-tab values remain in wizard state until Reset or a successful Save.
- **A2 — Single-holder account:** Actor leaves both Add Nominee and Add Joint Holder unchecked; only Tab 1 is completed and saved.
- **A3 — Quick Add nominee:** Actor cannot find the nominee in Customer search and uses **+ नवीन ग्राहक जोडा** to create a minimal Customer record inline before continuing.

**Exception Flow:**
- **E1 — Customer not found:** Autocomplete returns no match on Tab 1; actor must register the person via New Customer first ([BR-001](business-rules.md#br-001--customer-must-exist-before-recurring-account-can-be-opened)).
- **E2 — Required field missing:** System blocks Next or Save with a validation error for the missing required field (e.g. Scheme, Account Type, Duration, Installment Amount, Deposit Type, Account Operation Instructions).
- **E3 — View Only permission:** Actor with View Only can view all tabs but cannot Save ([BR-025](business-rules.md#br-025--recurring-screens-use-master-permission-levels)).
- **E4 — Interest Rate override:** Actor attempts to override the auto-filled Interest Rate; the permission gate is unresolved ([BR-008](business-rules.md#br-008--interest-rate-admin-override-role-undefined), TODO).

**Post Conditions:**
1. A Recurring account exists with a system-generated Account No., linked to the resolved Customer and Scheme, with a computed Maturity Amount and Maturity Date.
2. Zero or more Nominee records exist if Add Nominee was checked.
3. Zero or more Joint Holder records exist if Add Joint Holder was checked.

**Referenced Business Rules:** BR-001 through BR-025

---

### UC-002 — Search, view, remove, and export Recurring accounts via Account Register

**Actors:** Clerk / Cashier / Administrator (User with at least View Only on Account Register for search; All Rights for Remove)

**Preconditions:**
1. Actor has View Only or All Rights on Account Register ([BR-025](business-rules.md#br-025--recurring-screens-use-master-permission-levels)).
2. One or more Recurring accounts exist ([UC-001](#uc-001--open-a-new-recurring-deposit-account)).

**Main Flow:**
1. Actor opens **खाते रजिस्टर (Account Register)** under रिकरिंग; the संस्था (Organization) header is auto-filled from session ([BR-026](business-rules.md#br-026--organization-auto-fill-header-from-session)).
2. Actor optionally enters any combination of Primary Search filters — Branch, Scheme, Status (default Active), Account No. range, Account Holder, Customer No. range — all optional ([BR-027](business-rules.md#br-027--account-register-primary-search-fields-all-optional)).
3. Actor clicks **दाखवा (Show)**.
4. System displays matching accounts in the results grid with pagination and record count ([BR-030](business-rules.md#br-030--account-register-follows-interactive-reporting-standard)); loan-linked rows render pink and matured rows blue per the legend ([BR-028](business-rules.md#br-028--results-grid-legend-loan-linked-and-matured-highlighting), TODO).
5. Actor optionally selects a row and clicks **तपशील (Details)** for in-context detail, **निर्यात (Export)** to export the result set, or **खाते उतारा (Account Statement)** to view a statement ([BR-031](business-rules.md#br-031--account-details-and-account-statement-lack-dedicated-specs), TODO on both).
6. **To remove a row:** actor selects the account and clicks **काढा (Remove)**, which deletes the account registration row ([BR-029](business-rules.md#br-029--काढा-remove-deletes-the-account-registration-row)).

**Alternative Flow:**
- **A1 — No filters:** Actor clicks Show without entering any filter; system returns all Recurring accounts the actor is entitled to see, subject to branch-scoping ([BR-027](business-rules.md#br-027--account-register-primary-search-fields-all-optional) Notes, TODO).

**Exception Flow:**
- **E1 — No matches:** System renders an empty grid state, not an error.
- **E2 — No Rights:** Actor with No Rights on Account Register cannot navigate to the screen ([BR-025](business-rules.md#br-025--recurring-screens-use-master-permission-levels)).
- **E3 — View Only:** Actor with View Only can search, view, and export but cannot Remove ([BR-025](business-rules.md#br-025--recurring-screens-use-master-permission-levels)).
- **E4 — Remove of a transacted account:** Whether Remove is blocked for accounts with posted installment history is unresolved ([BR-029](business-rules.md#br-029--काढा-remove-deletes-the-account-registration-row), TODO).

**Post Conditions:**
1. Search/Export: no data is modified.
2. Remove: the selected account registration row is deleted.

**Referenced Business Rules:** BR-025 through BR-031

---

### UC-003 — Preview Recurring Deposit maturity via Interest Multiplier

**Actors:** Clerk / Cashier / Administrator (User with at least View Only on Interest Multiplier)

**Preconditions:**
1. Actor has View Only or All Rights on Interest Multiplier ([BR-025](business-rules.md#br-025--recurring-screens-use-master-permission-levels)).
2. At least one Recurring scheme exists in Settings ([BR-002](business-rules.md#br-002--scheme-required-and-loaded-from-recurring-scheme-master)).

**Main Flow:**
1. Actor opens **व्याज गुणक (Interest Multiplier)** under रिकरिंग.
2. Actor selects Scheme ([BR-032](business-rules.md#br-032--interest-multiplier-is-a-scheme-based-calculator-with-no-persistence)); Simple/Compound, Duration, and Interest Rate reveal/auto-fill from the scheme ([BR-033](business-rules.md#br-033--interest-multiplier-conditional-field-visibility)).
3. If the scheme is compound, actor selects the Compounding Frequency ([BR-033](business-rules.md#br-033--interest-multiplier-conditional-field-visibility)).
4. Actor enters Monthly Deposit Amount and optionally overrides Duration/Interest Rate.
5. Actor clicks **गणना करा (Calculate)**; system displays Deposit Amount, Interest Amount, and Maturity Amount, and populates the interest-breakdown grid ([BR-034](business-rules.md#br-034--interest-multiplier-computes-deposit-interest-and-maturity-amounts)).
6. Actor optionally clicks **निर्यात करा (Export)** on the breakdown grid, or **पुनर्रचना करा (Reset)** to clear.

**Alternative Flow:**
- **A1 — Simple interest scheme:** Compounding Frequency (#3) remains hidden when the scheme resolves to Simple interest ([BR-033](business-rules.md#br-033--interest-multiplier-conditional-field-visibility)).

**Exception Flow:**
- **E1 — Scheme not selected:** Option controls stay hidden and Calculate produces no output until a Scheme is chosen ([BR-032](business-rules.md#br-032--interest-multiplier-is-a-scheme-based-calculator-with-no-persistence), [BR-033](business-rules.md#br-033--interest-multiplier-conditional-field-visibility)).
- **E2 — Monthly Deposit Amount missing:** System blocks Calculate with a validation error on the required field ([BR-034](business-rules.md#br-034--interest-multiplier-computes-deposit-interest-and-maturity-amounts)).

**Post Conditions:**
1. No account is created and nothing is persisted — the screen is a preview calculator only ([BR-032](business-rules.md#br-032--interest-multiplier-is-a-scheme-based-calculator-with-no-persistence)).

**Referenced Business Rules:** BR-032 through BR-034 (and BR-002, BR-025)

---

## Related Documents

- [overview.md](overview.md)
- [business-rules.md](business-rules.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [../../05-ui-ux/recurring/new-recurring-account-screen.md](../../05-ui-ux/recurring/new-recurring-account-screen.md)
- [../../05-ui-ux/recurring/account-register-screen.md](../../05-ui-ux/recurring/account-register-screen.md)
- [../../05-ui-ux/recurring/interest-multiplier-screen.md](../../05-ui-ux/recurring/interest-multiplier-screen.md)
