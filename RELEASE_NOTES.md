# lumi-open-data v1.1.0

The passport photo dataset grows from 28 to **45 countries and territories**.
The other three datasets are unchanged from v1.0.0.

## What changed

| Dataset | v1.0.0 | v1.1.0 |
|---|---:|---:|
| Passport photo specifications | 28 entries | **45 entries** |
| TOEIC raw-to-scaled approximation | 101 + 101 rows | unchanged |
| Chinese zodiac sexagenary cycle | 121 entries | unchanged |
| Film stocks reference | 25 entries | unchanged |

Added: AR, AT, BR, CZ, EE, HR, IS, KE, LT, LV, MT, MX, RO, RS, SI, VN, ZA.

Every added entry was read on 2026-08-26 from the issuing authority's own
page or the official legal text — among them Iceland's Reglugerð 560/2009,
Croatia's Narodne novine, Latvia's Cabinet Regulation annex, and Lithuania's
parliamentary statute database. A new `verified_on` field records that date.
The 28 entries carried over from v1.0.0 have `verified_on: null`: they were
not re-checked for this release, and marking them verified would be a claim
nobody made.

## Anomalies are recorded as written, not normalised

Iceland is light grey, not white. Serbia is grey and the photo is not
mandatory. Malta accepts light grey or beige. Czechia accepts white, light
blue or light grey. Latvia requires the print to be 1–3 mm larger than
35×45. Lithuania prints 40×60 and the office trims it. Estonia publishes
only a pixel specification, so its millimetre fields are null with the pixel
requirement in `notes`.

## What is deliberately absent

Several countries were researched and left out rather than guessed at:

- **No printed specification exists.** Slovakia, Hungary, Luxembourg, Cyprus,
  Peru, Colombia, Nepal, Thailand and Bulgaria capture the photo at the
  counter, so there is no size to record.
- **The official page could not be opened to verify it.** The Philippines,
  Israel, Pakistan, Ukraine, the UAE, Macau, Ghana, Tanzania, Trinidad,
  Indonesia, Portugal and Bosnia. Second-hand figures were not accepted as a
  substitute.

45 entries is a working subset, not every country. Verify against the linked
official source before relying on any of it for an application.
