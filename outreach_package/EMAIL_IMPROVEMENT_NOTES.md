# Email Improvement Notes — Outreach Assets

Scope: review current email copy, subject lines, and pricing presentation. No new products or assets are created; only improvement recommendations for existing files.

---

## 1. Weak Messaging

### A. Greeting is too generic

- **Issue:** Most emails in `agency_outreach_campaign.md` and `subject_lines_and_copy.md` open with `Hi there,`. This is a cold-email spam signal.
- **Fix:** Use `Hi [First Name],` and require it to be filled before sending. If the first name is unknown, use `Hi [Agency] team,`.

### B. Feature-first opening

- **Issue:** The first paragraph is usually: `I noticed X is a B2B lead generation agency... I built a Website Contact Scraper that turns a list of URLs into a clean CSV with...` It lists features before the outcome.
- **Fix:** Lead with the buyer's outcome: `Want to stop your team opening prospect websites one by one?` Then introduce the scraper as the solution.

### C. CTA is passive

- **Issue:** `Want a free 50-contact sample for your target ICP?` is a yes/no question that is easy to ignore.
- **Fix:** Use a low-friction action CTA: `Reply with your target niche or 2-3 URLs and I will send the sample CSV today.`

### D. No differentiation from Apollo/ZoomInfo

- **Issue:** Only the long email body explicitly contrasts with paid databases. The short and medium versions do not answer `Why not use Apollo?`
- **Fix:** Add one sentence to the medium and short versions: `Unlike Apollo, every row links back to the live source URL — no per-contact fees.`

### E. No proof in the body

- **Issue:** The email says the scraper is `built for agencies` but provides no proof.
- **Fix:** Add one short proof line: `Used by agencies to build lists for outbound, demand-gen, and local SEO campaigns.` Or, once a job is complete, `Recently delivered 500 contacts for a [city] real-estate agency.`

### F. Subject lines can be stronger

- **Issue:** Some subject lines are weak or generic (`This changed how we think about contact data`, `A faster way to fill your SDR pipeline`).
- **Fix:** Prioritize subject lines that are specific and benefit-driven:
  - `Free 50-contact sample for [Agency]`
  - `Cut [vertical] prospect research by 80%`
  - `Stop paying ZoomInfo for public website data`

### G. No P.S. line

- **Issue:** The email ends without a P.S. line. A P.S. is one of the most-read parts of a cold email.
- **Fix:** Add a P.S. that reinforces the offer or removes risk: `P.S. No card or commitment required — just reply with a few URLs and I will run the sample.`

---

## 2. Weak Pricing Presentation

### A. Currency mismatch

- **Issue:** `agency_outreach_campaign.md` and `README.md` use ₹. `sales_sheet.md` and `landing_page_design.md` use $. A prospect who reads the email then clicks the sales sheet will see different prices.
- **Fix:** Choose one currency per campaign. For the current agency list (mostly global/US), convert ₹ to $ in `agency_outreach_campaign.md` or keep ₹ and update the sales sheet/landing page to ₹. Do not mix.

### B. No price anchoring

- **Issue:** The tiers are listed flat: ₹2,500 / ₹10,000 / ₹25,000 / ₹50,000. There is no `most popular` or `best value` badge.
- **Fix:** Highlight `Growth` (500 sites) as `Most popular for agencies` in the sales sheet and landing page.

### C. Pricing is missing from the email body

- **Issue:** The outreach email only says `free sample` and does not mention pricing. Prospects who are ready to buy may not reply because they do not know the cost.
- **Fix:** Add a soft price anchor in the medium/long body: `After the sample, a one-time build starts at ₹2,500 for 100 sites.`

### D. Payment and delivery terms are unclear

- **Issue:** No asset states `how to pay` or `when delivery happens`.
- **Fix:** Add one line to the email and sales sheet: `100% advance via UPI or bank transfer. CSV delivered within 24 hours of payment.`

### E. Add-ons are confusing

- **Issue:** `sales_sheet.md` lists add-ons (`Extra revision: $25`, `Custom niche filter: $50`, `Priority 12-hour delivery: $30`) that are not mentioned anywhere else. They create decision fatigue.
- **Fix:** Remove add-ons from the sales sheet or fold them into tiers. Simpler pricing converts faster.

### F. $ prices are too low and inconsistent with ₹

- **Issue:** $35 for 100 sites, $75 for 500 sites + source code. In ₹ terms, $35 ≈ ₹3,000, not ₹2,500. The $75 Growth tier includes source code, but in the README only the ₹50,000 Enterprise tier includes source code.
- **Fix:** Align tiers across all assets. Recommended single structure:

  | Tier | Count | Includes | Price |
  |---|---|---|---|
  | Starter | 100 | CSV | ₹2,500 |
  | Growth | 500 | CSV | ₹10,000 |
  | Scale | 1,500 | CSV | ₹25,000 |
  | Enterprise | 1,500 | CSV + source code | ₹50,000 |

### G. No monthly/retainer framing

- **Issue:** Pricing is one-time. For agencies that need ongoing lists, there is no retainer option mentioned.
- **Fix:** Add an optional retainer line to the sales sheet: `Need weekly lists? Ask about the monthly retainer.` This creates an upsell path.

---

## 3. Specific Edits to Make

### `email_template.html`

1. Replace `mailto:hello@example.com` with your real email.
2. Add LinkedIn link next to Portfolio and GitHub.
3. Replace `Hi there,` with `Hi [First Name],`.
4. Add a P.S. line under the signature.
5. Add `Sample scraped from live public websites` caption under the sample table.
6. Expand the sample table to show LinkedIn and Instagram columns.
7. Add one sentence of differentiation: `Unlike paid databases, every row links back to the source.`

### `subject_lines_and_copy.md`

1. Short version: open with a pain question, then the solution.
2. Medium version: add `No per-contact fees — every row links back to the source URL.`
3. Long version: keep, but add a `P.S.` line.
4. Add `Price anchoring` section: soft mention of `starts at ₹2,500`.
5. Add a `Best 3 subject lines` note recommending the free-sample and value subjects.

### `agency_outreach_campaign.md`

1. Replace `Hi there,` with `Hi [First Name],` for all 20 prospects.
2. Add one line of outcome before the feature list.
3. Use a stronger CTA: `Reply with your target ICP or 2-3 URLs and I will send the sample.`
4. Attach the correct sample CSV per agency vertical.
5. Add `100% advance, 24-hour delivery` to the `EXPECTED OFFER` block.

### `sales_sheet.md`

1. Pick one currency (recommend ₹ for this campaign).
2. Remove add-ons or simplify to one `Priority delivery` add-on.
3. Highlight `Growth` as `Most popular`.
4. Add `Free revision for missing/malformed rows` under every tier.
5. Add `100% advance via UPI or bank transfer` under pricing.

---

## 4. Top 5 Highest-Impact Edits

1. **Fix the mailto link.** A broken CTA is the single biggest reply killer.
2. **Standardize currency.** Mixed ₹/$ destroys trust immediately.
3. **Personalize greetings.** `Hi [First Name],` outperforms `Hi there,` in B2B.
4. **Attach the right sample.** Send real-estate/local-business samples to B2B agencies, not e-commerce.
5. **Add a P.S. and a provenance note.** These two small copy changes increase perceived reliability.

All edits are text-only within existing assets. No new products, repositories, or lead lists are created.
