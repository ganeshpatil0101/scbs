# Screen Spec — Nave / Debit (लेखा > नावे)

## Purpose

UI specification for accounting debit (payment) entries.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | नावे | Debit / Payment |
| Breadcrumb | डॅशबोर्ड > लेखा > नावे | Dashboard > Accounting > Debit |
| Parent Module | लेखा | Accounting |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | पेमेंट | Payment |
| 2 | चेक माहिती | Cheque Information |

## Reference Media

| File | Section |
| :--- | :--- |
| `screenshots/lekha/डॅशबोर्ड-लेखा-नावे.mp4` | Tab 1 — Payment |

Extracted frames: `screenshots/lekha/nave-frames/`.

Same interest-transaction warning as [jama-screen.md](jama-screen.md).

---

## Tab 1: पेमेंट (Payment)

### Payment Source

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | व्हाउचर क्र. | Voucher No. | Textbox | No | Read-only; e.g. `42` |
| 2 | रोख / बँक | Cash / Bank | Radio | No | Default: `रोख`. Controls Tab 2 enable/disable — see **Cross-Tab Behavior** below |
| 3 | बँक/कॅश निवडा | Select Bank/Cash | Dropdown | Yes | **When `रोख`:** `रोख शिल्लक` (Cash Balance). **When `बँक`:** loaded from Bank Master — sample: `SBI`, `HDFC`, `ICICI` |
| 4 | शिल्लक (नावे) | Balance (Debit) | Textbox | No | Read-only |
| 5 | तपशील | Details | Textbox | No | — |

### Section: नावे होणारी खाती (Accounts to be Debited)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 6 | शाखा निवडा | Select Branch | Autocomplete | Yes | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 7 | जी.एल. निवडा | Select GL | Autocomplete | Yes | Sample: `38 — Saving`, `91 — FD`, `42 — Loan`. Enter resolves by ID or name; shows display name |
| 8 | खातेधारक निवडा | Select Account Holder | Autocomplete | Yes | Sample: `101 — Account Holder 1`, `102 — Account Holder 2`, `103 — Account Holder 3`. Enter resolves by ID or name; shows display name |
| 9 | शिल्लक | Balance | Textbox | No | Read-only |
| 10 | न वाटलेली शिल्लक | Uncleared Balance | Textbox | No | Read-only |

### Section: व्यवहार (Transaction)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 11 | नावे / जमा | Debit / Credit | Radio | Yes | Default: `नावे` |
| 12 | व्यवहार रक्कम (रु.) | Transaction Amount (Rs.) | Textbox | Yes | — |

**Action:** `नावे` — add to grid. **Grid actions:** `निर्यात`, `काढा`, `वर`.

---

## Cross-Tab Behavior

| Tab 1 — `रोख / बँक` (field 2) | Tab 2 — चेक माहिती |
| :--- | :--- |
| `रोख` (Cash) selected | All Tab 2 fields **disabled** |
| `बँक` (Bank) selected | All Tab 2 fields **enabled** |

Same rule as [jama-screen.md](jama-screen.md#cross-tab-behavior).

---

## Tab 2: चेक माहिती (Cheque Information)

Enabled only when Tab 1 field 2 = `बँक`. All fields disabled when Tab 1 field 2 = `रोख`. Field set matches Jama Tab 2 (Instrument Details).

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 13 | धनादेश प्रकार निवडा | Select Cheque Type | Dropdown | No | `स्लिप` (Slip) |
| 14 | चेक रक्कम (रु.) | Cheque Amount (Rs.) | Textbox | No | Read-only |
| 15 | रक्कम अक्षरी | Amount in Words | Textbox | No | Read-only |
| 16 | चेक दिनांक | Cheque Date | Date | Yes | — |
| 17 | चेक क्र. | Cheque No. | Textbox | Yes | — |
| 18 | नाव | Name | Textbox | Yes | — |
| 19 | बँक निवडा | Select Bank | Dropdown | Yes | `SBI`, `HDFC`, `ICICI`, `Bank of Maharashtra`, `Other` |
| 20 | बँक शाखा | Bank Branch | Textbox | No | — |
| 21 | ड्रॉन ऑन बँक | Drawn on Bank | Textbox | No | — |
| 22 | ड्रॉन ऑन ब्रांच | Drawn on Branch | Textbox | No | — |
| 23 | अंतर्गत चेक नंबर | Internal Cheque Number | Textbox | No | Read-only |

**Navigation:** `मागे`, `पुढे`, `पूर्ण`, `पूर्ववत`.

---

## Mockup

| Property | Value |
| :--- | :--- |
| HTML mockup | [mockups/accounting/nave-screen/index.html](../mockups/accounting/nave-screen/index.html) |
| Review guide | [mockups/accounting/nave-screen/README.md](../mockups/accounting/nave-screen/README.md) |
| Status | Draft |

## Related Documents

- [overview.md](overview.md)
- [jama-screen.md](jama-screen.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
