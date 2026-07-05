# Screen Spec — New User (सेटिंग्ज > मास्टर > नवीन युजर)

> **Superseded (2026-07-05):** Consolidated into [staff-system-access-screen.md](staff-system-access-screen.md). Retained for field reference only.

## Purpose

UI specification for creating a system user. Two-tab form. Intended for AI agents implementing this screen.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | नवीन युजर | New User |
| Breadcrumb | डॅशबोर्ड > सेटिंग्ज > मास्टर > नवीन युजर | Dashboard > Settings > Master > New User |
| Parent Module | मास्टर | Master |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | युजरची माहिती | User Information |
| 2 | युजर रोल | User Role |

## Reference Screenshots

| Screenshot File | Tab |
| :--- | :--- |
| `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-मास्टर-नवीन युजर-1.png` | Tab 1 — User Information |

---

## Tab 1: युजरची माहिती (User Information)

### User Type - (Not required now skip)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | संचालक | Director | Radio | No | Default selected |
| 2 | कर्मचारी | Staff | Radio | No | — |

### Basic Information

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 3 | नाव (ग्राहक क्रमांक/नाव) | Name | Dropdown | Yes | Default: `निवडा`. populate all customer list |
| 4 | हुद्दा | Designation | Textbox | No | — |
| 5 | लॉगीन नाव | Login Name | Textbox | Yes | — |
| 6 | पासवर्ड | Password | Textbox | Yes | Masked |
| 7 | पडताळणी पासवर्ड | Confirm Password | Textbox | Yes | Masked |
| 8 | स्थिती | Status | Dropdown | Yes | Default: `सक्रिय` (Active). Other values: `सक्रिय,निष्क्रिय,स्थगित,सिस्टीम स्थगित,` |
| 9 | युजरचा प्रकार | User Type | Dropdown | Yes | Default: `सोसायटी` (Society). |
| 11 | सुपर युजर | Super User | Checkbox | No | — |

### Section: सेटिंग (Settings)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 14 | रोख भरणा व्हाउचर मर्यादा | Cash Deposit Voucher Limit | Textbox | No | — |
| 15 | रोख भरणा व्हाउचर पासिंग मर्यादा | Cash Deposit Voucher Passing Limit | Textbox | No | — |
| 16 | शाखा अंतर्गत व्यवहार | Intra-branch Transaction | Checkbox | No | When checked, enables limits below |
| 17 | शाखा अंतर्गत पावती मर्यादा | Intra-branch Receipt Limit | Textbox | No | Disabled until checkbox checked |
| 18 | शाखा अंतर्गत देय मर्यादा | Intra-branch Payable Limit | Textbox | No | Disabled until checkbox checked |

### Section: संघटना युजर अधिकार (Organization User Rights)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 19 | संघटना | Organization | Dropdown | Yes | Society name |
| 20 | शाखा निवडा | Select Branch | Autocomplete | Yes | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |

**Action:** `+ टाका` (Add) — add row to rights grid.

### Rights Grid

Columns: निवडा, अ.क्र., संघटना, शाखा नाव.

**Action:** `काढा` (Remove).

---

## Tab 2: युजर रोल (User Role)

See [user-role-screen.md](user-role-screen.md) — role assignment uses the same permission matrix pattern.

---

## Mockup

| Property | Value |
| :--- | :--- |
| HTML mockup | [mockups/settings/master/new-user-screen/index.html](../../mockups/settings/master/new-user-screen/index.html) |
| Review guide | [mockups/settings/master/new-user-screen/README.md](../../mockups/settings/master/new-user-screen/README.md) |
| Stack | Tailwind CSS v4 (CDN), Marathi labels only |
| Status | Draft — pending bank user review |

---

## Related Documents

- [overview.md](overview.md)
- [new-employee-screen.md](new-employee-screen.md)
- [user-role-screen.md](user-role-screen.md)
