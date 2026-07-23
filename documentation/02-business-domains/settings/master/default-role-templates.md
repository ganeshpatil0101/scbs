# Default Role Templates — Clerk / Cashier / Manager

## Purpose

Reusable **Role** permission profiles seeded when a new tenant is provisioned. Used by Staff & System Access Tab 4 ([BR-020](business-rules.md#br-020--staff-access-assigns-existing-role)) and by the tenant bootstrap checklist ([tenant-setup.md](../../../00-project-overview/tenant-setup.md)).

These are **Year-1 cooperative-bank defaults** for seed scripts — the bank may customize Roles after go-live. Values follow [BR-017](business-rules.md#br-017--permission-levels-are-all-rights--view-only--no-rights).

## Legend

| Code | Level | Marathi |
| :--- | :--- | :--- |
| AR | All Rights | सर्व अधिकार |
| VO | View Only | फक्त बघण्यासाठी |
| NR | No Rights | अधिकार नाही |

## Seed Roles

| Role code | Role name (EN) | Role name (MR) | Intent |
| :--- | :--- | :--- | :--- |
| `clerk` | Clerk | क्लर्क | Account opening, customer/membership ops, transactional posting (maker) |
| `cashier` | Cashier | कॅशियर | Cash desk — Rokhapal, note exchange, cash receipts/payments |
| `manager` | Manager | व्यवस्थापक | Supervision — verification, passing, interest, settings configuration |

**Out of seed:** Super User is a User flag ([BR-012](business-rules.md#br-012--super-user-permission-bypass)), not a Role. Create the first admin as Super User + Manager role during tenant setup.

## Design principles (seed)

1. **Maker–checker:** Clerk posts; Manager verifies/passes; Cashier does not pass/verify.
2. **Cash desk:** Cashier has AR on Rokhapal, Note Exchange, Jama, Nave, Deposit Account Transaction; limited elsewhere.
3. **Settings:** Only Manager has AR on Settings forms; Clerk/Cashier get NR.
4. **Interest / rate change:** Manager AR; Clerk VO or NR; Cashier NR.
5. Form list = all **current** (non-superseded) `05-ui-ux` screens as of 2026-07-23 (51 forms). When new screens are added, update this matrix and the seed script together.

## Permission matrix

`form_code` is the suggested menu-registry / seed key (stable identifier for `role_permission`).

| # | Menu | Form (EN) | Form (MR) | form_code | Clerk | Cashier | Manager | Spec |
| :---: | :--- | :--- | :--- | :--- | :---: | :---: | :---: | :--- |
| 1 | Accounting | Cashier (Rokhapal) | रोखपाल | `accounting.rokhapal` | VO | AR | AR | [rokhapal-screen.md](../../05-ui-ux/accounting/rokhapal-screen.md) |
| 2 | Accounting | Contra | कॉन्ट्रा | `accounting.contra` | AR | VO | AR | [contra-screen.md](../../05-ui-ux/accounting/contra-screen.md) |
| 3 | Accounting | Credit / Receipt | जमा | `accounting.jama` | AR | AR | AR | [jama-screen.md](../../05-ui-ux/accounting/jama-screen.md) |
| 4 | Accounting | Debit / Payment | नावे | `accounting.nave` | AR | AR | AR | [nave-screen.md](../../05-ui-ux/accounting/nave-screen.md) |
| 5 | Accounting | Deposit Account Transaction | ठेव खाते व्यवहार | `accounting.deposit-account-transaction` | AR | AR | AR | [deposit-account-transaction-screen.md](../../05-ui-ux/accounting/deposit-account-transaction-screen.md) |
| 6 | Accounting | Manual Interest Management | मॅन्युअल व्याज व्यवस्थापन | `accounting.manual-interest-management` | VO | NR | AR | [manual-interest-management-screen.md](../../05-ui-ux/accounting/manual-interest-management-screen.md) |
| 7 | Accounting | Multiple GL Transaction | एकाधिक जीएल व्यवहार | `accounting.multi-gl-transaction` | AR | VO | AR | [multi-gl-transaction-screen.md](../../05-ui-ux/accounting/multi-gl-transaction-screen.md) |
| 8 | Accounting | Note Exchange | नोटांची अदलाबदल | `accounting.note-exchange` | VO | AR | AR | [note-exchange-screen.md](../../05-ui-ux/accounting/note-exchange-screen.md) |
| 9 | Accounting | Transaction Passing | व्यवहार पासिंग | `accounting.transaction-passing` | NR | NR | AR | [transaction-passing-screen.md](../../05-ui-ux/accounting/transaction-passing-screen.md) |
| 10 | Accounting | Transaction Verification | व्यवहार तपासणी | `accounting.transaction-verification` | VO | VO | AR | [transaction-verification-screen.md](../../05-ui-ux/accounting/transaction-verification-screen.md) |
| 11 | Accounting | Transfer | ट्रान्सफर | `accounting.transfer` | AR | VO | AR | [transfer-screen.md](../../05-ui-ux/accounting/transfer-screen.md) |
| 12 | Bank | Bank Management | बँक व्यवस्थापन | `bank.bank-management` | AR | VO | AR | [bank-management-screen.md](../../05-ui-ux/bank/bank-management-screen.md) |
| 13 | Customer | Customer List | ग्राहक यादी | `customer.customer-list` | AR | VO | AR | [customer-list-screen.md](../../05-ui-ux/customer/customer-list-screen.md) |
| 14 | Customer | New Customer | नवीन ग्राहक | `customer.new-customer` | AR | NR | AR | [new-customer-screen.md](../../05-ui-ux/customer/new-customer-screen.md) |
| 15 | Customer | Other Account Management | इतर खाते व्यवस्थापन | `customer.other-account-management` | AR | NR | AR | [other-account-management-screen.md](../../05-ui-ux/customer/other-account-management-screen.md) |
| 16 | Daily | Account Register | खाते रजिस्टर | `daily.account-register` | AR | VO | AR | [account-register-screen.md](../../05-ui-ux/daily/account-register-screen.md) |
| 17 | Daily | Agent Collection Management | एजंट कलेक्शन व्यवस्थापन | `daily.agent-collection-management` | AR | VO | AR | [agent-collection-management-screen.md](../../05-ui-ux/daily/agent-collection-management-screen.md) |
| 18 | Daily | Agent to Agent Account Transfer | एजंट कडून एजंट कडे खाते ट्रान्सफर | `daily.agent-to-agent-transfer` | AR | NR | AR | [agent-to-agent-transfer-screen.md](../../05-ui-ux/daily/agent-to-agent-transfer-screen.md) |
| 19 | Daily | Interest Multiplier | व्याज गुणक | `daily.interest-multiplier` | VO | NR | AR | [interest-multiplier-screen.md](../../05-ui-ux/daily/interest-multiplier-screen.md) |
| 20 | Daily | New Account | नवीन खाते | `daily.new-account` | AR | NR | AR | [new-daily-account-screen.md](../../05-ui-ux/daily/new-daily-account-screen.md) |
| 21 | Daily | New Agent | नवीन एजंट | `daily.new-agent` | AR | NR | AR | [new-agent-screen.md](../../05-ui-ux/daily/new-agent-screen.md) |
| 22 | Fixed Deposit | Account Management | खाते व्यवस्थापन | `fd.account-management` | AR | VO | AR | [fd-account-management-screen.md](../../05-ui-ux/fixed-deposit/fd-account-management-screen.md) |
| 23 | Fixed Deposit | Deposit Loan Installment Payment | ठेव कर्ज हप्ता पेमेंट | `fd.deposit-loan-installment-payment` | AR | VO | AR | [deposit-loan-installment-payment-screen.md](../../05-ui-ux/fixed-deposit/deposit-loan-installment-payment-screen.md) |
| 24 | Fixed Deposit | Interest Multiplier | व्याज गुणक | `fd.interest-multiplier` | VO | NR | AR | [fd-interest-multiplier-screen.md](../../05-ui-ux/fixed-deposit/fd-interest-multiplier-screen.md) |
| 25 | Fixed Deposit | New Account | नवीन खाते | `fd.new-account` | AR | NR | AR | [new-fd-account-screen.md](../../05-ui-ux/fixed-deposit/new-fd-account-screen.md) |
| 26 | Investment | Bank Deposit Bank Management | बँक ठेव बँक व्यवस्थापन | `investment.bank-deposit-bank-management` | AR | NR | AR | [bank-deposit-bank-management-screen.md](../../05-ui-ux/investment/bank-deposit-bank-management-screen.md) |
| 27 | Investment | Interest Management | व्याज व्यवस्थापन | `investment.interest-management` | VO | NR | AR | [bank-deposit-interest-management-screen.md](../../05-ui-ux/investment/bank-deposit-interest-management-screen.md) |
| 28 | Investment | New Account | नवीन खाते | `investment.new-account` | AR | NR | AR | [bank-deposit-new-account-screen.md](../../05-ui-ux/investment/bank-deposit-new-account-screen.md) |
| 29 | Investment | Transaction | व्यवहार | `investment.transaction` | AR | VO | AR | [bank-deposit-transaction-screen.md](../../05-ui-ux/investment/bank-deposit-transaction-screen.md) |
| 30 | Loan | Account Register | खाते रजिस्टर | `loan.account-register` | AR | VO | AR | [loan-account-register-screen.md](../../05-ui-ux/loan/loan-account-register-screen.md) |
| 31 | Loan | Interest Management | व्याज व्यवस्थापन | `loan.interest-management` | VO | NR | AR | [loan-interest-management-screen.md](../../05-ui-ux/loan/loan-interest-management-screen.md) |
| 32 | Loan | Loan Information | कर्ज माहिती | `loan.loan-information` | AR | VO | AR | [loan-information-screen.md](../../05-ui-ux/loan/loan-information-screen.md) |
| 33 | Loan | Loan Transaction | कर्ज व्यवहार | `loan.loan-transaction` | AR | VO | AR | [loan-transaction-screen.md](../../05-ui-ux/loan/loan-transaction-screen.md) |
| 34 | Loan | New Deposit Loan | नवीन ठेव कर्ज | `loan.new-deposit-loan` | AR | NR | AR | [new-deposit-loan-screen.md](../../05-ui-ux/loan/new-deposit-loan-screen.md) |
| 35 | Loan | New Loan | नवीन कर्ज | `loan.new-loan` | AR | NR | AR | [new-loan-screen.md](../../05-ui-ux/loan/new-loan-screen.md) |
| 36 | Membership | Dividend Transaction | लाभांश व्यवहार | `membership.dividend-transaction` | AR | NR | AR | [dividend-transaction-screen.md](../../05-ui-ux/membership/dividend-transaction-screen.md) |
| 37 | Membership | Member Register | सभासद रजिस्टर | `membership.member-register` | AR | VO | AR | [member-register-screen.md](../../05-ui-ux/membership/member-register-screen.md) |
| 38 | Membership | Membership Transaction | सभासदत्व व्यवहार | `membership.membership-transaction` | AR | NR | AR | [membership-transaction-screen.md](../../05-ui-ux/membership/membership-transaction-screen.md) |
| 39 | Membership | New Membership | नवीन सभासदत्व | `membership.new-membership` | AR | NR | AR | [new-membership-screen.md](../../05-ui-ux/membership/new-membership-screen.md) |
| 40 | Membership | Shares Transfer Management | शेअर्स ट्रान्सफर व्यवस्थापन | `membership.shares-transfer-management` | AR | NR | AR | [shares-transfer-management-screen.md](../../05-ui-ux/membership/shares-transfer-management-screen.md) |
| 41 | Recurring | Account Register | खाते रजिस्टर | `recurring.account-register` | AR | VO | AR | [account-register-screen.md](../../05-ui-ux/recurring/account-register-screen.md) |
| 42 | Recurring | Interest Multiplier | व्याज गुणक | `recurring.interest-multiplier` | VO | NR | AR | [interest-multiplier-screen.md](../../05-ui-ux/recurring/interest-multiplier-screen.md) |
| 43 | Recurring | New Account | नवीन खाते | `recurring.new-account` | AR | NR | AR | [new-recurring-account-screen.md](../../05-ui-ux/recurring/new-recurring-account-screen.md) |
| 44 | Savings | Account Register | खाते रजिस्टर | `savings.account-register` | AR | VO | AR | [account-register-screen.md](../../05-ui-ux/savings/account-register-screen.md) |
| 45 | Savings | New Account | नवीन खाते | `savings.new-account` | AR | NR | AR | [new-savings-account-screen.md](../../05-ui-ux/savings/new-savings-account-screen.md) |
| 46 | Settings / Accounting | GL Account Setup | जी.एल. खाते सेटअप | `settings.gl-account-setup` | NR | NR | AR | [gl-account-setup-screen.md](../../05-ui-ux/settings/accounting/gl-account-setup-screen.md) |
| 47 | Settings / Loan | Interest Rate Change | व्याज दरात बदल | `settings.loan-interest-rate-change` | NR | NR | AR | [loan-interest-rate-change-screen.md](../../05-ui-ux/settings/loan/loan-interest-rate-change-screen.md) |
| 48 | Settings / Master | Staff & System Access | कर्मचारी व सिस्टम प्रवेश | `settings.staff-system-access` | NR | NR | AR | [staff-system-access-screen.md](../../05-ui-ux/settings/master/staff-system-access-screen.md) |
| 49 | Settings / Master | User Role | युजर रोल | `settings.user-role` | NR | NR | AR | [user-role-screen.md](../../05-ui-ux/settings/master/user-role-screen.md) |
| 50 | Settings / Membership | Membership Configuration | सभासदत्व सेटिंग्ज | `settings.membership-configuration` | NR | NR | AR | [membership-configuration-screen.md](../../05-ui-ux/settings/membership/membership-configuration-screen.md) |
| 51 | Settings / Schemes | New Scheme | नवीन योजना | `settings.new-scheme` | NR | NR | AR | [new-scheme-screen.md](../../05-ui-ux/settings/schemes/new-scheme-screen.md) |

## Counts by permission (seed)

| Role | AR | VO | NR |
| :--- | ---: | ---: | ---: |
| Clerk | 33 | 10 | 8 |
| Cashier | 6 | 16 | 29 |
| Manager | 51 | 0 | 0 |

## Seed script expectations (downstream)

When implementing tenant DB bootstrap (Phase 2/3):

1. Insert three `role` rows (`clerk`, `cashier`, `manager`).
2. Insert 51 `role_permission` rows per role (153 total) using `form_code` + permission level.
3. Menu registry must register the same 51 `form_code` values ([BR-015](business-rules.md#br-015--permission-grid-loaded-from-menu-registry)).
4. Do **not** invent extra forms in seed that are not in this table; add forms here first when UI specs gain a new current screen.

## Open confirmation

| Topic | Status |
| :--- | :--- |
| Matrix values above | **Proposed** — bank may adjust before first tenant go-live; reply with cell changes if needed |
| Additional seed roles (e.g. Director view-only) | Not in Year-1 seed unless requested |

## Related Documents

- [business-rules.md](business-rules.md) — BR-015, BR-017, BR-020
- [overview.md](overview.md)
- [tenant-setup.md](../../../00-project-overview/tenant-setup.md)
- [../../05-ui-ux/settings/master/user-role-screen.md](../../05-ui-ux/settings/master/user-role-screen.md)
- [../../../AI_INDEX.md](../../../AI_INDEX.md)
