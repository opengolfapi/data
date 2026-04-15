# OpenGolfAPI Data

The open database of every golf course in America.

**17,322 courses** with GPS coordinates, scorecards, contact info, and course metadata.

## Download

- [`opengolfapi-us.geojson`](opengolfapi-us.geojson) — Full dataset as GeoJSON (11MB)
- [`opengolfapi-us.csv`](opengolfapi-us.csv) — Full dataset as CSV (3.8MB)

## What's Included

| Field | Coverage |
|-------|----------|
| Name + coordinates | 99.8% |
| State + city | 96% |
| Course type | 94% |
| Par (total) | 90% |
| Hole-by-hole par | 90% (15,600 courses) |
| Phone | 79% |
| Website | 84% |
| Address | 98% |
| Year built | 89% |

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
npx @opengolfapi/mcp-server
```

Tools: `search_courses`, `get_course`

## Premium Data

Need tee ratings, slopes, yardages per tee, climate data, nearby hotels, real-time weather, or booking links?

**[GolfAGI API](https://golfagi.com)** — the intelligence layer on top of OpenGolfAPI.

## License

**ODbL 1.0** — same license as OpenStreetMap.

You can use this data for any purpose (including commercial) as long as you:
1. Attribute: "Contains data from OpenGolfAPI (opengolfapi.org)"
2. Share-Alike: keep derivative databases open under ODbL

## Data Sources

- [OpenStreetMap](https://www.openstreetmap.org/) — course locations (ODbL)
- [NOAA](https://www.ncei.noaa.gov/) — climate normals (public domain)
- [Nominatim](https://nominatim.openstreetmap.org/) — addresses (ODbL)
- Public course websites — phone, email (public facts)

## Support

- [Donate on Open Collective](https://opencollective.com/opengolfapi)
- [Report an issue](https://github.com/opengolfapi/data/issues)

## Schema

See [SCHEMA.md](SCHEMA.md) for the full field specification.
