# Screen Spec — Other Account Management (ग्राहक > इतर खाते व्यवस्थापन)

> **Consolidates:** [new-other-account-screen.md](new-other-account-screen.md) + [other-account-registration-screen.md](other-account-registration-screen.md)

## Purpose

Single screen for opening and managing “other” accounts (dividend payable, deposit, entrance fee, staff salary expense) for customers. Tab 1 opens a new account for one selected customer; Tab 2 lists and maintains registrations in bulk.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | इतर खाते व्यवस्थापन | Other Account Management |
| Breadcrumb | डॅशबोर्ड > ग्राहक > इतर खाते व्यवस्थापन | Dashboard > Customer > Other Account Management |
| Parent Module | ग्राहक | Customer |

**Auto-fill (header):** `संस्था` (Organization) — read-only `Label` from tenant session; not repeated in filter bars.

## Tabs

| # | Marathi Tab | English Tab | Replaces |
| :---: | :--- | :--- | :--- |
| 1 | नवीन खाते | New Account | New Other Account |
| 2 | नोंदणी यादी | Registration List | Other Account Registration |

## Reference Media

| File | Tab |
| :--- | :--- |
| `screenshots/grahak_khatedar/डॅशबोर्ड-ग्राहक-नवीन इतर खाते.png` | Tab 1 |
| `screenshots/grahak_khatedar/डॅशबोर्ड-ग्राहक-इतर खाते नोंदणी.mp4` | Tab 2 |

Extracted frames: `screenshots/grahak_khatedar/other-account-reg-frames/`.

---

## Tab 1: नवीन खाते (New Account)

Pick one customer, choose account type, then open the account.

### Section: प्राथमिक शोध / निवड (Primary Select)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा निवडा | Select Branch | Autocomplete | No | Enter resolves by ID or name; e.g. `1 — Branch 1`. See [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |
| 2 | ग्राहक निवडा | Select Customer | Autocomplete | Yes | Enter resolves by customer no. or name; e.g. `661 — Customer 1`. Replaces Customer Name + Customer No. range |
| 3 | ग्राहकानुसार खाते | Account by Customer | Dropdown | Yes | Default: `निवडा`. Values: `ब वर्ग देणे लाभांश` (Class B Dividend Payable), `अनामत खाते` (Deposit Account), `प्रवेश फी` (Entrance Fee), `नोकर पगार खर्च` (Staff Salary Expense) |
| 4 | स्थिती | Status | Dropdown | No | Default: `चालू`. Values: `सर्व`, `चालू`, `स्थगित`, `मृत`, `निलंबित`, `निवृत्त`, `वैद्यकीय`, `काढला` — filters customer lookup when used |

**Actions:** `दाखवा` (Show — optional refresh of customer context), `जतन करा` / `पूर्ण` (Complete — open account for selected customer + type).

### Section: Selected Customer Summary (read-only)

Shown after Customer Autocomplete resolves:

| # | Marathi Label | English Label | Type | Notes |
| :---: | :--- | :--- | :--- | :--- |
| 5 | ग्राहक क्र. | Customer No. | Label | From resolved customer |
| 6 | नाव | Name | Label | From resolved customer |
| 7 | पत्ता | Address | Label | From resolved customer |
| 8 | मोबाईल क्रमांक | Mobile Number | Label | From resolved customer |

---

## Tab 2: नोंदणी यादी (Registration List)

Bulk list, status update, and remove for other-account registrations.

### Section: प्राथमिक शोध (Primary Search)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 9 | शाखा निवडा | Select Branch | Autocomplete | Yes | Enter resolves by ID or name |
| 10 | ग्राहकानुसार खाते | Account by Customer | Dropdown | Yes | `ब वर्ग देणे लाभांश`, `अनामत खाते`, `प्रवेश फी`, `नोकर पगार खर्च` |
| 11 | स्थिती | Status | Dropdown | Yes | Default: `चालू`. Values: `चालू`, `बंद`, `स्थगित` |
| 12 | ग्राहक क्र. (पासून) | Customer No. (From) | Textbox | No | Range filter for bulk list |
| 13 | ग्राहक क्र. (पर्यंत) | Customer No. (To) | Textbox | No | Range filter for bulk list |

**Action:** `दाखवा` (Show).

### Section: Results Grid

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | अनु.क्र. | Sr. No. |
| 3 | ग्राहक क्र. | Customer No. |
| 4 | खाते क्रमांक | Account Number |
| 5 | नाव | Name |
| 6 | शाखा | Branch |

**Select all:** `सर्व निवडा`.

**Grid action:** `काढा` (Remove) — delete selected registrations (confirm dialog).

### Section: खाते स्थिती (Account Status — Update)

> **Visible:** When one or more grid rows selected.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 14 | खाते स्थिती | Account Status | Dropdown | Yes | `चालू` (Active), `बंद` (Closed), `स्थगित` (Suspended) |

**Actions:** `जतन करा` (Save status), `पूर्ववत` (Revert).

---

## Screen Actions (global)

| Button | Marathi | English | Tab |
| :--- | :--- | :--- | :---: |
| Show | दाखवा | Show | 1, 2 |
| Complete / Save | पूर्ण / जतन करा | Complete / Save | 1, 2 |
| Remove | काढा | Remove | 2 |
| Revert | पूर्ववत | Revert | 2 |

---

## Mockup

| Property | Value |
| :--- | :--- |
| HTML mockup | [mockups/customer/other-account-management-screen/index.html](../mockups/customer/other-account-management-screen/index.html) |
| Review guide | [mockups/customer/other-account-management-screen/README.md](../mockups/customer/other-account-management-screen/README.md) |
| Stack | Tailwind CSS v4 (CDN), Marathi labels only |
| Status | Draft — pending bank user review |

---

## Related Documents

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [customer-list-screen.md](customer-list-screen.md)
- [new-customer-screen.md](new-customer-screen.md)
- [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
- [../settings/membership/membership-configuration-screen.md](../settings/membership/membership-configuration-screen.md)
