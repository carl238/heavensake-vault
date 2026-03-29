---
type: knowledge
status: validated
last-synthesized: 2026-03-28
source-sessions:
  - 2026-03-28 Perplexity Computer SEO Deep Dive (Carl session)
  - 2026-03-18 AI Marketing Strategy — Carl + Jakub
  - HEAVENSAKE.COM SEO Audit Report (Jakub Cambor, March 2026)
  - HEAVENSAKE Keyword Research March 2026 (DataForSEO via Jakub)
  - HEAVENSAKE Semantic SEO Analysis 2026 (Giancarlo / Semrush)
tags: [seo, structured-data, json-ld, gtm, schema, technical, google, ai-readiness]
---

# SEO & Structured Data Status

Complete record of HEAVENSAKE's SEO technical infrastructure, structured data deployment, and audit findings. This is the reference document for all SEO-related decisions.

See also: [[Tech & Automation Stack]] | [[SEO & GEO Keyword Reference]] | [[AI Agent Readiness — Shopify Deployment]]

---

## I. Structured Data (JSON-LD via GTM)

All structured data is deployed via **Google Tag Manager** (GTM-NHZKXBTR), not hardcoded in Shopify theme files. This was a deliberate architectural choice: GTM injection allows updates without developer involvement.

### Live Schema Markup (as of March 28, 2026)

| Schema Type | GTM Tag ID | Scope | Key Details |
|---|---|---|---|
| **Organization** | Tag 6 | All pages | founder: Régis Camus, foundingDate: 2016, sameAs: 5 social profiles |
| **Product** | Tag 5 | Product pages only | All 5 products: Label 12, Label Azur, Label Noir, Prestige I, Noguchi Prestige |
| **Article** | Tag 7 | All 12 blog posts | Covers all `/blogs/journal/*` URLs with headline, datePublished, author |

### GTM Version History

| Version | What Changed | Date |
|---|---|---|
| v3 | Product Schema deployed (tag 5) | March 2026 |
| v4 | Organization Schema (tag 6) + Article Schema (tag 7) added with All Pages triggers | March 28, 2026 |
| v5 | Organization Schema corrected: founder → Régis Camus only, foundingDate → 2016 | March 28, 2026 |

### GTM Account Details

| Field | Value |
|---|---|
| Account ID | 6320865814 |
| Container ID | 233459423 |
| Container Tag | GTM-NHZKXBTR |

### Known Gaps in Organization Schema

The current GTM-injected Organization schema is functional but lighter than the full corrected version. Missing optional fields that can be restored later:
- `brand` (sub-entity)
- `slogan` ("A Better High")
- `knowsAbout` (sake, assemblage, etc.)

These are non-critical — Google Rich Results validator passes without them.

---

## II. Technical SEO Issues — Confirmed & Unfixed

These issues were identified in the March 2026 audit session and independently verified against the live site. They are real and should be addressed.

### Critical (Impact on ranking and user experience)

| Issue | Details | Fix Complexity |
|---|---|---|
| **Duplicate H1 tags** | Every product page and blog post has 2 H1 tags (page title + cart drawer "Your Cart"). Shopify theme bug. | Medium — theme edit |
| **5× duplicate age-verify scripts** | `ageverify.js` loaded 5 times on every page. Unnecessary render-blocking weight. | Easy — theme cleanup |
| **No lazy loading on images** | All product/blog images load eagerly. Hurts LCP (Largest Contentful Paint). | Easy — add `loading="lazy"` |
| **og:image uses http://** | Social sharing meta tag uses `http://` instead of `https://`. Browsers/platforms may block or warn. | Easy — theme edit |
| **Missing alt text (~70%)** | Most product images lack descriptive alt attributes. Hurts image SEO and accessibility. | Medium — content task |

### High (Functional but degrading)

| Issue | Details |
|---|---|
| **H2 pollution** | Cart drawer injects `<h2>Your Cart</h2>` into every page's heading hierarchy. Confuses crawlers. |
| **404 errors** | `/about`, `/blog`, `/pages/about` all return 404. These are common navigation targets. |
| **/collections/sake empty** | The collection page exists but shows no products. Should either populate or redirect. |
| **No visible dates/author on blog posts** | Blog articles lack visible publication dates and author names (bad for E-E-A-T signals). |
| **Sipsy footer link** | External link to Sipsy (brewery partner?) in footer — leaks PageRank to an unrelated domain. |

### Medium (Quality improvements)

| Issue | Details |
|---|---|
| **No breadcrumb navigation** | Product and blog pages lack breadcrumbs (no BreadcrumbList schema either). |
| **No FAQ schema** | FAQ content exists in some blog posts but is not marked up as FAQPage schema. |
| **Thin meta descriptions** | Several product pages have generic or missing meta descriptions. |
| **No sitemap optimization** | Default Shopify sitemap includes non-indexed pages. |

---

## III. Jakub Cambor's SEO Audit — Evaluation

**Source:** HEAVENSAKE.COM SEO Audit Report (March 2026), delivered with keyword research XLSX.
**Cost:** £650 for audit + XLSX data. Proposed: £1,500 for technical fixes + £1,000/month for monitoring.

### What Was Accurate
- H1 duplication, missing alt text, lazy loading absence — all confirmed
- 404s on /about and /blog — confirmed
- General recommendation to invest in content and backlinks — sound advice

### What Was Inaccurate or Misleading
| Claim | Reality |
|---|---|
| "None of 5 pages have Product schema" | His own Table 7 shows 2 of 5 have it. As of March 28, all 5 have Product JSON-LD via GTM. |
| "Hero image 2.98MB" alarm | Shopify CDN auto-serves WebP at ~10.6KB. The raw source file is large but never served to users. |
| "HubSpot + Klaviyo overlap" | Zero HubSpot tracking references found on the site. Only Klaviyo is installed. |
| "200,000+ monthly searches" opportunity | Inflated by duplicates, near-duplicates, and competitor brand terms in his XLSX data. |
| "10-20x growth in 12 months" | Unrealistic. Honest projection with aggressive content investment: 4-6x at 12 months. |

### Business Assessment
- The audit is AI-generated using DataForSEO API data (~$10 API cost for the raw data)
- The XLSX keyword research data is the genuine asset worth extracting
- Keyword volumes in Jakub's data consistently lower than Giancarlo's Semrush data (e.g., "buy sake online" 480 vs 3,000-5,000)
- Tippsy comparison is misleading (marketplace with 800+ products vs single-brand with 5 SKUs)
- **Recommendation (delivered to Carl):** Do not pay £1,500 for fixes (done in-house via Perplexity Computer). Do not pay £1,000/month for monitoring. Extract value from XLSX, move on.

### Jakub's Useful Data (Retained)
The keyword research XLSX contains 7 sheets of DataForSEO data. Relevant findings have been integrated into [[SEO & GEO Keyword Reference]].

---

## IV. Google Analytics & Tag Manager Configuration

| System | ID | Notes |
|---|---|---|
| GA4 Property | 468479136 | Connected and receiving data |
| GA4 Measurement ID | G-RFJ3RQPYV7 | In Shopify theme |
| GTM Container | GTM-NHZKXBTR | All structured data injected here |
| Shopify Store | heavensake-us.myshopify.com | US DTC store |
| Active Theme | 128229310513 (20260319_giancarlo_def) | Giancarlo's deployment |

---

## V. What Was Done vs What Remains

### Completed (March 28, 2026)
- [x] Organization JSON-LD deployed via GTM (founder: Régis Camus, foundingDate: 2016)
- [x] Product JSON-LD deployed via GTM (all 5 products)
- [x] Article JSON-LD deployed via GTM (all 12 blog posts)
- [x] Jakub's audit fully evaluated and findings validated/invalidated
- [x] Keyword research data extracted and integrated into Obsidian

### Not Yet Done (Requires Shopify Theme Edits)
- [ ] Fix duplicate H1 tags (theme-level change)
- [ ] Remove 4 of 5 duplicate ageverify.js scripts
- [ ] Add `loading="lazy"` to all product/blog images
- [ ] Fix og:image from http:// to https://
- [ ] Add alt text to ~70% of images missing it
- [ ] Remove or nofollow Sipsy footer link
- [ ] Fix /about and /blog 404s (create pages or set up redirects)
- [ ] Populate or redirect /collections/sake
- [ ] Add visible dates and author names to blog posts
- [ ] Add BreadcrumbList schema (can do via GTM)
- [ ] Add FAQPage schema to eligible blog posts (can do via GTM)

### Decision: Who Handles Theme Fixes?
The Shopify theme is managed by the dev team (historically ATOJ, now Giancarlo's theme). Theme-level HTML/Liquid edits require someone with Shopify theme access. GTM-injectable items (breadcrumbs, FAQ schema) can be handled by Perplexity Computer.

---

## VI. Key Principle

> **All structured data changes go through GTM, not Shopify theme files.** This keeps SEO infrastructure independent of developer cycles and allows rapid iteration.

This was established as the operating principle on March 28, 2026 during the Perplexity Computer SEO session with Carl.

---

## VII. GSC Structured Data Fixes (June 2025)

### Issue 1: Review Snippets — `itemReviewed` Error
**Reported by:** Google Search Console (Review Snippets report)
**Affected URL:** `heavensake.com/products/junmai12`
**Error:** "Missing field 'name' in 'itemReviewed'" — caused by redundant `itemReviewed` objects nested inside the Product schema in the Shopify theme.

**Root Cause:** The snippet `snippets/product-schema.liquid` contained 3 unnecessary `itemReviewed` blocks (lines 42, 52, 62) that created malformed Review schema. These were part of Giancarlo's theme deployment, unrelated to the GTM-based structured data work.

**Fix Applied:**
- Removed 3 `itemReviewed` lines from `product-schema.liquid`
- Fixed trailing commas and `offers` array formatting
- Validated with Schema Markup Validator (0 errors)
- GSC "Validate Fix" initiated

### Issue 2: Merchant Listings — Price Format Error
**Reported by:** Google Search Console (Merchant Listings report)
**Affected URL:** `jp.heavensake.com/products/label-azur`
**Error:** "Invalid floating point number in property 'price'" — price values contained commas (e.g., `8,800` instead of `8800`).

**Root Cause:** The snippet `snippets/agent-readiness-product-jsonld.liquid` output `{{ variant.price | money_without_currency }}` which includes comma formatting for Japanese Yen prices.

**Fix Applied:**
- Added `| remove: ','` filter to 3 price output lines (lines 221, 222, 236) in `agent-readiness-product-jsonld.liquid`
- Validated with Schema Markup Validator (0 errors)
- GSC "Validate Fix" initiated (may need re-validation after CDN cache clears, ~30 min)

### Prevention Notes
- **Theme-level schema edits** carry risk of GSC errors when themes are redeployed or updated. This reinforces the Section VI principle: structured data should go through GTM where possible.
- **Price formatting** is locale-dependent in Shopify. Any future multi-currency or multi-locale schema must account for `money_without_currency` including commas in some locales.
- **Monitor GSC weekly** for new structured data issues, especially after theme updates.
