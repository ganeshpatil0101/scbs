# Mockup — लाभांश व्यवहार

| Property | Value |
|---|---|
| Spec | [dividend-transaction-screen.md](../../../membership/dividend-transaction-screen.md) |
| Status | **Draft** |
| Created | 2026-07-12 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Notes

- Reference screenshots under `screenshots/sabhsadatv/` not verified in repo — mockup is spec-driven.
- Tab 1: सभासद निवडा Autocomplete replaces legacy Member Number + Customer Name fields.
- Tab 2: नावे / जमा and रोख / ट्रान्सफर mode radios (layout only; tab 3–4 always visible in mockup).
- Tab 3–4: चेक तपशील and ट्रान्सफर — spec marks transfer-mode-only; shown for layout review.
- **Removed (2026-07-22):** Tab 6 (केवायसी माहिती) — was a scaffold referencing the now-superseded Savings KYC pattern.
- **Resolved (2026-07-22):** `बँक निवडा` → Autocomplete from Bank Master, same as accounting/loan screens.

## Review checklist

- [ ] Tab 1: Member type radios, सभासद निवडा Autocomplete, warrant grid, summary labels
- [ ] Tab 1: फोटो / सही दाखवा KYC preview placeholders
- [ ] Tab 2: नावे/जमा and रोख/ट्रान्सफर radios; Branch / GL / Account Holder Autocomplete
- [ ] Tab 3: Cheque fields with required markers; NEFT/RTGS checkbox
- [ ] Tab 4: Transfer form, grid, नियमित करा / हटवा actions
- [ ] Tab 5: Ledger 15-column grid matches `app-ledger-tab` (savings variant)
- [ ] Footer: मागे / पुढे / पूर्ण / पूर्ववत
- [ ] Marathi labels; required markers; `data-spec-field` traceability
- [ ] Responsive + sticky footer

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen dividend-transaction-screen`.
