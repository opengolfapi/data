# OpenGolfAPI Data

The open database of every golf course in America.

**16,908 courses** with GPS coordinates, scorecards, contact info, and course metadata. Released under [ODbL](https://opendatacommons.org/licenses/odbl/1-0/) — same license as OpenStreetMap.

## Download

Pick your format. All files are in this repo and also on [GitHub Releases](https://github.com/opengolfapi/data/releases/latest) with SHA256 checksums.

| Format | File | Size (raw / gzipped) |
|---|---|---|
| GeoJSON | [`opengolfapi-us.geojson`](opengolfapi-us.geojson) / [`.gz`](opengolfapi-us.geojson.gz) | 15 MB / 2.2 MB |
| CSV | [`opengolfapi-us.csv`](opengolfapi-us.csv) / [`.gz`](opengolfapi-us.csv.gz) | 4.8 MB / 1.8 MB |
| NDJSON | [`opengolfapi-us.ndjson`](opengolfapi-us.ndjson) / [`.gz`](opengolfapi-us.ndjson.gz) | 15 MB / 2.2 MB |

Verify integrity with [`SHA256SUMS`](SHA256SUMS).

## What's Included

| Field | Coverage |
|-------|----------|
| Name + coordinates | 100% |
| State + city | 98% |
| Course type | 93% |
| Par (total) | 90% |
| Hole-by-hole par + handicap index | 90% |
| Phone | 72% |
| Website | 84% |
| Address | 99% |
| Year built | 89% |
| Architect | 3% |

Full field spec: [SCHEMA.md](SCHEMA.md).

## API

No signup needed. No API key. Just curl.

```bash
# Search courses
curl "https://api.opengolfapi.org/v1/courses/search?q=pebble+beach"

# Get course with scorecard
curl "https://api.opengolfapi.org/v1/courses/{id}"

# Browse by state
curl "https://api.opengolfapi.org/v1/courses/state/CA"
```

Rate limit: 1,000 calls/day.

## MCP Server (for AI agents)

```bash
npm install -g @opengolfapi/mcp-server
```

Tools: `search_courses`, `get_course`

## Premium Data

Need tee ratings, slopes, per-tee yardages, climate normals, nearby hotels, real-time weather, or booking links?

**[GolfAGI API](https://golfagi.com)** — the intelligence layer on top of OpenGolfAPI.

## License

**ODbL 1.0** — same license as OpenStreetMap.

You can use this data for any purpose (including commercial) as long as you:
1. Attribute: `Contains data from OpenGolfAPI (opengolfapi.org)`
2. Share-alike: keep derivative databases open under ODbL

## Data Sources

- [OpenStreetMap](https://www.openstreetmap.org/) — course locations (ODbL)
- [OpenMeteo](https://open-meteo.com/) — climate normals (CC BY)
- [Nominatim](https://nominatim.openstreetmap.org/) — reverse geocoding (ODbL)
- Public course websites — phone, email, hours, scorecards (public facts)
- [GolfPass](https://www.golfpass.com/) — architect, year built, par (public facts)

## Contribute

- Spotted a bad coordinate or wrong par? [Open an issue](https://github.com/opengolfapi/data/issues)
- Want to add international courses? We'd love help — open an issue to discuss

## Support OpenGolfAPI

- [Donate on Open Collective](https://opencollective.com/opengolfapi)
- [Sponsor on GitHub](https://github.com/sponsors/opengolfapi)
