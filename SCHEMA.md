# OpenGolf Schema Specification v1.0

> A standard for representing golf course data in open databases.

## Overview

The OpenGolf Schema defines a minimal, extensible format for describing golf courses. It is designed to be:

- **Minimal** — only factual, verifiable fields
- **Compatible** — maps cleanly to OSM tags, GeoJSON, CSV, and JSON
- **Extensible** — additional fields can be added without breaking consumers

## License

All data published under the OpenGolf Schema is licensed under the [Open Database License (ODbL) v1.0](https://opendatacommons.org/licenses/odbl/1-0/).

Attribution requirement: `source=OpenGolf` in any derived work.

---

## Course Object

### Required Fields

| Field | Type | Description | Example |
|-------|------|-------------|---------|
| `id` | string | Unique OpenGolf identifier (UUID) | `"40977ee8-33ee-4195-b6a2-99a4ca83c2bc"` |
| `name` | string | Course name | `"Pebble Beach Golf Links"` |
| `latitude` | number | WGS84 latitude | `36.5607` |
| `longitude` | number | WGS84 longitude | `-121.9296` |
| `country` | string | ISO 3166-1 alpha-2 | `"US"` |

### Recommended Fields

| Field | Type | Description | Example |
|-------|------|-------------|---------|
| `state` | string | State/province/region code | `"CA"` |
| `city` | string | City or town | `"Pebble Beach"` |
| `type` | enum | Course access type | `"public"` |
| `holes` | integer | Number of holes (9, 18, 27, 36) | `18` |
| `par` | integer | Total par | `72` |
| `phone` | string | E.164 format preferred | `"+18316228723"` |
| `website` | string | Course's own website URL | `"https://pebblebeach.com"` |
| `year_built` | integer | Year course opened | `1919` |

### Optional Fields

| Field | Type | Description | Example |
|-------|------|-------------|---------|
| `address` | string | Street address | `"1700 17 Mile Dr"` |
| `postal_code` | string | ZIP/postal code | `"93953"` |
| `architect` | string | Course designer | `"Jack Neville"` |
| `osm_id` | integer | OpenStreetMap feature ID | `12345678` |

### Course Type Enum

```
public       — Open to the public, no membership required
private      — Members only
municipal    — City/county owned, open to public
resort       — Attached to resort/hotel, open to guests + public
military     — On military base, restricted access
par3         — Par-3 or executive course
```

---

## Scorecard Object

Each course MAY include a `scorecard` array of hole objects.

| Field | Type | Description | Example |
|-------|------|-------------|---------|
| `hole` | integer | Hole number (1-18) | `7` |
| `par` | integer | Par for the hole | `3` |

```json
{
  "scorecard": [
    { "hole": 1, "par": 4 },
    { "hole": 2, "par": 5 },
    { "hole": 3, "par": 4 },
    { "hole": 4, "par": 4 },
    { "hole": 5, "par": 3 },
    { "hole": 6, "par": 5 },
    { "hole": 7, "par": 3 },
    { "hole": 8, "par": 4 },
    { "hole": 9, "par": 4 },
    { "hole": 10, "par": 4 },
    { "hole": 11, "par": 4 },
    { "hole": 12, "par": 3 },
    { "hole": 13, "par": 4 },
    { "hole": 14, "par": 5 },
    { "hole": 15, "par": 4 },
    { "hole": 16, "par": 4 },
    { "hole": 17, "par": 3 },
    { "hole": 18, "par": 5 }
  ]
}
```

---

## GeoJSON Format

Courses are represented as GeoJSON Point features:

```json
{
  "type": "Feature",
  "geometry": {
    "type": "Point",
    "coordinates": [-121.9296, 36.5607]
  },
  "properties": {
    "id": "40977ee8-33ee-4195-b6a2-99a4ca83c2bc",
    "name": "Pebble Beach Golf Links",
    "country": "US",
    "state": "CA",
    "city": "Pebble Beach",
    "type": "resort",
    "holes": 18,
    "par": 72,
    "year_built": 1919,
    "phone": "+18316228723",
    "website": "https://pebblebeach.com",
    "scorecard": [
      { "hole": 1, "par": 4 },
      { "hole": 2, "par": 5 }
    ],
    "source": "OpenGolf",
    "source_version": "1.0"
  }
}
```

A full dataset export is a GeoJSON FeatureCollection.

---

## OSM Tag Mapping

| OpenGolf Field | OSM Tag |
|----------------|---------|
| name | `name=*` |
| latitude/longitude | Node coordinates |
| type | `golf:type=*` |
| holes | `golf:holes=*` |
| par | `golf:par=*` |
| phone | `phone=*` |
| website | `website=*` |
| year_built | `start_date=*` |
| scorecard[n].par | `golf:hole:N:par=*` |
| (attribution) | `source=OpenGolf` |

---

## CSV Format

For bulk downloads, a flat CSV is also provided:

```csv
id,name,latitude,longitude,country,state,city,type,holes,par,year_built,phone,website,hole_1_par,hole_2_par,...,hole_18_par
40977ee8...,Pebble Beach Golf Links,36.5607,-121.9296,US,CA,Pebble Beach,resort,18,72,1919,+18316228723,https://pebblebeach.com,4,5,4,4,3,5,3,4,4,4,4,3,4,5,4,4,3,5
```

---

## Versioning

The schema follows semantic versioning:
- **Major** (2.0) — breaking changes to required fields
- **Minor** (1.1) — new optional fields added
- **Patch** (1.0.1) — clarifications, no field changes

Dataset releases are tagged with the schema version + date: `v1.0-2026-04-07`

---

## Extensions (NOT part of core schema)

The following fields are intentionally excluded from the open schema. They may be available through commercial APIs (e.g., GolfAGI):

- Tee ratings, slopes, yardages per tee
- Monthly climate/weather data
- Nearby points of interest
- Difficulty rankings
- Real-time weather
- Booking/tee time links
- Course condition data
- GPS-refined geometry
