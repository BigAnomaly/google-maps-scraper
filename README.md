[Google Maps Scraper](https://apify.com/rp_openpro.ai/google-maps-scraper?fpr=data)

# Google Maps Scraper with Email & Social Media Extractor (Apify)

**Turn Google Maps searches into outreach-ready local business leads** — **company names, phone numbers, full addresses, star ratings, websites, GPS coordinates, Place ID and CID**, plus optional **business emails, six social profiles, and marketing tags** (Google Analytics, Google Tag Manager, Facebook Pixel) pulled from each company website. One Actor for **cold email lists, agency prospecting, local SEO research, CRM enrichment, and Apify automations** — export **JSON, CSV, or Excel** with no extra tools.

**From $1.15 / 1,000 results** — one of the most complete **Google Maps email extractors** and **local lead generators** on Apify: emails, socials, and pixels **included**, not paid add-ons.

> **Other Google Maps scrapers give you names and phones. Then charge extra for emails. Then extra for socials. Then you realize you've paid $5+ for what we include at $1.15–$1.50.**

---

## Fast runs, fair usage on Apify

You care about **results per minute** and **cost per lead** — not how the Actor is wired internally. Here is what matters on the Apify platform:

- **You control how many businesses** you collect per search, so you only run as long as your use case needs — from quick tests to large regional exports.
- **Optional website enrichment stays practical at scale** — when contact scraping is on, business sites are processed **in parallel**, so bigger lists finish in reasonable time instead of crawling sites strictly one after another.
- **One Actor, one dataset** — Maps listings plus emails and socials land in the **same run and the same download**, so you are not paying for separate scrapers or stitching spreadsheets by hand.

---

## Why This Google Maps Scraper?

Most scrapers give you names and phone numbers. **We give you outreach-ready leads.**

Every result automatically includes emails and social profiles pulled directly from each business website — at no extra cost. Stop paying for a separate email finder. Stop manually looking up LinkedIn and Instagram profiles. Get everything in one run.

---

## How It Compares

| Feature | **Leadsit.eu (This Actor)** | compass (270K users) | Google Map Scrapper Neo | lukaskrivka (48K users) |
| --- | --- | --- | --- | --- |
| Business data | ✅ Free | ✅ Free | ✅ Free | ✅ Free |
| **Email extraction** | ✅ **Included free** | 💰 Paid add-on | ✅ Included | ✅ Included |
| **Social media (6 platforms)** | ✅ **All 6 included** | 💰 Paid add-on | ✅ Basic | ✅ Basic |
| **Marketing tags (GA, GTM, FB Pixel)** | ✅ **Unique feature** | ❌ No | ❌ No | ❌ No |
| GPS coordinates | ✅ Included | ✅ Included | ✅ Included | ✅ Included |
| Photos | ✅ Included | 💰 Paid add-on | ✅ Included | ❌ No |
| Place ID + CID | ✅ Both | ✅ Place ID only | ✅ Place ID only | ✅ Place ID only |
| Structured address fields | ✅ Street, City, Postal | ❌ Full string only | ❌ Full string only | ❌ Full string only |
| Opening hours | ✅ Included | ✅ Included | ✅ Included | ❌ No |
| Closed status detection | ✅ Included | ✅ Included | ✅ Included | ✅ Included |
| Languages | ✅ **34 languages** | ✅ 25+ | ❌ Unknown | ✅ 20+ |
| Dataset views | ✅ **4 custom views** | ✅ Views | ❌ Flat only | ❌ Flat only |
| **Price per 1,000 results** | **$1.50** | $2.10 + add-ons | $10.00 | $3.00 |

**Bottom line:** 30–85% cheaper than every competitor, with more features included. Other scrapers look cheap until you add emails, social media, and photos as paid extras. We bundle everything.

---

## What Data Do You Get Per Business?

Every result includes **24+ fields** — all flat, no nested objects, export directly to CSV, Excel, or Google Sheets:

### Core Google Maps Data

- 🏢 **Business name** & categories
- ⭐ **Rating** (average star score)
- 💬 **Total reviews** (number of customer reviews)
- 🔗 **Reviews URL** — direct link to the place's full Google Reviews page
- 📍 **Full address** + structured fields (street, city, postal code)
- 📍 **GPS coordinates** (latitude / longitude) for mapping
- 📞 **Phone number**
- 🌐 **Website URL** + clean domain
- 🕐 **Opening hours** (full weekly schedule)
- 📸 **Photo URLs** from Google Maps
- 🆔 **Place ID** + **CID** (Google's unique identifiers)
- 🚫 **Closed status** (temporarily or permanently closed)
- 🔗 **Google Maps URL** (direct link to listing)

### Email Extraction (included free)

- 📧 **Business email** — scraped directly from their website
- Smart filtering: real contact emails only — ignores unsubscribe links and system addresses
- Typical extraction rate: **40–60%** of businesses have a public contact email

### Social Media Profiles — 6 Platforms (included free)

- 📘 **Facebook** page URL
- 📷 **Instagram** profile URL
- 💼 **LinkedIn** company page URL
- 🐦 **Twitter/X** profile URL
- 🎥 **YouTube** channel URL
- 📌 **Pinterest** profile URL

### Marketing & Advertising Tags (unique to this Actor)

- 📊 **Google Analytics ID** (GA4 or Universal Analytics)
- 🏷️ **Google Tag Manager ID**
- 📱 **Facebook Pixel ID** (Meta advertising pixel)

> **Why marketing tags?** Businesses *without* GA/GTM/FB Pixel are warm leads for digital agencies. Businesses *with* them are ideal SaaS prospects already investing in digital marketing. No other Google Maps scraper on Apify offers this.

---

## Output Example

```
{
    "name": "Joe's Pizza",
    "fulladdress": "Joe's Pizza, 123 Broadway, New York, NY 10001, USA",
    "street": "123 Broadway",
    "municipality": "New York",
    "postalCode": "10001",
    "phone": "+1 212-555-0147",
    "website": "https://joespizzanyc.com",
    "domain": "joespizzanyc.com",
    "email": "info@joespizzanyc.com",
    "businessCategories": "Pizza restaurant, Italian restaurant",
    "averageRating": "4.7",
    "totalReviews": "1248",
    "reviewsUrl": "https://search.google.com/local/reviews?placeid=ChIJd8BlQ2BZwokRAFUEcm_qrcA",
    "latitude": "40.7484405",
    "longitude": "-73.9966986",
    "placeId": "ChIJd8BlQ2BZwokRAFUEcm_qrcA",
    "cid": "12795282804288502000",
    "openingHours": "Monday: 10 AM–11 PM | Tuesday: 10 AM–11 PM | ...",
    "businessStatus": null,
    "googleMapsUrl": "https://www.google.com/maps/place/?q=place_id:ChIJd8BlQ2BZwokRAFUEcm_qrcA",
    "photos": "https://lh5.googleusercontent.com/p/AF1QipN...",
    "facebookUrl": "https://www.facebook.com/joespizzanyc",
    "instagramUrl": "https://www.instagram.com/joespizzanyc",
    "linkedinUrl": null,
    "twitterUrl": "https://twitter.com/joespizzanyc",
    "youtubeUrl": null,
    "pinterestUrl": null,
    "googleAnalytics": "G-XYZ789ABC",
    "googleTagManager": "GTM-ABC123",
    "facebookPixel": "123456789012345",
    "searchTerm": "pizza restaurant",
    "scrapedAt": "2026-03-17T14:27:43.927Z"
}
```

All fields are flat — export directly to CSV, Excel, or Google Sheets without any transformation.

---

## How to Use

### Step 1: Configure Your Search

```
{
    "searchStringsArray": ["restaurant", "bar", "cafe"],
    "locationQuery": "Paris, France",
    "maxCrawledPlacesPerSearch": 200,
    "language": "fr",
    "scrapeContacts": true
}
```

### Step 2: Run

Click **Start**. The scraper searches Google Maps for each term in parallel, scrolls through all results, visits each business website for email and social extraction, and deduplicates results automatically.

### Step 3: Export

Download results in **JSON, CSV, Excel, XML, HTML, or RSS** — or connect via the Apify API.

**4 pre-built dataset views:**

- **Overview** — name, address, phone, website, email, categories, rating, total reviews, review link
- **Contact Info** — name, phone, email, website + all 6 social media URLs
- **Location** — address, street, city, postal code, coordinates, Maps URL
- **Marketing & Tracking** — website, domain, GA ID, GTM ID, FB Pixel ID, social URLs

---

## API Integration

### Node.js

```
const { ApifyClient } = require('apify-client');

const client = new ApifyClient({ token: 'YOUR_API_TOKEN' });

const run = await client.actor('rp_openpro.ai/google-maps-scraper').call({
    searchStringsArray: ['restaurant', 'bar', 'cafe'],
    locationQuery: 'Paris, France',
    maxCrawledPlacesPerSearch: 100,
    language: 'fr',
    scrapeContacts: true,
});

const { items } = await client.dataset(run.defaultDatasetId).listItems();

items.forEach(item => {
    console.log(`${item.name} | ${item.email || 'no email'} | ${item.phone}`);
    if (item.facebookUrl) console.log(`  Facebook: ${item.facebookUrl}`);
    if (item.instagramUrl) console.log(`  Instagram: ${item.instagramUrl}`);
    if (item.linkedinUrl) console.log(`  LinkedIn: ${item.linkedinUrl}`);
});
```

### Python

```
from apify_client import ApifyClient

client = ApifyClient("YOUR_API_TOKEN")

run = client.actor("rp_openpro.ai/google-maps-scraper").call(run_input={
    "searchStringsArray": ["restaurant", "bar", "cafe"],
    "locationQuery": "Paris, France",
    "maxCrawledPlacesPerSearch": 100,
    "language": "fr",
    "scrapeContacts": True,
})

for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(f"{item['name']} | {item.get('email', 'N/A')} | {item.get('phone', 'N/A')}")
```

### cURL

```
curl -X POST "https://api.apify.com/v2/acts/rp_openpro.ai~google-maps-scraper/runs?token=YOUR_API_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "searchStringsArray": ["dentist", "doctor"],
    "locationQuery": "London, UK",
    "maxCrawledPlacesPerSearch": 100,
    "scrapeContacts": true
  }'
```

---

## Use Cases

### Lead Generation with Email Outreach

Scrape "contractors in Miami" → 500 businesses with emails and phones → import to your CRM → start outreach. **No separate email finder needed.**

### Marketing Agency Prospecting

Find businesses *without* Google Analytics, Facebook Pixel, or GTM — each is a warm lead with a specific pain point you can solve. Filter using the **Marketing & Tracking** dataset view. This is a feature no other Google Maps scraper on Apify offers.

### Social Media Prospecting

Get Facebook, Instagram, and LinkedIn URLs for hundreds of businesses at once. Filter for those with active social profiles for social media management pitches.

### Competitor Intelligence

Map competitor locations, compare ratings across regions, and identify underserved areas before launching a new location or service.

### Market Research

Analyze business density, category distribution, and average ratings across neighborhoods, cities, or countries.

### SaaS Prospecting by Tech Stack

Filter by `googleTagManager`, `googleAnalytics`, or `facebookPixel` to find businesses already investing in digital tools — the highest-converting SaaS prospects.

### B2B Email Marketing

Build verified business email lists for targeted outreach campaigns. Every email comes directly from the business's own website.

### Data Enrichment

Already have a list of businesses? Run them through to enrich with phone, email, coordinates, social links, and marketing tags.

---

## Input Parameters

| Parameter | Type | Default | Description |
| --- | --- | --- | --- |
| `searchStringsArray` | string[] | required | Search terms (e.g., `"plumbers in London"`). Each runs as a separate parallel search. |
| `locationQuery` | string | `""` | Where to search (e.g., `"Paris, France"`). Use City + Country for best results. |
| `maxCrawledPlacesPerSearch` | number | `100` | Max places per search term. Set `0` for unlimited. Lower = faster + cheaper. |
| `language` | string | `"en"` | Display language. Supports **34 languages**: EN, FR, DE, ES, IT, PT, JA, KO, ZH, AR, and more. |
| `scrapeContacts` | boolean | `true` | Visit business websites to extract emails, 6 social platforms, and marketing tags. Disable for speed if you only need core Google Maps data. |
| `proxyConfiguration` | object | Apify Proxy (datacenter) | Default Apify Proxy is datacenter — cheaper and faster. Add `apifyProxyGroups: ["RESIDENTIAL"]` only if Google blocks you; do not use residential for routine tests. |

### Search Tips

**Good** — distinct, non-overlapping terms:

```
["restaurant", "bar", "pub", "cafe", "ice cream"]
```

**Avoid** — overlapping terms waste time and produce duplicates:

```
["restaurant", "restaurants", "chinese restaurant", "coffee", "coffee shop"]
```

### Location Tips

| Format | Example | Reliability |
| --- | --- | --- |
| City + Country | `"Paris, France"` | Best |
| Neighborhood + City | `"Brooklyn, New York, USA"` | Great |
| City only | `"Berlin"` | Good |
| Postal code | `"90210"` | Fair |

---

## Pricing

| Plan | Per result | Per 1,000 results |
| --- | --- | --- |
| Free (Personal) | $0.0015 | **$1.50** |
| Starter | $0.0014 | **$1.40** |
| Scale | $0.0013 | **$1.30** |
| Business | $0.00115 | **$1.15** |

✅ Every plan includes emails, 6 social media platforms, marketing tags, photos, and coordinates. No hidden fees. No add-ons.

🆓 Free trial: **10 places per run** — enough to verify results before committing.

> **Compare:** compass charges $2.10/1,000 for basic data + extra for emails. We charge $1.50/1,000 with everything included — **30% less for 3× more data.**

---

## Integrations

| Tool | Use case |
| --- | --- |
| **Google Sheets** | Auto-sync results to spreadsheets |
| **HubSpot / Salesforce** | Push leads directly to your CRM |
| **Zapier** | Automate your entire lead pipeline |
| **Make (Integromat)** | Multi-step workflows |
| **Airtable** | Searchable business database |
| **Slack / Email** | Notifications when runs complete |
| **LangChain** | Feed business data to AI agents |
| **Apify MCP** | Connect to AI assistants via Model Context Protocol |
| **Webhooks** | Trigger custom actions on completion |
| **Apify API** | Run from Node.js, Python, or cURL |

---

## FAQ

### How does email extraction work?

The scraper visits each business website listed on Google Maps and extracts real contact email addresses. It applies smart filtering to return only genuine business emails — ignoring automated and system addresses. Typical extraction rate is 40–60% of businesses.

### What social media platforms are supported?

Six platforms: **Facebook, Instagram, LinkedIn, Twitter/X, YouTube, and Pinterest**. Profile links are extracted directly from each business website.

### What are marketing tracking tags and why do they matter?

The scraper detects **Google Analytics**, **Google Tag Manager**, and **Facebook Pixel** on business websites. Businesses without these tags are perfect leads for digital marketing agencies. Businesses with them are already investing in digital tools — ideal SaaS prospects. No other Google Maps scraper on Apify provides this intelligence.

### How many results can I get?

No hard limit — Google Maps typically surfaces 20–120+ results per search depending on how dense the area is. For larger datasets, use multiple search terms or target different neighborhoods.

### Can I export to CSV or Google Sheets?

Yes. All output is flat — no nested objects — so it exports perfectly to CSV, Excel, or Google Sheets without any transformation needed.

### Can I schedule recurring runs?

Yes. Use Apify's built-in scheduler for daily, weekly, or any custom cadence. Keep your lead database fresh automatically.

### What if a business doesn't have a website?

All Google Maps data is still extracted. Contact enrichment fields (email, social URLs, tracking tags) will be `null` for businesses without a website.

### Is it a Google Places API alternative?

Yes. The official Google Places API caps results at 60 per query, charges $0.032 per request, and provides no emails, social profiles, or marketing tags. This Actor has no result caps and includes all those fields at a fraction of the cost.

### How is this different from other Google Maps scrapers on Apify?

Three differences: **(1)** Email and social media extraction is included free — competitors charge extra. **(2)** Marketing tag detection (GA, GTM, FB Pixel) is exclusive to this Actor. **(3)** At $1.50/1,000 with tiered discounts down to $1.15, we're the most cost-effective fully-enriched option on the platform.

---

> **Need B2B web results too, not just Maps?** Try [**Ultimate Leads**](https://console.apify.com/actors/5XYUiihBAg0sn8sBy) — it runs this Maps scraper + B2B URL Finder + deep contact enrichment in **one Actor, one merged dataset**. Companies that appear on Maps AND web search get combined into a single row.

---

*Built by [Leadsit.eu](https://leadsit.eu) — Lead generation tools for modern sales teams.*

*SEO: google maps scraper apify, local business leads from google maps, google maps email extractor, scrape google maps to csv excel, bulk google maps data export, google maps api alternative unlimited results, extract emails from google maps listings, google maps social media finder, b2b local lead generation, apify google maps cheap, google maps place id cid scraper, google maps enrichment tool, agency prospecting google maps, google maps facebook instagram linkedin, google analytics gtm facebook pixel from website*