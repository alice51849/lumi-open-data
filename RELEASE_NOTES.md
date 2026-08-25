# lumi-open-data v1.0.0

First tagged release of four small, source-linked reference datasets, published as machine-readable JSON by **Lumi Studio**.

This is the initial versioned snapshot. The underlying JSON files carry an internal data `version` of `2026-07-01`.

## What is in this release

All counts below were taken by reading the JSON files in this tag, not from prose.

| Dataset | File | Rows | Coverage |
|---|---|---:|---|
| Passport photo specifications | `passport-photo-specs/passport-photo-specs.json` | 28 entries | 28 countries/territories |
| TOEIC raw-to-scaled approximation | `toeic-score-conversion/toeic-raw-to-scaled.json` | 101 Listening + 101 Reading rows, plus a 21-point anchor curve | raw correct 0–100 per section |
| Chinese zodiac sexagenary cycle | `chinese-zodiac/chinese-zodiac.json` | 121 entries | 1924–2044 |
| Film stocks reference | `film-stocks/film-stocks.json` | 25 entries | selected well-known stocks |

### Passport photo specifications — 28 entries

Photo dimensions and background requirements for 28 countries and territories: AU, BE, CA, CH, CN, DE, DK, ES, FI, FR, GB, GR, HK, IE, IN, IT, JP, KR, MY, NL, NO, NZ, PL, SE, SG, TR, TW, US.

Fields: `country`, `iso2`, `width_mm`, `height_mm`, `inches` (only where an inch standard is commonly stated, otherwise `null`), `background`, `notes`, `source_url`. Every one of the 28 rows carries its own distinct official `source_url`.

**This is a 28-country selection, not a worldwide or exhaustive listing.** Passport and ID photo rules change and can differ by embassy, by applicant age, and between printed and online submission channels. Verify against the linked official source before relying on a value for a real application.

### TOEIC raw-to-scaled approximation — 101 + 101 rows

An approximate mapping from raw correct answers (0–100) to an estimated scaled score (5–495) for each of the Listening and Reading sections, plus a 21-point `anchors` curve the rows are interpolated from.

**These values are approximations for practice-test estimation only. They are not an official ETS conversion table.** ETS equates official TOEIC Listening & Reading scores per test form and does not publish a single universal raw-correct to scaled-score table; official scores can differ by form. The values here are produced by linear interpolation through common published preparation-chart anchor points in 5-point scaled-score increments. The same transparent curve is deliberately used for both Listening and Reading, precisely so the data does not imply a form-specific official equating. The file states this limitation in its own `important_note` and `method` fields, and lists its `source_urls`.

Do not use this dataset to report, predict, or represent an official TOEIC score.

### Chinese zodiac sexagenary cycle — 121 entries

One row per lunisolar year for 1924–2044, with `animal`, `heavenly_stem`, `earthly_branch`, `sexagenary_name`, `element`, `yin_yang`, and `stem_element_yin_yang`.

Derived deterministically from the standard 60-year cycle anchored at 1924 = Jia-Zi Wood Rat: for year *Y*, `n = (Y - 1924) mod 60`, `heavenly_stem = n mod 10`, `earthly_branch = n mod 12`, and the element follows the heavenly-stem pair.

**Calendar caveat:** rows are keyed by the Gregorian year in which that lunisolar year's Lunar New Year falls. Zodiac years do not begin on 1 January, so a January or early-February date before Lunar New Year belongs to the *previous* row. This dataset does not include Lunar New Year dates themselves.

### Film stocks reference — 25 entries

25 well-known photographic film stocks with `name`, `type`, `iso`, `format_notes`, `look_characteristics`, and `source_url`.

**A selected reference, not a catalogue of everything in production.** `look_characteristics` are descriptive rather than measured. Film availability, datasheets, and emulsion characteristics change; consult manufacturer documentation for technical exposure, processing, or archival decisions.

## Licensing

- JSON datasets: **CC-BY-4.0** — see `DATA_LICENSE.md`
- Code examples and documentation: **MIT License** — see `LICENSE`

Attribute as: `Lumi Studio, lumi-open-data, CC-BY-4.0`, and preserve `source_url` values when reusing the data.

## General limitation

These are reference datasets, not authoritative or regulatory sources. For regulated topics — passport photos and standardised tests especially — always confirm against the official source before acting on a value.

## Links

- Repository: https://github.com/alice51849/lumi-open-data
- Dataset browser: https://alice51849.github.io/ios-app-guide/data/
