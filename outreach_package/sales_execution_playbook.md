# Sales Execution Playbook — Website Contact Scraper

**Role:** Sales support only. No research, no new products, no new platforms.  
**Source files:** `agency_outreach_campaign.md`, `sales_sheet.md`, `sample_packages/*.csv`  
**Pricing (fixed):**
- ₹2,500 = 100 websites
- ₹10,000 = 500 websites
- ₹25,000 = 1,500 websites
- ₹50,000 = 1,500 websites + source code

---

## How to use this file

When a positive reply lands, follow the steps in order. Copy the relevant template, replace `[Prospect]` and `[Tier]` with real values, and send.

---

## 1. Positive Reply Triage

Classify the reply first:

| Reply type | What to send | Go to section |
|---|---|---|
| "Send me a sample" | Sample recommendation + sample delivery email | 2 + 8 |
| "What is the pricing?" | Pricing email | 4 |
| "Send a proposal" | Full proposal | 5 |
| "This is too expensive" | Negotiation reply | 6 |
| "Let's do it" / "Invoice" | Invoice text + payment instructions | 7 |
| "Where is my file?" | Delivery email | 8 |

---

## 2. Best Sample CSV Recommendation

Use the sample that feels closest to the prospect's target market. If you do not know, default to `Sample_B2B_Prospect_Data.csv` because it is the most generic and looks like a real local business list.

| Agency type | Recommended sample CSV | Why |
|---|---|---|
| B2B Lead Generation | `sample_packages/Sample_B2B_Prospect_Data.csv` | Shows complex B2B contact extraction |
| Demand Generation | `sample_packages/Sample_B2B_Prospect_Data.csv` | Versatile, looks like campaign data |
| Appointment Setting | `sample_packages/Sample_B2B_Prospect_Data.csv` | Local service businesses with phones |
| Local SEO | `sample_packages/Sample_B2B_Prospect_Data.csv` | Local business data with URLs and phones |
| Unknown / generic | `sample_packages/Sample_B2B_Prospect_Data.csv` | Safe default, no niche mismatch |

---

## 3. First Positive-Reply Response Templates

### A. Prospect asks for a free sample

**Subject:** Re: [original subject]

Hi [First Name],

Thanks for the reply.

I will run the scraper on 50 websites from your target list and send the CSV within 24 hours. If you do not have a list handy, tell me the niche and city and I will generate one for the sample.

Please attach your target URL list or reply with:
- Niche / vertical
- Target location (optional)
- Email or phone preference (or both)

Best,  
Sasidhar Mopuru  
Data & AI Platform Engineer  
https://sasireddy001.github.io/Portfolio/

---

### B. Prospect asks for pricing

**Subject:** Re: [original subject]

Hi [First Name],

Here is the pricing for the Website Contact Scraper output:

- ₹2,500 — 100 websites
- ₹10,000 — 500 websites
- ₹25,000 — 1,500 websites
- ₹50,000 — 1,500 websites + full source code

Each deliverable is a clean CSV with emails, phones, LinkedIn, Facebook, Instagram, page titles, and meta descriptions.

Turnaround is 24-48 hours. Payment via UPI or bank transfer. I can start as soon as you confirm the tier.

Want a free 50-contact sample first?

Best,  
Sasidhar Mopuru

---

### C. Prospect asks for a proposal

**Subject:** Proposal — Website Contact Scraper for [Agency]

Hi [First Name],

As discussed, here is the proposal.

**Scope:** Website contact scraping for [Prospect]  
**Input:** List of target website URLs or niche/location criteria  
**Output:** CSV with URL, emails, phones, LinkedIn, Facebook, Instagram, title, description  
**Deliverable format:** `.csv` file, UTF-8, ready for CRM / sequencer import  
**Timeline:** 24-48 hours after payment / URL list receipt

**Pricing options:**

| Tier | Websites | Deliverable | Price |
|------|----------|-------------|-------|
| Starter | 100 | CSV | ₹2,500 |
| Growth | 500 | CSV | ₹10,000 |
| Scale | 1,500 | CSV | ₹25,000 |
| Enterprise | 1,500 | CSV + full Node.js source code | ₹50,000 |

**Terms:** 100% advance via UPI / bank transfer. Revisions included for missing or malformed rows in the delivered file.

Reply with the tier you prefer and I will share the invoice.

Best,  
Sasidhar Mopuru  
Data & AI Platform Engineer  
https://sasireddy001.github.io/Portfolio/

---

### D. Prospect says "This looks good / Let's talk"

**Subject:** Re: [original subject]

Hi [First Name],

Great. I can run the free 50-contact sample today. Just share:

1. 50 target URLs, or
2. One niche + one city and I will build the list

Once you see the CSV quality, we can lock in the tier that fits your volume.

Best,  
Sasidhar Mopuru

---

## 4. Pricing Email (standalone)

Use this when the only question is price.

**Subject:** Pricing — Website Contact Scraper

Hi [First Name],

Quick pricing for the Website Contact Scraper:

- ₹2,500 = 100 websites
- ₹10,000 = 500 websites
- ₹25,000 = 1,500 websites
- ₹50,000 = 1,500 websites + source code

Each price is a one-time fee. The CSV includes emails, phones, LinkedIn, Facebook, Instagram, page titles, and meta descriptions.

Turnaround: 24-48 hours.

Let me know which tier works and I will send the invoice.

Best,  
Sasidhar Mopuru

---

## 5. Full Proposal Template

Copy this into an email or save as `proposal_[prospect].md`.

```
PROPOSAL — WEBSITE CONTACT SCRAPER

Prepared for: [Prospect Name]
Prepared by: Sasidhar Mopuru
Date: [Date]

PROJECT OVERVIEW
Extract verified public contact data from a list of target websites and deliver it as a clean CSV ready for CRM / outreach import.

DELIVERABLES
- CSV file with one row per URL
- Columns: source URL, emails, phones, LinkedIn URL, Facebook URL, Instagram URL, page title, meta description
- Data extracted from live public websites only

PRICING OPTIONS

Starter     — 100 websites   — ₹2,500
Growth      — 500 websites   — ₹10,000
Scale       — 1,500 websites — ₹25,000
Enterprise  — 1,500 websites + source code — ₹50,000

TIMELINE
24-48 hours after receipt of target URL list and payment.

TERMS
- 100% advance payment via UPI or bank transfer
- One free revision for missing or malformed rows
- All data sourced from public-facing websites

NEXT STEP
Confirm the tier and reply with your target URL list. I will issue the invoice and begin work immediately.

CONTACT
Sasidhar Mopuru
Data & AI Platform Engineer
https://sasireddy001.github.io/Portfolio/
```

---

## 6. Negotiation Replies

### Objection: "Too expensive"

Hi [First Name],

I can reduce the scope to match your budget:

- ₹1,500 for 50 websites if you want to test quality first
- ₹7,500 for 350 websites instead of 500

Or take the 100-site tier for ₹2,500 and upgrade later.

Which option works?

Best,  
Sasidhar Mopuru

---

### Objection: "We only need emails, not phones/socials"

Hi [First Name],

I can deliver an emails-only CSV. Because the scraper still has to load the full page, the cost stays the same for the tier, but the file is cleaner for your use case.

If volume is low, the 100-site tier at ₹2,500 is the best fit.

Best,  
Sasidhar Mopuru

---

### Objection: "Can you do a smaller test for free?"

Hi [First Name],

Yes — the free 50-contact sample is the standard test. If you need a larger paid pilot, I can do 100 sites for ₹2,500 or 50 sites for ₹1,500.

Send the URLs and I will start the sample.

Best,  
Sasidhar Mopuru

---

### Objection: "We want source code but not at ₹50,000"

Hi [First Name],

The source-code license is bundled with the 1,500-site tier. If you do not need 1,500 sites, the best alternative is the 500-site CSV for ₹10,000 and I can sell the source code separately for ₹35,000.

Or start with the ₹25,000 tier and add the source code for an additional ₹25,000 later.

Best,  
Sasidhar Mopuru

---

### Objection: "We need exclusivity / resell rights"

Hi [First Name],

You can use the CSV for your clients and campaigns. If you want the source code for reselling as your own product, the Enterprise tier (₹50,000) includes full usage rights.

Let me know what you have in mind and I can adjust the terms.

Best,  
Sasidhar Mopuru

---

### Objection: "Your competitor charges less"

Hi [First Name],

No problem. If you can share the quote, I can either match the closest tier or beat it on volume. The scraper runs locally and produces source-linked CSVs, so the value is in clean, transparent data.

What tier were you comparing?

Best,  
Sasidhar Mopuru

---

## 7. Invoice Text

Use this as the body of an invoice email or invoice message. Replace bracketed fields.

**Subject:** Invoice — Website Contact Scraper for [Agency]

Hi [First Name],

Please find the invoice details below.

**Service:** Website Contact Scraper  
**Tier:** [Starter / Growth / Scale / Enterprise]  
**Websites:** [100 / 500 / 1,500]  
**Amount:** ₹[Amount]  
**GST:** [Nil / 18% if applicable]  
**Total:** ₹[Total]  
**Payment terms:** 100% advance  
**Payment method:** UPI or bank transfer  
**UPI ID:** [your UPI ID]  
**Bank details:** [Account number, IFSC, name]  

Once the payment is confirmed, I will begin the scrape and deliver the CSV within 24-48 hours.

Best,  
Sasidhar Mopuru

---

## 8. Delivery Email

Use this after payment and after the scrape is complete.

**Subject:** Delivered — Website Contact Scraper CSV for [Agency]

Hi [First Name],

Please find the deliverable attached.

**File:** [prospect]_scraped_contacts_[date].csv  
**Websites scraped:** [count]  
**Columns included:** URL, emails, phones, LinkedIn, Facebook, Instagram, page title, meta description  
**Rows with at least one email or phone:** [count]  

If any rows look off or you need a different format, reply and I will fix it in the same delivery window.

For future orders, the same tiers apply:
- ₹2,500 = 100 sites
- ₹10,000 = 500 sites
- ₹25,000 = 1,500 sites
- ₹50,000 = 1,500 sites + source code

Best,  
Sasidhar Mopuru  
Data & AI Platform Engineer  
https://sasireddy001.github.io/Portfolio/

---

## 9. Quick Objection Handling Cheat Sheet

| Objection | Reply |
|---|---|
| "No budget" | Offer the ₹1,500 / 50-site test or free 50-contact sample. |
| "We already use a tool" | Ours runs locally, no API credits, source-linked rows. Free sample to compare. |
| "Data quality?" | Send free 50-contact sample first. Revisions included for paid orders. |
| "Too slow?" | 24-48 hour turnaround. Priority delivery within 12 hours for +₹500. |
| "Can you scrape LinkedIn profiles?" | No. We only scrape public website contact pages and social links found on those pages. |
| "Is this legal?" | We extract publicly available data from public websites. No password-protected or private data. |

---

## 10. Pricing & Deal Math

| Tier | Price | Cost per site | Use case |
|---|---|---|---|
| Starter | ₹2,500 | ₹25 | Small test or one campaign |
| Growth | ₹10,000 | ₹20 | Medium campaign, 2-3 SDRs |
| Scale | ₹25,000 | ₹16.67 | Large campaign, agency resell |
| Enterprise | ₹50,000 | ₹33.33 + source | OEM / resell / internal tool |

**Minimum acceptable discount:** Do not go below ₹1,500 for 50 sites.  
**Recommended upsell:** From Starter → Growth if the prospect needs more than 100 sites.  
**Preferred close:** Growth tier at ₹10,000 — best price/value ratio.
