# Screen Spec — Loan New Scheme (कर्ज > नवीन योजना)

## Purpose

UI specification for creating a new **Loan (कर्ज)** scheme. Extracted from video walkthrough. Intended for AI agents implementing this screen.

## Scope

Single wizard screen with **6 tabs**. Video covers all tabs; some dropdowns were not opened in the recording (marked `TODO`).

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | नवीन योजना | New Scheme |
| Breadcrumb | डॅशबोर्ड > सेटिंग्ज > कर्ज > नवीन योजना | Dashboard > Settings > Loan > New Scheme |
| Parent Module | कर्ज | Loan |
| Related Screens | [daily-new-scheme-screen.md](daily-new-scheme-screen.md), [savings-new-scheme-screen.md](savings-new-scheme-screen.md), [fixed-deposit-new-scheme-screen.md](fixed-deposit-new-scheme-screen.md), [recurring-new-scheme-screen.md](recurring-new-scheme-screen.md) | — |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | कर्ज योजना | Loan Scheme |
| 2 | कालावधी/व्याज दर | Duration / Interest Rate |
| 3 | व्याज दिनांक | Interest Date |
| 4 | जामीनदार | Guarantor |
| 5 | सोने/ठेव तारण | Gold / Deposit Security |
| 6 | शुल्क/कपात | Charges / Deduction |

## Reference Media

| Source | Description |
| :--- | :--- |
| `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-कर्ज-नविन योजना.mp4` | Full screen walkthrough (~116 s) |
| `screenshots/settings/loan-video-frames-dense/` | Extracted frames (0.5 s interval) for field capture |

### Video Timestamp Index (key dropdown captures)

| Timestamp | Tab | Content |
| :--- | :--- | :--- |
| 0.0–2.0 s | Tab 1 | Loan Type dropdown open |
| 25.0–27.0 s | Tab 1 | First Installment Date Type dropdown open |
| 82.0 s | Tab 2 | Duration Type dropdown (`दिवस`, `महिने`) |
| 90.5–91.0 s | Tab 3 | Interest Posting Day dropdown (1–31) |
| 92.5 s | Tab 3 | Interest Posting Month dropdown (all months) |
| 110.0–112.0 s | Tab 6 | Deduction dropdown open |

---

## Tab 1: कर्ज योजना (Loan Scheme)

### Fields

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | कर्ज प्रकार | Loan Type | Dropdown | Yes | See table below |
| 2 | ज.ले. हेड क्र. | G.L. Head No. | Textbox | Yes | Shown: `163` |
| 3 | योजना नाव | Scheme Name | Textbox | Yes | — |
| 4 | स्थिती | Status | Dropdown | Yes | Shown: `चालू` (Active). **TODO:** Capture other status values (e.g. inactive/closed) |
| 5 | फक्त सदस्यांना परवानगी द्या | Allow Only Members | Checkbox | No | — |
| 6 | पोस्टिंग | Posting | Radio Button | No | Installment Type group; default selected |
| 7 | इ.एम.आय. | EMI | Radio Button | No | Installment Type |
| 8 | साधा हप्ता | Simple Installment | Radio Button | No | Installment Type |
| 9 | फ्लॅट व्याज | Flat Interest | Radio Button | No | Installment Type |
| 10 | दिवसावर | Daily | Radio Button | No | Interest Calculation group |
| 11 | मासिक | Monthly | Radio Button | No | Interest Calculation |
| 12 | पाक्षिक | Fortnightly | Radio Button | No | Interest Calculation |
| 13 | पहिला हप्ता दिनांक प्रकार | First Installment Date Type | Dropdown | No | See table below |
| 14 | हप्तेबंद (व्याजासहित) | Installment-Based (With Interest) | Checkbox | No | Checked when Posting installment type selected; may appear disabled |
| 15 | बहुचलन | Multi-Channel | Checkbox | No | — |
| 16 | हप्त्याची रक्कम बदलण्याची सोय हवी | Allow Installment Amount Change | Checkbox | No | — |
| 17 | पहिल्या हप्त्यात अधिस्थगन कालावधी व्याज समायोजित करा | Adjust Moratorium Interest in First Installment | Checkbox | No | — |
| 18 | फक्त व्याज कर्ज वेळापत्रक आवश्यक | Interest-Only Loan Schedule Required | Checkbox | No | — |
| 19 | नवीन ग्राहक झाले नंतर आवश्यक महिने | Months Required After New Customer | Textbox | No | Default: `0`. Section: कर्ज घेऊ शकतो |
| 20 | त्याच योजनेत (कर्ज नूतनीकरण)% | Same Scheme (Loan Renewal) % | Textbox | No | Section: मागील कर्जाची शिल्लक ज्यापेक्षा कमी हवी |
| 21 | कोणत्याही योजनेमध्ये (नवीन कर्ज) % | Any Scheme (New Loan) % | Textbox | No | — |
| 22 | ठेव खाते अनिवार्य असावे | Deposit Account Mandatory | Checkbox | No | Enables deposit GL fields when checked |
| 23 | ठेव ज.ले. हेड निवडा | Select Deposit G.L. Head | Dropdown | No | Disabled until deposit mandatory checked. **TODO:** Capture GL head list |
| 24 | किमान ठेव खाते कालावधी (महिने) | Minimum Deposit Account Duration (Months) | Textbox | No | Disabled until deposit mandatory checked |
| 25 | पोस्टिंग हप्ते प्रकारासाठी, कर्ज अखेर दिनांक नंतर जमा व्यवहारावर व्याज पोस्टिंग | Post Interest on Credit After Loan End (Posting Installment Type) | Checkbox | No | — |
| 26 | पोस्टिंग सह | With Posting | Radio Button | No | Account closing interest; default |
| 27 | पोस्टिंग शिवाय | Without Posting | Radio Button | No | Account closing interest |
| 28 | मासिक बिलिंग सायकल दिवस निवडा (क्रेडिट कार्ड) | Monthly Billing Cycle Day (Credit Card) | Dropdown | Yes | Disabled unless Credit Card loan type. **TODO:** Capture day values (likely 1–31) |
| 29 | कर्ज अर्ज प्रणाली लागू | Loan Application System Applicable | Checkbox | No | — |

### Loan Type Dropdown Values

| Marathi | English |
| :--- | :--- |
| निवडा | Select |
| अल्पबचत तारण कर्ज | Small Savings Mortgage Loan |
| एच. पी. कर्ज | H.P. Loan |
| कायम ठेव कर्ज | Fixed Deposit Loan |
| कॅश क्रेडिट कर्ज | Cash Credit Loan |
| क्रेडीट कार्ड | Credit Card |
| गोदाम कर्ज | Warehouse Loan |
| घर कर्ज | Home Loan |
| ठेव तारण कर्ज | Deposit Mortgage Loan |
| तारणी कर्ज | Mortgage Loan |
| दिवसगत | Daily |
| रिकरिंग तारण कर्ज | Recurring Mortgage Loan |
| विनातारणी कर्ज | Unsecured Loan |
| विमा कर्ज | Insurance Loan |
| सभासद कर्ज | Member Loan |
| सोने तारण कर्ज | Gold Mortgage Loan |

### First Installment Date Type Dropdown Values

| Marathi | English |
| :--- | :--- |
| निवडा | Select |
| पुढील महिन्याचा खाते चालू दिवस | Next Month's Account Opening Day |
| पुढील महिन्याचा पहिला दिवस | First Day of Next Month |
| खाते चालू दिवस | Account Opening Day |
| कर्ज दिनांक ०१ ते १५ असेल तर पुढील महिन्याची १ दिनांक अन्यथा कर्ज दिनांक १६ ते महिना अखेर असेल तर १ महिना सोडून पुढील महिन्याची १ दिनांक | If loan date is 1–15 then 1st of next month; if 16–end of month then 1st of month after next |

### Navigation

| Marathi | English | Type |
| :--- | :--- | :--- |
| पुढे | Next | Button |

---

## Tab 2: कालावधी/व्याज दर (Duration / Interest Rate)

> Long scrollable tab. Bottom section visible from ~78 s in video.

### Input Row (add to grid)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | कालावधी (महिने) | Duration (Months) | Textbox | Yes | — |
| 2 | कमाल कर्ज रक्कम (रु.) पर्यंत | Maximum Loan Amount (Rs.) Up To | Textbox | Yes | — |
| 3 | व्याज दर (% द.सा.द.शे.) | Interest Rate (% p.a.) | Textbox | Yes | — |
| 4 | रीबेट दर (% द.सा.द.शे.) | Rebate Rate (% p.a.) | Textbox | No | — |
| 5 | अंतिम तारखेनुसार दंड व्याज दर | Penalty Rate as per End Date | Checkbox | No | Enables field below when checked |
| 6 | अंतिम तारखेपूर्वी दंडात्मक व्याज दर (% द.सा.द.शे.) | Penal Rate Before End Date (% p.a.) | Textbox | No | Disabled until checkbox checked |
| 7 | दंड व्याज दर (% द.सा.द.शे.) | Penalty Interest Rate (% p.a.) | Textbox | No | Hint: enter annualized rate (e.g. 24 for 2% monthly) |
| 8 | Category | Category | Dropdown | No | **TODO:** Capture dropdown values (benefit/category list not opened in video) |
| — | + टाका | + Add | Button | — | — |

### Grid Columns

| Marathi | English |
| :--- | :--- |
| निवडा | Select |
| अ.क्र. | Sr. No. |
| कालावधी | Duration |
| कर्ज रक्कम | Loan Amount |
| व्याज दर | Interest Rate |
| दंड व्याज दर | Penalty Interest Rate |
| व्याज दर अंतिम दिनांकापूर्वी | Interest Rate Before End Date |
| व्याज सवलत दर | Interest Rebate Rate |
| Category | Category |

**Grid action:** `काढा` / `वगळा` / `हटवा` (Remove) — label varies by UI state

### Section: दंड व्याज (Penalty Interest)

| Marathi | English | Type | Default |
| :--- | :--- | :--- | :--- |
| वेगळे ठेवा | Keep Separate | Radio Button | Selected |
| चालू व्याजामध्ये मिसळा | Mix with Current Interest | Radio Button | — |
| अंतिम दिनांका पर्यंत चालू व्याजामध्ये मिसळा | Mix with Current Interest Until End Date | Radio Button | — |
| व्यवहार न करता वेगळा ठेवा | Keep Separate Without Transaction | Radio Button | — |

### Section: दंड व्याज अंमलबजावणी (Penalty Interest Implementation)

| Marathi | English | Type |
| :--- | :--- | :--- |
| थकीत हप्त्यावर | On Overdue Installments | Radio Button |
| कर्जाच्या अंतिम दिनांका नंतर | After Loan End Date | Radio Button |
| दंड व्याज लागू करा या दिवसानंतर | Apply Penalty After (Days) | Textbox |

### Section: थकीत हप्त्याची संख्या (Overdue Installment Calculation Base)

| Marathi | English | Type | Default |
| :--- | :--- | :--- | :--- |
| थकीत हप्त्याची संख्या | Number of Overdue Installments | Textbox | — |
| येणे बाकीवर | On Outstanding Balance | Radio Button | Selected |
| हप्ता रकमेवर | On Installment Amount | Radio Button | — |
| थकीत मुद्दल रक्कमेवर | On Overdue Principal | Radio Button | — |
| चालू व्याजावर | On Current Interest | Radio Button | — |

### Additional Fields (bottom of tab)

| # | Marathi Label | English Label | Type | Values / Notes |
| :---: | :--- | :--- | :--- | :--- |
| 1 | खातेबंद होताना किमान व्याज कालावधी | Minimum Interest Period on Account Close | Textbox | — |
| 2 | कालावधी प्रकार निवडा | Select Duration Type | Dropdown | `निवडा`, `दिवस` (Days), `महिने` (Months) |
| 3 | उचल मर्यादा (डी.पी.) कमी करण्याचे प्रमाण | Drawing Power (D.P.) Reduction Rate | Checkbox | — |
| 4 | ऑटो डी.पी. = डी.पी. - (कर्ज रक्कम / डी.पी. कमी करण्याचे प्रमाण) | Auto D.P. Formula | Radio Button | Sub-option when D.P. checkbox checked |
| 5 | टक्केवारीनुसार | As per Percentage | Radio Button | Sub-option when D.P. checkbox checked |
| 6 | उचल मर्यादा कमी करण्याचा दर (%) | D.P. Reduction Rate (%) | Textbox | Disabled until D.P. options enabled |
| 7 | चक्रवाढ व्याज, व्याजाचे मुद्रीकरण न करता | Compound Interest Without Capitalization | Checkbox | — |
| 8 | व्याज दर अंतिम दिनांका पूर्वी | Interest Rate Before End Date | Checkbox | — |
| 9 | व्याज दर अंतिम दिनांका पूर्वी (% द.सा.द.शे.) | Interest Rate Before End Date (% p.a.) | Textbox | Disabled until checkbox checked |

### Navigation

| Marathi | English |
| :--- | :--- |
| मागे | Back |
| पुढे | Next |
| वर | Scroll to Top |

---

## Tab 3: व्याज दिनांक (Interest Date)

### Input Row

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | व्याज पोस्टिंग दिवस | Interest Posting Day | Dropdown | Yes | `निवडा`, `1` through `31` |
| 2 | व्याज पोस्टिंग महिना | Interest Posting Month | Dropdown | Yes | See month table below |
| — | + टाका | + Add | Button | — | — |

### Interest Posting Month Dropdown Values

| Marathi | English |
| :--- | :--- |
| निवडा | Select |
| जानेवारी | January |
| फेब्रुवारी | February |
| मार्च | March |
| एप्रिल | April |
| मे | May |
| जून | June |
| जुलै | July |
| ऑगस्ट | August |
| सप्टेंबर | September |
| ऑक्टोबर | October |
| नोव्हेंबर | November |
| डिसेंबर | December |

### Grid Columns

| Marathi | English |
| :--- | :--- |
| निवडा | Select |
| अ.क्र. | Sr. No. |
| पोस्टिंग दिनांक | Posting Date |

**Grid action:** `काढा` (Remove)

### Additional Options

| # | Marathi Label | English Label | Type |
| :---: | :--- | :--- | :--- |
| 1 | सर्व जमा व्यवहारावर आजच्या दिवसाअखेर व्याज गणना करावी | Calculate Interest on All Credit Transactions at End of Today | Checkbox |
| 2 | पोस्टिंग करतेवेळी चालू व्याजासोबत व्याज आकारणी सेवा शुल्क हवा | Interest Calculation Service Charge with Current Interest at Posting | Checkbox |
| 3 | ओ.आय.आर. (ओव्हरड्यू इंटरेस्ट रिसीव्हेबल) | O.I.R. (Overdue Interest Receivable) | Checkbox |

### Section: ओ.आय.आर. प्रकार (O.I.R. Type)

| Marathi | English | Type |
| :--- | :--- | :--- |
| ओ.आय.आर. तरतूद | O.I.R. Provision | Radio Button |
| ओ.आय.आर. पोस्टिंग | O.I.R. Posting | Radio Button |

### Section: ओ.आय.आर. च्या साठी (For O.I.R.)

| Marathi | English | Type |
| :--- | :--- | :--- |
| सर्व खाते | All Accounts | Radio Button |
| फक्त एनपीए खाते | NPA Accounts Only | Radio Button |
| केवळ परिपक्व खाते | Matured Accounts Only | Radio Button |

### Navigation

| Marathi | English |
| :--- | :--- |
| मागे | Back |
| पुढे | Next |

---

## Tab 4: जामीनदार (Guarantor)

| # | Marathi Label | English Label | Type | Required | Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | ग्राहक (अ) | Customer (A) | Textbox | No | Count of customer guarantors |
| 2 | अ वर्ग सभासद (ब) | Class A Member (B) | Textbox | No | Count |
| 3 | नाममात्र सभासद (क) | Nominal Member (C) | Textbox | No | Count |
| 4 | एकूण जामीनदार (अ.ब.क.) | Total Guarantors (A.B.C.) | Textbox | No | Read-only calculated sum |
| 5 | नवीन ग्राहक झाले नंतर आवश्यक महिने | Months Required After New Customer | Textbox | No | Section: जामीन राहू शकतो |
| 6 | एकूण खाती | Total Accounts | Textbox | No | Section: कोणता ग्राहक जामीनदार राहू शकतो |
| 7 | एकूण कर्ज रक्कम (रु.) | Total Loan Amount (Rs.) | Textbox | No | — |
| 8 | क्रॉस गॅरेंटर सुविधा हवी | Cross Guarantor Facility Required | Checkbox | No | Shown checked in video |

**No dropdowns** on this tab.

### Navigation

| Marathi | English |
| :--- | :--- |
| मागे | Back |
| पुढे | Next |

---

## Tab 5: सोने/ठेव तारण (Gold / Deposit Security)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | ठेव ज.ले. हेड | Deposit G.L. Head | Dropdown | No | **TODO:** Capture GL head list (not opened in video) |
| 2 | कर्ज मर्यादा (%) | Loan Limit (%) | Textbox | No | Percentage |
| 3 | ठेव रक्कमेवर | On Deposit Amount | Radio Button | No | Loan against group: ज्यावर कर्ज |
| 4 | शिल्लकेवर (सरेंडर मूल्य) | On Balance (Surrender Value) | Radio Button | No | — |
| 5 | कर्ज वाटप करताना ठेव रक्कमेची टक्केवारीकडे दुर्लक्ष हवे | Ignore Deposit Percentage During Disbursement | Checkbox | No | — |

### Grid: मागील कर्जाच्या योजनांमध्ये आधीपासूनच खाते उपस्थित आहेत

| Marathi Column | English Column |
| :--- | :--- |
| अ.क्र. | Sr. No. |
| ज.ले. हेड क्र. | G.L. Head No. |
| ज.ले. हेड | G.L. Head |

### Navigation

| Marathi | English |
| :--- | :--- |
| मागे | Back |
| पुढे | Next |

---

## Tab 6: शुल्क/कपात (Charges / Deduction)

### Selection Type

| Marathi | English | Type | Default |
| :--- | :--- | :--- | :--- |
| कपात | Deduction | Radio Button | Selected |
| शुल्क | Fee / Charge | Radio Button | — |

### Deduction Dropdown (when कपात selected)

| Marathi | English |
| :--- | :--- |
| निवडा | Select |
| कर्जदार कल्याण निधी | Borrower Welfare Fund |
| पिग्मी कमिशन | Pigmy Commission |
| प्रोसेसिंग फी | Processing Fee |
| ब वर्ग सभासद फी | Class B Member Fee |
| स्टेशनरी फी | Stationery Fee |

**TODO:** Capture Fee (`शुल्क`) dropdown values when शुल्क radio is selected — not shown in video.

### Grid Columns

| Marathi | English |
| :--- | :--- |
| निवडा | Select |
| अ.क्र. | Sr. No. |
| कपात | Deduction / Charge Name |
| % / रक्कम | % / Amount |
| कपात / शुल्क प्रकार | Deduction / Charge Type |

**Grid actions:** `+ टाका` (Add), `काढा` / `निकाला` / `वगळा` (Remove)

### Additional Fields

| # | Marathi Label | English Label | Type | Notes |
| :---: | :--- | :--- | :--- | :--- |
| 1 | नावे व्यवहारावेळी कपात खातेवर पोस्ट करायची आहे का? | Post Deduction to Account on Debit Transaction | Checkbox | — |
| 2 | कर्ज प्रक्रिया शुल्क आवश्यक | Loan Processing Fee Required | Checkbox | Enables timing radio group |
| 3 | कर्ज अर्ज मंजूर | Loan Application Approved | Radio Button | Processing fee timing |
| 4 | खाते चालू करतेवेळी | At Account Opening | Radio Button | Processing fee timing |
| 5 | कर्ज वितरणावेळी | At Loan Disbursement | Radio Button | Processing fee timing |

### Navigation

| Marathi | English |
| :--- | :--- |
| मागे | Back |

---

## Global Footer Actions (all tabs)

| Marathi | English | Type |
| :--- | :--- | :--- |
| पूर्ण | Complete / Save | Button |
| पूर्ववत | Reset | Button |
| वर | Scroll to Top | Button |

## Conditional Field Rules (from video)

| Condition | Effect |
| :--- | :--- |
| Installment Type = Posting | `हप्तेबंद (व्याजासहित)` checked / may be read-only |
| `ठेव खाते अनिवार्य असावे` unchecked | Deposit G.L. Head and min duration fields disabled |
| Loan Type ≠ Credit Card | Monthly billing cycle day dropdown disabled |
| `अंतिम तारखेनुसार दंड व्याज दर` unchecked | Penal rate before end date disabled |
| `उचल मर्यादा (डी.पी.)` unchecked | D.P. reduction rate textbox disabled |
| `व्याज दर अंतिम दिनांका पूर्वी` unchecked | Rate textbox disabled |
| `कर्ज प्रक्रिया शुल्क आवश्यक` unchecked | Processing fee timing radios inactive |

## Related Documents

- [overview.md](overview.md)
- [daily-new-scheme-screen.md](daily-new-scheme-screen.md)
- [savings-new-scheme-screen.md](savings-new-scheme-screen.md)
- [fixed-deposit-new-scheme-screen.md](fixed-deposit-new-scheme-screen.md)
- [recurring-new-scheme-screen.md](recurring-new-scheme-screen.md)
- [changelog.md](changelog.md)
