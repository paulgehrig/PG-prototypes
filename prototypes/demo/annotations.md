# Demo Annotations Reference

Annotations appear in the right margin of the 1024px content column (hidden below 1320px viewport width). Each annotation is anchored to a page element via `data-anchor` — the JS reads that element's position at navigation time and sets `top` accordingly. If no anchor is found, the annotation centers vertically in the viewport.

To update an annotation, find the `<!-- SCREEN: id -->` block in `emmy-e2e-demo 4.17.html` and edit the `<div class="demo-annotation">` block immediately inside it.

To change the anchor, update `data-anchor="<css-selector>"` on that div. The selector is scoped to the screen — use any valid CSS selector that matches an element within the screen.

---

## Scenario 1 — Alex

### alex-data-checks
- **Anchor:** `.cw-header`
- **Badge:** 🔗 Emmy API
- **Title:** Emmy API augments state data
- **Body:** These checks combine the state's existing data sources with additional lookups via the Emmy API. State wage records run first — can't confirm self-employment. Emmy API bridges the gap automated checks can't cross. Flags the case and activates the Emmy documentation flow.

### alex-cw-case
- **Anchor:** `.cw-section-title` ("Request additional information via Emmy")
- **Badge:** ⚡ Emmy Integration
- **Title:** First Emmy touchpoint
- **Body:** This entire request flow is built on the Emmy integration — it's where Emmy first enters the experience. Application data flows from the eligibility system directly into Emmy. State controls all messaging & branding. The link sent to the applicant is tokenized & secure. Caseworker's checkbox selections customize what Emmy shows the applicant.

### alex-emmy-welcome
- **Anchor:** `h1`
- **Badge:** ⚡ Emmy Value
- **Title:** Application data pre-loaded
- **Body:** Alex's self-employment details flow in from the state application — no re-entry required.

### alex-emmy-hub
- **Anchor:** `h1`
- **Badge:** ⚡ Emmy Value
- **Title:** Pre-populated from state application
- **Body:** Alex's reported work activity flows directly from the Medicaid application into Emmy's activity hub.

### alex-emmy-upload
- **Anchor:** `h1`
- **Badge:** ⚡ Emmy Value
- **Title:** Guided document upload
- **Body:** Emmy prompts for the right document types and organizes them by activity — ready for caseworker review.

### alex-emmy-submit
- **Anchor:** `h1`
- **Badge:** ⚡ Emmy Value
- **Title:** Structured review before submission
- **Body:** All data is presented for applicant review — reducing errors and building confidence before signing.

### alex-emmy-success
- **Anchor:** `h1`
- **Badge:** ⚡ Emmy Value
- **Title:** Caseworker-ready report delivered
- **Body:** Emmy sends the state a structured, organized report — not a pile of loose PDFs.

### alex-cw-emmy-review
- **Anchor:** `.cw-body h2` ("Review submitted information")
- **Badge:** 📋 Emmy Output
- **Title:** Emmy report in the portal
- **Body:** Documents and structured data from Emmy arrive directly in the caseworker portal — no manual sorting needed.

---

## Scenario 2 — Avery

### avery-data-checks
- **Anchor:** `#avery-dc-section-education` (Education / NSC section)
- **Badge:** 🔗 Emmy API
- **Title:** NSC call via Emmy API
- **Body:** The National Student Clearinghouse query is an Emmy API call — not a native state system check. It augments what the state already has. NSC returns below-half-time status → triggers CE flag. Without Emmy API, this check doesn't exist in the state's system. Emmy then activates to collect supplemental documentation.

### avery-cw-case
- **Anchor:** `.cw-section-title` ("Request additional information via Emmy")
- **Badge:** ⚡ Emmy Integration
- **Title:** First Emmy touchpoint
- **Body:** This entire request flow is built on the Emmy integration — it's where Emmy first enters the experience. Application data flows from the eligibility system directly into Emmy. State controls all messaging & branding. The link sent to the applicant is tokenized & secure. Caseworker's checkbox selections customize what Emmy shows the applicant.

### avery-emmy-welcome
- **Anchor:** `h1`
- **Badge:** ⚡ Emmy Value
- **Title:** State data pre-loaded
- **Body:** Avery's enrollment info flows in from the state application — she starts informed, not from scratch.

### avery-emmy-hub-prepop
- **Anchor:** `h1`
- **Badge:** ⚡ Emmy Value
- **Title:** Activity hub overview
- **Body:** All CE activity types in one place. Education is pre-populated from the state app and flagged for action.

### avery-edu-credits
- **Anchor:** `h1`
- **Badge:** ⚡ Emmy Value
- **Title:** Automatic CE calculation
- **Body:** Emmy converts credit hours to CE hours (4 credits × 12 = 48 hrs) — Avery just enters her credits.

### avery-edu-upload
- **Anchor:** `h1`
- **Badge:** ⚡ Emmy Value
- **Title:** Per-activity document collection
- **Body:** Emmy organizes documents by activity type, making the caseworker's review fast and clear.

### avery-edu-review
- **Anchor:** `h1`
- **Badge:** ⚡ Emmy Value
- **Title:** Activity-level review
- **Body:** A structured data table before saving — applicants confirm accuracy before the hub is updated.

### avery-emmy-hub-partial
- **Anchor:** `h1`
- **Badge:** ⚡ Emmy Value
- **Title:** Real-time progress tracking
- **Body:** The bar shows exactly how many hours remain. Emmy guides Avery toward what to add next — no manual math.

### avery-emmy-employment
- **Anchor:** `h1`
- **Badge:** ⚡ Emmy Value
- **Title:** Payroll connection via Emmy
- **Body:** Emmy connects to payroll providers and gig apps to pull verified income and hours automatically — no pay stubs to hunt down.

### avery-payroll-sync
- **Anchor:** `h1`
- **Badge:** ⚡ Emmy Value
- **Title:** Real-time payroll sync
- **Body:** Argyle (via Emmy) fetches verified income, employment, paystubs, and identity data directly from Uber — no manual uploads, no guesswork.

### avery-payment-details
- **Anchor:** `h1`
- **Badge:** ⚡ Emmy Value
- **Title:** Verified payroll data via Argyle
- **Body:** Emmy surfaces structured, verified income and hours directly from Uber — no pay stubs, no manual entry.

### avery-emmy-hub-with-employment
- **Anchor:** `h1`
- **Badge:** ⚡ Emmy Value
- **Title:** Employment added via Emmy
- **Body:** Uber Driver hours and income are now in the report — pulled automatically. Avery just needs to add community service to hit 80 hours.

### avery-cs-org
- **Anchor:** `h1`
- **Badge:** ⚡ Emmy Value
- **Title:** Multi-activity support
- **Body:** Avery layers community service on top of education — Emmy handles both CE paths in one submission.

### avery-cs-july
- **Anchor:** `h1`
- **Badge:** ⚡ Emmy Value
- **Title:** Monthly hour tracking
- **Body:** Emmy captures hours by reporting month, matching the state's monthly 80-hour CE threshold.

### avery-cs-review
- **Anchor:** `h1`
- **Badge:** ⚡ Emmy Value
- **Title:** Confirm before continuing
- **Body:** Each activity is reviewed separately before returning to the hub — one source of truth per activity.

### avery-emmy-hub-complete
- **Anchor:** `h1`
- **Badge:** ⚡ Emmy Value
- **Title:** Requirement met — 83 of 80 hrs
- **Body:** Progress bar turns green and Emmy confirms the threshold is crossed before Avery submits.

### avery-emmy-submit
- **Anchor:** `h1`
- **Badge:** ⚡ Emmy Value
- **Title:** Unified submission
- **Body:** Education + employment + community service combined into one complete CE report — one submission to the state.

### avery-emmy-success
- **Anchor:** `h1`
- **Badge:** ⚡ Emmy Value
- **Title:** Structured report delivered
- **Body:** Emmy sends the caseworker a clean, review-ready package — hours, documents, and calculated CE totals.

### avery-cw-emmy-review
- **Anchor:** `.cw-body h2` ("Review submitted information")
- **Badge:** 📋 Emmy Output
- **Title:** Emmy report in the portal
- **Body:** Structured data from Emmy gives the caseworker hours, documents, and CE totals — all in one place.
