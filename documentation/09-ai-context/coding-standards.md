# Coding Standards — CBS SaaS Platform

## Purpose

Canonical coding conventions for Angular frontend and NestJS backend. All code-generation skills (`@generate-ui-screen`, future backend skills) and the `coding-standards.mdc` rule delegate here.

## Scope

- TypeScript style, Angular patterns, NestJS patterns.
- Testing expectations.
- Accessibility and responsive requirements.
- Does **not** define business rules — those live in `02-business-domains/` (not started).

## Dependencies

- [technology-stack.md](technology-stack.md) — pinned versions
- [naming-conventions.md](naming-conventions.md) — file and symbol naming
- [folder-structure.md](folder-structure.md) — monorepo module layout (DEC-007)
- [../04-database-design/database-design-standards.md](../04-database-design/database-design-standards.md) — DB types and constraints
- [../05-ui-ux/shared/ui-simplification-patterns.md](../05-ui-ux/shared/ui-simplification-patterns.md) — UI behavior
- [../05-ui-ux/shared/entity-autocomplete-pattern.md](../05-ui-ux/shared/entity-autocomplete-pattern.md) — lookup fields

---

## Content

### General TypeScript rules

- **Strict mode** enabled (`strict: true` in `tsconfig.json`).
- Prefer `interface` for object shapes; `type` for unions/intersections.
- No `any` — use `unknown` and narrow, or typed DTOs.
- Async: prefer `async/await` over raw Promise chains.
- One public class/export per file for components, services, controllers.
- Max function length ~50 lines — extract helpers when exceeded.

### Angular standards

#### Component model

- **Standalone components only** — no NgModules.
- Container vs presentational split for multi-tab wizards (see [folder-structure.md](folder-structure.md)).
- Use `ChangeDetectionStrategy.OnPush` on presentational components where inputs are immutable.

#### Forms

- **Reactive Forms only** — never template-driven (`ngModel` on business forms).
- One `FormGroup` per tab; register into parent or NgRx-held form value.
- Validators from spec `Required` column:

| Spec | Validator |
| :--- | :--- |
| `Required: Yes` | `Validators.required` |
| Numeric amount/rate fields | `Validators.pattern` + `min(0)` unless spec says otherwise |
| Dropdown with listed values | Typed const array — no magic strings in template |
| `Disabled until X checked` | `valueChanges` → `enable()`/`disable()` on dependents |
| Read-only / auto-generated | Plain text or disabled control — never editable styled as disabled |

#### State management

- **NgRx:** one feature slice per multi-tab wizard screen (`state/<screen-name>/`).
- **Signals:** local UI only — tab index, accordion open, hover, loading flags.
- **Do not** put grid pagination/sort in NgRx — stays in `app-data-grid` component.
- Grid server state: parameters via `@Input()`, events via `@Output()`.

#### UI library and i18n

- **Angular Material** for all form controls, tables, tabs, dialogs.
- **ngx-translate** for every user-facing string — both `mr` and `en` keys.
- Never hardcode Marathi or English in templates.
- Theme: Material CSS variables only — no hardcoded hex colors.

#### UI simplification (mandatory)

Implement [ui-simplification-patterns.md](../05-ui-ux/shared/ui-simplification-patterns.md):

- **Advanced Settings:** `mat-expansion-panel` collapsed by default.
- **Conditional fields:** `*ngIf` visibility — not disabled mystery fields.
- **Autocomplete:** single control per Branch/GL/Account/Customer/Member/Agent — per [entity-autocomplete-pattern.md](../05-ui-ux/shared/entity-autocomplete-pattern.md).
- **Auto-fill fields:** read-only labels.

#### Role-based rendering

Per User Role screen spec — three levels:

| Level | Rule |
| :--- | :--- |
| All Rights | Full form, all actions enabled |
| View Only | All fields read-only; Save/Add/Post buttons **hidden** (not just disabled) |
| No Rights | Route guard blocks navigation entirely |

Use shared `*appHasPermission="'formCode'"` directive + `PermissionService`.

#### Responsive and accessibility

| Breakpoint | Rule |
| :--- | :--- |
| `< 600px` | Single column; grids → card list; tabs → `mat-select` step picker |
| `600–959px` | Two-column sections; horizontal scroll grids with sticky first column |
| `≥ 960px` | Full multi-column layout per spec grouping |

Use CDK `BreakpointObserver` — no hand-rolled media queries per component.

Non-negotiable:

- Visible keyboard focus on all interactive elements.
- Every control has `mat-label` or `aria-label` — not placeholder-only.
- Submit errors announced via `aria-live`.
- Sticky action bar on mobile for Save/Next/Back.

#### TODO scaffold pattern (unresolved spec gaps)

When a spec field/tab is `TODO`:

1. Render the field/tab with known properties.
2. Back dropdowns with placeholder service returning stub data.
3. Comment: `// TODO(spec-gap): <reason> — see <spec-file>`
4. Never invent plausible enum values — cross-check sibling specs first.

#### Reuse before create

Search `frontend/src/app/shared/` before creating new components. Build shared components when a pattern repeats across 2+ screens (data grid, entity autocomplete, nominee form, ledger tab, etc.).

---

### NestJS standards

#### Module structure

- One module per business domain (`customer`, `membership`, `loan`, …).
- `TenantModule` provides tenant-scoped DB connection — inject, never instantiate pools directly in domain services.
- `CatalogModule` for `control_catalog` only — separate from tenant modules.

#### Controllers

- Thin controllers — delegate to services.
- Use DTOs for all request bodies and query params.
- Return consistent response envelope:

```typescript
// Success
{ data: T, meta?: PaginationMeta }

// Error (via exception filter)
{ statusCode: number, message: string, error: string, details?: unknown }
```

#### DTOs and validation

- `class-validator` decorators on all input DTOs.
- `class-transformer` for query param coercion.
- Separate Create/Update DTOs — no single mega-DTO.
- Map DB `snake_case` ↔ JSON `camelCase` in service or entity layer.

#### Services and repositories

- Business logic in services — not controllers.
- Data access in repository classes — not raw queries in services.
- **DEC-001:** All tenant DB access goes through tenant-scoped connection from `TenantConnectionService`.
- Financial calculations use `decimal.js` or DB `numeric` — never JavaScript `number` for money arithmetic.

#### Error handling

- Global `HttpExceptionFilter` for consistent error shape.
- Domain exceptions extend a base `DomainException` with error code enum.
- Never expose stack traces or internal DB errors to client in production.

#### Security

- JWT guard on all routes except `/health` and `/auth/login`.
- Extract `tenant_id` from JWT — pass to connection router.
- Role/permission guard mirrors frontend `*appHasPermission` matrix.
- No secrets in code — AWS Secrets Manager (prod) / SSM (dev).

#### Logging

- Structured JSON logs (NestJS Logger or pino).
- Log tenant_id, user_id, request_id on every authenticated request.
- Never log passwords, tokens, or full PAN/Aadhaar values.

---

### Testing standards

| Layer | Tool | Minimum expectation |
| :--- | :--- | :--- |
| NestJS unit | Jest | Service methods with mocked repository |
| NestJS e2e | Jest + Supertest | Auth flow, one CRUD path per module |
| Angular unit | Jest/Vitest (CLI default) | Form validators, reducers, selectors |
| Angular component | TestBed | Permission directive, autocomplete debounce |
| Acceptance | Reference `AT-NNN` from domain docs | Integration tests when `02-business-domains/` exists |

Test file naming: `<name>.spec.ts` adjacent to source file.

---

### Code review checklist (agents self-check before reporting done)

- [ ] Follows [naming-conventions.md](naming-conventions.md)
- [ ] Follows [folder-structure.md](folder-structure.md) layout
- [ ] Spec is source of truth — every field traces to `05-ui-ux/` row
- [ ] No invented business rules or master data values
- [ ] Both `mr` and `en` i18n keys (frontend)
- [ ] Reactive Forms, standalone components, OnPush where applicable
- [ ] Shared components reused before creating new ones
- [ ] TODO gaps scaffolded, not skipped or guessed
- [ ] Accessibility and responsive breakpoints implemented
- [ ] Tenant routing via DEC-001 pattern (backend)
- [ ] DTO validation on all inputs (backend)
- [ ] No `float` for money; no `tenant_id` in tenant DB entities

---

## Related Documents

- [technology-stack.md](technology-stack.md)
- [naming-conventions.md](naming-conventions.md)
- [folder-structure.md](folder-structure.md) — monorepo module layout (DEC-007)
- [generation-rules.md](generation-rules.md)
- [changelog.md](changelog.md)
- [../05-ui-ux/shared/ui-simplification-patterns.md](../05-ui-ux/shared/ui-simplification-patterns.md)
- [../05-ui-ux/shared/entity-autocomplete-pattern.md](../05-ui-ux/shared/entity-autocomplete-pattern.md)
- [../04-database-design/database-design-standards.md](../04-database-design/database-design-standards.md)
