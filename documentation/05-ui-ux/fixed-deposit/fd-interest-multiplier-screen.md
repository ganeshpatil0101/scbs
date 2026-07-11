# Screen Spec — FD Interest Multiplier (मुदत ठेव > व्याज गुणक)

## Purpose

UI specification for calculating FD interest rates or duration for various deposit schemes.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | व्याज गुणक | Interest Multiplier |
| Breadcrumb | डॅशबोर्ड > मुदत ठेव > व्याज गुणक | Dashboard > Fixed Deposit > Interest Multiplier |
| Parent Module | मुदत ठेव | Fixed Deposit |

## Reference Screenshots / Media

| File | Section |
| :--- | :--- |
| `screenshots/मुदत ठेव/डॅशबोर्ड_मुदत ठेव_व्याज गुणक.mp4` | Full screen (from video) |
| `screenshots/मुदत ठेव/interest-multiplier-frames/frame_0000.jpg` | Calculator form |
| `screenshots/मुदत ठेव/interest-multiplier-frames/frame_0010.jpg` | Scheme dropdown open |

---

## Calculator Section

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | योजना निवडा | Select Scheme | Dropdown | Yes | Loaded dynamically from FD schemes (Settings > नवीन योजना). Sample: `दाम दुप्पट ठेव (कर्जातील)`, `दामदुप्पट`, `पेन्शन ठेव`, `मुदत ठेव` |
| 2 | मुदत ठेव / दाम दुप्पट / कॅश सर्टिफिकेट | FD / Double Money / Cash Certificate | Radio | No | Visible when scheme selected; hidden until field 1 set |
| 3 | साधा / कम्पाउंडींग | Simple / Compounding | Radio | No | Visible when scheme selected |
| 4 | मासिक / तिमाही / सहामाही / वार्षिक | Compounding Frequency | Radio | No | Visible only when field 3 = Compounding |
| 5 | कालावधी दिवसामध्ये / महिन्यामध्ये | Duration in Days / Months | Radio | No | Visible when scheme selected |
| 6 | व्याज दर / कालावधी | Calculate Interest Rate / Duration | Radio | No | Visible when scheme selected |
| 7 | कालावधी (महिना) | Duration (Months) | Textbox | No | Visible when field 5 = Months. e.g. `96` |
| 8 | कालावधी (दिवस) | Duration (Days) | Textbox | No | Visible when field 5 = Days |

**Actions:** `गणना करा` (Calculate), `पूर्वत` (Reset).

### Output Sections (read-only Labels)

| # | Marathi Label | English Label |
| :---: | :--- | :--- |
| 9 | व्याज दर | Interest Rate |
| 10 | दिनांक फरक | Date Difference |

---

## Related Documents

- [overview.md](overview.md)
- [ux-optimization.md](ux-optimization.md)
- [new-fd-account-screen.md](new-fd-account-screen.md)
- [../daily/interest-multiplier-screen.md](../daily/interest-multiplier-screen.md)
- [../settings/schemes/new-scheme-screen.md](../settings/schemes/new-scheme-screen.md)
