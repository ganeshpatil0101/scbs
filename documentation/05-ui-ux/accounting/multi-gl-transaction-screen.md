# Screen Spec — Multiple GL Transaction (लेखा > एकाधिक जीएल व्यवहार)

## Purpose

UI specification for posting transactions across multiple GL heads in one voucher.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | एकाधिक जीएल व्यवहार | Multiple GL Transaction |
| Breadcrumb | डॅशबोर्ड > लेखा > एकाधिक जीएल व्यवहार | Dashboard > Accounting > Multiple GL Transaction |
| Parent Module | लेखा | Accounting |

## Reference Media

| File | Section |
| :--- | :--- |
| `screenshots/lekha/डॅशबोर्ड-लेखा-एकाधिक जीएल व्यवहार.mp4` | Entry + current transaction grid |

Extracted frames: `screenshots/lekha/multi-gl-frames/`.

---

## Account Lookup

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | शाखा निवडा | Select Branch | Autocomplete | No | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 2 | जी.एल. निवडा | Select GL | Autocomplete | No | Sample: `38 — Saving`, `91 — FD`, `42 — Loan`. Enter resolves by ID or name; shows display name |
| 3 | खातेधारक निवडा | Select Account Holder | Autocomplete | No | Sample: `101 — Account Holder 1`, `102 — Account Holder 2`, `103 — Account Holder 3`. Enter resolves by ID or name; shows display name |
| 4 | न वटलेली शिल्लक | Uncleared Balance | Textbox | No | Read-only |
| 5 | लेजर शिल्लक | Ledger Balance | Label | No | — |
| 6 | अक्षरी रक्कम | Amount in Words | Textbox | No | Read-only |

**Utility buttons:** `खाते माहिती`, `खात्याचा हिशोब`, `पासबुक`, `चौकशी`.

## Transaction Entry

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 7 | व्यवहार प्रकार | Transaction Type | Radio | No | `नावे` (Debit) / `जमा` (Credit) |
| 8 | रक्कम रु. | Amount (Rs.) | Textbox | Yes | — |

**Action:** `+ भरा` (Fill/Add).

## Current Transaction Grid (करंट ट्रांझॅक्शन)

Columns: निवडा, अनु. क्र, जी.एल. हेड, खाते क्रमांक, खातेधारक, शिल्लक, नावे, जमा.

**Footer fields:**

| Marathi Label | English Label | Type | Required | Values / Notes |
| :--- | :--- | :--- | :---: | :--- |
| एकूण नावे | Total Debit | Label | — | Read-only |
| एकूण जमा | Total Credit | Label | — | Read-only |
| फरक रक्कम | Difference Amount | Label | — | Read-only |
| व्यवहार मोड | Transaction Mode | Dropdown | Yes | `रोख` (Cash), `चेक` (Cheque) — v1: receipt/issue recording only, no live clearing |
| व्हाउचर तपशील | Voucher Details | Textarea | No | — |

**Links:** `केवायसी माहिती खात्याचा तपशील`, `व्यवहार तपशील`, `लेजर`.

**Actions:** `काढा`, `पूर्ण`, `पूर्ववत`, `वर`.

---

## Mockup

| Property | Value |
| :--- | :--- |
| HTML mockup | [mockups/accounting/multi-gl-transaction-screen/index.html](../mockups/accounting/multi-gl-transaction-screen/index.html) |
| Review guide | [mockups/accounting/multi-gl-transaction-screen/README.md](../mockups/accounting/multi-gl-transaction-screen/README.md) |
| Status | Draft |

## Related Documents

- [overview.md](overview.md)
- [jama-screen.md](jama-screen.md)
- [nave-screen.md](nave-screen.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
