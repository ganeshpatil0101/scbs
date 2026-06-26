# Screen Spec — Loan Interest Rate Change (सेटिंग्ज > कर्ज > व्याज दरात बदल)

## Purpose

UI specification for changing loan scheme interest rates. Two-tab workflow. Intended for AI agents implementing this screen.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | व्याज दरात बदल | Interest Rate Change |
| Breadcrumb | डॅशबोर्ड > सेटिंग्ज > कर्ज > व्याज दरात बदल | Dashboard > Settings > Loan > Interest Rate Change |
| Parent Module | कर्ज | Loan |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | व्याज दर बदल | Interest Rate Change |
| 2 | आजपर्यंत झालेले व्याज दर बदल | Past Interest Rate Changes |

## Reference Screenshots

| Screenshot File | Tab |
| :--- | :--- |
| `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-कर्ज-व्याज दरात बदल-1.png` | Tab 1 — Interest Rate Change |

---

## Tab 1: व्याज दर बदल (Interest Rate Change)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | योजना | Scheme | Dropdown | Yes | Loan scheme list. Values: `TODO` (not opened in screenshot) |
| 2 | बदल दिनांक | Change Date | Date | Yes | — |
| 3 | सर्व खात्यांना नवीन दर लागू करावा | Apply New Rate to All Accounts | Radio | No | Default selected |
| 4 | फक्त नवीन खात्यांना नवीन दर लागू करावा | Apply New Rate to New Accounts Only | Radio | No | — |

**Actions:** `निर्यात` (Export), `पुढे` (Next).

---

## Tab 2: आजपर्यंत झालेले व्याज दर बदल (Past Interest Rate Changes)

Not captured in screenshots. Fields: `TODO`.

---

## Related Documents

- [overview.md](overview.md)
- [../schemes/loan-new-scheme-screen.md](../schemes/loan-new-scheme-screen.md)
