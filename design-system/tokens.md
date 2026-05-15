# Repro Construction Services — Design System Tokens

**Status:** Locked, v1.0 — 2026-05-15
**Consumer:** Homepage build agent (HTML/CSS); subsequent page builds; concierge intake module.
**Source brief:** `website-positioning-brief.md`, `wireframe-direction.md`, `repro-website-strategy-briefing.md`. This file is the spec. Do not re-derive.

The system reads as **Cafco's editorial confidence, tightened and graphic, with red as the energy.** White-space-forward, magazine-spread cadence, modern grotesque type, single-accent restraint. Owner-to-owner tone in every spacing and typographic choice. No card-grid icon parades, no Divi defaults, no fire-truck red, no construction-corporate gradients.

---

## 1. Color Palette

### Brand core

| Token | Hex | Role |
|---|---|---|
| `--color-red-primary` | `#C8102E` | Repro accent. The trade-flag red — used for the wordmark, the single accent moment per screen, primary CTA. Specifically chosen over `#DC2626` (Tailwind red-600, too web-saturated) and `#B22222` (firebrick, too brown). `#C8102E` is the Pantone 186-adjacent industrial red used on union signage, fire-rated hardware tags, and the kind of red you actually see on a jobsite that doesn't read cartoon. Strong but not garish. |
| `--color-red-deep` | `#9A0C23` | Hover state for primary red; press state on red buttons; underline accents on dark backgrounds. |
| `--color-red-tint` | `#FFF1F3` | 4% red wash for callout backgrounds, alert banners, focused-pillar surfaces. |
| `--color-black` | `#0A0A0A` | Near-black. True `#000000` reads flat on screens; `#0A0A0A` retains depth in photography overlays and feels like printed ink. |
| `--color-white` | `#FFFFFF` | True white. Canvas. The dominant surface. |
| `--color-off-white` | `#F7F6F3` | Warm paper — for alternating sections that need to break monotony without leaving the palette. Reads as drywall primer, not gray UI. |

### Neutrals (5-step)

| Token | Hex | Use |
|---|---|---|
| `--color-gray-900` | `#1A1A1A` | Body copy on light surfaces. Slightly softer than `--color-black`. |
| `--color-gray-700` | `#3D3D3D` | Subheads, secondary text, captions on light. |
| `--color-gray-500` | `#737373` | Tertiary text, metadata (project year, location stamp). |
| `--color-gray-300` | `#D4D4D4` | Hairline dividers, input borders, table rules. |
| `--color-gray-100` | `#EDEBE7` | Section backgrounds, image placeholder tone, hover surfaces. Reads slightly warm — coordinates with `--color-off-white`. |

### State colors

| Token | Hex | Use |
|---|---|---|
| `--color-hover-overlay` | `rgba(10,10,10,0.04)` | Hover overlay on neutral surfaces. |
| `--color-active-overlay` | `rgba(10,10,10,0.08)` | Pressed state. |
| `--color-focus-ring` | `#C8102E` (2px, offset 2px) | Accessible focus ring — uses primary red. Never the default browser blue. |
| `--color-success` | `#0F7A3C` | Concierge form success state. Muted forest, not Slack green. |
| `--color-error` | `#9A0C23` | Inline form error — reuses red-deep so we never introduce a second red family. |
| `--color-warning` | `#B5651D` | Construction amber — used sparingly (timeline at-risk indicator only). |

### Background tones (section rhythm)

The site alternates between three section surfaces to create magazine pacing without leaving the palette:

| Token | Hex | Cadence |
|---|---|---|
| `--bg-canvas` | `#FFFFFF` | Default. Most sections. |
| `--bg-paper` | `#F7F6F3` | Every 3rd–4th section for break. |
| `--bg-ink` | `#0A0A0A` | One section per page maximum — the "moment" (hero alt, testimonial pull-quote, CTA banner). White type, red accents. |

---

## 2. Typography

### Type family — locked

**Headers + body: Inter (variable weight).**
Inter chosen over Söhne (license cost: ~$1,000+ for web), GT America (license cost: similar), and Neue Haas Grotesk (license cost). Rationale: Inter is the closest free, open-source grotesque to Söhne/GT America — same neutral construction, same broad x-height, same industry-modern feel. Used by Linear, Vercel, Mercury — companies whose visual confidence Repro should rhyme with. Variable font means we get every weight from one file. **No serif accents, no display fonts.** The wordmark carries all the personality; the type system stays disciplined.

**CDN include (drop into `<head>`):**

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet">
```

System fallback stack: `'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif`.

### Type scale (desktop — see breakpoint section for mobile)

| Level | Size | Line-height | Letter-spacing | Weight | Use |
|---|---|---|---|---|---|
| **Display** | 88px / 5.5rem | 0.95 | -0.03em | 700 | Homepage hero headline only. One per page max. Set tight, big, confident. |
| **H1** | 56px / 3.5rem | 1.02 | -0.025em | 700 | Page-level headlines (case study title, service page lead). |
| **H2** | 40px / 2.5rem | 1.1 | -0.02em | 600 | Section openers ("Why operators choose Repro"). |
| **H3** | 24px / 1.5rem | 1.25 | -0.01em | 600 | Pillar card titles, sub-section heads, project tile titles. |
| **Body-large** | 20px / 1.25rem | 1.5 | 0 | 400 | Lead paragraphs, hero subhead, intro copy under H1. |
| **Body** | 17px / 1.0625rem | 1.6 | 0 | 400 | Default paragraph. Slightly larger than the 16px web default — gives the editorial-magazine feel. |
| **Caption** | 13px / 0.8125rem | 1.4 | 0.04em (tracked) | 500 | Eyebrow labels above section heads, photo credits, metadata. Often `text-transform: uppercase`. |

**Mobile scale** (≤768px): Display 56px, H1 40px, H2 32px, H3 22px, Body-large 18px, Body 16px, Caption 12px. Line-heights unchanged, letter-spacing unchanged.

### Hierarchy intent

- **Display** is the visual contract with the visitor. Reserved for the hero. "We build restaurants other GCs can't deliver on time." or similar.
- **H1** sets the page identity. Should never appear above the fold of a non-homepage screen alongside a Display.
- **H2** earns its size by introducing one idea per screen. If we have more than three H2s on a single page, the page is too long for Mark's "no endless scrolling" rule.
- **H3** carries the pillar structure. Always paired with a short body paragraph — never a bullet list.
- **Body-large** is the connective tissue between hero and content — the "Mark would actually say this out loud" voice register.
- **Body** is workhorse. Set in 70-character measure max for readability.
- **Caption** is editorial labeling — the small uppercase tag above an H2 ("CASE STUDY 01 / QSR FAST-TRACK"). This is where the magazine feel lives.

---

## 3. Spacing Scale

4px base. Use these exact values — no off-scale spacing.

| Token | Value | Use |
|---|---|---|
| `--space-0` | 0 | Reset. |
| `--space-1` | 4px | Inline icon offset, tight inline gap. |
| `--space-2` | 8px | Caption-to-headline spacing, tight stack. |
| `--space-3` | 12px | Button internal padding (vertical), form field internal padding. |
| `--space-4` | 16px | Default paragraph spacing, standard inline gap. |
| `--space-5` | 24px | Card internal padding (compact), small component gap. |
| `--space-6` | 32px | Card internal padding (standard), H3-to-body gap. |
| `--space-8` | 48px | Section subhead-to-content gap, large card padding. |
| `--space-10` | 64px | Between content blocks within a section. |
| `--space-12` | 96px | Section vertical padding (mobile). |
| `--space-16` | 128px | Section vertical padding (desktop). |
| `--space-20` | 160px | Hero-to-next-section breathing room. Use once per page. |

**Rule:** When in doubt, scale up. White space is the brand. Tight spacing reads as Divi-template; generous spacing reads as Cafco-editorial.

---

## 4. Grid System

### Breakpoints

| Token | Width | Range |
|---|---|---|
| `--bp-mobile` | up to 767px | Mobile portrait + landscape |
| `--bp-tablet` | 768px–1023px | Tablet, small laptop |
| `--bp-desktop` | 1024px–1439px | Standard laptop/desktop |
| `--bp-wide` | 1440px+ | Large displays |

### Container

| Token | Value |
|---|---|
| `--container-max` | 1320px (max content width, centered) |
| `--container-padding-mobile` | 20px |
| `--container-padding-tablet` | 40px |
| `--container-padding-desktop` | 64px |

### Columns

12-column grid on desktop, 8-column on tablet, 4-column on mobile.
Gutter: **24px desktop**, **20px tablet**, **16px mobile**.

| Token | Value |
|---|---|
| `--grid-columns-desktop` | 12 |
| `--grid-columns-tablet` | 8 |
| `--grid-columns-mobile` | 4 |
| `--grid-gutter-desktop` | 24px |
| `--grid-gutter-tablet` | 20px |
| `--grid-gutter-mobile` | 16px |

**Editorial rule:** content rarely fills 12 columns. Body copy lives in 6–8 columns max, offset. Full-bleed photography breaks the grid intentionally (negative margins to viewport edge) for hero modules — this is the magazine feel.

---

## 5. Component Primitives

### Buttons

Three variants. No fourth. No icon-only buttons in the primary nav.

**Primary (red)**
- Background: `--color-red-primary`
- Text: `--color-white`
- Font: Inter 600, 16px, letter-spacing 0.01em
- Padding: 16px 32px (vertical × horizontal)
- Border-radius: **2px** (intentionally near-square — soft pill radii read as web2 SaaS)
- Border: none
- Hover: background `--color-red-deep`, no scale transform
- Active: background `--color-red-deep`, inset shadow `0 1px 2px rgba(0,0,0,0.15)`
- Focus: 2px solid `--color-red-primary` outline, 2px offset
- Disabled: opacity 0.4, cursor not-allowed

**Secondary (outlined)**
- Background: transparent
- Text: `--color-black`
- Border: 1.5px solid `--color-black`
- Padding: 14.5px 30px (compensating for border so total height matches primary)
- Border-radius: 2px
- Hover: background `--color-black`, text `--color-white`
- Active: background `--color-gray-900`
- Focus: 2px solid `--color-red-primary` outline, 2px offset (focus is always red, regardless of button variant)

**Ghost (text-only)**
- Background: none
- Text: `--color-black`, 16px, weight 600
- Underline: 1.5px, offset 4px, `text-decoration-color: --color-red-primary`
- Padding: 0
- Hover: `text-decoration-thickness: 2px`
- Use: in-line CTAs within paragraphs, footer links, "read the full case study →"

### Pillar Cards (four-pillar grid)

The four pillars (Speed, Trust, QSR specialization, Owner relationship — confirm with positioning brief) are NOT icon-card-grid. They are typographic blocks.

- Background: `--bg-canvas` on white sections; `--bg-paper` on dark-background sections (inversion)
- Padding: `--space-8` (48px) all sides
- Border: top border only, 2px solid `--color-black`. **No card box-shadow. No rounded corners on the outer container.**
- Number eyebrow: Caption-styled, "01 / 02 / 03 / 04" — `--color-red-primary`, weight 600
- Title: H3 (24px)
- Body: Body (17px), max 3 lines
- Hover (if linked): top border becomes `--color-red-primary`, transition 200ms ease
- Layout: 4-up on desktop (3 columns each), 2-up on tablet (4 columns each), 1-up on mobile

**Critical:** no icons inside pillar cards. The numbered eyebrow is the visual hook. Icons would push us into the card-grid antipattern.

### Testimonial Blocks (named operator card)

Editorial pull-quote, not a card.

- Background: `--bg-ink` (`#0A0A0A`) or `--bg-paper` — alternate
- Padding: `--space-12` vertical, `--space-8` horizontal
- Quote text: H2 size (40px), weight 500 (lighter than headlines on purpose — quotes are spoken, not declared), italic NEVER (italic Inter looks software-y), color `--color-white` on ink, `--color-black` on paper
- Opening quote mark: oversized — 200px, weight 800, color `--color-red-primary`, positioned absolute top-left of the block, opacity 0.9
- Attribution stack:
  - Name (Body-large, weight 600)
  - Title + brand (Body, weight 400, `--color-gray-500` on light, `#A6A6A6` on dark)
  - Optional: brand logo grayscale at 24px height
- One testimonial per block. No carousels. **Pull-quote, page-break feel.**

### Project Tiles (case study cards)

These carry the homepage. Big, photographic, scannable.

- Aspect ratio: 4:5 (portrait) on desktop, 16:9 on mobile (flips for thumb-scroll)
- Background image: hero photo, full-bleed
- Overlay: linear-gradient from `rgba(10,10,10,0)` at 50% to `rgba(10,10,10,0.75)` at 100% — bottom-only
- Content (anchored bottom-left, `--space-6` padding):
  - Eyebrow caption: brand + location, e.g. "WORKS CAFE / WESTFORD, MA" — `--color-white`, 13px, tracked
  - Title: H3 white, e.g. "New build delivered in 11 weeks"
  - Metadata strip (revealed on hover): "11 WEEKS / $1.2M / NEW BUILD" — Caption, white, weight 500
- Hover: overlay deepens to 90% at bottom, metadata fades in (200ms), red 4px bottom border slides in from left
- No badges, no "View Project →" link visible — entire tile is clickable
- Click target: the whole tile, cursor pointer

### Section Dividers / Rules

- **Primary divider:** 1px solid `--color-gray-300`, full-width inside container
- **Editorial divider:** 4px solid `--color-red-primary`, 64px wide (not full width), used to separate eyebrow labels from section content — left-aligned, sits above H2
- **No decorative dividers, no SVG flourishes, no gradient lines.** The grid and whitespace do the dividing.

### Form Inputs (concierge intake baseline)

- Height: 56px (desktop), 52px (mobile)
- Padding: 16px horizontal, 18px vertical
- Background: `--color-white`
- Border: 1.5px solid `--color-gray-300`, bottom-only on dark backgrounds, full border on light
- Border-radius: 2px
- Font: Inter 400, 17px
- Placeholder: `--color-gray-500`, never the field label
- Label: Caption-styled, sits above field, `--space-2` gap, `--color-gray-700`
- Focus: border 1.5px `--color-red-primary`, no glow, no shadow
- Error: border `--color-error`, error message below at Caption size, `--color-error`
- Disabled: background `--color-gray-100`, text `--color-gray-500`
- **Concierge progress:** each step is a single question, full-width, large input — not a long form. One idea per screen applies here too.

---

## 6. Iconography Direction

**Restrained, optional, never decorative.** The system favors **typography over icons.** No icon-card-grids (the antipattern called out in the brief). When an icon is unavoidable — phone, email, location pin in the footer; chevron in pagination; check mark in form success — use **single-weight line icons, 1.5px stroke, 24px default size, color inherits from text.** Source: Phosphor Icons (Regular weight) or Lucide. Never two-weight, never filled, never colored — icons are typographic supplements, not visual statements. Pillar cards, service descriptions, and project metadata get **numerals and typography instead of icons.** The Repro wordmark is the only "logo-like" graphic element the system endorses. If you reach for an icon for a pillar or feature, the design is failing.

---

## 7. Motion

**Subtle, single-direction, never decorative.** Motion philosophy: every transition should feel like a job-site that's been planned — quiet, intentional, not theatrical. Use a single easing curve `cubic-bezier(0.4, 0, 0.2, 1)` (standard ease-out) and three durations only: **150ms** (micro-interactions: button hover, link underline), **300ms** (component reveals: card hover overlay, form focus), **600ms** (scroll-triggered fades, hero image reveal). **No parallax. No autoplay video. No infinite carousels. No bounce easing.** Scroll-triggered reveals use `opacity 0 → 1` and `transform: translateY(16px) → translateY(0)` — that combo only, applied to section headers and project tiles as they enter viewport. Honor `prefers-reduced-motion`: collapse all transitions to 0ms when set. Cursor is default — no custom cursor.

---

## 8. Photography Direction

**Jobsite-real and finished-space, owner-shot energy, never stock.** Two photo registers, both required:

**Register 1 — Finished-space hero photography.** Wide, evening-light interiors of completed restaurants. Furniture in place, signage lit, no construction debris, no people in hard hats. These are the magazine spreads. They headline case studies and the homepage hero. Color-grade: warm, slightly desaturated, never crushed-shadow Instagram-filter. Westford Works Cafe, Somerville Dunkin', Salem Canal St lead the rotation.

**Register 2 — Jobsite-real process photography.** Mid-build shots: framing exposed, electrical visible, drywall going up. Daytime, available light, no flash. People in them are real Repro crew — not models, not generic-trade stock. These live in case study process modules and the "about Repro" section. They prove the work is theirs.

**Never:** suited men shaking hands in front of blueprints, hard-hatted figures pointing at clipboards, hero shots of yellow excavators against blue sky, stock photos of architectural plans, drone shots of suburbs, any image with a watermark or stock-site provenance. If a photo could appear on Groom or Cornerstone's site, it cannot appear on Repro's.

**Hero (homepage):** Works Cafe Westford finished-space wide shot, evening interior light, full-bleed. Display headline overlays at 40% black gradient bottom-left.

**Aspect priorities:** finished-space → 16:9 or 21:9 (cinematic landscape). Jobsite-process → 3:2 or 4:5 (more square, feels documentary). Portraits of operators (testimonial subjects) → 4:5 vertical, environmental (in their restaurant), never headshot-on-gray-background.

**Image treatment:** no rounded corners on photography. No drop shadows. No duotone red overlay (the antipattern). Photos sit raw on the page; the type does the editorial work.

---

## 9. CSS Custom Property Reference

Paste this block into the site's root stylesheet (`:root {}`). All component CSS reads from these tokens. Do not hardcode any value that exists here.

```css
:root {
  /* === COLOR — BRAND === */
  --color-red-primary: #C8102E;
  --color-red-deep: #9A0C23;
  --color-red-tint: #FFF1F3;
  --color-black: #0A0A0A;
  --color-white: #FFFFFF;
  --color-off-white: #F7F6F3;

  /* === COLOR — NEUTRALS === */
  --color-gray-900: #1A1A1A;
  --color-gray-700: #3D3D3D;
  --color-gray-500: #737373;
  --color-gray-300: #D4D4D4;
  --color-gray-100: #EDEBE7;

  /* === COLOR — STATE === */
  --color-hover-overlay: rgba(10, 10, 10, 0.04);
  --color-active-overlay: rgba(10, 10, 10, 0.08);
  --color-focus-ring: #C8102E;
  --color-success: #0F7A3C;
  --color-error: #9A0C23;
  --color-warning: #B5651D;

  /* === COLOR — SECTION BACKGROUNDS === */
  --bg-canvas: #FFFFFF;
  --bg-paper: #F7F6F3;
  --bg-ink: #0A0A0A;

  /* === TYPE — FAMILY === */
  --font-sans: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;

  /* === TYPE — DESKTOP SCALE === */
  --type-display-size: 88px;
  --type-display-lh: 0.95;
  --type-display-ls: -0.03em;
  --type-display-weight: 700;

  --type-h1-size: 56px;
  --type-h1-lh: 1.02;
  --type-h1-ls: -0.025em;
  --type-h1-weight: 700;

  --type-h2-size: 40px;
  --type-h2-lh: 1.1;
  --type-h2-ls: -0.02em;
  --type-h2-weight: 600;

  --type-h3-size: 24px;
  --type-h3-lh: 1.25;
  --type-h3-ls: -0.01em;
  --type-h3-weight: 600;

  --type-body-large-size: 20px;
  --type-body-large-lh: 1.5;
  --type-body-large-ls: 0;
  --type-body-large-weight: 400;

  --type-body-size: 17px;
  --type-body-lh: 1.6;
  --type-body-ls: 0;
  --type-body-weight: 400;

  --type-caption-size: 13px;
  --type-caption-lh: 1.4;
  --type-caption-ls: 0.04em;
  --type-caption-weight: 500;

  /* === TYPE — MOBILE OVERRIDES (apply at max-width: 768px) === */
  --type-display-size-mobile: 56px;
  --type-h1-size-mobile: 40px;
  --type-h2-size-mobile: 32px;
  --type-h3-size-mobile: 22px;
  --type-body-large-size-mobile: 18px;
  --type-body-size-mobile: 16px;
  --type-caption-size-mobile: 12px;

  /* === SPACING === */
  --space-0: 0;
  --space-1: 4px;
  --space-2: 8px;
  --space-3: 12px;
  --space-4: 16px;
  --space-5: 24px;
  --space-6: 32px;
  --space-8: 48px;
  --space-10: 64px;
  --space-12: 96px;
  --space-16: 128px;
  --space-20: 160px;

  /* === GRID & CONTAINER === */
  --container-max: 1320px;
  --container-padding-mobile: 20px;
  --container-padding-tablet: 40px;
  --container-padding-desktop: 64px;

  --grid-columns-desktop: 12;
  --grid-columns-tablet: 8;
  --grid-columns-mobile: 4;
  --grid-gutter-desktop: 24px;
  --grid-gutter-tablet: 20px;
  --grid-gutter-mobile: 16px;

  /* === BREAKPOINTS (for reference; use in @media queries) === */
  --bp-mobile-max: 767px;
  --bp-tablet-min: 768px;
  --bp-tablet-max: 1023px;
  --bp-desktop-min: 1024px;
  --bp-wide-min: 1440px;

  /* === RADII === */
  --radius-sharp: 0;
  --radius-default: 2px;     /* buttons, inputs, tiles */
  --radius-pill: 999px;      /* reserved — concierge progress dots only */

  /* === BORDERS === */
  --border-hairline: 1px solid var(--color-gray-300);
  --border-rule: 1.5px solid var(--color-black);
  --border-pillar-top: 2px solid var(--color-black);
  --border-pillar-top-hover: 2px solid var(--color-red-primary);
  --border-editorial: 4px solid var(--color-red-primary);

  /* === SHADOWS (used sparingly) === */
  --shadow-press-inset: inset 0 1px 2px rgba(0, 0, 0, 0.15);
  /* No outer drop shadows in this system. */

  /* === MOTION === */
  --ease-standard: cubic-bezier(0.4, 0, 0.2, 1);
  --duration-micro: 150ms;
  --duration-component: 300ms;
  --duration-scene: 600ms;

  /* === Z-INDEX === */
  --z-base: 1;
  --z-sticky-nav: 50;
  --z-overlay: 100;
  --z-modal: 200;
  --z-concierge: 300;
}
```

---

## Build Notes for the Homepage Agent

- **Hero:** Display headline + Body-large subhead + Primary button + Secondary button, all left-aligned, layered over Works Cafe Westford full-bleed photo with 40% bottom gradient. Min-height 88vh, no taller.
- **Section rhythm:** canvas → paper → canvas → ink (one only) → canvas → paper → canvas. Roughly 5–7 sections total. Anything more violates the "no endless scrolling" rule.
- **One red moment per screen.** A primary button, OR a pull-quote opening mark, OR an editorial divider — not all three at once. Restraint is the brand.
- **Concierge entry point** lives in two places: sticky-nav-right "Get a fast-track bid" primary button, and a dedicated section above the footer ("Tell us what you're building. We'll be back to you in 24 hours.") with the first concierge question inline.
- **Footer:** ink background, white type, full NAP block (Peabody address, phone, email — sourced from `repro_contact_info.md`), brand portfolio logos grayscale at 32px height, social links as ghost text buttons. No newsletter signup.
- **Use the existing Repro wordmark** as-is for the nav logo, 32px height. Do not redraw.
