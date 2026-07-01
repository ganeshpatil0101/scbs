# Screen Spec — Other Account Registration (ग्राहक > इतर खाते नोंदणी)

## Purpose

UI specification for bulk registration of "other" accounts (dividend, deposit, fee accounts) for customers. Intended for AI agents implementing this screen.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | इतर खाते नोंदणी | Other Account Registration |
| Breadcrumb | डॅशबोर्ड > ग्राहक > इतर खाते नोंदणी | Dashboard > Customer > Other Account Registration |
| Parent Module | ग्राहक | Customer |

## Reference Media

| File | Section |
| :--- | :--- |
| `screenshots/grahak_khatedar/डॅशबोर्ड-ग्राहक-इतर खाते नोंदणी.mp4` | Full screen; dropdown values |

Extracted frames: `screenshots/grahak_khatedar/other-account-reg-frames/`.

---

## Filter Section

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | संस्थेचे नाव | Organization Name | Dropdown | Yes | Society name |
| 2 | शाखा निवडा | Select Branch | Autocomplete | Yes | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 3 | शाखा | Branch | Dropdown | No | e.g. कोतोली मुख्य कार्यालय |
| 4 | ग्राहकानुसार खाते | Account by Customer | Dropdown | Yes | `ब वर्ग देणे लाभांश` (Class B Dividend Payable), `अनामत खाते` (Deposit Account), `प्रवेश फी` (Entrance Fee), `नोकर पगार खर्च` (Staff Salary Expense) |
| 5 | स्थिती | Status | Dropdown | Yes | Default: `चालू` (Active). Other values: `TODO` |
| 6 | ग्राहक क्र. (पासून) | Customer No. (From) | Textbox | No | — |
| 7 | ग्राहक क्र. (पर्यंत) | Customer No. (To) | Textbox | No | — |

**Action:** `दाखवा` (Show) — load matching customers/accounts.

---

## Results Grid

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | अनु.क्र. | Sr. No. |
| 3 | ग्राहक क्र. | Customer No. |
| 4 | खाते क्रमांक | Account Number |
| 5 | नाव | Name |
| 6 | शाखा | Branch |

**Select all:** `सर्व निवडा` checkbox.

**Grid action:** `काढा` (Remove) — delete selected registrations.

---

## Account Status (Registration Action)

Visible when registering accounts (video frame ~7.5 s):

| Field | Marathi | English | Type | Values |
| :--- | :--- | :--- | :--- | :--- |
| खाते स्थिती | Account Status | Dropdown | `चालू` (Active), `बंद` (Closed), `स्थगित` (Suspended) |

---

## Related Documents

- [overview.md](overview.md)
- [new-other-account-screen.md](new-other-account-screen.md)
- [../settings/membership/dividend-calculation-screen.md](../settings/membership/dividend-calculation-screen.md)
