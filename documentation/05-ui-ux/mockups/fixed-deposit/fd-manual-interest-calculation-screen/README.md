# Mockup — मॅन्युअल व्याज आकारणी (मुदत ठेव)

| Property | Value |
|---|---|
| Spec | [fd-manual-interest-calculation-screen.md](../../../fixed-deposit/fd-manual-interest-calculation-screen.md) |
| Status | **Draft** |
| Created | 2026-07-16 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Notes

- Reference screenshot `screenshots/मुदत ठेव/डॅशबोर्ड_मुदत ठेव_ मॅन्युअल व्याज_आकारणी.png`.
- Interest Date is read-only auto-filled (last FY end).
- `स्थिती` dropdown and `अॅडव्हान्स शोध` marked TODO per spec.
- Concession Rate column included (display only).

## Review checklist

- [ ] All filter fields present with correct grouping
- [ ] Marathi labels clear for non-technical bank staff
- [ ] Required fields marked with *
- [ ] Grid columns match spec (11 columns)
- [ ] Summary totals and footer actions present
- [ ] Responsive on mobile and desktop

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen fd-manual-interest-calculation-screen`.
