# Screen Spec — New Other Account (ग्राहक > नवीन इतर खाते)

## Purpose

UI specification for opening a new "other" account for an existing customer. Customer search precedes account-type selection.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | नवीन इतर खाते | New Other Account |
| Breadcrumb | डॅशबोर्ड > ग्राहक > नवीन इतर खाते | Dashboard > Customer > New Other Account |
| Parent Module | ग्राहक | Customer |

## Reference Screenshots

| Screenshot File | Section |
| :--- | :--- |
| `screenshots/grahak_khatedar/डॅशबोर्ड-ग्राहक-नवीन इतर खाते.png` | Filter section with Status dropdown open |

---

## Filter Section

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | संघटना | Organization | Dropdown | Yes | Society name |
| 2 | शाखा कोड | Branch Code | Textbox | No | Read-only; e.g. `1` |
| 3 | शाखा | Branch | Dropdown | No | e.g. कोतोली मुख्य कार्यालय |
| 4 | ग्राहकाचे नाव | Customer Name | Textbox | No | — |
| 5 | ग्राहक क्र. (पासून) | Customer No. (From) | Textbox | No | — |
| 6 | ग्राहक क्र. (पर्यंत) | Customer No. (To) | Textbox | No | — |
| 7 | स्थिती | Status | Dropdown | No | `सर्व` (All), `चालू` (Active), `स्थगित` (Suspended), `मृत` (Deceased), `निलंबित` (Suspended/Barred), `निवृत्त` (Retired), `वैद्यकीय` (Medical), `काढला` (Removed) |
| 8 | ॲडव्हान्स शोध | Advanced Search | Link | No | Expands extra filters |
| 9 | ग्राहकानुसार खाते | Account by Customer | Dropdown | Yes | Default: `निवडा` (Select). Values: `TODO` |

**Action:** `दाखवा` (Show) — search customers matching filters.

---

## Customer Results Grid

Same column set as [customer-list-screen.md](customer-list-screen.md) minus consent/Aadhaar/PAN token columns (18 columns visible):

निवडा, अनु. क्र., ग्राहक क्र., नाव, पत्ता, जिल्हा, तालुका, शहर, मोबाईल क्रमांक, लेजर फोलिओ क्रमांक, शाखा क्रमांक, कर्मचारी कोड, एसएमएस अलर्ट, व्हाट्सअप अलर्ट, पॅन टोकन, पॅन पडताळणी दिनांक, पॅन आधार लिंकेज, कर्ज जोखिम मर्यादा.

**Select all:** `सर्व निवडा` checkbox above grid.

---

## Related Documents

- [overview.md](overview.md)
- [customer-list-screen.md](customer-list-screen.md)
- [other-account-registration-screen.md](other-account-registration-screen.md)
