# Cleanup Report — Outreach Assets

Scope: clean up existing outreach assets by replacing placeholder emails, standardizing pricing to INR, reviewing sample CSVs, and aligning repository URLs.

---

## Files Changed

### 1. `outreach_package/email_template.html`
- Replaced `mailto:hello@example.com` with `mailto:sasidharmopuru@gmail.com`
- Updated GitHub link to `https://github.com/Sasireddy001/Earn/tree/earn/InstantTools/website-contact-scraper`

### 2. `outreach_package/sales_sheet.md`
- Replaced `$` pricing with INR:
  - Starter: ₹2,500
  - Growth: ₹10,000
  - Scale: ₹25,000
  - Enterprise: ₹50,000
- Removed add-ons (`$25`, `$50`, `$30`) to match the four-tier pricing
- Added payment/delivery terms: `100% advance via UPI or bank transfer. CSV delivered within 24 hours of payment.`
- Updated GitHub link to canonical `Earn` repo path

### 3. `outreach_package/landing_page_design.md`
- Replaced `$` pricing with the same four INR tiers
- Added `Enterprise` tier
- Added payment/delivery terms

### 4. `outreach_package/REPLY_PLAYBOOK.md`
- Updated the `Do you have references?` response GitHub link to canonical `Earn` repo path

### 5. `outreach_package/TRUST_IMPROVEMENT_REPORT.md`
- Updated placeholder email example from `sasidhar.mopuru@email.com` to `sasidharmopuru@gmail.com`

### 6. `outreach_package/EMAIL_IMPROVEMENT_NOTES.md`
- Converted recommended pricing table to INR only, removed `$ approx` column

### 7. `website-contact-scraper/README.md`
- Updated `git clone` URL from `https://github.com/Sasireddy001/website-contact-scraper.git` to `https://github.com/Sasireddy001/Earn.git`
- Adjusted install/run commands to use `Earn` repo root and `website-contact-scraper/` subpath

### 8. `sample_packages/ecommerce_local_business_sample.csv`
- Added `data_status` column: `synthetic` for all rows
- Added `disclaimer` column: `Sample data for demonstration. Verify before use.`

### 9. `sample_packages/dental_clinic_sample.csv`
- Added `data_status` column: `synthetic` for all rows
- Added `disclaimer` column: `Sample data for demonstration. Verify before use.`

### 10. `sample_packages/real_estate_builder_sample.csv`
- Added `data_status` column: `synthetic` for all rows
- Added `disclaimer` column: `Sample data for demonstration. Verify before use.`

---

## Inconsistencies Fixed

| Inconsistency | Fix |
|---|---|
| Placeholder email `hello@example.com` in CTA | `sasidharmopuru@gmail.com` |
| `$` pricing in `sales_sheet.md` and `landing_page_design.md` | All prices now in INR (₹2,500 / ₹10,000 / ₹25,000 / ₹50,000) |
| Mixed tier structures (3 tiers with add-ons vs 4 tiers) | Aligned to four-tier INR structure across assets |
| GitHub links pointing to `Sasireddy001/website-contact-scraper` | Now point to `Sasireddy001/Earn/tree/earn/InstantTools/website-contact-scraper` where the README lives |
| Sample CSVs had no source/provenance marking | Added `data_status` and `disclaimer` columns to all outreach sample CSVs |
| No payment/delivery terms in sales sheet or landing page | Added `100% advance via UPI or bank transfer. CSV delivered within 24 hours of payment.` |

---

## Remaining Trust Gaps

These still need attention but were not part of the cleanup scope:

1. **No LinkedIn profile link** in the email signature or README footer.
2. **No client testimonials** or `trusted by` social proof anywhere.
3. **No screenshots** in the README, sales sheet, or landing page (still placeholders).
4. **No portfolio photo** or Accenture-focused bio on the portfolio page.
5. **No privacy / data-sourcing statement** in the email body or sales sheet.
6. **Sample phone numbers are synthetic** (`+91 40 1234 5678` style). They should be replaced with real numbers or omitted.
7. **Product README is still inside `Earn/InstantTools/website-contact-scraper/`**, not a standalone `website-contact-scraper` repo root.
8. **`agency_outreach_campaign.md` still uses `Hi there,`** and attaches the e-commerce sample to B2B agencies.
9. **`email_template.html` sample table shows only URL/Email/Phone**, not LinkedIn, Instagram, title, or description.
10. **`subject_lines_and_copy.md` plain-text email copy still lacks a P.S. and a soft price anchor.**

---

## Canonical References Now in Use

- **Email:** `sasidharmopuru@gmail.com`
- **Product pricing:** ₹2,500 / ₹10,000 / ₹25,000 / ₹50,000
- **GitHub product path:** `https://github.com/Sasireddy001/Earn/tree/earn/InstantTools/website-contact-scraper`
- **Sample data status:** `synthetic` with `Sample data for demonstration. Verify before use.` disclaimer
