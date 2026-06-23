[Google Maps Scraper](https://apify.com/sovereigntaylor/google-maps-scraper?fpr=data)

# Google Maps Business Scraper

Extract business data from Google Maps at scale. Get names, addresses, phone numbers, websites, ratings, reviews, hours, coordinates, and more for any business type in any location worldwide.

## Why This Actor?

- **Complete data extraction** — Get 15+ data fields per business including contact info, hours, and GPS coordinates
- **Any location worldwide** — Search businesses in any city, region, or country
- **Structured output** — Clean JSON ready for your CRM, spreadsheet, or database
- **Pay per result** — Only pay for successfully scraped listings, no wasted spend
- **Fast & reliable** — Built with proxy rotation and anti-blocking for consistent results

## Features

- Search any business type by keyword (restaurants, dentists, plumbers, hotels, etc.)
- Filter by location (city, state, zip code, or coordinates)
- Extract: name, address, phone, website, email, rating, reviews, price level
- GPS coordinates for mapping and geofencing
- Business hours and open/closed status
- Google Maps URL for each listing
- Category and subcategory classification
- Configurable zoom level and result limits
- Automatic pagination for large result sets
- Proxy support for reliable extraction

## Input Parameters

| Field | Type | Default | Description |
| --- | --- | --- | --- |
| `searchTerm` | string | *required* | Business type to search (e.g., "pizza", "dentist near me", "gym") |
| `location` | string | `""` | City or area (e.g., "Manhattan, New York", "London, UK", "Tokyo") |
| `maxResults` | number | `20` | Maximum number of listings to return (1-500) |
| `zoom` | number | `13` | Map zoom level (1-21). Lower = wider area, higher = more focused |

## Output Example

Each business listing includes all available data:

```
{
  "name": "Joe's Pizza",
  "address": "7 Carmine St, New York, NY 10014",
  "phone": "+1 212-366-1182",
  "website": "https://joespizzanyc.com",
  "rating": 4.4,
  "reviewCount": 8500,
  "priceLevel": "$",
  "category": "Pizza restaurant",
  "hours": [
    "Monday: 10:00 AM – 4:00 AM",
    "Tuesday: 10:00 AM – 4:00 AM",
    "Wednesday: 10:00 AM – 4:00 AM",
    "Thursday: 10:00 AM – 4:00 AM",
    "Friday: 10:00 AM – 5:00 AM",
    "Saturday: 10:00 AM – 5:00 AM",
    "Sunday: 10:00 AM – 4:00 AM"
  ],
  "coordinates": {
    "lat": 40.7305,
    "lng": -74.0023
  },
  "url": "https://maps.google.com/maps?cid=12345678901234567",
  "placeId": "ChIJHQl_OJBZwokR..."
}
```

## Use Cases

### Lead Generation & Sales Prospecting

Build targeted prospect lists for cold outreach. Search for any business type in any location to build lists with phone numbers and websites for your sales team.

**Example:** Find all dentists in Houston, TX:

```
{
  "searchTerm": "dentist",
  "location": "Houston, TX",
  "maxResults": 200
}
```

### Local SEO Audit & Competitor Analysis

Analyze competitors in your area. See their ratings, review counts, and how they rank on Google Maps. Identify gaps in the market.

**Example:** Analyze coffee shops in downtown Seattle:

```
{
  "searchTerm": "coffee shop",
  "location": "downtown Seattle, WA",
  "maxResults": 100
}
```

### Market Research & Location Intelligence

Analyze business density, pricing levels, and customer satisfaction across different areas. Perfect for site selection, franchise planning, and market entry analysis.

**Example:** Map all gyms in Brooklyn:

```
{
  "searchTerm": "gym",
  "location": "Brooklyn, NY",
  "maxResults": 300
}
```

### Real Estate Analysis

Map amenities and services near properties. Analyze walkability scores, restaurant density, and proximity to key services for real estate valuations.

### Travel & Hospitality

Build local guides, restaurant lists, and attraction databases for travel content or concierge services.

### Data Enrichment

Enrich your existing business database with Google Maps data — add missing phone numbers, websites, ratings, and coordinates.

## Integration Examples

### Export to Google Sheets

Use the Apify Google Sheets integration to automatically export results to a spreadsheet for your team.

### Connect to CRM

Push leads directly to HubSpot, Salesforce, or Pipedrive using Apify's built-in integrations.

### API Access

Call this actor programmatically from your application:

```
const { ApifyClient } = require('apify-client');
const client = new ApifyClient({ token: 'YOUR_API_TOKEN' });

const run = await client.actor('sovereigntaylor/google-maps-scraper').call({
    searchTerm: 'plumber',
    location: 'Austin, TX',
    maxResults: 50
});

const { items } = await client.dataset(run.defaultDatasetId).listItems();
console.log(items);
```

```
from apify_client import ApifyClient

client = ApifyClient('YOUR_API_TOKEN')
run = client.actor('sovereigntaylor/google-maps-scraper').call(run_input={
    'searchTerm': 'plumber',
    'location': 'Austin, TX',
    'maxResults': 50
})

items = list(client.dataset(run['defaultDatasetId']).iterate_items())
```

## FAQ

**How many results can I get?**
Up to 500 per run. For more, run multiple searches with different locations or zoom levels.

**Which countries are supported?**
Any country where Google Maps is available — over 200 countries and territories.

**How fresh is the data?**
Data is scraped in real-time from Google Maps. You always get the latest available information.

**Can I schedule regular scrapes?**
Yes! Use Apify's built-in scheduler to run this actor daily, weekly, or at any interval.

**What format is the output?**
JSON, CSV, or Excel — download directly or use the API to integrate with your systems.

## Pricing

Pay per result — you're only charged for each business listing successfully extracted. No monthly fees, no minimum spend. See the Pricing tab for current rates.

## Related Actors

- [Google Maps Email Extractor](https://apify.com/sovereigntaylor/google-maps-email-extractor) — Extract emails from Google Maps business websites
- [Google Search Scraper](https://apify.com/sovereigntaylor/google-search-scraper) — Scrape Google search results
- [Google Shopping Scraper](https://apify.com/sovereigntaylor/google-shopping-scraper) — Extract Google Shopping product data
- [B2B Leads Finder](https://apify.com/sovereigntaylor/b2b-leads-finder) — Multi-source B2B lead generation