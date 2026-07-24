# Use Cases — Savings

## Purpose

Actor goals for the Savings module screens. Each use case references business rules by ID.

---

### UC-001 — Open a new Savings account

**Actors:** Clerk / Administrator (User with All Rights on New Savings Account form)

**Preconditions:**
1. Actor has All Rights on New Savings Account ([BR-020](business-rules.md#br-020--savings-screens-use-master-permission-levels)).
2. A Customer record already exists for the intended account holder ([BR-001](business-rules.md#br-001--customer-must-exist-before-savings-account-can-be-opened)).
3. At least one active Savings scheme exists in Settings ([BR-002](business-rules.md#br-002--scheme-required-and-loaded-from-savings-scheme-master)).

**Main Flow:**
1. Actor opens **नवीन खाते (New Account)** under बचत (Savings).
2. **Tab 1 — खात्याची माहिती (Account Information):** Actor resolves the Customer via Autocomplete ([BR-001](business-rules.md#br-001--customer-must-exist-before-savings-account-can-be-opened)); system displays the Customer's विशेष सूचना summary read-only.
3. Actor selects Scheme ([BR-002](business-rules.md#br-002--scheme-required-and-loaded-from-savings-scheme-master)); Interest Rate auto-fills read-only from the scheme ([BR-005](business-rules.md#br-005--interest-rate-auto-filled-from-scheme-admin-override-role-undefined)).
4. Actor confirms Current Date (defaults to system date, [BR-006](business-rules.md#br-006--current-date-defaults-to-system-date)), enters Minimum Balance ([BR-007](business-rules.md#br-007--minimum-balance-required-at-opening)), optional Special Instructions, and Status (default Active, [BR-008](business-rules.md#br-008--account-status-default-and-shared-values-across-deposit-products)).
5. Optionally, actor expands **प्रगत सेटिंग्ज (Advanced Settings)** to set Debit Limit, Fund Transfer Limit ([BR-010](business-rules.md#br-010--debit-limit-and-fund-transfer-limit-optional-overrides)), or IFSC Code for bank payout ([BR-011](business-rules.md#br-011--ifsc-code-enables-bank-payout-auto-fill)).
6. Actor optionally checks Add Nominee and/or Add Joint Holder to reveal Tabs 2/3 ([BR-012](business-rules.md#br-012--nominee-section-conditional-on-add-nominee-checkbox), [BR-013](business-rules.md#br-013--joint-holder-section-conditional-on-add-joint-holder-checkbox)).
7. Actor clicks **पुढे (Next)**.
8. **Tab 2 — वारसदार (Nominee)**, if enabled: Actor resolves a nominee Customer via Autocomplete or quick-add popup ([BR-014](business-rules.md#br-014--nominee-lookup-resolves-to-existing-or-quick-added-customer)), selects Relation from the canonical list ([BR-015](business-rules.md#br-015--nominee-relation-reuses-canonical-membership-list)), optionally enters Percentage ([BR-016](business-rules.md#br-016--nominee-percentage-optional-nomination-date-and-age-system-derived)), and clicks **टाका (Add)** to append to the nominee grid.
9. Actor clicks Next.
10. **Tab 3 — संयुक्त खाते धारक (Joint Holder)**, if enabled: Actor optionally checks Guardian, resolves a joint holder Customer, and clicks **+ जोड (Add)** ([BR-017](business-rules.md#br-017--joint-holder-guardian-and-customer-fields-add-validates-selection)) to append to the grid. Actor selects Account Operation Instructions ([BR-018](business-rules.md#br-018--account-operation-instructions-required-with-defined-values)).
11. Actor clicks **जतन करा (Save)**. On create, this is the only persist point ([BR-019](business-rules.md#br-019--new-savings-account-wizard-atomic-save-on-create)).
12. System persists the Account (with auto-generated Account No., [BR-004](business-rules.md#br-004--account-no-auto-generated)), Nominee(s), and Joint Holder(s).

**Alternative Flow:**
- **A1 — Back navigation:** On Tab 2–3, actor clicks **मागे (Back)**. Values entered on prior tabs remain in wizard state until Reset or a successful Save.
- **A2 — Single-holder account:** Actor leaves both Add Nominee and Add Joint Holder unchecked; only Tab 1 is completed and saved.
- **A3 — Quick Add nominee:** Actor cannot find the nominee in Customer search and uses **+ नवीन ग्राहक जोडा** to create a minimal Customer record inline before continuing.

**Exception Flow:**
- **E1 — Customer not found:** Autocomplete returns no match on Tab 1; actor must register the person via New Customer first ([BR-001](business-rules.md#br-001--customer-must-exist-before-savings-account-can-be-opened)).
- **E2 — Required field missing:** System blocks Next or Save and displays a validation error for the missing required field (e.g. Scheme, Minimum Balance, Account Operation Instructions).
- **E3 — View Only permission:** Actor with View Only on New Savings Account can view all tabs but cannot Save ([BR-020](business-rules.md#br-020--savings-screens-use-master-permission-levels)).
- **E4 — Member-only scheme:** Selected scheme requires Member-only account holders; enforcement mechanism on this screen is unresolved ([BR-003](business-rules.md#br-003--member-only-scheme-enforcement-not-verifiable-on-this-screen), TODO).

**Post Conditions:**
1. A Savings account exists with a system-generated Account No., linked to the resolved Customer and Scheme.
2. Zero or more Nominee records exist if Add Nominee was checked.
3. Zero or more Joint Holder records exist if Add Joint Holder was checked.

**Referenced Business Rules:** BR-001 through BR-020

---

### UC-002 — Search, view, and maintain Savings accounts via Account Register

**Actors:** Clerk / Cashier / Administrator (User with at least View Only on Account Register for search; All Rights for Remove/Close)

**Preconditions:**
1. Actor has View Only or All Rights on Account Register ([BR-020](business-rules.md#br-020--savings-screens-use-master-permission-levels)).
2. One or more Savings accounts exist ([UC-001](#uc-001--open-a-new-savings-account)).

**Main Flow:**
1. Actor opens **खाते रजिस्टर (Account Register)** under बचत.
2. Actor optionally enters any combination of Primary Search filters — Branch, Scheme, Status (default Active), Account No. range, Account Holder, Customer No. range — all optional ([BR-021](business-rules.md#br-021--account-register-primary-search-fields-all-optional)).
3. Actor optionally checks कर्ज संलग्नीत खाते (Loan-linked accounts) to filter/highlight linked accounts ([BR-022](business-rules.md#br-022--loan-linked-accounts-filter-depends-on-undocumented-loan-domain), TODO).
4. Actor clicks **दाखवा (Show)**.
5. System displays matching accounts in the results grid with pagination and totals ([BR-023](business-rules.md#br-023--account-register-grid-and-search-follow-interactive-reporting-standard)); loan-linked rows render with pink highlighting.
6. Actor optionally selects a row and clicks **तपशील (Details)** for in-context detail, **निर्यात करा (Export)** to export the result set, or **खाते उतारा (Account Statement)** to view a statement ([BR-026](business-rules.md#br-026--account-details-and-account-statement-lack-dedicated-specs), TODO on both).
7. **To remove a row:** actor clicks **वगळा (Exclude)**, which behaves as Remove ([BR-024](business-rules.md#br-024--वगळा-exclude-is-equivalent-to-काढा-remove)).
8. **To close an account:** actor selects the account and clicks **खाते बंद करा (Close Account)**; system validates zero balance and no other active bank relationships before closing ([BR-025](business-rules.md#br-025--close-account-requires-zero-balance-and-no-other-active-bank-relationships)).

**Alternative Flow:**
- **A1 — No filters:** Actor clicks Show without entering any filter; system returns all Savings accounts the actor is entitled to see, subject to branch-scoping ([BR-021](business-rules.md#br-021--account-register-primary-search-fields-all-optional) Notes, TODO).
- **A2 — Revert:** Actor clicks **पूर्ववत** to discard a pending action before it is committed.

**Exception Flow:**
- **E1 — Close blocked (non-zero balance):** System rejects Close Account with a validation error naming the outstanding balance ([BR-025](business-rules.md#br-025--close-account-requires-zero-balance-and-no-other-active-bank-relationships)).
- **E2 — Close blocked (active relationship):** System rejects Close Account because the customer holds an active Loan, Daily, Recurring, or FD account ([BR-025](business-rules.md#br-025--close-account-requires-zero-balance-and-no-other-active-bank-relationships)).
- **E3 — No Rights:** Actor with No Rights on Account Register cannot navigate to the screen ([BR-020](business-rules.md#br-020--savings-screens-use-master-permission-levels)).
- **E4 — View Only:** Actor with View Only can search and view but cannot Remove or Close Account.

**Post Conditions:**
1. Search: no data is modified.
2. Remove: the selected account registration row is deleted.
3. Close Account: the account's Status becomes `बंद` and Account Close Date is recorded.

**Referenced Business Rules:** BR-020 through BR-026

---

## Related Documents

- [overview.md](overview.md)
- [business-rules.md](business-rules.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [../../05-ui-ux/savings/new-savings-account-screen.md](../../05-ui-ux/savings/new-savings-account-screen.md)
- [../../05-ui-ux/savings/account-register-screen.md](../../05-ui-ux/savings/account-register-screen.md)
