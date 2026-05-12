# Repro Construction — Website Rebuild

Working folder for the rebuild of [reproconstruction.com](https://reproconstruction.com) — a New England QSR / restaurant remodel general contractor (Mark Geissler, CEO).

## Strategic deliverables

Built in this order, each informs the next:

1. **[Brand discovery report](brand-discovery-report.md)** — public-footprint sweep of Repro's existing brand voice, visual identity, and positioning signals.
2. **[Website positioning brief](website-positioning-brief.md)** — competitive analysis vs. Greater Boston QSR / restaurant GCs (Groom, Cornerstone, Cafco, Connolly, Callahan), messaging matrix, recommended positioning statement, hero copy, and content gap analysis.
3. **[Strategy briefing](repro-website-strategy-briefing.md)** — the 3-layer stack (positioning fix → GEO content architecture → qualification concierge), competitive case for QSR specialization, the GEO-vs-SEO bifurcation. Read this before the wireframe doc.
4. **[SEO audit & action plan](seo-audit.md)** — technical audit of the current Divi / WordPress build, keyword opportunity table, on-page issue list, content gap recommendations.
5. **[GEO audit supplement](geo-audit-supplement.md)** — companion to the SEO audit. Six-pillar action plan to make the new site citable by ChatGPT / Claude / Perplexity / Google AI Overviews: AI crawler allowlist, `/llms.txt`, schema layer, NAP audit, freshness cadence, fact density.
6. **[Wireframe architectural direction](wireframe-direction.md)** — the recommended site architecture: concierge homepage (intent router + wizard + trust rail) on top of a deep, schema-rich content library. Tech stack and sequencing. Strategic refinements at top supersede any conflicts below.
7. **[Assets & imagery inventory](assets-inventory.md)** — manifest of every publicly available image on reproconstruction.com (categorized by brand / project), flagship shortlist, project metadata harvested, and manual scrape targets for FB / IG / Google Business Profile / CompanyCam.

## Client-facing artifacts

- **[Discovery questionnaire (live HTML form)](discovery-questionnaire.html)** → <https://fructifyme.github.io/repro-construction-website/discovery-questionnaire.html>. Mark fills it out, hits "Send to Mike," answers land in fructifyme@gmail.com via mailto.
- **[Discovery questionnaire (Markdown twin)](discovery-questionnaire.md)** — same content as plain markdown, for the email-friendly fallback.
- **[Outreach email to Mark](outreach-email-to-mark.md)** — ready-to-send cover note with the questionnaire link.

## Locked decisions

- **Primary vertical:** QSR refresh & remodel specialists, New England. Tighter than original framing — residential / multi-unit may be sidebar-only depending on Mark's revenue-mix answer.
- **Geographic priority:** Greater Boston / North Shore MA core; all of New England + parts of Florida.
- **HQ (canonical):** 525 Lowell St, Peabody MA 01960.
- **Architecture:** 3-layer stack — positioning → GEO content → qualification concierge. Built in that order.
- **Concierge wizard captures:** Brand → Location → Scope → Timeline → contact. Then books a call or hands off a qualified lead.
- **NO chat overlay on a traditional scrolling site.** No "ask me anything" chatbot. The strategy briefing calls this the "hybrid hell" trap.
- **"RePro Home Services" Danvers Facebook page is unrelated** and excluded from all materials.

## Open items for Mark — positioning blockers

Need these before any prototype work. Captured in the discovery questionnaire:

1. Which QSR brands has Repro completed projects for? (Dunkin' confirmed — full list?)
2. Project counts by brand, by state.
3. Residential / multi-unit — keep, drop, or sidebar-only?
4. How leads come in today; where the funnel leaks.
5. Brand assets: logo, colors, style guide preference, tagline keep / retire.
6. Three named testimonials (one QSR, one multifamily, one repeat client).
7. Three flagship project packets — Danvers Dunkin' 14-day is one; what are the other two?
8. CompanyCam workspace access (likely 10×–100× larger photo library than the public site).

## Hosting / deployment

- GitHub repo: <https://github.com/FructifyMe/repro-construction-website> (public)
- GitHub Pages enabled from `main` / root
- Live form: <https://fructifyme.github.io/repro-construction-website/discovery-questionnaire.html>
- PAT for git ops stored in project-local `.env` (gitignored). Source before any push: `export $(grep -v '^#' .env | xargs)`

## Repo conventions

- `/agents/` — Claude subagent definitions scoped to this project. See [agents/README.md](agents/README.md). Copy into `.claude/agents/` after clone to activate.
- All strategy docs live at the repo root for easy diffing and review.
- Future code (the actual site build) will live under `/site/` once we move into the build phase.
