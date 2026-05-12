# Repro Construction — Website Rebuild

Working folder for the rebuild of [reproconstruction.com](https://reproconstruction.com) — a Greater Boston QSR / restaurant remodel general contractor (Mark Geissler, CEO).

## Strategic deliverables

Built in this order, each informs the next:

1. **[Brand discovery report](brand-discovery-report.md)** — public-footprint sweep of Repro's existing brand voice, visual identity, and positioning signals. Open questions for Mark surfaced here.
2. **[Website positioning brief](website-positioning-brief.md)** — competitive analysis vs. Greater Boston QSR/restaurant GCs (Groom, Cornerstone, Cafco, Connolly, Callahan), messaging matrix, recommended positioning statement, hero copy, and content gap analysis.
3. **[SEO audit & action plan](seo-audit.md)** — technical audit of the current Divi/WordPress build, keyword opportunity table, on-page issue list, content gap recommendations, and a prioritized quick-wins / strategic-investments action plan.
4. **[Wireframe architectural direction](wireframe-direction.md)** — the recommended site architecture: concierge homepage (intent router + wizard + trust rail) on top of a deep, schema-rich SEO library (sector / city / branded-client / project case study pages). Tech stack and sequencing.

## Locked decisions

- **Primary vertical:** QSR / restaurant remodel (Dunkin', Jersey Mike's, Dave's Hot Chicken, Wayback Burgers).
- **Geographic priority:** Greater Boston / North Shore MA.
- **HQ address (canonical):** 525 Lowell St, Peabody, MA 01960.
- **Hero promise:** *Fast-track restaurant builders. New store open in 14 days.*
- **Architecture:** Concierge homepage + deep SEO library — single-viewport top layer, indexable depth underneath. Not a chat overlay on a scrolling site.
- **"RePro Home Services" Danvers Facebook page is unrelated** and excluded from all materials.

## Open items for Mark

1. Color & wordmark — preference, or open to refresh?
2. Tagline — keep *"Transforming a client's vision into reality"* or retire?
3. Three named testimonials (1 QSR, 1 multifamily, 1 residential)
4. Three case-study packets — Danvers Dunkin' 14-day, Revere 38-unit, one chef-driven QSR (photos, sq ft, timelines, scope)

## Repo conventions

- `/agents/` — Claude subagent definitions scoped to this project. See [agents/README.md](agents/README.md). Copy into `.claude/agents/` after clone to activate.
- All strategy docs live at the repo root for easy diffing and review.
- Future code (the actual site build) will live under `/site/` once we move into build phase.
