# Skymation reference data

This repository publishes the open-database tables that ship inside the
[Skymation](https://skymation.net) iOS app, as required by the Open Database
License (ODbL 1.0, section 4.6). It contains reference data only: no app code
and no user data.

**Not for operational use or navigation.** The tables come with no guarantee
of accuracy or fitness for use.

## Tables

| File | What it is | Rows |
| --- | --- | --- |
| `data/airport-timezones.tsv` | Airport ident → IANA time zone | 9,612 |
| `data/runway-corrections.tsv` | Corrections Skymation applies over the OurAirports runway table | 33 |
| `data/airport-corrections.tsv` | Corrections Skymation applies over the OurAirports airport and frequency tables (served city names in English and Turkish, frequency labels) | 83 |

Each table is also published as the exact `.tsv.gz` file bundled in the app.
`SHA256SUMS` lists the SHA-256 of every file, so a copy can be matched to an app
build. Lines starting with `#` are the notices shipped in each file.

## Sources and method

- **Airport time zones**: derived from
  [timezone-boundary-builder](https://github.com/evansiroky/timezone-boundary-builder)
  2026c polygons, (c) [OpenStreetMap contributors](https://www.openstreetmap.org/copyright),
  made available under the ODbL. Each airport's coordinates (OurAirports, public
  domain, fetched 2026-09-29) are matched to the polygon that contains them.
- **Runway corrections**: values from OpenStreetMap (retrieved 2026-11-15),
  (c) OpenStreetMap contributors, made available under the ODbL. Runway true
  headings are the WGS-84 geodesic bearing between the end nodes of the runway
  way; length, width and surface come from the way's tags. Some rows are
  Skymation's own findings, for example removing helipads that are listed as runways.
- **Airport corrections**: Skymation's own data, made available under the same
  licence.
- **How the app uses them**: the correction tables are applied at run time over
  the OurAirports tables (public domain, snapshot of 2026-09-29;
  [ourairports.com/data](https://ourairports.com/data/)). The OurAirports tables
  themselves are not covered by the ODbL and are not republished here.

## Licence

The tables in `data/` are made available under the
[Open Database License (ODbL) v1.0](https://opendatacommons.org/licenses/odbl/1-0/).
The full text is in [`LICENSE`](LICENSE).

Attribution: "Airport time zones and runway corrections: Skymation. Contains
data (c) OpenStreetMap contributors, available under the Open Database License."

Questions: furkan@fayntech.tr
