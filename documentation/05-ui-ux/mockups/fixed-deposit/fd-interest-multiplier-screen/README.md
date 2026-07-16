# Mockup — व्याज गुणक (मुदत ठेव)

| Property | Value |
|---|---|
| Spec | [fd-interest-multiplier-screen.md](../../../fixed-deposit/fd-interest-multiplier-screen.md) |
| Status | **Draft** |
| Created | 2026-07-16 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Notes

- Reference media: `screenshots/मुदत ठेव/डॅशबोर्ड_मुदत ठेव_व्याज गुणक.mp4`.
- Conditional radios hidden until scheme selected; compounding frequency hidden until Compounding selected.
- Duration months/days fields toggle based on duration unit radio.

## Review checklist

- [ ] All spec fields present with correct grouping
- [ ] Marathi labels clear for non-technical bank staff
- [ ] Required fields marked with *
- [ ] Conditional radio visibility approved
- [ ] Output labels (व्याज दर, दिनांक फरक) present
- [ ] Responsive on mobile and desktop

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen fd-interest-multiplier-screen`.
