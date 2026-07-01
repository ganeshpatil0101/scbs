# Screen Spec — New Loan (कर्ज > नवीन कर्ज)

## Purpose

UI specification for opening a new loan account. Six-tab wizard.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | नवीन कर्ज | New Loan |
| Breadcrumb | डॅशबोर्ड > कर्ज > नवीन कर्ज | Dashboard > Loan > New Loan |
| Parent Module | कर्ज | Loan |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | कर्ज माहिती | Loan Information |
| 2 | कर्ज हप्ता पत्रक | Loan Installment Schedule |
| 3 | जामीनदार | Guarantor |
| 4 | मंजुरी व तारण | Approval & Collateral |
| 5 | कर्ज रेकॉर्ड | Loan Record |
| 6 | एस.आय माहिती | S.I. Information |

## Reference Screenshots / Media

| File | Tab / Section |
| :--- | :--- |
| `screenshots/कर्ज/डॅशबोर्ड_कर्ज_नवीन कर्ज.mp4` | All tabs (from video frames) |
| `screenshots/कर्ज/new-loan-frames/frame_0005.jpg` | Tab 1 — Loan Information |
| `screenshots/कर्ज/new-loan-frames/frame_0015.jpg` | Tab 2 — Installment Schedule |
| `screenshots/कर्ज/new-loan-frames/frame_0030.jpg` | Tab 3 — Guarantor |
| `screenshots/कर्ज/new-loan-frames/frame_0060.jpg` | Tab 4 — Approval & Collateral |
| `screenshots/कर्ज/new-loan-frames/frame_0080.jpg` | Tab 5 — Loan Record |
| `screenshots/कर्ज/new-loan-frames/frame_0100.jpg` | Tab 6 — S.I. Information |

---

## Tab 1: कर्ज माहिती (Loan Information)

### Section: Scheme Selection

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | योजना निवडा | Select Scheme | Dropdown | Yes | Default: `योजना निवडा`. Values: `TODO` |
| 2 | योजना प्रकार | Scheme Type | Textbox | No | Read-only |

### Section: ग्राहक माहिती (Customer Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 3 | ग्राहक क्र. | Customer No. | Textbox | Yes | — |
| 4 | ग्राहक नाव | Customer Name | Textbox | No | Read-only |
| 5 | सभासद खाते क्र. | Member Account No. | Textbox | No | Read-only |
| 6 | वय(वर्ष) | Age (Years) | Textbox | No | Read-only |
| 7 | सभासदत्व प्रकार | Membership Type | Textbox | No | Read-only |
| 8 | ग्राहक शाखा | Customer Branch | Textbox | No | Read-only |
| 9 | विशेष सूचना | Special Instructions | Textbox | No | Read-only |

### Section: खाते माहिती (Account Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 10 | एजंट शाखा निवडा | Select Agent Branch | Autocomplete | No | Sample: `1 — Branch 1`, `2 — Branch 2`, `3 — Branch 3`. Enter resolves by ID or name; shows display name |
| 11 | एजंट कोड | Agent Code | Textbox | No | — |
| 12 | एजंट नाव शोध | Search Agent Name | Textbox | No | — |
| 13 | खाते क्र. | Account No. | Textbox | No | Auto-generated |
| 14 | व्याज दर स्लॅब (कालावधी - रक्कम - व्याज दर) | Interest Rate Slab | Dropdown | Yes | Values: `TODO` |
| 15 | कालावधी (महिने) | Duration (Months) | Textbox | Yes | — |
| 16 | वास्तविक कर्ज रक्कम (रु.) | Actual Loan Amount (Rs.) | Textbox | Yes | — |
| 17 | कर्ज रक्कम (रु.) | Loan Amount (Rs.) | Textbox | Yes | — |
| 18 | अनुदानाची कर्ज रक्कम (रु.) | Subsidy Loan Amount (Rs.) | Textbox | No | — |
| 19 | व्याज दर (द.सा.द.शे.) | Interest Rate (% p.a.) | Textbox | Yes | — |
| 20 | चालू दिनांक | Current Date | Date | Yes | System date |
| 21 | पहिला हप्ता दिनांक | First Installment Date | Date | No | — |
| 22 | एकूण हप्ते | Total Installments | Textbox | No | Read-only / calculated |
| 23 | परतीची दिनांक | Return Date | Date | No | — |
| 24 | हप्ता रक्कम (रु.) | Installment Amount (Rs.) | Textbox | Yes | — |
| 25 | दंडात्मक व्याज दर (द.सा.द.शे.) | Penalty Interest Rate (% p.a.) | Textbox | Yes | — |
| 26 | रिबेट | Rebate | Textbox | No | — |
| 27 | विशेष सूचना | Special Instructions | Textbox | No | — |
| 28 | बँकेचे बचत खाते क्रमांक | Bank Savings Account No. | Textbox | No | — |
| 29 | आय.एफ.एस.सी. कोड | IFSC Code | Textbox | No | — |
| 30 | बँकेचे नाव | Bank Name | Textbox | No | — |
| 31 | निधी हस्तांतरण मर्यादा | Fund Transfer Limit | Textbox | No | — |

### Section: विमा (Insurance)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 32 | विमा | Insurance | Checkbox | No | Enables fields below when checked |
| 33 | पॉलिसी नंबर | Policy Number | Textbox | No | — |
| 34 | विमा रक्कम (रु.) | Insurance Amount (Rs.) | Textbox | No | — |
| 35 | प्रीमियम रक्कम (रु.) | Premium Amount (Rs.) | Textbox | No | — |
| 36 | दिनांक (पासून) | Date (From) | Date | No | — |
| 37 | दिनांक (पर्यंत) | Date (To) | Date | No | — |
| 38 | तपशील | Details | Textbox | No | — |

**Action:** `पुढे` (Next).

---

## Tab 2: कर्ज हप्ता पत्रक (Loan Installment Schedule)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | हप्त्याचे महिने निवडा | Select Installment Months | Dropdown | Yes | Values: `TODO` |
| 2 | पहिला हप्ता दिनांक | First Installment Date | Date | Yes | — |

**Action:** `दाखवा` (Show) — generates schedule grid.

### Schedule Grid Columns

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | अ.क्र. | Sr. No. |
| 2 | हप्ता दिनांक | Installment Date |
| 3 | मुद्दल | Principal |
| 4 | व्याज | Interest |
| 5 | शुल्क | Charges |
| 6 | एकूण हप्ता | Total Installment |
| 7 | शिल्लक | Balance |

**Summary:** एकूण मुद्दल, व्याज, शुल्क, एकूण हप्ता.

**Actions:** `निर्यात` (Export), `मागे`, `पुढे`.

---

## Tab 3: जामीनदार (Guarantor)

### Guarantor Entry

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | + भरा | Add | Button | — | Adds guarantor to grid |

### Guarantor Grid Columns

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
| 9 | ठिकाण | Location |
| 10 | पिन कोड | Pin Code |
| 11 | दूरध्वनी क्रमांक | Telephone |
| 12 | मोबाईल क्रमांक | Mobile |

**Grid actions:** `निर्यात`, `काढा`.

### Section: सभासद जमीनदार आहे असे खाते (Accounts where member is guarantor)

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | अ.क्र. | Sr. No. |
| 2 | खाते क्रमांक | Account Number |
| 3 | नाव | Name |
| 4 | शिल्लक | Balance |
| 5 | थकीत | Overdue |

**Summary:** एकूण शिल्लक, थकीत.

**Note:** कर्ज थकीत माहिती साठी एम.डी. युजर यांचे नवीनत्तम गणना विचारात घेतली आहे.

### Section: सहकर्जदार (Co-borrower)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | ग्राहक क्र. | Customer No. | Textbox | No | — |
| 2 | ग्राहक नाव | Customer Name | Textbox | No | — |
| 3 | + भरा | Add | Button | — | — |

Co-borrower grid uses same columns as guarantor grid.

---

## Tab 4: मंजुरी व तारण (Approval & Collateral)

### Section: मंजुरी (Approval)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | स्थिती निवडा | Select Status | Dropdown | Yes | e.g. `चालू`. Other values: `TODO` |
| 2 | दावा दाखल स्थिती | Claim Filed Status | Dropdown | No | Disabled unless applicable |
| 3 | दावा दाखल कायदा | Claim Filed Law | Dropdown | No | Disabled unless applicable |
| 4 | Advocate Name | Advocate Name | Textbox | No | — |
| 5 | पालक कर्मचारी निवडा | Select Guardian Employee | Dropdown | Yes | Values: `TODO` |
| 6 | मंजुरी अधिकारी क्र | Approval Officer No. | Textbox | Yes | — |
| 7 | मंजूर अधिकारी/शिफारस संचालक निवडा | Select Approving Officer | Textbox | Yes | — |
| 8 | ठराव क्र. | Resolution No. | Textbox | No | — |
| 9 | बैठक दिनांक | Meeting Date | Date | No | — |
| 10 | तपशील | Details | Textbox | No | — |
| 11 | लेजर फोलिओ नं. | Ledger Folio No. | Textbox | No | — |

### Section: तारण (Collateral)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 12 | तारण | Collateral | Checkbox | No | Enables fields below |
| 13 | तारण प्रकार निवडा | Select Collateral Type | Dropdown | Yes* | Values: `TODO` |
| 14 | मूल्यांकन (रु.) | Valuation (Rs.) | Textbox | Yes* | — |
| 15 | मूल्यांकन दिनांक | Valuation Date | Date | Yes* | — |
| 16 | मूल्यांकनकाराचे नाव | Valuator Name | Textbox | Yes* | — |
| 17 | घसारा (%) | Depreciation (%) | Textbox | Yes* | — |
| 18 | तारण तपशील | Collateral Details | Textarea | Yes* | — |

\*Required when तारण checkbox is checked.

### Section: तारणासाठी इतर ठेवी (Other Deposits for Collateral)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 19 | तारणासाठी इतर ठेवी | Other Deposits for Collateral | Checkbox | No | — |

**Grid columns:** निवडा, खाते क्र., नाव, चालू दिनांक, शिल्लक, खाते बंद दिनांक.

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 20 | कर्जाचे कारण निवडा | Select Loan Reason | Dropdown | Yes | Values: `TODO` |

---

## Tab 5: कर्ज रेकॉर्ड (Loan Record)

### Section: कर्जदाराने पूर्वी घेतलेल्या कर्जाची माहिती

**Action:** `दाखवा` (Show).

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | अ.क्र. | Sr. No. |
| 2 | खाते क्र. | Account No. |
| 3 | मुद्दल | Principal |
| 4 | येणे बाकी | Balance Due |
| 5 | थकबाकी | Arrears |
| 6 | स्थिती | Status |

**Summary:** एकूण मुद्दल, येणे बाकी, थकबाकी. **Action:** `निर्यात`.

### Section: कर्जदार सध्या जामीन असलेल्या कर्जाची माहिती

Same columns and actions as above section.

---

## Tab 6: एस.आय माहिती (S.I. Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | जी.एल. निवडा | Select GL | Autocomplete | No | Sample: `42 — Loan`. Enter resolves by ID or name; shows display name |
| 2 | खातेधारक निवडा | Select Account Holder | Autocomplete | No | Sample: `101 — Account Holder 1`, `102 — Account Holder 2`, `103 — Account Holder 3`. Enter resolves by ID or name; shows display name |
| 3 | वारंवारता | Frequency | Dropdown | No | Values: `TODO` |
| 4 | दिवस / तारीख निवडा | Select Day / Date | Dropdown | No | e.g. `31` |

**Note:** टीप: महिना अंतिम तारीख (month-end date applies when day exceeds month length).

**Footer actions:** `पूर्ण`, `पूर्ववत`, `मागे`.

---

## Cross-Links

- [overview.md](overview.md)
- [new-deposit-loan-screen.md](new-deposit-loan-screen.md)
- [../settings/schemes/loan-new-scheme-screen.md](../settings/schemes/loan-new-scheme-screen.md)
