# Mockup — नवीन ग्राहक

| Property | Value |
|---|---|
| Spec | [new-customer-screen.md](../../../customer/new-customer-screen.md) |
| Status | **Draft** |
| Created | 2026-07-09 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Review checklist

- [ ] 3 tabs: ग्राहक तपशील / पत्ता / केवायसी कागदपत्रे
- [ ] संस्था read-only in header
- [ ] पॅन / आधार: textbox only — no ई-पडताळणी (phase 1)
- [ ] श्री. / सौ. + नाव on one row
- [ ] Single 2-column field grid (no empty left column)
- [ ] ग्राहक क्र. read-only Label; शाखा निवडा Autocomplete (editable)
- [ ] देहावसान तारीख hidden until स्थिती = मृत
- [ ] प्रगत सेटिंग्ज collapsed by default
- [ ] वारसदार टाका checked → वारसदार माहिती form visible (salutation, name, DOB, relation, mobile, %, address)
- [ ] Tab 2: Google Maps address search + address form + grid
- [ ] Tab 3: KYC as document cards (not grid) — upload on each card
- [ ] Tab 3: दस्तावेज क्रमांक only on पत्ता पुरावा / ओळख पुरावा
- [ ] Tab 3: मूळ आधार फोटो marked पर्यायी; progress `आवश्यक: n/4`
- [ ] Tab 3: पहा / काढा only after file selected
- [ ] Footer: रीसेट / मागे / पुढे / पूर्ण by tab
- [ ] Marathi labels clear for non-technical bank staff
- [ ] Required fields marked with *
- [ ] Responsive on mobile and desktop
- [ ] Sticky footer present

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen new-customer-screen`.
