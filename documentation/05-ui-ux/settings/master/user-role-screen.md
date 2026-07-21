# Screen Spec — User Role (सेटिंग्ज > मास्टर > युजर रोल)

## Purpose

UI specification for defining a user role and assigning per-form permissions. Intended for AI agents implementing this screen.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | युजर रोल | User Role |
| Breadcrumb | डॅशबोर्ड > सेटिंग्ज > मास्टर > युजर रोल | Dashboard > Settings > Master > User Role |
| Parent Module | मास्टर | Master |

## Reference Screenshots

| Screenshot File | Section |
| :--- | :--- |
| `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-मास्टर-युजर रोल.png` | Role name + permission grid (Accounting menu sample) |

---

## Fields

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | युजर रोल | User Role | Textbox | Yes | Role name |

---

## Permission Grid

Each row maps one form to one of three permission levels. Header checkboxes allow bulk select per column.

| # | Marathi Column | English Column | Type | Values / Notes |
| :---: | :--- | :--- | :--- | :--- |
| 1 | अ.क्र. | Sr. No. | Label | — |
| 2 | मेनु | Menu | Label | Module name from app menu registry (e.g. `अकाउंटींग`) — not a fixed enum |
| 3 | फॉर्मचे नाव | Form Name | Label | Screen name from app menu registry — populated dynamically for all modules |
| 4 | सर्व अधिकार | All Rights | Checkbox | Full access |
| 5 | फक्त बघण्यासाठी | View Only | Checkbox | Read-only |
| 6 | अधिकार नाही | No Rights | Checkbox | Deny access |

**Rows:** Full मेनु + फॉर्म list is loaded dynamically from the application menu registry (all modules). Spec sample below is Accounting only for layout reference; mockups show the same sample plus a note that remaining rows come from the registry.

**Sample rows (Accounting menu — partial; grid scrolls):**

| Sr. | Form (Marathi) | Form (English) |
| :---: | :--- | :--- |
| 1 | अंदाज पत्रक | Budget Sheet |
| 2 | अंदाज पत्रक अहवाल | Budget Report |
| 3 | अनुक्रम बदल | Change Sequence |
| 4 | अहवाल एमआयएस | MIS Report |
| 5 | एकाधिक मुदत ठेव खाते बंद | Close Multiple FD Accounts |
| 6 | कॅश ट्रान्सफर स्क्रोल | Cash Transfer Scroll |
| 7 | कोणतेही व्यवहार | Any Transactions |
| 8 | खाते यादी (जी एल हेड) | Account List (GL Head) |

---

## Mockup

| Property | Value |
| :--- | :--- |
| HTML mockup | [mockups/settings/master/user-role-screen/index.html](../../mockups/settings/master/user-role-screen/index.html) |
| Review guide | [mockups/settings/master/user-role-screen/README.md](../../mockups/settings/master/user-role-screen/README.md) |
| Stack | Tailwind CSS v4 (CDN), Marathi labels only |
| Status | Draft — pending bank user review |

---

## Related Documents

- [overview.md](overview.md)
- [staff-system-access-screen.md](staff-system-access-screen.md)
