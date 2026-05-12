# Repro Construction — Website Strategy Briefing

**Client:** Repro Construction LLC (reproconstruction.com)
**Principal:** Mark Geisler
**Date:** May 12, 2026
**Prepared for:** Repro Cowork session handoff
**Status:** Discovery / strategy phase — no build work started

---

## Who Mark is and what Repro does

Mark Geisler owns Repro Construction, a New England construction management firm. Mike (Fructify) knows him personally. The company's actual bread-and-butter is **QSR retrofits and remodels** — Dunkin' Donuts, drive-through quick-service restaurants, fast food refreshes. That's the core competency.

Mark is unhappy with his current site and wants a new one. Mike's instinct is that the entire website paradigm has shifted with AI — less scrolling and clicking through nav menus, more of a landing page that *asks* the visitor what they want, and an awareness that SEO has been displaced by AI search results (ChatGPT, Perplexity, Claude, Google AI Overviews).

This briefing is the discovery output. Before any design or build, the strategic foundation needs to be locked in.

---

## Problem #1: The current site's real issue isn't the design — it's the positioning

The current reproconstruction.com positions Repro as a generic New England GC: *"full service construction management firm that specializes in new construction, multi-unit residential, commercial tenant improvements and restaurants."*

That's a kitchen-sink pitch. Residential + commercial + restaurants in one sentence reads as "we'll take whatever work shows up."

**Meanwhile the competitive set leads hard with QSR specialization plus named brand credibility:**

- **The Beam Team** (Alpharetta, GA): "The General Contractor of choice for legendary brands" — leads with McDonald's, Domino's, KFC.
- **Apex Construction** (Nevada): "In 2024 we finished our 185th project building for McDonald's. With over 150 eateries built or remodeled in recent years…"
- **Asa Carlton, Inc.**: "two decades of expertise in quick service restaurant (QSR) construction projects… brands such as Chick-fil-A, Taco Bell, and Burger King."
- **QSR Team**: brand name is literally the category.

Every serious competitor anchors on QSR specialty + named-brand experience + project count. Repro's site does none of those things.

**Implication:** Even a perfectly executed AI-native website on top of generic "New England general contractor" positioning will underperform. The positioning fix has to come first. This is the Ferrari-interior-in-a-Civic problem.

**Open question for Mark:** which brands has Repro actually worked with (Dunkin' definitely — what else?), how many projects, what's the geographic footprint, what's the typical timeline / scope range? This becomes the heart of the new site.

---

## Problem #2: The website paradigm really has shifted — Mike's instinct is correct, with one wrinkle

Quick research synthesis of where things actually stand in May 2026:

### The tab and the nav menu are dying

- AI browsers (ChatGPT Search, Perplexity, Comet, Atlas) are compressing the traditional "open 8 tabs and compare" behavior into a single conversational layer. Research sessions are getting **40–70% shorter**.
- Users are starting to bookmark *prompts* instead of websites.
- The "comparison phase" — where websites historically captured B2B attention — is being eliminated. AI synthesizes the comparison and just delivers the answer.

### SEO and GEO are now two different games

- **GEO (Generative Engine Optimization)** is the new discipline. A page can rank #1 in Google and never get cited by ChatGPT if it lacks the structural elements AI engines prioritize.
- **AI-referred traffic jumped 527% YoY** in the first five months of 2025 (Previsible 2025 AI Traffic Report).
- The overlap between top Google links and AI-cited sources has dropped from **~70% to below 20%** (Brandlight research).
- GEO traffic converts **~4.4x better** than traditional search traffic (Semrush) — but it's lower volume and "zero-click" by default. Quality over quantity.

### What gets cited by AI engines

- **Concrete facts over marketing copy.** "Apex completed 185 McDonald's projects" gets cited. "Industry-leading quality" doesn't.
- **Structured data and schema markup.** Machine-readable formats are the new Rosetta Stone.
- **Cross-platform consistency.** AI triangulates facts — if your project count is different on your site, LinkedIn, and Google Business Profile, the AI omits it entirely to avoid hallucinating.
- **Freshness.** ~50% of content cited in AI answers is less than 13 weeks old. Stale sites get displaced fast.
- **Crawlable HTML.** No JavaScript-gated content. SSR or pre-rendered. Allow GPTBot, ClaudeBot, PerplexityBot, OAI-SearchBot in robots.txt.

### The wrinkle on "make the whole site a chatbot"

Conversation design experts are calling pure chatbot-as-homepage the **"hybrid hell phase"** — companies retrofitting conversational AI onto click-based architectures, ending up with two mediocre experiences. The actual 2026 best practice from leading design publications:

> Guided flows that let users ask for what they want, filter faster, compare options, and move forward without digging through menus. This trend isn't about replacing navigation; it's about reducing friction.

> AI assistants now guide users towards the content they're searching for as a natural part of the browsing experience… embedded in a website's navigation and built to proactively guide users through complex multi-step tasks.

So: **AI-native, but not chatbot-only.** A focused conversational concierge that does qualification and routing, layered over a clean, fast, GEO-optimized content base.

---

## Strategic recommendation: 3-layer stack, built in order

### Layer 1 — Positioning fix (must come first)

Re-anchor Repro as **"QSR refresh & remodel specialists, New England."** Name the brands Mark has worked with (Dunkin', any others). Lead with project counts, geographic footprint, and timeline-driven case studies.

Drop or de-emphasize the residential/multi-unit messaging unless it's a real second revenue stream Mark wants to grow. If it's just "we'd take it if it came in," it dilutes the positioning and hurts AI discoverability — generic GCs don't get cited by AI for "who does Dunkin' refreshes in MA."

### Layer 2 — GEO-first content architecture

Site is built to be cited by ChatGPT, Claude, Perplexity, and Google AI Overviews. Concretely:

- **Structured project case studies**, each with brand name, location, scope, square footage, timeline, before/after if available.
- **Schema markup** (LocalBusiness, ConstructionBusiness, Service, FAQPage) on every relevant page.
- **Fast SSR HTML**, no JavaScript-gated content, fast Core Web Vitals.
- **robots.txt allowing AI crawlers** (GPTBot, ClaudeBot, OAI-SearchBot, PerplexityBot).
- **Consistent NAP data** across site, Google Business Profile, LinkedIn, industry directories.
- **Fact-dense answers** to the questions QSR buyers actually ask: "Can you do an after-hours Dunkin' refresh in 30 days?" "What's your geographic coverage in New England?" "Do you handle franchisor brand compliance?"
- **Freshness cadence**: project pages and stats updated quarterly minimum.
- **An `/llms.txt` file** at the root pointing AI agents to the most important canonical pages.

### Layer 3 — Conversational concierge (the AI-native UX)

A focused intake/qualification layer on top of the content. **Not "ask me anything"** — that's the hybrid hell trap. Instead, a guided concierge that captures the four things every Repro project starts with:

1. **Brand** (Dunkin', Chick-fil-A, etc., or independent)
2. **Location** (state/city — drives feasibility)
3. **Scope** (refresh, full remodel, ground-up, drive-through retrofit)
4. **Timeline** (when does it need to be operational)

It then either books a call directly into Mark's calendar or hands off a fully qualified lead with all context attached. That's the actual economic value of AI on this site — it shortens the gap between "interested visitor" and "Mark on the phone with a qualified prospect."

This is also where MCP connectors come in: Google Calendar for booking, Gmail or Slack for hand-off notifications, optionally Smartsheet for lead tracking if Mark uses one.

**Build order matters: 1 → 2 → 3.** Skip ahead and we're building infrastructure on a flawed foundation.

---

## Open questions to close out with Mark before any build

1. **Brand list:** which QSR brands has Repro actually completed projects for? Need this for the positioning anchor and the case study library.
2. **Project counts and footprint:** total projects, by brand, by state. Even rough numbers.
3. **Residential / multi-unit revenue:** keep, drop, or secondary mention?
4. **Sales process today:** how do leads come in now? What does the current "interested → on the phone with Mark" funnel look like? Where does it leak?
5. **Brand assets:** logo, colors, photography (especially before/after job photos)?
6. **Tech today:** what's the current site built on? Hosting? Any CRM or lead tracking?
7. **Budget and timeline expectations** for the new site build.

---

## Suggested next steps for this Cowork session

1. **Schedule a discovery call with Mark** (or draft the questionnaire if Mike wants to do it async first) to close out the open questions above.
2. **Once positioning data is in hand**, draft a Repro Brand Guide and Client Persona doc (same approach used for Haibon Builders).
3. **Then move into site spec**: information architecture, content inventory, GEO content plan, concierge conversation flow.
4. **Then build**, likely Claude Code on Hostinger pattern Fructify has used before, with the conversational concierge as a Claude-powered widget.

This is structured as a Fructify v2 Cowork kit — `repro` as the client layer, leveraging the standard platform layer (skills, commands, agents). The kit-assessment skill is the right starting point if Mike wants to generate a value-add document for Mark before the discovery call.

---

## Research sources (for reference)

- "Death of the Browser Tab" — Digit, May 2026
- Conversational AI Trends 2026 — Tblocks, Master of Code
- GEO Guide 2026 — LLMrefs, Jasper, Frase.io, Media Shark, Surmado
- Web Design Trends 2026 — BBDirector, UIUX Showcase, Black Pug Studio (Medium)
- Conversation Design Predictions 2026 — Conversation Design Institute
- Competitive analysis: Beam Team, Apex Construction, Asa Carlton, QSR Team
