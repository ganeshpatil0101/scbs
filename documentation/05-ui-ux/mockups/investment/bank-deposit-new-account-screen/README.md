# Mockup — नवीन खाते (बँक ठेव)

| Property | Value |
|---|---|
| Spec | [bank-deposit-new-account-screen.md](../../../investment/bank-deposit-new-account-screen.md) |
| Status | **Draft** |
| Created | 2026-07-11 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Notes

- Reference screenshot under `screenshots/गुंतवणूक/` not verified in repo — mockup is spec-driven.
- `TODO` dropdowns (ठेव प्रकार enum, निधी, व्याज हस्तांतरण बँक) show `[TODO]` badge — no invented values.

## Review checklist

- [ ] बँक निवडा single Autocomplete (not GL ID + select pair)
- [ ] Auto-fill Labels: खाते क्रमांक, व्याज सुरु दिनांक, परतीची दिनांक/रक्कम, स्थिती
- [ ] प्रगत सेटिंग्ज collapsed by default (निधी, व्याज प्रकार, गणना प्रकार, पावती)
- [ ] Document upload + दस्तऐवज अपडेट करा action
- [ ] Marathi labels clear for non-technical bank staff
- [ ] Required fields marked with *
- [ ] Side-by-side sections on desktop
- [ ] Sticky footer: पूर्ववत / पूर्ण

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen bank-deposit-new-account-screen`.
