[Google Maps Scraper](https://apify.com/santamaria-automations/google-maps-scraper?fpr=data)

# Google Maps Scraper -- Extract Business Data from Any Location on Earth

Scrape Google Maps search results worldwide. Get business names, addresses, phone numbers, websites, reviews, ratings, opening hours, GPS coordinates, and 30+ structured fields per place. Fast, reliable, and priced per result.

## Why this scraper

- **All-inclusive pricing** -- 30+ fields per place at one flat rate. No extra charges for reviews, photos, hours, or address parsing.
- **Extremely fast** -- Returns results in seconds, not minutes.
- **Volume-friendly pricing** -- $1.00 per 1,000 places.
- **Built-in enrichment** -- optionally trigger AI-powered contact extraction or job listing extraction on every website found.
- **Your LLM, your choice** -- Gemini (recommended, free tier available), Groq, or OpenRouter with automatic fallback between providers.
- **Works worldwide** -- any country, any language. Pass an ISO language code and get localized results.

## Use with AI Agents (MCP)

Connect this actor to any MCP-compatible AI client — Claude Desktop, Claude.ai, Cursor, VS Code, LangChain, LlamaIndex, or custom agents.

**Apify MCP server URL:**

```
https://mcp.apify.com?tools=santamaria-automations/google-maps-scraper
```

**Example prompt once connected:**

> "Use `google-maps-scraper` to process data with google maps. Return results as a table."

Clients that support dynamic tool discovery (Claude.ai, VS Code) will receive the full input schema automatically via `add-actor`.

## Quick start

### Simple search

Pass plain search strings. Include the location in the string itself:

```
{
  "searchStrings": [
    "restaurants in Paris",
    "coffee shops in Tokyo",
    "dentists in New York"
  ],
  "maxResults": 20
}
```

### Structured queries

For programmatic use with company IDs, location filtering, and country codes:

```
{
  "queries": [
    {
      "query": "software companies",
      "location": "Berlin",
      "country": "DE",
      "company_id": "my-internal-id-123"
    },
    {
      "query": "plumbers",
      "location": "London",
      "country": "GB"
    }
  ],
  "maxResults": 50,
  "language": "en"
}
```

### With contact extraction

Find businesses and automatically extract team contacts from their websites:

```
{
  "searchStrings": ["IT companies in Munich"],
  "maxResults": 20,
  "enableContactExtraction": true,
  "geminiApiKey": "your-gemini-api-key"
}
```

### With job listing extraction

Find businesses and automatically extract open positions from their career pages:

```
{
  "searchStrings": ["software companies in Berlin"],
  "maxResults": 20,
  "enableJobExtraction": true,
  "geminiApiKey": "your-gemini-api-key"
}
```

## Input parameters

| Parameter | Type | Default | Description |
| --- | --- | --- | --- |
| `searchStrings` | string[] | `[]` | Simple search strings. Include location in the string for geo-targeting. |
| `queries` | object[] | `[]` | Structured queries with optional `query`, `location`, `country`, `company_id`. |
| `maxResults` | integer | `20` | Results per query. Max ~120 (Google Maps limit). |
| `language` | string | `"en"` | ISO 639-1 language code (en, de, fr, ja, es, pt, it, ko, zh, ar, etc.). |
| `enableContactExtraction` | boolean | `false` | After scraping, extract contacts from company websites via AI. |
| `enableJobExtraction` | boolean | `false` | After scraping, extract job listings from career pages via AI. |
| `enableBrowserFallback` | boolean | `false` | Re-scrape JS-rendered sites (React, Vue, Angular) with a full browser. Catches ~25% more sites. |
| `outputLanguage` | string | `"en"` | Language for AI-extracted fields (en/de/fr/it/es/pt/nl/auto). |
| `geminiApiKey` | string | -- | Gemini API key. Recommended for add-ons. Free tier: 1M tokens/min. |
| `groqApiKey` | string | -- | Groq API key. Ultra-fast inference. Optional fallback. |
| `openrouterApiKey` | string | -- | OpenRouter API key. Access 100+ models. Optional fallback. |
| `excludeCids` | string[] | `[]` | Google CIDs to skip. Useful for excluding already-scraped places. |
| `maxConcurrency` | integer | `10` | Parallel requests (1-20). |
| `requestDelay` | integer | `300` | Delay between pagination requests in milliseconds (100-10,000). |
| `proxyConfiguration` | object | Apify proxy | Proxy settings. Datacenter proxies work well. |

Use either `searchStrings` or `queries` (or both). With `searchStrings`, each string is sent directly to Google Maps. With `queries`, you can separate the search term from the location and attach your own `company_id` for linking results back to your data.

## Output

Each result contains 30+ fields. Here is an example:

```
{
  "company_id": "restaurants in Paris",
  "title": "Le Petit Cler",
  "category": "French restaurant",
  "categories": ["French restaurant", "Restaurant"],
  "address": "3 Rue Cler, 75007 Paris, France",
  "complete_address": {
    "street": "3 Rue Cler",
    "city": "Paris",
    "postal_code": "75007",
    "state": "Ile-de-France",
    "country": "France"
  },
  "latitude": 48.8571,
  "longitude": 2.3007,
  "plus_code": "8FW4V87C+X3",
  "timezone": "Europe/Paris",
  "phone": "+33 1 45 51 24 52",
  "website": "https://www.lepetitcler.com/",
  "emails": [],
  "review_rating": 4.5,
  "review_count": 1823,
  "reviews_per_rating": { "1": 42, "2": 31, "3": 89, "4": 312, "5": 1349 },
  "reviews_link": "https://search.google.com/local/reviews?placeid=...",
  "user_reviews": [
    {
      "name": "Marie Dupont",
      "rating": 5,
      "text": "Excellent cuisine, warm atmosphere...",
      "published_at": "2 months ago"
    }
  ],
  "status": "OPERATIONAL",
  "price_range": "$$",
  "open_hours": {
    "Monday": ["12:00-14:30", "19:00-22:30"],
    "Tuesday": ["12:00-14:30", "19:00-22:30"],
    "Wednesday": ["12:00-14:30", "19:00-22:30"],
    "Thursday": ["12:00-14:30", "19:00-22:30"],
    "Friday": ["12:00-14:30", "19:00-23:00"],
    "Saturday": ["12:00-23:00"],
    "Sunday": []
  },
  "thumbnail": "https://lh3.googleusercontent.com/places/...",
  "images": [
    { "title": "Interior", "image": "https://lh3.googleusercontent.com/..." }
  ],
  "owner": { "name": "Le Petit Cler", "link": "https://maps.google.com/..." },
  "about": [
    { "id": "dine_in", "name": "Dine-in" },
    { "id": "reservations", "name": "Reservations" }
  ],
  "reservations": [
    { "link": "https://www.thefork.com/...", "source": "TheFork" }
  ],
  "order_online": [],
  "menu": { "link": "https://www.lepetitcler.com/menu", "source": "lepetitcler.com" },
  "description": "Cozy French bistro in the heart of the 7th arrondissement.",
  "link": "https://www.google.com/maps/place/Le+Petit+Cler/...",
  "cid": "12345678901234567",
  "data_id": "0x47e671a4e...",
  "searchString": "restaurants in Paris",
  "_rank": 1,
  "scraped_at": "2026-03-05T10:30:00.000Z"
}
```

### Complete field reference

| Field | Type | Description |
| --- | --- | --- |
| `company_id` | string | Your reference ID (from `queries`) or the search string |
| `title` | string | Business name |
| `category` | string | Primary Google Maps category |
| `categories` | string[] | All assigned categories |
| `address` | string | Full formatted address |
| `complete_address` | object | Parsed components: street, city, postal_code, state, country |
| `latitude` | number | GPS latitude |
| `longitude` | number | GPS longitude |
| `plus_code` | string | Google Plus Code |
| `timezone` | string | IANA timezone identifier |
| `phone` | string | Phone number |
| `website` | string | Website URL |
| `emails` | string[] | Email addresses found on the listing |
| `open_hours` | object | Opening hours grouped by day of week |
| `popular_times` | object | Visitor traffic patterns by hour and day |
| `price_range` | string | Price level ($ to $$$$) |
| `status` | string | OPERATIONAL, CLOSED_TEMPORARILY, or CLOSED_PERMANENTLY |
| `review_count` | integer | Total number of reviews |
| `review_rating` | number | Average rating (1.0 to 5.0) |
| `reviews_per_rating` | object | Breakdown of reviews by star rating (1 through 5) |
| `reviews_link` | string | Direct URL to all reviews |
| `user_reviews` | array | Sample reviews with name, rating, text, date, owner response |
| `thumbnail` | string | Main business photo URL |
| `images` | array | Additional photos with titles |
| `reservations` | array | Reservation links with source (TheFork, OpenTable, etc.) |
| `order_online` | array | Online ordering links with source |
| `menu` | object | Menu link and source |
| `owner` | object | Business owner name and profile link |
| `about` | array | Amenities and features (dine-in, Wi-Fi, wheelchair access, etc.) |
| `description` | string | Business description from Google |
| `link` | string | Full Google Maps URL for this place |
| `cid` | string | Google Maps CID -- stable identifier that persists across name/address changes |
| `data_id` | string | Google internal data ID |
| `searchString` | string | The search query that produced this result |
| `_rank` | integer | Position in search results (1-based) |
| `scraped_at` | string | ISO 8601 timestamp |

## Enrichment add-ons

After the Maps scrape completes, this actor can automatically trigger AI-powered extraction on every website found in the results. Each add-on runs as a separate actor and produces its own dataset.

### Contact extraction

Extracts team member names, email addresses, phone numbers, positions, and departments from company websites. Powered by the [Website Contact Extractor](https://apify.com/santamaria-automations/website-contact-extractor).

Enable it by setting `enableContactExtraction: true` and providing at least one LLM API key. The sub-actor run ID is stored in the key-value store as `CONTACT_EXTRACTOR_RUN_ID`.

### Job listing extraction

Extracts open positions, job titles, locations, departments, and career page URLs from company websites. Powered by the [Website Job Extractor](https://apify.com/santamaria-automations/website-job-extractor).

Enable it by setting `enableJobExtraction: true` and providing at least one LLM API key. The sub-actor run ID is stored in the key-value store as `JOB_EXTRACTOR_RUN_ID`.

### Browser fallback

Some company websites are built with JavaScript frameworks (React, Vue, Angular) that require a full browser to render. When `enableBrowserFallback` is set to `true`, the contact/job extractors will automatically re-scrape these sites with a real browser. This catches ~25% more sites but increases cost and runtime. Only applies when contact or job extraction is enabled.

### LLM API keys

Both add-ons use LLMs to extract structured data. Provide one or more API keys. When multiple keys are provided, the system uses them in priority order with automatic fallback:

1. **Gemini** (recommended) -- Best quality-to-cost ratio. Free tier includes 1M tokens/min. Get a key at [Google AI Studio](https://aistudio.google.com/app/apikey).
2. **Groq** (optional) -- Ultra-fast inference. Get a key at [Groq Console](https://console.groq.com/keys).
3. **OpenRouter** (optional) -- Access to 100+ models. Get a key at [OpenRouter](https://openrouter.ai/keys).

One key is sufficient. With multiple keys, if the primary provider hits a rate limit, the system falls back to the next available provider automatically.

## Use cases

- **Lead generation** -- Search for businesses by type and location. Get phone numbers, websites, and emails in one run.
- **Market research** -- Map competitors in a geographic area with ratings, review counts, and price ranges.
- **Company enrichment** -- Add addresses, phone numbers, GPS coordinates, and opening hours to your existing database.
- **Local SEO monitoring** -- Track your business listing and competitor rankings across locations.
- **Real estate analysis** -- Find nearby amenities, restaurants, and services for property listings.
- **Hiring intelligence** -- Discover companies in a region and extract their open positions in a single pipeline.
- **Review analysis** -- Collect review ratings and sample reviews across competitors for sentiment analysis.

## Excluding already-scraped places

Use the `excludeCids` parameter to skip places you have already scraped. The CID (Customer ID) is a stable Google Maps identifier that does not change even if the business changes its name or address.

```
{
  "searchStrings": ["cafes in Zurich"],
  "maxResults": 100,
  "excludeCids": ["12345678901234567", "98765432109876543"]
}
```

This is useful for incremental scraping workflows where you want to collect only new results.

## Supported languages

Pass any ISO 639-1 language code: `en`, `de`, `fr`, `ja`, `es`, `pt`, `it`, `ko`, `zh-CN`, `ar`, `nl`, `pl`, `sv`, `da`, `fi`, `no`, `cs`, `hu`, `ro`, `el`, `tr`, `th`, `vi`, `id`, and more.

## Tips for better results

- **Include the location in your search** -- "plumber Berlin" works better than just "plumber"
- **Use the local language** for better results in non-English countries (e.g., "Zahnarzt Zurich" instead of "dentist Zurich")
- **Set language to match your target market** -- `de` for German results, `fr` for French
- **Use Exclude CIDs** to avoid re-scraping places you already have from previous runs

## Pricing

**$1.00 per 1,000 places** scraped. All 30+ fields are included per place. No extra charges for reviews, photos, opening hours, parsed addresses, or any other field.

Example costs:

- 100 places = $0.10
- 1,000 places = $1.00
- 10,000 places = $10.00

| Add-on | Pricing |
| --- | --- |
| Contact extraction | Billed separately by the [Website Contact Extractor](https://apify.com/santamaria-automations/website-contact-extractor) |
| Job listing extraction | Billed separately by the [Website Job Extractor](https://apify.com/santamaria-automations/website-job-extractor) |

## Limitations

- **~120 results per query** -- Google Maps returns a maximum of approximately 120 places per search query. For broader coverage, split your search into multiple queries by neighborhood or sub-region.
- **No individual place detail pages** -- Data comes from search results, not from visiting each place page individually. Most fields are populated, but some niche fields (full review text, all photos) may be limited to what Google includes in search results.
- **Search relevance** -- Results depend on Google's ranking algorithm. The same query may return slightly different results over time.
- **Rate limiting** -- Very high concurrency or very low request delays may trigger temporary blocks from Google. The defaults (10 concurrency, 300ms delay) are tuned for reliability.

## Related Actors

**Find businesses to enrich**

- [Kleinanzeigen.de Scraper — Germany](https://apify.com/santamaria-automations/kleinanzeigen-de-scraper)
- [Willhaben.at Scraper — Austria](https://apify.com/santamaria-automations/willhaben-at-scraper)
- [Tutti.ch Scraper — Switzerland](https://apify.com/santamaria-automations/tutti-ch-scraper)
- [Subito.it Scraper — Italy](https://apify.com/santamaria-automations/subito-it-scraper)
- [Marktplaats.nl Scraper — Netherlands](https://apify.com/santamaria-automations/marktplaats-nl-scraper)

**Real Estate**

- [Homegate.ch Scraper — Swiss real estate](https://apify.com/santamaria-automations/homegate-scraper)
- [Immowelt.de Scraper — German real estate](https://apify.com/santamaria-automations/immowelt-de-scraper)
- [Oikotie.fi Scraper — Finnish real estate](https://apify.com/santamaria-automations/oikotie-fi-scraper)

**E-Commerce**

- [AutoScout24 Scraper — European car listings](https://apify.com/santamaria-automations/autoscout24-scraper)
- [Booking.com Scraper — Hotel listings](https://apify.com/santamaria-automations/booking-com-scraper)

**Enrichment**

- [Website Email & Phone Scraper](https://apify.com/santamaria-automations/website-email-scraper)
- [Website Contact Extractor](https://apify.com/santamaria-automations/website-contact-extractor)
- [Website Job Extractor](https://apify.com/santamaria-automations/website-job-extractor)
- [LinkedIn Scraper](https://apify.com/santamaria-automations/linkedin-scraper)

## Support

Found a bug or have a feature request? [Open an issue](https://console.apify.com/actors/S3TUPOWUK8RoocPjh/issues).