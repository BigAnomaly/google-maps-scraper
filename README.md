[Google Maps Scraper](https://apify.com/web.harvester/google-maps-scraper?fpr=data)

# Google Maps Scraper

> Extract **45+ data fields** from every Google Maps business listing — phones, emails, reviews, social media, website tech stack, lead scores, and GPS coordinates. All from a single search query.

[![Apify Actor](https://img.shields.io/badge/Apify-Actor-blue)](https://apify.com/web.harvester/google-maps-scraper) [![TypeScript](https://img.shields.io/badge/built%20with-TypeScript-blue)](https://www.typescriptlang.org) [![Crawlee](https://img.shields.io/badge/powered%20by-Crawlee-orange)](https://crawlee.dev)

---

## What it does

Google Maps Scraper extracts detailed business information from [Google Maps](https://www.google.com/maps) search results. Provide search queries like `"restaurants in New York"` or `"dentists near me in London"` and the scraper returns every matching business with its full data profile.

Unlike the [Google Maps API](https://developers.google.com/maps), which caps results at 60 per query and charges per request, this scraper returns **hundreds of results per query** with richer data fields — including reviews, emails, social media, lead scoring, and technology detection.

---

## Features

| Category | What you get |
| --- | --- |
| **Core data** | Name, address, phone, website, rating, review count, hours, GPS, images, price range, status |
| **Reviews** | Up to ~300 reviews per business — text, rating, author, date, owner responses. Sortable by newest / highest / lowest / most relevant |
| **Emails & social** | Emails, Instagram, Facebook, Twitter/X, LinkedIn, YouTube, TikTok — crawled from the business website |
| **Tech detection** | CMS, ecommerce, booking, analytics, and payment platforms detected on the business website |
| **Smart Data** | Lead score (0–100), review keywords, owner response stats, digital presence audit, recently opened detection |
| **Monitoring** | Incremental scraping — only outputs new or changed places, perfect for scheduled runs |
| **Grid Search** | Automatically covers large areas with overlapping search points |
| **Interactive map** | HTML map with color-coded markers by rating, saved to Key-Value Store |
| **Run Metrics** | Detailed stage-level execution metrics (discovery, extraction, enrichment) and block tracking |
| **Scraping modes** | Browser (Full), Hybrid (Discovery API + Browser), or Fast Mode (API only) |
| **Three input modes** | Search queries, direct Google Maps URLs, or both |
| **Filtering** | By minimum rating, minimum reviews, operational status, and category |
| **Reliability** | Residential proxy rotation, resume on interruption, multi-language support |

---

## Quick start

1. Open the [Google Maps Scraper](https://apify.com/web.harvester/google-maps-scraper) on Apify
2. Click **Try for free** or **Start**
3. Enter your search queries — one per line
4. Optionally enable **Extract Reviews** and/or **Extract Emails**
5. Click **Start** and wait for the run to finish
6. Download results as **JSON, CSV, Excel, or XML** from the Dataset tab

---

## Input examples

### Minimal — just a query

```
{
  "queries": ["restaurants in New York"]
}
```

### Full extraction — reviews, emails, geo-targeting

```
{
  "queries": [
    "restaurants in New York",
    "coffee shops in Brooklyn",
    "dentists in Manhattan"
  ],
  "maxResultsPerQuery": 200,
  "enableReviews": true,
  "enableEmails": true,
  "maxReviewsPerPlace": 50,
  "reviewSort": "newest",
  "geo": "40.7128,-74.0060",
  "zoom": 14,
  "maxConcurrency": 6
}
```

### Hybrid Mode — discovery API with deep extraction

```
{
  "queries": ["restaurants in Paris"],
  "hybridMode": true,
  "maxResultsPerQuery": 300,
  "enableReviews": true
}
```

### Fast Mode — quick, high-volume extraction

```
{
  "queries": ["coffee shops"],
  "fastMode": true,
  "geo": "40.7128,-74.0060",
  "zoom": 15,
  "radius": 5000
}
```

### Direct URLs — enrich specific places

```
{
  "directUrls": [
    "https://www.google.com/maps/place/Joe's+Pizza/@40.7303,-74.0023,17z/...",
    "https://www.google.com/maps/place/Lombardi's+Pizza/@40.7216,-73.9956,17z/..."
  ],
  "enableReviews": true,
  "enableEmails": true
}
```

### Filtering — quality-only results

```
{
  "queries": ["marketing agencies in San Francisco"],
  "minRating": 4.0,
  "minReviews": 10,
  "excludeCategories": ["ATM", "Gas station"],
  "statusFilter": "operational",
  "enableEmails": true
}
```

### Grid Search — systematic area coverage

```
{
  "queries": ["restaurants"],
  "gridSearch": true,
  "geo": "48.8566,2.3522",
  "radius": 15000,
  "zoom": 14
}
```

### Monitoring — daily change tracking

```
{
  "queries": ["competitors near me"],
  "geo": "40.7128,-74.0060",
  "monitoringMode": true,
  "monitoringRatingThreshold": 0.2,
  "monitoringReviewThreshold": 10
}
```

---

## Input parameters

| Parameter | Type | Default | Description |
| --- | --- | --- | --- |
| `queries` | string[] | *required* | Search queries to run on Google Maps. Supports custom IDs via `query#!#customId`. |
| `directUrls` | string[] | — | Google Maps place URLs to scrape directly (skips search). Normal mode only. |
| `fastMode` | boolean | `false` | Use HTTP API instead of browser. Much faster but fewer fields. Requires `geo`. |
| `hybridMode` | boolean | `false` | 🚀 API-based discovery + browser-based extraction of 45+ fields. Recommended for >100 results. |
| `maxResultsPerQuery` | integer | `100` | Maximum places per query. `0` = unlimited. Max 1000. |
| `language` | string | `en` | IETF language code (e.g., `en`, `de`, `fr`, `ja`, `ar`). |
| `enableReviews` | boolean | `false` | Extract up to ~300 reviews per place. Not available in Fast Mode. |
| `enableEmails` | boolean | `false` | Crawl business websites for emails, social media, tech stack, and digital presence. |
| `maxReviewsPerPlace` | integer | `0` | Cap reviews per place. `0` = unlimited (~300). Requires `enableReviews`. |
| `reviewSort` | string | `newest` | Review sort order: `newest`, `most_relevant`, `highest`, `lowest`. |
| `geo` | string | — | Center point as `lat,lng`. Required for Fast Mode and Grid Search. |
| `gridSearch` | boolean | `false` | Generate overlapping search grid. Requires `geo` and `radius`. |
| `radius` | number | `10000` | Radius in meters from the geographic center. |
| `zoom` | integer | `15` | Map zoom level 0–21. Lower = wider area, higher = more focused. |
| `maxConcurrency` | integer | `6` | Parallel browser tabs (Normal Mode only). Max 20. |
| `minRating` | number | `0` | Skip businesses below this star rating. |
| `minReviews` | integer | `0` | Skip businesses with fewer reviews than this. |
| `excludeCategories` | string[] | — | Skip businesses matching these categories (case-insensitive partial match). |
| `statusFilter` | string | `any` | `any` or `operational` (excludes closed/temporarily closed). |
| `monitoringMode` | boolean | `false` | Only output new or changed places. State persists between runs on the same task. |
| `monitoringRatingThreshold` | number | `0.2` | Minimum rating change to flag as "changed". |
| `monitoringReviewThreshold` | integer | `10` | Minimum review count change to flag as "changed". |
| `enableMapOutput` | boolean | `true` | Generate an interactive HTML map with color-coded markers by rating. |
| `proxyConfig` | object | Residential | Apify Proxy settings. Residential proxies recommended. |

### Custom input IDs

By default, each result's `input_id` is set to the search query. To use your own identifier, append `#!#` (hash-bang-hash) followed by your ID:

```
{
  "queries": [
    "restaurants in New York#!#nyc-restaurants",
    "coffee shops in Brooklyn#!#bk-coffee"
  ]
}
```

Results will have `"input_id": "nyc-restaurants"` and `"input_id": "bk-coffee"`.

### Zoom level reference

| Zoom | Area | Best for |
| --- | --- | --- |
| 10 | ~50 km | Entire metro area or region |
| 12 | ~15 km | City-wide search |
| 14 | ~3 km | District or neighborhood |
| **15** (default) | ~1.5 km | Focused neighborhood |
| 17 | ~300 m | Single street or block |
| 19 | ~50 m | Individual building |

---

## Output

Each result contains **45+ structured fields**. Results are downloadable as JSON, CSV, Excel, or XML.

### Output example

```
{
  "input_id": "restaurants in New York",
  "title": "Joe's Pizza",
  "category": "Pizza restaurant",
  "categories": ["Pizza restaurant", "Italian restaurant", "Restaurant"],
  "address": "7 Carmine St, New York, NY 10014",
  "complete_address": {
    "borough": "Greenwich Village",
    "street": "7 Carmine St",
    "city": "New York",
    "state": "NY",
    "postal_code": "10014",
    "country": "US"
  },
  "phone": "+1 212-366-1182",
  "web_site": "http://www.joespizzanyc.com",
  "link": "https://www.google.com/maps/place/Joe's+Pizza/@40.7303,-74.0023,17z/...",
  "place_id": "ChIJLwjSR7VZwokRxlbSPGZPAhc",
  "cid": "1659568553828468934",
  "latitude": 40.7303,
  "longitude": -74.0023,
  "review_count": 12847,
  "review_rating": 4.4,
  "reviews_per_rating": { "1": 512, "2": 384, "3": 897, "4": 2689, "5": 8365 },
  "status": "OPERATIONAL",
  "description": "No-frills, old-school pizzeria serving classic NY-style slices since 1975.",
  "price_range": "$",
  "timezone": "America/New_York",
  "open_hours": { "Monday": ["10:00 AM - 2:00 AM"] },
  "popular_times": { "Monday": { "12": 55, "18": 85, "20": 60 } },
  "thumbnail": "https://lh5.googleusercontent.com/p/...",
  "images": [
    { "title": "All", "image": "https://lh5.googleusercontent.com/p/..." }
  ],
  "owner": { "id": "103194...", "name": "Joe's Pizza", "link": "https://..." },
  "is_claimed": true,
  "is_recently_opened": false,
  "emails": ["info@joespizzanyc.com"],
  "social_media": {
    "instagram": ["https://instagram.com/joespizzanyc"],
    "facebook": ["https://facebook.com/joespizzanyc"],
    "twitter": [],
    "linkedin": [],
    "youtube": [],
    "tiktok": ["https://tiktok.com/@joespizzanyc"]
  },
  "website_tech": {
    "cms": ["WordPress"],
    "ecommerce": [],
    "booking": [],
    "analytics": ["Google Analytics", "Google Tag Manager"],
    "payment": ["Square"]
  },
  "digital_presence": {
    "score": 72,
    "has_ssl": true,
    "has_mobile_viewport": true,
    "has_analytics": true,
    "has_structured_data": true,
    "cms_detected": true,
    "social_platforms_count": 2
  },
  "owner_response_stats": {
    "response_rate": 0.34,
    "total_responses": 17,
    "total_reviews_analyzed": 50
  },
  "review_keywords": [
    { "keyword": "slice", "count": 89 },
    { "keyword": "best pizza", "count": 67 },
    { "keyword": "long wait", "count": 23 }
  ],
  "lead_score": 78,
  "user_reviews": [
    {
      "Name": "Sarah M.",
      "Rating": 5,
      "Description": "Best pizza in NYC, hands down.",
      "When": "3 months ago"
    }
  ],
  "user_reviews_extended": []
}
```

### Complete field reference

| Field | Type | Description |
| --- | --- | --- |
| `input_id` | string | Search query or custom ID that produced this result |
| `title` | string | Business name |
| `category` | string | Primary category |
| `categories` | string[] | All categories |
| `address` | string | Full formatted address |
| `complete_address` | object | Structured address: street, city, state, postal_code, country, borough |
| `phone` | string | Phone number |
| `web_site` | string | Business website URL |
| `link` | string | Google Maps URL for this place |
| `place_id` | string | Google Place ID |
| `cid` | string | Google CID |
| `data_id` | string | Google internal data ID |
| `latitude` | number | GPS latitude |
| `longitude` | number | GPS longitude |
| `review_count` | number | Total number of reviews |
| `review_rating` | number | Average star rating (1.0–5.0) |
| `reviews_per_rating` | object | Review count by star rating (1–5) |
| `reviews_link` | string | Direct link to reviews page |
| `status` | string | Operating status: `OPERATIONAL`, `CLOSED`, etc. |
| `description` | string | Business description from Google |
| `price_range` | string | Price level: `$`, `$$`, `$$$`, `$$$$` |
| `timezone` | string | IANA timezone (e.g., `America/New_York`) |
| `plus_code` | string | Google Plus Code |
| `open_hours` | object | Opening hours by day of week |
| `popular_times` | object | Foot traffic by day and hour (0–100 scale) |
| `thumbnail` | string | Main thumbnail image URL |
| `images` | array | Gallery images with titles |
| `owner` | object | Business owner info: id, name, link |
| `is_claimed` | boolean | Whether the listing has been claimed by the owner |
| `is_recently_opened` | boolean | Heuristic: likely a recently opened business |
| `reservations` | array | Reservation links (e.g., OpenTable, Resy) |
| `order_online` | array | Online ordering links (e.g., DoorDash, Uber Eats) |
| `menu` | object | Menu link and source |
| `about` | array | Business attributes: service options, accessibility, payments, etc. |
| `user_reviews` | array | Inline reviews from the listing page (up to ~8) |
| `user_reviews_extended` | array | Full reviews when `enableReviews` is on (up to ~300) |
| `emails` | array | Email addresses found on the business website |
| `social_media` | object | Social profiles: Instagram, Facebook, Twitter/X, LinkedIn, YouTube, TikTok |
| `website_tech` | object | Detected technologies: CMS, ecommerce, booking, analytics, payment |
| `digital_presence` | object | Website audit: SSL, mobile viewport, analytics, structured data, CMS, score |
| `owner_response_stats` | object | Owner reply metrics: response_rate, total_responses, total_reviews_analyzed |
| `review_keywords` | array | Top keywords from reviews with frequency counts |
| `lead_score` | number | Lead quality score (0–100) based on multiple business signals |

### Fast Mode field availability

Fast Mode uses Google's internal HTTP API, which returns a reduced field set.

**Available:** `input_id`, `title`, `category`, `categories`, `address`, `phone`, `web_site`, `latitude`, `longitude`, `review_count`, `review_rating`, `status`, `timezone`, `plus_code`, `open_hours`, `data_id`, `lead_score`

**Not available:** `description`, `popular_times`, `thumbnail`, `images`, `owner`, `reservations`, `order_online`, `menu`, `about`, `user_reviews`, `user_reviews_extended`, `emails`, `social_media`, `website_tech`, `digital_presence`, `owner_response_stats`, `review_keywords`, `is_claimed`, `is_recently_opened`

---

## Smart Data

Every place extraction automatically computes these intelligence fields — no extra configuration needed.

> **Note:** `social_media`, `website_tech`, and `digital_presence` require `enableEmails: true` since they are derived from crawling the business website.

### Lead score (0–100)

A composite score that ranks businesses by outreach potential:

| Signal | Weight | What it measures |
| --- | --- | --- |
| Website presence | +15 pts | Whether the business has a website |
| Email availability | +20 pts | Contact accessibility |
| Social media | +2 pts | Per platform (max 10 pts) |
| Review volume | +10 pts | 50+ reviews |
| Review rating | +10 pts | 4.0+ average rating |
| Is claimed | +10 pts | Verified owner listing |
| Photos | +10 pts | 5+ listing images |
| Owner response | +15 pts | Scaled by % reply rate |

### Review keywords

Top keywords and two-word phrases (bigrams) extracted from reviews using NLP. The engine tokenizes text, filters out 190+ stopwords, and ranks phrases by frequency. Requires a minimum appearance of 2 reviews.

### Owner response stats

- **Response rate** — % of reviews with an owner reply
- **Total responses** — count of owner replies
- **Total reviews analyzed** — sample size examined

### Digital presence score (0–100)

| Check | Points | What it detects |
| --- | --- | --- |
| SSL (HTTPS) | 20 | Secure connection |
| Mobile viewport | 20 | `width=device-width` tag |
| CMS detected | 10 | Professional platform |
| Analytics | 15 | Traffic tracking tools |
| Social platforms | 15 | 5 pts per platform (max 15) |
| Structured data | 20 | Schema.org / JSON-LD |

### Website technology detection

| Category | Examples |
| --- | --- |
| **CMS** | WordPress, Wix, Squarespace, Webflow, GoDaddy, Weebly, Joomla, Drupal |
| **Ecommerce** | Shopify, WooCommerce, BigCommerce, Magento, PrestaShop |
| **Booking** | Calendly, Acuity, OpenTable, Booking.com, Yelp Reservations, Mindbody |
| **Analytics** | Google Analytics, Google Tag Manager, Facebook Pixel, Hotjar, Microsoft Clarity |
| **Payment** | Stripe, Square, PayPal, Braintree |

### Recently opened detection

Multi-factor heuristic based on low review counts relative to rating, recency of reviews, and business metadata signals.

---

## Monitoring mode

Track businesses over time with incremental scraping. On each run, only **new** or **changed** places are output — everything else is silently skipped.

### How it works

1. **First run** — all places are output and their state (rating, review count, status) is saved
2. **Subsequent runs** — each place is compared against saved state
3. **New places** — output with `_monitoring.is_new: true`
4. **Changed places** — output with `_monitoring.change_reasons` listing what changed (rating, review count, or status). Includes `previous_rating`, `previous_review_count`, and `previous_status` fields.
5. **Unchanged places** — silently skipped (state is still updated)

### Setup

```
{
  "queries": ["restaurants near me"],
  "geo": "40.7128,-74.0060",
  "monitoringMode": true,
  "monitoringRatingThreshold": 0.2,
  "monitoringReviewThreshold": 10
}
```

- `monitoringRatingThreshold: 0.2` — a rating shift from 4.5 → 4.3 triggers output; 4.5 → 4.4 does not
- `monitoringReviewThreshold: 10` — gaining 10+ new reviews since the last run triggers output

Schedule on an Apify Task to run daily or weekly. State is tied to the task — separate tasks maintain separate state stores.

> **Note:** Monitoring mode is not supported in Fast Mode.

---

## Use cases

### Lead generation

Build targeted prospect lists with verified contact information. Get phone numbers, websites, emails, social media profiles, and lead scores — ready for outreach or CRM import.

**Example:** `"marketing agencies in San Francisco"` with `enableEmails: true` → 200+ agencies with phone, email, social media, tech stack, and a lead score ranking each by outreach potential.

### Market research and competitive analysis

Compare ratings, review counts, price ranges, service options, and digital presence scores across hundreds of businesses instantly.

**Example:** `"fitness gyms in Austin TX"` → Compare 150+ gyms by rating, review volume, price range, website tech, and lead score.

### Local SEO monitoring

Track your business and competitors over time with Monitoring Mode. Get alerted when ratings drop, review counts spike, or new competitors appear.

### Review analysis

Extract thousands of reviews for sentiment analysis, trend detection, and customer feedback research. Use review keywords to identify recurring themes and owner response stats to benchmark engagement.

### Data enrichment

Augment existing business databases with fresh Google Maps data. Pass a list of specific Google Maps URLs via `directUrls` to enrich them with the full 45+ field extraction.

### Location intelligence

Use Grid Search to map every business of a given type within a radius. Download the interactive HTML map from Key-Value Store for visual analysis.

**Example:** Grid search for `"restaurants"` with `geo: "40.7484,-73.9857"` and `radius: 2000` → maps every restaurant within 2 km of the Empire State Building.

---

## Advanced configuration

### Fast Mode

Fast Mode uses Google Maps' internal HTTP API instead of browser rendering. Significantly faster and less memory-intensive, but returns fewer fields.

**Use when you need:**

- Basic business info only (name, address, phone, website, ratings, hours)
- High-volume, speed-optimised extraction
- No reviews or email enrichment

**Requirements:** `geo` is mandatory. `radius` controls the search area (default 10 km). No proxy support.

### Grid Search

Divides a circular area into a grid of overlapping search points. Each query runs at every grid point. Results are automatically deduplicated in Fast Mode by `data_id`.

**Requirements:** `geo` and `radius` are mandatory. Works in both Normal Mode and Fast Mode.

### Direct URLs

Skip search entirely by providing specific Google Maps place URLs. Ideal for enriching an existing list of businesses, re-scraping specific places, or processing a curated competitor set.

### Result filtering

Apply filters to skip unwanted businesses before they reach the dataset:

```
{
  "queries": ["restaurants in New York"],
  "minRating": 4.0,
  "minReviews": 10,
  "excludeCategories": ["Gas station", "ATM", "Parking lot"],
  "statusFilter": "operational"
}
```

### Scraping large datasets (10,000+ places)

- **Memory** — Allocate 4–8 GB
- **maxConcurrency** — 4–8 browser tabs for 4 GB RAM; 2–4 for 2 GB
- **Resume** — Crawlee's request queue persists progress automatically. If a run stops, restart with the same input to continue from where it left off.

---

## Integrations

Connect Google Maps Scraper data to your existing tools:

| Integration | How |
| --- | --- |
| **REST API** | [Apify API v2](https://docs.apify.com/api/v2) — fetch datasets, trigger runs, get webhooks |
| **Python** | `apify-client` PyPI package |
| **JavaScript / Node.js** | `apify-client` npm package |
| **Google Sheets** | Auto-export results to a spreadsheet |
| **Zapier / Make** | Connect to 5,000+ apps |
| **Slack** | Run completion notifications |
| **Webhooks** | Trigger on run start, success, or failure |

---

## Is it legal to scrape Google Maps?

Scraping publicly available data from Google Maps is generally considered legal. The landmark [hiQ Labs v. LinkedIn](https://en.wikipedia.org/wiki/HiQ_Labs_v._LinkedIn) ruling confirmed that accessing publicly accessible data does not violate the Computer Fraud and Abuse Act.

You should however:

- **Respect Google's Terms of Service** and use the data responsibly
- **Comply with local data privacy laws** (GDPR, CCPA, etc.) when handling personal data such as reviewer names
- **Avoid aggressive scraping** that could disrupt the service
- **Use data ethically** — do not use scraped contact information for spam or harassment

This Actor does not bypass authentication or access controls. It only extracts data that is publicly visible to any Google Maps user.

---

## Limitations

| Limitation | Detail |
| --- | --- |
| Review limit | Google shows a maximum of ~300 reviews per business |
| Email scope | Only the business website's landing page is checked |
| Social media scope | Only links visible on the landing page are extracted |
| Fast Mode | Reduced fields, no proxy support, no reviews or emails |
| Monitoring Mode | Not supported in Fast Mode |
| Memory | Large runs (10K+ places) need 4–8 GB |
| Result count | Depends on what Google Maps returns for the query |
| `longitude` field | GPS longitude coordinate |

---

## FAQ

**How many results can I get per query?**
Dense urban areas with broad queries (e.g., `"restaurants in New York"`) can return 500+ results. Niche queries in small towns may return fewer than 20. Set `maxResultsPerQuery: 0` for unlimited. Use Grid Search to cover larger areas.

**How long does a run take?**
~2–5 minutes for 100 places without reviews. Enabling reviews adds a few seconds per place. Email extraction adds a few more. Fast Mode is significantly quicker for basic data.

**What happens if a run is interrupted?**
Crawlee's request queue persists progress automatically. Restart with the same input and it picks up where it left off — no duplicates, no lost data.

**Can I target a specific location by coordinates?**
Yes — use the `geo` parameter with `lat,lng` format and adjust `zoom`. See Advanced configuration.

**Why are some fields empty?**
Not all businesses have every field on Google Maps. `price_range`, `description`, `popular_times`, and `menu` depend on the business. In Fast Mode, many fields are always empty by design. `social_media`, `website_tech`, and `digital_presence` require `enableEmails: true`.

**What are Smart Data features?**
Automatically computed intelligence fields: **lead scoring** (0–100), **review keyword analysis**, **owner response tracking**, and **recently opened detection**. Social media, tech detection, and digital presence require `enableEmails: true`.

**How does lead scoring work?**
The score (0–100) combines review rating, review volume, website presence, email availability, social media activity, and digital presence quality. Computed for every place — including Fast Mode (with partial data).

**What is Monitoring Mode?**
Incremental scraping: the first run saves all place states. Subsequent runs only output places that are new or have changed beyond the configured thresholds. Unchanged places are silently skipped.

**What's the difference between Normal, Hybrid, and Fast Mode?**
Normal Mode uses a real Playwright browser for the entire process. Hybrid Mode uses Google's internal API to find results (discovery) and browsers only for extraction, which is faster and more reliable for large queries. Fast Mode uses the API for both discovery and extraction — 10x faster but returns fewer fields.

**What proxy should I use?**
Residential proxies (the default) give the best results and lowest block rate in Normal Mode. Datacenter proxies may work for small runs. Fast Mode does not use proxies.

**How does Grid Search work?**
Grid Search divides a circle (defined by `geo` + `radius`) into overlapping search points. Each query runs at every point, ensuring complete area coverage. Fast Mode results are deduplicated by `data_id`.