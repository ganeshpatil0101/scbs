# Screen Spec — Share Rules (सेटिंग्ज > सभासदत्व > शेअर्स नियम)

> **Superseded (2026-07-05):** Consolidated into [membership-configuration-screen.md](membership-configuration-screen.md). Retained for field reference only.

## Purpose

UI specification for configuring share (equity) rules per branch. Intended for AI agents implementing this screen.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | शेअर्स नियम | Share Rules |
| Breadcrumb | डॅशबोर्ड > सेटिंग्ज > सभासदत्व > शेअर्स नियम | Dashboard > Settings > Membership > Share Rules |
| Parent Module | सभासदत्व (Settings) | Membership (Settings) |

## Reference Screenshots

| Screenshot File | Section |
| :--- | :--- |
| `screenshots/settings/डॅशबोर्ड-सेटिंग्ज-सभासदत्व-शेअर्स नियम.png` | Form + existing rules grid |

---

## Form Fields

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | सभासद | Member | Radio | No | Default selected |
| 2 | नाममात्र सभासद | Nominal Member | Radio | No | — |
| 3 | दर्शनी मूल्य | Face Value | Textbox | Yes | e.g. `100` |
| 4 | भाग मालिका | Share Series | Textbox | Yes | e.g. `A` |
| 5 | सदस्यानुसार कमाल भाग रक्कम मर्यादा(रु.) | Max Share Amount per Member (Rs.) | Textbox | Yes | e.g. `1000000` |
| 6 | अधिकृत शेअर्स भांडवली (रु.) | Authorized Share Capital (Rs.) | Textbox | Yes | e.g. `2000000` |
| 7 | गेल्या वर्षी अधिकृत शेअर्सची भांडवली (रु.) | Last Year Authorized Share Capital (Rs.) | Textbox | Yes | e.g. `2000000` |
| 8 | नियम बदलण्याची तारीख | Rule Change Date | Date | Yes | — |
| 9 | मर्यादा हस्तांतरण केल्यानंतर शेअर्स रक्कम | Share Amount After Limit Transfer | Dropdown | No |  |

## Actions

| Button | Marathi | English |
| :--- | :--- | :--- |
| Save | पूर्ण | Complete |
| Remove | काढा | Remove (selected grid rows) |

---

## Rules Grid

| # | Marathi Column | English Column | Sample Row 1 |
| :---: | :--- | :--- | :--- |
| 1 | निवडा | Select | — |
| 2 | अनु. क्र | Sr. No. | 1 |
| 3 | मालिका | Series | A |
| 4 | दर्शनी मूल्य | Face Value | 100 |
| 5 | मर्यादा | Limit | 1000000.00 |
| 6 | अधिकृत वाटा भांडवल | Authorized Share Capital | 2000000.00 |
| 7 | बदलेली तारीख | Changed Date | — |
| 8 | नॉन रीफ.डिप.एसी | Non-Ref. Dep. AC | — |
| 9 | शेवटचा लेख शेअर कॅप | Last Account Share Cap | 2000000.00 |
| 10 | शाखा | Branch | 1 |

---

## Related Documents

- [overview.md](overview.md)
- [dividend-calculation-screen.md](dividend-calculation-screen.md)
- [../../membership/new-membership-screen.md](../../membership/new-membership-screen.md)
