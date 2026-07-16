# Screen Spec — Accounting Transfer (लेखा > ट्रान्सफर)

## Purpose

UI specification for GL account-to-account transfer (debit one side, credit other).

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | ट्रान्सफर | Transfer |
| Breadcrumb | डॅशबोर्ड > लेखा > ट्रान्सफर | Dashboard > Accounting > Transfer |
| Parent Module | लेखा | Accounting |

## Reference Media

| File | Section |
| :--- | :--- |
| `screenshots/lekha/डॅशबोर्ड-लेखा-ट्रान्सफर.mp4` | Full screen |

Extracted frames: `screenshots/lekha/transfer-frames/`.

---

## Section: खाते व्यवहार (Account Transaction)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | चलन क्रमांक | Challan Number | Textbox | No | Read-only |

## Section: नावे खाते (Debit Account)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 2 | शाखा निवडा | Select Branch | Autocomplete | Yes | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 3 | जी.एल. निवडा | Select GL | Autocomplete | Yes | Sample: `38 — Saving`, `91 — FD`, `42 — Loan`. Enter resolves by ID or name; shows display name |
| 4 | खातेधारक निवडा | Select Account Holder | Autocomplete | Yes | Sample: `101 — Account Holder 1`, `102 — Account Holder 2`, `103 — Account Holder 3`. Enter resolves by ID or name; shows display name |
| 5 | शिल्लक | Balance | Textbox | No | Read-only |
| 6 | न वटलेली शिल्लक | Uncleared Balance | Textbox | No | Read-only |
| 7 | व्यवहार रक्कम (रू.) | Transaction Amount (Rs.) | Textbox | Yes | — |

**Action:** `नावे ₹` — add debit row.

## Section: जमा खाते (Credit Account)

Mirrors debit-side entry pattern. After debit row is added, credit account is entered here.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 8 | शाखा निवडा | Select Branch | Autocomplete | Yes | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 9 | जी.एल. निवडा | Select GL | Autocomplete | Yes | Sample: `38 — Saving`, `91 — FD`, `42 — Loan`. Enter resolves by ID or name; shows display name |
| 10 | खातेधारक निवडा | Select Account Holder | Autocomplete | Yes | Sample: `101 — Account Holder 1`, `102 — Account Holder 2`, `103 — Account Holder 3`. Enter resolves by ID or name; shows display name |
| 11 | शिल्लक | Balance | Textbox | No | Read-only |
| 12 | न वटलेली शिल्लक | Uncleared Balance | Textbox | No | Read-only |
| 13 | व्यवहार रक्कम (रू.) | Transaction Amount (Rs.) | Textbox | Yes | — |

**Action:** `जमा ₹` — add credit row.

## Transfer Grid

Columns: निवडा, अनु. क्र, जी.एल., खाते क्रमांक, खाते धारकाचे नाव, शिल्लक, व्यवहार रक्कम.

**Actions:** `काढा`, `वर`.

---

## Mockup

| Property | Value |
| :--- | :--- |
| HTML mockup | [mockups/accounting/transfer-screen/index.html](../mockups/accounting/transfer-screen/index.html) |
| Review guide | [mockups/accounting/transfer-screen/README.md](../mockups/accounting/transfer-screen/README.md) |
| Status | Draft |

## Related Documents

- [overview.md](overview.md)
- [jama-screen.md](jama-screen.md)
- [nave-screen.md](nave-screen.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
