# Business Domains — Overview

## Purpose

Master index for all `02-business-domains/` documentation. Each domain folder contains business rules, use cases, workflows, and acceptance tests derived from `05-ui-ux/` screen specs via `@generate-business-domain`.

## Scope

Covers operational and configuration domains for the CBS SaaS platform. Does not duplicate glossary definitions ([glossary.md](../00-project-overview/glossary.md)) or UI field tables ([05-ui-ux/](../05-ui-ux/)).

## Documentation Status

| Domain | Path | Status | Notes |
| :--- | :--- | :---: | :--- |
| Settings — Master | [settings/master/](settings/master/overview.md) | Done (2026-07-23) | Phase 1.7 template sub-area |
| Settings — Accounting | [settings/accounting/](settings/accounting/overview.md) | Done (2026-07-23) | GL Account Setup (22 BR, 2 UC, 2 WF, 25 AT) |
| Settings — Schemes | [settings/schemes/](settings/schemes/overview.md) | Done (2026-07-23) | Unified New Scheme (34 BR, 2 UC, 2 WF, 35 AT) |
| Settings — Membership | [settings/membership/](settings/membership/overview.md) | Done (2026-07-23) | Membership Configuration (15 BR, 2 UC, 2 WF, 15 AT) |
| Settings — Loan | [settings/loan/](settings/loan/overview.md) | Done (2026-07-23) | Interest Rate Change (14 BR, 1 UC, 1 WF, 14 AT) |
| Customer | [customer/](customer/overview.md) | Done (2026-07-24) | Customer List, New Customer, Other Account Management (33 BR, 4 UC, 4 WF, 33 AT) |
| Savings | [savings/](savings/overview.md) | Done (2026-07-24) | New Account, Account Register (26 BR, 2 UC, 2 WF, 26 AT); superseded Transaction/Manual Interest excluded (deferred to Accounting) |
| Fixed Deposit | [fixed-deposit/](fixed-deposit/overview.md) | Done (2026-07-24) | New Account, Account Management, Deposit Loan Installment, Interest Multiplier (43 BR, 4 UC, 4 WF, 43 AT); superseded Transaction/Manual Interest/Register/Renewal excluded |
| Daily (Pigmy) | [daily/](daily/overview.md) | Done (2026-07-24) | New Account, New Agent, Account Register, Agent Collection Management, Agent-to-Agent Transfer, Interest Multiplier (45 BR, 6 UC, 7 WF, 45 AT); superseded Transaction/Manual Interest/old Agent Collection excluded |
| Recurring | [recurring/](recurring/overview.md) | Done (2026-07-24) | New Account, Account Register, Interest Multiplier (34 BR, 3 UC, 3 WF, 34 AT); superseded Transaction/Credit/Manual Interest excluded (deferred to Accounting) |
| Membership (operational) | `membership/` | Not started | Phase 3 |
| Loan, Accounting | respective folders | Not started | Phase 3 |

## Standard File Set (per leaf domain)

Each documented sub-area or domain includes:

```text
overview.md
business-rules.md    # BR-001… (scoped per folder)
use-cases.md         # UC-001…
workflows.md
acceptance-tests.md  # AT-001…
changelog.md
```

## Build Order (Phase 1.7)

1. Settings/Master (template) — **done**
2. Settings/Schemes — **done**
3. Settings/Accounting — **done**
4. Settings/Membership — **done**
5. Settings/Loan — **done**
6. Customer — **done**
7. Savings — **done**
8. Fixed Deposit — **done**
9. Daily (Pigmy) — **done**
10. Recurring — **done**
11. Phase 3 operational domains (Membership, Loan, Accounting) per [cbs-project-execution-plan.md](../cbs-project-execution-plan.md)

## Related Documents

- [settings/overview.md](settings/overview.md)
- [../00-project-overview/tenant-setup.md](../00-project-overview/tenant-setup.md) — New tenant bootstrap checklist
- [../cbs-project-execution-plan.md](../cbs-project-execution-plan.md)
- [../AI_INDEX.md](../AI_INDEX.md)
- [../Software-Documentation-Standard.md](../Software-Documentation-Standard.md)
- [../09-ai-context/generation-rules.md](../09-ai-context/generation-rules.md)
