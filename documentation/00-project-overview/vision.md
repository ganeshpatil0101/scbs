# Vision — CBS SaaS Platform for Cooperative Banks

## Purpose

Defines why this Core Banking Software (CBS) platform exists, the problem it solves, and the high-level target market and differentiation strategy. Per the AI read order (`AI_INDEX-Documents.md`), this document must be read before any module-level documentation, architecture decision, or code generation.

## Scope

Covers the project-wide vision only. Does **not** cover:
- Measurable, numbered business goals — see [business-goals.md](business-goals.md)
- Infrastructure/multi-tenancy architecture — see [../01-architecture/architecture-overview.md](../01-architecture/architecture-overview.md)
- Module-level business rules — see individual `02-business-domains/` folders (not yet authored)

## Problem Statement

Existing CBS software for Indian cooperative banks suffers from three compounding problems:

1. **High cost** — Incumbent vendors charge high per-branch fees, plus AMC, plus one-time licensing costs, stacked together.
2. **Poor user experience** — Interfaces are old, rigid, and lack basic interactive reporting capability: no data-grid search, filtering, advanced search, or export. Cooperative bank staff (Clerk, Cashier roles especially) are often not highly trained on complex software, so any UI complexity directly translates into operational friction and errors.
3. **No API access** — Incumbent vendors do not expose APIs, blocking integration and extensibility.

## Vision Statement

Build a CBS platform for Indian cooperative banks that is **simple enough for non-technical staff to operate confidently**, **significantly cheaper than incumbent vendors**, and provides **modern interactive reporting and API access** that the current market does not offer — without compromising accounting accuracy or year-end processing reliability.

## Target Market

| Attribute | Value |
|---|---|
| Primary customer | Indian cooperative banks |
| Initial region | Maharashtra state |
| Year 1 target | 1 tenant (single cooperative bank) |
| Year 2–3 target | 5–10 tenants, Maharashtra-focused |
| Regulatory driver | None — this is a commercial sale, not a compliance-mandated migration |

> See [business-goals.md](business-goals.md) for the numbered, measurable version of this scale-up plan.

## Competitive Positioning

| Dimension | Incumbent CBS Vendors (observed) | This Platform (target) |
|---|---|---|
| Pricing model | High per-branch fee + AMC + one-time license, all stacked | Per-branch SaaS subscription + minimal AMC + separately priced custom functionality |
| UI/UX | Old, complex, not designed for low-tech-literacy staff | Simplicity-first; designed for Clerk/Cashier-level users |
| Reporting | Static, no grid search/filter/export | Interactive data grids with search, filtering, advanced search, export |
| APIs | Not provided | Provided (exact scope TODO — to be defined in API contracts) |
| Support | Reported as poor | TODO — support model not yet defined |

## Differentiation Principles

These principles should be treated as design constraints across all UI/UX and module documentation, not just marketing claims:

- **Simplicity first.** Every screen should be usable by cooperative bank staff without advanced computer literacy. When a UI choice trades off simplicity against feature richness, simplicity wins unless the feature is essential to a core banking workflow.
- **Interactive reporting by default.** Any list/grid screen (see `05-ui-ux/` screen specs) should support search, filter, advanced search, and export — this is a market gap, not an optional nice-to-have.
- **Cost discipline.** Architecture and infrastructure decisions (see `01-architecture/architecture-overview.md`) should be evaluated against the per-branch SaaS pricing model — infra cost per tenant directly affects whether the pricing strategy is viable.
- **Accuracy over automation shortcuts.** Especially for accounting and year-end processing — see [business-goals.md](business-goals.md) BG-001 for the specific success criterion.

## Out of Scope (Explicit Non-Goals)

- This project is **not** driven by an RBI or other regulatory mandate. Regulatory/compliance documentation (`07-compliance/`) should still be produced for due diligence, but it is not the sales or design driver.
- No multi-region (outside Maharashtra) rollout is planned within the current 1–3 year horizon.

## Dependencies

- [glossary.md](glossary.md) — formal definitions for terms used above (e.g., tenant, AMC).
- [../01-architecture/architecture-overview.md](../01-architecture/architecture-overview.md) — multi-tenancy and cost-efficiency decisions that this vision depends on for cost-discipline feasibility.

## Related Documents

- [business-goals.md](business-goals.md)
- [system-boundaries.md](system-boundaries.md)
- [../01-architecture/architecture-overview.md](../01-architecture/architecture-overview.md)
- [../AI_INDEX.md](../AI_INDEX.md)
