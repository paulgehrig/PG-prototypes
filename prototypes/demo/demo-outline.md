# Emmy Demo Scenarios

**Last updated:** April 15, 2026 (nav redesign, sentence case pass, email fidelity reduction, auto-advance, accessibility text size audit)

---

## Pick-up notes (for resuming work)

**Published demo:** https://paulgehrig.github.io/PG-prototypes/prototypes/demo/emmy-e2e-demo.html (via `paulgehrig/PG-prototypes` repo at `/tmp/PG-prototypes/prototypes/demo/emmy-e2e-demo.html`)

**This outline:** `/Users/paul/Documents/HR1 CE Reqs/Merged demo folder/demo-outline.md` — authoritative spec. Also mirrored in the PG-prototypes repo.

**Production reference:** https://github.com/DSACMS/iv-cbv-payroll (the CBV Rails app). Emmy screens should mirror this repo's styling, components, colors, and spacing as closely as possible.

**Demo scenarios in the file:**
1. **Scenario 1 — Alex Smith** — self-employment verification (can't be auto-verified, uploads docs through Emmy)
2. **Scenario 2 — Avery Johnson** — education + community service (enrolled less than half-time, adds community service to meet threshold)

**To do list**
- 

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

**Visual treatment:**
- **Background:** Warm peach gradient (linear-gradient from #fef3e8 to #fde7c9)
- **White card:** Centered, rounded corners (12px), shadow, max-width 700px -- contains all content below
- **Actor avatar** (centered, top) -- illustrated profile portrait with blue ring border (#005ea2, 4px) for people; grey circle with gear emoji for system/backend screens. Profile images for Alex Smith and Cara Martinez are embedded as base64 PNGs.
- **Phase title** -- large heading (32px, bold), e.g., "Avery submits her Medicaid application"
- **Perspective label** -- smaller text (16px, #565c65), e.g., "State Medicaid Portal"
- **Description** -- light blue-grey card (#f0f4f8) with blue left border (#005ea2), centered text, 1-2 neutral sentences describing what happens next without revealing outcomes
- **"In this phase, you'll see:"** -- 2-3 bullet list of what the next screens show
- **Visual treatment note** (yellow callout) -- when the visual mode changes, explain why
- **Action button** -- blue (#005ea2), rounded (6px), centered, with arrow chevron

Interstitials are how the demo self-narrates. The viewer should never be confused about who changed, what system they're in, or why.

**Tone rules for interstitial descriptions:**
- Describe what is about to happen, not what the outcome will be. The viewer should discover results on the screens themselves.
- Do not reveal whether someone meets or fails a requirement, whether a case is approved or denied, or what specific discrepancies exist.
- Do not prescribe what the state or caseworker will do with the information. Say "reviews" or "decides," not "approves" or "flags."
- Keep the language neutral and procedural. The interstitial sets up context, not conclusions.

### Shared UI elements

**Bottom bar** (all screens):
- Fixed to the bottom of the viewport (z-index 100, white #f9f9f9 background, 1px top border)
- Left: filled blue (#005ea2) toggle button with hamburger icon + "Scenario X: Name" + step count (e.g., "3 / 22") -- opens the sidebar
- Right: outlined blue Back / Next buttons matching USWDS button style
- On the home page, toggle shows "Emmy Demo" and Back/Next are disabled
- Arrow keys (left/right) also navigate between screens; Escape closes sidebar

**Sidebar** (slides from left):
- White background, 320px wide, overlays content with dark scrim
- Header with scenario name + close button
- Scenario 1 / Scenario 2 tab switcher
- Scenario summary card (blue border, light blue background) with name and description
- "Journey map" home link at top
- Phase-grouped screen list with active highlighting (blue background + left border) and click-to-navigate
- Phases color-coded: grey for state phases, blue for Emmy, green for determination
- Home and Reset accessible via sidebar

**Emmy header** (Emmy screens only):
Two stacked bands, constrained to the same 880px content width as the page body:
1. **Gov banner** (federal): "An official website of the United States government" with US flag emoji
2. **Main header** (white, 1px bottom border):
   - Left: two-line title
     - Primary title (22px, bold): "Emmy | Eligibility Made Easy"
     - Subtitle (14px, regular): "State Medicaid Agency"
   - Right: "Help", "Español" links (blue underlined)

**Site footer** (Emmy screens only):
- Dark navy (#162e51) band, constrained to same 880px content width as the header
- Two-line branding (left-aligned):
  - Line 1 (22px, bold): "Emmy"
  - Line 2 (14px, regular): "Eligibility Made Easy"

**Wireframe alert banner** (non-Emmy screens only):
- Yellow bar (#faf3d1) with warning icon (&#9888;), sticky at top
- Monospace font, 15px, semibold, centered text
- Labels each screen's context to make clear it is not part of Emmy (sentence case):
  - State application screens: "Example State Medicaid Application"
  - Backend verification screens: "Simulated state backend eligibility checks"
  - Caseworker screens: "Example caseworker eligibility portal"
  - Email screens: "Example email notification"
  - Determination screens: "Example eligibility determination"

**Screen layout:**
- Every screen fills the full viewport height (min-height: 100vh, flexbox column)
- Main content area grows to fill available space between header elements and the bottom bar
- 60px bottom padding on every screen to prevent the fixed bottom bar from overlapping content

### Text conventions

**Sentence case:** All titles, headings, labels, badges, alerts, button text, and navigation elements use sentence case (only first word capitalized). Exceptions: proper nouns (Emmy, Medicaid, State University, person names), abbreviations (CE, SUD, DMV, NSC), and product branding ("Eligibility Made Easy").

**Gender-neutral pronouns:** All applicants (Alex, Avery) are referred to with they/their/them. No gendered pronouns in any screen content or interstitial text.

**Minimum text size:** 14px for all content-facing text that users read (body text, labels, descriptions, table cells, badges in cards, form labels, alert text, signature text). Exceptions: uppercase UI labels with `text-transform: uppercase`, navigation chrome (sidebar, bottom bar), Gmail wrapper chrome, icon badges, and data check source labels.

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

Yes/No radio options are always ordered **Yes first, No second** for consistency across all screens.

### Emmy product UI design system

Emmy screens aim to look as close as possible to the production product at **https://github.com/DSACMS/iv-cbv-payroll** (the consent-based verification Rails app). When in doubt, mirror what that repo does.

**Reference files in the production repo:**
- `app/app/assets/stylesheets/uswds-settings.scss` — USWDS theme tokens
- `app/app/assets/stylesheets/uswds-overrides.scss` — global overrides
- `app/app/assets/stylesheets/activity_hub.scss` — activity hub layout
- `app/app/assets/stylesheets/cbv.scss` — header, footer, tables, success page
- `app/app/components/activity_flow_progress_indicator/` — progress indicator component
- `app/app/views/activities/activities/index.html.erb` — hub markup

**Color tokens** (use these hex values, not arbitrary colors):

| Token | Hex | Usage |
|-------|-----|-------|
| primary | #005ea2 | Primary buttons, links, header title, gov banner |
| primary-vivid | #0050d8 | Progress bar fill + border, progress number in progress |
| primary-lighter | #d9e8f6 | Progress bar track, success icon circle background |
| primary-darker | #162e51 | Gov banner background, footer background |
| success-dark | #00a91c | Complete progress state (bar, border, number, checkmark) |
| success-lighter | #ecf3ec | Complete progress bar track background, success icon backgrounds |
| blue-cool-5 | #e1f3f8 | Table header row backgrounds, subheader rows |
| ink | #1b1b1b | Body text, table borders |
| base (gray) | #565c65 | Subtitles, hints, secondary text |
| base-lighter | #dfe1e2 | Card borders, subtle dividers |
| faf3d1 | #faf3d1 | Wireframe alert banner, inline card alerts |

**Typography scale** (Emmy screens — `.emmy-page-content`):

| Level | Desktop | Mobile (<640px) | USWDS token (reference) |
|-------|---------|-----------------|-------------------------|
| h1 | 36px | 28px | "xl" |
| h2 | 28px | 24px | size 10 |
| h3 | 22px | 19px | size 8 |
| h4 | 19px | 19px | size 7 |

Line height 1.2 for headings. Body paragraphs use 16px, line height 1.62.

**Progress indicator** (activity hub sidebar + review screen banner):
- Track: `#d9e8f6` background with `#0050d8` 1px border, 4px radius, 19px tall
- Fill (in progress): `#0050d8` solid
- Fill (complete): `#00a91c`
- Complete track: `#ecf3ec` background with `#00a91c` border
- Current-hours number: `#0050d8` in progress, `#00a91c` complete
- Complete checkmark icons (next to "March" on complete hub, in complete banner on review): `#00a91c`

**Review tables** (`.emmy-review-table` — based on production `.cbv-table`):
- max-width: 44rem (704px)
- 1px ink border
- `<thead th>` background: `#e1f3f8` (blue-cool-5), 10px vertical padding
- tbody tr td:first-child is auto-bold (`font-weight: 700`)
- `<tr.subheader-row>` variant with blue-cool-5 background + bold text
- Edit link button: `.edit-link` — `#005ea2` underlined, bold

**USWDS forms** (Emmy spoke inputs):
- `.usa-form` wrapper (optional `--large` for 640px max-width)
- `.usa-form-group` per field (24px bottom margin)
- `.usa-label` — bold 16px Public Sans, block, 8px margin below
- `.usa-hint` — 16px gray `#71767a`, sits between label and input
- `.usa-input` / `.usa-select` / `.usa-textarea` — 40px height, 1px `#565c65` border, 16px font, focus outline `#2491ff`
- `.usa-input--small` (7rem max) for credit hours / hours
- `.usa-input--medium` (15rem max) for zip codes
- Every input has matching `id` ↔ `for` label association

**Success screen** (`.usa-icon-list` pattern):
- `<ul class="usa-icon-list">` with `<li class="usa-icon-list__item">` items
- Icon: 48px pill (`#d9e8f6` primary-lighter bg, `#005ea2` primary-vivid SVG fill)
- Content: h3 (20px bold) + paragraph + button, stacked with proper spacing

### Activity Hub card treatment (Emmy screens)

The Activity Hub uses two distinct card treatments, and the choice depends on the state of the activity. **Do not conflate them.**

**Pattern A — Standard USWDS card (production default).** Use this for filled activities that are ready as-reported and do not require applicant attention. This is the pattern used in production's iv-cbv-payroll and is the default for any activity a user has already supplied data for.

Structure:
- `<section class="activity-hub-section">` wrapper
- Section header: activity title (h2) + outline "+ Add" button (`.activity-hub-add-btn`)
- `<div class="usa-card activity-hub-card">` with `.usa-card__container`
  - `.usa-card__header` — flex row with `h3.usa-card__heading` + `a.usa-link` ("Edit")
  - 2px base-lighter bottom border on the header
  - `.usa-card__body` — no horizontal padding on the container; body has `padding: 0 20px`
- `.activity-month-details` inside the body — 172px fixed "Month" label (bold) on the left, flex data column on the right with stacked `<p class="margin-y-0">` lines

Applied to:
- `avery-emmy-hub-partial` (Education card)
- `avery-emmy-hub-complete` (Education + Community service cards)

**Pattern B — Special-state card.** Use this when an activity is pre-populated from the application and requires applicant attention (upload required, credit hours needed, discrepancy). The card visually carries an inline alert or badge that draws the eye.

Examples:
- `alex-emmy-hub` — pre-populated employment with an inline "Upload required" yellow alert inside the card, describing the documentation needed
- `avery-emmy-hub-prepop` — pre-populated education with a "Needs Information" warning tag and a "Credit hours: Needs Information" row inside the card

Pattern B uses the legacy `.hub-edu-filled-card` / `.hub-edu-month-row` markup with scenario-specific inline alert/badge styling. It is intentionally visually distinct from Pattern A so applicants immediately recognize "this one needs me to do something" vs "this one is already accepted."

**Empty-state card** (both patterns): a light grey card (`.activity-hub-empty-state` or `.hub-empty-card`) with a single line like "No employment added." Used in any section where no data has been provided.

### Caseworker request pattern (all scenarios)

Every scenario's "Case review and request" screen (`{prefix}-cw-case`) uses the same "Request additional documentation" form:

**Standardized checkbox list** (same 5 options across scenarios):
- Education enrollment details
- Proof of income
- Additional community engagement hours
- Proof of community service
- Proof of work program participation

Each scenario pre-checks only the options relevant to its narrative:
- Scenario 1 (Alex): Proof of income
- Scenario 2 (Avery): Education enrollment details + Additional community engagement hours

**Message to applicant textarea:**
- Populated via **typing animation** (character-by-character) when the screen is filled, as if the caseworker is composing the message in real time.
- Typing speed: ~18ms/character, with a small pause on line breaks.
- Message content is scenario-specific and matches exactly what appears in the email the applicant receives next.

**Send button interaction:**
- The "Send Emmy link to {Name}" button is **interactive**, not pre-sent. The caseworker must click it to send.
- On click: button text changes to "Request sent", button is disabled, and a confirmation note appears below ("A link to Emmy has been sent to the applicant at {email}.").
- **Auto-advance:** 5 seconds after sending, the screen automatically advances to the next screen.
- Returning to the screen resets the button state and clears the textarea.

### Email notification pattern (all scenarios)

Every scenario includes an email notification screen at the start of Phase 4 (Emmy). The screen shows the applicant viewing the email in their inbox:

- **Gmail wrapper:** Top bar with Gmail logo and search, left sidebar with Inbox/Starred/Sent/Drafts, toolbar above the message. Strictly visual -- not interactive. Full fidelity (this is the applicant's real inbox).
- **Co-branded email card:** Grey header (#3d4551) with monospace font, "State Medicaid Agency" on the left and "Emmy / Eligibility Made Easy" on the right. Uses the same greyscale wireframe treatment as other state system screens to signal this is not Emmy.
- **Subject line:** Appears in the Gmail subject area with an "Inbox" label.
- **Email body copy:** Monospace font, greyscale. Comes directly from the caseworker's message on the case review screen. This keeps the two screens consistent and shows the applicant is reading exactly what the caseworker wrote.
- **CTA card:** Light blue (#f0f7ff) bordered card with a "Verify with Emmy" button -- this is the only full-fidelity element in the email body, signaling the transition to Emmy.
- **Signature:** Monospace, greyscale. "Thank you, State Medicaid Agency." No caseworker name -- notices are sent from a central inbox.
- **Meta footer:** Monospace, greyscale. Case reference number, 30-day deadline, phone number for questions.

### Backend data checks structure (all scenarios)

The automated verification screen uses the same 4-section structure across all scenarios:

| Section | Content | Data sources |
|---------|---------|-------------|
| 1. Identity | DMV Records, Address Verification | Always verified |
| 2. Exemptions | VA/Disability, Pregnancy/Caregiving, Medical Frailty/SUD, Age | Scenario-appropriate age; other exemption records usually "No record" |
| 3. Household Income | State quarterly wage data | Single check; result varies by scenario |
| 4. Education | National Student Clearinghouse | Single check; result varies by scenario |

Each section reveals with a staggered animation (spinner → checks load one by one → status badge appears). The final alert card describes what needs follow-up.

**Tone for alerts:** Describe what the state can't confirm, not a "discrepancy" between what the applicant said and what the data shows. The applicant is not attesting to a specific enrollment level or hours — they're attesting to whether they're a student, working, etc.

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

Blue gradient header with "Emmy Demo" badge, "Medicaid eligibility process" title, and subtitle.

**Scenario launch buttons** (between header and blueprint):

Two prominent blue buttons positioned above the blueprint diagram:

- **Scenario 1: Doc upload**
- **Scenario 2: CE flow**

Each button navigates to that scenario's details page.

**Service blueprint diagram** (max-width 1400px) showing the overall Medicaid eligibility process as a horizontal swimlane chart with three rows:

| Row | Label | Color |
|-----|-------|-------|
| Applicant | What the applicant does at each step | Purple |
| Caseworker / State | What the state system and caseworker do | Gray |
| Emmy | Where Emmy fits in the process | Blue |

Columns represent the 5 process steps: Application, Data checks, Request info (if not auto-verified), Review (if not auto-verified), Decision. Each card has an inline icon + title on one line with a description below.

The diagram communicates that Emmy only activates when the state can't auto-verify -- it fills the gap between automated systems and manual documentation.

**Footer note:** "This demo focuses on how the Emmy App fits within the broader Medicaid eligibility process."

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
- Hours per month: 80
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

**Visual mode:** Wireframe (narrator treatment)

Animated verification checks (staggered reveal), grouped into 4 sections:

1. **Identity** -- Verified
   - DMV Records: Identity confirmed (checkmark)
   - Address Verification: State residency confirmed (checkmark)
2. **Exemptions** -- None Apply
   - VA / Disability: No record
   - Pregnancy / Caregiving: No record
   - Medical Frailty / SUD: No record
   - Age: Age 33 (N/A)
3. **Household Income** -- Action Needed
   - State quarterly wage data: No records found -- self-employment not captured (X)
4. **Education** -- Not a Student
   - National Student Clearinghouse: No enrollment records (N/A)

Alert: "Self-employment cannot be confirmed automatically. More information is required to determine Medicaid eligibility."

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

#### Screen 6: Caseworker case review and request (`alex-cw-case`)

**Visual mode:** Wireframe

Case detail view for MC-2026-04-0002. Case Details table showing all four application sections (Your Information, Income, Education, Community Engagement) with their verification statuses.

**Request additional documentation** section:
- Standardized checkbox list -- "Education enrollment details", "Proof of income", "Additional community engagement hours"
- Pre-checked for Alex: **Proof of income** only
- Message to applicant textarea, populated via typing animation when the caseworker "composes" the message
- "Send Emmy Link to Alex" button -- interactive. Click to send. After sending, button shows "Request Sent" and a note appears: "A link to Emmy has been sent to the applicant at alex.smith@example.com."

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

**Visual mode:** Wireframe (shown inside a Gmail inbox UI)

Shown as a viewed message in a mock Gmail interface (top bar with Gmail logo + search, left sidebar with Inbox/Starred/Sent, toolbar above the email).

The email itself is a co-branded card:
- **Header:** Gradient from navy to state blue, showing "State Medicaid Agency / Department of Health and Human Services" on the left and "Emmy / Eligibility Made Easy" on the right
- **Subject:** "Action needed: verify your self-employment for Medicaid"
- **Body:** The caseworker's message from the case review screen -- "Hello Alex, We received your Medicaid application. To make a decision, we need documentation about your self-employment. Please use the secure link below to provide documents that show your self-employment hours (such as invoices, contracts, or work logs)."
- **CTA card:** Light blue background with "Verify with Emmy" button
- **Signature:** "Thank you, State Medicaid Agency" (no individual caseworker name — sent from central inbox)
- **Meta:** Case reference, 30-day deadline, phone number

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
| Hours per month | 80 | Screen 2 |
| Monthly income | $600 | Screen 2 |
| Reporting period | March 2026 | Screen 9 |
| Application date | April 1, 2026 | Screen 3 |
| Coverage effective date | April 1, 2026 | Screen 13 |
| CE path | 80 hours/month via self-employment | Screen 4 |

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

Animated verification checks (staggered reveal), grouped into 4 sections:

1. **Identity** -- Verified
   - DMV Records: Identity confirmed (checkmark)
   - Address Verification: State residency confirmed (checkmark)
2. **Exemptions** -- None Apply
   - VA / Disability: No record
   - Pregnancy / Caregiving: No record
   - Medical Frailty / SUD: No record
   - Age: Age 22 (N/A)
3. **Household Income** -- Eligible
   - State quarterly wage data: No wage records (matches attestation) (checkmark)
4. **Education** -- More Info Needed
   - National Student Clearinghouse: State University -- less than half-time (warning)

Alert: "Enrollment is less than half-time. More information is required to determine Medicaid eligibility."

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

Case detail view for MC-2026-4872. Case Details table showing all four application sections (Your Information, Income, Education, Community Engagement) with their verification statuses.

**Request additional documentation** section:
- Same standardized checkbox list -- "Education enrollment details", "Proof of income", "Additional community engagement hours"
- Pre-checked for Avery: **Education enrollment details** and **Additional community engagement hours**
- Message to applicant textarea, populated via typing animation
- "Send Emmy Link to Avery" button -- interactive. Click to send. After sending, button shows "Request Sent" and a note appears: "A link to Emmy has been sent to the applicant at avery.johnson@example.com."

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
  - Avery adds volunteering hours
  - The progress bar reaches 80 hours
  - Avery reviews and submits the report to the state
- **Note (yellow):** These screens show Emmy at full fidelity -- this is the product experience.
- **Button:** Open Emmy >

---

#### Screen 9: Email -- Documentation request (`avery-email`)

**Visual mode:** Wireframe (shown inside a Gmail inbox UI)

Same Gmail wrapper and co-branded email card as scenario 1. The email body uses the exact caseworker message from the case review screen:

- **Subject:** "Action needed: verify your enrollment for Medicaid"
- **Body:** "Hello Avery, Our records show you may be enrolled less than half-time at State University. Please provide your credit hours and any documentation to verify enrollment. You may also add other qualifying activities."
- **CTA card:** "Verify with Emmy" button
- **Signature:** "Thank you, State Medicaid Agency" (no individual caseworker name — sent from central inbox)

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
- **Employment** -- not reported. "Add" action.
- **Community service** -- not reported. "Add" action.
- **Work programs** -- not reported. "Add" action.

"Review and submit" button available but progress incomplete.

> **Callout:** The progress bar shows the gap. Avery decides to add Uber driving hours to close the gap faster while also earning income.

---

#### Screen 16: Emmy -- Employment spoke: search (`avery-emmy-employment`)

**Visual mode:** Full USWDS

Avery searches for and selects Uber as her employer. Emmy prompts her to connect her Uber account via payroll sync (Argyle) to pull in hours and income automatically.

"Connect Uber account" button.

---

#### Screen 17: Emmy -- Employment spoke: payroll sync (`avery-payroll-sync`)

**Visual mode:** Full USWDS

Argyle payroll sync flow. Avery authenticates her Uber account. Emmy retrieves her March 2026 driving activity.

Loading/sync state shown, then confirmation that data has been retrieved.

---

#### Screen 18: Emmy -- Employment spoke: payment details (`avery-payment-details`)

**Visual mode:** Full USWDS

March 2026 Uber earnings pulled via payroll sync:
- Employer: Uber
- Hours driven: 20
- Income: $170

"Save and continue" button.

---

#### Screen 19: Emmy -- Activity Hub, employment added (`avery-emmy-hub-with-employment`)

**Visual mode:** Full USWDS

**Progress:**
- 68 / 80 hours (progress bar at 85%)
- "12 hours still needed"

**Activities (updated):**
- **Education** -- 48 hours (4 credits x 12 hrs/credit, State University)
- **Employment** -- 20 hours, $170 income (Uber, March 2026)
- **Community service** -- not reported. "Add" action.
- **Work programs** -- not reported. "Add" action.

"Review and submit" button available but progress incomplete.

> **Callout:** Adding Uber brought Avery from 48/80 to 68/80. She's close — 12 hours short. She adds her community service hours to close the gap.

---

#### Screen 20: Emmy -- Community service spoke: organization (`avery-cs-org`)

**Visual mode:** Full USWDS

Pre-filled organization details:
- Organization: Westbrook community garden
- Address: 1033 Berkman St, Tallahassee, FL 32301
- Coordinator: Aaron Keyes
- Email: aaron.keyes@westbrookgardens.org
- Phone: (415) 344-8009

"Save and continue" button.

---

#### Screen 21: Emmy -- Community service spoke: hours (`avery-cs-july`)

**Visual mode:** Full USWDS

Monthly hour entry for March 2026:
- Hours: 15

"Save and continue" button.

---

#### Screen 22: Emmy -- Community service spoke: review (`avery-cs-review`)

**Visual mode:** Full USWDS

Review of community service entry:
- Organization: Westbrook community garden
- Coordinator: Aaron Keyes
- March hours: 15

"Save and return to Activity Hub" button.

---

#### Screen 23: Emmy -- Activity Hub, requirement met (`avery-emmy-hub-complete`)

**Visual mode:** Full USWDS

**Progress:**
- 83 / 80 hours (progress bar full, success state, green checkmark)
- "1/1 months completed"

**Activities (updated):**
- **Education** -- 48 hours (4 credits x 12 hrs/credit, State University)
- **Employment** -- 20 hours, $170 income (Uber, March 2026)
- **Community service** -- 15 hours (Westbrook community garden)

"Review and submit" button (prominent).

> **Callout:** The payoff. Progress went from 48/80 → 68/80 → 83/80. Three activity types combined to meet the threshold. Emmy doesn't determine eligibility — it reports hours.

---

#### Screen 24: Emmy -- Review and submit (`avery-emmy-submit`)

**Visual mode:** Full USWDS

Page title: "Review and submit your community engagement report."

"1/1 months completed" banner.

**Activity 1: Education**
- Enrollment table: Spring 2026, less than half-time, 4 credits, 48 CE hours
- 3 documents uploaded

**Activity 2: Employment**
- Employer: Uber
- March hours: 20
- March income: $170
- Source: Connected via payroll sync

**Activity 3: Community service**
- Organization: Westbrook community garden
- March: 15 hours

Certification checkbox. "Submit report" button.

---

#### Screen 25: Emmy -- Submitted (`avery-emmy-success`)

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

#### Screen 26: Caseworker receives Emmy report (`avery-cw-emmy-review`)

**Visual mode:** Wireframe

Caseworker portal with case detail. Emmy report card showing:

**Education documents** (3 files, received via Emmy):
- transcript.pdf, enrollment-verification.pdf, tuition-letter.pdf
- Verification note: Documentation confirms 4 credit hours in Spring 2026, equating to 48 hours of community engagement per month.
- Institution: State University, Term: Spring 2026, Credit Hours: 4, CE Hours: 48 (4 credits x 12 hours/credit)

**Employment details** (via payroll sync):
- Employer: Uber, March hours: 20, March income: $170

**Community service details** (self-attested, no documents):
- Organization: Westbrook community garden, Supervisor: Aaron Keyes, March: 15 hours

**CE Summary:**
- Education: 48 hrs (March)
- Employment: 20 hrs (March)
- Community Service: 15 hrs (March)
- Total: 83 hrs (March)
- Exceeds 80-hour requirement (checkmark)

"Approve & Enroll in Medicaid" button.

---

#### Screen 27: Avery receives determination (`avery-determination`)

**Visual mode:** Wireframe (side-by-side caseworker portal + Avery's mobile view)

Caseworker side: Case approved, income eligibility confirmed, CE requirement verified (83 hrs across education, employment, and community service), documentation reviewed via Emmy.

Avery's mobile view: Determination notice -- "Your Medicaid application has been approved." Coverage start date. Brief next steps.

---

### Screen count summary

| Phase | Interstitial | Content screens | Visual mode |
|-------|-------------|-----------------|-------------|
| 1. State application | A | 5 | Wireframe |
| 2. Backend verification | B | 1 | Wireframe |
| 3. Caseworker + notification | C | 2 | Wireframe |
| 4. Emmy | D | 16 (email + 15 Emmy) | Email: wireframe; Emmy: full USWDS |
| 5. Determination | E | 2 | Wireframe |
| **Total** | **5** | **27** | |

**32 screens total** (27 content + 5 interstitials). Emmy screens are the majority (16 of 27 content screens).

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
| Uber hours (March) | 20 | Screen 18 |
| Uber income (March) | $170 | Screen 18 |
| Community service organization | Westbrook community garden | Screen 20 |
| Community service coordinator | Aaron Keyes | Screen 20 |
| Community service hours | 15 (March) | Screen 21 |
| Total hours | 83 (48 edu + 20 employment + 15 CS) | Screen 23 |
| 80-hour threshold | 80 | Screen 14 |
| Reporting period | March 2026 | Screen 10 |
| Income | $0/month reported on application (Uber income captured in Emmy) | Screen 2 |
| Application/submission date | April 1, 2026 | Screen 4 |

> **Fixed:** All caseworker dashboard dates updated to April 2026 — Avery Johnson → April 1, Jordan Davis → March 31, Michael Chen → March 29. Submitted date in `avery-cw-emmy-review` → April 1, 2026.
