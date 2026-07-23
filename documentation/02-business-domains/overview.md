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
| Customer | `customer/` | Not started | Next full domain after Settings |
| Membership (operational) | `membership/` | Not started | Phase 3 |
| Savings, FD, Daily, Recurring, Loan, Accounting | respective folders | Not started | Phase 3 |

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
6. Customer (next)
7. Phase 3 operational domains per [cbs-project-execution-plan.md](../cbs-project-execution-plan.md)
3. Customer
4. Phase 3 operational domains per [cbs-project-execution-plan.md](../cbs-project-execution-plan.md)

## Related Documents

- [settings/overview.md](settings/overview.md)
- [../00-project-overview/tenant-setup.md](../00-project-overview/tenant-setup.md) — New tenant bootstrap checklist
- [../cbs-project-execution-plan.md](../cbs-project-execution-plan.md)
- [../AI_INDEX.md](../AI_INDEX.md)
- [../Software-Documentation-Standard.md](../Software-Documentation-Standard.md)
- [../09-ai-context/generation-rules.md](../09-ai-context/generation-rules.md)
