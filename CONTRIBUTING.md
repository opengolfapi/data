# Contributing to OpenGolfAPI

Thanks for helping build the open database of every golf course on Earth.

## Ways to contribute

### Report bad data (easiest)

Found a wrong par, bad phone number, or a course in the wrong city? [Open an issue](https://github.com/opengolfapi/data/issues/new) with:

- Course name and state
- What's wrong
- What the correct value should be
- Source (course website, personal knowledge, etc.)

### Claim your course (course owners/staff)

Visit your course page on [courses.opengolfapi.org](https://courses.opengolfapi.org), scroll to "Own or manage this course?", and submit a claim. Once verified, you can update your course info directly. Free, forever.

### Submit data corrections via pull request

1. Download the latest dataset from [Releases](https://github.com/opengolfapi/data/releases/latest)
2. Find the course in the GeoJSON or CSV
3. Fork this repo, make your edit, submit a PR
4. Include your source (link to course website, photo of scorecard, etc.)

We'll review and merge within 48 hours.

### Add international courses

We're US-only in v1.0. To add courses from another country:

1. Open an issue titled "Add [Country] courses"
2. Describe your data source and its license (must be ODbL-compatible)
3. We'll work with you on the schema mapping and import

Priority countries: Canada, UK, Ireland, Australia, Japan, South Korea.

### Improve the schema

The [schema spec](https://github.com/opengolfapi/schema) defines what fields exist. To propose a new field:

1. Open an issue in [opengolfapi/schema](https://github.com/opengolfapi/schema/issues)
2. Explain: what field, why it's useful, where the data comes from
3. Community discusses, we reach consensus, field gets added

### Build with the API

Built something with OpenGolfAPI? We'd love to list it. Open an issue or PR adding your project to the README.

## Data standards

- **Coordinates:** WGS84 (EPSG:4326), decimal degrees, longitude before latitude in GeoJSON
- **Course names:** Title case, no abbreviations (e.g., "Pebble Beach Golf Links" not "PEBBLE BEACH GL")
- **Phone numbers:** E.164 format preferred, but we accept local formats
- **Websites:** Full URL including https://
- **Par:** Integer, 3-6 per hole, typically 27-72 total
- **Handicap index:** 1-18, lower = harder hole
- **Course type:** `public`, `private`, `semi-private`, `resort`, `municipal`, `military`

## What we don't accept

- Data from copyrighted or proprietary sources (commercial APIs, paid databases)
- Scraped data that violates a website's terms of service
- Bulk imports without prior discussion (open an issue first)
- Data that can't be licensed under ODbL

## Code of conduct

Be respectful. This is a community project. We don't tolerate harassment, spam, or bad-faith contributions. Violators get banned.

## License

By contributing, you agree that your contributions will be licensed under [ODbL 1.0](https://opendatacommons.org/licenses/odbl/1-0/), the same license as the rest of the dataset.

## Questions?

- Email: hello@opengolfapi.org
- GitHub Issues: [opengolfapi/data/issues](https://github.com/opengolfapi/data/issues)
- Open Collective: [opencollective.com/opengolfapi](https://opencollective.com/opengolfapi)
