[Google Maps Scraper](https://apify.com/lanky_quantifier/google-maps-scraper?fpr=data)

# Google Maps Business Leads Scraper

Extract structured business data from Google Maps — names, addresses, phone numbers, websites, ratings, and review counts. Built for B2B sales teams, agencies, and market researchers who need local business leads at scale.

## What does it do?

Send any search query (like `"HVAC companies in Berlin"` or `"dentists in New York"`), and the scraper returns a clean JSON list of matching businesses with full contact and metadata — no API key required.

## Output data

Each result includes:

| Field | Description |
| --- | --- |
| `name` | Business name |
| `address` | Full street address |
| `phone` | Phone number (if available) |
| `website` | Website URL |
| `rating` | Google star rating (1–5) |
| `reviewCount` | Total number of reviews |
| `category` | Business category |
| `placeId` | Google Maps Place ID (CID) |
| `mapsUrl` | Direct Google Maps link |

## Example input

```
{
  "searchQueries": ["electricians in Munich", "plumbers in Hamburg"],
  "maxResultsPerQuery": 50,
  "language": "de"
}
```

## Example output

```
[
  {
    "name": "Elektro Müller GmbH",
    "address": "Hauptstraße 12, 80331 München",
    "phone": "+49 89 123456",
    "website": "https://elektro-mueller.de",
    "rating": 4.7,
    "reviewCount": 84,
    "category": "Elektriker",
    "placeId": "ChIJN1t_tDeuEmsRUsoyG83frY4",
    "mapsUrl": "https://maps.google.com/?cid=..."
  }
]
```

## Use cases

- **B2B cold outreach** — build prospect lists for any city, niche, and region
- **Market research** — analyze competitor density and ratings in a territory
- **Agency lead gen** — resell local business lists to SMB clients
- **Directory building** — populate a local business directory with fresh data
- **HVAC / trades / legal / medical** — any vertical with a physical presence

## Key features

- **No API key needed** — works without Google API credentials
- **Multi-query** — run multiple searches in one job
- **Language support** — results in any Google Maps language (`en`, `de`, `fr`, `ru`, etc.)
- **Smart pagination** — automatically collects all results from search pages
- **Deduplication** — no duplicate entries in output
- **Stealth mode** — built-in headers to avoid bot detection

## Pricing

Pay per result via Apify PAY_PER_EVENT. You only pay for data you actually receive.

## Support

Questions or custom requirements → [vhub.systems@gmail.com](mailto:vhub.systems@gmail.com)