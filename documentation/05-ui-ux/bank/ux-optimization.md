# Bank Module — UX Optimization Audit

Audit date: 2026-07-07. Applied: 2026-07-07. Domain: `documentation/05-ui-ux/bank/`.

Patterns applied: [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md), [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md).

Reference implementation: [../settings/ux-optimization.md](../settings/ux-optimization.md).

## Summary

| Metric | Before | After |
| :--- | :---: | :---: |
| Menu screens | 3 | 1 |
| Tabs | — | 2 |
| Field removals | — | 2 (duplicate branch controls) |
| Fields → Autocomplete | — | 3 |
| Fields → Auto-fill | — | 2 |
| Fields → Advanced / Additional search | — | 9 |
| Label clarifications | — | 2 |

Three legacy menu entries merged into **बँक व्यवस्थापन (Bank Management)** — one page, list + create/update per tab.

## Consolidated Screen Map

| New screen | Replaces | Document |
| :--- | :--- | :--- |
| बँक व्यवस्थापन (Bank Management) | Bank Register + New Bank + Cheque Register | [bank-management-screen.md](bank-management-screen.md) |

### Tab layout

| Tab | Marathi | English | CRUD on one page |
| :---: | :--- | :--- | :--- |
| 1 | बँक खाते | Bank Accounts | List + Create + Update (form panel) |
| 2 | चेक रजिस्टर | Cheque Register | List + Update (cheque processing panel). Create via जमा/नावे |

## Cross-Domain Note

[../investment/bank-deposit-new-bank-screen.md](../investment/bank-deposit-new-bank-screen.md) registers investment GL bank *masters*; operational bank accounts remain under **बँक > बँक व्यवस्थापन**. **Do not merge** — different modules.

---

## Tab 1 — Bank Accounts (was Register + New Bank)

### Field changes applied

| Original field | Action | Applied in |
| :--- | :--- | :--- |
| संघटना (Organization) | **Auto-fill** | Screen header — removed from filter |
| शाखा कोड + शाखेचे नाव | **Simplify** → Autocomplete | Tab 1 primary search |
| जी.एल. हेड क्रमांक | **Simplify** → Autocomplete | Tab 1 form panel |
| स्थिती on create | **Auto-fill** | Read-only `चालू`; editable on Update |
| Internal branch txn, min balance, fund transfer | **Hide Advanced** | Tab 1 प्रगत सेटिंग्ज |
| IFSC | Keep | Tab 1 form (default view) |

### Layout

Filter → Grid (list) → Form panel (Create via `+ नवीन`, Update via row select / `तपशील`).

---

## Tab 2 — Cheque Register

### Field changes applied

| Original field | Action | Applied in |
| :--- | :--- | :--- |
| शाखा क्र. + शाखा निवडा | **Simplify** → Autocomplete | Tab 2 primary search |
| Amount, customer, cheque no., approval dates, bank method | **Hide Advanced** | अतिरिक्त शोध section |
| Approval date labels | **Simplify** | From/To pair |
| Bank Method required | Relaxed | Optional in additional search |
| Cheque return fee + actions | **Conditional** | Visible when row(s) selected |

### Layout

Filter → Grid (list) → Processing panel (Update when rows selected).

---

## Deprecated Specs (reference only)

| Superseded spec | New spec |
| :--- | :--- |
| [bank-register-screen.md](bank-register-screen.md) | [bank-management-screen.md](bank-management-screen.md) — Tab 1 |
| [new-bank-screen.md](new-bank-screen.md) | [bank-management-screen.md](bank-management-screen.md) — Tab 1 |
| [check-register-screen.md](check-register-screen.md) | [bank-management-screen.md](bank-management-screen.md) — Tab 2 |

---

## Action Checklist

### High priority

- [x] Consolidate 3 screens → bank-management-screen.md (2 tabs)
- [x] Tab 1: list + create/update form on one page
- [x] Tab 2: list + conditional update panel on one page
- [x] Bank Register: Organization → Auto-fill; Branch → Autocomplete
- [x] New Bank: GL → Autocomplete; Advanced Settings section
- [x] Cheque Register: Branch → Autocomplete; tiered filters; conditional actions
- [x] Superseded banners on old specs
- [x] overview.md, changelog.md updated

### Low priority

- [ ] Resolve `TODO` dropdown values (Account Type, Status, Bank Method) before mockup
- [ ] Generate HTML mockup for bank-management-screen

---

## Apply Status

| Phase | Status |
| :--- | :--- |
| Phase 1 — Audit | Complete |
| Phase 2 — Plan | Complete |
| Phase 3 — Apply to specs | **Complete (2026-07-07)** |

---

## Related Documents

- [overview.md](overview.md)
- [bank-management-screen.md](bank-management-screen.md)
- [changelog.md](changelog.md)
- [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
- [../../AI_INDEX.md](../../AI_INDEX.md)
