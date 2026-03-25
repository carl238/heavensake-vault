# Tech Decisions from Marketing Meetings

> **Source:** Monday Marketing Meetings (June 2025 – March 2026)
> **Total entries:** 59 tech & operations mentions across 40 meetings
> **Last updated:** 2026-03-25

This note captures every technology tool, platform, infrastructure decision, implementation, bug, and blocker surfaced in the weekly Monday marketing meetings. Organized by system/tool, with chronological entries within each section.

---

## Navigation

- [[#HubSpot CRM]]
- [[#Shopify / Website]]
- [[#Meta Ads Manager / Instagram]]
- [[#Fireflies — Meeting Transcription]]
- [[#Notion]]
- [[#Airtable]]
- [[#Zapier / Automation]]
- [[#ChatGPT & AI Tools]]
- [[#Whisper Flow]]
- [[#ClickUp]]
- [[#Other Tools]]
  - [[#Canva]]
  - [[#TikTok]]
  - [[#LinkedIn]]
  - [[#Google Drive]]
  - [[#Tock]]
  - [[#Alibaba]]
  - [[#SEO Tools]]
  - [[#Analytics & Website Traffic]]
  - [[#NFC Authentication]]
  - [[#Honey Badger]]
  - [[#Instagram — Orphaned Account Issue]]

---

## HubSpot CRM

**Role:** Single source of truth for contact database, PR outreach, VIP segmentation, and automated email campaigns.
**Owner:** Giancarlo Cappelletti (system build); all team members (data input)

| Date | Topic | What was decided / done / blocked |
|------|-------|----------------------------------|
| **2026-03-16** | PR contacts database — mandatory fields | Giancarlo ensuring all HubSpot entries include mandatory PR contact owner email. Building A/B/C tiering system. Dashboards and task monitoring protocol in progress. |
| **2026-03-09** | Contact tiering and PR database | HubSpot has contacts but no tier system. Need A/B/C tiering. Team members need to classify A (top strategic), B, or C. Starting from 13 contacts (Carl's); Zak adding 30–40 from Airtable. Goal: 100 top PR/influencer contacts activable at click of button. |
| **2026-02-23** | PR database and automated outreach system | Building PR database in HubSpot or Notion with automated email outreach. Emails to be sent from individual team member accounts (personalized). Abdel may help with more advanced automation. System goal: 100 PR contacts activable with one click. |
| **2026-02-09** | Customer database for VIP identification | Extracting top 20% spenders from Shopify for Club Heaven VIP program. Gloria to share database with Zak and Nes. Prestige buyers and jacket buyers to be auto-flagged as VIP. |
| **2026-01-26** | Contact list migration to HubSpot | Zak had 30–40 PR/strategic contacts in Airtable; plan to transfer to HubSpot. Consolidating all contact data into HubSpot as single source of truth. |
| **2025-12-29** | CRM gap identified | E-commerce customers spending $3,000–$4,000/year never contacted. CRM to be used proactively for VIP outreach. Team asked to update CRM before newsletter send. |
| **2025-06-23** | AI-powered database enrichment | HubSpot AI enriching customer records with location data. 50% of existing records completed. Automatic for new signups. Enables geographic segmentation for Prestige marketing. |

**Current state (as of March 2026):** Tiering system (A/B/C) built by Giancarlo; team needs to execute the classification. PR database being populated. Dashboards in progress.

**Related:** [[Open Items — PR Database]] | [[Club Heaven VIP Program]] | [[PR Strategy — Direct Outreach]]

---

## Shopify / Website

**Role:** E-commerce platform (US site). Primary DTC sales channel.
**Owner:** Team Digital / ATOJ (Japanese dev agency)

### US Website Timeline

| Date | Milestone / Issue | Status |
|------|-------------------|--------|
| **2025-06-23** | New website planned; Prestige website had to be rebuilt for mobile (Safari/Chrome iPhone incompatibility). Vaas doing rebuild. | Remediation |
| **2025-07-21** | New website direction: e-commerce focused. Homepage: hero image + product + Regis story + blog. Newsletter signup with extended fields. Weekly blog for SEO. Japanese website target September. | Planning |
| **2025-10-27** | Website set to launch **October 29, 2025**. Ad agency ATOJ (Japan-based) lacks US consumer understanding — US team to provide all insights for ads. Zak confirmed adequate product stock for e-commerce. | Pre-launch |
| **2025-11-03** | **Launch bugs identified:** Website live at us.shop subdomain but heavensake.com still showing old site (URL forwarding not set up). Bugs: free shipping incorrectly shown; wrong photo of Nizawa; purchase dropdown missing. Carl to lead next-day meeting with ATOJ. | Critical bugs |
| **2025-11-10** | Pre-launch review with Japanese dev team scheduled. Previous agency "messed up everything" — switched mid-development. Features discussed: trade portal, gated product sheets, Buy Now in dropdown, events section. | Feature review |
| **2025-11-17** | **Website UX issues identified:** (1) Too many clicks to Buy Now — 3 clicks; (2) Label Noir bottle pops out from bottom wrong; (3) No contact form; (4) Missing 21+ age gate; (5) 'Explore Our Collection' button should be 'Buy Now'; (6) No events section. Floating Buy Now button approved as priority fix. | Feedback round |
| **2025-12-01** | US website launch confirmed. Newsletter to announce. Instagram post following week. Features planned: floating Buy Now, events landing page, downloadable asset portal (email gate), AI chatbot for FAQ, QR codes, Sensei Som page, 21+ gate, contact form. | Launched |
| **2026-01-12** | US website newly launched per Carl's announcement. Floating Buy Now being added. Japanese website also launching end of November 2025. Tagline: "Two cultures, one vision" on homepage. | Live |
| **2026-02-09** | Extracting top 20% Shopify spenders for Club Heaven. Gloria to share database with team. | Data extraction |

### Specific Website Features Decided

| Feature | Decision | Status |
|---------|----------|--------|
| Floating "Buy Now" button | Approved (Nov 17, 2025); reduces clicks to purchase | Implemented |
| Product sheets portal (gated) | Email capture required before download | Planned |
| 21+ age verification gate | Required by US alcohol law; flagged by John Pak | Not yet implemented as of Nov 2025 |
| Collaborations/Events page | Critical for Japanese accounts (95% check website first) | In development |
| Sensei Som / Events landing page | Inbound channel for event partnerships | Planned |
| AI chatbot (basic FAQ) | Approved concept | Planned |
| US tab with locations + events | Discussed; implementation TBD | Planned |

### E-Commerce Bug Log

| Date | Bug | Resolution |
|------|-----|-----------|
| 2025-10-20 | Label Noir shown as out of stock (it was in stock) | Offer customer Label Orange as compensation; fix stock display |
| 2025-11-03 | URL forwarding: heavensake.com showing old site | Carl leading ATOJ meeting |
| 2025-11-03 | Free shipping shown incorrectly at checkout | ATOJ to fix |
| 2025-11-03 | Wrong photo of Nizawa on product page | ATOJ to fix |
| 2025-11-03 | Purchase dropdown menu missing | ATOJ to fix |
| 2025-06-23 | Prestige signup confirmation email not received by Zak | Under investigation by Lauranne |

**Related:** [[Open Items — Website Features]] | [[Financial Notes — E-commerce VIP Customers]]

---

## Meta Ads Manager / Instagram

**Role:** Primary paid social channel; geo-targeted event advertising; organic content platform.
**Owner:** Team Digital; Lauranne Giudicelli (consultant); ATOJ (Japan ads)

| Date | Topic | What was decided |
|------|-------|-----------------|
| **2025-12-01** | Geo-targeted ad strategy | Carl proposed Instagram Reels/Stories ads targeting sake lovers by city (e.g., "sake lovers in Houston"). Confirmed: Instagram can target by city AND interests. Ads don't need to live on main feed — boosted stories only. Strategy: run event invite ads for restaurant partners, collect data, show ROI to accounts. Budget: ~**$300 minimum** for an event ad. |
| **2025-11-10** | US advertising agency search | Currently only have ads agency for Japan (ATOJ). Need US agency. Team planning to evaluate agencies. Still in progress as of early 2026. |
| **2025-09-29** | Ad strategy: geographic A/B testing | Lauranne planning A/B tests geographically: if CA not performing, try NY specifically. Once something works in one location, replicate to others. |
| **2025-08-18** | Reels strategy defined | Two types: (1) reach-oriented (new audience); (2) engagement-oriented (existing followers). 50/50 balance recommended. Best performing: Oto Omakase reel. |
| **2025-06-16** | Carl takes direct control of Instagram | Daily posts at 5–6pm. Excel document to track important contacts/events for sharing. |

**Platform insights:**
- Instagram vs. TikTok: same reel performs differently — high-end content outperforms on Instagram; trending/stoic content outperforms on TikTok (see [[#TikTok]])
- Sara (stoic Sara) content: outperformed on TikTok; Oto Omakase outperformed on Instagram

**Related:** [[Open Items — US Advertising Agency]] | [[Content Strategy]]

---

## Fireflies — Meeting Transcription

**Role:** Official company standard for meeting transcription. All Monday marketing meetings recorded.
**Contact:** Fred from Fireflies (fred@fireflies.ai) participates in all calls.

| Date | Topic | What happened |
|------|-------|--------------|
| **2026-03-23** | Integration with Notion | Zak set up Fireflies to feed meeting recordings directly into Notion. First call being tested. Goal: automatically document action items, assign tasks, make everything searchable. Will connect with Zapier for automation. |
| **2026-01-12** | Standard tool established | Carl instructed all team members to **stop using Otter.ai and cancel subscriptions**. Fireflies is the company standard. Fred from Fireflies added as permanent participant on all calls. |
| **2025-09-15** | Multi-language support question | Carl asked about Italian-language transcription. Answer: change language in Fireflies settings ("update language"). For multi-language calls (e.g., Japanese), better to download MP3 and use separate translation tool. ChatGPT better for non-English deciphering. |
| **2025-08-04** | Standard usage | Fireflies used for all Monday marketing meetings. Noemi requested it be added to Mila follow-up meeting. |

**Current integration plan:** Fireflies → Notion (via Zapier) for automatic task creation from action items.

**Related:** [[Notion]] | [[Zapier / Automation]]

---

## Notion

**Role:** Knowledge management and project tracking. Being set up to receive Fireflies output.
**Owner:** Zak Gross (setup); team-wide usage planned

| Date | Topic | What happened |
|------|-------|--------------|
| **2026-03-23** | Fireflies integration | Zak set up Fireflies to feed recordings into Notion. First call being tested. All action items, tasks to be auto-documented and searchable. |
| **2026-02-23** | PR database option | PR database being considered for HubSpot OR Notion with automated email outreach. HubSpot ultimately preferred as primary CRM. |
| **2026-02-16** | Event project management migration | Migrating event management to Notion for better project tracking. Transition calendar from current system to Notion being planned. |

**Status:** Early implementation. Fireflies → Notion → Zapier pipeline being built. Abdel's status (automation specialist) unclear.

**Related:** [[Fireflies — Meeting Transcription]] | [[Zapier / Automation]]

---

## Airtable

**Role:** Operational backbone for event management, POS tracking, sales performance, and contact lists. Being progressively replaced by HubSpot for contact data.
**Owner:** Various team members; Noemi Di Nunzio was primary admin (departed September 2025)

| Date | Topic | What happened |
|------|-------|--------------|
| **2026-03-23** | PR database migration | Zak had 30–40 contacts in Airtable. Plan: transfer to HubSpot as single source of truth. |
| **2026-01-26** | Contact migration to HubSpot | Zak's Airtable contact list being consolidated into HubSpot. |
| **2025-12-22** | POS supplier tracking — quality issues | POS supplier data in Airtable questionable after Noemi's departure. Invoice verification needed (cross-reference with Michele/finance). Flight board Alibaba contact found in Airtable. |
| **2025-12-15** | POS supplier sourcing | Noemi found flight board and carafe suppliers on Alibaba. Margherita struggling to contact them now. |
| **2025-11-17** | Sales performance tracker | Zak built Airtable tracker: account visits logged, performance tracked. John Pak having difficulty with data entry (UI confusion). Zak to show John offline. |
| **2025-11-10** | Airtable training | Zak trained John Pak live on Airtable during the call. HubSpot vs. Airtable comparison: Airtable more detailed for operations. |
| **2025-11-03** | Access/upgrade issue | Zak's team unable to edit Airtable — being asked to upgrade. Unclear if wrong company profile or needs upgrade. Sebastian (technical manager) to resolve. |
| **2025-11-03** | Uses defined | Airtable used for: event management tables, POS requests, wins/losses reporting. |
| **2025-10-27** | Event management system post-Noemi | New systematic Airtable event table form implemented. Nes to ensure accurate event data entry. John to use for POS product requests with specific quantities/types. |
| **2025-09-29** | Weekly reporting process | Mio sending weekly Airtable form link every Friday via email reminder. Team fills in wins/losses and discussion topics for Monday meeting prep. |
| **2025-08-25** | Events Airtable folder | Margherita to create Airtable folder for events with account information fields (name, Instagram, relationship status, etc.). |
| **2025-08-18** | Event submission form — fixed | Noemi working with Airtable support to fix event submission form; also connecting with new suppliers. |
| **2025-08-04** | Event submission form — broken | Airtable event submission form not working. Submit to Noemi via email as interim. Fix target: Wednesday/Thursday. |
| **2025-07-28** | Event KPI form build | Noemi to build Airtable form for event submissions including KPIs (attendance, engagement, sales data). |
| **2025-07-21** | POS automation proposal | Noemi proposing POS inventory automation: team submits requests via form; system checks stock; auto low-stock notifications; auto-quote requests to suppliers. Working with Abdel (automation specialist). 1–2 months to implement. |
| **2025-06-30** | Texas POS inventory tab | John Pak created Texas inventory tab in Airtable POS folder with current stock levels (flight boards, tote bags, etc.). |
| **2025-06-30** | Event-to-content automation | Lauranne working on automation to link event submissions to content creation tasks. Needs more time. |
| **2025-06-23** | Content-event table integration | Lauranne reorganizing Airtable to link event table with content table — auto-creates tasks when events are entered. |
| **2025-06-23** | Confirmed as company standard | Airtable confirmed as the centralized company tool for all data and operations at this point (later supplemented by HubSpot for CRM). |

**Issues history:**
- Form broken (Aug 4, 2025) → fixed (Aug 18, 2025) → upgrade issue (Nov 3, 2025)
- Data quality degraded after Noemi's departure (September 2025)
- Invoice data may be incorrect — verify with Michele (finance)

**Related:** [[HubSpot CRM]] | [[Open Items — Airtable Upgrade]] | [[POS Strategy]]

---

## Zapier / Automation

**Role:** Planned automation layer connecting Fireflies → Notion for task management.
**Owner:** Zak Gross (setup); Abdel (automation specialist — status unclear)

| Date | Topic | What happened |
|------|-------|--------------|
| **2026-03-23** | Fireflies → Notion automation | Zak asked about using Zapier to automate Fireflies action items into Notion tasks. Abdel's status for this project uncertain — Giancarlo doesn't know if Abdel is still working with Heavensake. |
| **2025-07-21** | POS inventory automation (earlier proposal) | Noemi proposed POS automation via Airtable + automation specialist Abdel. Quote requested; 1–2 months to implement. |

**Blockers:** Abdel's availability and working relationship with Heavensake is unconfirmed as of March 23, 2026.

**Related:** [[Fireflies — Meeting Transcription]] | [[Notion]] | [[Open Items — Abdel Status]]

---

## ChatGPT & AI Tools

**Role:** Marketing strategy ideation, content creation, weekly reporting, and meeting preparation.
**Owners:** All team members encouraged to use; Giancarlo / Team Digital for structured outputs

| Date | Tool | What happened |
|------|------|--------------|
| **2026-03-02** | Perplexity AI (Computer) | Carl: *"I spent the weekend playing around with Perplexity Computer. It is an absolute insanity."* Using for brand strategy, content creation, digital marketing. Carl: *"For the first time today I can tell you I have done it myself."* Sees as transforming outreach, content, brand strategy, testing. |
| **2026-03-16** | Perplexity AI | Carl using Perplexity to research brand ambassador candidates. |
| **2026-01-26** | ChatGPT — market analysis | Zak used ChatGPT to amalgamate team questionnaire responses into strategic document. Carl encourages all team to use ChatGPT for weekly 5–10 min market situation reflection to feed aggregated analysis. |
| **2026-01-05** | ChatGPT — marketing ideation | Zak used ChatGPT to develop Miami strategy deck (Magnum ritual protocols, influencer strategy, brand language). Carl: *"Ask your ChatGPT if you give me 10 marketing ideas for Heaven Sake in my state."* |
| **2025-12-01** | AI for content creation | Carl proposed using AI to transform restaurant photos into content. AI makes copywriting for event pages "probably okay quality." Being used to help restaurants market themselves. |
| **2025-09-15** | ChatGPT for transcription | ChatGPT noted as better than Fireflies for deciphering non-English (Japanese) content in recordings. |
| **2025-06-23** | Weekly reporting system | All team members to record voice notes, transcribe via ChatGPT, submit by Monday morning (ideal: Friday afternoon). Outputs stored in Google Docs → Airtable. AI to identify patterns across team reports. |

**Carl's vision:** AI infrastructure to enable consumer-pull demand at scale — *"Push a button and have hundreds of thousands of people [hyped about] Heaven Sake."*

**Related:** [[Whisper Flow]] | [[Digital Strategy — Giancarlo]] | [[Weekly Reporting System]]

---

## Whisper Flow

**Role:** Voice-to-email dictation app for faster communication. Runs on Mac via function key.

| Date | Topic | What happened |
|------|-------|--------------|
| **2026-03-23** | Tool introduction | Carl and Zak both using Whisper Flow. Press function key on Mac and speak; converts to email text. Zak: *"Banging out 10–20 emails every five minutes."* Not like ChatGPT — doesn't polish emails but can combine with Gmail AI or ChatGPT for polish. Zak: *"Not mandatory but kind of should be."* Carl: *"Would probably make it mandatory."* |

**Status:** Strongly recommended; may become mandatory. Differs from ChatGPT: it transcribes and converts speech to email text without polishing.

---

## ClickUp

**Role:** Project management for website and content projects.
**Owner:** Team Digital

| Date | Topic | What happened |
|------|-------|--------------|
| **2025-09-29** | Project management implementation | Digital team: *"We are doing a proper ClickUp to follow everything, every timelines."* Mentioned as coordination tool for website and content projects. |

**Status:** Mentioned once; unclear if still active. Later discussions focus on Notion for knowledge management.

---

## Other Tools

### Canva
| Date | Topic | What happened |
|------|-------|--------------|
| **2025-07-21** | Templates | Templates for event flyers already uploaded to Canva. Main issue: photo curation and rights management. |

### TikTok
| Date | Topic | What happened |
|------|-------|--------------|
| **2025-07-21** | Content differentiation | TikTok test: posted Oto Omakase reel and Sara (stoic Sara) reel. **Results opposite to Instagram:** Sara/trending content outperformed on TikTok; Oto Omakase (high-end) outperformed on Instagram. Validates need for platform-specific content strategies. |

### LinkedIn
| Date | Topic | What happened |
|------|-------|--------------|
| **2025-08-18** | Neglected channel | Lauranne reminded team not to forget LinkedIn for B2B connections with suppliers and industry contacts. |
| **2025-09-22** | IWC award post | Carl instructed Margherita to post immediately on LinkedIn about Shichi Ken's IWC award win. |

### Google Drive
| Date | Topic | What happened |
|------|-------|--------------|
| **2026-02-16** | Marketing assets centralization | Centralizing all digital marketing assets into one G Drive folder — "Event in a Box" folder structure. Dark and light format templates for feature menus and pairings. Editable assets for quick turnaround. Caesar leading organization. |
| **2025-12-08** | Distributor/commercial folder | Shared Google Drive maintained for distributor and commercial materials. Mio has access. Margherita sharing cocktail list via this drive. |

### Tock (Restaurant Booking Platform)
| Date | Topic | What happened |
|------|-------|--------------|
| **2025-11-24** | ICA dinner quality issue | ICA dinner booked through Tock. Carl: Tock page copywriting was "three star" and images "two star" — inadequate for a $600 dinner. Heavensake redesigned the event presentation. |

### Alibaba (Supplier Sourcing)
| Date | Topic | What happened |
|------|-------|--------------|
| **2025-12-15** | POS supplier sourcing | Noemi found flight board and carafe suppliers on Alibaba. Margherita struggling to contact them post-Noemi departure. |
| **2025-12-22** | Supplier unresponsive | Multiple Alibaba suppliers unresponsive. Carl: need multiple quotes from alternative suppliers for cost/timing comparison. |

### SEO Tools
| Date | Topic | What happened |
|------|-------|--------------|
| **2025-12-01** | Turkish digital team | Two Turkish tech-savvy women supporting ongoing SEO optimization and blog content for US website. Weekly blog articles for SEO and ChatGPT/AI visibility. |

### Analytics & Website Traffic Monitoring
| Date | Topic | What happened |
|------|-------|--------------|
| **2025-09-15** | Nobody assigned after Lauren | Carl frustrated: nobody tracking website traffic, cart behavior, add-to-cart data. Previously Lauren's responsibility. Carl: *"We need to measure the statistics immediately."* Needed: how many adding to cart, traffic since new website launch. Currently unassigned. |

**Status:** UNRESOLVED — see [[Open Items — Website Analytics Owner]]

### NFC Authentication (Anti-Tampering)
| Date | Topic | What happened |
|------|-------|--------------|
| **2025-11-03** | Prestige bottle authentication | Following transit damage incident, NFC (Near Field Communication) authentication tags explored — similar to Moncler jacket authentication. Larger sticker seal implemented as interim measure. |

### Honey Badger (Communication Platform)
| Date | Topic | What happened |
|------|-------|--------------|
| **2025-06-30** | Communication failure | Grace sent scope of work via Honey Badger app; Zak didn't receive it. Told to use regular email. Not a Heavensake tool; should not be used for company communications. |

### Instagram — Orphaned Account Issue
| Date | Topic | What happened |
|------|-------|--------------|
| **2025-09-01** | "EventSake US" account | Margherita discovered Instagram profile "EventSake US" that nobody on team created or has login access for. Working to identify original email and close it. Carl: *"If you cannot find which one was the recovery address, we need to manage this together."* |

**Status:** Ongoing — Margherita and Carl handling. Unknown if resolved.

---

## Tool Stack Summary

| Tool | Primary Use | Owner | Status |
|------|-------------|-------|--------|
| **HubSpot** | CRM, PR database, automated outreach, VIP segmentation | Giancarlo | Active — being built out |
| **Shopify** | E-commerce (US website) | Team Digital / ATOJ | Live with ongoing fixes |
| **Fireflies** | Meeting transcription | All (Fred@fireflies participates) | Company standard |
| **Notion** | Knowledge management, action items from meetings | Zak | Being set up (Fireflies integration) |
| **Airtable** | Events, POS, sales performance tracking | Multiple | Active but degraded post-Noemi |
| **Zapier** | Automation (Fireflies → Notion) | Abdel (status unknown) | Planned |
| **ChatGPT** | Content, strategy, weekly reporting | All team | Active, encouraged |
| **Perplexity** | Research (ambassador research, brand strategy) | Carl, team | Carl using actively |
| **Whisper Flow** | Voice-to-email dictation | Carl, Zak (+ team) | Strongly recommended |
| **Instagram/Meta** | Organic content, paid ads | Team Digital | Active |
| **TikTok** | Platform-specific content | Team Digital | Testing |
| **LinkedIn** | B2B, industry credibility | All | Underused — flagged |
| **Google Drive** | Asset sharing, templates | All | Active |
| **Canva** | Event flyer templates | Marketing team | Templates uploaded |
| **ClickUp** | Project management (website/content) | Team Digital | Uncertain current use |
| **Alibaba** | POS supplier sourcing | Margherita | Problematic — suppliers unresponsive |
| **Tock** | Restaurant event booking | External accounts | Used for ICA dinner |

---

## Tags

`#tech` `#hubspot` `#shopify` `#website` `#airtable` `#fireflies` `#notion` `#chatgpt` `#automation` `#zapier` `#instagram` `#meta-ads` `#crm` `#e-commerce`

**Related notes:**
- [[Product Decisions from Marketing Meetings]]
- [[Financial Notes from Marketing Meetings]]
- [[Open Items from Marketing Meetings]]
- [[Monday Marketing Meetings Index]]
