# Screen Spec — Customer List (ग्राहक > ग्राहक यादी)

## Purpose

UI specification for searching and listing customers. Intended for AI agents implementing this screen.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | ग्राहक यादी | Customer List |
| Breadcrumb | डॅशबोर्ड > ग्राहक > ग्राहक यादी | Dashboard > Customer > Customer List |
| Parent Module | ग्राहक | Customer |

## Reference Screenshots

| Screenshot File | Section |
| :--- | :--- |
| `screenshots/grahak_khatedar/डॅशबोर्ड-ग्राहक-ग्राहक यादी.png` | Full screen with Masters Passing dropdown open |

---

## Filter Section

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | संस्थेचे नाव | Organization Name | Dropdown | Yes | e.g. श्रद्धा नागरी सहकारी पतसंस्था मर्यादित- कोतोली |
| 2 | शाखा निवडा | Select Branch | Autocomplete | No | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 3 | शाखा | Branch | Dropdown | No | e.g. कोतोली मुख्य कार्यालय |
| 4 | ग्राहकाचे नाव | Customer Name | Textbox | No | — |
| 5 | ग्राहक क्र. (पासून) | Customer No. (From) | Textbox | No | — |
| 6 | ग्राहक क्र. (पर्यंत) | Customer No. (To) | Textbox | No | — |
| 7 | स्थिती | Status | Dropdown | No | Default: `चालू` (Active). Other values: `TODO` |
| 8 | मास्टर्स पासिंग | Masters Passing | Dropdown | No | `सर्व` (All), `पास` (Pass), `पास नसलेले` (Not Passed), `रद्द` (Cancelled) |

**Links:** `अॅडव्हान्स शोध` (Advance Search) — expands additional filters (not shown in screenshot).

**Action:** `दाखवा` (Show) — blue button with search icon; runs filter query.

---

## Results Grid

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

## Related Documents

- [overview.md](overview.md)
- [new-customer-screen.md](new-customer-screen.md)
- [new-other-account-screen.md](new-other-account-screen.md)
- [other-account-registration-screen.md](other-account-registration-screen.md)
- [../membership/new-membership-screen.md](../membership/new-membership-screen.md)
