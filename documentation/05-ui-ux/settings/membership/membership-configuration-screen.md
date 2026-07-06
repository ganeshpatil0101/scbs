# Screen Spec — Membership Configuration (सेटिंग्ज > सभासदत्व > सभासदत्व सेटिंग्ज)

> **Consolidates:** [share-rules-screen.md](share-rules-screen.md) + [dividend-calculation-screen.md](dividend-calculation-screen.md)

## Purpose

Single screen for configuring share rules and running dividend calculation. Staff no longer choose between two separate menu items for member equity settings.

## Screen Identification

| Property | Marathi | English |
| :--- | :--- | :--- |
| Screen Name | सभासदत्व सेटिंग्ज | Membership Configuration |
| Breadcrumb | डॅशबोर्ड > सेटिंग्ज > सभासदत्व > सभासदत्व सेटिंग्ज | Dashboard > Settings > Membership > Membership Configuration |
| Parent Module | सभासदत्व (Settings) | Membership (Settings) |

## Tabs

| # | Marathi Tab | English Tab |
| :---: | :--- | :--- |
| 1 | शेअर्स नियम | Share Rules |
| 2 | लाभांश आकारणी | Dividend Calculation |

### Shared filter (both tabs)

| # | Marathi Label | English Label | Type | Required | Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | सभासद | Member | Radio | No | Default selected |
| 2 | नाममात्र सभासद | Nominal Member | Radio | No | — |

---

## Tab 1: शेअर्स नियम (Share Rules)

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 3 | दर्शनी मूल्य | Face Value | Textbox | Yes | e.g. `100` |
| 4 | भाग मालिका | Share Series | Textbox | Yes | e.g. `A` |
| 5 | सदस्यानुसार कमाल भाग रक्कम मर्यादा(रु.) | Max Share Amount per Member (Rs.) | Textbox | Yes | e.g. `1000000` |
| 6 | अधिकृत शेअर्स भांडवली (रु.) | Authorized Share Capital (Rs.) | Textbox | Yes | e.g. `2000000` |
| 7 | मागील वर्षाची अधिकृत भांडवली (रु.) | Previous Year Authorized Capital (Rs.) | Textbox | Yes | Renamed from confusing duplicate label |
| 8 | नियम बदलण्याची तारीख | Rule Change Date | Date | Yes | — |

**Removed:** Share Amount After Limit Transfer dropdown — no master values defined.

### Actions

| Button | Marathi | English |
| :--- | :--- | :--- |
| Save | पूर्ण | Complete |
| Remove | काढा | Remove (selected grid rows) |

### Rules Grid

Columns: निवडा, अनु. क्र, मालिका, दर्शनी मूल्य, मर्यादा, अधिकृत वाटा भांडवल, बदलेली तारीख, शाखा.

---

## Tab 2: लाभांश आकारणी (Dividend Calculation)

### Filter Section

| # | Marathi Label | English Label | Type | Required | Values / Notes |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 9 | शाखा निवडा | Select Branch | Autocomplete | No | Branch list |
| 10 | वर्ष | Year | Dropdown | Yes | `2026`, `2027`, `2028` |
| 11 | नावे | Account Head (Debit) | Dropdown | Yes | Default: `मा.वर्षाचा शिल्लक नफा` |
| 12 | शेकडा (%) | Percentage | Textbox | No | — |

**Action:** `लाभांश गणना` (Calculate Dividend).

### Settings Labels (Read-only)

Display-only hints from system configuration (not editable on this screen):

- लाभांश गणना कालावधी
- प्रो रेटा बंद शेअर खाते नियम
- लाभांश रक्कम राऊंड अप

### Results Grid

Columns: निवडा, अनु. क्र, ग्राहक क्र., सभासद क्र., नाव, भांडवल.

**Footer totals:** एकूण भांडवल, एकूण लाभांश.

---

## Mockup

| Property | Value |
| :--- | :--- |
| HTML mockup | [mockups/settings/membership/membership-configuration-screen/index.html](../../mockups/settings/membership/membership-configuration-screen/index.html) |
| Review guide | [mockups/settings/membership/membership-configuration-screen/README.md](../../mockups/settings/membership/membership-configuration-screen/README.md) |
| Stack | Tailwind CSS v4 (CDN), Marathi labels only |
| Status | Draft — pending bank user review |

---

## Related Documents

- [overview.md](overview.md)
- [ux-optimization.md](../ux-optimization.md)
- [../../shared/ui-simplification-patterns.md](../../shared/ui-simplification-patterns.md)
- [../../membership/overview.md](../../membership/overview.md)
