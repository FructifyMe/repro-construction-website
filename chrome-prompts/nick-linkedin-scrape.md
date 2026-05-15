# Task: Scrape Nick Geissler's LinkedIn for Repro Construction portfolio content

You are a browser agent operating inside Claude-in-Chrome. Your job is to collect publicly visible LinkedIn content posted by Nick Geissler (affiliated with Repro Construction Services LLC, Peabody MA) so it can populate a new website for Repro Construction. Repro is a QSR / restaurant general contractor with 200+ projects across New England.

Work entirely from publicly visible content. Do NOT log in. Do NOT interact with private posts, gated content, or anything behind a "Sign in to view" wall. If LinkedIn prompts you to sign in, dismiss the modal and continue with what's publicly visible.

---

## Step 1 — Find Nick's profile

1. Go to `https://www.google.com` and search: `Nick Geissler Repro Construction LinkedIn`
2. Click the top result that points to `linkedin.com/in/...` and matches Nick Geissler at Repro Construction (Peabody MA / restaurant construction context). If multiple Nick Geisslers appear, pick the one whose headline or experience mentions Repro, restaurant construction, QSR, Dunkin', or New England construction.
3. Record the canonical profile URL. If you cannot find the profile after two tries, also search `site:linkedin.com "Nick Geissler" "Repro"` on Google.
4. If still not found, stop and report the failure clearly in the manifest header.

## Step 2 — Capture Nick's role history

From the profile's Experience section, capture every role at Repro Construction (title, dates, location, description text). Also capture any prior roles for context. Put this in a section titled `## Role History` at the top of the output file.

## Step 3 — Navigate to Nick's posts

1. From the profile, click "Show all posts" or visit `https://www.linkedin.com/in/<handle>/recent-activity/all/` directly.
2. Switch the activity filter to "Posts" (not Comments, not Reactions).

## Step 4 — Scroll carefully and collect every post

LinkedIn aggressively rate-limits and throttles scraping. Follow these rules:

- Scroll in small increments (about one viewport at a time).
- Pause 3–5 seconds between scrolls to let content load and to avoid triggering throttling.
- Do not rapid-click or batch-open posts.
- If LinkedIn shows a CAPTCHA, throttle warning, or "unusual activity" notice, stop scrolling, wait 60 seconds, then resume more slowly. If it persists, stop and report what you collected.

For each post you encounter, capture:

- Post date (as shown, e.g., "2y", "Mar 2024" — convert relative dates to approximate absolute dates based on today)
- Full caption / body text
- Project name if stated (e.g., "The Works Cafe Westford")
- Location if stated (city, state, street address)
- Brand if stated (Dunkin', Jersey Mike's, etc.)
- Direct URL to the post (click the post timestamp to get the permalink, then copy)
- URLs of every image attached to the post (right-click each image, copy image address — capture the highest-resolution URL available; LinkedIn often serves `media.licdn.com/...` URLs)
- Whether the post contains a video, time-lapse, or before/after sequence (note as `VIDEO`, `TIME-LAPSE`, or `BEFORE/AFTER`)
- Any comments from named individuals that read like testimonials, endorsements, or operator praise (capture commenter name, their stated role/company if visible, and the comment text verbatim)

## Step 5 — Priority flagging

Flag with `[PRIORITY]` any post that mentions or visually depicts:

- The Works Cafe (especially Westford MA)
- Dunkin' (especially 74 Middlesex Ave, Somerville MA)
- Jersey Mike's
- Inspire Brands
- Wayback Burger
- Yella on the Water
- Zo Greek Cuisine
- Any address on Canal St, Salem MA
- Anything in Westford MA

Capture non-priority posts too — Repro's portfolio is broader than this list. Just don't flag them.

## Step 6 — Quote candidate flagging

Flag with `[QUOTE CANDIDATE]` any post or comment that contains a statement that could function as a testimonial or marketing quote — for example, a brand operator thanking Repro, praising the work, calling out a successful opening, or describing a smooth project. Capture the speaker's name and role verbatim.

## Step 7 — Output format

Produce a single markdown document. Structure:

```
# Nick Geissler LinkedIn Scrape — Repro Construction Portfolio
Profile URL: <url>
Scrape date: <today>
Total posts captured: <n>

## Role History
- Title | Company | Dates | Location | Description

## Project Manifest

| # | Project Name | Location | Brand | Post Date | Photo URLs | Caption | Post URL | Flags |
|---|---|---|---|---|---|---|---|---|
| 1 | ... | ... | ... | ... | url1; url2; url3 | full caption text | ... | [PRIORITY] [QUOTE CANDIDATE] |

## Quote Candidates (detail)
For each [QUOTE CANDIDATE]:
- Source post URL
- Speaker name + role/company
- Verbatim quote
- Context (was this a post body, a comment, a caption?)

## Notes / Gaps
- Anything unreadable, blocked, or skipped
```

Use `;` to separate multiple photo URLs in the Photo URLs cell. If a caption contains pipe characters, escape them as `\|` so the table doesn't break. If a cell is unknowable, write `—` (em dash). If text exists but is unreadable, write `[UNREADABLE]`.

## Step 8 — Hard rules

- Do NOT fabricate. If a project name, location, brand, or date isn't explicitly stated or clearly visible, write `—` or `[UNREADABLE]`. Never guess.
- Do NOT download images — capturing the URL is sufficient. Mike will right-click and save later.
- Do NOT include posts that are just reshares of other people's content unless Nick added substantive commentary about a Repro project.
- Do NOT include private posts, sponsored content, or "Sign in to view" content.
- Do NOT skip posts because they seem off-topic. Capture everything Nick personally posted; flag selectively.
- If you hit the bottom of his activity feed, note "End of feed reached" in the Notes section. If you stopped early due to throttling, note that too with the approximate scroll depth.

## Step 9 — Deliver

Output the complete markdown document as your final response. Do not summarize or truncate the manifest — return the full table. If the manifest is very long, that's expected and correct.
