# Landing Page Design — Website Contact Scraper

## Page goal
Turn visitors into sample requests and discovery calls.

---

## 1. Wireframe / Section Flow

```
┌─────────────────────────────────────────────────────────────┐
│  NAV  [Logo]  [Features] [How it works] [Pricing] [Get sample] │
├─────────────────────────────────────────────────────────────┤
│  HERO                                                       │
│  Headline                                                   │
│  Subhead                                                    │
│  [Primary CTA: Get free 50-contact sample]                  │
│  [Secondary link: View sample CSV]                          │
├─────────────────────────────────────────────────────────────┤
│  LOGO BAR — "Built for lead-gen, demand-gen, appointment    │
│  setting & local SEO agencies"                              │
├─────────────────────────────────────────────────────────────┤
│  PROBLEM                                                    │
│  3-column: Manual research / Wasted SDR time / Bad data     │
├─────────────────────────────────────────────────────────────┤
│  SOLUTION                                                   │
│  Large screenshot or terminal mockup: URL list → CSV output │
├─────────────────────────────────────────────────────────────┤
│  FEATURES                                                   │
│  6 feature cards in 3x2 grid                                │
├─────────────────────────────────────────────────────────────┤
│  SAMPLE CSV SCREENSHOT                                      │
│  Stylised CSV preview (placeholder for real screenshot)     │
├─────────────────────────────────────────────────────────────┤
│  HOW IT WORKS                                               │
│  3 steps: Paste URLs → Run scraper → Download CSV           │
├─────────────────────────────────────────────────────────────┤
│  PRICING                                                    │
│  3-tier card layout                                         │
├─────────────────────────────────────────────────────────────┤
│  CTA BANNER                                                 │
│  Final headline + email form                                │
├─────────────────────────────────────────────────────────────┤
│  FOOTER                                                     │
│  Links + copyright                                          │
└─────────────────────────────────────────────────────────────┘
```

---

## 2. Copy

### Nav
- Logo: **Website Contact Scraper**
- Links: Features, How it works, Pricing
- CTA: **Get free sample**

### Hero
**Headline:** Turn website URLs into enriched contact CSVs in one click.
**Subhead:** Extract emails, phones, LinkedIn, Facebook, Instagram, page titles, and meta descriptions from any list of websites. Built for lead-gen, demand-gen, appointment-setting, and local SEO agencies.
**Primary CTA:** Get a free 50-contact sample
**Secondary CTA:** See sample output

### Logo bar
**Text:** Built for agencies that live and die by the quality of their prospect lists.

### Problem
**Headline:** Manual contact research is slowing you down.
- **Time drain:** Your team opens dozens of websites every day.
- **Bad data:** Public databases are outdated, expensive, and full of stale contacts.
- **Lost focus:** Every hour spent copying data is an hour not spent selling.

### Solution
**Headline:** One command. One clean CSV.
**Body:** Upload a list of URLs. The scraper visits each website, pulls the public contact data, and returns a CSV you can import into any CRM or sequencing tool.

### Features
**Headline:** Everything you need to build prospect lists faster.
- **Email extraction** — captures contact and sales emails from text and mailto links.
- **Phone extraction** — finds local and international numbers.
- **Social links** — pulls LinkedIn, Facebook, Instagram, Twitter URLs.
- **Page metadata** — captures title and meta description for context.
- **Retry logic** — handles timeouts, redirects, and transient failures.
- **Local or cloud** — runs on your machine or server, no SaaS lock-in.

### Sample CSV screenshot
**Placeholder caption:** Sample output: website, emails, phones, and social links in a clean CSV.

### How it works
**Headline:** Prospect lists in three simple steps.
1. **Paste URLs** — Drop in a list of target websites or upload a CSV.
2. **Run the scraper** — One command processes hundreds of sites in minutes.
3. **Download the CSV** — Import into your CRM, outreach tool, or cold-email sequencer.

### Pricing
**Headline:** Simple, usage-based pricing.

- **Starter — $35**  
  100 websites scraped  
  CSV with emails, phones, socials  
  24-hour delivery

- **Growth — $75**  
  500 websites scraped  
  Source code included  
  One free revision

- **Scale — $150**  
  1,500 websites scraped  
  Source code + custom niche filters  
  Priority support

**CTA under cards:** Get a free 50-contact sample

### Final CTA banner
**Headline:** Stop copy-pasting. Start scaling.
**Subhead:** Get your free 50-contact sample and see the data quality for yourself.
**Form:** Email input + [Get free sample] button

### Footer
- © Sasidhar Mopuru. All rights reserved.
- Portfolio | GitHub | Contact

---

## 3. Layout

- **Container:** max-width `1200px`, centered, `16px` side padding on mobile.
- **Grid:** 12-column grid, `24px` gutter.
- **Hero:** two-column on desktop (text left, illustration/mockup right), single-column on mobile.
- **Features:** 3x2 grid on desktop, 2x3 on tablet, 1-column on mobile.
- **Pricing:** 3 cards side by side on desktop, stacked on mobile. Middle card highlighted with subtle shadow.
- **Spacing:** section padding `80px` desktop, `48px` mobile.
- **Border radius:** `8px` for cards and buttons, `6px` for inputs.

---

## 4. Colors

| Role | Hex | Use |
|------|-----|-----|
| Primary | `#2563EB` | Buttons, links, accents |
| Primary hover | `#1D4ED8` | Button hover |
| Background | `#FFFFFF` | Page background |
| Section alt | `#F9FAFB` | Alternate section backgrounds |
| Surface | `#F3F4F6` | Cards, inputs, code blocks |
| Text primary | `#111827` | Headings, body text |
| Text secondary | `#6B7280` | Captions, placeholders |
| Border | `#E5E7EB` | Dividers, card borders |
| Success | `#10B981` | Check marks, positive badges |

---

## 5. Typography

- **Font family:** `Inter, Segoe UI, Roboto, Helvetica, Arial, sans-serif`
- **Headings:**
  - H1: `48px / 700 / -0.02em` (hero)
  - H2: `32px / 700 / -0.015em` (section titles)
  - H3: `20px / 600` (card titles)
- **Body:** `16px / 400 / 1.6`
- **Caption / small:** `14px / 400 / 1.5`
- **Button:** `15px / 600`

---

## 6. Assets needed

- Hero mockup: terminal window or browser screenshot showing `URL list → CSV`
- Sample CSV screenshot: stylised table of 5 rows
- Favicon: simple `</>` or magnifying glass icon
