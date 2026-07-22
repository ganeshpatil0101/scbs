# Screen Spec — Manual Interest Management (मॅन्युअल व्याज व्यवस्थापन)

> **Consolidates:** [../savings/manual-interest-calculation-screen.md](../savings/manual-interest-calculation-screen.md), [../fixed-deposit/fd-manual-interest-calculation-screen.md](../fixed-deposit/fd-manual-interest-calculation-screen.md), [../recurring/recurring-interest-management-screen.md](../recurring/recurring-interest-management-screen.md), and newly captured Daily (Pigmy) provision + assessment screens.

## Purpose

Single screen for bulk interest **provision** (accrual) and **assessment** (posting) on deposit products: Savings, Fixed Deposit, Daily (Pigmy), and Recurring. Two radio groups at the top drive module-specific filters, grid labels, and primary posting actions.

**Removed from legacy per-module screens (by design):**
- Separate menu entries per module × action (8 legacy screens → 1).
- Legacy dual Branch Code + Branch Name and GL Code + GL Name pairs — replaced by Autocomplete per [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md).
- Legacy duplicate `व्याज दिनांक निवडा` dropdown + `पोस्टिंग दिनांक` pair on Savings — replaced by read-only auto-filled **व्याज दिनांक** (last FY-end).
- Legacy बचत **खाते क्र.** + **खाते** dropdown — replaced by **जी.एल. निवडा** Autocomplete (default `55 — सेव्हिंग ठेव`), consistent with other modules.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | मॅन्युअल व्याज व्यवस्थापन | Manual Interest Management |
| Breadcrumb | डॅशबोर्ड > मॅन्युअल व्याज व्यवस्थापन | Dashboard > Manual Interest Management |
| Parent Module | लेखा (cross-product) | Accounting (cross-product) |

## Reference Screenshots / Media

| File | Module | Action |
| :--- | :--- | :--- |
| `screenshots/bachat/डॅशबोर्ड-बचत-मॅन्युअल व्याज-आकारणी.png` | बचत | आकारणी |
| `screenshots/bachat/डॅशबोर्ड-बचत-मॅन्युअल व्याज-तरतूद.png` | बचत | तरतूद |
| `screenshots/मुदत ठेव/डॅशबोर्ड_मुदत ठेव_ मॅन्युअल व्याज_आकारणी.png` | मुदत ठेव | आकारणी |
| `screenshots/मुदत ठेव/डॅशबोर्ड_मुदत ठेव_मॅन्युअल व्याज_तरतूद.png` | मुदत ठेव | तरतूद |
| `screenshots/डेली/डॅशबोर्ड_डेली_मॅन्युअल व्याज_तरतूद.png` | डेली | तरतूद |
| `screenshots/डेली/डॅशबोर्ड_डेली_मॅन्युअल व्याज_आकारणी.png` | डेली | आकारणी |
| `screenshots/रिकरिंग/डॅशबोर्ड_रिकरिंग_मॅन्युअल व्याज_तरतुद.png` | रिकरिंग | तरतूद |
| `screenshots/रिकरिंग/डॅशबोर्ड_रिकरिंग_मॅन्युअल व्याज_आकारणी.png` | रिकरिंग | आकारणी |

---

## Header: Module and Action Selection

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | मॉड्यूल निवडा | Select Module | Radio | Yes | `बचत` (Savings), `मुदत ठेव` (FD), `डेली` (Daily), `रिकरिंग` (Recurring). Drives GL default, grid column labels, legend, and footer button labels |
| 2 | कार्यवाही निवडा | Select Action | Radio | Yes | `तरतूद` (Provision), `आकारणी` (Assessment). Drives primary posting button label and backend workflow; shared filter + grid layout |

---

## Filter Section

| # | Marathi Label | English Label | Type | Required | Visibility | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- | :--- |
| 3 | शाखा निवडा | Select Branch | Autocomplete | Yes | All | Sample: `1 — कोतोली मुख्य कार्यालय`. Enter resolves by ID or name; see [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |
| 4 | जी.एल. निवडा | Select GL | Autocomplete | Yes | All | Filtered by module; default on module select: `55 — सेव्हिंग ठेव` (बचत), `91 — मुदत ठेव` (FD), `38 — पिग्मी ठेव` (Daily), `91 — रिकरिंग ठेव` (Recurring sample). Enter resolves by ID or name |
| 5 | व्याज दिनांक | Interest Date | Label (read-only) | Yes | All | Auto-filled: last financial year-end date only (e.g. `31.03.2026`). Replaces legacy `व्याज दिनांक निवडा` dropdown |
| 6 | व्याज पोस्ट दिनांक | Interest Post Date | Date | No | All | Label on legacy screens also appears as `व्याज पोस्टिंग दिनांक` (Daily/Recurring) — unified here |
| 7 | खाते क्र. (पासून) | Account No. (From) | Textbox | No | All | Range filter start |
| 8 | खाते क्र. (पर्यंत) | Account No. (To) | Textbox | No | All | Range filter end |
| 9 | स्थिती | Status | Dropdown | No | मुदत ठेव | Default: `सर्व` (All). Values: `सर्व` (All), `चालू` (Active), `बंद` (Closed), `स्थगित` (Suspended) — reuses standard FD account-status enum, same as [fd-account-register-screen.md](../fixed-deposit/fd-account-register-screen.md) |

**Action:** `व्याज गणना करा` (Calculate Interest) — populates results grid. Legacy डेली/रिकरिंग screenshots label this button `व्याज आकारणी`; standardized per [ui-simplification-patterns.md](../shared/ui-simplification-patterns.md).

---

## Results Grid

**Select all:** `सर्व निवडा`.

**Legend (डेली, रिकरिंग):** Pink row indicator — account period is in interest-free window; provision will still be made. Text varies slightly by module; display when **मॉड्यूल निवडा** = डेली or रिकरिंग.

**Grid action:** `निर्यात` / `निर्यात करा` (Export) — all modules.

| # | Marathi Column | English Column | Visibility | Notes |
| :---: | :--- | :--- | :--- | :--- |
| 10 | निवडा | Select | All | Checkbox column |
| 11 | अ. क्र. / अनु. क्र | Sr. No. | All | Label varies: `अनु. क्र` (बचत), `अ. क्र.` (others) |
| 12 | खाते क्र. / खाते क्रमांक | Account No. | All | Label varies by module |
| 13 | सभासदाचे नाव | Member Name | बचत | — |
| 14 | खाते धारकाचे नाव | Account Holder Name | मुदत ठेव | — |
| 15 | खातेदार | Account Holder | डेली, रिकरिंग | — |
| 16 | चालू दिनांक | Current / Start Date | बचत, मुदत ठेव | — |
| 17 | खाते चालू दिनांक | Account Opening Date | डेली, रिकरिंग | — |
| 18 | अंतिम व्याज दिनांक | Final Interest Date | बचत | — |
| 19 | व्याज दिनांक | Interest Date | मुदत ठेव | — |
| 20 | शेवटची व्याज दिनांक | Last Interest Date | डेली, रिकरिंग | — |
| 21 | व्याज दर | Interest Rate | All | — |
| 22 | शिल्लक | Balance | All | — |
| 23 | तरतूद | Provision | All | Read-only in grid; editable **व्याज** column on some legacy screens |
| 24 | व्याज / वर्तमान व्याज | Interest / Current Interest | All | Label `वर्तमान व्याज` on मुदत ठेव only; editable textbox on populated rows (legacy) |
| 25 | सवलत दर | Concession Rate | मुदत ठेव | — |

**Info note (बचत):** provision message when account duration is below scheme minimum — shown when applicable.

**Removed:** legacy मुदत ठेव grid side action `उल्लेख करा` (Process) — not carried into the consolidated UI (2026-07-22).

---

## Footer Summary (read-only)

| # | Marathi Label | English Label | Visibility |
| :---: | :--- | :--- | :--- |
| 26 | एकूण शिल्लक | Total Balance | All |
| 27 | एकूण तरतूद | Total Provision | All |
| 28 | एकूण व्याज | Total Interest | All |
| 29 | एकूण व्याज + एकूण तरतूद | Total Interest + Total Provision | All |

---

## Footer Actions (by module × action)

Primary posting button driven by **कार्यवाही निवडा**; reset button label varies by module.

| Module | तरतूद — primary | तरतूद — reset | आकारणी — primary | आकारणी — secondary / reset |
| :--- | :--- | :--- | :--- | :--- |
| बचत | `तरतूद` | `पूर्ववत` | `पोस्ट` | `पूर्ववत` |
| मुदत ठेव | `तरतूद` | `पुनर्रचना करा` | `पोस्टिंग` | `पुनर्रचना करा` |
| डेली | `तरतूद` | `पूर्ववत` | `पोस्टिंग` | `पूर्ववत` (inferred from तरतूद mode) |
| रिकरिंग | `तरतूद` | `पूर्ववत` | `निश्चित` | `प्रोसीडिंग`, `पूर्ववत` |

**Workflow:** Staff typically runs **तरतूद** (provision/accrual) at period-end, then **आकारणी** (assessment/posting) to finalize interest to accounts.

---

## Resolved Items (2026-07-22)

| Item | Resolution |
| :--- | :--- |
| डेली आकारणी primary posting button | Set to `पोस्टिंग` (reused FD label) — bank confirmation |
| FD Status dropdown values | Reused standard FD account-status enum: `सर्व`, `चालू`, `बंद`, `स्थगित` |
| FD grid `उल्लेख करा` side action | Removed — not carried into consolidated UI |

---

## Mockup

- [HTML mockup (Draft)](../mockups/accounting/manual-interest-management-screen/) — Marathi layout for bank review

---

## Related Documents

- [ux-optimization.md](ux-optimization.md)
- [overview.md](overview.md)
- [deposit-account-transaction-screen.md](deposit-account-transaction-screen.md)
- [../shared/ui-simplification-patterns.md](../shared/ui-simplification-patterns.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
- [../savings/manual-interest-calculation-screen.md](../savings/manual-interest-calculation-screen.md)
- [../fixed-deposit/fd-manual-interest-calculation-screen.md](../fixed-deposit/fd-manual-interest-calculation-screen.md)
- [../recurring/recurring-interest-management-screen.md](../recurring/recurring-interest-management-screen.md)
- [../investment/bank-deposit-interest-management-screen.md](../investment/bank-deposit-interest-management-screen.md)
- [../loan/loan-interest-management-screen.md](../loan/loan-interest-management-screen.md)
