# Folder Structure — CBS SaaS Platform

## Purpose

Defines the repository and module layout for frontend, backend, documentation, and AI skills so agents scaffold code consistently across Phase 2 and beyond.

## Scope

- Top-level **monorepo** layout (`/frontend`, `/backend`, `/documentation`) — **DEC-007**.
- Workspace tooling (pnpm workspaces).
- Angular `src/app/` structure.
- NestJS module structure.
- Documentation folder (fixed location — do not relocate).
- Cursor Agent Skills layout (`.cursor/skills/` + `.cursor/rules/`).

## Dependencies

- [technology-stack.md](technology-stack.md) — frameworks and pnpm workspace tooling
- [naming-conventions.md](naming-conventions.md) — file and folder naming
- [../01-architecture/architecture-overview.md](../01-architecture/architecture-overview.md) — DEC-001 tenant routing, DEC-007 monorepo
- [../Software-Documentation-Standard.md](../Software-Documentation-Standard.md) — documentation tree
- [changelog.md](changelog.md)

---

## Content

### Repository layout decision (DEC-007)

| Field | Value |
| :--- | :--- |
| Decision | **Monorepo** — single git repository with `/frontend`, `/backend`, `/documentation` |
| Date | 2026-07-22 |
| Options rejected | Two separate repos (`cbs-frontend` + `cbs-backend`) — cross-repo changes and doc drift outweigh independent deploy cycles at pilot scale |
| Rationale | One PR for cross-cutting changes (UI + API + docs); shared CI; documentation stays versioned with code; small team |
| Trade-off accepted | Larger clone; requires workspace tooling (pnpm) |
| Full decision record | [architecture-overview.md § DEC-007](../01-architecture/architecture-overview.md) |

**Workspace tooling:** pnpm workspaces (see [technology-stack.md](technology-stack.md)). Root `package.json`:

```json
{
  "name": "cbs",
  "private": true,
  "packageManager": "pnpm@9.x",
  "scripts": {
    "frontend": "pnpm --filter frontend",
    "backend": "pnpm --filter backend"
  }
}
```

Each workspace (`frontend/`, `backend/`) has its own `package.json`. Shared dev tooling (Prettier, ESLint config) lives at repo root.

---

### Monorepo layout (canonical)

**Current state (Phase 1 — documentation only):** `frontend/` and `backend/` do not exist yet. Phase 2 scaffold adds them per tree below.

```text
cbs/                              ← monorepo root (single git repository)
├── .cursor/
│   ├── rules/                    ← glob-triggered rule delegators (*.mdc)
│   └── skills/                   ← Agent Skills (SKILL.md per skill)
├── .github/
│   └── workflows/                ← CI/CD (Phase 2)
├── documentation/                ← all project docs (DO NOT relocate)
│   ├── AI_INDEX.md
│   ├── 00-project-overview/
│   ├── 01-architecture/
│   ├── 04-database-design/
│   ├── 05-ui-ux/
│   └── 09-ai-context/
├── frontend/                     ← Angular SPA (Phase 2)
│   ├── angular.json
│   ├── package.json
│   ├── public/
│   │   └── i18n/
│   │       ├── mr.json
│   │       └── en.json
│   └── src/
│       ├── app/
│       │   ├── core/             ← singleton services, guards, interceptors
│       │   │   ├── auth/
│       │   │   ├── permission/
│       │   │   └── api/
│       │   ├── shared/           ← reusable components, directives, pipes
│       │   │   ├── components/
│       │   │   │   ├── data-grid/
│       │   │   │   ├── entity-autocomplete/
│       │   │   │   ├── nominee-form/
│       │   │   │   └── ...
│       │   │   ├── directives/
│       │   │   │   └── has-permission/
│       │   │   └── services/
│       │   │       └── master-data/
│       │   ├── features/         ← one folder per domain/module
│       │   │   ├── customer/
│       │   │   ├── membership/
│       │   │   ├── savings/
│       │   │   ├── settings/
│       │   │   └── ...
│       │   ├── layout/           ← shell, nav, breadcrumb
│       │   ├── app.routes.ts
│       │   └── app.config.ts
│       ├── environments/
│       └── styles/
├── backend/                      ← NestJS API (Phase 2)
│   ├── package.json
│   ├── nest-cli.json
│   └── src/
│       ├── main.ts
│       ├── app.module.ts
│       ├── common/               ← filters, pipes, decorators, base DTOs
│       ├── tenant/               ← DEC-001 connection router / pool manager
│       │   ├── tenant.module.ts
│       │   ├── tenant-connection.service.ts
│       │   └── tenant.middleware.ts
│       ├── catalog/                ← control_catalog DB (platform routing)
│       ├── auth/
│       ├── customer/
│       ├── membership/
│       ├── settings/
│       └── ...                   ← one module folder per domain
├── screenshots/                  ← legacy app capture source (pre-code)
├── other/                        ← misc non-doc assets
├── package.json                  ← workspace root
├── pnpm-workspace.yaml
└── .prettierrc                   ← shared formatting (Phase 2)
```

**pnpm workspace file** (`pnpm-workspace.yaml`):

```yaml
packages:
  - 'frontend'
  - 'backend'
```

---

### Angular feature module pattern

Each screen from `05-ui-ux/<domain>/*-screen.md` maps to a feature folder under `frontend/src/app/features/`:

```text
features/<domain>/<screen-name>/
├── <screen-name>.component.ts          ← container (tab shell, NgRx-connected)
├── <screen-name>.component.html
├── <screen-name>.component.scss
├── <screen-name>.routes.ts             ← lazy route
├── tabs/                               ← one presentational component per spec tab
│   ├── basic-info-tab/
│   └── ...
└── state/                              ← NgRx slice (multi-tab wizards only)
    ├── <screen-name>.actions.ts
    ├── <screen-name>.reducer.ts
    ├── <screen-name>.selectors.ts
    └── <screen-name>.effects.ts
```

**List/register screens** (Customer List, Account Register): filter-bar component + shared `app-data-grid` — no NgRx slice unless server state is complex.

---

### NestJS domain module pattern

```text
backend/src/<domain>/
├── <domain>.module.ts
├── <domain>.controller.ts
├── <domain>.service.ts
├── dto/
│   ├── create-<entity>.dto.ts
│   └── update-<entity>.dto.ts
├── entities/                           ← ORM entity definitions (when ORM chosen)
│   └── <entity>.entity.ts
└── repositories/
    └── <entity>.repository.ts
```

**Tenant context:** Every controller/service that touches tenant financial data receives the tenant-scoped connection from `TenantConnectionService` — never hardcode a database name.

**Control catalog:** Separate `catalog/` module for platform routing DB — not mixed with tenant domain modules.

---

### Documentation folder (fixed — do not change)

Per [Software-Documentation-Standard.md](../Software-Documentation-Standard.md), documentation stays at repo root `documentation/` — never moved into `frontend/` or `backend/`:

```text
documentation/
├── AI_INDEX.md
├── 00-project-overview/
├── 01-architecture/
├── 02-business-domains/          ← not started
├── 03-api-contracts/             ← not started
├── 04-database-design/
├── 05-ui-ux/
├── 06-non-functional/            ← not started
├── 07-compliance/                ← not started
├── 08-testing/                   ← not started
└── 09-ai-context/
```

| Artifact type | Path pattern |
| :--- | :--- |
| Screen specs | `documentation/05-ui-ux/<domain>/<screen-name>-screen.md` |
| Mockups | `documentation/05-ui-ux/mockups/<domain>/<screen-name>/` |
| API contracts (future) | `documentation/03-api-contracts/<domain>/METHOD-verb-noun.md` |
| DB entities | `documentation/04-database-design/<domain>/<entity>.md` |

---

### Agent Skills layout (Cursor — Agent Skills open standard)

```text
.cursor/
├── rules/
│   ├── generate-document.mdc
│   ├── generate-ui-screen.mdc
│   ├── generate-ui-mockup.mdc
│   ├── design-database-schema.mdc
│   ├── optimize-ui-ux.mdc
│   └── coding-standards.mdc        ← auto-loads on *.ts/*.html/*.scss edits
└── skills/
    ├── design-database-schema/
    │   └── SKILL.md
    └── optimize-ui-ux/
        └── SKILL.md
```

Skills follow the [Agent Skills open standard](https://agentskills.io): each skill is a folder with required `SKILL.md` (`name` + `description` frontmatter) and optional `references/`, `scripts/`, `assets/`.

---

## Related Documents

- [technology-stack.md](technology-stack.md)
- [naming-conventions.md](naming-conventions.md)
- [coding-standards.md](coding-standards.md)
- [generation-rules.md](generation-rules.md)
- [changelog.md](changelog.md)
- [../01-architecture/architecture-overview.md](../01-architecture/architecture-overview.md)
- [../cbs-project-execution-plan.md](../cbs-project-execution-plan.md)
- [../Software-Documentation-Standard.md](../Software-Documentation-Standard.md)
