# Screen Spec — New Deposit Loan (कर्ज > नवीन ठेव कर्ज)

## Purpose

UI specification for opening a new loan against fixed/recurring deposits. Three-tab wizard.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | नवीन ठेव कर्ज | New Deposit Loan |
| Breadcrumb | डॅशबोर्ड > कर्ज > नवीन ठेव कर्ज | Dashboard > Loan > New Deposit Loan |
| Parent Module | कर्ज | Loan |

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
| 1 | योजना निवडा | Select Scheme | Dropdown | Yes | Values: `TODO` |
| 2 | योजना प्रकार | Scheme Type | Textbox | No | Read-only |

### ग्राहक माहिती (Customer Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 3 | ग्राहक क्र. | Customer No. | Textbox | Yes | — |
| 4 | सभासदाचे नाव | Member Name | Textbox | No | Read-only |
| 5 | सभासद क्रमांक | Member Number | Textbox | No | Read-only |
| 6 | वय (वर्षे) | Age (Years) | Textbox | No | Read-only |
| 7 | सभासद प्रकार | Member Type | Textbox | No | Read-only |
| 8 | ग्राहक शाखा | Customer Branch | Textbox | No | Read-only |
| 9 | विशेष सूचना | Special Instructions | Textbox | No | Read-only |

### खाते माहिती (Account Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 10 | एजंट शाखा क्र. | Agent Branch No. | Textbox | No | e.g. `1` |
| 11 | एजंट शाखा निवडा | Select Agent Branch | Dropdown | No | e.g. कोतोली मुख्य कार्यालय |
| 12 | एजंट क्रमांक | Agent Number | Textbox | No | — |
| 13 | एजंट नाव शोध | Search Agent Name | Textbox | No | — |
| 14 | खाते क्र. | Account No. | Textbox | No | Read-only |

**Actions:** `ठेवी दाखवा` (Show Deposits), `इतर ठेवी दाखवा` (Show Other Deposits).

### Deposit Tables

**Left table columns:** निवडा, खाते क्रमांक, परतीची दिनांक, शिल्लक, ठेव रक्कम, व्याज तरतूद, चालू व्याज.

**Right table columns:** निवडा, खाते क्रमांक, नाव, चालू दिनांक, शिल्लक, बंद दिनांक, व्याज तरतूद, चालू व्याज.

### Surrender Value

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 15 | सरेंडर मूल्य तरतुदी सहित | Surrender Value with Provision | Checkbox | No | — |
| 16 | सरेंडर मूल्य वर्तमान व्याजासहित | Surrender Value with Current Interest | Checkbox | No | — |

**Action:** `सरेंडर रक्कम गणना करा` (Calculate Surrender Amount).

### Summary (Read-only)

| # | Marathi Label | English Label |
| :---: | :--- | :--- |
| 17 | जुन्या कर्जावरील शिल्लक | Balance on Old Loan |
| 18 | निवडलेल्या ठेवींची एकूण बाकी | Total Balance of Selected Deposits |
| 19 | निवडलेल्या ठेवींची एकूण ठेव रक्कम | Total Deposit Amount of Selected |
| 20 | सरासरी ठेव व्याज दर (% पीए) | Average Deposit Interest Rate (% p.a.) |

---

## Tab 2: कर्ज माहिती (Loan Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | स्थिती निवडा | Select Status | Dropdown | Yes | e.g. `चालू`. Other values: `TODO` |
| 2 | चालू दिनांक | Current Date | Date | Yes | — |
| 3 | कर्ज रक्कम (रु.) | Loan Amount (Rs.) | Textbox | Yes | — |
| 4 | कालावधी (महिने) | Duration (Months) | Textbox | Yes | — |
| 5 | सरासरी ठेव तारण कर्ज व्याज दर (% पीए) | Avg. Deposit Collateral Loan Rate | Textbox | Yes | — |
| 6 | हप्ता रक्कम (रु.) | Installment Amount (Rs.) | Textbox | Yes | — |
| 7 | एकूण हप्ते | Total Installments | Textbox | No | — |
| 8 | शेवटची दिनांक | Last Date | Date | No | — |
| 9 | दंड व्याज दर | Penalty Interest Rate | Textbox | Yes | — |
| 10 | रिबेट | Rebate | Textbox | No | — |
| 11 | विशेष सूचना | Special Instructions | Textbox | No | — |
| 12 | एल. एफ. क्रमांक | L.F. Number | Textbox | No | — |
| 13 | कर्ज मागणीचे कारण निवडा | Select Reason for Loan Request | Dropdown | Yes | Values: `TODO` |
| 14 | बँकेचे बचत खाते क्रमांक | Bank Savings Account No. | Textbox | No | — |
| 15 | आय.एफ.एस.सी. कोड | IFSC Code | Textbox | No | — |
| 16 | बँकेचे नाव | Bank Name | Textbox | No | — |

### मंजुरी (Approval)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 17 | पालक कर्मचारी निवडा | Select Guardian Employee | Dropdown | No | Values: `TODO` |
| 18 | मंजूरी अधिकारी क्र. | Approval Officer No. | Textbox | No | — |
| 19 | मंजूरी अधिकारी / परिचयकर्ता निवडा | Select Approval Officer / Introducer | Textbox | No | — |

### सह-अर्जदार (Co-applicant)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 20 | ग्राहक क्र. | Customer No. | Textbox | No | — |
| 21 | सभासदाचे नाव | Member Name | Textbox | No | — |
| 22 | टाका + | Add | Button | — | — |

**Co-applicant grid columns:** निवडा, अनु. क्र., ग्राहक क्र., नाव, पत्ता, जिल्हा, तालुका, शहर, ठिकाण, पिन कोड, दूरध्वनी क्रमांक, मोबाईल क्रमांक.

**Grid actions:** `निर्यात करा`, `काढा`.

### वारसदार (Nominee)

`TODO` — section header visible; fields not captured in video.

---

## Tab 3: एस.आय माहिती (S.I. Information)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | जि.एल.क्र. | G.L. No. | Textbox | No | — |
| 2 | जि.एल निवडा | Select G.L. | Dropdown | No | Values: `TODO` |
| 3 | खाते क्र. | Account No. | Textbox | No | — |
| 4 | खाते नाव निवडा | Select Account Name | Dropdown | No | Values: `TODO` |
| 5 | वारंवारता | Frequency | Dropdown | No | Values: `TODO` |
| 6 | दिवस / तारीख निवडा | Select Day / Date | Dropdown | No | e.g. `31` |

**Note:** टीप: महिना अंतिम तारीख.

**Footer actions:** `पूर्ण`, `पूर्वत`, `मागे`.

---

## Cross-Links

- [overview.md](overview.md)
- [new-loan-screen.md](new-loan-screen.md)
- [../fixed-deposit/new-fd-account-screen.md](../fixed-deposit/new-fd-account-screen.md)
