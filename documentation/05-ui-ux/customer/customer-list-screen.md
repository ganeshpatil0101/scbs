# Screen Spec — Customer List (ग्राहक > ग्राहक यादी)

## Purpose

UI specification for searching and listing customers. Intended for AI agents implementing this screen.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | ग्राहक यादी | Customer List |
| Breadcrumb | डॅशबोर्ड > ग्राहक > ग्राहक यादी | Dashboard > Customer > Customer List |
| Parent Module | ग्राहक | Customer |

**Auto-fill (header):** `संस्था` (Organization) — read-only `Label` from tenant session; not repeated in filter bar.

## Reference Screenshots

| Screenshot File | Section |
| :--- | :--- |
| `screenshots/grahak_khatedar/डॅशबोर्ड-ग्राहक-ग्राहक यादी.png` | Full screen with Masters Passing dropdown open |

---

## Filter Section

### Section: प्राथमिक शोध (Primary Search)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा निवडा | Select Branch | Autocomplete | No | Enter resolves by ID or name; e.g. `1 — Branch 1`. Replaces legacy Branch Autocomplete + Branch Dropdown pair |
| 2 | ग्राहकाचे नाव | Customer Name | Textbox | No | — |
| 3 | ग्राहक क्र. (पासून) | Customer No. (From) | Textbox | No | Range filter |
| 4 | ग्राहक क्र. (पर्यंत) | Customer No. (To) | Textbox | No | Range filter |
| 5 | स्थिती | Status | Dropdown | No | Default: `चालू` (Active). Values: `चालू`, `बंद` (Closed), `स्थगित` (Suspended), `मृत` (Deceased), `निलंबित` (Barred), `निवृत्त` (Retired), `वैद्यकीय` (Medical), `काढला` (Removed) |

**Link:** `अॅडव्हान्स शोध` (Advance Search) — expands additional filters.

**Action:** `दाखवा` (Show) — blue button with search icon; runs filter query.

### Section: अॅडव्हान्स शोध (Advance Search)

> Collapsed by default. Visible when Advance Search link expanded.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 6 | मास्टर्स पासिंग | Masters Passing | Dropdown | No | `सर्व` (All), `पास` (Pass), `पास नसलेले` (Not Passed), `रद्द` (Cancelled) |

---

## Results Grid

### Default columns

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | अनु. क्र. | Sr. No. |
| 3 | ग्राहक क्र. | Customer No. |
| 4 | नाव | Name |
| 5 | पत्ता | Address |
| 6 | जिल्हा | District |
| 7 | तालुका | Taluka |
| 8 | शहर | City |
| 9 | मोबाइल क्रमांक | Mobile Number |

### Additional columns (Details / Export / column picker)

> Not shown in the default grid. Available via `तपशील` (Details), `निर्यात करा` (Export), or optional column picker.

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 10 | लेजर फोलिओ क्रमांक | Ledger Folio Number |
| 11 | शाखा क्रमांक | Branch Number |
| 12 | कर्मचारी कोड | Employee Code |
| 13 | एसएमएस अलर्ट | SMS Alert |
| 14 | व्हाट्सअप अलर्ट | WhatsApp Alert |
| 15 | संमती दिनांक | Consent Date |
| 16 | संमती संदेश | Consent Message |
| 17 | निधी हस्तांतरण मर्यादा | Fund Transfer Limit |
| 18 | आधार टोकन | Aadhaar Token |
| 19 | आधार पडताळणी दिनांक | Aadhaar Verification Date |
| 20 | पॅन टोकन | PAN Token |
| 21 | पॅन पडताळणी दिनांक | PAN Verification Date |
| 22 | पॅन आधार लिंकेज | PAN Aadhaar Linkage |
| 23 | कर्ज जोखिम मर्यादा | Loan Risk Limit |

**Grid actions:** `तपशील` (Details), `निर्यात करा` (Export) — floating buttons on the right.

---

## Mockup

| Property | Value |
| :--- | :--- |
| HTML mockup | [mockups/customer/customer-list-screen/index.html](../mockups/customer/customer-list-screen/index.html) |
| Review guide | [mockups/customer/customer-list-screen/README.md](../mockups/customer/customer-list-screen/README.md) |
| Stack | Tailwind CSS v4 (CDN), Marathi labels only |
| Status | Draft — pending bank user review |

---

## Related Documents

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [new-customer-screen.md](new-customer-screen.md)
- [other-account-management-screen.md](other-account-management-screen.md)
- [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
- [../membership/new-membership-screen.md](../membership/new-membership-screen.md)
