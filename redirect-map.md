# 301 Redirect Map — reproconstruction.com migration

**Purpose:** Preserve every link, bookmark, and Google index entry pointing to the current Divi/WordPress site after we cut over to the new site. Every line below is a permanent (HTTP 301) redirect from the old URL to its new home.

**When to apply:** During the cutover. Configure these in Vercel/Netlify (`_redirects` or `vercel.json`) or via `.htaccess` if we end up on a traditional host.

---

## Discovered current URLs (from May 12 crawl of reproconstruction.com)

| Current URL | What it is | New URL | Notes |
|---|---|---|---|
| `https://reproconstruction.com/` | Homepage | `https://reproconstruction.com/` | No redirect needed — replaced in place |
| `https://reproconstruction.com/?page_id=2` | Galleries | `https://reproconstruction.com/portfolio/` | Renamed for clarity |
| `https://reproconstruction.com/?page_id=1411` | Recent Projects | `https://reproconstruction.com/projects/` | Becomes the main projects index |
| `https://reproconstruction.com/?page_id=1281` | About Us / Team | `https://reproconstruction.com/about/` | |
| `https://reproconstruction.com/?page_id=1258` | Project: Revere / Nahant St | `https://reproconstruction.com/projects/nahant-st-revere-38-unit/` | Slug names the brand-relevant scope |
| `https://reproconstruction.com/?page_id=1520` | Project: Winchendon 49 Central | `https://reproconstruction.com/projects/winchendon-49-central/` | |
| `https://reproconstruction.com/?page_id=1576` | Project: Dunkin' Danvers 14-day | `https://reproconstruction.com/projects/dunkin-danvers-14-day/` | Flagship — high SEO/GEO value |
| `https://reproconstruction.com/?page_id=373` | Residential | `https://reproconstruction.com/residential/` | Drop / hide this redirect entirely IF Mark decides residential is dropped from positioning |
| `https://reproconstruction.com/?page_id=985` | Job Opportunities | `https://reproconstruction.com/careers/` | |
| `https://reproconstruction.com/?page_id=390` | Subcontractor Application | `https://reproconstruction.com/careers/subcontractors/` | |
| `https://reproconstruction.com/?page_id=133` | Contact | `https://reproconstruction.com/contact/` | |

---

## Likely additional pages to redirect (need a final crawl pre-launch)

The page IDs above came from links discovered via the homepage crawl. WordPress sites usually have more pages reachable only via direct URL or sitemap. Before launch:

1. Pull `https://reproconstruction.com/sitemap.xml` (or use a WP admin export) to enumerate every published page ID
2. For any page ID not in the table above, decide: redirect to closest match, redirect to homepage, or leave 404'd if it's truly orphaned content
3. Special attention to: blog posts, individual project gallery pages, any service-specific landing pages, any past press releases

---

## Vercel `vercel.json` format (drop-in)

```json
{
  "redirects": [
    { "source": "/", "destination": "/", "permanent": true },
    { "source": "/?page_id=2", "destination": "/portfolio/", "permanent": true },
    { "source": "/?page_id=1411", "destination": "/projects/", "permanent": true },
    { "source": "/?page_id=1281", "destination": "/about/", "permanent": true },
    { "source": "/?page_id=1258", "destination": "/projects/nahant-st-revere-38-unit/", "permanent": true },
    { "source": "/?page_id=1520", "destination": "/projects/winchendon-49-central/", "permanent": true },
    { "source": "/?page_id=1576", "destination": "/projects/dunkin-danvers-14-day/", "permanent": true },
    { "source": "/?page_id=373", "destination": "/residential/", "permanent": true },
    { "source": "/?page_id=985", "destination": "/careers/", "permanent": true },
    { "source": "/?page_id=390", "destination": "/careers/subcontractors/", "permanent": true },
    { "source": "/?page_id=133", "destination": "/contact/", "permanent": true }
  ]
}
```

## Netlify `_redirects` format (drop-in)

```
/?page_id=2          /portfolio/                                     301!
/?page_id=1411       /projects/                                      301!
/?page_id=1281       /about/                                         301!
/?page_id=1258       /projects/nahant-st-revere-38-unit/             301!
/?page_id=1520       /projects/winchendon-49-central/                301!
/?page_id=1576       /projects/dunkin-danvers-14-day/                301!
/?page_id=373        /residential/                                   301!
/?page_id=985        /careers/                                       301!
/?page_id=390        /careers/subcontractors/                        301!
/?page_id=133        /contact/                                       301!
```

---

## Post-cutover checklist

- [ ] Verify each redirect with `curl -I https://reproconstruction.com/?page_id=1576` → expect `HTTP/2 301` + `location: /projects/dunkin-danvers-14-day/`
- [ ] Submit new sitemap to Google Search Console
- [ ] Submit new sitemap to Bing Webmaster Tools (powers ChatGPT search)
- [ ] Spot-check Google's index for any straggling old URLs (`site:reproconstruction.com page_id` in Google)
- [ ] Verify Google Business Profile website link still works (should — points at `/`)
- [ ] Verify every social profile bio link still resolves (Facebook, Instagram, LinkedIn)
