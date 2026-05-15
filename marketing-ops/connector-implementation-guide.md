# Marketing Connector Implementation Guide — Repro Construction

**Audience:** Mike (Fructify) executes initial wire-up. Mark/Nick maintain post-handoff.
**Sequencing principle:** Free / mandatory tools first. Paid tools second. Nice-to-haves last.
**Operating principle:** Repro is a $7M restaurant GC. We are not building a SaaS marketing stack. We are wiring up four or five tools that pay back inside 60 days and walking away.

---

## Phase 1 — Day 0 (launch day, mandatory)

### 1. Google Search Console — free, mandatory

Mandatory before any other SEO tool. Free. Verifies the site to Google and exposes the queries people are actually using to find Repro.

**Setup:**
1. Mike adds Mark as a property owner via `https://search.google.com/search-console`.
2. Choose "URL prefix" property, enter `https://reproconstruction.com`.
3. Verify via HTML meta tag method — paste the verification tag in `<head>` of every page.

**Snippet to add inside `<head>` of every page (or the shared layout/partial):**

```html
<meta name="google-site-verification" content="REPLACE_WITH_GSC_TOKEN_AT_SETUP" />
```

**What to do in the first 30 days:**
- Submit `sitemap.xml` from the GSC dashboard.
- Watch the "Performance" tab weekly. Note which queries the site is getting impressions on (target queries: "Dunkin contractor Massachusetts," "Works Cafe construction partner," etc.).
- Use "URL Inspection" to force re-crawl after any major page edit.

---

### 2. Analytics — pick one (Plausible recommended)

**Plausible (recommended):** $9-19/mo, privacy-friendly, no cookie banner needed, simple dashboard, GDPR-safe by default. The right choice for a 30-year construction firm that is not running heavy paid acquisition.

**GA4 (alternative):** Free. Better if Mark decides to run Google Ads or Meta ads later — the conversion tracking integrates natively. Heavier setup, cookie banner required.

**Recommendation for Repro:** Plausible. Switch to GA4 only if and when Mark commits to paid acquisition.

**Plausible snippet (paste in `<head>` of every page):**

```html
<script defer data-domain="reproconstruction.com" src="https://plausible.io/js/script.js"></script>
```

**GA4 snippet (only if going that direction instead):**

```html
<!-- Google tag (gtag.js) -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

**Wire-up:** Mike installs in the shared `<head>` partial. Mark gets a viewer login. Nick gets a viewer login.

---

### 3. Form handling — Formspree (recommended) or Basin

The current concierge intake at `/contact` uses a `mailto:` fallback. That has to go before launch — `mailto:` opens a desktop email client (Outlook, Apple Mail), which most QSR operators on mobile don't have configured. We lose 30-50% of inquiries to that flow.

**Formspree (recommended):** $10/mo Personal plan covers Repro's volume. Built-in spam filter, file uploads, autoresponder, webhook to HubSpot/Zapier.

**Basin (alternative):** Same idea, smaller team. $8/mo. Fine alternative if Formspree changes pricing.

**Replacement snippet for the concierge intake form** (replaces current `mailto:` action):

```html
<form action="https://formspree.io/f/REPLACE_WITH_FORMSPREE_ID" method="POST">
  <label>Brand
    <select name="brand" required>
      <option value="">Select a brand</option>
      <option>Dunkin'</option>
      <option>Jersey Mike's</option>
      <option>Inspire Brands</option>
      <option>The Works Cafe</option>
      <option>Wayback Burger</option>
      <option>Other / Independent</option>
    </select>
  </label>
  <label>Location (city, state)
    <input type="text" name="location" required>
  </label>
  <label>Scope
    <select name="scope" required>
      <option value="">Select scope</option>
      <option>New build</option>
      <option>Remodel / refresh</option>
      <option>Fast-track tenant improvement</option>
      <option>Multi-unit rollout</option>
      <option>Pre-construction consulting</option>
    </select>
  </label>
  <label>Timeline
    <select name="timeline" required>
      <option value="">Select timeline</option>
      <option>Active now</option>
      <option>Next 3 months</option>
      <option>Next 6 months</option>
      <option>6-12 months out</option>
      <option>Exploring / no date yet</option>
    </select>
  </label>
  <label>Name <input type="text" name="name" required></label>
  <label>Email <input type="email" name="email" required></label>
  <label>Phone <input type="tel" name="phone"></label>
  <input type="hidden" name="_subject" value="New concierge intake — reproconstruction.com">
  <input type="hidden" name="_next" value="https://reproconstruction.com/thank-you">
  <button type="submit">Send to Mark and Nick</button>
</form>
```

**Webhook chain:** Formspree → HubSpot CRM contact create → HubSpot workflow → kicks off the nurture sequence if no booked call within 7 days. Document the webhook URL in the team password manager.

---

## Phase 2 — Week 1-2 (revenue infrastructure)

### 4. Email + CRM — HubSpot Starter (recommended over Klaviyo for Repro)

**HubSpot Starter:** $20/mo Marketing + $20/mo Sales. Total ~$40/mo at start. Free CRM tier covers contact management — Mark and Nick can each get a seat.

**Why HubSpot, not Klaviyo:** Klaviyo is engineered for e-commerce — abandoned cart, browse abandonment, product feeds. Repro doesn't have any of those triggers. Klaviyo's B2B workflows feel bolted-on. HubSpot's deal pipeline + contact properties + native form integration is what Repro actually needs. Email automation is HubSpot's weaker side compared to Klaviyo, but for a 6-email nurture sequence and a weekly newsletter, it's more than enough.

**Wire-up sequence:**
1. Mike creates the HubSpot account under `mark@reproconstruction.com`.
2. Connect HubSpot Forms or use Formspree webhook to push intake into HubSpot as a new contact with `lifecyclestage = lead`.
3. Build the deal pipeline stages: *Intake Received → Discovery Call → Proposal → Bid Submitted → Awarded → Lost*.
4. Paste the 6 nurture emails from `nurture-sequence.md` as a HubSpot Workflow triggered by `form fill = concierge intake AND days since fill = 7 AND deal stage != Discovery Call`.
5. Mark and Nick each get a Sales seat. They get email tracking + calendar booking via HubSpot Meetings.

**Mark's "Talk to Mark" CTA on the site** → links to a HubSpot Meetings page. Mike provisions a 30-minute "QSR project consult" meeting type and embeds the booking link site-wide.

---

### 5. SEO monitoring — GSC + Ahrefs Lite (or skip Ahrefs)

**Google Search Console:** Free, mandatory (covered above).

**Ahrefs Lite ($129/mo):** Recommended *only* if Mike or Mark plans to actively pursue link building and competitive SEO. For a referral-driven business, Ahrefs is a luxury. Most of Repro's wins will come from:
- Branded queries ("Repro Construction")
- Brand-specific queries ("Dunkin contractor Massachusetts") — these need on-page content, not link building
- Local-pack queries ("restaurant contractor Peabody") — these need GBP work, not Ahrefs

**Similarweb ($199/mo+):** Skip. Similarweb is built for digital-native businesses with high web traffic. Repro's competitive cohort (Groom, Cornerstone) doesn't have enough traffic to make Similarweb's data useful.

**Recommendation for Repro:** GSC only. Re-evaluate Ahrefs at 6 months post-launch *if* Mark wants to actively chase non-branded SEO.

---

## Phase 3 — Week 2-4 (publishing infrastructure)

### 6. Social scheduling — Buffer (recommended)

**Buffer Essentials:** $6/mo per channel. Repro needs LinkedIn (Nick personal + Repro company page) + GBP + Instagram. ~$25/mo total.

**Hootsuite:** More expensive ($99/mo+), more bloated, designed for agencies. Skip.

**Why this matters:** LinkedIn is where Nick's content compounds. Nick is busy running projects. Buffer lets Nick batch-write 4 weeks of LinkedIn posts on a Sunday afternoon and never think about it again. That's the entire ROI.

**Critical for QSR construction:** LinkedIn *organic* > LinkedIn *paid*. Do not let Mark buy LinkedIn ads. The audience is too narrow and the cost-per-impression is too high. Nick posting consistently from his personal account is the engine. Buffer is the way that engine runs without breaking.

---

### 7. Canva — Pro plan ($15/mo)

Mike will build the following recurring templates inside a shared Canva team:

1. **Case study card** — square format, brand badge, project name, target-open hit, 2-line operator quote.
2. **Before/after carousel** — 5-slide LinkedIn carousel, square format, branded.
3. **Brand-spec compliance graphic** — vertical format for Instagram and LinkedIn, with one stat or one spec callout.
4. **Equipment-arrived post template** — simple photo overlay for "long-lead [equipment] delivered, on schedule for [brand] [location]."
5. **Quote graphic template** — for the three named operator quotes, with brand badge.
6. **Stat card template** — for cost-of-cheap-GC stats and similar (the 22-28% number, target-open hit rate, etc.).

**Handoff:** Nick is the primary user. Each template comes with a 90-second Loom walkthrough on how to swap in new content.

---

### 8. Review collection — keep it simple

**Options:**

- **Reputation.com / Birdeye / Podium:** $300-500/mo. Designed for high-volume local businesses (auto dealers, dentists, etc.). Massive overkill for a GC doing 20-30 projects a year.
- **Google native:** Free. Mark sends the review request template from `gbp-optimization.md` after every completed project.
- **Reviewshake / Grade.us:** $50-100/mo middle path. Worth it only if Mark commits to chasing reviews on multiple platforms (Google + BBB + Houzz).

**Recommendation:** **Skip the tooling.** Mark sends the review-request template from the GBP doc manually, 5-7 days after every completed project. Calendar reminder on Mark's calendar at project closeout. That's it. 20-30 reviews a year is plenty to dominate the local pack for QSR-related queries.

---

## What Mike has to actually pay for / authenticate vs. what's free

| Tool | Status | Mike to authenticate? | Monthly cost |
|---|---|---|---|
| Google Search Console | Mandatory, free | Yes — verify via meta tag | $0 |
| Plausible Analytics | Recommended | Yes — Mike creates the account | $9-19 |
| Formspree | Mandatory (replace mailto) | Yes — Mike creates form endpoint | $10 |
| HubSpot Starter (Marketing + Sales) | Strongly recommended | Mark creates account, Mike configures | ~$40-50 |
| Buffer Essentials | Recommended | Nick creates account, Mike configures | ~$25 |
| Canva Pro | Recommended | Mike creates team, adds Nick/Mark | $15 |
| Google Business Profile | Mandatory, free | Mark verifies (already verified) | $0 |
| Ahrefs / Similarweb | Skip at launch | No | $0 (skipped) |
| Reputation.com / Birdeye | Skip | No | $0 (skipped) |

**Total committed monthly spend at launch: ~$100-115/mo.** That's the entire marketing stack. Anything beyond this is unnecessary at Repro's scale until Mark sees ROI from these eight tools and decides to scale up.

---

## Handoff package to Mark/Nick

When Mike hands the keys over:

- [ ] Shared 1Password vault with all credentials.
- [ ] One Loom video (≤ 5 minutes) walking through the dashboards.
- [ ] One-page cheat sheet: which tool answers which business question.
- [ ] Monthly check-in slot on Mark's calendar — 30 minutes, first Tuesday of the month — to review what's working and kill what isn't.
