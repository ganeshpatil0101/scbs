# Screen Spec — Loan Interest Rate Change (सेटिंग्ज > कर्ज > व्याज दरात बदल)

> **Simplified (2026-07-05):** History grid moved from separate Tab 2 to collapsible section on same page. See [ux-optimization.md](../ux-optimization.md).

## Purpose

UI specification for changing loan scheme interest rates. Single-page form with collapsible change history.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | व्याज दरात बदल | Interest Rate Change |
| Breadcrumb | डॅशबोर्ड > सेटिंग्ज > कर्ज > व्याज दरात बदल | Dashboard > Settings > Loan > Interest Rate Change |
| Parent Module | कर्ज | Loan |

## Reference Screenshots

| Screenshot File | Section |
| :--- | :--- |
| `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-कर्ज-व्याज दरात बदल-1.png` | Rate change form |

---

## Section: व्याज दर बदल (Interest Rate Change)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | योजना | Scheme | Dropdown | Yes | Loan scheme list — populated dynamically |
| 2 | बदल दिनांक | Change Date | Date | Yes | — |
| 3 | सर्व खात्यांना नवीन दर लागू करावा | Apply New Rate to All Accounts | Radio | No | Default selected |
| 4 | फक्त नवीन खात्यांना नवीन दर लागू करावा | Apply New Rate to New Accounts Only | Radio | No | — |

**Actions:** `निर्यात` (Export), `जतन करा` (Save).

---

## Section: मागील व्याजदर (Past Rate Changes) — collapsed by default

Collapsible history log. Former Tab 2 content.

### Grid Columns

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | अ.क्र. | Sr. No. |
| 2 | योजना क्र. | Scheme No. |
| 3 | योजना | Scheme |
| 4 | कालावधी | Duration |
| 5 | बदल दिनांक | Change Date |
| 6 | पूर्वीचा व्याज दर (द.सा.द.शे.) | Previous Interest Rate (p.a. %) |
| 7 | पूर्वीचा दंड व्याजदर (द.सा.द.शे.) | Previous Penalty Rate (p.a. %) |

---

## Mockup

| Property | Value |
| :--- | :--- |
| HTML mockup | [mockups/settings/loan/loan-interest-rate-change-screen/index.html](../../mockups/settings/loan/loan-interest-rate-change-screen/index.html) |
| Review guide | [mockups/settings/loan/loan-interest-rate-change-screen/README.md](../../mockups/settings/loan/loan-interest-rate-change-screen/README.md) |
| Stack | Tailwind CSS v4 (CDN), Marathi labels only |
| Status | Draft — pending bank user review |

---

## Related Documents

- [overview.md](overview.md)
- [ux-optimization.md](../ux-optimization.md)
- [../schemes/new-scheme-screen.md](../schemes/new-scheme-screen.md)
- [../../shared/ui-simplification-patterns.md](../../shared/ui-simplification-patterns.md)
