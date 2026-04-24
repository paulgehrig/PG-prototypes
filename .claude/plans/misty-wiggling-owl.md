# Plan: Restructure Beneficiary Archetypes Table with Full Population Funnel

## Context

The existing archetypes table only covers the non-exempt Medicaid expansion adults who reach Emmy — it's missing the two earlier stages of the population funnel (formally exempt beneficiaries, and non-exempt beneficiaries whose CE compliance is auto-verified via ex parte). As a result, the population percentages sum to ~115% of an undefined universe rather than 100% of the real expansion adult population.

The fix has two parts: (1) add a population funnel overview using research-backed national numbers, and (2) restructure the archetype table into three tiers that together cover 100% of the 20.1M Medicaid expansion adults subject to HR1.

---

## Research Findings (Sources)

| Stage | Number | Confidence | Source |
|---|---|---|---|
| Total expansion adults enrolled | 20.1M | High | CBPP/CBO, March 2025 |
| Subject to HR1 CE per CBO | 18.5M | High | CBO, cited by KFF |
| Formally exempt (various categories) | ~40% (~8M) | Low-Moderate | Derived from KFF SIPP methodology + state waiver precedent |
| Non-exempt, auto-verified via ex parte | ~30% (~6M) | Low-Moderate | Urban Institute (~52% of all adults could be data-matched); AR precedent 60-83% of non-exempt |
| Non-exempt, Emmy activates | ~30% (~6M) | Low-Moderate | Residual; consistent with CBO 5.2-6M coverage loss projection |

**KFF SIPP caveat (critical):** The "53% working, 9% in school, 17% likely exempt, 21% at risk" breakdown was calculated AFTER filtering out parents of under-18 children, SSI/SSDI recipients, Medicare dual-enrollees, and pregnant people. The 21% at-risk figure is NOT 21% of all 20.1M adults — it's 21% of a pre-filtered subgroup that represents roughly 50% of the total expansion population. True at-risk share of full population: ~8-12%.

---

## Changes to `/Users/paul/Desktop/HR1 CE Reqs/03-Research-Insights/beneficiary-archetypes-table.md`

### 1. Add Population Funnel Section (after "How Emmy Fits In")

New section with a 3-row summary table:

| Stage | Est. % of Expansion Adults | Est. Number | Notes |
|---|---|---|---|
| **Formally exempt** | ~40% | ~8M | State identifies via data match or self-attestation at application; no Emmy |
| **Non-exempt, auto-verified** | ~30% | ~6M | Ex parte data confirms compliance; no Emmy |
| **Non-exempt, Emmy activates** | ~30% | ~6M | Ex parte couldn't fully verify; Emmy resolves the gap |
| **Total** | 100% | ~20.1M | March 2025 enrollment, 41 states + DC |

Include a note: all percentages are rough estimates with wide confidence intervals. The exempt share in particular will vary significantly by state demographics. Figures will sharpen after Nebraska's May 2026 launch and CBO's post-rule modeling.

### 2. Restructure the Archetype Table into Three Tiers

Replace the single flat table with three clearly labeled tier sections. All `Est. % of Population` values are expressed as % of all 20.1M expansion adults. The sum across all three tiers = ~100%.

---

#### Tier 0: Formally Exempt (~40% total)

New archetypes. Columns: Category | Archetype | Est. % | Exemption Basis | How State Typically Identifies | Policy Questions

| Category | Archetype | Est. % | Exemption Basis | How State Typically Identifies |
|---|---|---|---|---|
| CAREGIVING | Parent/guardian of child ≤13 or disabled dependent | ~20% | HR1 §71119 explicit exemption | Household composition data from application; SNAP/TANF records |
| DISABILITY | Medically frail (no formal disability income) | ~8% | Medically frail CMS standard | Diagnosis codes, prior auth records, self-attestation with provider letter; significant fall-off between eligible and successfully documented (NH: 82% drop-off) |
| WORK PROGRAMS | SNAP/TANF work requirement complier | ~5% | Already subject to other work requirement | Cross-program data match (SNAP, TANF records) |
| PREGNANCY | Pregnant or postpartum | ~1% | HR1 explicit exemption | Pregnancy data in eligibility system; CHIP/maternity enrollment |
| OTHER | AI/AN, SUD active treatment, recently incarcerated, 100% disabled veteran, foster youth | ~6% | Multiple HR1 explicit exemptions | Tribal status, treatment program enrollment, incarceration records, VA disability rating, foster care records — each requires a separate data match |

**Tier 0 subtotal: ~40%**

---

#### Tier 1: Non-Exempt, Auto-Verified via Ex Parte (~30% total)

New archetypes. These people have CE compliance confirmed automatically — they never reach Emmy. Columns: Category | Archetype | Est. % | Ex Parte Data Source | Notes

| Category | Archetype | Est. % | Ex Parte Data Source |
|---|---|---|---|
| EMPLOYMENT | Steady W-2 worker, payroll confirmed | ~18% | SWICA/state wage records, Work Number, or SWICA confirming 80+ hrs/month or ≥$580/month income |
| EMPLOYMENT | Income-path compliant, wage data confirmed | ~6% | Payroll/wage data confirms ≥$580/month regardless of hours |
| EDUCATION | Full-time student, enrollment auto-confirmed | ~4% | National Student Clearinghouse (NSC) or state higher ed database |
| WORK PROGRAMS | State work program participant, confirmed | ~2% | State work program database (where it exists and is connected) |

**Tier 1 subtotal: ~30%**

Note: Ex parte verification rates vary widely by state system maturity. California's early 2026 data match verified ~36% of its expansion population; Arkansas's mature system (2018-19) verified 60-83% of non-exempt adults. The ~30% above is a national central estimate.

---

#### Tier 2: Non-Exempt, Emmy Activates (~30% total)

Existing archetypes, with recalibrated % values (now as % of all 20.1M expansion adults, summing to ~30%). Add two new columns from the previous update: `Typical Application Attestation` and `Emmy Activation Type`.

New % assignments (recalibrated from prior ad hoc estimates):

| Archetype | Old % | New % (of all 20.1M) |
|---|---|---|
| Steady Full-Time Employee (payroll insufficient) | ~25-30% | ~5% |
| Multiple Part-Time Jobs Worker | ~8-12% | ~2% |
| Reduced Hours Worker + Volunteer Combo | ~5-7% | ~1.5% |
| Recently Employed / Job Churn | ~10-15% | ~3% |
| Seasonal / Temporary Worker | ~4-6% | ~1.5% |
| Cash / Under-the-Table Worker | ~5-8% | ~2% |
| Health Fluctuation Worker | ~6-9% | ~2% |
| Self-Employed / Gig Worker (High Volume) | ~6-8% | ~2% |
| Inconsistent Gig Worker | ~8-10% | ~2.5% |
| Full-Time Student (auto-confirm failed) | ~5-8% | ~2% |
| Part-Time Student + Work/Volunteer Combo | ~3-5% | ~1.5% |
| Student on Summer / Winter Break | ~1-2% | ~0.5% |
| Recently Graduated Student | ~1-2% | ~0.5% |
| Active Job Training / Workforce Program | ~3-5% | ~1% |
| High-Hour Volunteer | ~2-3% | ~1% |
| Informal Caregiver (non-exempt) | ~3-5% | ~1% |

**Tier 2 subtotal: ~30%** ✓

### 3. Update Summary Statistics Section

Replace current summary with:
- Funnel recap (Exempt ~40% / Auto-verified ~30% / Emmy pool ~30%)
- Within Emmy pool: "Likely to Meet" vs. "On the Fence" vs. "Unknown" breakdown
- Note that "likely to meet" in the Emmy tier means "will meet with documentation" not "meets without any documentation"
- Data confidence disclaimer referencing KFF, CBO, Urban Institute sources

### 4. Update Emmy Activation Type Distribution Table

Keep as-is — it covers the ~30% Emmy pool and the Distribution table's percentages (Documentation ~40-50%, Documentation + Gap ~35-45%, Cold ~10-15%) are % of Emmy sessions, not % of all expansion adults. Add a clarifying note to that effect.

### 5. Add Data Sources Section at Bottom

List the key sources used for population figures:
- KFF SIPP analysis (June 2022 data) — with the denominator caveat explained
- CBO HR1 coverage impact estimates
- Urban Institute coverage loss assessment
- Arkansas ARWorks waiver data (2018-2019) — ex parte precedent
- California KFF analysis (April 2026) — early data match rates

---

## Key Decisions / Assumptions

1. **Percentages are of total 20.1M** — not of the Emmy pool or filtered subgroup. This is the most useful denominator for understanding program scale.
2. **Ranges replaced with single central estimates** — the old ranges (~5-8%) made summing impossible. New values use a single point estimate with a note that confidence is low-moderate.
3. **"Steady Full-Time Employee" stays in Tier 2** — represents the subset whose payroll data couldn't verify compliance (not all steady employees; those auto-verified are captured in Tier 1).
4. **Exempt archetypes don't have "Emmy Activation Type"** — they exit the funnel before Emmy is relevant.

---

## File to Edit

`/Users/paul/Desktop/HR1 CE Reqs/03-Research-Insights/beneficiary-archetypes-table.md`
