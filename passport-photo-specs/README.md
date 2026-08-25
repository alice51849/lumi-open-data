# Passport photo specifications

Source-linked reference data for passport/ID photo dimensions and backgrounds.

**File:** `passport-photo-specs.json` — 45 countries/territories, one entry each.

## Fields

- `country`, `iso2`
- `width_mm`, `height_mm` — `null` where the issuing authority publishes a pixel
  specification instead of a print size (see `notes`)
- `inches` where an inch standard is commonly stated, otherwise `null`
- `background`
- `notes`
- `source_url`
- `verified_on` — ISO date on which the `source_url` page was opened and the numbers
  read off it. `null` means the entry predates this check and has not been re-opened.

Rules change and may differ for embassies, online submissions, babies/children, or
counter-capture workflows. Verify with `source_url` before submitting an official
application.

## Coverage

45 entries. This is a working subset, not every country.

Argentina (AR), Australia (AU), Austria (AT), Belgium (BE), Brazil (BR), Canada (CA),
China (CN), Croatia (HR), Czechia (CZ), Denmark (DK), Estonia (EE), Finland (FI),
France (FR), Germany (DE), Greece (GR), Hong Kong (HK), Iceland (IS), India (IN),
Ireland (IE), Italy (IT), Japan (JP), Kenya (KE), Latvia (LV), Lithuania (LT),
Malaysia (MY), Malta (MT), Mexico (MX), Netherlands (NL), New Zealand (NZ),
Norway (NO), Poland (PL), Romania (RO), Serbia (RS), Singapore (SG), Slovenia (SI),
South Africa (ZA), South Korea (KR), Spain (ES), Sweden (SE), Switzerland (CH),
Taiwan (TW), Turkey (TR), United Kingdom (GB), United States (US), Vietnam (VN).

## What is deliberately not here

Many states no longer accept an applicant-supplied printed photo at all — the facial
image is captured at the counter — so there is no print specification to record.
Where the official source publishes no dimensions, the country is left out rather than
filled in from a secondary source. Examples checked and skipped for this reason:
Slovakia, Hungary, Luxembourg, Cyprus, Peru, Colombia, Nepal, Thailand, Bulgaria.

## Odd cases worth knowing

- Iceland: light **grey** background, not white.
- Serbia: uniform **grey** background, and the photo is optional.
- Malta and the UK: light grey or cream, not white.
- Czechia: white *to light blue or light grey* are all accepted.
- Lithuania: printed at 40 x 60 mm, then trimmed to 35 x 45 mm by the authority.
- Latvia: the print must be 1–3 mm *larger* than 35 x 45 mm.
- Estonia: a pixel specification (≥ 1300 × 1600 px), no print size.

```js
const data = require("./passport-photo-specs.json");
console.log(data.entries.filter((x) => x.width_mm === 35 && x.height_mm === 45));
```

Relevant Lumi Studio app: [Snapport](https://apps.apple.com/app/id6780575828).
