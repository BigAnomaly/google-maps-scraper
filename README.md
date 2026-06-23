[Google Maps Scraper](https://apify.com/cryptosignals/google-maps-scraper?fpr=data)

# Google Maps Scraper

## Use as MCP Tool

This actor is available as an **MCP (Model Context Protocol) tool** — call it directly from Claude, VS Code Copilot, or ChatGPT without writing a line of code. [Configure via Apify MCP Configurator](https://apify.com/apify/actors-mcp-server).

Extract business listings from Google Maps at scale — names, addresses, phone numbers, ratings, reviews, opening hours, categories, and GPS coordinates. Search by keyword and location or supply direct Google Maps place URLs. No API key needed.

## Why use this scraper?

The official Google Places API charges per request and has strict usage limits. This actor scrapes Google Maps search results directly using a real browser, giving you **rich business data** at a fraction of the cost. Perfect for lead generation, market research, local SEO audits, and building business directories.

## Key features

- **No API key needed** — uses browser-based scraping for authentic results
- **Search by keyword + location** — e.g. "dentist in Chicago"
- **Direct URL support** — scrape specific Google Maps place pages
- **Rich data extraction** — ratings, reviews, hours, phone, website, GPS coordinates
- **Country/locale support** — get results localized to any country
- **Up to 100 results** per search query
- **Pay per result** pricing — only pay for data delivered

## Use cases

### 1. Lead generation for sales teams

Build targeted prospect lists of businesses by industry and location. Get phone numbers, websites, and addresses for outreach campaigns.

### 2. Local SEO audits

Analyze competitor rankings, review counts, and ratings in local search results. Identify gaps in your Google Maps presence.

### 3. Market research & site selection

Map the competitive landscape for any industry in any area. Use GPS coordinates and review data to identify underserved markets.

### 4. Business directory building

Create niche business directories (e.g., vegan restaurants in Portland, coworking spaces in Berlin) with verified, up-to-date data.

### 5. Real estate & investment analysis

Evaluate neighborhoods by analyzing nearby business density, quality (ratings), and types. Great for commercial real estate due diligence.

### 6. Franchise & expansion planning

Research competitor density and customer sentiment in target markets before opening new locations.

### 7. Review monitoring & reputation analysis

Track ratings and review counts for your business and competitors over time by scheduling regular scraping runs.

### 8. Academic & urban planning research

Collect geospatial business data for urban studies, economic geography research, and accessibility analysis.

### 9. Supply chain & vendor discovery

Find manufacturers, suppliers, and service providers in specific regions with verified contact information.

## Input parameters

| Parameter | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| `searchQuery` | string | ✅ Yes | — | Search term to look up on Google Maps, e.g. `"coffee shops in New York"`, `"dentist near 90210"` |
| `maxResults` | integer | No | `5` | Maximum number of results to extract (1–100) |
| `country` | string | No | `"US"` | ISO country code for locale — affects language and regional results (`US`, `GB`, `DE`, `FR`, `JP`, etc.) |
| `startUrls` | array | No | `[]` | Direct Google Maps place URLs to scrape instead of searching. Useful for scraping specific known businesses. |

### Example input — search mode

```
{
  "searchQuery": "italian restaurant in San Francisco",
  "maxResults": 30,
  "country": "US"
}
```

### Example input — direct URL mode

```
{
  "startUrls": [
    { "url": "https://www.google.com/maps/place/Tartine+Bakery" },
    { "url": "https://www.google.com/maps/place/Blue+Bottle+Coffee" }
  ],
  "maxResults": 10
}
```

### Search query tips

- **Be specific with location**: `"plumber in Austin TX"` works better than `"plumber"`
- **Use ZIP codes**: `"dentist near 60601"` for precise geographic targeting
- **Category searches**: `"hotels"`, `"gas stations"`, `"EV charging stations"`
- **Near landmarks**: `"restaurants near Times Square"`

## Output format

Each result is a structured JSON object:

```
{
  "name": "Bright Smile Dental",
  "address": "123 N Michigan Ave, Chicago, IL 60601",
  "phone": "+1 312-555-0199",
  "website": "https://brightsmile.example.com",
  "rating": 4.7,
  "reviewCount": 342,
  "category": "Dentist",
  "latitude": 41.8827,
  "longitude": -87.6246,
  "openingHours": {
    "Monday": "8:00 AM – 5:00 PM",
    "Tuesday": "8:00 AM – 5:00 PM",
    "Wednesday": "8:00 AM – 5:00 PM",
    "Thursday": "8:00 AM – 7:00 PM",
    "Friday": "8:00 AM – 3:00 PM",
    "Saturday": "Closed",
    "Sunday": "Closed"
  },
  "url": "https://maps.google.com/maps?cid=1234567890",
  "placeId": "ChIJa2T3cPrTD4gRSq6K0v6y8JU"
}
```

## Data fields reference

| Field | Type | Description |
| --- | --- | --- |
| `name` | string | Business name |
| `address` | string | Full street address |
| `phone` | string | Phone number with country code |
| `website` | string | Business website URL |
| `rating` | float | Google star rating (0–5) |
| `reviewCount` | integer | Total number of Google reviews |
| `category` | string | Business category (e.g., Restaurant, Dentist) |
| `latitude` | float | GPS latitude coordinate |
| `longitude` | float | GPS longitude coordinate |
| `openingHours` | object | Operating hours for each day of the week |
| `url` | string | Google Maps listing URL |
| `placeId` | string | Google Place ID for deduplication |

## How to use with Python

```
from apify_client import ApifyClient

client = ApifyClient("YOUR_API_TOKEN")

run = client.actor("cryptosignals/google-maps-scraper").call(
    run_input={
        "searchQuery": "plumber in Austin TX",
        "maxResults": 30,
        "country": "US",
    }
)

for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(f"{item['name']} — {item.get('rating', 'N/A')} stars ({item.get('reviewCount', 0)} reviews)")
    print(f"  Address: {item.get('address')}")
    print(f"  Phone:   {item.get('phone')}")
    print(f"  Website: {item.get('website')}")
    print()
```

### Export to CSV with pandas

```
import pandas as pd
from apify_client import ApifyClient

client = ApifyClient("YOUR_API_TOKEN")
run = client.actor("cryptosignals/google-maps-scraper").call(
    run_input={"searchQuery": "gym in Miami", "maxResults": 50}
)

items = list(client.dataset(run["defaultDatasetId"]).iterate_items())
df = pd.DataFrame(items)
df.to_csv("miami_gyms.csv", index=False)
print(f"Exported {len(df)} businesses to CSV")
```

## How to use with Node.js

```
import { ApifyClient } from 'apify-client';

const client = new ApifyClient({ token: 'YOUR_API_TOKEN' });

const run = await client.actor('cryptosignals/google-maps-scraper').call({
    searchQuery: 'coffee shops in Seattle',
    maxResults: 20,
    country: 'US',
});

const { items } = await client.dataset(run.defaultDatasetId).listItems();
for (const item of items) {
    console.log(`${item.name} — ${item.rating} stars (${item.reviewCount} reviews)`);
    console.log(`  ${item.address}`);
    console.log(`  ${item.phone || 'No phone'} | ${item.website || 'No website'}`);
}
```

## How to use via API

```
curl -X POST "https://api.apify.com/v2/acts/cryptosignals~google-maps-scraper/runs?token=YOUR_API_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"searchQuery": "dentist in Chicago", "maxResults": 20, "country": "US"}'
```

## Pricing

This actor uses Apify's **Pay Per Result** model. You are charged only for successfully extracted business listings — not for failed searches or empty results.

| Plan | Included results | Best for |
| --- | --- | --- |
| Free | Trial usage | Testing with a few queries |
| Personal | Low-volume | Individual research projects |
| Team | Medium-volume | Sales teams and agencies |
| Business | High-volume | Large-scale lead generation |

Start with the free tier to test your queries before scaling up.

## Integrations

Export your data anywhere:

- **Google Sheets** — one-click export to spreadsheets
- **Webhooks** — trigger your pipeline when a run finishes
- **Zapier / Make** — connect to 5,000+ apps and CRMs
- **Amazon S3 / Google Cloud Storage** — store in your data lake
- **Slack / Email** — get notified when data is ready
- **Apify API** — full programmatic access from any language
- **HubSpot / Salesforce** — push leads directly to your CRM via Zapier

## Tips for best results

1. **Be specific with locations** — "coffee shop in Brooklyn NY" returns better results than "coffee shop"
2. **Start with a small `maxResults`** (5-10) to verify data quality before scaling up
3. **Use `startUrls`** when you already know which businesses to scrape — it is faster and more reliable than searching
4. **Schedule regular runs** to keep your business data fresh — ratings and hours change frequently
5. **Combine with geocoding** — use the GPS coordinates for mapping and geographic analysis

## Frequently Asked Questions

### Does this require a Google Maps API key?

No. This actor uses browser automation to scrape Google Maps directly. No API key, billing account, or Google Cloud setup is needed.

### How many results can I get per search?

Up to 100 results per search query. Google Maps typically shows 20-60 results for most searches. For comprehensive coverage of a large area, break your search into smaller geographic zones.

### Can I scrape Google Maps in different countries and languages?

Yes. Set the `country` parameter to any ISO country code (e.g., `DE` for Germany, `JP` for Japan). Results will be returned in the local language and format.

### How accurate is the data?

The data comes directly from Google Maps listings. Ratings, review counts, addresses, and phone numbers reflect what is currently shown on Google Maps.

### Can I scrape reviews text, not just review counts?

This actor extracts the review count and average rating. For full review text extraction, look for a dedicated Google Maps reviews scraper.

### What if Google blocks the scraper?

The actor uses Playwright with realistic browser fingerprints. For best results with large volumes, use residential proxies via Apify's proxy configuration.

### Can I schedule automatic scraping?

Yes. Use Apify's built-in scheduler to run this actor on any interval — hourly, daily, weekly, or with custom cron expressions. Perfect for keeping your lead database up to date.

### What output formats are available?

JSON, CSV, Excel, and XML. You can also push results directly to Google Sheets, webhooks, S3, and more via Apify's integration options.

### Is scraping Google Maps legal?

Scraping publicly available business listing data is generally permissible. This actor accesses only public information displayed on Google Maps. Always consult your legal team and review Google's Terms of Service for your specific use case.

### How does this compare to the Google Places API?

The Google Places API charges $17 per 1,000 requests for basic data and $32 per 1,000 for contact details. This actor provides the same data at a lower cost, with no API key setup or billing configuration required.