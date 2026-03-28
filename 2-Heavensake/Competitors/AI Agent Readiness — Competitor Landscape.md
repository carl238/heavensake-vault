---
type: competitive-intelligence
status: validated
last-updated: 2026-03-27
tags: [competitors, ai-readiness, geo, structured-data, agent-commerce, benchmark]
---

# AI Agent Readiness — Competitor Landscape

How well can AI shopping agents discover, evaluate, and recommend each brand? Scored 1-10 based on structured data, schema markup, bot access, and e-commerce completeness.

See also: [[Competitor Intelligence]] | [[Digital Strategy]] | [[Product Portfolio]]

---

## Rankings (March 2026)

| Rank | Brand | Score | Platform | Key Differentiator |
|------|-------|-------|----------|-------------------|
| 1 | **SAKE HUNDRED** | 8.5/10 | Shopify | Full Product + Offer JSON-LD, BreadcrumbList, 113 products, rich editorial |
| 2 | **True Sake** | 8/10 | Shopify | Product + Offer + Organization + Breadcrumbs, ~500-1000 SKUs, massive educational content |
| 3 | **SOTO Sake** | 7.5/10 | WordPress + AccelPay | Product + Offer JSON-LD with ABV in structured data, BreadcrumbList |
| 4 | **IWA Sake** | 6/10 | WordPress + Shopify (split domains) | Organization + BreadcrumbList on main site, separate Shopify store |
| 5 | **Brooklyn Kura** | 4/10 | Shopify | Zero structured data, no schemas at all despite Shopify |
| 6 | **Dassai** | 3/10 | Custom (Nginx) | Zero JSON-LD, no DTC e-commerce in US, redirects to retailers |
| 7 | **HEAVENSAKE** (pre-optimization) | 3/10 | Shopify (Dawn) | FAQPage + Organization schema only, no Product/Offer |

---

## What Determines AI Agent Readiness

An AI shopping agent evaluating a sake brand looks for:

**Structured data (JSON-LD)** — Product schema with price, availability, brand. Offer schema with shipping and returns. BreadcrumbList for site hierarchy. FAQPage for common questions.

**Machine-readable product specs** — ABV, rice polishing ratio, acidity, tasting notes, food pairings encoded as structured fields, not just prose or CSS visuals.

**Bot access** — robots.txt allowing GPTBot, Google-Extended, CCBot. No Cloudflare blocks on legitimate AI crawlers.

**E-commerce completeness** — Full DTC flow (discover → compare → cart → checkout) accessible via API or MCP, not just a human-facing website.

**Shopify Agentic Storefronts** — Shopify's native feature that syndicates products to ChatGPT, Perplexity, and Copilot shopping agents. A toggle in Admin settings.

---

## Competitor Detail

### SAKE HUNDRED (sake100.com) — 8.5/10
The benchmark. Full Product + Offer JSON-LD on all product pages. BreadcrumbList. Excellent OG tags. 113 products in sitemap. Rich editorial content ("Story", "Letters from the Founder"). Only gap: ABV in HTML but not in JSON-LD.

### True Sake (truesake.com) — 8/10
The content moat. 500+ products on Shopify with proper Product + Offer + Organization + BreadcrumbList schemas. Deep educational resources ("Sake Wisdom", "Sake Types"). A retailer, not a brand — but their catalog depth gives them massive AI surface area.

### SOTO Sake (sotosake.com) — 7.5/10
The only competitor with ABV in structured data (14% in Product JSON-LD). WordPress + AccelPay. Product + Offer + BreadcrumbList schemas. Clean specs. Open robots.txt.

### IWA Sake (iwa-sake.jp) — 6/10
Split architecture: WordPress brand site (iwa-sake.jp) with Organization + BreadcrumbList, separate Shopify store (iwa-sake.us) for DTC. This fragmentation weakens agent signal. ~6-10 products. High-quality content about assemblage philosophy.

### Brooklyn Kura (brooklynkura.com) — 4/10
On Shopify but zero structured data deployed — no JSON-LD, no OG tags, no schemas. Strong local/craft positioning and subscription model. Standard Shopify robots.txt allows bots.

### Dassai (dassai.com) — 3/10
The most famous sake brand globally, yet completely invisible to AI agents. Custom Nginx site. Zero JSON-LD. No OG tags. No DTC e-commerce in the US — redirects to third-party retailers. Massive opportunity for HEAVENSAKE to be more agent-discoverable than Dassai.

---

## HEAVENSAKE Advantages

- **FAQPage schema on all 5 product pages** — unique among all competitors. Product-specific Q&A with ABV, pairings, storage, and brewing details.
- **Organization schema** — correctly implemented with full brand entity data.
- **robots.txt explicitly allows GPTBot, Google-Extended, CCBot** — most competitors only have default Shopify allowances.
- **Dassai's weakness is our opportunity** — the most recognized brand has the worst agent readiness. If we complete our structured data implementation, we leapfrog the market leader in agent discoverability.

---

## What HEAVENSAKE Needs to Match SAKE HUNDRED

1. Product + Offer JSON-LD on all product pages (code ready, pending deployment)
2. BreadcrumbList schema (code ready)
3. Shopify metafields populated with ABV, pairings, specs for all 5 products (definitions created, values pending)
4. Shopify Agentic Storefronts activated
5. ABV in structured data (would make HEAVENSAKE the second brand after SOTO to achieve this)
