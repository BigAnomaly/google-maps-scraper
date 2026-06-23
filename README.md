[Google Maps Scraper](https://apify.com/buseta/google-maps-scraper?fpr=data)

# Google Maps Scraper + AI Business Intelligence

Fast, low-cost Google Maps scraper with AI-powered lead scoring and personalized outreach generation. Extract businesses, reviews, emails, and social links from Google Maps — no browser needed, pure HTTP for maximum speed and minimum cost.

## Features

- **Search with auto-grid** — Bypass Google's 20-result limit. Automatically subdivides large areas into grid cells to find hundreds or thousands of businesses
- **Multi-query batch** — Paste a list of searches (e.g., 50 cities x 1 category) and scrape them all in one run
- **Email & social extraction** — Crawl business websites to find email addresses and social media links (free, no extra charge)
- **Reviews** — Scrape reviews with text, rating, date, reviewer info, and owner responses
- **Filters** — Filter by rating range or find only businesses without a website
- **AI Lead Scoring** — AI analyzes each business and generates a lead score (0-100) with a ready-to-send cold email
- **AI Market Report** — One-click market intelligence report for your entire dataset
- **CSV-friendly output** — Flat fields ready for Excel, Google Sheets, or CRM import

## Pricing

| Event | Price |
| --- | --- |
| Place scraped | $4.00 / 1,000 |
| Review scraped | $0.50 / 1,000 |
| AI Lead Score + Outreach draft | $35.00 / 1,000 |
| AI Market Report | $0.10 / run |
| Email & social extraction | Free |
| Platform usage | Free |

### Typical Run Costs

| Use Case | Places | Reviews | Emails | AI | Total Cost |
| --- | --- | --- | --- | --- | --- |
| Quick lead search (20 places + emails) | $0.08 | — | Free | — | **$0.08** |
| City-wide lead gen (200 places + emails) | $0.80 | — | Free | — | **$0.80** |
| Full pipeline (200 places + emails + AI outreach) | $0.80 | — | Free | $7.00 | **$7.80** |
| Competitor research (100 places + 10 reviews each) | $0.40 | $0.50 | — | — | **$0.90** |
| Market report (500 places + AI report) | $2.00 | — | — | $0.10 | **$2.10** |

## Use Case Examples

### 1. Lead Generation — Find businesses without websites

You're a web design agency looking for prospects in Miami.

**Input:**

```
{
    "mode": "search",
    "search_queries": ["restaurants in Miami", "salons in Miami", "gyms in Miami"],
    "max_places": 200,
    "only_without_website": true,
    "get_emails": false,
    "ai_lead_scoring": true,
    "ai_goal": "web_design",
    "ai_sender_name": "Sarah"
}
```

**What you get:** 200 businesses in Miami that don't have a website, each with a lead score and a personalized email like:

```
Subject: Helping Miami Salons Get Found Online

Hi Bella's Beauty Lounge,

I noticed you have a great Google rating (4.8★) but no website yet — which means potential customers searching "salons near me"
might be finding your competitors first. A simple, mobile-friendly website could help you capture those local searches
and let customers book online.

Would you be open to a quick 10-minute chat about getting one set up?

Best,
Sarah
```

### 2. SEO Agency — Find businesses with weak online presence

**Input:**

```
{
    "mode": "search",
    "search_queries": ["plumbers in Dallas"],
    "max_places": 100,
    "get_reviews": true,
    "max_reviews_per_place": 5,
    "get_emails": true,
    "ai_lead_scoring": true,
    "ai_goal": "seo_marketing",
    "ai_sender_name": "Mike"
}
```

**What you get:** 100 plumbers in Dallas with their emails, reviews, and AI-generated outreach emails focused on SEO opportunities.

### 3. Reputation Management — Find businesses with bad reviews

**Input:**

```
{
    "mode": "search",
    "search_queries": ["dentists in Chicago"],
    "max_places": 200,
    "max_rating": 3.5,
    "get_reviews": true,
    "max_reviews_per_place": 10,
    "reviews_sort": "lowest",
    "ai_lead_scoring": true,
    "ai_goal": "reputation_management"
}
```

**What you get:** Dentists in Chicago with 3.5 stars or lower, their worst reviews, and personalized outreach pitching reputation management services.

### 4. Market Research — Analyze an entire market

**Input:**

```
{
    "mode": "search",
    "search_queries": ["coffee shops in San Francisco"],
    "max_places": 500,
    "ai_market_report": true
}
```

**What you get:** 500 coffee shops with full data, plus an AI market report:

```
{
    "type": "ai_market_report",
    "market_summary": "The coffee shop market in San Francisco is highly saturated with 500+ providers...",
    "saturation_level": "high",
    "key_findings": [
        "Average rating is 4.4★ — quality bar is high",
        "23% of shops have no website",
        "The Mission district has 3x more shops than Sunset despite similar population"
    ],
    "opportunities": [
        {
            "opportunity": "115 coffee shops have no website",
            "target_count": 115,
            "action": "Web design outreach targeting established shops (4+ stars) without web presence"
        }
    ],
    "recommendations": [
        "Focus on the Sunset and Richmond districts — underserved relative to population",
        "Target businesses with 50+ reviews but no website — established but digitally behind"
    ]
}
```

### 5. Custom B2B Sales — Sell anything to local businesses

You run a commercial cleaning company and want to pitch office cleaning to businesses.

**Input:**

```
{
    "mode": "search",
    "search_queries": ["law firms in Boston", "accounting firms in Boston", "dental offices in Boston"],
    "max_places": 100,
    "get_emails": true,
    "ai_lead_scoring": true,
    "ai_goal": "custom",
    "ai_custom_pitch": "I run CleanPro Commercial Cleaning. We provide daily office cleaning, deep cleaning, and sanitization services for professional offices. Our pricing starts at $500/month.",
    "ai_sender_name": "James from CleanPro"
}
```

### 6. Simple Scrape — Just get the data, no AI

**Input:**

```
{
    "mode": "search",
    "search_queries": ["hotels in London"],
    "max_places": 50,
    "get_emails": true
}
```

**What you get:** 50 hotels with name, address, phone, website, rating, categories, coordinates, hours, emails, and social links.

### 7. Scrape Specific Places by URL

**Input:**

```
{
    "mode": "place_urls",
    "place_urls": [
        "https://www.google.com/maps/place/Gramercy+Tavern/@40.7384555,-73.9885064,17z/data=!3m1!4b1!4m6!3m5!1s0x89c259a1820824bd:0x2b79dcdc251b8415",
        "https://www.google.com/maps/place/Le+Bernardin/@40.7615199,-73.9816553,17z"
    ],
    "get_reviews": true,
    "max_reviews_per_place": 20,
    "get_emails": true
}
```

### 8. Area Coverage with Bounding Box

Scrape all gyms within a specific geographic area:

**Input:**

```
{
    "mode": "search",
    "search_queries": ["gym"],
    "bounding_box": {
        "sw_lat": 40.70,
        "sw_lng": -74.02,
        "ne_lat": 40.80,
        "ne_lng": -73.93
    },
    "max_places": 500
}
```

## Output Fields

Each place in the dataset includes:

| Field | Description |
| --- | --- |
| `name` | Business name |
| `address` | Full address |
| `phone` | Phone number |
| `website` | Website URL |
| `email` | Primary email (if email extraction enabled) |
| `emails_all` | All emails found, comma-separated |
| `category` | Primary business category |
| `categories_all` | All categories, comma-separated |
| `rating` | Google rating (1.0 - 5.0) |
| `place_id` | Google Place ID |
| `google_maps_url` | Direct Google Maps link |
| `latitude` | Latitude coordinate |
| `longitude` | Longitude coordinate |
| `description` | Business description from Google |
| `price_level` | Price level ($, $$, $$$) |
| `hours_monday` ... `hours_sunday` | Opening hours per day |
| `social_facebook` | Facebook page URL |
| `social_instagram` | Instagram profile URL |
| `social_twitter` | Twitter/X profile URL |
| `social_linkedin` | LinkedIn page URL |
| `social_youtube` | YouTube channel URL |
| `reviews` | Array of review objects (if enabled) |
| `ai_lead_score` | Lead score 0-100 (if AI enabled) |
| `ai_lead_reason` | Why this score was given |
| `ai_outreach_subject` | Email subject line |
| `ai_outreach_email` | Personalized email draft |

## AI Goal Guide

When enabling AI Lead Scoring, choose the goal that matches your business:

| Goal | Best For | What AI Focuses On |
| --- | --- | --- |
| **Web Design** | Web agencies, freelance developers | Targets businesses with no website. Pitches modern web presence, online booking, competitor comparison |
| **SEO & Marketing** | SEO agencies, Google Ads specialists | Targets businesses with low visibility, few reviews, or weak online presence vs. competitors |
| **Reputation Management** | Reputation agencies, review management tools | Targets businesses with low ratings. References specific negative review themes, offers solutions |
| **General B2B Sales** | Any product/service sold to local businesses | Professional intro pitch. Describe your offering in the "Custom pitch" field |
| **Custom** | Anything else | Write your own pitch context. AI personalizes it for each business using their profile data |

## How Auto-Grid Works

When you search for "dentists in Chicago" with `max_places: 500`, the scraper:

1. Geocodes "Chicago" to a bounding box
2. Divides the area into grid cells (~2km each)
3. Searches each cell separately (20 results per cell)
4. Deduplicates results by Place ID
5. Stops when `max_places` is reached

This bypasses Google's 20-result-per-query limit, giving you comprehensive area coverage.

## Tips

- **Start small** — Test with `max_places: 20` first to verify data quality
- **Email extraction is free** — Always enable it for lead gen use cases
- **Use multi-query** — Instead of one broad search, use specific queries: `["pizza in Brooklyn", "pizza in Queens", "pizza in Manhattan"]`
- **Filter smartly** — Use `only_without_website: true` for web design leads, or `max_rating: 3.5` for reputation management leads
- **AI works best with reviews** — Enable `get_reviews` alongside AI lead scoring for more accurate scores and better outreach personalization