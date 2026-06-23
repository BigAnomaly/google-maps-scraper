[Google Maps Scraper](https://apify.com/scraperlink/google-maps-scraper?fpr=data)

# Google Maps Scraper

**$0.50 per 1,000 results — all-in. No proxy fees. No compute surprises.**

Pull structured business data from Google Maps at a fraction of what other actors charge. Every run is fast, lightweight, and billed only for results you actually receive — each business lands as its own row in the dataset.

The leading Google Maps actor on Apify charges **$2.10 per 1,000 results**. We charge **$0.50**. That's 4× cheaper, with more data fields, faster runs, and zero hidden costs.

---

## What makes this different

|  | This actor | Top competitor |
| --- | --- | --- |
| Price per 1,000 results | **$0.50** | $2.10+ |
| Proxy & infrastructure costs | **Included** | Billed separately |
| Data fields per result | **40+** | ~20 |
| Output organized into tabs | **6 tabs** | Basic table |
| Browser required | **No** | Yes (Playwright) |
| Bulk queries in one run | **Yes** | Yes |
| Results as individual rows | **Yes** | Sometimes nested |
| Max results per query | **200** | 120–200 |

**No browser means no Playwright, no Chromium, no headless overhead.** Runs complete in seconds, not minutes. You're not paying Apify compute for a browser to sit idle while a page loads.

**Proxy costs are absorbed.** Every request is routed through our infrastructure. You never need to configure Apify proxies or eat proxy credits from your own plan.

---

## Data you get (40+ fields across 6 tabs)

### Overview

Name, rating, review count, price level, category, full address, website, phone, and direct Google Maps URL — everything you need at a glance.

### Contact Info

Full address broken into components (street, number, neighborhood, city, postal code, state, country), domain, all three phone formats (international, formatted, digits-only), coordinates (lat/lng), plus code, and the building or complex the business is located in.

### Hours

Live open/closed status, weekly opening hours, service-specific hours (lunch, dinner, brunch, happy hour, and more), and booking/reservation links.

### Ratings & Reviews

Total score, star rating, rating count, review count, full review distribution (1–5 stars breakdown), and price tier.

### Media & Identity

Place ID, Data ID, CID, FID, Google Maps URL, search result URL, business image, thumbnail, logo, and owner information.

### Metadata

Original search query, rank and position in results, timezone, temporarily/permanently closed flags, about text, and popular times histogram data.

---

## Input

| Field | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| `query` | string list | ✅ | — | One or more Google Maps search queries (e.g. `dentists in chicago`) |
| `num` | integer |  | `20` | Results to return per query (max `200`) |
| `gl` | string |  | `us` | Country for Google Maps results — match this to the country you're searching in (`ca`, `gb`, `de`, etc.) |
| `hl` | string |  | `en` | Interface language for Google results (`fr`, `es`, `de`, etc.) |
| `fields` | string |  | — | Comma-separated list of fields to keep — leave blank to get everything |

### Example: multi-city lead generation

```
{
  "query": [
    "personal injury lawyers in houston",
    "personal injury lawyers in dallas",
    "personal injury lawyers in austin"
  ],
  "num": 200,
  "gl": "us",
  "hl": "en"
}
```

### Example: international search

```
{
  "query": ["coffee shops in london"],
  "num": 100,
  "gl": "gb",
  "hl": "en"
}
```

---

## Sample result

```
{
  "query": "restaurants in toronto",
  "searchString": "restaurants in toronto",
  "rank": 1,
  "position": 1,
  "title": "Black+Blue Toronto",
  "categoryName": "Restaurant",
  "type": "Restaurant",
  "categories": [
    "Restaurant",
    "Brunch restaurant",
    "Event venue",
    "Fine dining restaurant",
    "Lounge bar",
    "Seafood restaurant",
    "Steak house",
    "Sushi restaurant",
    "Wine bar"
  ],
  "types": [
    "Restaurant",
    "Brunch restaurant",
    "Event venue",
    "Fine dining restaurant",
    "Lounge bar",
    "Seafood restaurant",
    "Steak house",
    "Sushi restaurant",
    "Wine bar"
  ],
  "address": "130 King St W, Toronto, ON M5X 2A2, Canada",
  "neighborhood": "Old Toronto",
  "street": "130 King St W",
  "streetNumber": null,
  "city": "Toronto",
  "postalCode": "M5X 2A2",
  "state": "Ontario",
  "countryCode": "CA",
  "locatedIn": "Old Toronto",
  "timezone": "America/Toronto",
  "totalScore": 4.7,
  "rating": 4.7,
  "reviewsCount": 5589,
  "ratingCount": 5589,
  "reviewsDistribution": null,
  "priceLevel": "CA$100 or above",
  "phone": "+1 647-368-8283",
  "phoneNumber": "(647) 368-8283",
  "phoneUnformatted": "+16473688283",
  "website": "https://blackandbluesteakhouse.ca/toronto-home/",
  "domain": "blackandbluesteakhouse.ca",
  "placeId": "ChIJ243-C381K4gRHMKWCGU86iM",
  "dataId": "/g/11s9wnk_vb",
  "cid": "2587947340511232540",
  "cidHex": "0x882b357f0bfe8ddb:0x23ea3c650896c21c",
  "fid": "0x882b357f0bfe8ddb:0x23ea3c650896c21c",
  "googleMapsUrl": "https://www.google.com/maps/place/?q=place_id:ChIJ243-C381K4gRHMKWCGU86iM",
  "url": "https://www.google.com/maps/search/?api=1&query=Black%2BBlue+Toronto&query_place_id=ChIJ243-C381K4gRHMKWCGU86iM",
  "imageUrl": "https://lh3.googleusercontent.com/gps-cs-s/APNQkA...",
  "thumbnailUrl": "https://lh3.googleusercontent.com/gps-cs-s/APNQkA...",
  "logoUrl": "https://lh3.googleusercontent.com/-ih84iASeZ7Y/AAAAAAA.../photo.jpg",
  "owner": {
    "name": "Black+Blue Toronto (Owner)",
    "googleId": "102477914189084708456"
  },
  "location": {
    "lat": 43.6480996,
    "lng": -79.3831247
  },
  "latitude": 43.6480996,
  "longitude": -79.3831247,
  "plusCode": null,
  "temporarilyClosed": null,
  "permanentlyClosed": null,
  "openingHours": {
    "Friday": "11:30 AM–12 AM",
    "Saturday": "10:30 AM–12 AM",
    "Sunday": "10:30 AM–12 AM",
    "Monday": "11:30 AM–12 AM",
    "Tuesday": "11:30 AM–12 AM",
    "Wednesday": "11:30 AM–12 AM",
    "Thursday": "11:30 AM–12 AM"
  },
  "openingHoursDetailed": [
    { "day": "Friday",    "hours": ["11:30 AM–12 AM"] },
    { "day": "Saturday",  "hours": ["10:30 AM–12 AM"] },
    { "day": "Sunday",    "hours": ["10:30 AM–12 AM"] },
    { "day": "Monday",    "hours": ["11:30 AM–12 AM"] },
    { "day": "Tuesday",   "hours": ["11:30 AM–12 AM"] },
    { "day": "Wednesday", "hours": ["11:30 AM–12 AM"] },
    { "day": "Thursday",  "hours": ["11:30 AM–12 AM"] }
  ],
  "openingHoursState": "Open · Closes 12 AM",
  "serviceHours": {
    "Lunch":       { "Friday": "11:30 AM–2 PM" },
    "Happy hours": { "Friday": "2:30–5:30 PM" },
    "Kitchen":     { "Friday": "11:30 AM–12 AM" },
    "Dinner":      { "Friday": "3 PM–12 AM" },
    "Brunch":      { "Friday": "Closed" }
  },
  "bookingLinks": [
    "https://party-request.tripleseat.com/venues/8qsUeRbI/?rwg_token=...",
    "https://www.google.com/maps/reserve/v/dine/c/DUtUFyMlWBE?source=pa",
    "https://party-request.tripleseat.com/venues/8qsUeRbI/?rwg_token=..."
  ],
  "popularTimes": null,
  "about": null
}
```

---

## Use cases

- **Lead generation** — Build targeted prospect lists by business type and location
- **Competitor research** — Monitor competitor ratings, hours, and pricing across cities
- **Market analysis** — Map business density and coverage in any region
- **Directory building** — Populate local business directories with verified contact data
- **CRM enrichment** — Append phone, website, coordinates, and hours to existing records

---

## Notes

- Multiple queries run in one actor invocation — no need to start separate runs per city or keyword.
- Set `gl` to match the country you're targeting for the most accurate local results (`gl=ca` for Canada, `gl=gb` for UK, `gl=de` for Germany).
- Use `fields` to trim output to only the columns you need — useful for large runs where you want a lean dataset.
- Results are cached on our infrastructure for 1 hour, so repeated identical queries return immediately without re-fetching.
- This actor makes no browser calls. It connects directly to our scraping infrastructure, meaning cold starts are near-instant and memory usage stays flat throughout the run.