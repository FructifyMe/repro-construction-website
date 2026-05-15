# Repro Site QA Report — 2026-05-15

## Executive summary

- **All 22 pages render and all internal links resolve** — zero broken hrefs, zero leading-slash GitHub-Pages traps. Solid foundation.
- **3 missing image files** would produce broken-image icons on the homepage: the leadership headshots (`team-mark-geissler.jpg`, `team-nick-geissler.jpg`, `team-chris-sibulkin.jpg`). These are referenced at `index.html:812-814` and have TODO comments above them, so they were planned — but they are real broken `<img>` tags right now, not commented out.
- **Mustache placeholders (`{{...}}`) are still live in `case-studies/works-cafe-westford.html`** — 14 of them, including `{{TARGET_OPEN_DATE}}`, `{{ACTUAL_OPEN_DATE}}`, `{{PROJECT_VALUE}}`. These will render as literal curly-brace text on the live page. **Most embarrassing finding.** Mark/Nick must fill these before launch.
- **`[CONTENT TO BE PROVIDED BY NICK]` / `[TESTIMONIAL TO BE GATHERED]` / `[VERIFY WITH NICK]` placeholders appear in 13 pages** — most case studies, all brand pages, both 3 service-area pages, both vertical pages. Many are visibly tagged with red "placeholder" badges (intentional pre-launch flags) but they are still live text on the page.
- **Title + meta description compliance is broken in nearly every page.** 17 of 22 titles exceed 60 chars; 19 of 22 meta descriptions exceed 160 chars. Will display truncated in Google SERPs.

## Pages audited

| Page | Lines |
|---|---|
| `index.html` | 1201 |
| `start-project.html` | 1785 |
| `case-studies/works-cafe-westford.html` | 1249 |
| `case-studies/dunkin-somerville.html` | 814 |
| `case-studies/canal-st-salem.html` | 810 |
| `brands/dunkin.html` | 611 |
| `brands/inspire-brands.html` | 403 |
| `brands/jersey-mikes.html` | 410 |
| `brands/wayback-burger.html` | 410 |
| `brands/works-cafe.html` | 410 |
| `verticals/restaurant.html` | 1359 |
| `verticals/multi-unit.html` | 835 |
| `verticals/residential.html` | 774 |
| `service-areas/peabody.html` | 629 |
| `service-areas/danvers.html` | 629 |
| `service-areas/salem.html` | 629 |
| `service-areas/beverly.html` | 629 |
| `service-areas/westford.html` | 629 |
| `service-areas/somerville.html` | 629 |
| `service-areas/boston.html` | 629 |
| `service-areas/north-shore.html` | 629 |
| `llms.txt` | 77 |
| `sitemap.xml` | 132 |
| **Total** | **16,312** |

## 1. NAP consistency

All 22 audited pages carry the canonical NAP. No variants found in audited pages:

- Name: "Repro Construction" present 6–19 times per page; "Repro Construction Services LLC" used in formal contexts (footer, JSON-LD).
- Address: "525 Lowell St, Peabody, MA 01960" present on every page.
- Phone: `(617) 820-8681` present on every page; `tel:+1-617-820-8681` / `tel:+16178208681` both used consistently (acceptable).
- Email: `mark@reproconstruction.com` present on every page.

**Rogue NAP detected but OUT OF SCOPE:**

- `discovery-questionnaire.html` uses `fructifyme@gmail.com` (this is the Fructify intake, not a Repro page — leave as-is).
- `outreach-email-to-mark.html` uses `(978) 880-0953` and `mfarley@fructifyme.com` (this is Mike's outbound prospecting email — leave as-is).
- `start-project.html:1220` uses `(617) 555-0100` as the **placeholder attribute** on a phone input field, not as a real number. Acceptable — but consider replacing with `(555) 555-5555` or similar so it's unambiguously a sample.

## 2. Internal link integrity

- **0 broken internal links** across 22 pages.
- **0 leading-slash hrefs** — none of the GitHub-Pages-breaking `href="/..."` patterns exist.
- All 22 sitemap.xml entries point to files that exist on disk.

| Status | Count |
|---|---|
| Total internal links checked | ~hundreds |
| Broken targets | 0 |
| Leading-slash GH-Pages traps | 0 |

## 3. Schema presence

| Page | JSON-LD Types Present | Verdict |
|---|---|---|
| `index.html` | Organization, LocalBusiness, FAQPage, Person, PostalAddress, OpeningHoursSpecification, AdministrativeArea | OK |
| `start-project.html` | WebPage, Organization, CommunicateAction, BreadcrumbList, Person | OK |
| `case-studies/works-cafe-westford.html` | Article, GeneralContractor, Organization, ImageObject, Review, Rating, Place | OK |
| `case-studies/dunkin-somerville.html` | Article, GeneralContractor, Organization, ImageObject, Review, Rating, Place | OK |
| `case-studies/canal-st-salem.html` | Article, GeneralContractor, Organization, ImageObject, Review, Rating, Place | OK |
| `brands/dunkin.html` | Service, LocalBusiness, FAQPage, BreadcrumbList, AdministrativeArea | OK |
| `brands/jersey-mikes.html` | Service, LocalBusiness, FAQPage, BreadcrumbList | OK |
| `brands/works-cafe.html` | Service, LocalBusiness, FAQPage, BreadcrumbList | OK |
| `brands/wayback-burger.html` | Service, LocalBusiness, FAQPage, BreadcrumbList | OK |
| `brands/inspire-brands.html` | Service, LocalBusiness, FAQPage, BreadcrumbList | OK |
| `verticals/restaurant.html` | Service, LocalBusiness, FAQPage, OfferCatalog, Offer, BreadcrumbList | OK |
| `verticals/multi-unit.html` | Service, LocalBusiness, FAQPage, OfferCatalog, Offer, BreadcrumbList | OK |
| `verticals/residential.html` | Service, LocalBusiness, FAQPage, OfferCatalog, Offer, BreadcrumbList | OK |
| `service-areas/*.html` (all 8) | LocalBusiness, FAQPage, BreadcrumbList, City, AdministrativeArea, OpeningHoursSpecification | OK |

**No missing schema. Coverage is excellent across all 22 pages.** One nit: some service-area JSON-LD blocks use inconsistent spacing around `"@type":` (e.g., `"@type":"City"` vs. `"@type": "City"` on the same page). Cosmetic only; parsers don't care.

## 4. OG/Twitter meta

| Page | og: count | twitter: count | Status |
|---|---|---|---|
| `index.html` | 7 | 4 | OK |
| `start-project.html` | 7 | 3 | OK (slight twitter shortage) |
| All other 20 pages | 7 | 4 | OK |

**Every page has Open Graph and Twitter Card meta. No duplicates detected. `start-project.html` has 3 twitter tags instead of 4 — minor.**

## 5. Title + meta description

| Page | Title len | Desc len | Flags |
|---|---|---|---|
| `index.html` | 62 | 260 | TITLE>60, DESC>160 |
| `start-project.html` | 62 | 200 | TITLE>60, DESC>160 |
| `case-studies/works-cafe-westford.html` | 63 | 217 | TITLE>60, DESC>160 |
| `case-studies/dunkin-somerville.html` | 76 | 232 | TITLE>60, DESC>160 |
| `case-studies/canal-st-salem.html` | 54 | 222 | DESC>160 |
| `brands/dunkin.html` | 55 | 167 | DESC>160 |
| `brands/jersey-mikes.html` | 61 | 172 | TITLE>60, DESC>160 |
| `brands/works-cafe.html` | 55 | 171 | DESC>160 |
| `brands/wayback-burger.html` | 58 | 176 | DESC>160 |
| `brands/inspire-brands.html` | 56 | 185 | DESC>160 |
| `verticals/restaurant.html` | 66 | 195 | TITLE>60, DESC>160 |
| `verticals/multi-unit.html` | 75 | 205 | TITLE>60, DESC>160 |
| `verticals/residential.html` | 73 | 184 | TITLE>60, DESC>160 |
| `service-areas/peabody.html` | 72 | 158 | TITLE>60 |
| `service-areas/danvers.html` | 72 | 177 | TITLE>60, DESC>160 |
| `service-areas/salem.html` | 70 | 164 | TITLE>60, DESC>160 |
| `service-areas/beverly.html` | 72 | 177 | TITLE>60, DESC>160 |
| `service-areas/westford.html` | 73 | 155 | TITLE>60 |
| `service-areas/somerville.html` | 75 | 174 | TITLE>60, DESC>160 |
| `service-areas/boston.html` | 71 | 170 | TITLE>60, DESC>160 |
| `service-areas/north-shore.html` | 57 | 170 | DESC>160 |

**17 of 22 titles exceed 60 chars. 19 of 22 descriptions exceed 160 chars.** Service-area pages share the boilerplate "Construction & Restaurant Contractor in {City}, MA | Repro Construction" pattern, all 70–75 chars. Consider shortening to e.g. "Restaurant Contractor in {City}, MA | Repro Construction" (~57 chars).

## 6. Image references

**3 missing files (all on homepage):**

- `index.html:812` → `assets/images/team-mark-geissler.jpg` — missing
- `index.html:813` → `assets/images/team-nick-geissler.jpg` — missing
- `index.html:814` → `assets/images/team-chris-sibulkin.jpg` — missing

All 18 other unique image refs resolve cleanly. og:image references all resolve.

## 7. Placeholder inventory

### `{{MUSTACHE_TOKENS}}` (must-fill before launch)

All 14 occurrences are in **`case-studies/works-cafe-westford.html`**. Unique tokens:

- `{{SQUARE_FOOTAGE}}` — line 933
- `{{SEAT_COUNT}}` — line 934
- `{{TARGET_OPEN_DATE}}` — lines 936, 991, 1131
- `{{ACTUAL_OPEN_DATE}}` — lines 937, 991
- `{{SCHEDULE_VARIANCE}}` — line 938
- `{{PROJECT_VALUE}}` — line 939
- `{{PROJECT_LEAD_NAME}}` — line 941
- `{{DAYS_SAVED_VS_BASELINE}}` — line 991
- `{{PUNCH_CLOSE_DAYS}}` — line 1064
- `{{FOLLOW_ON_PROJECTS}}` — line 1087
- `{{CUSTOMER_RECEPTION_METRIC}}` — line 1088

These render as literal `{{TOKEN}}` text on the page — biggest pre-launch blocker.

### `[CONTENT TO BE PROVIDED BY NICK]` — 14 occurrences

- `case-studies/canal-st-salem.html`: lines 594, 610, 629, 634, 639, 644, 660, 676
- `case-studies/dunkin-somerville.html`: lines 598, 614, 633, 638, 643, 664, 680

### `[TESTIMONIAL TO BE GATHERED]` — 13 occurrences

- `index.html`: lines 1065, 1079
- `case-studies/canal-st-salem.html`: line 91 (in JSON-LD reviewBody!)
- `case-studies/dunkin-somerville.html`: line 93 (in JSON-LD reviewBody!)
- `brands/dunkin.html`: line 492
- `brands/inspire-brands.html`: line 324
- `brands/jersey-mikes.html`: line 331
- `brands/wayback-burger.html`: line 331
- `verticals/multi-unit.html`: line 713
- `verticals/residential.html`: line 657
- `verticals/restaurant.html`: lines 1211, 1224

**⚠ Critical:** The `[TESTIMONIAL TO BE GATHERED]` strings in JSON-LD `reviewBody` will publish to Google as the literal review text. Either remove the Review/Rating schema blocks until real quotes exist, or fill them in.

### `[TESTIMONIAL TO BE PROVIDED BY NICK]` — 2 occurrences

- `case-studies/canal-st-salem.html`: line 692
- `case-studies/dunkin-somerville.html`: line 696

### `[VERIFY WITH NICK]` — 15 occurrences (all in brand pages)

- `brands/dunkin.html`: lines 459, 468, 477
- `brands/inspire-brands.html`: lines 291, 300, 309
- `brands/jersey-mikes.html`: lines 298, 307, 316
- `brands/wayback-burger.html`: lines 298, 307, 316
- `brands/works-cafe.html`: lines 298, 307, 316

### `[LOCAL PROJECTS — VERIFY WITH NICK]` — 3 occurrences

- `service-areas/beverly.html`: line 520
- `service-areas/danvers.html`: line 520
- `service-areas/peabody.html`: line 520

(Other 5 service-area pages don't have this token — worth checking whether their local-project sections are real or just absent.)

### `[PROJECT TO BE PROVIDED BY MARK]` — 3 occurrences

- `verticals/multi-unit.html`: lines 678, 686, 695

### `[CASE STUDIES TO BE PROVIDED]` — 3 occurrences

- `verticals/residential.html`: lines 621, 630, 639

### `TODO` — 10 occurrences (all in `index.html`, all in HTML comments)

Lines 922, 949, 1009, 1054, 1068, 1082, 1105, 1113, 1122, 1167. These are inline notes to self about wordmark SVG, hero background, case-study link placeholders, operator portraits, team headshots, and Nick's LinkedIn URL. They won't show on the rendered page but are signals of unfinished work.

**Total live placeholders on rendered pages: 67 (excluding HTML-comment TODOs).**

## 8. Token compliance

Rogue hex codes found (not in the locked palette):

| Hex | Locations | Severity |
|---|---|---|
| `#fff` | 5 brand pages (verify-flag CSS) | Cosmetic — equivalent to `#FFFFFF` but should be `var(--color-white)`. Brand verify flags are pre-launch only so will disappear anyway. |
| `#A6A6A6` | `index.html` (3x), `start-project.html` (2x), case-studies | Light-gray text on dark sections. Not in palette — should use `var(--color-gray-300)` (#D4D4D4) or `var(--color-gray-500)` (#737373). |
| `#C9C9C9` | `index.html`, `start-project.html`, all 3 case studies | Footer link color on dark. Same issue as above. |
| `#888` | `index.html`, `start-project.html`, all 3 case studies | Footer-bottom caption color on dark. Not in palette. |
| `#2a2a2a` | `index.html` (2x), all 3 case studies | Testimonial photo placeholder background and similar. Should be `var(--color-gray-900)` or `var(--color-black)`. |
| `#1f1f1f` | `verticals/multi-unit.html`, `verticals/residential.html` | Work-tile placeholder background. Same issue. |

**None of these will look wrong visually** — they're all in the near-black/light-gray family. But they violate the locked-token rule and would need cleanup before any future palette swap. Recommend a global pass to swap each to a named token.

## 9. Section count per page

| Page | Top-level `<section>` | Status |
|---|---|---|
| `index.html` | 5 | OK |
| `start-project.html` | 3 | OK |
| `case-studies/works-cafe-westford.html` | 9 | **OVER (>8)** |
| `case-studies/dunkin-somerville.html` | 9 | **OVER (>8)** |
| `case-studies/canal-st-salem.html` | 9 | **OVER (>8)** |
| `brands/*` (all 5) | 6 | OK |
| `verticals/restaurant.html` | 8 | At threshold |
| `verticals/multi-unit.html` | 7 | OK |
| `verticals/residential.html` | 7 | OK |
| `service-areas/*` (all 8) | 6 | OK |

**All 3 case-study pages exceed the "no endless scrolling" rule by one section each.** Worth a visual check — case studies are inherently long-form so this may be intentional. If so, consider documenting the case-study exception in `tokens.md`.

## 10. Red-moment heuristic

Counted references to red (var or hex) across all pages. This is a CSS-rule count, not a count of visible elements — true visual check needs Mike's eye. Threshold heuristic: more than ~15 `--color-red-primary` refs per page suggests red is showing up in more than one moment per section.

| Page | red-primary | red-deep | red-tint | Note |
|---|---|---|---|---|
| `case-studies/works-cafe-westford.html` | 18 | 10 | 7 | High — but this is the flagship case study with monospace red badges for {{TOKEN}} placeholders; once filled, many of these red tints disappear. |
| `verticals/restaurant.html` | 18 | 2 | 2 | High — longest page, hero + CTA + multiple section accents. Worth visual check. |
| `start-project.html` | 18 | 4 | 4 | High — multi-step form with red validation states; expected. |
| All others | 12–16 | 2–4 | 0–2 | Within range. |

**No page screams of red over-use, but `works-cafe-westford.html` should be re-checked once the `{{TOKEN}}` red-tint badges are removed/converted to real values.**

## What Mark/Nick still need to provide

### Mark must provide
- **Team headshots** (3 images): `team-mark-geissler.jpg`, `team-nick-geissler.jpg`, `team-chris-sibulkin.jpg`
- **Multi-unit project content**: 3 entries in `verticals/multi-unit.html` (lines 678, 686, 695)
- Wordmark SVG (per TODO at `index.html:922`)
- Confirm Nick's public LinkedIn URL (per TODO at `index.html:1167`)
- Optional: operator headshots (Richard French, Jason Pino, Philip Dietrich)

### Nick must provide
- **Works Cafe Westford case-study metrics** (14 mustache tokens at `case-studies/works-cafe-westford.html`): square footage, seat count, target/actual open dates, schedule variance, project value, project lead name, days saved vs. baseline, punch-close days, follow-on projects, customer reception metric.
- **Canal St Salem case-study content** (8 `[CONTENT TO BE PROVIDED BY NICK]` tokens)
- **Dunkin Somerville case-study content** (7 `[CONTENT TO BE PROVIDED BY NICK]` tokens)
- **Case-study testimonials** (Canal St, Dunkin Somerville) — 2 quotes
- **Brand-page verifications** (15 `[VERIFY WITH NICK]` tags across 5 brand pages — typically franchisee references and project counts)
- **Service-area local projects** (Beverly, Danvers, Peabody — 3 service-area pages awaiting local project lists)
- **Residential case studies** (3 entries in `verticals/residential.html`)

### Testimonials to gather (operator quotes — Mark or Nick)
- Richard French quote (The Works Cafe) — referenced in `index.html`, `brands/works-cafe.html`, `verticals/restaurant.html`
- Jason Pino quote (Dunkin) — referenced in `index.html`, `brands/dunkin.html`, `case-studies/dunkin-somerville.html`, `verticals/restaurant.html`
- Philip Dietrich quote (Jersey Mike's) — referenced in `index.html`, `brands/jersey-mikes.html`
- Wayback Burger operator quote — `brands/wayback-burger.html`
- Inspire Brands operator quote — `brands/inspire-brands.html`
- Multi-unit operator quote — `verticals/multi-unit.html`
- Residential homeowner quote — `verticals/residential.html`

## Mike's pre-launch action items

### P0 — blockers (would embarrass Mark/Nick on launch day)
1. **Strip or fill the 14 `{{MUSTACHE}}` tokens in `case-studies/works-cafe-westford.html`** — these will render as literal `{{TOKEN}}` text. Either fill from Nick's data or replace with neutral copy ("project value: undisclosed", etc.).
2. **Remove or fill `[TESTIMONIAL TO BE GATHERED]` from JSON-LD `reviewBody` in case-study schema** (`canal-st-salem.html:91`, `dunkin-somerville.html:93`) — Google will index this literal string.
3. **Add or remove the 3 missing team headshots** at `index.html:812-814` — broken-image icons on home page hero is the worst visual launch bug.
4. **Decide on the 67 visible `[BRACKETED PLACEHOLDER]` tags** — either fill them with real content from Mark/Nick, or hide them with `display:none` until they ship.

### P1 — SEO compliance (do before Google indexes)
5. **Shorten 17 page titles to ≤60 chars** — start with service-area boilerplate template ("Construction & Restaurant Contractor in {City}, MA | Repro Construction" → "Restaurant Contractor in {City}, MA | Repro Construction").
6. **Shorten 19 meta descriptions to 150–160 chars.**
7. **Verify all 3 case studies' top-level section count is intentional** (currently 9 each; rule is ≤8).

### P2 — polish
8. **Token cleanup pass**: replace `#fff`, `#A6A6A6`, `#C9C9C9`, `#888`, `#2a2a2a`, `#1f1f1f` with named tokens from `design-system/tokens.md`.
9. **Add the 4th twitter card meta** to `start-project.html`.
10. **Normalize JSON-LD whitespace** in service-area pages (`"@type":"City"` vs. `"@type": "City"`).
11. **Replace the `(617) 555-0100` placeholder** in the `start-project.html` phone-input `placeholder=` attribute with an unambiguous fake (e.g., `(555) 555-5555`).
12. **Empty `insights/` directory** — either populate or remove the link strategy if any page references it. (Confirmed: no pages link to `/insights/` so this is fine; the directory just exists empty.)

