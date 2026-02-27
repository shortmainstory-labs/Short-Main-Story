# Short Main Story — Platform Build & Deploy Task

## For: Claude in Cursor
## Goal: Build a deployable website platform and publish it to the web

---

## PROJECT OVERVIEW

**Short Main Story** is a safety intelligence platform for families — run by a solo founder. It combines:
1. **4 interactive safety games** (already built as standalone HTML files)
2. **A landing page** (already built, needs integration)
3. **Safety intelligence feed** (Telegram + Newsletter — setup instructions)
4. **Future tools** (Scam Shield, SMS Invest — placeholder pages for now)

The platform should be deployed as a **static website on Netlify** (free tier).

---

## WHAT ALREADY EXISTS (Files to Include)

These HTML files are ALREADY BUILT and should be placed in the project root:

| File | Description |
|------|-------------|
| `index.html` | Landing page (rename from `sms-labs-landing.html`) |
| `sms-detective-game.html` | Game 1: SMS Detective — spot scam texts |
| `street-smart-game.html` | Game 2: Street Smart — stranger danger training |
| `ai-defender-game.html` | Game 3: AI Defender — cyber crime investigation |
| `free-mind-game.html` | Game 4: Free Mind — digital wellness & addiction awareness |

**IMPORTANT:** These files are standalone HTML (no framework, no build step). They include all CSS and JS inline. Just serve them as-is.

---

## PROJECT STRUCTURE TO CREATE

```
short-main-story/
├── index.html                    ← Landing page (from sms-labs-landing.html)
├── sms-detective-game.html       ← Game 1 (already built)
├── street-smart-game.html        ← Game 2 (already built)
├── ai-defender-game.html         ← Game 3 (already built)
├── free-mind-game.html           ← Game 4 (already built)
├── about.html                    ← NEW: About the founder page
├── subscribe.html                ← NEW: Subscribe / join page
├── 404.html                      ← NEW: Custom 404 page
├── robots.txt                    ← SEO
├── sitemap.xml                   ← SEO
├── netlify.toml                  ← Netlify configuration
├── _redirects                    ← Netlify redirects
├── assets/
│   └── favicon.svg               ← Simple shield favicon
└── README.md                     ← Project documentation
```

---

## TASK 1: Create `netlify.toml`

```toml
[build]
  publish = "."

[[headers]]
  for = "/*"
  [headers.values]
    X-Frame-Options = "DENY"
    X-Content-Type-Options = "nosniff"
    Referrer-Policy = "strict-origin-when-cross-origin"
    Content-Security-Policy = "default-src 'self' 'unsafe-inline' 'unsafe-eval' https://fonts.googleapis.com https://fonts.gstatic.com https://cdnjs.cloudflare.com; img-src 'self' data: https:; font-src 'self' https://fonts.gstatic.com"

[[headers]]
  for = "/*.html"
  [headers.values]
    Cache-Control = "public, max-age=0, must-revalidate"

[[headers]]
  for = "/assets/*"
  [headers.values]
    Cache-Control = "public, max-age=31536000, immutable"
```

---

## TASK 2: Create `_redirects`

```
# Netlify redirects
# Clean URLs
/games      /index.html#games      200
/tools      /index.html#tools      200
/schools    /index.html#schools    200

# Old SMS Labs URLs (in case anyone has them)
/sms-labs-landing.html  /  301
```

---

## TASK 3: Create `robots.txt`

```
User-agent: *
Allow: /

Sitemap: https://shortmainstory.com/sitemap.xml
```

---

## TASK 4: Create `sitemap.xml`

```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemapschemas.org/sitemap/0.9">
  <url>
    <loc>https://shortmainstory.com/</loc>
    <changefreq>weekly</changefreq>
    <priority>1.0</priority>
  </url>
  <url>
    <loc>https://shortmainstory.com/sms-detective-game.html</loc>
    <changefreq>monthly</changefreq>
    <priority>0.8</priority>
  </url>
  <url>
    <loc>https://shortmainstory.com/street-smart-game.html</loc>
    <changefreq>monthly</changefreq>
    <priority>0.8</priority>
  </url>
  <url>
    <loc>https://shortmainstory.com/ai-defender-game.html</loc>
    <changefreq>monthly</changefreq>
    <priority>0.8</priority>
  </url>
  <url>
    <loc>https://shortmainstory.com/free-mind-game.html</loc>
    <changefreq>monthly</changefreq>
    <priority>0.8</priority>
  </url>
  <url>
    <loc>https://shortmainstory.com/about.html</loc>
    <changefreq>monthly</changefreq>
    <priority>0.6</priority>
  </url>
  <url>
    <loc>https://shortmainstory.com/subscribe.html</loc>
    <changefreq>monthly</changefreq>
    <priority>0.7</priority>
  </url>
</urlset>
```

---

## TASK 5: Create `about.html`

Create a clean, warm "About the Founder" page. Design should match the landing page aesthetic (Fraunces + DM Sans fonts, warm editorial feel).

### Content for about.html:

**Hero section:**
- "One Founder. Real Voice. No BS."
- Subtitle: "Short Main Story is built by one person who takes responsibility for everything — the quality, the honesty, and the trust."

**The Story section:**
- "I'm 45. Father. Master of Sport. Full-time employee building this platform on evenings and weekends because my family needs it — and yours does too."
- "I built these safety games because I couldn't find anything that actually WORKS. Not boring pamphlets. Not fear-based lectures. Real interactive training where parents and kids practice TOGETHER."
- "I started with scam detection (SMS Detective), then stranger danger (Street Smart), then cybercrime investigation (AI Defender), then digital wellness (Free Mind). Each game exists because I saw a real threat and thought: my family needs to be prepared."

**The Promise section:**
- "I only recommend what I actually use"
- "I earn money honestly and tell you when I do"
- "Safety information is always free — lifesaving knowledge is never behind a paywall"
- "If a company offers me money to recommend a bad product, I say no and tell you why"
- "This is my life's work — not a quick exit, not a trend"

**Why Trust Me section:**
- 🏅 Master of Sport, 45, still training — I walk the talk on health
- 🧠 I built every game myself — I understand the threats deeply
- 👨‍👧 I'm a parent — this isn't business, it's personal
- 💼 I work full-time — I'm building this because I care, not because I need to

**Contact:**
- Email: hello@shortmainstory.com
- Telegram: link to channel
- Newsletter: link to subscribe

**Design notes:**
- Use same CSS variables as landing page
- Same fonts: Fraunces (display), DM Sans (body), JetBrains Mono (mono)
- Warm, personal feel — this is NOT a corporate "about us" page
- Keep it honest and human
- Navigation should link back to index.html

---

## TASK 6: Create `subscribe.html`

A simple page with 3 subscription options:

1. **Telegram Channel** (primary) — Join button linking to t.me/shortmainstory (placeholder URL)
2. **Weekly Email Digest** — "The Safety Forecast" — embed a Beehiiv or Substack signup form (use placeholder for now)
3. **WhatsApp Channel** — "Coming Soon" badge

### Content:
- "Choose how you want your safety intelligence delivered"
- "No spam. No data selling. Just honest safety news, research, and predictions."
- "AI researches. I review. You get what matters."
- Show example messages (from the landing page intel section)

**Design:** Match landing page. Clean, warm, 3-column layout for the options.

---

## TASK 7: Create `404.html`

Simple, friendly 404 page:
- "Oops! This page doesn't exist."
- "But while you're here — did you know 1 in 3 people can't spot a scam text?"
- Button: "Play SMS Detective" → links to sms-detective-game.html
- Button: "Go Home" → links to index.html

---

## TASK 8: Create `assets/favicon.svg`

Simple SVG shield icon:

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32">
  <path d="M16 2L4 7v8c0 7.73 5.12 14.96 12 17 6.88-2.04 12-9.27 12-17V7L16 2z" fill="#1A1A2E"/>
  <path d="M16 5L7 9v6c0 6.19 3.84 11.97 9 13.6 5.16-1.63 9-7.41 9-13.6V9L16 5z" fill="#E94560"/>
  <text x="16" y="21" text-anchor="middle" fill="white" font-size="12" font-weight="bold" font-family="sans-serif">S</text>
</svg>
```

---

## TASK 9: Update `index.html` (Landing Page)

The landing page needs these small fixes:
1. Add `<link rel="icon" href="/assets/favicon.svg" type="image/svg+xml">` to `<head>`
2. Add link to `about.html` in the footer
3. Make sure all game links point to correct filenames
4. Update subscribe buttons to link to `subscribe.html`
5. Update navigation to include "About" link

---

## TASK 10: Create `README.md`

```markdown
# Short Main Story

Safety intelligence platform for families. Interactive games, honest recommendations, real-time alerts.

## Live Site
https://shortmainstory.com

## Structure
- `index.html` — Landing page
- `sms-detective-game.html` — Game: Spot scam texts
- `street-smart-game.html` — Game: Stranger danger training
- `ai-defender-game.html` — Game: Cyber crime investigation
- `free-mind-game.html` — Game: Digital wellness
- `about.html` — About the founder
- `subscribe.html` — Join Telegram / Newsletter

## Tech Stack
- Pure HTML/CSS/JS (no framework, no build step)
- Hosted on Netlify (free tier)
- Fonts: Google Fonts (Fraunces, DM Sans, JetBrains Mono)

## Deployment
Push to GitHub → auto-deploys via Netlify.

## Contact
hello@shortmainstory.com
```

---

## DEPLOYMENT INSTRUCTIONS

### Step 1: GitHub Repository
1. Create a new GitHub repo called `short-main-story`
2. Push all files to main branch

### Step 2: Netlify Deployment
1. Go to https://app.netlify.com
2. Click "Add new site" → "Import an existing project"
3. Connect your GitHub account
4. Select the `short-main-story` repository
5. Build settings:
   - **Build command:** (leave empty — no build needed)
   - **Publish directory:** `.` (root)
6. Click "Deploy"

### Step 3: Custom Domain (Optional)
1. Buy `shortmainstory.com` on Namecheap, Google Domains, or Cloudflare (~$12/year)
2. In Netlify: Settings → Domain Management → Add custom domain
3. Follow Netlify's DNS instructions
4. SSL is auto-enabled (free)

### Step 4: Verify
- Visit your Netlify URL (e.g., `short-main-story.netlify.app`)
- Test all game links work
- Test navigation
- Test mobile responsiveness
- Check 404 page works

---

## FUTURE ADDITIONS (Not for now)

These are planned but NOT needed for launch:

| Feature | When | Notes |
|---------|------|-------|
| Telegram Bot + Channel | Week 2 | Create @ShortMainStory bot via @BotFather |
| Beehiiv Newsletter | Week 2 | Free tier, up to 2,500 subscribers |
| n8n AI Pipeline | Month 1 | Self-hosted on €5/month VPS |
| Scam Shield tool | Month 3+ | Interactive web tool |
| SMS Invest alerts | Month 3+ | Telegram bot + web dashboard |
| Premium membership | Month 6+ | Stripe integration |
| School dashboard | Month 6+ | Teacher login + progress tracking |

---

## DESIGN SYSTEM REFERENCE

All pages should use these consistent styles:

### Colors
```css
--ink: #1A1A2E;       /* Primary text */
--paper: #FAFAF8;     /* Background */
--fire: #E94560;      /* Accent / CTA */
--ocean: #3A86FF;     /* Links / info */
--forest: #06D6A0;    /* Success / positive */
--violet: #8338EC;    /* Premium / special */
--sun: #F5A623;       /* Warnings / highlights */
--dim: #6B7280;       /* Secondary text */
--muted: #9CA3AF;     /* Tertiary text */
```

### Fonts
```css
/* Display headings */
font-family: 'Fraunces', serif;

/* Body text */
font-family: 'DM Sans', sans-serif;

/* Code / labels */
font-family: 'JetBrains Mono', monospace;
```

### Google Fonts Import
```html
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;0,9..40,600;0,9..40,700;0,9..40,800;0,9..40,900;1,9..40,400&family=Fraunces:ital,opsz,wght@0,9..144,300;0,9..144,500;0,9..144,700;0,9..144,900;1,9..144,400&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
```

### Shared CSS Variables (Include in every page)
```css
:root {
  --ink:#1A1A2E; --ink2:#16213E; --paper:#FAFAF8; --warm:#F8F4EF; --cream:#FFF8E8;
  --fire:#E94560; --fire2:rgba(233,69,96,0.06);
  --ocean:#3A86FF; --ocean2:rgba(58,134,255,0.06);
  --forest:#06D6A0; --forest2:rgba(6,214,160,0.06);
  --violet:#8338EC; --violet2:rgba(131,56,236,0.06);
  --sun:#F5A623;
  --dim:#6B7280; --muted:#9CA3AF; --border:rgba(0,0,0,0.05);
  --shadow-sm:0 1px 3px rgba(0,0,0,0.04);
  --shadow-md:0 4px 20px rgba(0,0,0,0.06);
}
```

---

## CRITICAL NOTES FOR CURSOR/CLAUDE

1. **NO FRAMEWORKS.** This is pure HTML/CSS/JS. No React, no Next.js, no Vite. Just files.
2. **NO BUILD STEP.** Everything serves directly from the file system.
3. **ALL CSS IS INLINE** in each HTML file (in `<style>` tags). No external CSS files.
4. **ALL JS IS INLINE** in each HTML file (in `<script>` tags). No external JS files.
5. **The game files are COMPLETE** — do not modify them unless specifically asked.
6. **Mobile responsive** — every page must work on phones. Use `clamp()` for font sizes.
7. **Warm, editorial aesthetic** — NOT corporate, NOT startup-y. Think: independent magazine for families.
8. **Scroll reveal animations** — use IntersectionObserver for `.rv` class elements.

---

## SUMMARY: WHAT TO DO

1. ✅ Create project folder `short-main-story/`
2. ✅ Copy in the 5 existing HTML files (4 games + landing page renamed to index.html)
3. ✅ Create `netlify.toml`, `_redirects`, `robots.txt`, `sitemap.xml`
4. ✅ Create `about.html` (founder story page)
5. ✅ Create `subscribe.html` (Telegram + newsletter signup)
6. ✅ Create `404.html` (friendly error page)
7. ✅ Create `assets/favicon.svg`
8. ✅ Update `index.html` with favicon, about link, subscribe links
9. ✅ Create `README.md`
10. ✅ Init git repo, push to GitHub
11. ✅ Deploy to Netlify
12. ✅ Test everything

**Estimated time for Claude in Cursor: 30-60 minutes.**
**Estimated time for you to deploy: 15 minutes (GitHub + Netlify clicks).**
