# Screen Spec — Deposit Loan Installment Payment (ठेव > ठेव कर्ज हप्ता पेमेंट)

## Purpose

UI specification for processing installment payments on loans against deposits. Loan opening is on [New Deposit Loan](../loan/new-deposit-loan-screen.md) (Loan module); this screen handles installment payment under the FD/Deposit menu.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | ठेव कर्ज हप्ता पेमेंट | Deposit Loan Installment Payment |
| Breadcrumb | डॅशबोर्ड > ठेव > ठेव कर्ज हप्ता पेमेंट | Dashboard > Deposit > Deposit Loan Installment Payment |
| Parent Module | मुदत ठेव | Fixed Deposit |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | व्याज | Interest |
| 2 | इतर कपात | Other Deductions |
| 3 | कर्ज माहिती | Loan Information |
| 4 | साहित्य तपशील / तारण तपशील | Collateral Details |
| 5 | ट्रान्सफर | Transfer |
| 6 | केवायसी माहिती | KYC Information |

## Reference Screenshots / Media

| File | Tab |
| :--- | :--- |
| `screenshots/मुदत ठेव/डॅशबोर्ड_ठेव_ठेव कर्ज हप्ता पेमेंट.mp4` | Tab 1 (from video) |
| `screenshots/मुदत ठेव/deposit-loan-installment-frames/frame_0000.jpg` | Tab 1 |

---

## Tab 1: व्याज (Interest)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | रोख / ट्रान्सफर | Cash / Transfer | Radio | Yes | — |
| 2 | जी.एल. निवडा | Select GL | Autocomplete | Yes | Sample: `42 — Loan`. Enter resolves by ID or name; shows display name |
| 3 | ग्राहक निवडा | Select Customer | Autocomplete | No | Replaces `ग्राहक क्र.` + `ग्राहक निवडा` dropdown. Enter resolves by customer no. or name. See [entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md) |
| 4 | खातेधारक निवडा | Select Account Holder | Autocomplete | No | Alternative lookup when customer not used. Sample: `101 — Account Holder 1`. Enter resolves by ID or name |
| 5 | दिनांक | Date | Label (read-only) | Yes | System date |

**Note:** कृपया खाते क्रमांक किंवा ग्राहक क्रमांक प्रविष्ट करा — use field 3 (Customer) or field 4 (Account Holder); not both required.

**Action:** `व्याज गणना करा` (Calculate Interest).

### Results Grid

**Select all:** `सर्व निवडा`.

| # | Marathi Column | English Column |
| :---: | :--- | :--- |
| 1 | निवडा | Select |
| 2 | अ. क्र. | Sr. No. |
| 3 | खाते क्र. | Account No. |
| 4 | ग्राहक क्र. | Customer No. |
| 5 | खातेधारक | Account Holder |
| 6 | नाव 2 | Name 2 |
| 7 | बँकेचे बचत खाते क्रमांक | Bank Savings Account No. |
| 8 | आय.एफ.एस.सी. कोड | IFSC Code |
| 9 | चालू दिनांक | Start Date |
| 10 | शेवटची तारीख | Last Date |
| 11 | व्याज दिनांक | Interest Date |
| 12 | व्याज दर | Interest Rate |
| 13 | शिल्लक | Balance |
| 14 | मुद्दल हप्ता | Principal Installment |
| 15 | वर्तमान व्याज | Current Interest |
| 16 | एकूण हप्ता | Total Installment |

**Action:** `निर्धारित करा` (Set/Determine).

**Summary:** एकूण तरतूद, एकूण व्याज, एकूण रक्कम.

**Footer:** `पुढे`, `पूर्ण`, `पूर्वत`.

---

## Tab 2: इतर कपात (Other Deductions)

`TODO` — not captured in video.

## Tab 3: कर्ज माहिती (Loan Information)

`TODO` — not captured in video. Defer to [New Deposit Loan Tab 2](../loan/new-deposit-loan-screen.md) when captured.

## Tab 4: साहित्य तपशील / तारण तपशील (Collateral Details)

`TODO` — not captured in video.

## Tab 5: ट्रान्सफर (Transfer)

`TODO` — not captured in video. Same pattern as [savings-transaction-screen.md](../savings/savings-transaction-screen.md) Tab 3 when captured.

## Tab 6: केवायसी माहिती (KYC Information)

`TODO` — not captured in video. Uses shared component `app-kyc-info-tab` when captured.

---

## Related Documents

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [../loan/new-deposit-loan-screen.md](../loan/new-deposit-loan-screen.md)
- [../shared/entity-autocomplete-pattern.md](../shared/entity-autocomplete-pattern.md)
