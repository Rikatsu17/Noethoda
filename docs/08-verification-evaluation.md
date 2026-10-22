# Oiqyn — Verification and Evaluation Plan

**Project:** Development of a Literacy Platform with Personalized Learning Recommendation  
**Team:** Adilbekov Daniyal (SE-2414); Rassul Sakenov (SE-2403)  
**Status:** Draft plan for team and supervisor review; application verification and participant studies pending  
**Related deliverable:** First pre-defense, 24 October 2026

## 1. Purpose and Current Evidence

This plan explains how the team will check that Oiqyn implements its requirements
and assess the usefulness of its recommendations and interface. The audience is
university students aged 18 and over across different years of study.

The plan is based on [06-requirements.md](06-requirements.md),
[07-recommendation-design.md](07-recommendation-design.md),
the [architecture diagrams](../diagrams/README.md), and the
[UX prototype](../prototype/README.md). Requirement IDs, priorities, and proposed
thresholds retain the meanings given in document 06.

Three questions require different evidence:

| Question | Evidence to collect |
|---|---|
| Does the application implement its specified behavior? | Automated and manual acceptance checks linked to every requirement. |
| Are its next-activity choices useful compared with a simpler method? | Reproducible baseline comparison and independent review of candidate relevance. |
| Can target users complete the main journey? | Observed task completion, time, assistance, and problems in a formative usability test. |

A working interface, correct algorithm, or favorable relevance rating does not
by itself prove improved learning. Learning gains are not claimed in this plan.

The existing browser-only prototype has documented demonstration checks in its
README. It has no production authentication, FastAPI service, or PostgreSQL
database. Its checks do not establish server security, persistent data integrity,
API performance, or complete requirement acceptance.

For the pre-defense, this deliverable is a reviewable evaluation plan. Future
application tests must not be presented as already completed.

## 2. Test Levels and Ownership

| Level | Scope | Lead |
|---|---|---|
| Unit | Scoring, evidence selection, eligibility, ranking, tie-breaking, empty states. | Daniyal |
| Integration | FastAPI authorization, PostgreSQL transactions, content versions, concurrent submissions. | Daniyal |
| End-to-end | Learner and administrator journeys through the interface and backend. | Both |
| Interface quality | Keyboard access, labels, contrast, viewport behavior, zoom, and usability sessions. | Rassul |
| Evaluation | Shared-fixture baseline comparison, relevance review, and reporting. | Daniyal; both review interpretation |
| Reproducibility | Clean setup and independent rerun by the other team member. | Both |

Unit fixtures use synthetic records. Integration checks use an isolated test
database. Performance tests use generated data and a separate test deployment.
Do not run destructive fixtures against real learner records.

The supervisor will be asked to review the protocol, content assumptions, and
interpretation. No supervisor agreement or review is recorded yet.

## 3. Acceptance Test Register

These are planned check groups, not existing test files or passing results.
Each group will have individual cases and evidence for every listed criterion.
The full wording in document 06 remains authoritative.

| Test group | Requirements | Procedure and expected outcome |
|---|---|---|
| T01 — Accounts | FR-01 | Register, sign in, and sign out. Check empty required fields, duplicate email, and incorrect credentials. Reject self-assigned administrator privileges. Confirm that the old session cannot access protected resources after sign-out. |
| T02 — Authorization | FR-02 | Use two learners and one administrator. Call the API directly as anonymous, learner A, and learner B. Deny access to another learner's records and learner access to content-management operations; allow authorized own-record and administrator actions. |
| T03 — Diagnostic and scoring | FR-03, FR-04 | Cover all four areas with versioned questions and explicit skipping. Verify 2 correct + 2 incorrect = 50%; all skipped = no percentage and insufficient evidence. Ignore any browser-supplied score and calculate from stored keys. Reject unknown or out-of-attempt question IDs without saving a result. Show answer explanations. |
| T04 — Skill evidence | FR-05 | With no prior evidence, 0 or 1 scored response gives insufficient evidence, 0/2 gives needs practice, and 2/2 gives target met. A later incomplete attempt preserves the earlier qualifying result and its date. A later qualifying attempt updates it. Opening/completing a lesson alone changes no skill score. |
| T05 — Recommendations | FR-06, FR-07 | Execute Section 4; audit eligibility, exact selected item/state, review flag, explanation evidence, and stored versions. Repeat with reordered candidates and changed year of study. Reject invalid snapshots/configuration; do not return TARGETS_MET for invalid input. |
| T06 — Learning and progress | FR-08, FR-09, FR-13 | Open an available lesson, read objective/material, complete it, submit practice, and retake with a new attempt ID. Keep completion separate from assessed skill. Show review labeling, scores, dates, statuses, and next step. Refresh and sign in again: committed records remain. Reconcile totals with storage; retries do not increase totals. Skill filtering changes only the displayed subset. |
| T07 — Content administration | FR-10 | Create/edit drafts for skills, activities, questions, feedback, and prerequisites. Publish valid content. Reject missing skill references, missing keys, self-dependencies, and cycles. Deny learner starts of drafts/archives. Archive a previously recommended activity: opening it must recheck availability and request a new choice, retaining old results and decision history. |
| T08 — Version history | FR-11 | Start an attempt on version 1, publish a changed answer key as version 2, then submit the original attempt. It must use version 1. A new attempt uses version 2. Retain question versions, answers, scores, and scoring-rule versions; historical scores must not silently change. |
| T09 — Comparison runner | FR-12 | Run both methods on the same versioned fixtures; retain inputs, outputs, candidate exclusions, and versions. Rerun unchanged inputs and compare substantive outputs, excluding run timestamps/IDs. The command and artifacts must be reproducible. |
| T10 — Credentials and sessions | NFR-01 | Inspect configured Argon2id parameters against document 06. Two accounts with the same test password must have different salted hashes. Inspect database records, API responses, and logs for plaintext passwords or logged session credentials. Check HTTPS for authentication/protected requests on an internet-accessible deployment. |
| T11 — Atomic and duplicate-safe writes | NFR-02 | Inject failures between attempt and profile writes and immediately before commit: neither partial result nor partial profile persists. Submit identical answers concurrently twice under one attempt ID: exactly one attempt and the same saved result. Different answers under that submitted ID are rejected. A deliberate retake has a new ID. |
| T12 — Accessibility and layout | NFR-03, NFR-04 | Run the screen/browser checks in Section 7; retain keyboard observations, contrast measurements, viewport/zoom evidence, and exact browser versions. |
| T13 — API workload | NFR-05 | Run P1 in Section 8. Record latency per operation, failures, actual request rate, and missed schedules. |
| T14 — Usability | NFR-06 | Run the five-participant protocol in Section 6 and report success, time, assistance, and problems. |
| T15 — Setup and evidence | NFR-07 | The other member starts from a clean checkout using documented prerequisites, locked dependencies, migrations, seed data, and example configuration without real secrets. Run the documented checks. Confirm a commit-linked result for every Must criterion. |

FR-13, NFR-05, and NFR-06 are Should requirements. All other IDs in this table
are Must requirements. A group covering both priorities must report its
individual criteria separately.

A group is not accepted because one example passes. For example, passing normal
sign-in does not also pass session invalidation or administrator restrictions.

## 4. Recommendation Fixtures and Baseline

### 4.1 Frozen comparison conditions

Use configuration **recommendation-v0.1** and the six-activity catalogue in
document 07. Freeze a catalogue snapshot named **evaluation-catalogue-v1** before
the first run. Both methods receive identical evidence, completion records,
catalogue overrides, and configuration for common eligibility.

The proposed method applies the documented gap/difficulty/completion score.
The baseline applies the same eligibility and empty-state rules, then selects
the first candidate by baseline order and stable ID. Never compare against a
baseline that is forced to recommend blocked or unpublished content.

For reference:

| Activity | Target | Difficulty | Prerequisites | Fixed order |
|---|---|---|---|---|
| A01 | S01 | 1 | None | 1 |
| A02 | S02 | 1 | None | 2 |
| A03 | S03 | 1 | S01 | 3 |
| A04 | S04 | 2 | None | 4 |
| A05 | S03 | 2 | S01 | 5 |
| A06 | S02 | 2 | None | 6 |

S01 = web addresses; S02 = checking claims; S03 = phishing;
S04 = spreadsheet formulas. All activities are published and uncompleted
unless an override is listed.

### 4.2 Twenty prepared cases

The vector is **[S01, S02, S03, S04]**. A fraction means correct/scored answers
in the latest qualifying attempt. **?** means no qualifying evidence, with a
null score. Every case has its own profile ID, evidence IDs, and snapshot version.
These are synthetic cases, not participants or collected survey responses.

The expected outputs below are specification-derived expectations.
They are not results of running the future backend.

| Case | Profile vector | Setup or purpose | Proposed output | Baseline output |
|---|---|---|---|---|
| P01 | [?, ?, ?, ?] | No submitted evidence. | ASSESSMENT_REQUIRED | ASSESSMENT_REQUIRED |
| P02 | [?, ?, ?, ?] | One scored answer per skill, counts [0/1, 1/1, 0/1, 1/1]; no earlier evidence. | ASSESSMENT_REQUIRED | ASSESSMENT_REQUIRED |
| P03 | [?, ?, ?, ?] | Two skipped questions per skill; no earlier evidence. | ASSESSMENT_REQUIRED | ASSESSMENT_REQUIRED |
| P04 | [?, 1/2, 2/2, 2/2] | Known information-literacy gap alongside an unknown unrelated skill. | A06 | A02 |
| P05 | [2/2, 2/2, 0/2, 2/2] | Zero correct answers is a known gap, not missing evidence. | A03 | A03 |
| P06 | [2/2, 2/2, 1/2, 2/2] | Mid-range gap prefers difficulty 2. | A05 | A03 |
| P07 | [2/2, 2/2, 7/10, 2/2] | Exact 70% boundary meets the target. | TARGETS_MET | TARGETS_MET |
| P08 | [2/2, 2/2, 10/10, 2/2] | Full score meets the target. | TARGETS_MET | TARGETS_MET |
| P09 | [?, 2/2, 0/2, 2/2] | Unknown S01 blocks A03 and A05. | NO_ELIGIBLE_CONTENT | NO_ELIGIBLE_CONTENT |
| P10 | [0/2, 2/2, 0/2, 2/2] | Low S01 blocks phishing activities; A01 remains eligible. | A01 | A01 |
| P11 | [7/10, 2/2, 1/3, 2/2] | Prerequisite exactly at target permits phishing practice. | A03 | A03 |
| P12 | [2/2, 1/2, 0/2, 2/2] | Override: both A03 and A05 require S01 AND S02. S02 fails one prerequisite. | A06 | A02 |
| P13 | [2/2, 1/2, 0/2, 1/2] | Worked example from document 07. | A03 | A02 |
| P14 | [2/2, 1/2, 2/2, 1/2] | A04 and A06 tie at 50; fixed order selects A04. | A04 | A02 |
| P15 | [2/2, 1/2, 0/2, 1/2] | A03 previously completed: score becomes 90, remains top, and is marked Review. | A03 (Review) | A02 |
| P16 | [2/2, 1/2, 2/2, 1/2] | Start from P13, then submit a new qualifying S03 result of 2/2; preserve earlier attempt history. | A04 | A02 |
| P17 | [7/10, 7/10, 7/10, 7/10] | All represented skills meet target; no claim about unassessed competence. | TARGETS_MET | TARGETS_MET |
| P18 | [2/2, 1/2, 2/2, 2/2] | Override: A02 and A06 unpublished; no published activity targets the remaining gap. | NO_ELIGIBLE_CONTENT | NO_ELIGIBLE_CONTENT |
| P19 | [0/2, 2/2, 0/2, 2/2] | Override: A01 unpublished; both published phishing candidates blocked by S01. | NO_ELIGIBLE_CONTENT | NO_ELIGIBLE_CONTENT |
| P20 | [?, 2/2, 0/2, ?] | Report the S03 gap, unknown S01 prerequisite, and unknown S04; do not invent scores. | NO_ELIGIBLE_CONTENT | NO_ELIGIBLE_CONTENT |

P01–P03 intentionally reach the same profile state through different evidence
histories. P14 and P16 distinguish a static tie from an assessment-driven update.
Catalogue overrides are explicit fixture snapshots applied equally to both
methods.

The 20 cases cover the groups in document 07, but are not an exhaustive test
suite. Add unit cases for the 0.35 difficulty boundary, stable-ID tie-breaking
when baseline orders match, invalid registries/configuration, and mixed
completion versions. These extra cases do not count as additional participants.

### 4.3 Expected invariants and metrics

For every fixture, retain the full candidate set, exclusion reasons, score
factors, selected output, explanation inputs, and relevant versions.

| Measure | Calculation and proposed acceptance |
|---|---|
| Expected-output agreement | Correct selected activity or empty state / 20, separately per method; target 20/20. |
| Eligibility violations | Selected activities that violate publication, target-skill, or prerequisite rules / all selected activities; target zero violations for each method. |
| Empty-state correctness | Correct states and reported gaps/unknowns/blockers / cases with no eligible item; target all correct. |
| Explanation consistency | Decisions whose explanation matches actual evidence, eligibility, completion flag, and ranking reason / audited decisions; target all correct. Baseline reasons must state fixed-order selection. |
| Determinism | Repeat each fixture three times and once with candidate order reversed; all substantive outputs must match the original run. |
| Year-of-study invariance | Change only year of study for each fixture; selected outputs and evidence-based reasons must remain unchanged. |
| Trace completeness | Decisions retaining profile, catalogue, rule versions, and evidence references / all decisions; target all complete. |

Report numerators and denominators, not percentages alone. Use “not applicable”
when a denominator is zero. Invalid-input errors are checked separately and must
not be counted as successful empty states.

The internal ranking score is not a recommendation-quality metric. A03 scoring
higher than A02 only demonstrates the specified formula, not educational benefit.

## 5. Independent Review of Recommendation Relevance

After the technical checks pass, arrange two reviewers familiar with digital
skills teaching. Recruitment and availability are pending. This is a proposed
review, not a completed agreement with the supervisor.

Before showing method outputs, freeze the rating rubric and record catalogue,
fixture, and configuration versions. Reviewers first work independently.

Show the learner evidence, prerequisites, activity objective, and learning
material. Hide method names, internal ranking scores, and presentation order
cues. Randomize candidate order with a recorded seed. If both methods choose
the same activity for a case, present it once and assign its rating to both
methods. Count that case as agreement, not two independent observations.

Rate next-activity relevance using this rubric:

| Rating | Meaning |
|---|---|
| 0 — Unsuitable | Does not address a demonstrated need or requires knowledge the profile does not support. |
| 1 — Weak | Related to a gap, but material or challenge is poorly matched; a substantial revision is needed. |
| 2 — Appropriate | Addresses a demonstrated gap with plausible readiness and challenge; minor reservations may remain. |
| 3 — Strong | Clear, well-supported next step for the stated evidence and available content. |

Reviewers must provide a short reason, including concerns about assessment
quality or authored difficulty labels. Keep original ratings when reviewers
later discuss disagreements.

For cases where both methods return an activity, report per-case ratings,
method agreement, and reviewer-specific win/tie/loss counts for the proposed
method. Summarize ratings descriptively; show cases with one eligible candidate
separately from cases with alternatives. Review empty-state usefulness separately
and exclude it from activity-rating averages.

If only one reviewer is available, report the deviation and the absence of
inter-reviewer comparison. Do not describe the review as independent if the
algorithm author is the only rater.

**Evaluation question:** Does the proposed ranking produce more appropriate
next steps than the fixed eligible order on these cases? Equal or worse results
are valid findings. No superiority threshold is an implementation acceptance
condition. The small, authored catalogue and fixtures limit generalization;
no statistical or learning-effect claim follows from this comparison.

If weights are revised after seeing ratings, version the revision and label
those cases as development evidence. Use additional, previously unrated cases
before describing a new comparison as a fresh evaluation.

## 6. Formative Usability Test

This protocol implements the proposed Should target NFR-06.

**Participants:** five consenting university students aged 18 or over from at
least two years of study. Do not recruit only first-year students. Record broad
experience with digital learning without using year of study as an ability
estimate.

**Environment:** the same recorded build, starting scenario, sample content,
device/browser setup, and instructions. Use a fresh test account or reset demo
state for each participant. A prototype session evaluates that prototype; it
does not pass production requirements automatically.

**Session:** give a neutral introduction and obtain consent for observation.
Use participant codes U01–U05. Record elapsed time from the beginning of the
task sequence; the limit is 15 minutes. Ask the participant to:

1. Complete the initial assessment, answering or explicitly skipping questions.
2. Find the next activity or empty-state guidance and explain what evidence
   the system used.
3. Open the assigned sample activity, record completion, and submit its practice.
4. Find updated progress and explain the difference between activity completion
   and assessed skill status.

If an assessment produces no recommended activity, provide the same preannounced
sample profile to every participant for the remaining activity tasks. This
planned scenario transition is not counted as moderator help. Record the
transition; it must not conceal a failure to interpret the preceding empty state.

A successful interpretation identifies the relevant evidence and next action
without claiming that missing evidence equals failure or completion proves skill.
Use a checklist fixed before the sessions.

Record task completion, total time, help requests, actual assistance, errors,
and comments. Questions may be acknowledged neutrally; instructions that reveal
where to click or how to solve a task count as assistance. If a participant
cannot continue, help them for feedback purposes but record the unassisted
journey as unsuccessful. Participants may stop at any time.

**Proposed target:** at least 4 of 5 complete the whole sequence correctly within
15 minutes without task-solving assistance. Report individual outcomes and the
small sample limitation; do not present this as a population success rate.

After the tasks, ask what was unclear, whether the recommendation explanation
was understandable, and what should change. Prioritize observed blockers,
revise the interface, and link changes to the tested version. A later retest
must identify the new version and whether participants are returning.

Keep repository reports anonymized. Publish summaries and consented excerpts,
not identifiable recordings. These sessions do not replace the separate
relevance-evidence requirement for actual user discussions or client agreement.

## 7. Accessibility and Browser Checks

For registration, assessment, activity, and progress screens:

- Traverse and operate every interactive control with the keyboard; record
  visible focus, logical navigation, and any trap.
- Inspect programmatic input labels and text descriptions of skill states.
- Measure text contrast: at least 4.5:1 for ordinary text and 3:1 for large
  text, using the definitions and exceptions referenced in document 06.
- Run the core journey in the selected stable Chrome and Firefox versions at
  360 × 800 and 1366 × 768 CSS-pixel viewports.
- At the desktop viewport, repeat at 200% browser zoom. No required question,
  result, or action may become inaccessible.
- Record exact browser/OS versions, viewport, zoom, page, observation, and
  evidence. Fix and rerun failed checks on the changed build.

These are selected acceptance checks, not a complete WCAG conformance audit.
The earlier Chrome preview and embedded mobile viewport observations do not
replace this browser matrix or contrast/keyboard checks.

## 8. Performance Test P1

Use the conditions already proposed in document 06:

| Setting | Required test condition |
|---|---|
| Application host | FastAPI and PostgreSQL on one host: 4 vCPU, 8 GB RAM; record OS, database, runtime, dependency versions, and deployment configuration. |
| Dataset | Synthetic 1,000 learners, 40 skills, 100 activities, and 10,000 submitted attempts at the start of the measured run. |
| Load source | Separate generator, 10 virtual users, each scheduled to issue one request per second: 10 requests/second in total. |
| Duration | 60-second warm-up, followed by five minutes of measurement. |
| Request mix | 50% progress reads, 30% recommendations, 20% valid assessment submissions with unique attempt IDs. |
| Timing | End-to-end API latency from the generator over the test network; record generator/network setup. |
| Timeout | Five seconds per request. |

Warm-up must not silently change the declared starting dataset: use a separate
warm-up set or restore the measurement fixture and document the procedure.
Pre-create enough distinct valid in-progress attempts for submissions.
The initial 10,000 submitted attempts will increase during measurement; record
the final count.

Schedule starts independently of response completion. A response taking longer
than one second must not silently reduce the offered load. Record scheduled,
started, completed, failed, timed-out, and missed requests per operation.

Report each operation's request counts, median, p95, maximum completed-request
latency, and timeout count. Report timeouts alongside latency; do not drop them
and claim a passing tail-latency result. For acceptance, include timed-out
requests in the latency sample as the five-second failure boundary and clearly
label that convention.

Targets are p95 ≤ 1 second for progress and recommendations, p95 ≤ 2 seconds for
submissions, and a combined server-error/timeout proportion below 1%. Count
the union of these failures once per started request. Report unexpected client
errors separately; a run with invalid scripted submissions is not a valid P1
run. A run that misses scheduled load cannot pass.

Capture one valid run after a smoke check. If a failure leads to a change, retain
the failed run, identify the change, and rerun under the same conditions.
Do not select only the best run. P1 is synthetic performance evidence, not
evidence that 100 real lessons have been authored.

## 9. Reproducibility and Result Records

Before an application evaluation, freeze and record:

- Repository commit and relevant pull request.
- Requirement and recommendation-configuration versions.
- Catalogue, question, scoring-rule, and fixture versions.
- Runtime, dependency, database, browser, and operating-system versions.
- Exact setup/check commands, generated-data seed, and measurement conditions.
- Tester, date, and links to logs, screenshots, or anonymized observations.

The future implementation should provide a documented command for automated
checks and a separate command for the baseline comparison. This document does
not claim those commands already exist. Store synthetic fixtures and scripts
in the repository; exclude credentials and identifiable participant records.

Use one result row per acceptance criterion or concrete case:

| Test/case ID | Requirement | Expected | Observed | Status | Commit/build | Evidence | Tester/date |
|---|---|---|---|---|---|---|---|
| Example: T03 scoring | FR-04 | 2 correct + 2 incorrect = 50% | Not run | Not run | Pending | Pending | Pending |
| Example: P13 | FR-06, FR-12 | Proposed A03; baseline A02 | Not run | Not run | Pending | Pending | Pending |

Allowed statuses are **Pass**, **Fail**, **Not run**, and **Blocked**, with a
reason for blocked cases. A specification-derived expectation is not a Pass.

A Must requirement is accepted only when every criterion has passing evidence
for the tested version. Failed, blocked, or unrun mandatory checks remain open.
Deferred Should requirements need a recorded reason and supervisor discussion.

## 10. Pre-defense Readiness and Follow-up

Before 24 October 2026:

- [ ] Add this plan to the repository through the linked documentation issue.
- [ ] Have Rassul review alignment with requirements, recommendation design,
      diagrams, and prototype; record actual comments and changes.
- [ ] Ask the supervisor to review the planned baseline, metrics, scope, and
      numerical targets; record feedback when it is received.
- [ ] Prepare to explain the 20 synthetic cases, common eligibility filter,
      usability protocol, and difference between planned and completed work.
- [ ] Keep the current prototype-check record visible without presenting it
      as full application acceptance.

After the backend and frontend are implemented, execute the corresponding
checks, recruit participants/reviewers, and add dated results. Keep this plan
alongside the results so deviations are visible.

User-interview evidence, survey findings, independent ratings, usability results,
performance measurements, and supervisor feedback remain pending unless their
actual records are added. The team must report the real state at pre-defense.

**YouTrack issue:** add the actual issue URL after creation.  
**Pull request:** add the actual PR URL after creation.  
**Team review:** pending.  
**Supervisor feedback:** pending.

