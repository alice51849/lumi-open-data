# Chinese zodiac sexagenary cycle

Deterministic 1924–2044 reference for the Chinese sexagenary cycle.

**File:** `chinese-zodiac.json`

Each row is the lunisolar year whose Lunar New Year begins in the listed Gregorian year. Dates in January/February before Lunar New Year use the previous row.

## Fields

- `gregorian_year_of_lunar_new_year`
- `animal`
- `heavenly_stem`
- `earthly_branch`
- `sexagenary_name`
- `element`
- `yin_yang`
- `stem_element_yin_yang`

```js
const data = require("./chinese-zodiac.json");
const row = data.entries.find((x) => x.gregorian_year_of_lunar_new_year === 2024);
console.log(row.animal, row.sexagenary_name); // Dragon Jia-Chen
```

Relevant Lumi Studio app: [Zodira](https://apps.apple.com/app/id6783609555).
