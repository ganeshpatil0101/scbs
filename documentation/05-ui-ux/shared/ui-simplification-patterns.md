# UI Simplification Patterns (Cooperative Bank CBS)

Canonical patterns for simplifying CBS UI specs so **non-technical bank staff** (Clerk, Cashier, Branch Manager) can complete tasks without accounting or IT knowledge.

Apply these patterns during `@optimize-ui-ux` reviews and when authoring or updating any `*-screen.md` spec, mockup, or Angular screen.

## Design Principles

| Principle | Rule |
| :--- | :--- |
| Progressive disclosure | Show essential fields by default. Move technical or rare fields to a collapsible **प्रगत सेटिंग्ज (Advanced Settings)** section. |
| Conditional visibility | Hide fields until their parent condition is met. Do **not** show disabled fields that staff cannot explain. |
| Auto-fill | When a value is system-generated or has a single default, render as read-only or omit from the default view. |
| Single lookup control | Replace Customer No. + Customer Name (or ID + select) pairs with one **Autocomplete** per [entity-autocomplete-pattern.md](entity-autocomplete-pattern.md). |
| Task-oriented screens | One screen = one business task. Merge screens staff always use together (e.g. Employee + User login). |
| Shared components | Document repeated tab/section patterns once; reference a shared component instead of duplicating field tables. |

## Field Disposition Actions

Use these labels in optimization audits and spec changelogs:

| Action | When to apply | Spec notation |
| :--- | :--- | :--- |
| **Remove** | Field marked skip/not required, no values defined, or duplicate of another control | Omit from spec; note in changelog with reason |
| **Auto-fill** | GL Head No. on GL Account Setup (creation only), User Type = Society, default Status | `Type: Label (read-only)` or omit with default in Notes. **Schemes:** GL Head is an Autocomplete lookup from master — not auto-generated |
| **Simplify** | Two fields that should be one; confusing conditional disable | Merge or redesign; document new control |
| **Hide Advanced** | Unicode names, receipt series, OIR, DP formula, moratorium rules | Move to `### Section: प्रगत सेटिंग्ज` with `Visible: When expanded` |
| **Consolidate** | Entire screen merged into another | Mark old spec **Superseded**; link to new spec |

## Shared UI Components (document once, reuse everywhere)

| Component ID | Pattern | Used by |
| :--- | :--- | :--- |
| `app-interest-posting-grid` | Interest Posting Day + Month dropdowns → Add → posting-date grid | All scheme types |
| `app-rate-slab-editor` | Duration + Duration Type + Rate + Add → slab grid | FD, Daily, Recurring account-close tabs |
| `app-charges-select` | Charges dropdown + grid (identical values) | All scheme types |
| `app-benefits-checkboxes` | Senior Citizen / Female / Widow / Disabled / … checkboxes + benefit rate | FD, Recurring (one section per scheme, not two tabs) |
| `app-entity-autocomplete` | Branch / GL / Account / Customer / Member lookup | Master, Accounting, Membership, Transactions, Customer |

When a screen uses a shared component, the spec may reference the component instead of repeating every column — but **required-ness and visibility rules** must still be stated on the screen spec.

## Screen Consolidation Pattern

When merging screens:

1. Create one new `*-screen.md` with combined tabs in task order.
2. Add **Superseded** banner on each old spec linking to the new file.
3. Update module `overview.md` and `AI_INDEX.md`.
4. Append `changelog.md` with consolidation entry and date.
5. Mockups and Angular work target the **new** spec only.

## Advanced Settings Section Template

Use this section heading on any screen with hidden technical fields:

```markdown
### Section: प्रगत सेटिंग्ज (Advanced Settings)

> Collapsed by default. Visible to users with accounting/admin role or when expanded manually.

| # | Marathi Label | English Label | Type | Required | Notes |
| ... fields moved from default view ...
```

## Optimization Deliverables (per domain folder)

Each optimized domain must have:

| File | Purpose |
| :--- | :--- |
| `<domain>/ux-optimization.md` | Audit summary, action checklist, before/after screen count |
| Updated `overview.md` | Lists **current** screens only; deprecated screens in a separate table |
| `changelog.md` entry | What changed, why, links to new specs |

## Related Documents

- [entity-autocomplete-pattern.md](entity-autocomplete-pattern.md)
- [../settings/ux-optimization.md](../settings/ux-optimization.md) — Settings module audit (reference implementation)
- [../../../.cursor/skills/optimize-ui-ux/SKILL.md](../../../.cursor/skills/optimize-ui-ux/SKILL.md)
