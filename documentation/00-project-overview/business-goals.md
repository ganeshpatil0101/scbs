# Business Goals — CBS SaaS Platform for Cooperative Banks

## Purpose

Defines explicit, numbered, measurable business goals for the platform. Goals here must use unambiguous language (no "usually / generally / sometimes") per `Software-Documentation-Standard.md` and `AI_INDEX-Documents.md` Business Rules Standard, applied here to goals for the same traceability reason.

## Scope

Covers commercial/business goals only. Does not cover:
- Functional/business rules for specific modules (e.g., minimum balance rules) — see `02-business-domains/*/business-rules.md` (not yet authored)
- The narrative problem statement and market positioning — see [vision.md](vision.md)

## Dependencies

- [vision.md](vision.md) — problem statement and competitive context these goals operationalize
- [../01-architecture/architecture-overview.md](../01-architecture/architecture-overview.md) — cost estimates (Section 9) that BG-003 depends on

## Goals

### BG-001 — Year 1: Single-Tenant Operational Accuracy

Onboard exactly **one** cooperative bank tenant in Year 1, located in Maharashtra. Success is defined as:
- All accounting reports reconcile with full accuracy (no manual or very less correction required after standard processing).
- Year-end close process completes without requiring extensive very less manual user intervention.

**Status:** Target, not yet measured — no tenant onboarded at time of writing.

### BG-002 — Year 2–3: Controlled Regional Scale-Up

Expand from 1 tenant to **5–10 tenants** within Years 2–3, continuing to focus exclusively on Maharashtra-region cooperative banks. Do not expand outside Maharashtra within this horizon.

**Rationale:** Validate the platform with deep regional focus before geographic expansion (see [vision.md](vision.md) Out of Scope).

### BG-003 — Cost Advantage Over Incumbent Vendors

Pricing model: **per-branch SaaS subscription + minimal AMC + separately priced on-demand/custom functionality.**

This must structurally undercut the incumbent vendor model of *(high per-branch fee + AMC + one-time license, all three stacked)*. Infrastructure cost per tenant (see `architecture-overview.md` Section 9) must be tracked against per-branch subscription pricing to confirm margin viability — **TODO: target margin/price point not yet defined; needs explicit pricing decision before BG-003 can be marked measurable.**

### BG-004 — UX Simplicity for Low-Tech-Literacy Staff

All UI screens (see `05-ui-ux/`) must be operable by cooperative bank staff without advanced computer literacy, particularly Clerk and Cashier roles who perform high-frequency transactional work.

**Measurement:** TODO — no usability benchmark (e.g., task completion time, error rate, training time) has been defined yet. Recommend defining this before UAT.

### BG-005 — Interactive Reporting as a Standard Feature

Every list/register/grid screen across all modules must support: search, column filtering, advanced search, and export — closing the gap explicitly identified against incumbent vendors in [vision.md](vision.md).

**Cross-reference:** This is already partially reflected in existing UI specs (e.g., `05-ui-ux/customer/customer-list-screen.md`, `05-ui-ux/fixed-deposit/fd-account-register-screen.md` both include `निर्यात करा` / Export actions and grid search). Confirm this pattern is applied consistently across **all** register/list screens during `03-api-contracts/` and `05-ui-ux/` review — several screens currently have `TODO` markers for grid columns/actions that should be resolved with this goal in mind.

### BG-006 — API Availability

Provide API access to tenant data/functionality — an explicit gap in the incumbent vendor market.

**TODO:** Scope of public API surface (which modules, what auth model, rate limits) is not yet defined. Should be defined in `03-api-contracts/` once a module's domain documentation exists.

### BG-007 — Revenue Model Structure

Revenue components, in order of predictability:
1. Per-branch subscription fee (recurring, predictable)
2. Minimal AMC (recurring, predictable)
3. On-demand/custom functionality fee (one-off, billed per request when a tenant wants bank-specific functionality built)

**TODO:** Specific price points for all three components are not yet defined — flag as an open commercial decision, not a documentation gap.

### BG-008 — No Regulatory Compliance Mandate (Explicit Non-Goal)

This project is **not** justified or driven by an RBI or other regulatory compliance mandate. Compliance documentation (`07-compliance/`) should still exist for due-diligence and correctness (e.g., standard cooperative banking accounting norms), but compliance is explicitly **not** a sales driver or success metric for this platform.

## Open Items (require business decisions before these goals are fully measurable)

| Goal | Missing decision |
|---|---|
| BG-003 | Specific per-branch price point and AMC percentage/amount |
| BG-004 | Usability benchmark/acceptance criteria |
| BG-006 | API scope, auth model |
| BG-007 | Price points for all three revenue components |

## Related Documents

- [vision.md](vision.md)
- [glossary.md](glossary.md) — TODO: not yet authored
- [../01-architecture/architecture-overview.md](../01-architecture/architecture-overview.md)
- [../AI_INDEX.md](../AI_INDEX.md)
