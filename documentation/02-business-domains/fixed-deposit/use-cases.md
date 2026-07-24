# Use Cases — Fixed Deposit

## Purpose

Actor goals for the Fixed Deposit module screens. Each use case references business rules by ID.

---

### UC-001 — Open a new FD account

**Actors:** Clerk / Administrator (User with All Rights on New FD Account form)

**Preconditions:**
1. Actor has All Rights on New FD Account ([BR-030](business-rules.md#br-030--fd-screens-use-master-permission-levels)).
2. A Customer record already exists for the intended account holder ([BR-001](business-rules.md#br-001--customer-must-exist-before-fd-account-can-be-opened)).
3. At least one active FD scheme exists in Settings with Duration & Rates rows ([BR-002](business-rules.md#br-002--scheme-required-and-loaded-from-fd-scheme-master), [BR-007](business-rules.md#br-007--interest-rate-slab-required-and-drives-duration)).

**Main Flow:**
1. Actor opens **नवीन खाते (New Account)** under मुदत ठेव (Fixed Deposit).
2. **Tab 1 — खात्याची माहिती (Account Information):** Actor resolves the Customer via Autocomplete ([BR-001](business-rules.md#br-001--customer-must-exist-before-fd-account-can-be-opened)); the customer summary displays read-only.
3. Actor selects Scheme ([BR-002](business-rules.md#br-002--scheme-required-and-loaded-from-fd-scheme-master)); Closed/Open Ended, Interest Type, and Compounding auto-fill read-only ([BR-003](business-rules.md#br-003--scheme-derived-attributes-auto-filled-read-only)).
4. Actor optionally selects Agent Branch + Agent ([BR-004](business-rules.md#br-004--agent-and-sales-agent-optional-agent-scoped-to-agent-branch)), selects Account Type ([BR-006](business-rules.md#br-006--account-type-required-with-defined-values)) and Interest Rate Slab — Duration months/days and Interest Rate auto-fill ([BR-007](business-rules.md#br-007--interest-rate-slab-required-and-drives-duration), [BR-010](business-rules.md#br-010--interest-rate-auto-filled-from-slab-admin-override-role-undefined)).
5. Actor confirms Current Date ([BR-008](business-rules.md#br-008--current-date-defaults-to-system-date)), enters FD Amount ([BR-009](business-rules.md#br-009--fd-amount-required)) and Interest Start Date ([BR-011](business-rules.md#br-011--interest-start-date-required)); system computes Maturity Amount, Return Date, and Receipt Date ([BR-012](business-rules.md#br-012--maturity-amount-return-date-and-receipt-date-system-computed)). Actor sets Status (default Active, [BR-013](business-rules.md#br-013--account-status-default-and-shared-values-across-deposit-products)) and optional IFSC/bank payout ([BR-014](business-rules.md#br-014--ifsc-code-enables-bank-payout-auto-fill)).
6. Actor optionally expands **प्रगत सेटिंग्ज (Advanced Settings)** to set Sales Agent ([BR-004](business-rules.md#br-004--agent-and-sales-agent-optional-agent-scoped-to-agent-branch)), Receipt Prefix/Number ([BR-016](business-rules.md#br-016--receipt-prefix-and-receipt-number-required)), or Multiple FD values ([BR-017](business-rules.md#br-017--multiple-fd-workflow-semantics-undefined), TODO).
7. Actor optionally checks Add Nominee and/or Add Joint Holder to reveal Tabs 2/3 ([BR-018](business-rules.md#br-018--nominee-section-conditional-on-add-nominee-checkbox), [BR-019](business-rules.md#br-019--joint-holder-section-conditional-on-add-joint-holder-checkbox)) and clicks **पुढे (Next)**.
8. **Tab 2 — वारसदार (Nominee)**, if enabled: Actor resolves a nominee Customer via Autocomplete or quick-add ([BR-020](business-rules.md#br-020--nominee-lookup-resolves-to-existing-or-quick-added-customer)), selects Relation from the canonical list ([BR-021](business-rules.md#br-021--nominee-relation-reuses-canonical-membership-list)), optionally enters Percentage ([BR-022](business-rules.md#br-022--nominee-percentage-optional-nomination-date-and-age-system-derived)), and clicks **टाका (Add)**.
9. **Tab 3 — संयुक्त खाते धारक (Joint Holder)**, if enabled: Actor optionally checks Guardian, resolves a joint holder Customer, and clicks **+ जोड (Add)** ([BR-023](business-rules.md#br-023--joint-holder-guardian-and-customer-fields-add-validates-selection)); selects Account Operation Instructions ([BR-024](business-rules.md#br-024--account-operation-instructions-required-with-defined-values)).
10. **Tab 4 — इतर (Other):** Actor optionally configures Interest Reinvestment ([BR-025](business-rules.md#br-025--interest-reinvestment-enables-si-reinvestment-frequency)), Auto Renewal / Renewal type ([BR-026](business-rules.md#br-026--auto-renewal-and-renewal-mutually-exclusive-renewal-type-radios)), Interest Transfer routing ([BR-027](business-rules.md#br-027--interest-transfer-enables-gl-holder-and-frequency-routing)), and Account Closing routing ([BR-028](business-rules.md#br-028--account-closing-gl-routing-enabled-by-checkbox)).
11. Actor clicks **पूर्ण (Complete)**. On create, this is the only persist point ([BR-029](business-rules.md#br-029--new-fd-account-wizard-atomic-save-on-create)).
12. System persists the Account (with auto-generated Account No., [BR-005](business-rules.md#br-005--account-no-auto-generated)), Nominee(s), and Joint Holder(s).

**Alternative Flow:**
- **A1 — Back navigation:** On Tabs 2–4, actor clicks **मागे (Back)**; prior-tab values remain in wizard state until Reset or a successful Complete.
- **A2 — Single-holder account:** Actor leaves both Add Nominee and Add Joint Holder unchecked; only Tabs 1 and 4 are completed and saved.
- **A3 — Quick Add nominee:** Actor uses **+ नवीन ग्राहक जोडा** to create a minimal Customer inline before continuing ([BR-020](business-rules.md#br-020--nominee-lookup-resolves-to-existing-or-quick-added-customer)).
- **A4 — Double-money scheme:** For दामदुप्पट / कॅश सर्टिफिकेट schemes, Maturity Amount reflects the scheme grid's fixed maturity value rather than a computed interest accrual ([BR-012](business-rules.md#br-012--maturity-amount-return-date-and-receipt-date-system-computed)).

**Exception Flow:**
- **E1 — Customer not found:** Autocomplete returns no match on Tab 1; actor must register the person via New Customer first ([BR-001](business-rules.md#br-001--customer-must-exist-before-fd-account-can-be-opened)).
- **E2 — Required field missing:** System blocks Next/Complete with a validation error (e.g. Scheme, Account Type, Interest Rate Slab, FD Amount, Interest Start Date, Receipt Prefix/Number, Account Operation Instructions).
- **E3 — View Only permission:** Actor with View Only can view all tabs but cannot Complete ([BR-030](business-rules.md#br-030--fd-screens-use-master-permission-levels)).
- **E4 — Multiple FD (TODO):** Behaviour of the Multiple FD block is unresolved ([BR-017](business-rules.md#br-017--multiple-fd-workflow-semantics-undefined), TODO).

**Post Conditions:**
1. An FD account exists with a system-generated Account No., linked to the resolved Customer and Scheme, with computed Maturity Amount and Return Date.
2. Zero or more Nominee records exist if Add Nominee was checked.
3. Zero or more Joint Holder records exist if Add Joint Holder was checked.

**Referenced Business Rules:** BR-001 through BR-030

---

### UC-002 — Search and maintain FD accounts and renewal history

**Actors:** Clerk / Cashier / Administrator (View Only for search/export; All Rights for Remove)

**Preconditions:**
1. Actor has View Only or All Rights on Account Management ([BR-030](business-rules.md#br-030--fd-screens-use-master-permission-levels)).
2. One or more FD accounts exist ([UC-001](#uc-001--open-a-new-fd-account)).

**Main Flow:**
1. Actor opens **खाते व्यवस्थापन (Account Management)** under मुदत ठेव; the Organization header auto-fills read-only ([BR-031](business-rules.md#br-031--account-management-search-fields-all-optional-organization-auto-filled)).
2. **Tab 1 — खाते रजिस्टर (Account Register):** Actor optionally enters any combination of Branch, Scheme, Status, Account No. range, Account Holder, Customer No. range — all optional ([BR-031](business-rules.md#br-031--account-management-search-fields-all-optional-organization-auto-filled)) — and clicks **दाखवा (Show)**.
3. System renders matching accounts with pagination and totals ([BR-033](business-rules.md#br-033--account-management-follows-interactive-reporting-standard)); loan-linked rows show pink, matured rows show blue ([BR-032](business-rules.md#br-032--register-grid-legend-loan-linked-and-matured-accounts)).
4. Actor optionally selects a row and clicks **तपशील (Details)** for in-context detail, **निर्यात करा (Export)**, or **खाते उतारा (Account Statement)** ([BR-035](business-rules.md#br-035--account-statement-and-details-lack-dedicated-specs), TODO).
5. **To remove a row:** actor clicks **काढा (Remove)**, which deletes the selected account registration row ([BR-034](business-rules.md#br-034--काढा-remove-deletes-the-account-registration-row)).
6. **Tab 2 — नूतनीकरण यादी (Renewal List):** Actor filters (Branch, Scheme, Account Holder, Account No./Customer No. ranges, Renewal Date range, Receipt Number) and clicks Show; system lists renewal events, exportable via निर्यात करा ([BR-036](business-rules.md#br-036--renewal-list-is-read-and-export-only)).

**Alternative Flow:**
- **A1 — No filters:** Actor clicks Show without filters; system returns all FD accounts the actor is entitled to see, subject to branch-scoping ([BR-031](business-rules.md#br-031--account-management-search-fields-all-optional-organization-auto-filled) Notes, TODO).

**Exception Flow:**
- **E1 — No Rights:** Actor with No Rights cannot navigate to the screen ([BR-030](business-rules.md#br-030--fd-screens-use-master-permission-levels)).
- **E2 — View Only:** Actor with View Only can search, view, and export but cannot Remove.
- **E3 — Remove restriction (TODO):** Whether Remove is blocked for accounts with posted transactions is unresolved ([BR-034](business-rules.md#br-034--काढा-remove-deletes-the-account-registration-row)).

**Post Conditions:**
1. Search/Export: no data is modified.
2. Remove: the selected account registration row is deleted.
3. Renewal List: no data is modified (read/export only).

**Referenced Business Rules:** BR-030 through BR-036

---

### UC-003 — Record a deposit-loan installment payment

**Actors:** Clerk / Cashier (User with All Rights on Deposit Loan Installment Payment form)

**Preconditions:**
1. Actor has All Rights on Deposit Loan Installment Payment ([BR-030](business-rules.md#br-030--fd-screens-use-master-permission-levels)).
2. A loan-against-deposit already exists, opened via [New Deposit Loan](../../05-ui-ux/loan/new-deposit-loan-screen.md) ([BR-037](business-rules.md#br-037--deposit-loan-must-exist-before-installment-payment)).

**Main Flow:**
1. Actor opens **ठेव कर्ज हप्ता पेमेंट (Deposit Loan Installment Payment)** under the Deposit menu.
2. **Tab 1 — व्याज (Interest):** Actor selects Cash/Transfer mode and a GL, then resolves the loan by Customer **or** Account Holder ([BR-038](business-rules.md#br-038--installment-interest-tab-requires-mode-gl-and-a-customer-or-account-holder-lookup)); Date is read-only (system date).
3. Actor clicks **व्याज गणना करा (Calculate Interest)**; system populates the installment grid (Principal Installment, Current Interest, Total Installment) ([BR-039](business-rules.md#br-039--calculate-interest-populates-installment-grid-set-applies)).
4. Actor selects rows (or `सर्व निवडा`) and clicks **निर्धारित करा (Set)**; system applies the selected installments and updates the summary (एकूण तरतूद, एकूण व्याज, एकूण रक्कम) ([BR-039](business-rules.md#br-039--calculate-interest-populates-installment-grid-set-applies), TODO).

**Alternative Flow:**
- **A1 — Account Holder lookup:** Actor uses Account Holder Autocomplete instead of Customer when the customer number is not to hand ([BR-038](business-rules.md#br-038--installment-interest-tab-requires-mode-gl-and-a-customer-or-account-holder-lookup)).

**Exception Flow:**
- **E1 — No loan found:** No installment lines are returned because the resolved party has no active deposit loan ([BR-037](business-rules.md#br-037--deposit-loan-must-exist-before-installment-payment)).
- **E2 — Tabs 2–6 (TODO):** Other Deductions, Loan Information, Collateral, Transfer, and KYC tabs are not captured ([BR-040](business-rules.md#br-040--deposit-loan-installment-tabs-26-not-captured), TODO).
- **E3 — View Only:** Actor with View Only can calculate interest but cannot Set/persist an installment ([BR-030](business-rules.md#br-030--fd-screens-use-master-permission-levels)).

**Post Conditions:**
1. `TODO:` What "Set" persists (a posted transaction vs. a staged installment) is unresolved pending the Loan domain ([BR-039](business-rules.md#br-039--calculate-interest-populates-installment-grid-set-applies)).

**Referenced Business Rules:** BR-030, BR-037 through BR-040

---

### UC-004 — Calculate FD interest rate or duration

**Actors:** Clerk / Cashier / Administrator (any User with access to Interest Multiplier)

**Preconditions:**
1. Actor has at least View Only on FD Interest Multiplier ([BR-030](business-rules.md#br-030--fd-screens-use-master-permission-levels)).
2. At least one FD scheme exists ([BR-041](business-rules.md#br-041--interest-multiplier-is-a-scheme-based-calculator-with-no-persistence)).

**Main Flow:**
1. Actor opens **व्याज गुणक (Interest Multiplier)** under मुदत ठेव.
2. Actor selects an FD Scheme; option controls become visible ([BR-042](business-rules.md#br-042--interest-multiplier-conditional-field-visibility)).
3. Actor sets product type, Simple/Compounding (and Compounding Frequency if applicable), Duration in Days/Months, and the Calculate Interest Rate/Duration target ([BR-042](business-rules.md#br-042--interest-multiplier-conditional-field-visibility), [BR-043](business-rules.md#br-043--interest-multiplier-computes-interest-rate-or-duration)).
4. Actor enters Duration (Months or Days) as applicable and clicks **गणना करा (Calculate)**.
5. System displays read-only व्याज दर (Interest Rate) and दिनांक फरक (Date Difference) outputs ([BR-043](business-rules.md#br-043--interest-multiplier-computes-interest-rate-or-duration)).

**Alternative Flow:**
- **A1 — Reset:** Actor clicks **पूर्वत (Reset)** to clear the form and outputs ([BR-041](business-rules.md#br-041--interest-multiplier-is-a-scheme-based-calculator-with-no-persistence)).

**Exception Flow:**
- **E1 — No scheme selected:** Option controls stay hidden until a Scheme is selected ([BR-042](business-rules.md#br-042--interest-multiplier-conditional-field-visibility)).

**Post Conditions:**
1. No account or record is created; the screen is stateless ([BR-041](business-rules.md#br-041--interest-multiplier-is-a-scheme-based-calculator-with-no-persistence)).

**Referenced Business Rules:** BR-030, BR-041 through BR-043

---

## Related Documents

- [overview.md](overview.md)
- [business-rules.md](business-rules.md)
- [workflows.md](workflows.md)
- [acceptance-tests.md](acceptance-tests.md)
- [../../05-ui-ux/fixed-deposit/new-fd-account-screen.md](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md)
- [../../05-ui-ux/fixed-deposit/fd-account-management-screen.md](../../05-ui-ux/fixed-deposit/fd-account-management-screen.md)
- [../../05-ui-ux/fixed-deposit/deposit-loan-installment-payment-screen.md](../../05-ui-ux/fixed-deposit/deposit-loan-installment-payment-screen.md)
- [../../05-ui-ux/fixed-deposit/fd-interest-multiplier-screen.md](../../05-ui-ux/fixed-deposit/fd-interest-multiplier-screen.md)
