# Emmy Demo Scenarios

**Last updated:** April 14, 2026

---

## Shared conventions (all scenarios)

### Two visual modes

Everything in every demo scenario uses one of two treatments:

| Mode | When | Font | Color | Fidelity |
|------|------|------|-------|----------|
| **Emmy** | All Emmy screens | Source Sans Pro / Public Sans (USWDS) | Blue USWDS color scheme, full component library | High -- this is the product |
| **Everything else** | State portal, backend checks, caseworker portal, email, determination | Monospace | Greyscale only | Low -- wireframe-level, clearly "not Emmy" |

The contrast should be immediately obvious. When a viewer sees color and USWDS components, they know they're looking at Emmy. When they see greyscale monospace, they know it's a state system that varies by implementation.

### Interstitial screens

At every transition between actors or systems, a full-page interstitial introduces the next phase. Format:

- **Actor avatar** (centered, top) -- colored circle with initial for people, gear emoji for systems
- **Phase title** -- large heading, e.g., "Avery submits her Medicaid application"
- **Perspective label** -- who is acting, e.g., "State Medicaid Portal"
- **Description** -- grey left-bordered card on grey background, 1-2 neutral sentences describing what happens next without revealing outcomes or prescribing what the state does with the information
- **"In this phase, you'll see:"** -- 2-3 bullet list of what the next screens show
- **Visual treatment note** (yellow callout) -- when the visual mode changes, explain why (e.g., "These screens use wireframe styling to indicate they are part of the state's Medicaid portal, not Emmy.")
- **Action button** (grey, not blue) to proceed (e.g., "Begin Application >", "Continue >")

Interstitials are how the demo self-narrates. The viewer should never be confused about who changed, what system they're in, or why.

**Tone rules for interstitial descriptions:**
- Describe what is about to happen, not what the outcome will be. The viewer should discover results on the screens themselves.
- Do not reveal whether someone meets or fails a requirement, whether a case is approved or denied, or what specific discrepancies exist.
- Do not prescribe what the state or caseworker will do with the information. Say "reviews" or "decides," not "approves" or "flags."
- Keep the language neutral and procedural. The interstitial sets up context, not conclusions.

### Shared UI elements

**Config header** (all screens):
- Sticky dark bar at top (z-index 100, #1b1b1b background)
- "Back to Home" button -- returns to the service blueprint landing page
- Scenario label (e.g., "Scenario 1 -- Self-Employment Verification") -- updates when switching scenarios; hidden on the home page
- Collapsible process stepper toggle -- hidden on the home page
- "Reset demo" button -- resets to Interstitial A of the current scenario

**Process stepper drawer** (all screens):
- Collapsible panel below config header
- Phases listed with step-by-step breakdown
- Current step highlighted blue; visited steps get green dot; unvisited steps gray
- Phase 4 (Emmy) title in blue; all others in gray

**Emmy header** (Emmy screens only):
- Gov banner: "An official website of the United States government"
- Brand: "Emmy | Eligibility Made Easy" + "State" label
- Links: "Help", "Espanol"

**Site footer** (Emmy screens only):
- Emmy branding + "Share feedback" button with chat icon

**Wireframe alert banner** (non-Emmy screens only):
- Light orange/tan bar at top of content area
- Labels the context (e.g., "Example online Medicaid application", "Caseworker eligibility portal")

**Flow navigation** (all screens):
- Bottom bar with Back / Next buttons
- Center label (optional)
- Independent of stepper -- allows sequential screen-by-screen navigation

### Shared narrative structure

Every scenario follows the same 5-phase arc:

| Phase | Actor | Visual mode | Purpose |
|-------|-------|-------------|---------|
| 1. Application | Applicant | Wireframe | Applicant submits Medicaid application via state portal |
| 2. Verification | System (automated) | Wireframe | State runs automated checks against external data |
| 3. Caseworker | Caseworker | Wireframe | Caseworker reviews gaps and triggers documentation request |
| 4. Emmy | Applicant | Full USWDS | Applicant verifies activities and submits report through Emmy |
| 5. Determination | Caseworker | Wireframe | Caseworker reviews Emmy report and makes eligibility decision |

Each phase starts with an interstitial. Phase 4 (Emmy) contains the majority of content screens.

### Shared data

- **Reporting period:** March 2026 (all scenarios)
- **Caseworker name:** Cara Martinez (all scenarios)

### Data consistency rules

Each scenario defines a data table (at the end of its section) listing every name, date, ID, institution, hours value, and other data that appears on more than one screen. These rules apply when building or updating any scenario:

**Single source of truth per scenario.** Every data point (name, DOB, application ID, hours, dates, etc.) must have exactly one canonical value in the scenario's data table. Every screen that displays that data point must use that exact value -- no rounding, reformatting, or paraphrasing.

**Dates must form a coherent timeline.** The reporting period, application date, email/notification dates, and determination date should follow a logical sequence. If the reporting period is March 2026, the application cannot be submitted in December 2026. A reasonable default timeline:
1. Reporting period: March 2026
2. Application submitted: early April 2026
3. Verification checks / caseworker review: same day or within days
4. Emmy link sent: within days of application
5. Emmy submission: within days of receiving link
6. Determination: within 10 business days of application

**IDs must be consistent across navigation and display.** If an application ID appears in a URL, a case card, a confirmation screen, and an email, it must be identical in all four places. Watch for placeholder IDs left over from earlier drafts.

**Names and personal details cannot vary by screen.** If the applicant's DOB is 06/15/1992 on the application form, it must be 06/15/1992 on the caseworker review screen. If the caseworker's name is Cara Martinez on the dashboard, it must be Cara Martinez on the determination notice.

**Calculated values must be derivable.** If education hours = credits x 12, and credit hours = 4, then education CE hours must be 48 everywhere. If total = education + community service, and community service = 47, then total must be 95. Don't hard-code totals independently of their components.

**Reporting period language must be consistent.** Don't mix "March," "March 2026," and "March 2026 (January-May)" for the same data point. Pick one label per context (e.g., "March" in compact UI, "March 2026" in descriptions) and apply it uniformly.

**When updating any value, grep the full prototype for every occurrence.** A single data point can appear in CSS IDs, HTML content, JavaScript data structures, stepper labels, and comments. Changing it in the visible content but not the stepper label or screen ID creates silent inconsistencies.

### Application form structure (all scenarios)

The state Medicaid application uses the same 5-step sequence across all scenarios:

| Step | Label | Content |
|------|-------|---------|
| 1 | Your Information | Name, DOB, SSN, phone, address |
| 2 | Income | "Are you currently earning any income?" (Yes/No radio) + details if Yes |
| 3 | Education | "Are you a student?" (Yes/No radio) |
| 4 | Community Engagement | "Did you do any community service in March?" (Yes/No) + "Did you do any work programs in March?" (Yes/No) |
| 5 | Review & Submit | Summary of all sections, certification checkbox, submit button |

Click-to-fill behavior: clicking anywhere on the screen fills all fields with scenario-appropriate values. Each scenario defines which radio buttons auto-select to Yes vs No based on its narrative.

### CE hours calculation

- **Credit-to-CE-hours ratio:** 12 CE hours per credit hour
- **80-hour monthly threshold** for the hours/income path
- **$580/month income** for the income path
- **Half-time enrollment** for the education path

### Scenario navigation

All scenarios share a single HTML prototype with a common navigation framework:
- **Config header** includes a scenario selector so viewers can toggle between scenarios
- **Process stepper** updates to reflect the current scenario's screens
- **"Reset demo"** resets to the beginning of the current scenario
- Each scenario's screens, interstitials, and stepper phases are defined independently but rendered in the same shell

### Building a multi-scenario prototype

This section documents the technical approach for combining scenarios into one HTML file.

**Screen ID namespacing.** Every screen ID must be prefixed with the applicant's lowercase name to avoid collisions:
- Scenario 1: `alex-app-info`, `alex-emmy-welcome`, `alex-cw-dashboard`, etc.
- Scenario 2: `avery-app-info`, `avery-emmy-welcome`, `avery-cw-dashboard`, etc.
- Shared screens (intro/selector): use neutral IDs like `intro`, `scenario-selector`
- Interstitials follow the same convention within each scenario: `alex-phase-verification`, `avery-phase-verification`

**Phase structure must match across scenarios.** Both scenarios must use the same 5-phase arc, even if a scenario has fewer screens within a phase. This keeps the stepper layout consistent when switching scenarios. The 5 phases are:
1. Application
2. Verification
3. Caseworker
4. Emmy
5. Determination

Scenario 1's React source currently uses 4 phases (it merges verification into the caseworker phase). When building the consolidated prototype, split it into 5 to match.

**One visual language for wireframes.** The scenario 2 prototype uses greyscale monospace for all non-Emmy screens. Scenario 1's React source uses a blue-themed state portal with colored buttons and styled headers. The consolidated prototype must use a single wireframe treatment -- greyscale monospace -- for all non-Emmy screens in both scenarios. This means the scenario 1 state portal screens need to be rebuilt in that style.

**Shared CSS structure.** Organize styles into layers:
1. **Reset and base** -- applies everywhere
2. **Config header and stepper** -- shared navigation chrome
3. **Interstitial screens** -- grey background, grey buttons, neutral tone (shared)
4. **Wireframe screens** -- greyscale monospace template (shared)
5. **Emmy screens** -- USWDS components, gov banner, Emmy header/footer (shared)
6. **Scenario-specific styles** -- any layout unique to a scenario (e.g., hub progress cards in scenario 2, upload area in scenario 1). Prefix with scenario name: `.avery-hub-progress`, `.alex-upload-area`

**JavaScript data per scenario.** The `screenOrder`, `stepperPhases`, and any fill-on-click data should be defined as scenario-specific objects, keyed by scenario name. The navigation, stepper rendering, and screen-show/hide logic should be generic and operate on whichever scenario is active. Example structure:
```
const scenarios = {
  scenario1: { screenOrder: [...], stepperPhases: [...], label: 'Scenario 1 -- Self-Employment' },
  scenario2: { screenOrder: [...], stepperPhases: [...], label: 'Scenario 2 -- Education + Community Service' }
};
let activeScenario = 'scenario1';
```

**Scenario switching behavior:**
- Switching scenarios hides all screens from the current scenario and shows the first screen (interstitial A) of the new one
- Stepper resets to show the new scenario's phases
- Visited-screen state resets

**Entry point: Service blueprint.** The prototype opens on a service blueprint home page. The config header includes a "Back to Home" button that returns to this page from any screen in either scenario. This is the primary way to switch between scenarios.

### Home page: Service blueprint (`home`)

The landing page for the entire demo. Not part of any scenario -- it sits above both and provides context before the viewer chooses a path.

**Layout:**

Header bar with "Emmy Demo" branding (same config header used throughout, but with no scenario label or stepper toggle shown on this page).

**Service blueprint diagram** showing the overall Medicaid eligibility process as a horizontal swimlane chart with three rows:

| Row | Label | Color |
|-----|-------|-------|
| Applicant | What the applicant does at each step | Purple |
| Caseworker / State | What the state system and caseworker do | Gray |
| Emmy | Where Emmy fits in the process | Blue |

Columns represent the 5 process steps: Application, Data checks, Request info (if not auto-verified), Review (if not auto-verified), Decision.

The diagram communicates that Emmy only activates when the state can't auto-verify -- it fills the gap between automated systems and manual documentation.

**Scenario launch buttons** (below the blueprint):

Two prominent buttons, each with a short description:

- **Scenario 1: Self-Employment Verification**
  "Alex attests to 80 hours/month of self-employment. The state can't auto-verify, so Alex uploads documentation through Emmy."

- **Scenario 2: Education + Community Service**
  "Avery is enrolled below half-time. Emmy helps Avery document credit hours, add community service, and submit a complete report."

Each button navigates to that scenario's Interstitial A.

**Footer note:** "This is a demonstration prototype. Wireframe screens represent state systems that vary by implementation. Emmy screens show the product at full fidelity."

**Reuse styling and components across scenarios.** Scenario 1 is simpler than scenario 2 (fewer Emmy screens, no progress tracking, no spoke pattern). When building scenario 1 in the consolidated HTML, reuse scenario 2's shared components (Emmy header/footer, wireframe templates, interstitial layout, config header, stepper, flow nav, document upload cards) rather than building parallel versions. Only the content and screen sequence differ.

**Email screen placement.** Every scenario includes an email/notification screen as the first screen inside Phase 4 (Emmy), before the Emmy welcome. This is the bridge between the caseworker sending the request and the applicant entering Emmy. Scenario 1's React source skips this screen; add it when building the consolidated prototype.

### Figma Make considerations

- Each screen (including interstitials) is one static Figma frame. No animations or conditional rendering.
- All form fields are pre-filled and read-only. Show the "after" state.
- Document uploads show the completed state (file name + size), not the upload interaction.
- Progress bars are static widths set per frame. No animation.
- Keep text short. 1-2 sentences max per content block.
- Reuse components. Interstitial layout, Emmy header/footer, progress bar, activity cards should each be a Figma component.
- Non-Emmy screens share one greyscale monospace template. Emmy screens share the USWDS template. Interstitials are a third template.
- Navigation between screens is handled in code, not by Figma Make.

---

## Scenario 1: Applicant attests to meeting CE requirement but the state can't auto-verify

### What this scenario demonstrates

Alex applies for Medicaid and attests to 80 hours/month of self-employment (freelance graphic design). The state's automated systems can't verify self-employment through Quarterly Wage Data, so a caseworker sends Alex a link to Emmy to upload documentation. Alex uploads invoices and contracts, and the caseworker reviews the structured submission.

**Emmy capabilities shown:** Document upload for self-employment verification, structured report to the state, pre-populated application data carried into Emmy.

**Source:** React/TypeScript application (`Scenario 1_Draft Demo-CODE.zip`). Uses Vite + React Router.

---

### Screens

---

#### Interstitial A: State Application

- **Avatar:** Applicant (A, purple)
- **Title:** Alex submits a Medicaid application
- **Perspective:** State Medicaid Portal
- **Description:** Alex fills out a Medicaid application on the state's portal, including personal information, income, and self-employment details.
- **In this phase, you'll see:**
  - Alex enters personal info and income
  - Alex reports self-employment activity
  - Alex reviews and submits the application
- **Note (yellow):** These screens use wireframe styling to indicate they are part of the state's Medicaid portal, not Emmy.
- **Button:** Begin Application >

---

#### Screen 1: Application start (`alex-app-start`)

**Visual mode:** Wireframe (state portal)

"Example State Medicaid Portal" header. Landing page with:
- "Apply for health coverage" heading
- What you'll need: personal info, income/employment, community engagement activities
- "Start application" button

---

#### Screen 2: Application form (`alex-app-form`)

**Visual mode:** Wireframe (state portal)

5-step form:

**Step 1 -- Your Information:**
- First name: Alex
- Last name: Smith
- Date of birth: 06/15/1992
- SSN: 123-45-6789

**Step 2 -- Income:**
- Self-employment: Yes
- Type: Freelance graphic design
- Hours per week: 20
- Income per month: $600

**Step 3 -- Education:**
- "Are you a student?" -- No (click to fill selects No)

**Step 4 -- Community Engagement:**
- "Did you do any community service in March?" -- No (click to fill selects No)
- "Did you do any work programs in March?" -- No (click to fill selects No)

**Step 5 -- Review and Submit:**
- Summary of all sections
- Attestation checkbox
- "Submit application" button

---

#### Screen 3: Submission confirmation (`alex-app-submitted`)

**Visual mode:** Wireframe (state portal)

Success confirmation:
- Application ID: MC-2026-04-0002
- Submitted: April 1, 2026
- What happens next: eligibility review, automated data source checks, possible request for documentation, decision within 10 business days

---

#### Interstitial B: Backend Verification

- **Avatar:** System (gear emoji)
- **Title:** The state checks Alex's information
- **Perspective:** Backend Eligibility System
- **Description:** After Alex submits, the state's eligibility system runs automated checks to verify what was reported.
- **Button:** Continue >

---

#### Screen 4: Automated verification (`alex-data-checks`)

**Visual mode:** Wireframe

Animated verification checks (staggered reveal):

1. **Identity verification** -- Verified via DMV records (checkmark)
2. **Residence verification** -- State residency confirmed (checkmark)
3. **Employment/income verification** -- Unable to verify. Self-employment hours can't be confirmed through Quarterly Wage Data. Requires manual documentation. (X)

Summary: 2 of 3 checks passed. Application routed to caseworker queue.

---

#### Interstitial C: Caseworker Review

- **Avatar:** Caseworker (C, gray)
- **Title:** A caseworker requests documentation
- **Perspective:** Caseworker Eligibility Portal
- **Description:** A caseworker reviews the verification results and decides what additional information is needed from Alex.
- **In this phase, you'll see:**
  - Caseworker dashboard showing pending cases
  - Caseworker reviews the case and sends a documentation request via Emmy
- **Note (yellow):** The caseworker portal uses wireframe styling. Emmy does not initiate contact -- it responds to a request the state has already decided to make.
- **Button:** Continue >

---

#### Screen 5: Caseworker dashboard (`alex-cw-dashboard`)

**Visual mode:** Wireframe

"Eligibility Portal" header, Caseworker: Cara Martinez. Table of recent applications:

| Application ID | Applicant | Date | Status |
|---|---|---|---|
| MC-2026-04-0002 | Alex Smith | April 1, 2026 | Needs Review |
| MC-2026-04-0001 | Jordan Davis | March 31, 2026 | Complete |
| MC-2026-04-0003 | Michael Chen | March 29, 2026 | Pending Documents |

Alert: "Application MC-2026-04-0002 requires follow-up. Self-employment verification could not be completed automatically."

"Request More Information" button on Alex's row.

---

#### Screen 6: Caseworker request for information (`alex-cw-case`)

**Visual mode:** Wireframe

Two-column layout:
- **Left:** Applicant info (Alex Smith, DOB March 22, 1995, email, phone)
- **Right:** Application status -- self-employment verification failed, CE requirement attested (80 hrs/month, meets if verified)

**Request via Emmy** section:
- Pre-composed message asking Alex for self-employment documentation (invoices, contracts, work logs)
- "Send Emmy Link to Alex" button
- Success confirmation: "Emmy link sent successfully!"

---

#### Interstitial D: Emmy

- **Avatar:** Applicant (A, purple)
- **Title:** Alex provides documentation through Emmy
- **Perspective:** Emmy
- **Description:** Alex opens the link from the email and uses Emmy to provide documentation for their self-employment.
- **In this phase, you'll see:**
  - Alex receives an email with a link to Emmy
  - Alex's self-employment details carried over from the application
  - Alex uploads supporting documents
  - Alex reviews and submits the report to the state
- **Note (yellow):** These screens show Emmy at full fidelity -- this is the product experience.
- **Button:** Open Emmy >

---

#### Screen 7: Email -- Documentation request (`alex-email`)

**Visual mode:** Wireframe (email chrome)

From: State Department of Health and Human Services
Subject: Action needed -- verify your self-employment for Medicaid
Body: We need documentation to confirm your self-employment hours. Prominent "Verify with Emmy" button. 30-day deadline. Phone number for questions.

> **Callout:** The email bridges state systems and Emmy. Same pattern as scenario 2.

---

#### Screen 8: Emmy -- Welcome (`alex-emmy-welcome`)

**Visual mode:** Full Emmy (USWDS)

"Welcome, Alex!" with Emmy header and gov banner.

**What is Emmy?** Info card explaining the tool.

**What you need to do:**
1. Upload documentation for your self-employment (reported 80 hours/month, 20 hrs/week, freelance graphic design)
2. Review and submit

Estimated time: 5 minutes. "Get started" button.

---

#### Screen 9: Emmy -- Activity Hub (`alex-emmy-hub`)

**Visual mode:** Full Emmy (USWDS)

Split layout:
- **Left:** Instructions -- "Add documentation for your self-employment"
- **Right:** Employment card (pre-populated from application):
  - Tag: "From your application"
  - Type of work: Freelance graphic design
  - Hours per month: 80 hours
  - Alert: "Upload required -- your state needs documentation to confirm your self-employment hours"

"Continue to upload" button. Secondary: "Add additional activities."

---

#### Screen 10: Emmy -- Upload documents (`alex-emmy-upload`)

**Visual mode:** Full Emmy (USWDS)

"Upload supporting documents" heading.

**What you reported:**
- Type: Freelance graphic design
- March hours: 80 hours
- March income: $600

Drag-and-drop upload area (PDF, JPG, PNG, max 10MB).

**Acceptable documents:** Business tax records, invoices, bank statements, contracts, business license.

Back / "Continue to review" buttons.

---

#### Screen 11: Emmy -- Review and submit (`alex-emmy-submit`)

**Visual mode:** Full Emmy (USWDS)

**Self-employment information** table:
- Type of work: Freelance Graphic Design
- Hours in March: 80 hours
- Income in March: $600

**Supporting documentation:** Document uploaded (Invoice-March-2026.pdf) with edit link.

**Legal agreements:** Scrollable terms, certification checkbox, electronic signature consent.

Back / "Submit" button (disabled until checkbox checked).

---

#### Screen 12: Emmy -- Submitted (`alex-emmy-success`)

**Visual mode:** Full Emmy (USWDS)

"You successfully submitted your self-employment verification."

Confirmation code: MC-2026-04-0002-V. "Your eligibility worker will review your information."

Download submission option.

---

#### Interstitial E: Determination

- **Avatar:** Caseworker (C, gray)
- **Title:** The caseworker makes an eligibility decision
- **Perspective:** Caseworker Eligibility Portal
- **Description:** The caseworker receives Alex's report from Emmy and reviews it alongside the rest of the application.
- **In this phase, you'll see:**
  - Caseworker receives a structured report from Emmy
  - Caseworker reviews and acts on Alex's application
  - Alex receives a determination notice
- **Note (yellow):** The caseworker portal uses wireframe styling. The structured report from Emmy is what the caseworker acts on.
- **Button:** Continue >

---

#### Screen 13: Caseworker determination (`alex-cw-emmy-review`)

**Visual mode:** Wireframe

Caseworker: Cara Martinez. Header cards: Alex Smith, Application ID, Submitted April 1, 2026.

Tabbed interface:
- **Documents Received:** Invoice-March-2026.pdf and Client_Contracts.pdf (both "Received via Emmy"). Work activity details: freelance graphic design, 20 hrs/week, 80 hrs/month, started January 2026.
- **Verification Status:** Automated verification failed for self-employment. CE requirement met (80 hrs/month documented via invoices/contracts). Recommendation: Approve.
- **Application History:** Timeline from submission through Emmy link sent, documents received.

"Approve & Enroll in Medicaid" / "Request Additional Information" buttons.

---

#### Screen 14: Alex receives determination (`alex-determination`)

**Visual mode:** Wireframe

"You're Approved!" with large checkmark.

**Notice of Determination:**
- Application ID, determination date (April 1, 2026), applicant (Alex Smith), caseworker (Cara Martinez)
- Coverage effective April 1, 2026
- Member ID: MC123456789
- Plan: Standard Medicaid, $0 premium

**Determination details:** Income qualifies, CE met via self-employment (20 hrs/week, 80+ hrs/month), documentation verified.

**What happens next:** Medicaid card in 7-10 days, choose PCP within 30 days, coverage begins immediately.

**Ongoing requirements:** 80 hrs/month, report changes within 10 days, complete annual review.

---

### Screen count summary

| Phase | Interstitial | Content screens | Visual mode |
|-------|-------------|-----------------|-------------|
| 1. State application | A | 3 | Wireframe |
| 2. Backend verification | B | 1 | Wireframe |
| 3. Caseworker | C | 2 | Wireframe |
| 4. Emmy | D | 6 (email + 5 Emmy) | Email: wireframe; Emmy: full USWDS |
| 5. Determination | E | 2 | Wireframe |
| **Total** | **5** | **14** | |

**19 screens total** (14 content + 5 interstitials). Emmy screens are 5 of 14 content screens.

---

### Data that must stay consistent across screens

| Data point | Value | First appears |
|------------|-------|---------------|
| Applicant name | Alex Smith | Screen 2 |
| Applicant DOB | 06/15/1992 | Screen 2 |
| Applicant email | alex.smith@example.com | Screen 6 |
| Applicant phone | (555) 234-5678 | Screen 6 |
| Application ID | MC-2026-04-0002 | Screen 3 |
| Confirmation code | MC-2026-04-0002-V | Screen 11 |
| Caseworker name | Cara Martinez | Screen 5 |
| Self-employment type | Freelance graphic design | Screen 2 |
| Hours per week | 20 | Screen 2 |
| Hours per month | 80 | Screen 2 |
| Monthly income | $600 | Screen 2 |
| Reporting period | March 2026 | Screen 9 |
| Application date | April 1, 2026 | Screen 3 |
| Coverage effective date | April 1, 2026 | Screen 13 |
| CE path | 80 hours/month via self-employment | Screen 4 |

> **Implementation note:** The React source has DOB and reporting period inconsistencies that need to be fixed when building the consolidated HTML prototype. DOB should be 06/15/1992 throughout. Reporting period should be March 2026 throughout.

---

### Key differences from Scenario 2

| Aspect | Scenario 1 | Scenario 2 |
|--------|-----------|-----------|
| **Applicant** | Alex Smith | Avery Johnson |
| **CE path** | 80 hours via self-employment | Combined: education (48 hrs) + community service (47 hrs) = 95 hrs |
| **Verification gap** | Self-employment invisible to Quarterly Wage Data | Education enrollment below half-time |
| **Emmy's role** | Document upload only | Activity tracking, hour entry, document upload, progress toward 80-hr threshold |
| **Emmy screens** | 5 (welcome, hub, upload, review, submitted) | 13 (welcome, hub x3, edu spoke x3, CS spoke x4, review, submitted) |
| **Progress tracking** | Not shown (binary: upload or don't) | Progress bar (48/80 -> 95/80) |
| **Implementation** | React/TypeScript (Vite) | Static HTML |
| **Phase structure** | 4 phases | 5 phases |

---

## Scenario 2: Applicant doesn't meet CE requirement and needs to add additional activities

### What this scenario demonstrates

Avery applies for Medicaid and attests to half-time student enrollment. State data shows she's enrolled less than half-time. Emmy helps Avery document her credit hours, identify the gap, add volunteering hours with documentation, and submit a complete report.

**Emmy capabilities shown:** Attestation data carried over from state application, progress tracking across multiple activity types, document upload for self-attested activities, structured report to the state.

---

### Screens

---

#### Interstitial A: State Application

- **Avatar:** Applicant (A, purple)
- **Title:** Avery submits her Medicaid application
- **Perspective:** State Medicaid Portal
- **Description:** Avery fills out a Medicaid application on her state's portal, including personal information, income, and any community engagement activities.
- **In this phase, you'll see:**
  - Avery enters personal info, income, education, and community engagement
  - Avery reviews and submits the application
- **Note (yellow):** These screens use wireframe styling to indicate they are part of the state's Medicaid portal, not Emmy.
- **Button:** Begin Application >

---

#### Screen 1: State application -- Your Information (`avery-app-info`)

**Visual mode:** Wireframe

Step 1 of 5 -- "Your Information." Pre-filled fields:

- Full name: Avery Johnson
- Date of birth: 03/14/2004
- Phone: (217) 555-0134
- Address: 123 Main Street, Springfield, IL 62701

"Continue" button.

---

#### Screen 2: State application -- Income (`avery-app-income`)

**Visual mode:** Wireframe

Step 2 of 5 -- "Income."

- "Are you currently earning any income?" -- No (click to fill selects No)

"Continue" button.

---

#### Screen 3: State application -- Education (`avery-app-education`)

**Visual mode:** Wireframe

Step 3 of 5 -- "Education."

- "Are you a student?" -- Yes (click to fill selects Yes)

"Continue" button.

> **Callout:** Avery reports being a student. The state will verify enrollment status against NSC data.

---

#### Screen 4: State application -- Community Engagement (`avery-app-community`)

**Visual mode:** Wireframe

Step 4 of 5 -- "Community Engagement."

- "Did you do any community service in March?" -- No (click to fill selects No)
- "Did you do any work programs in March?" -- No (click to fill selects No)

"Continue" button.

---

#### Screen 5: State application -- Review and submit (`avery-app-review`)

**Visual mode:** Wireframe

Step 5 of 5 -- "Review and submit." Summary: personal info, income (no income reported), education (student: yes), community engagement (community service: no, work programs: no). Certification checkbox. "Submit application" button.

---

#### Interstitial B: Backend Verification

- **Avatar:** System (gear emoji)
- **Title:** The state checks Avery's information
- **Perspective:** Backend Eligibility System
- **Description:** After Avery submits, the state's eligibility system runs automated checks against external data sources to verify what she reported.
- **In this phase, you'll see:**
  - Income confirmed below the Medicaid threshold
  - Education enrollment found but below half-time -- insufficient for CE education path
  - CE cannot be auto-confirmed; the case is flagged for caseworker review
- **Note (yellow):** This screen represents automated checks happening behind the scenes, not a screen any user sees.
- **Button:** Continue >

---

#### Screen 6: Behind the scenes -- Verification checks (`avery-data-checks`)

**Visual mode:** Wireframe (narrator treatment)

Vertical checklist with status indicators:

1. **Income eligibility** -- Confirmed below threshold (checkmark)
2. **CE exemption screening** -- No exemptions apply (dash)
3. **Education enrollment** -- State University, less than half-time. Does not satisfy education path. (warning)
4. **CE hours/income** -- Cannot auto-confirm community service hours. No income data for $580/month path. (X)

Result: "CE cannot be confirmed automatically. Caseworker review needed."

> **Callout:** This establishes why Emmy activates: education was found but isn't sufficient on its own, and volunteering has no electronic data source.

---

#### Interstitial C: Caseworker Review

- **Avatar:** Caseworker (C, gray)
- **Title:** A caseworker requests documentation
- **Perspective:** Caseworker Eligibility Portal
- **Description:** A caseworker reviews the verification results and decides what additional information is needed from Avery.
- **In this phase, you'll see:**
  - Caseworker dashboard showing pending cases
  - Caseworker reviews the case and sends a documentation request
  - Avery receives an email with a link to Emmy
- **Note (yellow):** The caseworker portal uses wireframe styling. Emmy does not initiate contact -- it responds to a request the state has already decided to make.
- **Button:** Continue >

---

#### Screen 7: Caseworker dashboard (`avery-cw-dashboard`)

**Visual mode:** Wireframe

Caseworker portal header: "Caseworker: Cara Martinez". Table of pending cases showing Avery Johnson's case with status "Pending -- documentation needed."

---

#### Screen 8: Caseworker case review and request (`avery-cw-case`)

**Visual mode:** Wireframe

Case detail view. Summary:
- Application ID: MC-2026-4872
- Applicant: Avery Johnson
- Income: $0/month (verified)
- CE status: Education enrolled -- half-time attested, NSC shows below half-time. Community service unverified.
- Action: Documentation request with pre-filled message explaining the enrollment discrepancy

"Send request via Emmy" button (shown as completed).

---

#### Interstitial D: Emmy

- **Avatar:** Applicant (A, purple)
- **Title:** Avery provides documentation through Emmy
- **Perspective:** Emmy
- **Description:** Avery opens the link from her email and uses Emmy to provide documentation and report her activities.
- **In this phase, you'll see:**
  - Avery's attestation data carried over from the application
  - Progress tracking showing the gap between reported hours and the 80-hour threshold
  - Avery enters education credit hours and uploads documentation
  - Avery adds volunteering hours and uploads documentation
  - The progress bar reaches 80 hours
  - Avery reviews and submits the report to the state
- **Note (yellow):** These screens show Emmy at full fidelity -- this is the product experience.
- **Button:** Open Emmy >

---

#### Screen 9: Email -- Documentation request (`avery-email`)

**Visual mode:** Wireframe (email chrome)

From: State Department of Health and Human Services
Subject: Action needed on your Medicaid application
Body: Enrollment at State University may be below half-time. Need to verify credit hours and provide documentation. May also add other qualifying activities. Prominent "Verify with Emmy" button. 30-day deadline. Phone number for questions.

> **Callout:** The email bridges state systems and Emmy. The Emmy link is the key element.

---

#### Screen 10: Emmy -- Welcome (`avery-emmy-welcome`)

**Visual mode:** Full USWDS

Emmy header + gov banner. Welcome message explaining what this tool does and what Avery will need to provide. Application ID shown.

**What we know so far** (summary from state):
- Avery reported being enrolled at State University at least half-time
- State records show enrollment is less than half-time
- Need to verify credit hours and provide documentation

Consent checkbox + "Get started" button.

> **Callout:** This is where the audience sees that Emmy has Avery's data from the state. She doesn't start from scratch.

---

#### Screen 11: Emmy -- Activity Hub, initial (`avery-emmy-hub-prepop`)

**Visual mode:** Full USWDS

Hub with split layout. Left sidebar shows progress card and reporting period (March 2026). Right side shows activity sections.

**Activities:**
- **Education** -- State University. Needs credit hour entry. "Add your credit hours" action.
- **Employment** -- Not reported. "Add" action.
- **Community service** -- Not reported. "Add" action.
- **Work programs** -- Not reported. "Add" action.

> **Callout:** Hub shows all four activity categories. Education is pre-populated from the application but needs credit hours entered.

---

#### Screen 12: Emmy -- Education spoke: credit hours (`avery-edu-credits`)

**Visual mode:** Full USWDS

Term label: Spring 2026. Prompt to enter credit hours for State University.

Pre-filled: 4 credit hours.

"I didn't take any classes this term" checkbox (unchecked).

"Save and continue" button.

---

#### Screen 13: Emmy -- Education spoke: upload documents (`avery-edu-upload`)

**Visual mode:** Full USWDS

Upload supporting documents for State University, Spring 2026 (4 credit hours).

Documents uploaded (completed state):
- transcript.pdf
- enrollment-verification.pdf
- tuition-letter.pdf

"Save and continue" button.

---

#### Screen 14: Emmy -- Education spoke: review (`avery-edu-review`)

**Visual mode:** Full USWDS

Review table:

| Term | Enrollment status | Credit hours | Community engagement hours |
|------|-------------------|-------------|---------------------------|
| Spring 2026 (January-May) | Less than half-time | 4 | 48 |

Documents uploaded (3 files listed). "Save and return to Activity Hub" button.

> **Callout:** 4 credits x 12 hours/credit = 48 CE hours. Application data is pre-filled. Document upload is required for self-attested activities.

---

#### Screen 15: Emmy -- Activity Hub, partial (`avery-emmy-hub-partial`)

**Visual mode:** Full USWDS

**Progress:**
- 48 / 80 hours (progress bar at 60%)
- "32 hours still needed" (implied by progress card)

**Activities:**
- **Education** -- 48 hours counted (4 credits x 12 hrs/credit). State University details shown.
- **Community service** -- not reported. "Add" action.
- **Employment** -- not reported. "Add" action.
- **Work programs** -- not reported. "Add" action.

"Review and submit" button available but progress incomplete.

> **Callout:** The progress bar shows the gap. Emmy guides Avery toward what to do next without requiring her to understand the three compliance paths.

---

#### Screen 16: Emmy -- Community service spoke: organization (`avery-cs-org`)

**Visual mode:** Full USWDS

Pre-filled organization details:
- Organization: Westbrook community garden
- Address: 1033 Berkman St, Tallahassee, FL 32301
- Coordinator: Aaron Keyes
- Email: aaron.keyes@westbrookgardens.org
- Phone: (415) 344-8009

"Save and continue" button.

---

#### Screen 17: Emmy -- Community service spoke: hours (`avery-cs-july`)

**Visual mode:** Full USWDS

Monthly hour entry for March 2026:
- Hours: 47

"Save and continue" button.

---

#### Screen 18: Emmy -- Community service spoke: upload documents (`avery-cs-upload`)

**Visual mode:** Full USWDS

Documents uploaded (completed state):
- volunteer-log-march.pdf
- coordinator-letter.pdf

"Save and continue" button.

---

#### Screen 19: Emmy -- Community service spoke: review (`avery-cs-review`)

**Visual mode:** Full USWDS

Review of community service entry:
- Organization: Westbrook community garden
- Coordinator: Aaron Keyes
- March hours: 47

Documents uploaded (2 files listed). "Save and return to Activity Hub" button.

---

#### Screen 20: Emmy -- Activity Hub, requirement met (`avery-emmy-hub-complete`)

**Visual mode:** Full USWDS

**Progress:**
- 95 / 80 hours (progress bar full, success state, green checkmark)
- "1/1 months completed"

**Activities (updated):**
- **Education** -- 48 hours (4 credits x 12 hrs/credit, State University)
- **Community service** -- 47 hours (Westbrook community garden, documents uploaded)

"Review and submit" button (prominent).

> **Callout:** The payoff. Progress went from 48/80 to 95/80. Emmy guided Avery from gap to completion. The framing is "hours reported," not "you're eligible" -- Emmy doesn't determine eligibility.

---

#### Screen 21: Emmy -- Review and submit (`avery-emmy-submit`)

**Visual mode:** Full USWDS

Page title: "Review and submit your community engagement report."

"1/1 months completed" banner.

**Activity 1: Education**
- Enrollment table: Spring 2026, less than half-time, 4 credits, 48 CE hours
- 3 documents uploaded

**Activity 2: Community service**
- Organization: Westbrook community garden
- March: 47 hours
- 2 documents uploaded

Certification checkbox. "Submit report" button.

---

#### Screen 22: Emmy -- Submitted (`avery-emmy-success`)

**Visual mode:** Full USWDS

Success icon. "Your report has been submitted."

Confirmation code: MC-2026-4872. "A caseworker will review your report alongside your application."

---

#### Interstitial E: Determination

- **Avatar:** Caseworker (C, gray)
- **Title:** The caseworker makes an eligibility decision
- **Perspective:** Caseworker Eligibility Portal
- **Description:** The caseworker receives Avery's report from Emmy and reviews it alongside the rest of her application.
- **In this phase, you'll see:**
  - Caseworker receives a structured report from Emmy
  - Caseworker approves Avery's application
  - Avery receives a determination notice
- **Note (yellow):** The caseworker portal uses wireframe styling. The structured report from Emmy is what the caseworker acts on.
- **Button:** Continue >

---

#### Screen 23: Caseworker receives Emmy report (`avery-cw-emmy-review`)

**Visual mode:** Wireframe

Caseworker portal with case detail. Emmy report card showing:

**Education documents** (3 files, received via Emmy):
- transcript.pdf, enrollment-verification.pdf, tuition-letter.pdf
- Verification note: Documentation confirms 4 credit hours in Spring 2026, equating to 48 hours of community engagement per month.
- Institution: State University, Term: Spring 2026, Credit Hours: 4, CE Hours: 48 (4 credits x 12 hours/credit)

**Community service documents** (2 files, received via Emmy):
- volunteer-log-march.pdf, coordinator-letter.pdf
- Organization: Westbrook community garden, Supervisor: Aaron Keyes, March: 47 hours

**CE Summary:**
- Education: 48 hours/month
- Community Service: 47 hrs (March)
- Total: 95 hrs (March)
- Exceeds 80-hour requirement (checkmark)

"Approve & Enroll in Medicaid" button.

---

#### Screen 24: Avery receives determination (`avery-determination`)

**Visual mode:** Wireframe (side-by-side caseworker portal + Avery's mobile view)

Caseworker side: Case approved, income eligibility confirmed, CE requirement verified (95 hrs), documentation reviewed via Emmy.

Avery's mobile view: Determination notice -- "Your Medicaid application has been approved." Coverage start date. Brief next steps.

---

### Screen count summary

| Phase | Interstitial | Content screens | Visual mode |
|-------|-------------|-----------------|-------------|
| 1. State application | A | 5 | Wireframe |
| 2. Backend verification | B | 1 | Wireframe |
| 3. Caseworker + notification | C | 2 | Wireframe |
| 4. Emmy | D | 13 (email + 12 Emmy) | Email: wireframe; Emmy: full USWDS |
| 5. Determination | E | 2 | Wireframe |
| **Total** | **5** | **24** | |

**29 screens total** (24 content + 5 interstitials). Emmy screens are the majority (13 of 24 content screens).

---

### Data that must stay consistent across screens

| Data point | Value | First appears |
|------------|-------|---------------|
| Applicant name | Avery Johnson | Screen 1 |
| Applicant DOB | 03/14/2004 | Screen 1 |
| Applicant phone | (217) 555-0134 | Screen 1 |
| Applicant address | 123 Main Street, Springfield, IL 62701 | Screen 1 |
| Application ID | MC-2026-4872 | Screen 7 |
| Caseworker name | Cara Martinez | Screen 6 |
| Education institution | State University | Screen 3 |
| Credit hours | 4 (less than half-time) | Screen 11 |
| CE hours per credit | 12 | Screen 13 |
| Education CE hours | 48 (4 x 12) | Screen 13 |
| Education term | Spring 2026 (January-May) | Screen 11 |
| Community service organization | Westbrook community garden | Screen 15 |
| Community service coordinator | Aaron Keyes | Screen 15 |
| Community service hours | 47 (March) | Screen 16 |
| Total hours | 95 | Screen 19 |
| 80-hour threshold | 80 | Screen 14 |
| Reporting period | March 2026 | Screen 10 |
| Income | $0/month | Screen 2 |
| Application/submission date | April 1, 2026 | Screen 4 |

> **Needs fix in prototype:** The current HTML prototype uses "December 15, 2026" as the submission/email date across 5 locations. This must be updated to early April 2026 to align with the March 2026 reporting period per the timeline rules above.
