# Mockup — मॅन्युअल व्याज व्यवस्थापन

| Property | Value |
|---|---|
| Spec | [manual-interest-management-screen.md](../../../accounting/manual-interest-management-screen.md) |
| Status | **Draft** |
| Created | 2026-07-19 |
| Language | Marathi only (English via ngx-translate in Angular phase) |

## How to open

Open `index.html` in any web browser. Requires internet for Tailwind CDN and Google Fonts.

## Review checklist

- [ ] मॉड्यूल निवडा radio switches filter fields (बचत / मुदत ठेव / डेली / रिकरिंग)
- [ ] कार्यवाही निवडा radio switches footer primary button (तरतूद / आकारणी)
- [ ] जी.एल. निवडा Autocomplete visible for all modules (default `55 — सेव्हिंग ठेव` for बचत)
- [ ] मुदत ठेव: स्थिती dropdown (सर्व/चालू/बंद/स्थगित) + सवलत दर column
- [ ] व्याज दिनांक read-only; grid populate button = व्याज गणना करा
- [ ] डेली / रिकरिंग: pink legend for interest-free period
- [ ] Footer totals: एकूण शिल्लक, एकूण तरतूद, एकूण व्याज, एकूण व्याज + एकूण तरतूद
- [ ] Footer buttons match module × action matrix in spec
- [ ] डेली आकारणी primary button = पोस्टिंग (resolved 2026-07-22, reused FD label)
- [ ] मुदत ठेव legacy `उल्लेख करा` grid action removed
- [ ] Marathi labels clear for non-technical bank staff
- [ ] Required fields marked with *
- [ ] Responsive on mobile and desktop
- [ ] Branch/GL use single Autocomplete controls

## Supersedes

This mockup replaces module-specific manual interest mockups:

- [manual-interest-calculation-screen](../../savings/manual-interest-calculation-screen/)
- [fd-manual-interest-calculation-screen](../../fixed-deposit/fd-manual-interest-calculation-screen/)
- [recurring-interest-management-screen](../../recurring/recurring-interest-management-screen/)

## Approval

When approved, change Status to **Approved**. Then run `/generate-ui-screen manual-interest-management-screen`.
