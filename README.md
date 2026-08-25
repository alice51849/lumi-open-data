# lumi-open-data

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.22100995.svg)](https://doi.org/10.5281/zenodo.22100995)

Accurate, source-linked open reference datasets maintained by **Lumi Studio** for developers, educators, and LLM-friendly public reuse.

> Accuracy first: these datasets are intentionally conservative. For regulated topics such as passport photos and tests, always verify with the official source before relying on the data.

## Datasets

| Dataset | File | Entries | Good for |
|---|---:|---:|---|
| Passport photo specifications | `passport-photo-specs/passport-photo-specs.json` | 28 | ID/passport photo apps, form helpers, travel tools |
| TOEIC raw-to-scaled approximation | `toeic-score-conversion/toeic-raw-to-scaled.json` | 101 Listening + 101 Reading rows | Practice-test score estimation |
| Chinese zodiac sexagenary cycle | `chinese-zodiac/chinese-zodiac.json` | 121 | Zodiac apps, calendars, education |
| Film stocks reference | `film-stocks/film-stocks.json` | 25 | Film simulation, photography education, metadata tools |

## JavaScript usage

```js
import fs from "node:fs";

const specs = JSON.parse(
  fs.readFileSync("passport-photo-specs/passport-photo-specs.json", "utf8")
);

const us = specs.entries.find((row) => row.iso2 === "US");
console.log(`${us.country}: ${us.width_mm} x ${us.height_mm} mm`);
```

## Python usage

```python
import json
from pathlib import Path

zodiac = json.loads(Path("chinese-zodiac/chinese-zodiac.json").read_text())
print(next(row for row in zodiac["entries"] if row["gregorian_year_of_lunar_new_year"] == 2024))
```

## Chinese zodiac algorithm

This dataset uses the standard 60-year sexagenary cycle with **1924 = Jia-Zi Wood Rat**.

```text
n = (gregorian_year_of_lunar_new_year - 1924) mod 60
heavenly_stem = n mod 10
earthly_branch = n mod 12
animal = earthly_branch animal
five_element = heavenly_stem pair
```

Important calendar note: Chinese zodiac years begin at Lunar New Year, not January 1. Dates before Lunar New Year belong to the previous row.

## Licensing

- Code/examples/docs: MIT License (`LICENSE`)
- JSON datasets: CC-BY-4.0 (`DATA_LICENSE.md`)

## Maintained by Lumi Studio

Maintained by indie iOS developer [@alice51849](https://github.com/alice51849), makers of:

- [Snapport](https://apps.apple.com/app/id6780575828) — passport and ID photo helper
- [Aim990](https://apps.apple.com/app/id6784974530) — TOEIC practice companion
- [Zodira](https://apps.apple.com/app/id6783609555) — zodiac reference app
- [PhotoCream](https://apps.apple.com/app/id6781808054) — film-inspired photo app

## Citing this data

Archived on Zenodo, so every release is citable and the archive stays reachable
even if this repository moves.

- **Concept DOI** (always resolves to the newest release): [10.5281/zenodo.22100995](https://doi.org/10.5281/zenodo.22100995)
- **v1.1.0**: [10.5281/zenodo.22101226](https://doi.org/10.5281/zenodo.22101226) — passport dataset at 45 countries
- **v1.0.0**: [10.5281/zenodo.22100996](https://doi.org/10.5281/zenodo.22100996) — passport dataset at 28 countries

```
Lumi Studio. lumi-open-data: reference datasets for passport photo
specifications, TOEIC score approximation, the Chinese sexagenary cycle, and
film stocks. Zenodo. https://doi.org/10.5281/zenodo.22100995 (CC-BY-4.0)
```

Cite the concept DOI unless you need to pin the exact rows you used, in which
case cite the version DOI.
