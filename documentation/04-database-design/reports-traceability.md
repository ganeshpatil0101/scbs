# Reports Traceability — Database Requirements

## Purpose

Maps each `05-ui-ux/reports/` report spec to the database entities and columns required to generate it. Used by `@design-database-schema` to validate that domain schemas support statutory and operational reporting (BG-001 year-end close, BG-005 interactive reporting).

**Rule:** Reports aggregate ledger and master data — they do not define new persisted tables unless a materialized view is explicitly documented.

## Reference Reports

Source specs: [05-ui-ux/reports/overview.md](../05-ui-ux/reports/overview.md)

---

## Summary Matrix

| Report | Spec | Primary Entities | Grain | Key Filters |
| :--- | :--- | :--- | :--- | :--- |
| Balance Sheet | [balance-sheet-report.md](../05-ui-ux/reports/balance-sheet-report.md) | `gl_head`, `gl_group`, `gl_transaction` | GL head balance by category, comparative FY | As-on date, fiscal year |
| Daybook | [daybook-report.md](../05-ui-ux/reports/daybook-report.md) | `gl_transaction`, `gl_head`, product accounts | Voucher line per GL group per day | Business date |
| GL Wise | [gl-wise-report.md](../05-ui-ux/reports/gl-wise-report.md) | `gl_transaction`, `gl_head` | Daily debit/credit/balance per GL head | GL head, date range |
| Loan Statement | [loan-statement-report.md](../05-ui-ux/reports/loan-statement-report.md) | `loan_account`, `loan_transaction`, `loan_transaction_component`, `customer` | Transaction line per loan account | Account, date range |
| Profit & Loss | [profit-loss-statement-report.md](../05-ui-ux/reports/profit-loss-statement-report.md) | `gl_head`, `gl_group`, `gl_transaction` | Income/expense GL heads by category, comparative FY | Fiscal year |
| Purvani | [purvani-report.md](../05-ui-ux/reports/purvani-report.md) | `gl_transaction`, `gl_head`, `gl_group`, product accounts | Voucher line across GL heads | Date range, GL type/head |
| Trial Balance | [trial-balance-report.md](../05-ui-ux/reports/trial-balance-report.md) | `gl_head`, `gl_group`, `gl_transaction` | GL head debit/credit balance by category | As-on date |

---

## Report Details

### Balance Sheet (ताळेबंद)

**Type:** Print | **Pages:** 2

**Required data:**

| Output column / section | Source entity.column | Notes |
| :--- | :--- | :--- |
| GL line items with codes | `gl_head.gl_head_no`, `gl_head.name`, `gl_group.category` | Categories: liabilities, assets, capital |
| Prior-year amount | Sum `gl_transaction` before prior FY end | Comparative column |
| Current-year amount | Sum `gl_transaction` before current FY end | Comparative column |
| Deposit subtotals (Pigmy, Saving, FD, Recurring) | `gl_head` grouped under Deposits category | Product GL heads from schemes |
| Profit on liability side | P&L result carried forward | Links to P&L report |

**Schema dependencies:** `gl_head` must have `gl_group_id` → `gl_group.category` mapping to balance-sheet sections (देणी/येणी/खर्च/उत्पन्न).

**TODO:** Fiscal year table / period boundaries not yet defined.

---

### Daybook (रोज किर्द)

**Type:** Print | **Pages:** 3

**Required data:**

| Output column | Source entity.column | Notes |
| :--- | :--- | :--- |
| व्हा क्र. (Voucher No.) | `gl_transaction.voucher_no` | |
| खाते क्र. (Account No.) | Product account business number via `gl_transaction.account_id` | |
| जी.एल.क्र. (G.L. No.) | `gl_head.gl_head_no` via `gl_transaction.gl_head_id` | |
| Particulars | `gl_transaction.narration` + account holder name join | |
| रोख (Cash) | `gl_transaction.cash_amount` | |
| ट्रान्सफर (Transfer) | `gl_transaction.transfer_amount` | |
| एकूण (Total) | cash + transfer or debit/credit amount | |
| GL group header | `gl_head.name`, `gl_head.gl_head_no` | Grouped sections |
| Grand totals | Sum by Jama/Nave side | Debit = Nave, Credit = Jama |

**Schema dependencies:** `gl_transaction` must store `cash_amount` and `transfer_amount` separately (not just debit/credit).

---

### GL Wise Report (जनरल लेजर)

**Type:** Screen + Print | **Pages:** 1

**Required data:**

| Output column | Source entity.column | Notes |
| :--- | :--- | :--- |
| Date | `gl_transaction.txn_date` | One row per business date in range |
| G.L. | `gl_head.name` | Filter: single GL head |
| Opening Balance | Running balance before first txn of day | Computed from prior `gl_transaction` rows |
| Debit (नावे) | Sum `gl_transaction.debit_amount` for day | |
| Credit (जमा) | Sum `gl_transaction.credit_amount` for day | |
| Closing Balance | Running balance after day | |

**Schema dependencies:** Index `idx_gl_transaction_gl_head_id_txn_date` on `(gl_head_id, txn_date)`.

---

### Loan Account Statement (कर्ज खाते उतार)

**Type:** Print | **Pages:** 1

**Required data — header:**

| Output field | Source entity.column |
| :--- | :--- |
| G.L. Head | `gl_head.name` via `loan_account.gl_head_id` or scheme |
| Account No. | `loan_account.account_no` |
| Name | `customer` name fields |
| Customer No. | `customer.customer_no` |
| Sanctioning Officer | `loan_account.approval_officer` |
| Address | `address` via customer |
| Term, Loan Amount, Installment, Rate, Status, Overdue | `loan_account.*` |
| First Installment Date | `loan_account.first_installment_date` |

**Required data — ledger grid:**

| Output column | Source entity.column | Notes |
| :--- | :--- | :--- |
| Date | `loan_transaction.txn_date` | |
| Particulars | `loan_transaction.narration` | |
| Total Deposit | `loan_transaction.total_deposit` | |
| Principal Jama/Nave | `loan_transaction_component` where `component_type = principal` | |
| Interest Jama/Nave | `component_type = interest` | |
| Penalty Interest | `component_type = penalty_interest` | |
| Overdue Interest Receivable | `component_type = overdue_interest` | |
| Other Expenses/Deduction | `component_type = other_charge` | |
| Balance | Running principal balance | |

**Schema dependencies:** Domain entities `loan_account`, `loan_transaction`, `loan_transaction_component` in `04-database-design/loan/`.

---

### Profit & Loss Statement (नफा-तोटा पत्रक)

**Type:** Print | **Pages:** 2

**Required data:**

| Output section | Source entity.column | Notes |
| :--- | :--- | :--- |
| Expenditure lines (खर्च) | `gl_head` where `gl_group.category = expense` | Interest on deposits, admin expenses, etc. |
| Income lines (उत्पन्न) | `gl_head` where `gl_group.category = income` | Loan interest, investment interest, fees |
| Comparative FY amounts | Sum `gl_transaction` by GL head per fiscal year | |
| Net profit/loss | Income total − Expense total | |

**Schema dependencies:** `gl_group.category` must distinguish `income` vs `expense` vs `asset` vs `liability`.

---

### Purvani (पुरवणी)

**Type:** Screen + Print | **Pages:** 1

**Required data:**

| Output column | Source entity.column | Notes |
| :--- | :--- | :--- |
| Opening Balance | Sum `gl_transaction` before date range | Debit/credit label |
| Sr. No. | Row sequence | |
| G.L. Type | `gl_group` code via `gl_head.gl_group_id` | Filter optional |
| Voucher No. | `gl_transaction.voucher_no` | |
| Account No. | Product account business number | |
| Customer Name | `customer` name via account | |
| Cash / Transfer / Total | `cash_amount`, `transfer_amount` | |
| Date | `gl_transaction.txn_date` | |
| G.L. | `gl_head.name` | |
| Closing Balance | Sum through end of date range | |

**Schema dependencies:** Same as Daybook — voucher-level detail with cash/transfer split.

---

### Trial Balance (तेरीज पत्रक)

**Type:** Print | **Pages:** 3

**Required data:**

| Output column | Source entity.column | Notes |
| :--- | :--- | :--- |
| Sr. No. | Sequential across all GL heads | |
| G.L. Head name + code | `gl_head.name`, `gl_head.gl_head_no` | |
| Debit balance (नावे) | Net debit balance per GL head as-on date | |
| Credit balance (जमा) | Net credit balance per GL head as-on date | |
| Category group headers | `gl_group.name`, `gl_group.category` | देणी, येणी, खर्च, उत्पन्न sections |
| Category subtotals | Sum of GL heads in category | |
| Grand total | Total debit = Total credit | Must reconcile |
| P&L summary box | Derived from income/expense GL totals | Links to P&L |

**Schema dependencies:** Complete chart of accounts in `gl_group` + `gl_head`; all posted transactions in `gl_transaction`.

---

## Cross-Domain Schema Requirements (from reports)

These shared structures must exist before year-end reports (BG-001) can reconcile:

1. **`gl_group`** — category enum covering: liabilities, assets, income, expense, capital (maps to Trial Balance / Balance Sheet sections).
2. **`gl_head`** — full chart of accounts with `gl_head_no`, name, group, balance_type.
3. **`gl_transaction`** — all product and accounting screens post here; voucher balancing enforced.
4. **Product account tables** — each with `account_no`, `gl_head_id` (via scheme), `customer_id`, `branch_id`, `status`.
5. **Fiscal year configuration** — `TODO:` not yet defined; required for comparative Balance Sheet and P&L columns.

---

## Updating This Document

When `@design-database-schema` adds or changes entities:

1. Check if any report in this matrix is affected.
2. Add rows to the relevant report's Required data table.
3. Add new reports to the Summary Matrix when specs are added under `05-ui-ux/reports/`.
4. Append entry to domain `changelog.md` noting report traceability update.

---

## Related Documents

- [overview.md](overview.md)
- [database-design-standards.md](database-design-standards.md)
- [../05-ui-ux/reports/overview.md](../05-ui-ux/reports/overview.md)
- [../00-project-overview/business-goals.md](../00-project-overview/business-goals.md) — BG-001, BG-005
- [../../.cursor/skills/design-database-schema/SKILL.md](../../.cursor/skills/design-database-schema/SKILL.md)
