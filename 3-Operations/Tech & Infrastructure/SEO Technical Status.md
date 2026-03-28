---
type: knowledge
status: validated
last-updated: 2026-03-28
source: perplexity-computer-seo-session
tags: [seo, technical, shopify, gtm, schema, performance]
---

# SEO Technical Status

The definitive record of heavensake.com's technical SEO state. Maintained by Perplexity Computer, validated against the live site.

---

## Current State (March 28, 2026)

**Shopify store:** heavensake-us.myshopify.com
**Theme:** Dawn v15.4.0 ("20260319_giancarlo_def"), ID 128229310513
**Custom API app:** "SEO Cleanup Tool" — scopes: write_files, write_script_tags, write_themes

### What's Live and Working

| Item | Status | Method | Date |
|------|--------|--------|------|
| Hero image WebP | LIVE | Shopify API (theme asset update) | 2026-03-28 |
| og:image HTTPS | LIVE | Theme code editor (meta-tags.liquid line 23) | 2026-03-28 |
| H1 tag structure | LIVE | header.liquid — h1→div at lines 152, 179, 195, 222 | 2026-03-28 |
| Heading hierarchy | LIVE | article-coming-up-next.liquid + email-signup-banner.liquid | 2026-03-28 |
| Product JSON-LD schema | LIVE | GTM (5 products) — Version 3 | 2026-03-27 |
| Organization JSON-LD | LIVE | GTM (homepage only) — Version 5 | 2026-03-27 |
| Article JSON-LD | LIVE | GTM (12 blog posts) — Version 4 | 2026-03-27 |
| Blog meta descriptions | LIVE | Shopify blog editor | 2026-03-28 |
| Product image alt text | LIVE | Shopify product editor (10 images, 5 products) | 2026-03-28 |
| Blog image alt text | LIVE | Shopify blog editor (11 posts) | 2026-03-28 |
| /collections/sake | LIVE | 6 products (Label Azur, Label 12, Prestige I + 3 others) | 2026-03-28 |
| Lazy loading | ALREADY IMPLEMENTED | Dawn v15.4.0 native (card-product, card-collection, article-card) | Verified 2026-03-28 |

### Performance Impact

| Metric | Before | After |
|--------|--------|-------|
| Hero image size | 2.84 MB (PNG) | 57 KB (WebP, q90) | 
| Estimated page weight reduction | ~2.8 MB saved on homepage load |
| Schema coverage | 0 pages | 18 pages (5 products + 1 homepage + 12 articles) |
| Alt text coverage | Incomplete | All product images + 11 blog featured images |

---

## Structured Data (GTM Container: GTM-NHZKXBTR)

All structured data is deployed via Google Tag Manager — zero code in the Shopify theme.

| Schema Type | Scope | GTM Version | Notes |
|------------|-------|-------------|-------|
| Product | 5 product pages | Version 3 | Name, price, image, SKU, brand, availability |
| Organization | Homepage only | Version 5 | Founder: Régis Camus. Founded 2016. |
| Article | 12 blog posts | Version 4 | Headline, author, datePublished, image |

**Important:** The Organization schema lists Régis Camus as sole founder. No other founders are mentioned. This is a Carl directive.

---

## Known Issues — Not Yet Resolved

### Age Verification Script Duplication (Workaround Active)

**Problem:** 5 duplicate instances of age-verify-with-email-capture.herokuapp.com + 1 smart-age-verification + 1 orphaned jQuery script. All injected via Shopify's `content_for_header` from previously uninstalled apps. The ScriptTag API returns empty (count: 0) — these are orphaned at the platform level.

**Workaround:** A MutationObserver script blocker was injected into theme.liquid after `content_for_header`. It intercepts script elements as they're added to the DOM and removes duplicates at runtime.

**Permanent fix:** Contact Shopify Support and ask them to purge orphaned ScriptTags. Only Shopify can remove them — the API and admin UI cannot see them.

### Items Jakub's Audit Got Wrong

These claims from the March 2026 SEO audit were verified as incorrect:

1. **"Zero lazy loading"** — False. Dawn v15.4.0 has proper lazy loading in card-product.liquid, card-collection.liquid, and article-card.liquid.
2. **"OUR WORLD" as a separate H2** — False. This is a navigation menu item, not a heading tag in the theme.
3. **"AMBUSH & HEAVENSAKE" blog post** — Not found in admin articles list.

---

## Shopify API Access

A custom app ("SEO Cleanup Tool") was created during this session for API-level theme and file operations.

- **Client ID:** 691f13d87d18ee15ce035425499421ee
- **Scopes:** write_files, write_script_tags, write_themes
- **Note:** The Pipedream Shopify connector (shopify_developer_app__pipedream) returns null for all queries due to insufficient scopes. Use the custom app token or browser for Shopify operations.

---

## Google Analytics & Search Console

| Property | ID | Notes |
|----------|-----|-------|
| GA4 (Main) | 468479136 ("HEAVENSAKE NEW") | Europe/Rome timezone |
| GA4 (Japan) | 468600383 ("HEAVENSAKE NEW JP") | Asia/Tokyo timezone |
| Measurement ID | G-RFJ3RQPYV7 | |
| GSC | carl@heavensake.com property | Set up ~March 10, 2026 |

**GSC data warning:** The property was set up March 10, 2026. Any "Last 3 months" reports before late June 2026 will show incomplete data. Always cross-reference the data collection window.

---

## SEO Content Pipeline

4 pillar articles identified as highest-ROI content:
1. "What Is Sake" (14,800 monthly volume)
2. "Types of Sake" (12,100)
3. "Sake Cocktails" (3,600)
4. "Best Sake Brands" (1,300)

Full 30-topic blog calendar maintained separately. See [[SEO & GEO Keyword Reference]] for the complete keyword list.

---

## Related Notes

- [[Tech & Automation Stack]]
- [[SEO & GEO Keyword Reference]]
- [[Jakub Cambor]]
- [[Vendors & Agency Failures]]
