---
type: knowledge
source: notebooklm-extraction
status: validated
last-updated: 2026-03-25
tags: [legal, compliance, three-tier, evin-law, age-gating, alcohol-advertising, US-law, France-law]
---

# Legal & Compliance

Legal and regulatory constraints governing how HEAVENSAKE operates, sells, and advertises. Non-negotiable. Any deviation risks fines, license revocation, or reputational damage.

---

## 1. US Alcohol Sales Law — The Three-Tier Bypass

**The Problem:** HEAVENSAKE is legally prohibited from selling alcohol directly to individual consumers in the United States under the US three-tier distribution system (Manufacturer → Distributor → Retailer). A brand cannot legally own a direct-to-consumer alcohol checkout in its own name.

**The Workaround:**
- The [[Shopify]] checkout and invoicing entity is legally owned by the US distributor: [[SIPC]] (also referred to as [[CIPC]])
- HEAVENSAKE acts only as the **marketing front** — it drives traffic to the Shopify store but does not technically complete the sale
- HEAVENSAKE holds admin access to the Shopify backend solely to **extract customer data**
- All legal alcohol sale responsibility sits with SIPC/CIPC

**Implication for the team:** When customers buy from "heavensake.com," the legal seller of record is SIPC/CIPC, not HEAVENSAKE. This must be maintained for compliance. No internal documents should describe HEAVENSAKE as "selling" alcohol in the US without this nuance.

**Open question:** The exact margin structure SIPC takes for fulfilling US DTC Shopify orders is not documented in current sources. The final legal liability boundary between HEAVENSAKE and CIPC/SIPC for US alcohol sales also requires formal legal documentation.

---

## 2. Evin Law — France Advertising Compliance

**What it is:** The Loi Évin (Evin Law) is France's strict alcohol advertising legislation (Law No. 91-32 of January 10, 1991). It governs what can and cannot be communicated in alcohol advertising in France.

**HEAVENSAKE obligations:**
- Must avoid any narrative that promotes irresponsible or excessive consumption
- Cannot use imagery or language that associates alcohol consumption with social success, sexual performance, or athletic achievement in the French market
- All French-market advertising must adhere to Evin Law specifications
- The Monaco F1 event content (France-adjacent market) falls under these regulations

**Scope:** Also applies to French-language content published globally.

---

## 3. Age-Gating Requirements

**What is required:**
- All HEAVENSAKE digital properties (website, landing pages, email captures, e-commerce) must implement strict age-gating before any alcohol purchase, product information, or brand content can be accessed
- Age-gating is a legal requirement in the US, France, Japan, UK, and most other priority markets

**Current implementation:**
- Age gate is present on the HEAVENSAKE website
- Must be reviewed on all new landing pages (Type A and Type B — see [[SOPs & Workflows]]) before launch
- Any third-party partner integration (pop-ups, embeds, affiliate links) must maintain age-gating compliance

---

## 4. Alcohol Advertising Regulations — Multi-Market

| Market | Key Regulation | Key Rule |
|--------|---------------|----------|
| **France** | Loi Évin | No promotion of excessive consumption; restricted placement (no TV, cinema, billboards near schools) |
| **USA** | DISCUS / TTB / State laws | Must include responsible drinking disclaimer; age-gated ads on digital platforms |
| **Japan** | Self-regulatory norms (National Tax Agency) | Avoid youth targeting; responsible consumption messaging required |
| **UAE** | Federal Law No. 3 of 1987 | Alcohol advertising severely restricted; activations must be within licensed premises only |

**Cross-market principle:** Content produced for one market may not comply in another. All international campaigns must be reviewed for multi-market compliance before publication.

---

## 5. Intellectual Property — Torii Gate Design

Carl flagged a concern about IP protection for the Torii gate design that is being used for the Monaco F1 anniversary event. The design work is being executed by [[Studio Magla]] / [[Lisa Hanze]] (Ruby Carmen). Carl requested follow-up to ensure HEAVENSAKE retains ownership of any custom creative assets produced by event production partners.

**Status:** Flagged — not yet confirmed as resolved. See [[Contradictions & Open Questions]].

---

## 6. Magnum Bottle Defect (Production Compliance)

A quality control issue was identified during sample testing: the cap from a standard 720ml bottle fits **too loosely** on the Magnum format bottle. Initial specs required the neck and cap opening to be identical to the 720ml. The Magnum requires remanufacturing before launch.

**Risk:** Shipping a product with a defective seal risks wine oxidation, customer complaints, and potential liability.

**Owner:** [[Sebastien L'Hermitte]] / supply chain lead. Status: In progress.

---

## 7. Shipping Compliance

- All HEAVENSAKE products must be shipped globally in **reefer containers at exactly 5°C (45°F)** to preserve namazake-like vitality and aroma
- This is both a quality standard and a legal requirement in markets where temperature-controlled alcohol transport is mandated
- Custom presentation boxes shipped **inside** the bottle box are **BANNED** — alters shipping weight classes and risks breakage; custom items must be shipped separately (custom boxes cost ~10× standard)

---

## Related Notes

- [[SOPs & Workflows]]
- [[Vendors & Agency Failures]]
- [[DTC & E-Commerce Strategy]]
- [[Contradictions & Open Questions]]
