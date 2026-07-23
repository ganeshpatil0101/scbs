# Tenant Setup Checklist

## Purpose

Single checklist of everything required to **provision a new cooperative-bank tenant** on the CBS SaaS platform. Downstream seed scripts, control-catalog entries, and go-live runbooks must follow this document — do not invent bootstrap steps elsewhere.

Year-1 target: one pilot tenant (BG-001). Each later tenant reuses the same checklist.

## Related standing decisions

| Topic | Decision | Source |
| :--- | :--- | :--- |
| Tenancy | Database-per-tenant; JWT carries `tenant_id` | DEC-001 — [architecture-overview.md](../01-architecture/architecture-overview.md) |
| Login uniqueness | Unique within tenant | [BR-010](../02-business-domains/settings/master/business-rules.md#br-010--login-name-uniqueness) |
| Password policy | Min 8; ≥1 letter + ≥1 digit; no Year-1 history | [BR-011](../02-business-domains/settings/master/business-rules.md#br-011--password-complexity) |
| Super User | All Rights on all forms; branch rights still apply | [BR-012](../02-business-domains/settings/master/business-rules.md#br-012--super-user-permission-bypass) |
| Branch rights | ≥1 required; single-branch HO auto-assigns | [BR-018](../02-business-domains/settings/master/business-rules.md#br-018--minimum-branch-rights-on-save) |
| Default Roles | Clerk / Cashier / Manager seed matrix | [default-role-templates.md](../02-business-domains/settings/master/default-role-templates.md) |

---

## Phase A — Platform / control plane (once per tenant)

| # | Step | Owner | Status / notes |
| :---: | :--- | :--- | :--- |
| A1 | Register tenant in **control catalog** (`tenant_id` → DB name + credentials) | Platform ops | Required before first API call |
| A2 | Create empty **PostgreSQL database** for the tenant on shared RDS | Platform ops | DEC-001 |
| A3 | Run schema migrations (all modules) against the new DB | Platform ops | After `04-database-design/` entities exist |
| A4 | Register menu / form codes in **application menu registry** (same 51 `form_code` values as role seed) | Platform / deploy | Must match [default-role-templates.md](../02-business-domains/settings/master/default-role-templates.md) |

---

## Phase B — Tenant master seed (required before staff login)

| # | Step | Data / rule | Doc status |
| :---: | :--- | :--- | :---: |
| B1 | **Organization** (society) | At least one Organization name for the bank | TODO — shared entity (`@design-database-schema shared`) |
| B2 | **Branch** | At least one Branch (Year-1 often Head Office only). Single-branch tenants auto-assign this branch on Staff Tab 3 ([BR-018](../02-business-domains/settings/master/business-rules.md#br-018--minimum-branch-rights-on-save)) | TODO — shared entity |
| B3 | **Default Roles** | Seed Clerk, Cashier, Manager + 51 permissions each | [default-role-templates.md](../02-business-domains/settings/master/default-role-templates.md) |
| B4 | **Initial admin User** | Create Customer → Employee → User with Super User = Yes, Role = Manager, ≥1 branch right, password meeting [BR-011](../02-business-domains/settings/master/business-rules.md#br-011--password-complexity) | [settings/master](../02-business-domains/settings/master/overview.md) |
| B5 | Verify admin can log in and open Staff & System Access + User Role | Smoke test | After B4 |

---

## Phase C — Product & accounting configuration (before operations)

Complete via Settings UI (or seed scripts once contracts exist). Order below is recommended.

| # | Step | UI / domain | Doc status |
| :---: | :--- | :--- | :---: |
| C1 | **GL Account Setup** (chart of accounts / GL groups & heads) | Settings → Accounting | UI done; business domain TODO |
| C2 | **Product schemes** (Savings, FD, Daily, Recurring, Loan as needed) | Settings → Schemes → New Scheme | UI done; business domain TODO |
| C3 | **Membership configuration** + share rules | Settings → Membership | UI done; business domain TODO |
| C4 | **Loan interest rate** baseline (if loans in scope for go-live) | Settings → Loan → Interest Rate Change | UI done; business domain TODO |
| C5 | Optional: Bank master rows for cheque/investment flows | Bank module | UI done |

---

## Phase D — Operational readiness

| # | Step | Notes |
| :---: | :--- | :--- |
| D1 | Register remaining staff (Clerk / Cashier / Manager users) via Staff & System Access | Assign seeded Roles ([BR-020](../02-business-domains/settings/master/business-rules.md#br-020--staff-access-assigns-existing-role)) |
| D2 | Confirm maker–checker path: Clerk posts → Manager verifies/passes | Aligns with seed matrix |
| D3 | Confirm Cashier Rokhapal / note exchange path | Seed Cashier AR on cash forms |
| D4 | Customer + Membership pilot records | After Customer / Membership domain docs + code |
| D5 | Day-1 reconciliation / opening balances | Accounting ops — process TBD in accounting domain |

---

## Out of scope for this checklist

- SMS / WhatsApp / payment gateway (see [system-boundaries.md](system-boundaries.md))
- Cross-tenant data copy
- Automated migration from incumbent CBS (Phase 5 of execution plan)

---

## Document maintenance

When a new **current** UI screen is added under `05-ui-ux/`:

1. Add a row to [default-role-templates.md](../02-business-domains/settings/master/default-role-templates.md) for Clerk / Cashier / Manager.
2. Update menu-registry seed and `role_permission` seed counts.
3. Note the change in this file’s related changelog or Settings/Master changelog.

---

## Related Documents

- [vision.md](vision.md)
- [business-goals.md](business-goals.md) — BG-001 Year-1 tenant
- [glossary.md](glossary.md) — Tenant, Branch, Organization, Role
- [system-boundaries.md](system-boundaries.md)
- [../01-architecture/architecture-overview.md](../01-architecture/architecture-overview.md) — DEC-001
- [../02-business-domains/settings/master/overview.md](../02-business-domains/settings/master/overview.md)
- [../02-business-domains/settings/master/default-role-templates.md](../02-business-domains/settings/master/default-role-templates.md)
- [../02-business-domains/settings/master/business-rules.md](../02-business-domains/settings/master/business-rules.md)
- [../cbs-project-execution-plan.md](../cbs-project-execution-plan.md)
- [../AI_INDEX.md](../AI_INDEX.md)
