# Screen Spec — New Deposit Loan (कर्ज > नवीन ठेव कर्ज)

## Purpose

UI specification for opening a new loan against fixed/recurring deposits. Three-tab wizard.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | नवीन ठेव कर्ज | New Deposit Loan |
| Breadcrumb | डॅशबोर्ड > कर्ज > नवीन ठेव कर्ज | Dashboard > Loan > New Deposit Loan |
| Parent Module | कर्ज | Loan |

**Auto-fill (header):** `संस्था` (Organization) — read-only `Label` from tenant session.

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | ठेव माहिती | Deposit Information |
| 2 | कर्ज माहिती | Loan Information |
| 3 | एस.आय माहिती | S.I. Information |

## Reference Screenshots / Media

| File | Tab |
| :--- | :--- |
| `screenshots/कर्ज/डॅशबोर्ड_कर्ज_नवीन ठेव कर्ज.mp4` | All tabs (from video) |
| `screenshots/कर्ज/new-deposit-loan-frames/frame_0000.jpg` | Tab 1 |
| `screenshots/कर्ज/new-deposit-loan-frames/frame_0025.jpg` | Tab 2 |
| `screenshots/कर्ज/new-deposit-loan-frames/frame_0050.jpg` | Tab 3 |

---

## Tab 1: ठेव माहिती (Deposit Information)

### Scheme Selection

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | योजना निवडा | Select Scheme | Dropdown | Yes | Loaded dynamically from Loan / Deposit-Loan schemes (Settings > नवीन योजना). Sample: `ठेव कर्ज`. Full list from scheme master — not a fixed enum |
| 2 | योजना प्रकार | Scheme Type | Label | No | Auto-fill from selected scheme |

### ग्राहक माहिती (Customer Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 3 | ग्राहक निवडा | Select Customer | Autocomplete | Yes | Replaces Customer No. + Member Name pair. See [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |
| 4 | सभासद क्रमांक | Member Number | Label | No | Auto-fill when customer selected |
| 5 | वय (वर्षे) | Age (Years) | Label | No | Auto-fill when customer selected |
| 6 | सभासद प्रकार | Member Type | Label | No | Auto-fill when customer selected |
| 7 | ग्राहक शाखा | Customer Branch | Label | No | Auto-fill when customer selected |
| 8 | विशेष सूचना | Special Instructions | Label | No | Read-only from customer master |

### खाते माहिती (Account Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 9 | एजंट शाखा निवडा | Select Agent Branch | Autocomplete | No | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3` |
| 10 | एजंट निवडा | Select Agent | Autocomplete | No | Replaces Agent Number + Search Agent Name |
| 11 | खाते क्र. | Account No. | Label | No | Auto-generated |

**Actions:** `ठेवी दाखवा` (Show Deposits), `इतर ठेवी दाखवा` (Show Other Deposits).

### Deposit Tables

**Left table columns:** निवडा, खाते क्रमांक, परतीची दिनांक, शिल्लक, ठेव रक्कम, व्याज तरतूद, चालू व्याज.

**Right table columns:** निवडा, खाते क्रमांक, नाव, चालू दिनांक, शिल्लक, बंद दिनांक, व्याज तरतूद, चालू व्याज.

### Surrender Value

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 14 | सरेंडर मूल्य तरतुदी सहित | Surrender Value with Provision | Checkbox | No | — |
| 15 | सरेंडर मूल्य वर्तमान व्याजासहित | Surrender Value with Current Interest | Checkbox | No | — |

**Action:** `सरेंडर रक्कम गणना करा` (Calculate Surrender Amount).

### Summary (Read-only)

| # | Marathi Label | English Label |
| :---: | :--- | :--- |
| 16 | जुन्या कर्जावरील शिल्लक | Balance on Old Loan |
| 17 | निवडलेल्या ठेवींची एकूण बाकी | Total Balance of Selected Deposits |
| 18 | निवडलेल्या ठेवींची एकूण ठेव रक्कम | Total Deposit Amount of Selected |
| 19 | सरासरी ठेव व्याज दर (% पीए) | Average Deposit Interest Rate (% p.a.) |

---

## Tab 2: कर्ज माहिती (Loan Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | स्थिती निवडा | Select Status | Dropdown | Yes | Default: `चालू` (Active). Values: `चालू`, `बंद` (Closed), `स्थगित` (Suspended) — same as [New Loan](new-loan-screen.md) |
| 2 | चालू दिनांक | Current Date | Label | Yes | System date |
| 3 | कर्ज रक्कम (रु.) | Loan Amount (Rs.) | Textbox | Yes | — |
| 4 | कालावधी (महिने) | Duration (Months) | Textbox | Yes | — |
| 5 | सरासरी ठेव तारण कर्ज व्याज दर (% पीए) | Avg. Deposit Collateral Loan Rate | Label | Yes | Auto-fill from deposit selection |
| 6 | हप्ता रक्कम (रु.) | Installment Amount (Rs.) | Textbox | Yes | — |
| 7 | एकूण हप्ते | Total Installments | Label | No | Calculated from duration |
| 8 | शेवटची दिनांक | Last Date | Date | No | — |
| 9 | दंड व्याज दर | Penalty Interest Rate | Textbox | Yes | — |
| 10 | विशेष सूचना | Special Instructions | Textbox | No | — |
| 11 | कर्ज मागणीचे कारण निवडा | Select Reason for Loan Request | Dropdown | Yes | Default: `निवडा`. Values: `इतर`, `वायवसाय कर्ज`, `वाहन तारण कर्ज`, `सोने तारण`, `स्थावर तारण कर्ज` — same as [New Loan](new-loan-screen.md) `कर्जाचे कारण` |

### मंजुरी (Approval)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 17 | पालक कर्मचारी निवडा | Select Guardian Employee | Autocomplete | No | From Staff master. Sample: `1 — कर्मचारी 1`. Enter resolves by staff ID or name. Same as [New Loan](new-loan-screen.md) |
| 18 | मंजूरी अधिकारी क्र. | Approval Officer No. | Textbox | No | — |
| 19 | मंजूरी अधिकारी / परिचयकर्ता निवडा | Select Approval Officer / Introducer | Textbox | No | — |

### सह-अर्जदार (Co-applicant)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 20 | ग्राहक निवडा | Select Customer | Autocomplete | No | Replaces Customer No. + Member Name pair |
| 21 | टाका + | Add | Button | — | — |

**Co-applicant grid columns:** निवडा, अनु. क्र., ग्राहक क्र., नाव, पत्ता, जिल्हा, तालुका, शहर, ठिकाण, पिन कोड, दूरध्वनी क्रमांक, मोबाईल क्रमांक.

**Grid actions:** `निर्यात करा`, `काढा`.

### वारसदार (Nominee)

> Optional — shown when `वारसदार जोडा` is checked. Same pattern as deposit New Account nominee tabs. See [quick-add-customer-pattern.md](../shared/quick-add-customer-pattern.md).

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| N0 | वारसदार जोडा | Add Nominee | Checkbox | No | Unchecked by default. When checked, nominee search + details become visible |
| N1 | ग्राहक निवडा | Select Customer | Autocomplete | Yes* | Nominee lookup. Includes **+ नवीन ग्राहक जोडा** per [quick-add-customer-pattern.md](../shared/quick-add-customer-pattern.md). \*Required when N0 checked |
| N2 | नाते | Relation | Dropdown | Yes* | Same as [Membership nominee relation](../membership/new-membership-screen.md) |
| N3 | टक्केवारी | Percentage | Textbox | No | e.g. `100` |
| N4 | नामांकन दिनांक | Nomination Date | Label (read-only) | No | System date |
| N5 | नामांकन करताना वय | Age at Nomination | Label (read-only) | No | Auto-calculated from resolved customer's DOB |

**Actions:** `टाका` (Add), `निवड करा`, `काढा`.

**Nominee grid columns:** निवडा, अनु. क्र., ग्राहक क्रमांक, ग्राहकाचे नाव, नाते, टक्केवारी, नामांकन करताना वय, नामांकन दिनांक.

### Section: प्रगत सेटिंग्ज (Advanced Settings)

> Collapsed by default.

| # | Marathi Label | English Label | Type | Required | Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 22 | रिबेट | Rebate | Textbox | No | — |
| 23 | एल. एफ. क्रमांक | L.F. Number | Textbox | No | — |
| 24 | बँकेचे बचत खाते क्रमांक | Bank Savings Account No. | Textbox | No | Payout details |
| 25 | आय.एफ.एस.सी. कोड | IFSC Code | Textbox | No | — |
| 26 | बँकेचे नाव | Bank Name | Textbox | No | — |

---

## Tab 3: एस.आय माहिती (S.I. Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | जी.एल. निवडा | Select GL | Autocomplete | No | Sample: `42 — Loan`. Enter resolves by ID or name; shows display name |
| 2 | खातेधारक निवडा | Select Account Holder | Autocomplete | No | Sample: `101 — Account Holder 1`, `102 — Account Holder 2`, `103 — Account Holder 3`. Enter resolves by ID or name; shows display name |
| 3 | वारंवारता | Frequency | Dropdown | No | Values: `दैनिक`, `पाक्षिक`, `मासिक`, `तिमाही`, `सहामाही`, `वार्षिक` — same as [New Loan](new-loan-screen.md) S.I. Frequency |
| 4 | दिवस / तारीख निवडा | Select Day / Date | Dropdown | No | e.g. `31` |

**Note:** टीप: महिना अंतिम तारीख.

**Footer actions:** `पूर्ण`, `पूर्ववत`, `मागे`.

---

## Mockup

- [HTML mockup (Draft)](../mockups/loan/new-deposit-loan-screen/) — Marathi 3-tab wizard for bank review

## Cross-Links

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [new-loan-screen.md](new-loan-screen.md)
- [../fixed-deposit/new-fd-account-screen.md](../fixed-deposit/new-fd-account-screen.md)
- [../fixed-deposit/deposit-loan-installment-payment-screen.md](../fixed-deposit/deposit-loan-installment-payment-screen.md) — installment payment (FD menu)
- [../shared/quick-add-customer-pattern.md](../shared/quick-add-customer-pattern.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
