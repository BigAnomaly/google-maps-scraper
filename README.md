[Google Maps Scraper](https://apify.com/makework36/google-maps-scraper?fpr=data)

# Google Maps Business Scraper

Extract business names, addresses, ratings, categories, and GPS coordinates from Google Maps search results.

## What data does it extract?

| Field | Description |
| --- | --- |
| `name` | Business name |
| `category` | Business category (e.g. `Pizza restaurant`) |
| `rating` | Average rating (1-5) |
| `address` | Full street address |
| `lat` | GPS latitude |
| `lng` | GPS longitude |
| `placeId` | Google Place ID |
| `mapsUrl` | Direct Google Maps link |

## Use cases

- **Market research** -- Find all businesses of a type in any city to analyze density and competition
- **Business directories** -- Build local listings with names, addresses, and ratings at scale
- **Sales prospecting** -- Generate target lists by category and location for outreach

## How to use

Search by category and city:

```
{
    "searchQueries": ["pizza restaurants", "dentists"],
    "locationQuery": "New York, NY",
    "maxResults": 100
}
```

Location already in the query:

```
{
    "searchQueries": ["coffee shops in San Francisco", "gyms near downtown Chicago"],
    "maxResults": 50
}
```

## Input parameters

| Parameter | Type | Default | Description |
| --- | --- | --- | --- |
| `searchQueries` | string[] | required | Search terms like `"coffee shops"`, `"lawyers"`, `"gyms"` |
| `locationQuery` | string | `""` | City or region. Leave empty if already in the query. |
| `maxResults` | integer | `20` | Max places per query (up to 100) |

## Output example

```
{
    "name": "Joe's Pizza",
    "category": "Pizza restaurant",
    "rating": 4.5,
    "address": "7 Carmine St, New York, NY 10014",
    "lat": 40.7305,
    "lng": -74.0021,
    "placeId": "0x89c2598f57ae9429:0x89b3e834c0ae8612",
    "mapsUrl": "https://www.google.com/maps/place/...",
    "searchQuery": "pizza restaurants",
    "locationQuery": "New York, NY",
    "scrapedAt": "2026-03-27T20:00:00.000Z"
}
```

## Performance & cost

- ~$1 per 1,000 results
- No proxies needed for most searches
- Typically 100 results in under 30 seconds

## FAQ

**Do I need a proxy?**
No. Works without proxies for most queries.

**Can I scrape multiple cities at once?**
Yes -- include the city in each query: `["dentists in Chicago", "dentists in Houston"]`.

**Need phone numbers, emails, and opening hours?**
Use our Google Maps Lead Scraper which includes full contact data.