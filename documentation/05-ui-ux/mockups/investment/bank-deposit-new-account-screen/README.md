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
- ठेव प्रकार: full enum (`मुदत ठेव` … `आवर्ती ठेव वार्षिक`).
- व्याज हस्तांतरणासाठी बँक: Autocomplete from society Bank master (बँक व्यवस्थापन).
- `निधी` removed (not required).
- व्याज गणना प्रकार: `दिवस`, `महिने`.

## Review checklist

- [ ] बँक निवडा single Autocomplete (investment bank masters)
- [ ] ठेव प्रकार full dropdown (7 deposit types)
- [ ] Auto-fill Labels: खाते क्रमांक, व्याज सुरु दिनांक, परतीची दिनांक/रक्कम, स्थिती = चालू
- [ ] Interest-transfer bank Autocomplete from society Bank master
- [ ] प्रगत सेटिंग्ज collapsed by default (व्याज प्रकार, गणना प्रकार, पावती) — no निधी
- [ ] Document upload + दस्तऐवज अपडेट करा action
- [ ] Marathi labels clear for non-technical bank staff
- [ ] Required fields marked with *
- [ ] Side-by-side sections on desktop
- [ ] Sticky footer: पूर्ववत / पूर्ण

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen bank-deposit-new-account-screen`.
