# Repro Construction Website — Architectural Direction

**Date:** May 12, 2026
**Source:** Synthesis of competitive analysis, SEO audit, brand discovery, and current (2025–2026) AI-first website research.

---

## The decision

**Build a concierge homepage on top of a deep SEO library — not a chat overlay on a traditional scrolling site.**

This is the architecture: a single-viewport, no-scroll-required surface at `reproconstruction.com` that asks the visitor what they're here for and routes them, sitting on top of a clean-URL library of sector, city, and project pages underneath. The router is the storefront; the library is the warehouse.

The reason this is the right call for Repro specifically:
- Mark explicitly does not want endless scrolling.
- Mark's buyers (QSR franchisees, multi-unit developers, retail rollout managers) are mobile-heavy and decision-fast — they will not fill out long forms but will tap "I'm opening a new QSR location" on a phone.
- The SEO audit says Repro needs deep indexable content (branded vertical pages, city pages, project case studies) to win Google AI Overviews and long-tail buyer-intent queries.
- The competitive analysis says nobody in Greater Boston is doing this — every competitor is a conventional scroll-down WordPress site.

A pure single-screen site gives Google nothing to crawl. A traditional scrolling site gives Mark's buyers everything they hate. The two-layer architecture is the only way to satisfy both constraints.

---

## What the top layer (homepage) looks like

**One viewport. No scroll required to convert.** Above the fold, on a 1440px laptop or a 390px iPhone, the visitor sees:

1. **The H1 positioning statement.** "Fast-track restaurant builders. New store open in 14 days." Bold, sans-serif, takes one line on desktop and three on mobile.
2. **A 4-tile intent router** (sentence case labels, real Tabler-style icons):
   - "I'm opening a new restaurant location"
   - "I'm remodeling an existing restaurant"
   - "I'm building or rolling out multi-unit"
   - "I'm doing a residential or custom build"
   Each tile routes to a dedicated sector landing page underneath.
3. **A persistent "Tell us about your project" button** that opens a 5-step inline wizard (project type → market/city → target open date → square footage → name + contact). No more than one input per step. Completable in under 90 seconds on a phone.
4. **A trust rail** — three signals visible without scrolling: client logo wall (Dunkin', Jersey Mike's, Dave's Hot Chicken, Wayback, Smith & Wollensky), "30+ years," and one short pull quote from a named operator (when Mark provides one).
5. **Phone number and "Talk to Mark" button** always visible — this is the named-owner advantage the competitive set doesn't have.
6. **A 20-second muted auto-loop reel** — time-lapse of a recent project or before/after of the Danvers Dunkin' 14-day. Background-video style, not a hero illustration.

Everything else is below the fold and is *optional* — the visitor only sees it if they choose to look. The page validates Mark's "everything's gotta be right there" requirement: a buyer can call, wizard, or route in under 5 seconds without scrolling.

---

## What the deep layer (everything underneath) looks like

Clean URL structure, schema-rich, AI-search-engineered. Every router tile and every secondary nav item leads here.

**Sector pages (4 — one per router tile):**
- `/restaurant-construction/` — flagship QSR vertical
- `/multi-unit/` — multi-unit residential / mixed-use
- `/tenant-fit-out/` — retail and commercial TI
- `/residential/` — kitchens, baths, additions, custom

**Branded landing pages (5 to start, more as the portfolio grows):**
- `/clients/dunkin/`
- `/clients/jersey-mikes/`
- `/clients/daves-hot-chicken/`
- `/clients/wayback-burgers/`
- `/clients/family-dollar/`

These are the SEO winners — long-tail branded queries Repro can rank for fast because almost nobody is competing.

**City / service-area pages (6 to start):**
- `/locations/peabody-ma/`
- `/locations/danvers-ma/`
- `/locations/salem-ma/`
- `/locations/beverly-ma/`
- `/locations/boston-ma/`
- `/locations/north-shore-ma/`

**Per-project case studies (3 deep at launch, then expand):**
- `/projects/dunkin-danvers-14-day/`
- `/projects/nahant-st-revere-38-unit/`
- `/projects/[chef-driven-restaurant]/`

Each project page: hero image, 4 metrics (sq ft, timeline, vertical, client), 3 paragraph narrative, 6–12 photo gallery, one client quote (when available), "Related projects" rail.

**Supporting pages:**
- `/about/` — team bios with Mark front and center
- `/process/` — how Repro works (design-build vs CM vs GC, the 14-day playbook)
- `/careers/` — keep existing job/subcontractor application surface
- `/contact/` — full contact form + map + office hours

**Hidden but accessible:**
- The wizard funnel itself (`/start-project/`) for direct linking from ads
- A sitemap and FAQ pages with schema markup feeding AI Overviews

---

## How the wizard works (concise)

The wizard replaces a traditional contact form. Five screens, one question each, no progress bar (we don't want to imply effort). Each screen is one large input.

| Step | Question | Input type |
|---|---|---|
| 1 | What kind of project are you starting? | 4 large tiles (same as router) |
| 2 | Where? | City field with autocomplete (MA, NH, RI, ME, VT, CT, FL) |
| 3 | When does it need to be open? | Date picker — Mark can route fast-track tagged inquiries to himself |
| 4 | How big? | Slider: < 2,000 sq ft / 2–5k / 5–10k / 10k+ |
| 5 | Who should we call? | Name + phone + email + optional context |

Completed submissions route to Mark's email and a Smartsheet pipeline (consistent with how Mike runs other client engagements). Auto-reply confirmation goes out in <60 seconds.

---

## Tech stack recommendation

- **Framework:** Next.js (React) or Astro for static-first speed + server-rendered SEO. Both ship clean URLs, schema, and SSR/SSG out of the box. Avoid WordPress — the current site is the cautionary tale.
- **Hosting:** Vercel or Netlify. Free tier handles Repro-scale traffic. Both auto-deploy from GitHub on push.
- **CMS for project content:** Sanity, Contentful, or simple MDX files in the repo. Mark won't be hand-editing — Mike/team will push content via the repo.
- **Forms / wizard backend:** Formspree, Resend, or a thin serverless function. Pipe to Mark's email + Smartsheet.
- **Analytics:** Plausible (privacy-first, simple) or GA4 if Mark wants Google Ads integration later.
- **Imagery:** WebP/AVIF, lazy-loaded, responsive `srcset`. Optimize before commit.
- **Schema markup:** LocalBusiness sitewide, Service on sector pages, Project on case studies, FAQ on sector pages, Review on testimonials.

---

## Why this beats the current state

| Dimension | Current site | This direction |
|---|---|---|
| First impression | Generic full-service GC | Owner-side fast-track restaurant builder |
| Scroll required to convert | 3+ screens | Zero — wizard or phone above the fold |
| Mobile experience | Cramped Divi cards | Single-input-per-screen wizard |
| URL structure | `?page_id=1865` | `/projects/dunkin-danvers-14-day/` |
| Indexable by Google AI Overviews | No (no schema) | Yes (full schema layer) |
| Per-brand landing pages | None | One per major QSR client |
| Per-city landing pages | None | Six |
| Trust signals visible without scrolling | Some logos | Logos + tenure + testimonial + phone |
| Time-to-quote for visitor | Open contact form, type, submit, wait | 90-second wizard or one tap to phone |

---

## What this means for sequencing

1. **Lock the visual direction** — color, type, hero treatment. Two-day exercise. Builds on the brand discovery + positioning brief.
2. **Build the homepage prototype** — single page in HTML, no backend. Mike can show Mark in 24 hours.
3. **Confirm with Mark** — does he buy the concierge approach? If yes, scale up to the full architecture.
4. **Build sector + city + project pages** — these are the SEO investment. Bulk content can be templated.
5. **Wire the wizard + backend** — Formspree or similar, plus Smartsheet pipeline integration.
6. **Migrate from reproconstruction.com** — 301 redirect map for every `?page_id=` URL.
7. **Submit to Search Console + GBP** — measure from day one.

---

## Open questions for Mark

- Color: does Mark have a strong preference, or are we free? Suggestion: lean into deep red (matching subtle Repro brand cues) or a strong safety-yellow accent.
- Tagline: keep "Transforming a client's vision into reality" as a secondary line, or retire?
- Existing wordmark: sacred, or open to a refresh?
- Phone routing: should the wizard's fast-track-tagged inquiries route to Mark's mobile directly, or to a shared inbox?
- Smartsheet integration: which workspace owns the new project pipeline? (Mike likely already has this set up under another engagement.)

---

## Sources

- [Greiner Construction — sector-routed homepage example](https://www.greinerconstruction.com/)
- [Tuckman-Barbee — proof-first GC homepage](https://www.tuckman-barbee.com/)
- [Maman Corp — interactive scroll-light GC](https://www.mamancorp.com/)
- [v0.app — single-input command-bar paradigm](https://v0.app/)
- [Vercel — terminal hero, performance-as-visual](https://vercel.com/)
- [Heyflow — interactive wizard / landing page guide](https://heyflow.com/blog/interactive-landing-pages/)
- [Adobe Marketo Engage — conversational landing pages](https://experienceleague.adobe.com/en/docs/marketo-learn/tutorials/dynamic-chat/conversational-landing-pages)
- [21 Web Design Trends 2026 — AI-first web](https://uiuxshowcase.com/blog/21-web-design-trends-2026-design-for-humans-ai-first-web/)
- [Stackmatix — Google AI Overviews CTR impact](https://www.stackmatix.com/blog/google-ai-overview-seo-impact)
- [ALM Corp — AEO vs SEO 2026](https://almcorp.com/blog/aeo-vs-seo-2026-complete-strategy-guide/)
