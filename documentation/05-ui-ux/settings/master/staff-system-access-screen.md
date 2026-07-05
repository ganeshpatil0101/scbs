# Screen Spec — Staff & System Access (सेटिंग्ज > मास्टर > कर्मचारी व सिस्टम प्रवेश)

> **Consolidates:** [new-employee-screen.md](new-employee-screen.md) + [new-user-screen.md](new-user-screen.md)

## Purpose

Single wizard for registering a staff member/director **and** granting system login, branch rights, and role permissions. Replaces separate New Employee and New User screens.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | कर्मचारी व सिस्टम प्रवेश | Staff & System Access |
| Breadcrumb | डॅशबोर्ड > सेटिंग्ज > मास्टर > कर्मचारी व सिस्टम प्रवेश | Dashboard > Settings > Master > Staff & System Access |
| Parent Module | मास्टर | Master |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | कर्मचारी माहिती | Employee Details |
| 2 | लॉगीन व पासवर्ड | Login & Password |
| 3 | शाखा अधिकार | Branch Rights |
| 4 | युजर रोल | User Role |

---

## Tab 1: कर्मचारी माहिती (Employee Details)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | ग्राहक | Customer | Autocomplete | Yes | Single control: ID + name. Replaces separate Customer No. + Customer Name |
| 2 | हुद्दा | Designation | Dropdown | Yes | `निवडा`, `मुख्य कार्यकारी अधिकारी`, `अध्यक्ष`, `उपाध्यक्ष`, `संचालक` |
| 3 | संचालक | Director | Radio | No | Employee type. Default selected |
| 4 | कर्मचारी | Employee | Radio | No | Employee type |

**Removed:** `Is Employee Currently in Service?` — defaults to Yes at creation; editable only in edit mode.

---

## Tab 2: लॉगीन व पासवर्ड (Login & Password)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 5 | लॉगीन नाव | Login Name | Textbox | Yes | — |
| 6 | पासवर्ड | Password | Textbox | Yes | Masked |
| 7 | पडताळणी पासवर्ड | Confirm Password | Textbox | Yes | Masked |
| 8 | स्थिती | Status | Dropdown | Yes | Default: `सक्रिय`. Values: `सक्रिय`, `निष्क्रिय`, `स्थगित`, `सिस्टीम स्थगित` |
| 9 | सुपर युजर | Super User | Checkbox | No | — |

**Auto-fill (hidden):** User Type defaults to `सोसायटी` (Society) — not shown.

### Section: प्रगत सेटिंग्ज (Advanced Settings) — collapsed by default

| # | Marathi Label | English Label | Type | Required | Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 10 | रोख भरणा व्हाउचर मर्यादा | Cash Deposit Voucher Limit | Textbox | No | — |
| 11 | रोख भरणा व्हाउचर पासिंग मर्यादा | Cash Deposit Voucher Passing Limit | Textbox | No | — |
| 12 | शाखा अंतर्गत व्यवहार | Intra-branch Transaction | Checkbox | No | When checked, enables limits below |
| 13 | शाखा अंतर्गत पावती मर्यादा | Intra-branch Receipt Limit | Textbox | No | Visible when #12 checked |
| 14 | शाखा अंतर्गत देय मर्यादा | Intra-branch Payable Limit | Textbox | No | Visible when #12 checked |

**Removed:** Director/Staff radio at top of old New User screen (duplicate of Tab 1).

---

## Tab 3: शाखा अधिकार (Branch Rights)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 15 | संघटना | Organization | Dropdown | Yes | Society name |
| 16 | शाखा निवडा | Select Branch | Autocomplete | Yes | `1 — Branch 1`, etc. |

**Action:** `+ टाका` (Add) — add row to rights grid.

### Rights Grid

Columns: निवडा, अ.क्र., संघटना, शाखा नाव.

**Action:** `काढा` (Remove).

---

## Tab 4: युजर रोल (User Role)

See [user-role-screen.md](user-role-screen.md) — same permission matrix embedded as final wizard step.

---

## Actions

| Button | Marathi | English |
| :--- | :--- | :--- |
| Save | जतन करा | Save |
| Reset | रीसेट | Reset |
| Back | मागे | Back (tab 2+) |
| Next | पुढे | Next (tab 1–3) |

---

## Related Documents

- [overview.md](overview.md)
- [ux-optimization.md](../ux-optimization.md)
- [user-role-screen.md](user-role-screen.md)
- [../../shared/ui-simplification-patterns.md](../../shared/ui-simplification-patterns.md)
- [../../shared/entity-autocomplete-pattern.md](../../shared/entity-autocomplete-pattern.md)
