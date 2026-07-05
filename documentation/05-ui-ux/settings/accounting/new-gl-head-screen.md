# Screen Spec — New GL Head (सेटिंग > लेखा > नवीन जी. एल. हेड)

> **Superseded (2026-07-05):** Consolidated into [gl-account-setup-screen.md](gl-account-setup-screen.md). Retained for field reference only.

## Purpose

UI specification for creating a new GL (General Ledger) head. Intended for AI agents implementing this screen.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | नवीन जी. एल. हेड | New GL Head |
| Breadcrumb | डॅशबोर्ड > सेटिंग > लेखा > नवीन जी. एल. हेड | Dashboard > Settings > Accounting > New GL Head |
| Parent Module | लेखा | Accounting |

## Reference Media

| File | Section |
| :--- | :--- |
| `screenshots/settings/डॅशबोर्ड-सेटिंग-लेखा-नवीन जी. एल. हेड.mp4` | Account Group dropdown + full form |

Extracted frames: `screenshots/settings/new-gl-head-frames/`.

---

## Primary Fields

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | खाते गट | Account Group | Dropdown | Yes | See [Account Group Values](#account-group-values) below |
| 2 | खाते प्रकार | Account Type | Dropdown | Yes | Default: `इतर` (Other). |
| 3 | जी. एल. हेड क्र. | GL Head No. | Textbox | Yes | Auto-generated (e.g. `163`) |
| 4 | जी. एल. हेडचे नाव | GL Head Name | Textbox | Yes | — |
| 5 | संक्षिप्त नाव | Short Name | Textbox | No | — |
| 6 | युनिकोड नाव | Unicode Name | Textbox | No | — |
| 7 | स्थिती | Status | Dropdown | Yes | Default: `चालू` (Active), `बंद` (Inactive), `स्थगित` (Stop)  |
| 8 | प्रारंभ दिनांक | Start Date | Date | Yes | System date |

---

## Section: प्राथमिक गट (Primary Group)

### Balance Type (शिल्लक प्रकार)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 9 | जमा | Credit | Radio | No | — |
| 10 | नावे | Debit | Radio | No | — |
| 11 | इतर | Other | Radio | No | — |

### Account Category

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 12 | सामान्य खाते | General Account | Radio | No | — |
| 13 | शाखा खाते | Branch Account | Radio | No | — |
| 14 | सभासदाप्रमाणे खाते | Member-like Account | Radio | No | — |
| 15 | कॉन्ट्रा | Contra | Checkbox | No | — |

### Organization / Branch

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 16 | संघटना | Organization | Dropdown | No | Society name; read-only when member account selected |
| 17 | शाखा निवडा | Select Branch | Autocomplete | No | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |

## Actions

| Button | Marathi | English |
| :--- | :--- | :--- |
| Save | पूर्ण | Complete |
| Reset | पूर्ववत | Revert |

---

## Account Group Values

Captured from video frames `f_000`–`f_010` (scrollable list; combined):

| Marathi | English |
| :--- | :--- |
| इतर भत्ता | Other Allowance |
| इतर येणी व तरतूदी | Other Receivables & Provisions |
| कर्ज | Loan |
| कर्जावरील व्याज | Interest on Loan |
| गुंतवणूक | Investment |
| गुंतवणुकीवरील व्याज | Interest on Investment |
| चालू तोटा | Current Loss |
| चालू नफा | Current Profit |
| ठेवी | Deposits |
| ठेवीवरील व्याज | Interest on Deposits |
| डिपॉझिट देणे | Deposit Payable |
| डिपॉझिट येणे | Deposit Receivable |
| तरतूद खर्च | Provision Expense |
| तोटा | Loss |
| देणे व्याज | Interest Payable |
| नफा | Profit |
| पगार कपात | Salary Deduction |
| पगार मिळकत | Salary Income |
| प्रत्यक्ष खर्च | Direct Expense |
| प्रोजेक्ट खर्च | Project Expense |
| प्रोजेक्ट जमा | Project Income |
| फंड ट्रान्सफर | Fund Transfer |
| बँक इंटरेस्ट म्हणून दिले | Paid as Bank Interest |
| बँक कर्ज | Bank Loan |
| बँकेचे व्याज मिळाले | Bank Interest Received |
| बँक ओव्हरड्राफ्ट | Bank Overdraft |
| मालमत्ता | Asset |
| येणे व्याज | Interest Receivable |
| राखीव व इतर निधी | Reserve and Other Funds |
| रोख व बँकेतील शिल्लक | Cash and Bank Balance |
| लाभांश | Dividend |
| वसूल भाग भांडवल | Paid-up Share Capital |
| व्यवस्थापकीय खर्च | Administrative Expense |
| शाखा गुंतवणूक | Branch Investment |
| शाखा देणी | Branch Liabilities |
| शाखा येणे | Branch Receiviable |
| सर्वसाधारण खर्च | Overall Expenses |

---

## Mockup

| Property | Value |
| :--- | :--- |
| HTML mockup | [mockups/settings/accounting/new-gl-head-screen/index.html](../../mockups/settings/accounting/new-gl-head-screen/index.html) |
| Review guide | [mockups/settings/accounting/new-gl-head-screen/README.md](../../mockups/settings/accounting/new-gl-head-screen/README.md) |
| Stack | Tailwind CSS v4 (CDN), Marathi labels only |
| Status | Draft — pending bank user review |

---

## Related Documents

- [overview.md](overview.md)
- [new-gl-group-screen.md](new-gl-group-screen.md)
- [../schemes/overview.md](../schemes/overview.md)
