---
name: optimize-ui-ux
description: >-
  Review and simplify CBS UI/UX screen specs for non-technical cooperative bank
  staff. Use when optimizing a 05-ui-ux domain folder, consolidating screens,
  removing redundant fields, or invoking "/optimize-ui-ux". Produces ux-optimization.md,
  updated specs, and changelog entries following ui-simplification-patterns.md.
---

# Optimize UI/UX (Core Banking Software)

Systematic review and simplification of `documentation/05-ui-ux/<domain>/` screen specs so **Clerk, Cashier, and Branch Manager** staff can complete tasks without accounting or IT knowledge.

**Reference implementation:** [documentation/05-ui-ux/settings/ux-optimization.md](../../documentation/05-ui-ux/settings/ux-optimization.md)

## When to Use

- User asks to simplify, review, or optimize UI screens for a domain folder
- User invokes `/optimize-ui-ux <domain>` (e.g. `customer`, `reports`, `loan`)
- Before generating mockups or Angular for a domain with many similar screens
- After capturing screenshots from legacy app — prune before spec finalization

## Non-Negotiable Principles

Read and apply [documentation/05-ui-ux/shared/ui-simplification-patterns.md](../../documentation/05-ui-ux/shared/ui-simplification-patterns.md) in full. Summary:

| Principle | Rule |
| :--- | :--- |
| Progressive disclosure | Technical fields → **प्रगत सेटिंग्ज (Advanced Settings)** collapsible |
| Conditional visibility | Hide until parent condition met — never show disabled mystery fields |
| Auto-fill | System-generated values → read-only `Label` |
| Single Autocomplete | No Customer No. + Name pairs — one lookup per [entity-autocomplete-pattern.md](../../documentation/05-ui-ux/shared/entity-autocomplete-pattern.md) |
| Task-oriented merge | Combine screens staff always use together |
| Shared components | Document repeated patterns once (`app-interest-posting-grid`, etc.) |

## Execution Workflow (follow in order)

### Phase 1 — Audit

1. Read [documentation/AI_INDEX.md](../../documentation/AI_INDEX.md).
2. List all `*-screen.md` files under `documentation/05-ui-ux/<domain>/`.
3. Read each spec + module `overview.md` + any mockups in `mockups/<domain>/`.
4. For each screen, classify every field:
   - **Keep** (essential, required for daily staff work)
   - **Remove** (marked skip, no values, duplicate)
   - **Auto-fill** (always same value / system-generated)
   - **Simplify** (merge two fields, redesign conditional)
   - **Hide Advanced** (accountant/IT only)
5. Identify duplicate UI patterns across screens (posting grids, slab editors, charges tabs).
6. Identify screen pairs/groups that share responsibility and should merge.

### Phase 2 — Plan

7. Create or update `<domain>/ux-optimization.md` with:
   - Before/after screen count
   - Consolidation map (new screen → replaces which old screens)
   - Field action checklist (High / Medium / Low priority)
   - Deprecated spec table
8. Present consolidation proposals using task-oriented naming (Marathi + English).

### Phase 3 — Apply (after user approval or when user says "apply")

9. Create new consolidated `*-screen.md` files for merged screens.
10. Add **Superseded** banner on each old spec linking to new file.
11. Apply field removals/simplifications in new specs (not only in audit doc).
12. Update module `overview.md` — **Current Screens** table + **Superseded** table.
13. Update parent `overview.md` if domain has sub-modules.
14. Append entries to module `changelog.md` and domain `changelog.md` if present.
15. Update [documentation/AI_INDEX.md](../../documentation/AI_INDEX.md) with new links.
16. If mockups exist for superseded screens, note in README that mockups target new spec path.

### Phase 4 — Downstream alignment

17. New mockups (`@generate-ui-mockup`) target **current** specs only.
18. New Angular (`@generate-ui-screen`) targets **current** specs; use Advanced section + shared component IDs from simplification patterns.

## Deliverables Checklist

- [ ] `<domain>/ux-optimization.md` exists with action checklist
- [ ] Consolidated screen specs created where merges were planned
- [ ] Old specs have Superseded banner + link
- [ ] All `overview.md` files list current vs superseded screens
- [ ] `changelog.md` updated in each touched sub-module
- [ ] `AI_INDEX.md` updated
- [ ] [ui-simplification-patterns.md](../../documentation/05-ui-ux/shared/ui-simplification-patterns.md) referenced

## Domain Folder Targets (pending optimization)

| Domain | Path | Notes |
| :--- | :--- | :--- |
| Settings | `05-ui-ux/settings/` | **Done** — reference implementation |
| Customer | `05-ui-ux/customer/` | Candidate: merge related registration flows |
| Reports | `05-ui-ux/reports/` | Candidate: shared filter patterns |
| Loan (operational) | `05-ui-ux/loan/` | Candidate: transaction screen tab overlap |
| Savings / FD / Daily / Recurring | operational folders | Candidate: shared account-opening tabs |

## Field Disposition Labels

Use consistently in audit tables and changelogs:

`Remove` | `Auto-fill` | `Simplify` | `Hide Advanced` | `Consolidate`

## Related Documents

- [ui-simplification-patterns.md](../../documentation/05-ui-ux/shared/ui-simplification-patterns.md)
- [settings/ux-optimization.md](../../documentation/05-ui-ux/settings/ux-optimization.md)
- [.cursor/rules/generate-ui-mockup.mdc](../../.cursor/rules/generate-ui-mockup.mdc)
- [.cursor/rules/generate-ui-screen.mdc](../../.cursor/rules/generate-ui-screen.mdc)
- [.cursor/rules/generate-document.mdc](../../.cursor/rules/generate-document.mdc)

## Notes for Cursor

- Invoke with `@optimize-ui-ux` or `/optimize-ui-ux <domain>`.
- Phase 1–2 can run without file writes (review only). Phase 3 requires explicit user approval unless user says "apply all".
- Do not delete superseded specs — mark Superseded and retain for field archaeology.
- Prefer canvas for review presentation; apply changes to markdown specs as source of truth.
