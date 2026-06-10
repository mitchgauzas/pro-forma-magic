# Pro Forma Magic — Project Context for Claude

## What This Is
A static HTML/CSS marketing website for **Pro Forma Magic Inc.**, a real estate investment analysis SaaS platform. Built by Mitch Gauzas, Commercial REALTOR® licensed since 2005, based in Ottawa, Canada.

---

## Company Details
- **Legal name:** Pro Forma Magic Inc.
- **Founder:** Mitch Gauzas
- **Email:** support@proformamagic.com
- **LinkedIn:** linkedin.com/in/mitchgauzas
- **Phone:** 1-613-302-5752
- **Address:** 2 Barbara Ann Private, Ottawa, Ontario, Canada K2C 3V2
- **Copyright year:** 2026

---

## Product & Pricing
- **Model:** Annual license — one-time fee per year, no monthly billing
- **Base price:** $299 CAD/year
- **Free trial:** 7 days, no credit card required
- **Cancellation:** Cancel anytime, access continues to anniversary date, no refund
- **International pricing:** PPP (Purchasing Power Parity) — price adjusts based on user's country relative to Canadian average income. Display in local currency. Currency detection via IP geolocation API (to be built on pricing page).
- **Payment processor:** Stripe (planned)

---

## Target Users
The platform is for anyone who works with real estate in any capacity:
- Buyers
- Sellers
- Brokers
- Property managers
- Appraisers
- Analysts
- Mortgage brokers
- Underwriters

**Copy guidelines:**
- Never say "your clients" — use "you", "any investment", "your situation"
- Do not make boastful or unquantifiable claims — this is a new platform
- Be inclusive of all user types, not just service providers
- Use "platform" (singular), not "tools" (plural)
- Oxford commas required throughout
- REALTOR® always has the registered trademark symbol

---

## Design Tokens (CSS Variables)
```css
--gold: #D4A030
--gold-btn: #C8922A
--gold-light: #E8A830
--dark: #0E0B06
--dark2: #1A1510
--dark3: #120f08       /* footer background */
--cream: #FAF7F0
--text: #2A2318
--muted: #6B5E4E
```

---

## Typography
- **Headings:** Cormorant Garamond (serif), loaded from Google Fonts
- **Body:** DM Sans (sans-serif), loaded from Google Fonts
- **Heading emphasis:** one or two `<em>` phrases per heading — italic, same colour as heading text. Emphasis should NOT repeat the pill label above it.

---

## Section Layout Pattern
Each alternating section uses CSS Grid full-bleed half/half:
```css
.section { display: grid; grid-template-columns: 1fr 1fr; min-height: 580px; }
```
- **Cream sections:** `#FAF7F0` background, text left, photo right
- **Gold sections:** `#C8922A` background, photo left, text right
- Mobile: photo always appears below text (`order:1` on text-col, `order:2` on photo-col)

---

## Page Section Order (index.html)
1. **Nav** — fixed, transparent, darkens on scroll (`.scrolled` class via JS)
2. **Hero** — full viewport, hero-home.jpg background, dark overlay
3. **S2 Smarter Analysis** — cream, pill: "Smarter Analysis"
4. **S3 Win More Business** — gold, pill: "Win More Business"
5. **S4 Investment Strategy** — cream, pill: "Investment Strategy", has CTA button
6. **S5 Property Types** — gold, pill: "Property Types"
7. **S6 Costs & Returns** — cream, pill: "Costs & Returns"
8. **S7 Investment Forecast** — gold, pill: "Investment Forecast"
9. **S8 Training Videos** — white `#ffffff`, centered layout
10. **S9 Google Reviews** — ⚠️ COMMENTED OUT — restore when real reviews collected
11. **S10 Founder/Team** — cream `#FAF7F0`, centered, single founder card
12. **S11 FAQ** — white `#ffffff`
13. **Footer** — dark `#120f08`

---

## Images (`/images/`)
| File | Used For |
|---|---|
| `home-img01.png` | Wordmark logo in nav (1327×265) |
| `logo.png` | Square icon 500×500 (not used in nav) |
| `hero-home.jpg` | Hero background |
| `sec2-historic-building.jpg` | S2 photo |
| `home-img02.jpg` | S3 photo |
| `sec4-investment-strategy.jpg` | S4 photo |
| `sec5-property-types.jpg` | S5 photo |
| `sec6-determine-costs.jpg` | S6 photo |
| `home-img03.jpg` | S7 photo |
| `sec8-training-video.jpg` | Training video thumbnail |
| `founder-headshot.jpg` | Mitch Gauzas headshot (600×600, center-cropped) |
| `home-img04/05.jpg` | Old team photos (unused, keep for reference) |
| `team-right.jpg` | Old team photo (unused, keep for reference) |

---

## Buttons
- **Hero CTA:** `.btn-hero-gold` — large pill, animated arrow rotates -45° on hover
- **Section CTA:** `.btn-gold` — standard pill, same arrow animation, `align-self:flex-start` to prevent stretching in flex column
- **Nav CTA:** `.btn-trial` — smaller version of same style
- **Arrow:** SVG diagonal arrow inside rounded square background `rgba(255,255,255,.22)`

---

## Social Icons
All SVG inline icons in footer: Instagram, LinkedIn (mitchgauzas), YouTube, TikTok, Facebook, X (Twitter). Hover colour: `var(--gold)`.

---

## Pages Built
- `index.html` — homepage ✅
- `pricing.html` — PPP currency detection, START FREE TRIAL ✅
- `referral.html` — info-only (no action buttons on public page) ✅
- `faq.html` — live search, accordion, 6 categories ✅
- `video-library.html` — filter tabs, sort, placeholders ✅
- `terms.html` — Terms & Conditions + Privacy Policy toggle ✅

## Pages Pending
- `features.html` — shell exists, not designed yet
- `samples.html`
- `schedule-demo.html`

---

## Dashboard — Referral Page (backlog for post-launch)

When the user has subscribed and designs are provided, build the dashboard referral page with:

### Referral Program (10% commission):
- **Generate Referral Link button** — visible to all subscribers, but INACTIVE during free trial
  - Free trial users who click it see a modal: "Become a paid subscriber to activate your referral link."
  - Active paid subscribers can generate and copy their personal referral link
- **Banking email field** — for Interac e-Transfer payouts

### Affiliate Program (15% of sales):
- **Become an Affiliate button** — links to affiliate application/contact flow (details TBD)

### E-Transfer Payment Note (both cards):
- "Commission payments are made via Interac e-Transfer. Availability varies by country. Where unavailable, Pro Forma Magic Inc. will arrange an alternative electronic payment method."

### Trial user pop-up copy:
- Heading: "Paid Subscription Required"
- Body: "Activate your referral link by becoming a paid subscriber. Your referral link will be ready as soon as your subscription is active."
- CTA: "Start Subscription"

### Rules:
- Referral link only generates after first payment clears
- Commission paid when referred user completes first payment (not on free trial sign-up)
- Referral also receives 10% discount on their first year

---

## Pricing Page Notes (when building)
- Show $299 CAD as baseline
- Use IP geolocation API (e.g. ipapi.co) to detect country on page load
- Map country → PPP-adjusted price in local currency
- Note on page: "Available in your local currency — pricing reflects your market"
- Stripe for payment processing
- Annual license only — no monthly option

---

## Git
- **Repo:** github.com/mitchgauzas/pro-forma-magic
- **Active branch:** `website-homepage`
- **Server:** `python3 serve.py` on port 8080 (see `.claude/launch.json`)

---

## Design Reference
- PDF design file: `/Users/mitchgauzas/Downloads/homepage-design.pdf`
- Rendered pages: `/Users/mitchgauzas/Downloads/design-pages/page-1.png` through `page-10.png`
- Additional designs uploaded to Google Drive → "Home Page Design" folder
