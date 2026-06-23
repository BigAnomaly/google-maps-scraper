[Google Maps Scraper](https://apify.com/thirdwatch/google-maps-scraper?fpr=data)

# Google Maps Scraper

> Scrape Google Maps search results — business names, addresses, phone numbers, websites, ratings, categories, GPS coordinates, and opening hours.

## What you get

Business-listing data from Google Maps for any search query in any location — "plumbers in Houston", "dentists in Chicago", "hotels in Paris". Returns structured results with contact info, ratings, categories, GPS coordinates, area/neighborhood, description, and current opening status. Ideal for lead generation, market research, and location intelligence.

## Output fields

| Field | Description |
| --- | --- |
| `name` | Business name |
| `address` | Full formatted address |
| `phone` | Phone number |
| `website` | Business website URL |
| `rating` | Google rating (1.0-5.0) |
| `categories` | Business categories (e.g., "Plumber", "Electrician") |
| `latitude` | GPS latitude |
| `longitude` | GPS longitude |
| `place_id` | Google Place ID |
| `google_maps_url` | Direct link to the Google Maps listing |
| `area` | Neighborhood / area name |
| `description` | Business description (when available) |
| `opening_status` | Current status (e.g., "Open - Closes 8 PM") |
| `opening_hours` | Structured day-by-day schedule (when available) |

## Example output

```
{
    "name": "Village Plumbing, Air & Electric",
    "address": "10644 W Little York Rd Suite 200, Houston, TX 77041",
    "phone": "(281) 607-5357",
    "website": "https://www.villageplumbing.com/",
    "rating": 4.8,
    "categories": ["Plumber", "Air conditioning contractor", "Electrician"],
    "latitude": 29.8640568,
    "longitude": -95.5618629,
    "place_id": "ChIJIc-2aF_AQIYRJabyrgymSoA",
    "google_maps_url": "https://www.google.com/maps/place/?q=place_id:ChIJIc-2aF_AQIYRJabyrgymSoA",
    "area": "Carverdale",
    "opening_status": "Open - Closes 8 PM"
}
```

## Input parameters

| Parameter | Required | Description |
| --- | --- | --- |
| `searchQuery` | Yes | Google Maps search query (e.g., "plumbers in Houston", "dentists in Chicago", "hotels in Paris"). |
| `maxResults` | No | Maximum results (1-100). Each page fetches up to 20. Default `20`. |
| `language` | No | Language code (`en`, `es`, `fr`, `de`, `ja`, etc.). Default `en`. |
| `region` | No | Country code to bias results (`us`, `uk`, `in`, `de`, etc.). Default `us`. |

## Use cases

- **Lead generation**: Build prospect lists of local businesses with phone and website for cold outreach.
- **Market research**: Analyze business density, rating bands, and category mix in any city or neighborhood.
- **Local SEO**: Audit competitor listings and track ratings over time for clients.
- **Data enrichment**: Append addresses, GPS coordinates, and categories to CRM and customer records.
- **Real estate and retail siting**: Map businesses around a property or territory to inform site-selection.
- **Field operations**: Generate contact lists for door-to-door or phone-based outreach campaigns.

 

## Use cases & recipes

Step-by-step guides on [thirdwatch.dev/blog](https://thirdwatch.dev/blog):

- [Build a Local Business Database with Google Maps (2026)](https://thirdwatch.dev/blog/build-local-business-database-with-google-maps)
- [Find Restaurants by Cuisine and Rating on Google Maps (2026)](https://thirdwatch.dev/blog/find-restaurants-by-cuisine-and-rating)
- [Scrape Business Phone and Website from Google Maps (2026)](https://thirdwatch.dev/blog/scrape-business-phone-and-website-from-google-maps)
- [Scrape Google Maps Businesses for Lead Generation (2026)](https://thirdwatch.dev/blog/scrape-google-maps-businesses-for-lead-gen)

 -end

## Pricing

Pay-per-result pricing. Tiered discounts apply automatically based on usage volume.

| Tier | Price per result |
| --- | --- |
| FREE | $0.002 |
| BRONZE | $0.0017 |
| SILVER | $0.0013 |
| GOLD | $0.001 |

## Limitations

- Review count and price level are not available from the search response — only `rating` and categories.
- Up to 100 results per single `searchQuery`. For more, split into narrower queries (e.g., per neighborhood).
- Results depend on Google Maps' own ranking for that query, language, and region.
- Sponsored results are handled as Google Maps presents them.
- Opening hours are returned only when Google Maps itself publishes a structured schedule for the business.

## Compared to alternatives

- **vs. compass/crawler-google-places** (350K users, $0.004/result): Our $0.001-$0.002 tiered pricing is 2-4x cheaper for the same core fields (name, phone, website, rating, coordinates).
- **vs. Google Places API**: The Places API charges per call, caps responses at 60 results per query, and requires billing setup — this actor returns 100 results per query with simpler pricing.

Pairs well with [Yelp Business Scraper](https://apify.com/thirdwatch/yelp-business-scraper) and [TripAdvisor Scraper](https://apify.com/thirdwatch/tripadvisor-scraper) for full local-business intelligence.

## FAQ

**Can I scrape outside the US?**
Yes. Set `region` to the country code (e.g., `uk`, `in`, `de`, `fr`) and optionally `language` to a matching locale.

**Why isn't review count in the output?**
Review counts are not exposed in Google Maps' search-results response — they only appear on individual business pages. This actor is a search-results scraper; review count and price level are not retrievable at this level.

**Can I get more than 100 results?**
Not in one query. Google Maps caps search-results depth — for larger lists, split your search geographically (e.g., "plumbers in Houston Heights" + "plumbers in Montrose" + ...).

**Does the output include opening hours?**
Yes, when Google Maps publishes a structured schedule for the business. The `opening_hours` field returns a day-by-day array when available, and `opening_status` gives the live "Open / Closes at X" label.

**How fresh is the data?**
Pulled live at run time — as fresh as Google Maps itself.

Last verified: 2026-04

More scrapers at [thirdwatch.dev](https://thirdwatch.dev).