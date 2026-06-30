# Passport photo specifications

Source-linked reference data for passport/ID photo dimensions and backgrounds.

**File:** `passport-photo-specs.json`

## Fields

- `country`, `iso2`
- `width_mm`, `height_mm`
- `inches` where an inch standard is commonly stated, otherwise `null`
- `background`
- `notes`
- `source_url`

Rules change and may differ for embassies, online submissions, babies/children, or counter-capture workflows. Verify with `source_url` before submitting an official application.

```js
const data = require("./passport-photo-specs.json");
console.log(data.entries.filter((x) => x.width_mm === 35 && x.height_mm === 45));
```

Relevant Lumi Studio app: [Snapport](https://apps.apple.com/app/id6780575828).
