# Changelog

## v1.0.0 — 2026-04-15

Initial public release.

- **16,908 US golf courses** with coordinates
- Fields: name, lat/lng, state, city, address, postal code, course type, holes, par, total yardage, year built, architect, phone, website, OSM id, last updated
- Scorecard: per-hole par + handicap index where available (15,211 courses with scorecards)
- Formats: GeoJSON, CSV, NDJSON (raw + gzipped)
- Checksums: SHA256SUMS
- License: [ODbL 1.0](https://opendatacommons.org/licenses/odbl/1-0/)

### Coverage

| Field | Count | % |
|---|---|---|
| Total | 16,908 | 100% |
| Scorecard (holes + par) | 15,211 | 90.0% |
| Par total | 15,219 | 90.0% |
| Website | 14,266 | 84.4% |
| Phone | 12,139 | 71.8% |
| Address | 16,650 | 98.5% |
| Architect | 540 | 3.2% |
| Total yardage | 584 | 3.5% |

### Known limitations

- 382 courses are excluded from this release due to bad upstream coordinates (geocoded to wrong countries). Tracked for cleanup in v1.1.
- Architect and total yardage have low coverage — primarily derived from GolfPass where available. Community contributions welcome.
- International coverage is not included in v1.0 — focus was US first.
