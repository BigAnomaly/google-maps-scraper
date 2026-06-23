[Google Maps Scraper](https://apify.com/openclawai/google-maps-scraper?fpr=data)

Extract business data from Google Maps with no API key. Get names, addresses, phone numbers, websites, ratings, reviews, coordinates, opening hours, and more.

---

## What You Get

| Field | Description |
| --- | --- |
| `title` | Business name |
| `category` | Business type (e.g. "Coffee shop") |
| `address` | Full street address |
| `phone` | Phone number |
| `website` | Business website URL |
| `review_rating` | Average rating (1.0–5.0) |
| `review_count` | Total number of reviews |
| `status` | Open / Closed / Temporarily closed |
| `description` | Business description |
| `price_range` | Price indicator ($, $$, $$$) |
| `open_hours` | Hours per day of week |
| `latitude` | GPS latitude |
| `longitude` | GPS longitude |
| `plus_code` | Google Plus Code |
| `images` | Up to 5 photo URLs |
| `reviews` | Top 10 reviews (optional) |
| `link` | Direct Google Maps URL |

---

## Example Inputs

### Find restaurants in a city

```
{
    "query": "restaurants in New York",
    "maxResults": 50
}
```

### Lead gen — local businesses

```
{
    "query": "plumbers in Austin Texas",
    "maxResults": 100,
    "proxyConfiguration": {
        "useApifyProxy": true,
        "apifyProxyGroups": ["RESIDENTIAL"]
    }
}
```

### Scrape reviews too

```
{
    "query": "coffee shops in London",
    "maxResults": 20,
    "scrapeReviews": true
}
```

---

## Use Cases

- **Lead generation** — build lists of local businesses with contact info
- **Competitor research** — track competitor ratings, reviews, locations
- **Market analysis** — map business density in any area
- **Real estate** — find nearby amenities for property listings
- **Travel & hospitality** — aggregate restaurants, hotels, attractions
- **Review monitoring** — track what customers say about businesses

---

## Pricing

Pay per result scraped. You only pay for what you get.

| Volume | Cost per place |
| --- | --- |
| 1–100 | $0.005 |
| 100–1000 | $0.003 |
| 1000+ | $0.002 |

---

## Proxy Recommendation

Google Maps has aggressive bot detection. **Residential proxies are strongly recommended** for scraping at scale.

Configure in the `proxyConfiguration` input field using Apify Residential proxies.

---

## Output Example

```
{
    "title": "Joe's Coffee",
    "category": "Coffee shop",
    "address": "123 Main St, New York, NY 10001",
    "phone": "+1 (212) 555-0100",
    "website": "https://joescoffee.com",
    "review_rating": 4.5,
    "review_count": 843,
    "status": "Open",
    "description": "Cozy neighborhood cafe serving specialty espresso drinks.",
    "price_range": "$$",
    "open_hours": {
        "monday": "7:00 AM – 8:00 PM",
        "tuesday": "7:00 AM – 8:00 PM"
    },
    "latitude": 40.7128,
    "longitude": -74.006,
    "plus_code": "87G8+Q2 New York",
    "images": ["https://..."],
    "search_query": "coffee shops in New York",
    "scraped_at": "2026-04-08T12:00:00Z"
}
```