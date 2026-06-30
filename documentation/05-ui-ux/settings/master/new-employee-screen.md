# Screen Spec — New Employee (सेटिंग्ज > मास्टर > नवीन कर्मचारी) - (Not required in first phase skip now)

## Purpose

UI specification for registering a new employee or director. Intended for AI agents implementing this screen.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | नवीन कर्मचारी | New Employee |
| Breadcrumb | डॅशबोर्ड > सेटिंग्ज > मास्टर > नवीन कर्मचारी | Dashboard > Settings > Master > New Employee |
| Parent Module | मास्टर | Master |

## Reference Screenshots

| Screenshot File | Section |
| :--- | :--- |
| `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-मास्टर-नवीन कर्मचारी.png` | Full form with Designation dropdown open |

---

## Fields

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | संचालक | Director | Radio | No | Employee type. Default selected |
| 2 | कर्मचारी | Employee | Radio | No | Employee type |
| 3 | ग्राहक क्रमांक | Customer Number | Textbox | Yes | — |
| 4 | ग्राहकाचे नाव | Customer Name | Textbox | Yes | — |
| 5 | हुद्दा | Designation | Dropdown | Yes | `निवडा` (Select), `मुख्य कार्यकारी अधिकारी` (CEO), `अध्यक्ष` (Chairman), `उपाध्यक्ष` (Vice Chairman), `संचालक` (Director). Additional values may exist: `TODO` |
| 6 | हे कर्मचारी सध्या सेवेमध्ये आहे काय? | Is Employee Currently in Service? | Radio | No | `होय` (Yes) / `नाही` (No). Default: `होय` |

## Actions

| Button | Marathi | English |
| :--- | :--- | :--- |
| Save | पूर्ण | Complete |
| Reset | पूर्ववत | Revert |

---

## Related Documents

- [overview.md](overview.md)
- [new-user-screen.md](new-user-screen.md)
- [../../customer/new-customer-screen.md](../../customer/new-customer-screen.md)
