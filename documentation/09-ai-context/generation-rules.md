# Generation Rules — CBS SaaS Platform

## Purpose

Meta-document defining how AI agents (Cursor, Claude, etc.) must read project documentation, invoke Agent Skills, and scaffold code or docs consistently. Unblocks Phase 2 code generation per [cbs-project-execution-plan.md](../cbs-project-execution-plan.md) §1.3.

## Scope

- Mandatory read order before any generation task.
- Agent Skills system layout and progressive disclosure model.
- Skill selection guide (which skill for which task).
- Non-negotiable generation constraints.
- Template for authoring future skills (e.g. `generate-nestjs-module` at Phase 2).

## Dependencies

- [coding-standards.md](coding-standards.md)
- [naming-conventions.md](naming-conventions.md)
- [folder-structure.md](folder-structure.md)
- [technology-stack.md](technology-stack.md)
- [../AI_INDEX.md](../AI_INDEX.md)
- [../Software-Documentation-Standard.md](../Software-Documentation-Standard.md)

---

## Content

### Agent Skills system (this project)

This project implements the open [Agent Skills standard](https://agentskills.io) ([specification](https://agentskills.io/specification), [GitHub repo](https://github.com/agentskills/agentskills)) via Cursor:

```text
.cursor/
├── skills/<skill-name>/SKILL.md    ← Required: name + description frontmatter + workflow
└── rules/<skill-name>.mdc          ← Optional: glob-triggered delegator to SKILL.md
```

**Progressive disclosure** (per standard):

1. **Discovery** — agent loads skill `name` + `description` at startup.
2. **Activation** — when task matches description, agent reads full `SKILL.md`.
3. **Execution** — agent follows workflow; loads referenced docs (`09-ai-context/`, domain specs) as needed.

Skills must stay under ~500 lines in `SKILL.md`; put detailed reference material in linked docs under `documentation/`.

### Mandatory read order

Before generating **any** code or documentation, read in this order — **never skip**:

| Step | Document | Why |
| :---: | :--- | :--- |
| 1 | [AI_INDEX.md](../AI_INDEX.md) | Module index and current status |
| 2 | [vision.md](../00-project-overview/vision.md) | Problem statement and scope |
| 3 | [glossary.md](../00-project-overview/glossary.md) | Term definitions — never redefine |
| 4 | [architecture-overview.md](../01-architecture/architecture-overview.md) | DEC-001–006, infra, tenant routing |
| 5 | Relevant domain docs | `05-ui-ux/<domain>/`, `04-database-design/<domain>/`, `02-business-domains/` when exists |
| 6 | [coding-standards.md](coding-standards.md) | How to write code |
| 7 | [naming-conventions.md](naming-conventions.md) | Names for files, APIs, DB, IDs |
| 8 | [folder-structure.md](folder-structure.md) | Where files go |
| 9 | [generation-rules.md](generation-rules.md) | This document |
| 10 | Target skill `SKILL.md` or rule `.mdc` | Task-specific workflow |

For UI screen implementation, also read the target `*-screen.md`, domain `overview.md`, `ux-optimization.md`, and approved mockup if Status = **Approved**.

For database design, also read [database-design-standards.md](../04-database-design/database-design-standards.md) and [reports-traceability.md](../04-database-design/reports-traceability.md).

### Skill selection guide

| Task | Invoke | Rule / Skill path |
| :--- | :--- | :--- |
| Author/update modular docs (business rules, use cases, architecture) | `@generate-document` | [.cursor/rules/generate-document.mdc](../../.cursor/rules/generate-document.mdc) |
| HTML layout mockup from screen spec | `@generate-ui-mockup` | [.cursor/rules/generate-ui-mockup.mdc](../../.cursor/rules/generate-ui-mockup.mdc) |
| Angular screen from approved spec/mockup | `@generate-ui-screen` | [.cursor/rules/generate-ui-screen.mdc](../../.cursor/rules/generate-ui-screen.mdc) |
| Database entity docs from UI specs | `@design-database-schema` | [.cursor/skills/design-database-schema/SKILL.md](../../.cursor/skills/design-database-schema/SKILL.md) |
| UX simplification / screen consolidation | `@optimize-ui-ux` | [.cursor/skills/optimize-ui-ux/SKILL.md](../../.cursor/skills/optimize-ui-ux/SKILL.md) |
| Any TypeScript/HTML/SCSS edit (standards enforcement) | Auto via glob | [.cursor/rules/coding-standards.mdc](../../.cursor/rules/coding-standards.mdc) |
| NestJS module from API contract | `@generate-nestjs-module` | **Not yet created** — Phase 2; use template below |

### Non-negotiable generation constraints

1. **Never invent business rules** — insert `TODO:` and ask via `AskQuestion` (max 1–2 questions per turn).
2. **Never create undocumented entities** — every DB table/API endpoint traces to a spec or explicit user answer.
3. **Never generate APIs without related use cases** — when `02-business-domains/` exists.
4. **Never generate database tables without business ownership** — cite spec field `#` or report column.
5. **Never generate code before reading documentation** — follow read order above.
6. **Never duplicate definitions** — reuse glossary and shared entities.
7. **Always reference glossary terms** consistently.
8. **Always maintain cross-links** — every doc ends with `## Related Documents`.
9. **Always update changelog** when modifying domain documentation.
10. **Spec is source of truth** for UI — mockup wins on layout only when Status = **Approved**; spec wins on field presence/required-ness.

### TODO scaffold pattern

When documentation or specs have unresolved gaps:

| Context | Action |
| :--- | :--- |
| Documentation | `TODO: <question>` inline — ask user before inventing |
| UI spec dropdown values | Placeholder service stub in code; `// TODO(spec-gap): ...` comment |
| Entire uncaptured tab | Tab shell with "Coming soon" state — navigation count must match spec |
| DB entity field | `TODO:` in entity doc Source column |

### Document size limits

Per [Software-Documentation-Standard.md](../Software-Documentation-Standard.md):

- Preferred: 200–500 lines per file
- Hard max: 700 lines — split into `-part2.md` and cross-link

### Authoring a new skill (template)

When creating skills for Phase 2+ (e.g. `generate-nestjs-module`):

```text
.cursor/skills/<skill-name>/
├── SKILL.md              ← Required
├── references/           ← Optional: link to 09-ai-context/, API contracts
└── scripts/              ← Optional: validation scripts
```

**SKILL.md frontmatter (required):**

```yaml
---
name: <skill-name>          # max 64 chars, lowercase-hyphens
description: >              # max 1024 chars, third person, WHAT + WHEN
  <What it does>. Use when <trigger scenarios>.
---
```

**SKILL.md body sections:**

1. When to Use
2. Non-Negotiable Principles (table)
3. Read Order (must include `09-ai-context/` files)
4. Execution Workflow (numbered steps)
5. Deliverables Checklist
6. Pre-Completion Checklist
7. Related Documents

**Companion rule (optional):**

```yaml
# .cursor/rules/<skill-name>.mdc
---
description: <same as skill description, shorter>
globs:
  - "<paths that trigger this rule>"
alwaysApply: false
---
# Delegates to .cursor/skills/<skill-name>/SKILL.md
```

Register new skills in this document's Skill Selection Guide and [AI_INDEX.md](../AI_INDEX.md).

### Phase 2 codegen sequence (when API contracts exist)

Recommended order per domain (repeat from execution plan §3):

1. Complete `02-business-domains/<domain>/` docs
2. Finalize `03-api-contracts/<domain>/`
3. Finalize `04-database-design/<domain>/`
4. `@design-database-schema <domain>` if not done
5. `@generate-nestjs-module <domain>` (future skill)
6. `@generate-ui-screen <screen-name>` from `05-ui-ux/`
7. Write acceptance tests referencing `AT-NNN`
8. Update domain `changelog.md`

### Output quality checklist

Before marking any generation task complete:

- [ ] Read order followed — no skipped steps
- [ ] [coding-standards.md](coding-standards.md) and [naming-conventions.md](naming-conventions.md) applied
- [ ] Cross-links resolve to real files
- [ ] No invented business rules or master data
- [ ] TODO gaps documented, not silently guessed
- [ ] Changelog updated (if domain docs touched)
- [ ] `AI_INDEX.md` updated (if new modules/files created)
- [ ] File size within limits

---

## Related Documents

- [coding-standards.md](coding-standards.md)
- [naming-conventions.md](naming-conventions.md)
- [folder-structure.md](folder-structure.md) — monorepo paths and module layout (DEC-007)
- [technology-stack.md](technology-stack.md)
- [changelog.md](changelog.md)
- [../AI_INDEX.md](../AI_INDEX.md)
- [../01-architecture/architecture-overview.md](../01-architecture/architecture-overview.md)
- [../Software-Documentation-Standard.md](../Software-Documentation-Standard.md)
- [../cbs-project-execution-plan.md](../cbs-project-execution-plan.md)
- [Agent Skills standard](https://agentskills.io)
