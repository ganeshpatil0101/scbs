# Naming Conventions — CBS SaaS Platform

## Purpose

Single canonical reference for file, folder, variable, API, database, and documentation identifier naming. AI agents must not invent alternate conventions per screen or module.

## Scope

- Documentation files and IDs (`BR-`, `UC-`, `AT-`).
- Database tables and columns (summary — full rules in database-design-standards.md).
- Angular and NestJS source code.
- API contract file naming (future `03-api-contracts/`).

## Dependencies

- [../04-database-design/database-design-standards.md](../04-database-design/database-design-standards.md) — DB naming authority
- [../Software-Documentation-Standard.md](../Software-Documentation-Standard.md) — doc file naming
- [folder-structure.md](folder-structure.md) — where names are applied

---

## Content

### Documentation files

| Element | Convention | Example |
| :--- | :--- | :--- |
| Markdown files | `lowercase-with-hyphens.md` | `business-rules.md`, `new-customer-screen.md` |
| Screen specs | `<screen-name>-screen.md` | `deposit-account-transaction-screen.md` |
| API contract files | `METHOD-verb-noun.md` | `POST-create-customer.md`, `GET-account-details.md` |
| DB entity files | `<entity>.md` (singular) | `customer.md`, `gl_transaction.md` |
| Avoid | PascalCase, spaces, `Final`, version suffixes | ~~`AccountOverviewFinal.md`~~ |

### Documentation identifiers

| Type | Format | Rules |
| :--- | :--- | :--- |
| Business rules | `BR-001`, `BR-002`, … | Sequential; never reuse — deprecate instead |
| Use cases | `UC-001`, … | Sequential |
| Acceptance tests | `AT-001`, … | Must reference `UC-NNN` / `BR-NNN` verified |
| Architecture decisions | `DEC-001`, … | Recorded in architecture-overview.md |
| Business goals | `BG-001`, … | Recorded in business-goals.md |
| Non-functional | `SEC-001`, `PERF-001`, … | Per domain prefix |

### Database naming

**Canonical source:** [database-design-standards.md](../04-database-design/database-design-standards.md). Summary:

| Element | Convention | Example |
| :--- | :--- | :--- |
| Table | Singular `snake_case` | `customer`, `loan_account`, `gl_transaction` |
| Primary key | Always `id` | `bigint generated always as identity` |
| Foreign key | `<referenced_entity>_id` | `customer_id`, `gl_head_id` |
| Boolean | `is_<flag>` | `is_active`, `is_contra` |
| Business numbers | Separate column, not PK | `customer_no`, `account_no`, `voucher_no` |
| Timestamps | `created_at`, `updated_at` | `timestamptz` |
| Audit users | `created_by`, `updated_by` | FK → `user.id` |
| Enum values (stored) | English `snake_case` in CHECK | `'individual'`, `'proprietorship_firm'` |
| Index | `idx_<table>_<columns>` | `idx_gl_transaction_gl_head_id_txn_date` |

**Never:** `tenant_id` in tenant-DB tables (DEC-001). **Never:** `float`/`double` for money.

### Angular naming

| Element | Convention | Example |
| :--- | :--- | :--- |
| File names | `kebab-case` + type suffix | `new-customer.component.ts`, `customer.service.ts` |
| Component selector | `app-<kebab-case>` | `app-new-customer`, `app-data-grid` |
| Shared components | `app-` prefix under `shared/components/` | `app-entity-autocomplete` |
| Directives | `app` prefix, camelCase export | `appHasPermission` |
| Services | `<name>.service.ts`, `@Injectable({ providedIn: 'root' })` for singletons | `permission.service.ts` |
| NgRx files | `<feature>.actions.ts`, `.reducer.ts`, `.selectors.ts`, `.effects.ts` | `new-customer.actions.ts` |
| Routes | `<feature>.routes.ts` | `customer.routes.ts` |
| i18n keys | dot-separated, domain-scoped | `customer.new.tab1.firstName` |
| Interfaces / types | PascalCase | `CustomerType`, `PermissionLevel` |
| Enums (TS) | PascalCase name, PascalCase or string members matching spec | `CustomerType.Individual` |

### NestJS naming

| Element | Convention | Example |
| :--- | :--- | :--- |
| Module | `<domain>.module.ts` | `customer.module.ts` |
| Controller | `<domain>.controller.ts` | `customer.controller.ts` |
| Service | `<domain>.service.ts` | `customer.service.ts` |
| Repository | `<entity>.repository.ts` | `customer.repository.ts` |
| DTO | `<action>-<entity>.dto.ts` | `create-customer.dto.ts` |
| Entity (ORM) | `<entity>.entity.ts` | `customer.entity.ts` |
| Route paths | `kebab-case`, plural resources | `/customers`, `/loan-accounts` |
| Route params | `:id`, `:customerNo` (camelCase for business numbers) | `/customers/:id` |

### API naming (REST — future `03-api-contracts/`)

| Element | Convention | Example |
| :--- | :--- | :--- |
| Base path | `/api/v1/<resource>` | `/api/v1/customers` |
| HTTP methods | Standard REST verbs | GET list/detail, POST create, PUT/PATCH update |
| Query params | `camelCase` | `?branchId=1&status=active` |
| Request/response body | `camelCase` JSON | `{ "customerNo": "1001", "firstName": "..." }` |
| Error codes | Domain-prefixed string | `CUSTOMER_NOT_FOUND`, `VALIDATION_FAILED` |

JSON uses `camelCase`; database uses `snake_case` — map in DTO/entity layer.

### Git conventions (Phase 2)

| Element | Convention | Example |
| :--- | :--- | :--- |
| Branch | `feature/<ticket>-<short-desc>` | `feature/auth-login-screen` |
| Commit | Conventional Commits | `feat(customer): add new customer wizard tab 1` |

---

## Related Documents

- [../04-database-design/database-design-standards.md](../04-database-design/database-design-standards.md)
- [coding-standards.md](coding-standards.md)
- [folder-structure.md](folder-structure.md) — monorepo paths (DEC-007)
- [changelog.md](changelog.md)
- [../01-architecture/architecture-overview.md](../01-architecture/architecture-overview.md)
- [../Software-Documentation-Standard.md](../Software-Documentation-Standard.md)
- [../05-ui-ux/shared/entity-autocomplete-pattern.md](../05-ui-ux/shared/entity-autocomplete-pattern.md)
