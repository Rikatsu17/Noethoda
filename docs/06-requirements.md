# Oiqyn — Requirements Specification

**Project:** Development of a Literacy Platform with Personalized Learning Recommendation  
**Team:** Adilbekov Daniyal (SE-2414); Rassul Sakenov (SE-2403)  
**Status:** Initial draft for team and supervisor review  
**Related deliverable:** First pre-defense, 24 October 2026

## 1. Purpose, Users, and Evidence Status

This document defines what the proposed Oiqyn MVP must do and how its
implementation will be checked. It describes future behavior, not completed
features or passed tests.

The target audience is **university students aged 18 and over across different
years of study** who want to improve their IT and digital literacy skills.
Recommendations depend on assessed skills and learning needs, not year of study.

The requirements are derived from the project proposal in the README, the
literature review, the existing-system comparison, and the provisional
technology decisions. User interviews and survey findings have not yet been
provided. These requirements must therefore be reviewed against actual user
evidence; none is presented as an interview-confirmed need.

Two application roles are proposed:

| Role | Responsibilities |
|---|---|
| Learner | Complete assessments, study activities, view recommendations and personal progress. |
| Content administrator | Manage skills, learning materials, questions, and prerequisite links. |

The team will also run evaluation scripts. This does not require a separate
evaluation dashboard or another application role.

### Priorities

| Priority | Meaning |
|---|---|
| Must | Mandatory for the proposed MVP. Every acceptance criterion must pass before this requirement is marked complete. |
| Should | Desirable, but may be deferred with a recorded reason and supervisor discussion. |
| Could | Optional future improvement; excluded from the current delivery commitment. |

Priorities and numerical targets below are **project proposals**, not approved
stakeholder commitments or measured results. For this pre-defense, the
deliverable is a reviewed specification; implementing every requirement is a
later diploma-project stage.

## 2. Scope and Operational Rules

The core journey is: account creation → diagnostic assessment → skill profile →
recommended activity and explanation → practice and feedback → updated progress.

The content covers IT and internet fundamentals, information literacy, digital
safety, and digital productivity. As a proposed minimum for the prototype,
include one defined skill and one learning activity in each area, with at least
two scored diagnostic questions and two activity-assessment questions per skill.
This small content set supports a technical demonstration, not comprehensive
coverage of digital competence.

These draft rules make acceptance checks reproducible:

| Rule | Proposed behavior |
|---|---|
| R1 — Assessment evidence | Each scored question has one primary skill and a versioned answer key. In the initial prototype, a correct answer scores 1 and an incorrect answer scores 0. A skipped question supplies no scored evidence. |
| R2 — Skill status | Use the latest submitted assessment containing at least two scored responses for the skill. Its score is correct responses divided by scored responses. A score of at least 70% means “Target met”; a lower score means “Needs practice”. Without such an assessment, show “Insufficient evidence”. |
| R3 — Profile updates | An attempt with insufficient evidence does not replace an earlier qualifying result. Show the date of the evidence used. Lesson completion alone never changes a skill status. |
| R4 — Eligibility | An activity is eligible when it is published, targets at least one skill marked “Needs practice”, and every prerequisite skill is marked “Target met”. An unknown prerequisite does not count as satisfied. A previously completed activity may be recommended as review if the learner still needs practice. |
| R5 — Ranking and baseline | Apply the same eligibility filter to both methods. The proposed method ranks eligible activities using versioned rules and content features; the baseline follows a fixed, documented activity order. Neither method uses year of study as a skill estimate. |
| R6 — Missing recommendations | Return an activity only when an eligible candidate exists. Otherwise distinguish: more assessment needed; all represented skills at target; or no eligible content for the current gaps. If gaps and unknown skills coexist, report both limitations. |

The two-response minimum and 70% threshold are simple operational settings
proposed for the prototype. They are not validated measures of digital
competence. The team and supervisor must review them before freezing the
implementation baseline. Ranking weights and tie-breaking will be specified in
the planned `docs/07-recommendation-design.md`; a recommender cannot pass its
acceptance checks until those rules are documented and versioned.

Native mobile apps, payments, official certification, university-system
integration, training a large language model, and large-scale deployment remain
outside the initial MVP.

## 3. Functional Requirements

| ID | Priority | Requirement | Acceptance criteria |
|---|---|---|---|
| FR-01 | Must | Account registration and authentication | A new learner can register with a valid email and password, sign in, and sign out. Empty required fields, duplicate email registration, and incorrect credentials produce a clear error. Registration cannot grant administrator privileges. After sign-out, the previous session cannot access protected resources. |
| FR-02 | Must | Access control | Learner A can retrieve A's assessment and progress records. Requests to read or change learner B's records are denied by the backend, including requests made directly to the API. An unauthenticated request cannot access personal records. A learner cannot use administrator content-management operations. |
| FR-03 | Must | Initial diagnostic assessment | A learner can view the diagnostic instructions, answer questions, explicitly skip questions, and submit the attempt. Each question is linked to a defined skill and content version. The assessment covers the four content areas. Skipped answers remain distinguishable from incorrect answers. |
| FR-04 | Must | Assessment scoring and feedback | The backend calculates the result using the stored question version and answer key, rather than trusting a score sent by the browser. A fixture with two correct and two incorrect answers scores 50%. An all-skipped attempt shows “Insufficient evidence” without a percentage score. Unknown question IDs and answers outside the attempt are rejected without saving a result. After submission, the learner sees the result and answer explanations. |
| FR-05 | Must | Evidence-based skill profile | The profile lists each represented skill, its status, and the evidence date where available. Under R2, zero or one scored response without earlier qualifying evidence gives “Insufficient evidence”; two incorrect answers give “Needs practice”; two correct answers give “Target met”. An incomplete later assessment preserves the previous qualifying result. Opening or completing a lesson does not change these statuses. |
| FR-06 | Must | Personalized next activity | Given a profile, content version, and recommendation-configuration version, the system applies R4 and R5. Prepared cases must show zero prerequisite violations and no unpublished activities. A documented tie-breaking rule makes identical inputs produce the same result. Changing relevant assessment evidence can change the recommendation; changing only year of study cannot. |
| FR-07 | Must | Recommendation explanations and empty states | Every recommendation includes a learner-readable reason identifying the relevant skill need and the assessment evidence used. The stored decision identifies its profile, content, and rule versions so the reason can be checked. Where no candidate exists, return an appropriate R6 state with a clear next step, such as completing assessment or reviewing the skill profile; do not fabricate an activity or claim that an unknown skill is at target. |
| FR-08 | Must | Learning activities and practice | A learner can open an available activity, read its objective and material, record completion, and submit its related assessment. Completion and assessed skill status are stored separately. A learner can attempt the assessment again; a new attempt is retained and updates the profile according to R2–R3. If a completed activity is recommended again, the interface labels it as review. |
| FR-09 | Must | Personal progress dashboard | The learner can view completed activities, assessment attempts with scores and dates, current skill statuses, and the next recommendation or empty state. After refresh or a new sign-in, committed records remain available. Displayed totals match the stored records and do not count an identical submission retry as a new attempt. |
| FR-10 | Must | Content administration | An authorized administrator can create and edit draft skills, activities, questions, feedback, and prerequisite links; publish valid content; and archive activities. Publishing rejects missing skill references, missing answer keys, and prerequisite cycles. Learners cannot start archived or draft activities. Previously saved results remain accessible after content is archived. |
| FR-11 | Must | Versioned learning records | Editing published assessment content creates a new version. A submitted attempt retains the question version, answers, score, and scoring-rule version used at submission. Changing a correct answer later does not silently change historical scores. New attempts use the applicable published version; an already started attempt remains tied to its original version. |
| FR-12 | Must | Reproducible recommendation comparison | A documented script or command runs the proposed method and fixed-order baseline on the same versioned content and at least 20 prepared profiles. Cases cover missing evidence, low scores, unmet prerequisites, ties, no eligible content, and all skills at target. Output records the inputs, versions, selected activity or empty state, and eligibility checks for both methods. Repeating the run with unchanged inputs reproduces the results. |
| FR-13 | Should | Progress filtering | The learner can filter assessment history by skill and restore the full history. Filtering changes the displayed subset without changing stored results or profile scores. |

The prepared profiles in FR-12 are test fixtures. They are not actual
participants, training data, or evidence of improved learning. A bookmarking
feature may be considered later as a Could item, but is not part of the current
MVP commitment.

## 4. Non-functional Requirements

| ID | Priority | Requirement | Acceptance criteria and conditions |
|---|---|---|---|
| NFR-01 | Must | Credential and session protection | Passwords are stored using salted Argon2id, with the proposed minimum configuration of 19 MiB memory, two iterations, and parallelism 1, following OWASP guidance [S1]. Two accounts using the same password have different stored hashes. Inspection of database records, API responses, and logs finds no plaintext passwords or logged session credentials. An internet-accessible deployment uses HTTPS for authentication and protected requests. |
| NFR-02 | Must | Consistent and duplicate-safe assessment writes | Attempt results and the corresponding profile update commit together. A simulated database failure during submission leaves neither a partial result nor a partial profile change. Two concurrent submissions with the same attempt ID and identical answers create exactly one submitted attempt and return the same saved result. Reusing that submitted ID with different answers is rejected. A deliberate retake receives a new attempt ID. |
| NFR-03 | Must | Basic accessibility | On registration, assessment, activity, and progress screens, a keyboard user can reach and operate every interactive control with visible focus and no keyboard trap. Inputs have programmatically associated labels, and skill status is communicated with text as well as color. Text contrast is at least 4.5:1 for ordinary text and 3:1 for large text, using the WCAG definitions and exceptions [S2]. Record manual keyboard checks and contrast measurements. These are selected checks, not a claim of full WCAG conformance. |
| NFR-04 | Must | Responsive browser interface | The core journey works at 360 × 800 and 1366 × 768 CSS-pixel viewports in the stable Chrome and Firefox releases selected for testing. Record exact browser versions. No required button, question, or result is clipped or inaccessible. At 200% zoom on the desktop viewport, the same tasks remain possible without lost content or controls. |
| NFR-05 | Should | API responsiveness | Under test profile P1 below, the 95th-percentile response time is at most 1 second for progress and recommendation requests, and 2 seconds for assessment submissions. The combined proportion of server errors and requests exceeding the 5-second timeout is below 1%. Report latency separately for each operation and count timeouts as failures. |
| NFR-06 | Should | Usability of the main journey | In a formative test with five consenting adult students from at least two years of study, at least four complete assessment, interpret their recommendation, finish one activity, and locate their updated progress within 15 minutes without moderator assistance. Record task success, time, help requests, and observed problems. This is a proposed local usability target, not a population estimate. |
| NFR-07 | Must | Reproducible setup and verification | Another team member can start the application from a clean checkout using documented prerequisites, locked dependency versions, database migrations, seed content, and example configuration without real secrets. The documented check command runs the available automated acceptance tests. Every Must requirement has a recorded automated or manual verification result tied to the tested commit; all its criteria must pass before it is accepted. |

**P1 — Proposed performance test conditions:** API and PostgreSQL on one test
host with 4 vCPU and 8 GB RAM; record operating system and software versions.
Use synthetic data for 1,000 learners, 40 skills, 100 activities, and 10,000
submitted attempts. Run a separate load generator with 10 virtual users, each
issuing one request per second, with a 60-second warm-up followed by five
minutes of measurement. The request mix is 50% progress reads, 30%
recommendation requests, and 20% valid assessment submissions with unique
attempt IDs. Measure end-to-end API request latency from the load generator
over the test network. Record achieved request rate and any missed scheduled
requests; a run that cannot sustain the stated load is not a passing run.

P1 describes a synthetic workload for evaluation, not a requirement to author
100 real learning activities. The performance and usability targets have not
been tested or approved.

## 5. Traceability and Planned Verification

The following identifiers describe planned verification groups, not completed
test files. Detailed procedures, fixtures, rating rubrics, and measurement
records will be maintained in the planned
`docs/08-verification-evaluation.md`.

| Group | Requirements | Planned check | Basis |
|---|---|---|---|
| V1 — Accounts and permissions | FR-01, FR-02, NFR-01 | Registration, sign-in/out, direct API authorization checks, credential-storage inspection. | README account scope; technology drivers D1–D2. |
| V2 — Assessment and evidence | FR-03, FR-04, FR-05, FR-11, NFR-02 | Known-answer fixtures, missing-evidence cases, content-version changes, concurrent retries, and failed transactions. | README diagnostic/profile scope; drivers D3–D4. |
| V3 — Recommendations | FR-06, FR-07, FR-12 | Prepared profiles, prerequisite checks, explanation audit, deterministic repeat runs, and baseline comparison. | README recommendation design; drivers D5–D6 and D8. |
| V4 — Learning and content | FR-08, FR-09, FR-10, FR-13 | Student learning scenario, dashboard reconciliation, and administrator publishing/archiving scenario. | README learning/content scope; driver D2. |
| V5 — Interface quality | NFR-03, NFR-04, NFR-06 | Keyboard, contrast, viewport, zoom, and formative usability checks. | README responsive interface; proposed design targets. |
| V6 — Delivery quality | NFR-05, NFR-07 | P1 workload, clean setup, and review of acceptance evidence. | Two-person MVP constraint; drivers D1 and D7. |

D1–D8 refer to `docs/05-technologies.md`. The provisional implementation remains
React/TypeScript, FastAPI, PostgreSQL, and a recommendation module inside the
backend. These choices do not replace acceptance checks.

Adilbekov Daniyal will lead backend, data-integrity, scoring, recommendation,
and performance checks. Rassul Sakenov will lead interface, accessibility,
responsive-layout, and usability checks. Both will review the requirements
and integration results.

Functional acceptance proves that the system follows its specified rules.
Recommendation usefulness and any learning improvement require separate
evaluation. The comparison must allow the baseline to perform equally well
or better; superiority is not an acceptance condition.

## 6. Review and Change Control

Before treating this draft as the implementation baseline:

1. Review needs and priorities using real user discussions and any available
   survey findings. Record supported findings separately from assumptions.
2. Ask the supervisor to review the scope, assessment rules, minimum content
   set, priorities, and proposed evaluation targets.
3. Finalize and version the ranking rules, weights, and tie-breaking in
   `docs/07-recommendation-design.md`.
4. Align the context, use case, and component diagrams and interface mockups
   with the requirement IDs.
5. Record each accepted change, its reason, affected requirement IDs, and
   linked YouTrack issue and GitHub pull request.

**Current review state:** No supervisor approval or implementation test result
is recorded in this document. A review by Rassul can check document consistency;
it does not substitute for supervisor feedback or user evidence.

## 7. Technical References

- **[S1]** OWASP, [Password Storage Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html).
  Used for the proposed password-storage configuration in NFR-01.
- **[S2]** W3C, [Web Content Accessibility Guidelines (WCAG) 2.2](https://www.w3.org/TR/WCAG22/).
  Used for the selected accessibility checks in NFR-03; see criteria 1.4.1,
  1.4.3, 2.1.1, 2.1.2, 2.4.7, and 4.1.2.

These technical references support specific implementation constraints. They
do not establish demand for Oiqyn or validate the proposed learning-assessment
thresholds.

