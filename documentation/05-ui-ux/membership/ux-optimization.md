# Membership Module — UX Optimization Audit

Audit date: 2026-07-12. Applied: 2026-07-12. Domain: `documentation/05-ui-ux/membership/`.

Patterns applied: [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md), [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md).

Reference implementation: [../customer/ux-optimization.md](../customer/ux-optimization.md) (Other Account Management merge), [../loan/ux-optimization.md](../loan/ux-optimization.md) (transaction mode + conditional tabs).

## Summary

| Metric | Before | After |
| :--- | :---: | :---: |
| Menu screens | 6 | **5** |
| Shares Transfer surfaces | 2 screens | 1 screen (2 top-level tabs) |
| Customer/Member No+Name pairs | 5 locations | 0 (Autocomplete) |
| Organization as form field | Register | Session header |
| Fields → Advanced | — | 12+ |
| Shared components documented | — | 5 |

## Consolidated Screen Map

| New / kept screen | Replaces / action | Document |
| :--- | :--- | :--- |
| नवीन सभासदत्व (New Membership) | Field cleanup | [new-membership-screen.md](new-membership-screen.md) |
| सभासद रजिस्टर (Member Register) | Field cleanup; `तपशील` gap noted | [member-register-screen.md](member-register-screen.md) |
| सभासदत्व व्यवहार (Membership Transaction) | Mode-conditional tabs + Advanced + shared refs | [membership-transaction-screen.md](membership-transaction-screen.md) |
| लाभांश व्यवहार (Dividend Transaction) | Member Autocomplete + shared refs | [dividend-transaction-screen.md](dividend-transaction-screen.md) |
| **शेअर्स ट्रान्सफर व्यवस्थापन (Shares Transfer Management)** | Shares Transfer + Shares Transfer List | [shares-transfer-management-screen.md](shares-transfer-management-screen.md) |

**Not merged:** Membership Transaction ↔ Dividend Transaction (different Tab 1 workflows — share capital vs dividend warrants).

### Tab layout (Shares Transfer Management)

| Top tab | Marathi | English | Replaces |
| :---: | :--- | :--- | :--- |
| 1 | नवीन ट्रान्सफर | New Transfer | Shares Transfer (3 inner tabs) |
| 2 | ट्रान्सफर यादी | Transfer List | Shares Transfer List |

---

## Decisions Applied (2026-07-12)

| # | Decision |
| :---: | :--- |
| 1 | Merge Shares Transfer + Shares Transfer List → Shares Transfer Management (user choice 1A) |
| 2 | Do **not** add सभासद माहिती (Member Information) — Register `तपशील` remains open gap (user choice 2B) |
| 3 | Customer No. + Name → Customer Autocomplete on New Membership |
| 4 | Member No. + Name → Member Autocomplete on Dividend Tab 1 and Shares Transfer From/To |
| 5 | Organization → session header on Member Register |
| 6 | Membership Transaction: Instrument + Transfer tabs visible when mode = `ट्रान्सफर`; Share Allocation on Credit; withdrawal grid on Debit |
| 7 | Document shared `app-cheque-tab`, `app-transfer-tab`, `app-kyc-info-tab`, `app-nominee-form` |
| 8 | Ledger tab on Membership Transaction — **not added** (Dividend already has Ledger) |
| 9 | Introducer on New Membership Tab 2 → Customer Autocomplete (same as primary member pick) |

---

## Action Checklist (all applied in specs)

### High priority

- [x] Consolidate Shares Transfer + List → shares-transfer-management-screen.md
- [x] Customer Autocomplete on New Membership Tab 1 and Tab 2 (introducer + joint holder row)
- [x] Member Autocomplete on Dividend Tab 1 and Shares Transfer From/To
- [x] Organization → session header on Member Register
- [x] Member Register: Customer Name search → Customer Autocomplete
- [x] Membership Transaction: conditional tabs by Credit/Debit and Cash/Transfer mode
- [x] Shared component references on transaction screens
- [x] Superseded banners on old Shares Transfer + List specs

### Medium priority

- [x] New Membership → प्रगत सेटिंग्ज (Director, Annual Report, GL/Account Holder, Director Relative; nominee bank/occupation)
- [x] Membership Transaction → Advanced (Resolution Date/No., Special Instructions)
- [x] Register Advanced Search link retained; fields uncaptured
- [x] TODO tabs scaffolded with explicit deferrals (Nominee); KYC tabs later removed 2026-07-22 (see TODO Closure Pass)
- [x] Member entity added to entity-autocomplete-pattern.md

### Low priority / deferred

- [x] Member class naming (`अ वर्ग` vs `सभासद`) — noted below; labels not unified pending confirmation
- [x] Mockups — Phase 4 (`/generate-ui-mockup`); 5 Draft HTML mockups under `mockups/membership/`

---

## TODO Closure Pass (2026-07-22)

Bank confirmation resolved all remaining dropdown/tab gaps across the 5 current membership screens (superseded specs excluded):

| # | Item | Resolution |
| :---: | :--- | :--- |
| 1 | New Membership — स्थिती (Status) values | Reused standard account-status enum: `चालू`, `बंद`, `स्थगित` |
| 2 | New Membership — संचालक (Director) dropdown | Converted to Checkbox (director yes/no), default unchecked |
| 3 | New Membership — वार्षिक अहवाल (Annual Report) values | `पोस्ट` (Post), `कुरीअर` (Courier) |
| 4 | New Membership — स्थान/जिल्हा/तालुका/शहर dropdowns | Converted to Textbox, consistent with New Customer address block |
| 5 | New Membership — नाते (Relation) "may extend" note | Finalized existing 13-value canonical list |
| 6 | Membership Txn / Dividend Txn / Shares Transfer — बँक निवडा | Converted to Autocomplete from Bank Master (same as accounting/loan) |
| 7 | Membership Txn Tab 4 — शेअर्स सिरीज (Share Series) values | Reused Share Class enum: `अ वर्ग`, `ब वर्ग` |
| 8 | Shares Transfer — स्क्रोल निवडा (Select Scroll) | Removed — not required |
| 9 | Member Register — Advanced Search link | Removed — primary filters sufficient |
| 10 | Membership Txn Tab 7 (KYC) / Dividend Txn Tab 6 (KYC) | Removed — scaffolds referenced now-superseded Savings KYC pattern |

Mockups updated to match (`mockups/membership/`); see [changelog.md](changelog.md) 2.0.0.

---

## Deprecated Specs (reference only)

| Superseded spec | New spec |
| :--- | :--- |
| [shares-transfer-screen.md](shares-transfer-screen.md) | [shares-transfer-management-screen.md](shares-transfer-management-screen.md) — Tab 1 |
| [shares-transfer-list-screen.md](shares-transfer-list-screen.md) | [shares-transfer-management-screen.md](shares-transfer-management-screen.md) — Tab 2 |

---

## Open Gaps (retained)

| Gap | Disposition |
| :--- | :--- |
| Register `तपशील` → Member Information | **Deferred** (user 2B) — no navigation target spec |
| Member class naming (`अ वर्ग` vs `सभासद`) | Note only — may be different enums |
| Mockups | 5 Draft under `mockups/membership/` |

---

## Apply Status

| Phase | Status |
| :--- | :--- |
| Phase 1 — Audit | Complete |
| Phase 2 — Plan | Complete |
| Phase 3 — Apply to specs | **Complete (2026-07-12)**; TODO closure pass **Complete (2026-07-22)** |
| Phase 4 — Mockups | **Complete (Draft, 2026-07-12)**; updated for TODO closure **2026-07-22** |

---

## Related Documents

- [overview.md](overview.md)
- [changelog.md](changelog.md)
- [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
- [../customer/ux-optimization.md](../customer/ux-optimization.md)
- [../loan/ux-optimization.md](../loan/ux-optimization.md)
- [../../AI_INDEX.md](../../AI_INDEX.md)
