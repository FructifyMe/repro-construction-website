# Repro Construction — SEO Audit & Action Plan

**Site:** reproconstruction.com
**Audit type:** Full site (current state + recommendations for the new build)
**Date:** May 12, 2026
**Lane focus:** QSR / restaurant remodel, Greater Boston
**Note:** Without an SEO tool connected (Ahrefs, Semrush, GSC), volume and difficulty estimates are directional. For precise data, connect one of those before re-running.

---

## Executive summary

The site has a strong **content asset base** — a deep, named project library (Dunkin', Dave's Hot Chicken, Jersey Mike's, Wayback, Family Dollar, multi-unit Revere) — and consistent NAP information. **Everything else is leaving search traffic on the table.** The site is a 2022 WordPress/Divi build with default URL structure (`?page_id=XXX`), no SEO meta descriptions, no structured data, alt text that is filename garbage, and a 2022 copyright. There is no LocalBusiness schema, no FAQ schema, no Article schema — and search has shifted to favor exactly those signals for AI Overviews.

**Top three priorities, in order of impact:**

1. **Switch to clean URLs + per-project slugs** (`/projects/dunkin-donuts-danvers-ma/`). Single biggest lift available.
2. **Add LocalBusiness + Service + Article schema** on every relevant page. This is what Google AI Overviews surface.
3. **Rewrite every title tag and meta description** around buyer-intent queries ("Dunkin contractor Massachusetts," "fast-track restaurant remodel North Shore").

**Overall assessment:** **Needs significant work.** The current site is functionally invisible to anyone searching with intent. The good news: with a clean rebuild already on the table, every fix below can be baked into the new site rather than retrofitted.

---

## 1. Keyword opportunity table

Sorted by opportunity score (combination of buyer intent, relevance to Repro's strengths, and how empty the current SERP is for these terms in Greater Boston).

| Keyword | Est. difficulty | Opportunity | Current ranking | Intent | Recommended content type |
|---|---|---|---|---|---|
| Dunkin contractor Massachusetts | Moderate | **High** | Not ranking | Commercial | Branded vertical landing page + Dunkin' case studies |
| Restaurant general contractor Boston | Moderate | **High** | Not ranking | Commercial | QSR vertical landing page |
| Fast-track restaurant remodel Massachusetts | Easy | **High** | Not ranking | Commercial | Speed-focused service page + 14-day case study |
| Jersey Mike's franchise construction Massachusetts | Easy | **High** | Not ranking | Commercial | Branded case study |
| QSR construction company New England | Moderate | **High** | Not ranking | Commercial | QSR vertical hub page |
| Restaurant tenant improvement North Shore MA | Easy | **High** | Not ranking | Commercial | Service-area landing page |
| Dave's Hot Chicken contractor | Easy | High | Not ranking | Commercial | Branded case study |
| Drive-thru construction Massachusetts | Easy | High | Not ranking | Commercial | Service page (drive-thru add/build) |
| Multi-unit apartment builder Greater Boston | Hard | Medium | Not ranking | Commercial | Multi-unit landing page + Revere case study |
| Commercial remodel contractor Peabody MA | Easy | Medium | Not ranking | Commercial | Service-area landing page |
| Construction management Peabody MA | Easy | Medium | Not ranking | Commercial | Service page |
| Design-build contractor New England | Hard | Medium | Not ranking | Commercial | Design-build service page |
| Retail tenant improvement Boston | Moderate | Medium | Not ranking | Commercial | Retail vertical landing page |
| How long does a restaurant remodel take | Easy | Medium | Not ranking | Informational | Blog / FAQ schema |
| What does a QSR contractor do | Easy | Medium | Not ranking | Informational | Blog / FAQ schema |
| Cost to build a Dunkin franchise | Easy | Medium | Not ranking | Informational | Blog (high franchisee intent) |
| Restaurant builder near me | Hard | Medium | Not ranking | Commercial | LocalBusiness schema + location pages |
| Restaurant renovation Salem MA | Easy | Medium | Not ranking | Commercial | Service-area landing page |
| Restaurant renovation Beverly MA | Easy | Medium | Not ranking | Commercial | Service-area landing page |
| Restaurant renovation Danvers MA | Easy | Medium | Not ranking | Commercial | Service-area landing page |
| Multifamily general contractor Massachusetts | Hard | Medium | Not ranking | Commercial | Multi-unit landing page |
| Kitchen and bath remodel North Shore MA | Hard | Low | Not ranking | Commercial | Residential landing page |
| Custom home builder New England | Hard | Low | Not ranking | Commercial | Residential landing page |
| 14-day restaurant remodel | Easy | Low (low volume but trophy keyword) | Not ranking | Commercial | Case study + earned-media play |
| Repro Construction | Easy | High (brand) | Likely #1 already | Navigational | Home page, polished |

**Read on this:** Repro's biggest, most defensible wins live in the *branded QSR* lane — "Dunkin contractor Massachusetts," "Jersey Mike's construction," "Dave's Hot Chicken contractor." Repro already builds these. Almost nobody is competing on these long-tail branded searches. A dedicated landing page per brand (with the actual project gallery and a process narrative) will rank fast and convert at the highest rate.

---

## 2. On-page issues

| Page | Issue | Severity | Recommended fix |
|---|---|---|---|
| All pages | URLs use `?page_id=XXX` query parameters | **Critical** | Configure WordPress permalinks to `/post-name/` structure. Migrate with 301 redirects. |
| Project pages | URLs leak Divi builder params (`&et_fb=1&PageSpeed=off`) | **Critical** | Strip query strings from project links. Set canonical URLs. |
| All pages | No meta descriptions present in `<head>` | **Critical** | Install Yoast/RankMath. Write a unique 150–160 char meta description per page. |
| All pages | No structured data of any kind (no LocalBusiness, no Organization, no Article) | **Critical** | Add LocalBusiness schema sitewide, Article schema on case studies, FAQ on service pages. |
| Home page | Title tag is "Repro Construction \| General Construction Services" — generic | High | Rewrite: "Repro Construction — Restaurant & QSR Builders in New England" |
| Home page | No clear H1 — uses H2 "Our Services" at top | High | Add one H1: "Fast-track restaurant builders. New store open in 14 days." |
| All pages | Image alt text is filename garbage (`dunks10`, `aHR0cHM6...`, `20230618_113254`) | High | Rewrite every alt to describe the image with the brand and location ("Completed Dunkin' Donuts interior, Danvers MA — 14-day remodel"). |
| Projects | Project pages have no descriptive titles ("Recent Projects" page is one big tile board with `?page_id=` links) | High | Each project should be its own page with a slug like `/projects/dunkin-donuts-danvers/` and a proper title tag. |
| About | Typo "knowklage" appears in body copy | High | Fix typo. Re-run a copy editor pass on every page. |
| About | Title tag is "About Us \| Repro Construction" — generic | Medium | "About Repro Construction — 30+ Years Building Restaurants & Multi-Unit in New England" |
| Contact | Office hours mismatch (8–6 on Contact, 8–5 on Galleries footer) | Medium | Lock to 8am–6pm sitewide. |
| Footer | Copyright "2022" | Medium | Auto-render current year. |
| Home | Facebook feed throws visible OAuth token error to users | Medium | Remove the broken Facebook feed or reauthorize the token. Don't surface error text to users. |
| All pages | `meta-viewport` uses `user-scalable=0` — accessibility violation | Medium | Remove `user-scalable=0` and `maximum-scale=1.0`. Let users pinch-zoom. |
| All pages | No internal linking between project pages (orphan-style) | Medium | Each project page links to "Related projects" — same brand or same vertical. |
| All pages | No breadcrumb navigation | Medium | Add breadcrumb component + BreadcrumbList schema. |
| All pages | Open Graph and Twitter Card meta missing | Medium | Add og:title / og:description / og:image / twitter:card on every page. |
| Home | "Some Recent Projects" — vague H2 | Low | "Recent restaurant & multi-unit projects" |
| Home | Client logos have no alt text describing the client name | Low | "Dunkin' Donuts logo — Repro client" etc. |
| All pages | Image files served as full-size .jpg/.jpeg (e.g., `-scaled.jpg`) instead of WebP/AVIF | Low | Convert images to WebP/AVIF, serve responsive `srcset`. Speeds page load and Core Web Vitals. |

---

## 3. Content gap recommendations

What competitors have that Repro doesn't — ranked by ROI.

| Topic / asset | Why it matters | Format | Priority | Effort |
|---|---|---|---|---|
| Branded landing pages: Dunkin', Jersey Mike's, Wayback, Dave's Hot Chicken, Family Dollar | Groom owns `/dunkin-donuts` URL — Repro can own the same for every brand they build. Highest-intent commercial query type. | Vertical landing page per brand | **High** | Moderate (half day each) |
| Service-area landing pages: Peabody, Danvers, Salem, Beverly, Boston, North Shore | "Restaurant builder near me" + "[city] commercial remodel" queries. Local intent is huge in this market. | One page per city, with local-relevant projects | **High** | Moderate |
| Speed/fast-track service page | Repro's most differentiated promise has no dedicated page. Currently buried as a banner. | Dedicated service page with the 14-day timeline as the centerpiece | **High** | Quick win |
| Testimonials surface | Cafco has 6+ named-operator quotes on home. Repro has zero. | Testimonial section + standalone page with `Review` schema | **High** | Depends on Mark gathering quotes |
| Case studies with structured data | Repro has the photos and the projects but they're stored as image galleries, not narratives | Per-project page: timeline, sq ft, vertical, photos, scope, client quote | **High** | Moderate per case study |
| FAQ pages with schema | Direct fuel for Google AI Overviews + "People Also Ask" | One FAQ section per vertical landing page | **High** | Quick win |
| Process explainer | Buyers want to know how design-build vs. CM vs. GC differs. Nobody in the competitive set explains this well. | Pillar article: "How to choose a contractor for your restaurant build" | Medium | Substantial |
| Blog cadence | Even monthly. Industry insights + project recaps. Signals freshness to Google. | Monthly blog post | Medium | Ongoing |
| Drive-thru build expertise page | QSR drive-thru is a specialty within QSR that Cornerstone explicitly mentions. Easy gap to claim. | Service sub-page | Medium | Quick win |
| Permitting / lease-to-open timeline guide | High-intent for franchisees ("how long from lease signing to opening day") | Pillar guide | Medium | Substantial |
| Subcontractor recruiting content | Existing application page is bare. Bigger trade-recruiting content surface helps with talent + indirect SEO. | Career hub | Low | Moderate |

---

## 4. Technical SEO checklist

| Check | Status | Details |
|---|---|---|
| HTTPS | **Pass** | Site is on HTTPS, no mixed content observed. |
| Mobile viewport configured | **Warning** | `user-scalable=0` violates accessibility; remove. |
| Clean URL structure | **Fail** | All pages use `?page_id=XXX`. Critical for new build. |
| Canonical tags | Warning | Canonicals point to query-string URLs. Once permalinks change, canonicals must follow. |
| XML sitemap | Unknown | Could not retrieve sitemap.xml. Likely absent. Add via Yoast/RankMath. |
| robots.txt | Unknown | Could not retrieve. Verify present and not blocking key paths. |
| Meta descriptions | **Fail** | None present on any audited page. |
| Title tags unique per page | Warning | Present, but generic and not keyword-optimized. |
| H1 unique per page | Warning | Some pages have no clear H1 (home), others have weak ones ("Galleries"). |
| Structured data | **Fail** | Zero schema. Highest-impact AI-search miss. |
| Open Graph / Twitter | **Fail** | Missing. Social shares will render blank previews. |
| Internal linking | Warning | Project pages don't cross-link. No related-content pattern. |
| Broken links | Warning | Facebook feed integration throws visible error. The `et_fb=1` builder URLs being indexed risks duplicate content. |
| Image optimization | Warning | Large .jpg files served at full size. Convert to WebP, add responsive `srcset`. |
| Image alt text | **Fail** | Filenames as alts. Rewrite every alt. |
| Core Web Vitals (LCP, CLS, INP) | Warning | Divi sites + unoptimized images typically run LCP > 2.5s on mobile. Test with PageSpeed Insights post-rebuild. |
| Indexation hygiene | Warning | Divi `?et_fb=1` URLs may be indexed. Add disallow rules + cleanup. |
| Local schema (LocalBusiness) | **Fail** | Not present. Critical for local search in QSR/restaurant. |
| FAQ schema | **Fail** | Not present. |
| Article / NewsArticle schema | **Fail** | Not present on project pages. |
| Hreflang | N/A | Single-language site. |
| Site speed (preliminary) | Warning | Divi 4.24.3 + unoptimized assets. Benchmark after rebuild. |
| Google Business Profile | Unknown | Verify claimed, with photos, services, and hours matching the site. (Not visible in this audit — worth checking directly.) |

---

## 5. Competitor comparison

| Dimension | Repro | Groom | Cornerstone D/B | Cafco | Connolly |
|---|---|---|---|---|---|
| Clean URL structure | No (`?page_id=`) | Yes (`/dunkin-donuts`) | Yes | Yes (`/portfolio/[name]`) | Yes |
| Per-project case study pages | Thin / inconsistent | Yes | Yes | Yes (deep) | Yes |
| Named-brand vertical pages | No | **Yes** | Yes (named brand list) | No (different vertical) | No |
| Testimonials with names | No | Some | Some | **Yes (multiple, named)** | Yes |
| Structured data (visible) | None | Basic | Basic | Basic | Basic |
| Blog / news cadence | None visible | Quarterly | None visible | Light | Active news section |
| Site freshness signals (copyright, content) | 2022 | Current | Current | 2026 update | Current |
| Service-area pages | No | Limited | No | No | Some |
| Visual identity strength | Weak (Divi default) | Conventional | Conventional | **Editorial / strong** | Refined / heritage |
| Mobile experience | Average | Average | Average | Above average | Above average |
| Backlink signals (relative) | Light (assumed) | Stronger (national chain pages) | Moderate | Strong (press, awards) | Strong (local civic) |
| SERP feature ownership (assumed) | Minimal | Some (branded queries) | Some (branded queries) | Some (chef-driven press) | Some (heritage stories) |

**Winner per dimension:** Repro loses every row today. None of these are unwinnable — the asset base (project library) is the rate-limiting input, and Repro has it. Everything else is execution.

---

## 6. Prioritized action plan

### Quick wins (do in the next two weeks — most pre-rebuild)

| Action | Impact | Effort | Notes |
|---|---|---|---|
| Update copyright year to current sitewide | Low | <15 min | Trust signal. |
| Remove broken Facebook feed embed (or reauth) | Medium | <30 min | Visible error on home page hurts brand. |
| Fix "knowklage" typo on About | Medium | <5 min | Embarrassing on a credibility page. |
| Standardize office hours to M–F 8am–6pm sitewide | Low | <15 min | Internal consistency. |
| Rewrite all image alt text on home, About, Galleries, Recent Projects | High | 2–3 hrs | Both accessibility and SEO. |
| Install Yoast or RankMath, write meta descriptions for top 10 pages | High | 2–3 hrs | Will appear in SERP snippets immediately. |
| Add Google Business Profile, claim it, fully populate photos / hours / services | High | 1–2 hrs | Critical for local QSR queries. |
| Submit XML sitemap to Google Search Console + Bing Webmaster | High | 30 min | Baseline for measurement. |
| Remove `user-scalable=0` from viewport meta | Low | <5 min | Accessibility fix. |

### Strategic investments (build into the new site)

| Action | Impact | Effort | Notes |
|---|---|---|---|
| Migrate to clean URL structure (`/projects/dunkin-danvers/`) | **High** | Inherent in rebuild | The single biggest lift. |
| Build one branded landing page per major QSR client (Dunkin', Jersey Mike's, Dave's, Wayback, Family Dollar) | **High** | 5–8 hrs each | These pages will outrank anything else Repro publishes. |
| Build 4–6 service-area landing pages (Peabody, Danvers, Salem, Beverly, Boston, North Shore) | **High** | 3–4 hrs each | Owns local intent. |
| Add LocalBusiness + Organization schema sitewide | **High** | 2–4 hrs to implement | Foundational for AI search. |
| Add Article schema to every case study, FAQ schema to every service page | **High** | 4–6 hrs total | Direct fuel for AI Overviews. |
| Build a dedicated speed/fast-track service page with the 14-day Dunkin' as the centerpiece case study | **High** | 4–6 hrs | Repro's most differentiated promise — give it a permanent home. |
| Collect and publish 3+ named-operator testimonials, with Review schema | **High** | Depends on Mark gathering them | Biggest "missing piece" identified in positioning brief. |
| Per-project case studies (3 deep, then continue) — Danvers Dunkin' 14-day, Revere 38-unit, named chef-driven QSR | High | 6–8 hrs each | The narrative versions of what's currently photo-only galleries. |
| Establish blog cadence — one post/month, alternating "industry insight" and "project recap" | Medium | 3–4 hrs per post | Freshness signal + long-tail keyword harvest. |
| Build a process / methodology pillar page ("How to choose a contractor for your restaurant build") | Medium | 8–12 hrs | Top-of-funnel awareness content for franchisees. |
| Drive-thru, retail TI, and multi-unit dedicated service pages | Medium | 4–6 hrs each | Captures vertical-specific intent. |
| Convert all images to WebP, add responsive srcset, lazy-load below the fold | Medium | Inherent in rebuild | Core Web Vitals win. |
| Add breadcrumb nav + BreadcrumbList schema | Medium | 2–3 hrs | Both UX and SEO. |
| Set up internal linking pattern: "Related projects" by brand and by vertical | Medium | Inherent in rebuild | Topic-cluster signal. |
| 301 redirect map from old `?page_id=` URLs to new clean URLs | **Critical** | 4–6 hrs | Preserves whatever rankings exist. Skip this and you lose all your equity. |
| Connect Search Console, GA4, and a rank tracker post-launch | High | 2–3 hrs | Measurement layer. |
| Backlink campaign: get listed in Dunkin' contractor directories, Jersey Mike's franchisee resources, MA general contractor associations | Medium | Ongoing | Authority signal. |
| Earn one press mention per quarter (industry publication, "14-day remodel" angle, named-project profile) | Medium | Ongoing | Domain authority. |

---

## 7. Measurement plan (post-launch)

Track monthly for the first six months:

- Organic sessions overall + by landing page
- Branded vs. non-branded query share (target: non-brand reaches 50%+ within 6 months)
- Top 10 ranking keywords + position changes
- Inbound contact-form submissions, with source attribution
- Phone call volume (if number is uniquely tagged for site)
- Google Business Profile impressions, direction requests, calls
- Core Web Vitals (LCP, INP, CLS) on mobile + desktop
- New referring domains (backlink signal)

**Baseline benchmark to set on day 1:** Whatever the current site ranks for in Google Search Console. Capture it before migration so post-launch impact is measurable.

---

## 8. Sources

- [Repro Construction — Home](https://reproconstruction.com/)
- [Recent Projects](https://reproconstruction.com/?page_id=1411)
- [About Us](https://reproconstruction.com/?page_id=1281)
- [Galleries](https://reproconstruction.com/?page_id=2)
- [Contact](https://reproconstruction.com/?page_id=133)
- [Residential](https://reproconstruction.com/?page_id=373)
- [Groom — Dunkin' Donuts (URL structure benchmark)](https://groomco.com/dunkin-donuts)
- [Cafco Construction (testimonial benchmark)](https://cafcoconstruction.com/)
- [Cornerstone Design/Build (vertical positioning benchmark)](https://www.cornerstonedesignbuild.com/)
- [Connolly Brothers](https://www.connollybrothers.com/)
