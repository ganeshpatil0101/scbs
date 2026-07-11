# Changelog — Investment Screens

| Version | Date | Changes | Reason | Author |
| :--- | :--- | :--- | :--- | :--- |
| 1.0.0 | 2026-07-05 | Bank Deposit module — 6 screen specs | New screenshots in `screenshots/गुंतवणूक/` | AI Agent |
| 1.1.0 | 2026-07-11 | UX optimization: 6 → 4 screens | Consolidate bank master + interest screens; Autocomplete, Auto-fill, Advanced patterns | AI Agent |
| 1.2.0 | 2026-07-11 | HTML mockups (Draft) for 4 optimized screens | Bank-user layout review via `@generate-ui-mockup` | AI Agent |

## 1.1.0 Detail (2026-07-11)

### Consolidations

| Action | Old specs | New spec |
| :--- | :--- | :--- |
| Consolidate | `bank-deposit-new-bank-screen.md`, `bank-deposit-bank-list-screen.md` | `bank-deposit-bank-management-screen.md` |
| Consolidate | `bank-deposit-interest-assessment-screen.md`, `bank-deposit-interest-provision-screen.md` | `bank-deposit-interest-management-screen.md` |

### Field changes

| Screen | Changes |
| :--- | :--- |
| New Account | Bank GL pair → Autocomplete; Auto-fill account no., maturity, status; `खाते` → `खाते नाव`; Advanced section for receipt/interest type/fund |
| Transaction | Branch/GL/Account Autocomplete; Account Summary Panel; cheque tab conditional visibility; `app-ledger-tab` reference |
| Interest Management | Branch/Bank Autocomplete; remove ambiguous `खाते` filter; shared filter/grid across tabs |

### New documents

- [ux-optimization.md](ux-optimization.md) — audit summary and action checklist

### Superseded (retained)

- `bank-deposit-new-bank-screen.md`
- `bank-deposit-bank-list-screen.md`
- `bank-deposit-interest-assessment-screen.md`
- `bank-deposit-interest-provision-screen.md`

## 1.2.0 Detail (2026-07-11)

### Mockups (Draft)

| Screen | Path |
| :--- | :--- |
| बँक ठेव बँक व्यवस्थापन | [../mockups/investment/bank-deposit-bank-management-screen/](../mockups/investment/bank-deposit-bank-management-screen/) |
| नवीन खाते | [../mockups/investment/bank-deposit-new-account-screen/](../mockups/investment/bank-deposit-new-account-screen/) |
| व्यवहार | [../mockups/investment/bank-deposit-transaction-screen/](../mockups/investment/bank-deposit-transaction-screen/) |
| व्याज व्यवस्थापन | [../mockups/investment/bank-deposit-interest-management-screen/](../mockups/investment/bank-deposit-interest-management-screen/) |

Superseded specs were not mockuped.
