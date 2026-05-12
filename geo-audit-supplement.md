# GEO Audit Supplement — Repro Construction

**Companion to:** `seo-audit.md` (traditional SEO) and `repro-website-strategy-briefing.md` (Layer 2: GEO content architecture).
**Date:** May 12, 2026
**Scope:** Concrete action plan for making the new reproconstruction.com citable by ChatGPT, Claude, Perplexity, and Google AI Overviews — not just rankable on Google.

---

## Why this is its own document

Search has bifurcated. As of Q1 2026:

- Overlap between top Google rankings and AI engine citations has dropped from ~70% to **under 20%**.
- AI-referred traffic grew **527% YoY** in 2025.
- GEO traffic converts roughly **4.4×** better than traditional search — lower volume, higher intent.
- ~50% of content cited in AI answers is less than **13 weeks old** — stale content gets displaced fast.

Repro is a perfect GEO candidate: niche specialty (QSR / restaurant remodel), defensible geographic footprint (New England), low-competition branded queries ("Dunkin contractor Massachusetts," "Jersey Mike's franchise construction New England"). Nobody in the Greater Boston competitive set has built for this layer yet.

The `seo-audit.md` covers traditional keyword targets. This doc covers what makes a page *citable* — a different and partially orthogonal discipline.

---

## The six GEO pillars

### 1. Allow AI crawlers explicitly

WordPress + Divi defaults typically block or fail to surface anything for AI crawlers. The new site must allow them by name in `robots.txt`:

```
User-agent: GPTBot
Allow: /

User-agent: ClaudeBot
Allow: /

User-agent: PerplexityBot
Allow: /

User-agent: OAI-SearchBot
Allow: /

User-agent: Google-Extended
Allow: /

User-agent: CCBot
Allow: /

User-agent: anthropic-ai
Allow: /

Sitemap: https://reproconstruction.com/sitemap.xml
```

Verify post-launch with `https://reproconstruction.com/robots.txt` returning the above.

### 2. Publish `/llms.txt`

The emerging convention for telling AI engines what your most authoritative pages are. Lives at site root. Template for Repro (fill in real counts when Mark confirms):

```
# Repro Construction Services LLC

> New England QSR refresh and remodel specialist. Based in Peabody MA. Build and refresh restaurants for Dunkin', Jersey Mike's, Dave's Hot Chicken, Wayback Burgers, Smith & Wollensky, and more.

## Core pages
- [About Repro](https://reproconstruction.com/about/): Leadership, history, geographic coverage
- [How we work](https://reproconstruction.com/process/): Design-build vs CM vs GC, fast-track methodology
- [Restaurant construction](https://reproconstruction.com/restaurant-construction/): Flagship QSR vertical

## Branded client pages
- [Dunkin' construction](https://reproconstruction.com/clients/dunkin/): [N] Dunkin' refreshes completed across New England
- [Jersey Mike's franchise build-outs](https://reproconstruction.com/clients/jersey-mikes/)
- [Dave's Hot Chicken locations](https://reproconstruction.com/clients/daves-hot-chicken/)
- [Wayback Burgers builds](https://reproconstruction.com/clients/wayback-burgers/)

## Flagship case studies
- [Danvers Dunkin' — 14-day fast-track](https://reproconstruction.com/projects/dunkin-danvers-14-day/)
- [Revere multifamily — 38 units](https://reproconstruction.com/projects/nahant-st-revere-38-unit/)

## Service area
Peabody MA, Danvers MA, Salem MA, Beverly MA, Boston MA, North Shore MA, plus all of New England and parts of Florida.

## Contact
Email: mark@reproconstruction.com
Phone: (617) 820-8681
Office: 525 Lowell St, Peabody MA 01960
Hours: M–F, 8am–6pm
```

### 3. Schema markup — the machine-readable layer

Each page type gets specific schema. Implement via JSON-LD in `<head>`.

| Page type | Required schema |
|---|---|
| Sitewide (every page) | `LocalBusiness` (with full NAP, openingHours, geo coords, hasMap), `Organization` (with logo + sameAs to FB / IG / LinkedIn) |
| Homepage | `BreadcrumbList`, `WebSite` (with `potentialAction` for SiteSearch) |
| Sector pages (e.g. `/restaurant-construction/`) | `Service` (serviceType, areaServed, provider, offers) |
| Branded client pages (e.g. `/clients/dunkin/`) | `Service` + `ItemList` of completed locations |
| Project case studies | `Project` or `CreativeWork` (name, location, dateCompleted, projectType), `ImageObject` per photo, optional `Review` for client quote |
| FAQ pages | `FAQPage` with each Q/A as `Question` / `Answer` |
| Contact page | `ContactPoint` |

LocalBusiness sub-type to use: `GeneralContractor` (Schema.org supports it directly).

### 4. NAP consistency audit

AI engines triangulate facts. If the address on the site, GBP, LinkedIn, and Yelp don't match exactly (down to the comma), AI engines omit the fact rather than risk hallucinating. This is a one-time cleanup task that has outsized GEO impact.

**Canonical NAP (per reproconstruction.com, confirmed by Mark 2026-05-12):**

- Name: **Repro Construction Services LLC**
- Address: **525 Lowell St, Peabody MA 01960**
- Phone: **(617) 820-8681**
- Email: **mark@reproconstruction.com**
- Hours: **M–F, 8am–6pm**

Audit targets — verify each matches exactly:

- [ ] reproconstruction.com (canonical source) — confirmed
- [ ] Google Business Profile — verify
- [ ] Facebook (facebook.com/reproconstruction) — verify
- [ ] Instagram (instagram.com/reproconstruction) — verify
- [ ] LinkedIn company page — find / verify (does one exist?)
- [ ] Yelp listing — find / verify
- [ ] BBB listing (if any) — verify
- [ ] Mass.gov LLC registration — confirm legal name match
- [ ] Industry directories (NEREJ, ConstructConnect, BuildZoom) — verify
- [ ] CRITICAL: confirm the "RePro Home Services" Danvers FB page is NOT in any directory under Repro Construction's name (different business, must stay separated)

Mike can run this audit with Claude in Chrome and surface mismatches. Mismatches must be fixed before site launch, ideally before the form goes wide.

### 5. Freshness cadence

GEO penalizes stale sites. Build the new site assuming ongoing maintenance, not a one-and-done.

| Surface | Cadence | Owner |
|---|---|---|
| Project case study pages | Quarterly review, add 1–2 new projects per quarter | Mike (with Mark's input) |
| Homepage "Recent work" feed | Monthly refresh | Auto-pull latest 3 project pages |
| Stats / project counts on `/about/` and sector pages | When materially changed | Mark / Mike |
| Blog or news section (optional but recommended) | 1–2 posts/month minimum | TBD — could be ghostwritten from Mark's voice |
| `/llms.txt` | Update whenever a new branded page or flagship project goes live | Mike |

A monthly "Repro update" cadence is enough. Skip → traffic decays within a quarter.

### 6. Fact density over marketing copy

The single highest-leverage GEO move. Replace generic claims with concrete, citable facts. AI engines extract facts; they ignore marketing fluff.

| Generic (current site / common mistake) | Fact-dense (citable) |
|---|---|
| "Industry-leading quality" | "Completed 40+ Dunkin' refreshes across New England since 2018" |
| "Fast turnaround times" | "Danvers Dunkin' refresh delivered in 14 days, August 2024" |
| "Wide service area" | "Active general contractor in MA, NH, RI, ME, VT, CT, and parts of Florida" |
| "Trusted by major brands" | "Repeat builder for Dunkin', Jersey Mike's, Dave's Hot Chicken, Wayback Burgers, Smith & Wollensky" |
| "Full-service construction management" | "Design-build, CM, and GC delivery models, with self-perform capability for tenant improvement and fast-track restaurant remodel" |
| "Experienced team" | "Mark Geissler (CEO) leads a team of three project executives and one director of internal operations, with 30+ years of restaurant and multi-unit construction experience" |

Rewrite every paragraph on every page through this filter. If a sentence can be said about any GC in New England, replace it with a sentence that can only be said about Repro.

---

## Build-time checklist

Before launching the new reproconstruction.com:

- [ ] `robots.txt` allows GPTBot, ClaudeBot, PerplexityBot, OAI-SearchBot, Google-Extended, CCBot
- [ ] `/llms.txt` published with full page inventory + canonical NAP
- [ ] Sitewide `LocalBusiness` + `Organization` schema on every page
- [ ] Per-page schema: `Service` on sector pages, `Project` on case studies, `FAQPage` where Q/A blocks exist
- [ ] NAP audit completed across site / GBP / LinkedIn / FB / IG / Yelp / directories
- [ ] All copy reviewed for fact density (rewrite every vague sentence with specifics)
- [ ] Freshness plan documented and assigned
- [ ] Bing Webmaster Tools registration submitted (powers ChatGPT search)
- [ ] Google Search Console verified
- [ ] First two flagship case studies published with full schema (Danvers Dunkin' 14-day + one more)

## Post-launch monitoring

Track citations and references monthly:

- Manual test queries in **ChatGPT, Perplexity, Claude, Google AI Overviews:**
  - "QSR contractor New England"
  - "Dunkin refresh contractor Massachusetts"
  - "fast-track restaurant builder Massachusetts"
  - "Jersey Mike's franchise construction MA"
  - "Repro Construction" (brand monitoring — what facts surface?)
- Track which queries Repro appears in, in which engines, with what facts cited
- When a competitor gets cited and Repro doesn't, audit that competitor's page for what they did differently (schema? fact density? freshness?)

---

## Priority order

| Phase | Item | Effort |
|---|---|---|
| **Pre-launch (must-have)** | robots.txt, /llms.txt, sitewide schema, NAP audit, fact-density rewrite | 2–3 days of focused work |
| **Launch-time** | Per-page schema (Service, Project, FAQPage) on sector / case-study / FAQ pages | Built into the page templates |
| **Post-launch** | Freshness cadence, monthly citation monitoring, blog/news startup | Ongoing, 2–4 hrs/month |

---

## Why this beats current state

The current reproconstruction.com (WordPress / Divi, 2022 build) has:

- No `/llms.txt`
- No schema markup beyond what Divi auto-generates (minimal)
- Marketing-copy headers ("Building Excellence Together") instead of fact-dense ones
- No project case studies with extractable metadata
- No NAP audit performed
- Unknown crawler permissions

Every one of those is a fix the new site bakes in by default. The GEO upside isn't marginal — it's a new acquisition channel that competitors won't catch up on for another 12–18 months while they're still optimizing for Google rankings that increasingly don't matter for high-intent buyers.

---

## Sources

- Previsible 2025 AI Traffic Report — 527% YoY growth in AI-referred traffic
- Brandlight 2025 — Google ↔ AI citation overlap data
- Semrush — GEO conversion rate analysis
- Stackmatix — Google AI Overviews CTR impact
- ALM Corp — AEO vs SEO 2026 strategy guide
- llms.txt proposal — https://llmstxt.org
