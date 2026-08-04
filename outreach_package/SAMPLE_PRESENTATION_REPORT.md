# Sample Presentation Report — Outreach Assets

Scope: review how the free sample is presented and identify what weakens it. No new products or assets are created; only improvement notes for existing files.

---

## 1. Current Sample Assets

- `sample_packages/Sample_B2B_Prospect_Data.csv` — 3 e-commerce / local business rows
- `sample_packages/Sample_Dental_Lead_Data.csv` — 3 dental clinic rows
- `sample_packages/Sample_RealEstate_Contacts.csv` — 3 real-estate builder rows
- `email_template.html` — 3-row sample table (URL, Email, Phone)
- `sales_sheet.md` — sample `What You Get` table with a real-estate example
- `README.md` — sample output from `github.com/about` and `vercel.com/contact`

---

## 2. Weaknesses

### A. Phone numbers look fake

- **Issue:** Sample CSVs contain numbers like `+91 40 1234 5678`, `+91 80 2345 6789`, and `+91 40 9876 5432`. These are clearly placeholder sequences, not real business numbers.
- **Why it matters:** Prospects will immediately question whether the scraper can find real contacts or if the data is made up.
- **Fix:** Replace placeholder phone numbers with real numbers from the actual websites, or remove the phone column from the sample CSVs if real numbers are not available. Showing three accurate emails is better than showing three fake phones.

### B. Only 3 rows per CSV

- **Issue:** Each sample CSV has only 3 rows. That is not enough to prove the tool works at scale.
- **Why it matters:** A buyer cannot judge coverage, error rate, or formatting from three rows.
- **Fix:** Expand each sample to 10 rows minimum, or create a single `master_sample.csv` with 12-15 rows across 2-3 verticals. Show breadth.

### C. Same attachment for every agency

- **Issue:** `agency_outreach_campaign.md` attaches `Sample_B2B_Prospect_Data.csv` to every prospect, including B2B lead-gen agencies like OUTRIVA and BuzzLead. A B2B agency does not care about local boutiques and grocery stores.
- **Why it matters:** Irrelevant samples make the sender look lazy and reduce perceived fit.
- **Fix:** Map the right sample to the right agency type:
  - B2B lead-gen / demand-gen / appointment-setting agencies → `sample_packages/b2b_saas_sample.csv` (create from existing `Sample_RealEstate_Contacts.csv` if no better file exists, or re-label)
  - Local SEO agencies → `Sample_Dental_Lead_Data.csv` or `Sample_RealEstate_Contacts.csv`
  - E-commerce / DTC agencies → `Sample_B2B_Prospect_Data.csv`
  - If a vertical-specific sample does not exist, send the `Sample_RealEstate_Contacts.csv` because real estate is closest to B2B local sales.

### D. No sample provenance note

- **Issue:** The email and sales sheet show sample data but never say where it came from. Prospects may think it is fabricated.
- **Why it matters:** Transparency is the core value proposition (`every row links back to the source URL`). The sample itself should prove this.
- **Fix:** Add a one-line caption above or below the sample table: `Sample scraped from live public websites — each row includes the source URL.`

### E. Email template table is too narrow

- **Issue:** The HTML email shows only `URL`, `Email`, and `Phone` columns. It hides LinkedIn, Facebook, Instagram, title, and description — the features that differentiate the scraper.
- **Why it matters:** The email sample does not sell the full value of the output.
- **Fix:** Add one more row to the email table showing a LinkedIn and Instagram column, or include a second small table titled `Also extracts social links and page metadata`.

### F. No before/after frame

- **Issue:** The sample is just a table. It does not contrast the old way (manual copy-paste) with the new way (CSV in seconds).
- **Why it matters:** Buyers need to feel the pain relief. A table alone does not show saved hours.
- **Fix:** Add a one-sentence caption under the sample table: `This CSV was generated in under 2 minutes from a 3-URL list. No manual work.`

### G. README sample uses GitHub and Vercel

- **Issue:** The README `Sample Output` uses `github.com/about` and `vercel.com/contact`, which are not relatable to agency buyers. They also do not show emails or phones, only social links.
- **Why it matters:** The README is a buyer-facing page. It should show the exact output an agency would receive for their ICP.
- **Fix:** Replace the README sample output with the `Sample_RealEstate_Contacts.csv` or `Sample_Dental_Lead_Data.csv` data. Show real business contacts, not big-tech about pages.

### H. No visual sample

- **Issue:** There are no screenshots of the CSV opened in Excel / Google Sheets.
- **Why it matters:** Visual proof is faster to trust than a text CSV.
- **Fix:** Take a screenshot of one of the sample CSVs opened in Excel or Google Sheets and save it as `assets/sample-csv-screenshot.png`. Replace the `Sample CSV screenshot` placeholder in `landing_page_design.md` and `README.md` with this file once it exists. (This is a screenshot, not a new product asset.)

---

## 3. Recommended Sample Strategy by Prospect Type

| Agency type | Best sample to attach | Why |
|---|---|---|
| B2B lead-gen | Real-estate builder sample, re-labeled as `b2b_local_business_sample.csv` | Shows corporate-style contacts and real estate decision-makers |
| Demand-gen | Real-estate builder sample or a SaaS/tech services CSV | High-ticket B2B contacts |
| Appointment setting | Dental clinic sample or real-estate builder sample | Decision-makers at local businesses |
| Local SEO | Ecommerce local business sample | Direct local business contacts |

If a perfectly aligned sample does not exist, use the closest one and add a one-line note: `This is a 3-row example from the [vertical] sector. I can run the same on your target ICP.`

---

## 4. Quick Fixes Ranked

| Priority | Fix | File to edit |
|---|---|---|
| P0 | Remove or replace fake phone numbers | `sample_packages/*.csv` |
| P0 | Attach the right sample per agency | `agency_outreach_campaign.md` |
| P1 | Expand sample to 10 rows or add provenance note | `sample_packages/*.csv`, `email_template.html` |
| P1 | Show social links in email sample | `email_template.html` |
| P2 | Add before/after caption | `email_template.html`, `sales_sheet.md` |
| P2 | Replace README sample with business contacts | `website-contact-scraper/README.md` |
| P3 | Add screenshot of CSV in spreadsheet | `landing_page_design.md`, `README.md` |

All fixes are within existing assets. No new product features or repositories are needed.
