# Screen Spec — Bank Deposit New Bank (गुंतवणूक > बँक ठेव > नवीन बँक)

## Purpose

UI specification for registering a new investment bank (G.L. head master for bank deposits). Distinct from operational **बँक > नवीन बँक** — see [../bank/new-bank-screen.md](../bank/new-bank-screen.md).

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | नवीन बँक | New Bank |
| Breadcrumb | डॅशबोर्ड > गुंतवणूक > बँक ठेव > नवीन बँक | Dashboard > Investment > Bank Deposit > New Bank |
| Parent Module | गुंतवणूक > बँक ठेव | Investment > Bank Deposit |

## Reference Screenshots

| File | Section |
| :--- | :--- |
| `screenshots/गुंतवणूक/डॅशबोर्ड-गुंतवणूक-बँक ठेव-नवीन बँक.png` | Full screen + dropdown |

---

## Form Fields

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | जीएल हेड क्र. | G.L. Head No. | Textbox | No | e.g. `167` |
| 2 | बँकेचे नाव | Bank Name | Textbox | Yes | — |
| 3 | तपशील | Details | Textbox | No | — |
| 4 | बँक प्रकार | Bank Type | Dropdown | No | `इतर` (Other), `शेड्यूल्ड कमर्शियल बँक ठेव` (Scheduled Commercial Bank Deposit), `पोस्ट ऑफिस ठेव` (Post Office Deposit), `आर.बी.आय.` (RBI), `राज्य सहकारी बँक` (State Cooperative Bank), `जिल्हा सहकारी बँक` (District Cooperative Bank), `राष्ट्रीयकृत बँक` (Nationalized Bank), `प्रायव्हेट सहकारी बँक` (Private Cooperative Bank) |

**Actions:** `पूर्ण`, `पुन्हा टाका` (Reset).

---

## Related Documents

- [overview.md](overview.md)
- [bank-deposit-bank-list-screen.md](bank-deposit-bank-list-screen.md)
- [../bank/new-bank-screen.md](../bank/new-bank-screen.md)
