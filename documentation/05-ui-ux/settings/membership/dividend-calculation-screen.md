# Screen Spec — Dividend Calculation (सेटिंग्ज > सभासदत्व > लाभांश आकारणी)

> **Superseded (2026-07-05):** Consolidated into [membership-configuration-screen.md](membership-configuration-screen.md). Retained for field reference only.

## Purpose

UI specification for calculating member dividends. Intended for AI agents implementing this screen.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | लाभांश आकारणी | Dividend Calculation |
| Breadcrumb | डॅशबोर्ड > सेटिंग्ज > सभासदत्व > लाभांश आकारणी | Dashboard > Settings > Membership > Dividend Calculation |
| Parent Module | सभासदत्व (Settings) | Membership (Settings) |

## Reference Screenshots

| Screenshot File | Section |
| :--- | :--- |
| `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-सभासदत्व-लाभांश आकारणी.png` | Full screen |

---

## Filter Section

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | सभासद | Member | Radio | No | Default selected |
| 2 | नाममात्र सभासद | Nominal Member | Radio | No | — |
| 3 | शाखा निवडा | Select Branch | Autocomplete | No | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 4 | वर्ष | Year | Dropdown | Yes | Default: `निवडा`. Values: `2026,2027,2028` |
| 5 | नावे | Account Head (Debit) | Dropdown | Yes | Default: `मा.वर्षाचा शिल्लक नफा` (Last Year's Balance Profit). |
| 6 | शेकडा (%) | Percentage | Textbox | No | — |
| 7 | + प्रगत शोध | Advanced Search | Link | No | Expands filters |

**Action:** `लाभांश गणना` (Calculate Dividend) — blue button.

---

## Settings Labels (Read-only Rules)

Display-only configuration hints (not editable on this screen):

- लाभांश गणना — (Dividend Calculation —)
- सभासद झाल्यानंतर लाभांश द्यावयाचा कालावधी - (Period for dividend after membership)
- प्रो रेटा साठी चालू वर्षातील बंद शेअर खात्यांना लाभांश दिला पाहिजे ? (Pro-rata for closed share accounts?)
- लाभांश रक्कम राऊंड अप करावी का ? (Round up dividend amount?)

---

## Results Grid

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | अनु. क्र | Sr. No. |
| 3 | ग्राहक क्र. | Customer No. |
| 4 | सभासद क्र. | Member No. |
| 5 | नाव | Name |
| 6 | भांडवल | Capital |

**Select all:** `सर्व निवडा` checkbox.

**Footer totals:** `एकूण भांडवल` (Total Capital), `एकूण लाभांश` (Total Dividend) — display fields, default `0.00`.

---

## Related Documents

- [overview.md](overview.md)
- [share-rules-screen.md](share-rules-screen.md)
- [../../membership/new-membership-screen.md](../../membership/new-membership-screen.md)
- [../../customer/other-account-registration-screen.md](../../customer/other-account-registration-screen.md)
