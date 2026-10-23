# Oiqyn — Project Management Plan

**Project:** Development of a Literacy Platform with Personalized Learning Recommendation  
**Team:** Adilbekov Daniyal (SE-2414); Rassul Sakenov (SE-2403)  
**Supervisor:** Bakayeva Bakyt Bolatkyzy  
**First pre-defense:** 24 October 2026  
**Status:** Proposed working plan; team review and supervisor feedback pending

## 1. Purpose and Project Boundaries

This document defines responsibilities, milestones, dependencies, risks, and the
workflow for tracking Oiqyn. It supports the project-management component of
the first pre-defense.

The proposed product is a web platform for university students aged 18 and over
across different years of study. It connects diagnostic assessment, a skill
profile, short learning activities, explained recommendations, and progress.

The first pre-defense focuses on the proposal, evidence, analysis, requirements,
architecture, prototype, evaluation plan, and management records. A complete
production application is a later diploma-project deliverable.

The initial scope remains the one defined in the [README](../README.md) and
[requirements](06-requirements.md). Native mobile applications, payments,
official certification, university-system integration, training a large language
model, and large-scale deployment are outside the MVP.

The provisional implementation is React/TypeScript, FastAPI, PostgreSQL, and a
Python recommendation module inside the backend. The current browser prototype
demonstrates interactions; it is not the production application.

## 2. Project Records and Current Status

| Record | Location | Purpose |
|---|---|---|
| Git repository | [Rikatsu17/Oiqyn](https://github.com/Rikatsu17/Oiqyn) | Source files, documents, change history, pull requests, and reviews. |
| Task board | [Oiqyn on YouTrack](https://oiqyn.youtrack.cloud/issues/OIQ) | Task owner, priority, acceptance criteria, due date, status, and links. |
| Project overview | [README](../README.md) | Scope, team, current stage, and links to available deliverables. |
| Analysis and design | [Literature](03-literature-review.md), [systems](04-existing-systems.md), [technologies](05-technologies.md), [requirements](06-requirements.md), [recommendations](07-recommendation-design.md) | Research, requirements, and design decisions. |
| Architecture and UX | [Diagrams](../diagrams/README.md), [prototype](../prototype/README.md) | System structure and demonstrable user scenarios. |
| Verification | [Evaluation plan](08-verification-evaluation.md) | Planned checks, baseline, metrics, and measurement conditions. |
| Supervisor feedback | Planned: `docs/10-supervisor-feedback.md` | Actual comments, decisions, and resulting changes. |
| Submission record | Planned: `docs/11-submission.md` | Submitted version, readiness evidence, and unresolved limitations. |

Draft analysis/design documents, diagrams, an interactive prototype, and the
evaluation plan have been prepared during project preparation. Their existence
does not establish that every file is merged into GitHub, reviewed by Rassul,
or approved by the supervisor. Verify those states using actual links.

No interview findings, survey dataset, participant usability results, complete
application test results, or supervisor feedback are recorded in this plan.
Do not mark those activities complete without their evidence. Update the README
when deliverables become available so it does not continue describing existing
work as merely planned.

## 3. Responsibilities

The following allocation describes primary ownership, not a claim that the work
has already been performed. Supporting contributions should be recorded in the
corresponding issue and pull request.

| Work area | Primary owner | Support / review | Expected contribution |
|---|---|---|---|
| Backend and database | Adilbekov Daniyal | Rassul Sakenov | API, data model, migrations, access control, and persistent records. |
| Assessment and recommendations | Adilbekov Daniyal | Rassul Sakenov; supervisor feedback on design | Scoring, evidence updates, prerequisite filtering, ranking, explanations, and baseline comparison. |
| Frontend and UX | Rassul Sakenov | Adilbekov Daniyal | Learner/admin screens, responsive behavior, progress visualization, and API integration. |
| User research | Rassul Sakenov | Adilbekov Daniyal | Coordinate discussions, collect consented notes, and summarize findings; both conduct discussions. |
| Literature and technology analysis | Adilbekov Daniyal | Rassul Sakenov | Verify sources, compare alternatives, and connect findings to decisions. |
| Requirements and architecture | Adilbekov Daniyal | Rassul Sakenov | Align requirement IDs, components, data, and scenarios. |
| Interface and usability checks | Rassul Sakenov | Adilbekov Daniyal | Keyboard/layout checks, usability sessions, observations, and fixes. |
| Technical verification | Adilbekov Daniyal | Rassul Sakenov | Backend checks, data consistency, recommendation fixtures, and performance evaluation. |
| Board, documentation, and integration | Adilbekov Daniyal | Rassul Sakenov | Maintain links, coordinate milestones, and reconcile changes; each member updates their own tasks. |
| Presentation and defense | Rassul Sakenov | Adilbekov Daniyal | Assemble the presentation; both prepare explanations and rehearse their own contributions. |

Bakayeva Bakyt Bolatkyzy is the academic supervisor, not an implementation task
owner. The team will request substantive feedback on scope, requirements,
design, and evaluation. Actual feedback and decisions belong in document 10.

Every issue has one primary assignee. Reviewing a teammate's work is a real
contribution, but it must not be presented as authorship of that work. Do not
create artificial commits, tasks, or approvals to make contributions look equal.

## 4. Milestones Before the First Pre-defense

Dates below are planning targets. The confirmed pre-defense date is 24 October
2026; the institutional submission time and channel must be checked separately.

| Milestone | Target | Lead | Completion evidence and dependencies |
|---|---|---|---|
| M1 — Relevance evidence and scope review | By 23 October | Rassul | Anonymized findings from 3–5 user-representative discussions, or a substantive agreement with an actual client; distinguish assumptions and update affected requirements. Depends on participant/client availability. |
| M2 — Consistent analysis and design package | By 23 October | Daniyal | Reviewed proposal, literature/system/technology comparisons, requirements, recommendation design, diagrams, and evaluation plan. Drafts can be prepared in parallel; final review must account for M1 findings. |
| M3 — Demonstrable UX | By 23 October | Rassul | Prototype opens from the repository package, shows the main journey and missing-evidence states, and has a review record. Depends on consistent scenarios and requirements. |
| M4 — Management and supervisor feedback records | By 23 October | Daniyal | Responsibilities, milestones, risks, issue/PR links, and actual supervisor comments with decisions. Documents may be prepared earlier; substantive review needs the deliverables being reviewed. |
| M5 — Reviewed submission snapshot and rehearsal | 24 October, before the required submission/defense time | Daniyal coordinates; both present | Inspect merged files, fix links, update the README and submission checklist, record unresolved items, freeze the submitted commit, and rehearse the presentation. Depends on M1–M4 or an explicit record of remaining gaps. |

The 23 October targets are intended to leave time for final checks. A missed
target remains an open item with an owner and next action. It must not be
converted into a completed item to make the checklist appear ready.

A Google Forms survey is optional supporting evidence. The supplied rubric does
not require 30 responses. A survey does not automatically replace the required
user discussions or substantive client agreement.

M5 can identify a submission snapshot even when gaps remain. Such a snapshot
records what is being submitted; it does not certify that every rubric component
has been satisfied.

## 5. Provisional Implementation Sequence After Pre-defense

These are planning estimates, not university-approved deadlines. After
pre-defense feedback, both members will confirm available time and assign
calendar dates in YouTrack.

| Milestone | Indicative duration | Lead | Dependency and exit condition |
|---|---|---|---|
| M6 — Resolve feedback and agree the implementation baseline | First working week after pre-defense | Daniyal | Record feedback; revise scope, requirements, content assumptions, and evaluation settings. Unresolved decisions have owners. |
| M7 — Implement one complete learner journey | Approximately 2 weeks after M6 | Daniyal, with Rassul on frontend tasks | One learner can sign in, submit a diagnostic, receive a persisted skill profile and explained activity, complete practice, and see updated progress. Core API contract and seed content are agreed first. |
| M8 — Complete mandatory scenarios and integration | Approximately 2–3 weeks after M7 | Rassul coordinates integration; Daniyal owns backend tasks | Add remaining mandatory administration, versioning, empty states, and interface behavior; execute the associated acceptance checks. |
| M9 — Evaluate, fix, and prepare the next defense package | Approximately 1–2 weeks after M8 | Daniyal; Rassul leads usability | Run document 08 procedures on the tested build, retain results and failures, address issues, and update the report/presentation. Depends on a stable build and reviewer/participant availability. |

Frontend screens and backend work may proceed in parallel after their data
contract is agreed. The final evaluation must use the integrated application.
Participant recruitment can begin earlier, once the protocol is ready.

Do not silently reduce Must requirements to fit an estimate. Record any proposed
scope or priority change, its effect on the project aim, and the relevant team
and supervisor discussion. Should features may be deferred with a stated reason.

## 6. Dependencies and Coordination

| Dependency | Why it matters | Action and owner |
|---|---|---|
| User evidence → final requirements | Assumed needs may not match actual student difficulties. | Rassul records findings; Daniyal updates affected requirement IDs. |
| Skill/content definitions → assessment and recommendations | Inconsistent tags, answer keys, or prerequisites make results unreliable. | Daniyal versions the catalogue and requests content review before evaluation. |
| Requirements/API contract → frontend/backend integration | Different meanings for unknown scores, completion, or versions create inconsistent screens. | Both agree example requests/responses and state meanings before connecting components. |
| Stable build + test data → evaluation | Results are not reproducible without identified inputs and versions. | Daniyal records commit, configuration, fixtures, environment, and commands. |
| Participant/reviewer availability → user-facing evaluation | Recruitment delays can block planned sessions. | Rassul schedules sessions and records any protocol deviation. |
| Substantive deliverables → supervisor review | A file list alone cannot produce useful feedback on the design. | Daniyal supplies specific documents and questions; both address actual comments. |

Use the existing communication channel for a short daily check-in until
pre-defense and at least one weekly planning check afterward. Each member
states what changed, what is next, and what is blocked. Record decisions that
affect scope, requirements, dates, or acceptance in YouTrack or the repository.

As a proposed work limit, each member focuses on one main implementation task
at a time. Review work can proceed alongside it. If a dependency blocks a task,
record the blocker and move to useful independent work.

## 7. YouTrack and GitHub Workflow

Use the existing issues where they already describe the work. The tables in
this document are a plan, not instructions to create a new issue for every row.

Each active task should contain:

- A clear title and expected deliverable.
- One assignee, priority, due date, and acceptance criteria.
- Links to affected requirements/documents and any blocking task.
- The branch/PR link, review outcome, and completion evidence.

Use the project's existing state names. Conceptually, work moves through
**To do → In progress → In review → Done**. This document does not claim those
exact state names have already been configured. A blocked task needs a reason
and next action, whether represented by a status, tag, or comment.

For a meaningful change:

1. Select the existing issue or create a focused one if it is missing.
2. Create a branch from the latest `main`, using the actual issue ID:
   `OIQ-N/short-description`.
3. Commit the work with the issue ID and a meaningful message.
4. Open a pull request stating the change, reason, and checks performed.
5. Ask the other team member to review; address comments in the same branch.
6. Merge after the required review and checks.
7. Link the PR in YouTrack and mark Done only when all acceptance criteria
   are met.

Here, `N` is the number assigned by YouTrack, not a document or milestone number.
Keep `main`; branches are temporary work areas. Documentation may be added out
of numerical order if its dependencies and references remain clear.

For this document, use `OIQ-N/project-management` with the actual issue ID.
A possible PR title is **Add project management plan**. The issue and PR links
below remain pending until created; no new issue number is assumed.

## 8. Definition of Done and Change Control

For a documentation task, Done means the expected file exists at the agreed
path, its claims and sources have been checked, related documents are consistent,
the required teammate review occurred, changes are merged, and the issue links
to the evidence. Supervisor review is additionally required where specified by
the task or deliverable.

For an implementation task, also require passing evidence for its acceptance
criteria, review of applicable negative/error cases, and updated setup or test
instructions where behavior changed. A running demo does not prove all criteria.

When changing scope, a requirement, recommendation rule, or API contract:

1. Record the proposed change and its reason.
2. Identify affected requirements, components, tests, documents, and milestones.
3. Record the decision and relevant review.
4. Update the linked artifacts and version any changed rules or content.
5. Recheck affected behavior.

Do not move historical submission tags or rewrite old results to match new
rules. The planned `pre-defense-1` tag will identify the actual submitted commit
after final checks. Record that commit in the submission document; tag creation
is not claimed here.

## 9. Risk Register

Likelihood and impact are initial qualitative estimates for planning. They are
not measured probabilities. Owners review risks at check-ins and when a trigger
occurs.

| Risk | Likelihood / impact | Trigger | Prevention and response | Owner |
|---|---|---|---|---|
| Insufficient relevance evidence by the deadline | High / High | Required discussions or client agreement are still unavailable on 23 October. | Prioritize real discussions and record findings promptly. If incomplete, report the gap and a dated next action; do not invent evidence or treat a survey target as a replacement. | Rassul |
| Supervisor feedback arrives late | Medium / High | No substantive comments before final package review. | Request review of specific key deliverables early. Record actual contact and response when they occur. If unavailable, report pending feedback and continue teammate consistency checks. | Daniyal |
| Scope exceeds a two-person team's capacity | Medium / High | Added features delay the main journey or mandatory checks. | Keep the agreed exclusions, deliver the core journey first, and discuss deferring Should features. Changes to Must commitments require a documented decision. | Daniyal |
| Assessment or content rules are weak | Medium / High | Review finds ambiguous questions, incorrect keys, or unsupported difficulty/prerequisite labels. | Use versioned content, known-answer cases, and reviewer feedback. Revise before evaluation; report the limited evidence behind the two-answer minimum and thresholds. | Daniyal |
| Ranking offers no advantage over baseline | Medium / Medium | Blinded relevance ratings show ties or worse choices. | Use identical eligibility and fixed evaluation conditions. Report the outcome honestly; examine causes and consider a simpler method through documented design review. | Daniyal |
| Frontend/backend interpretations diverge | Medium / High | UI treats unknown as zero, completion as skill mastery, or stale content as current. | Agree response examples and integrate a small journey early. Add checks for these specific state transitions. | Rassul |
| Data or access-control defects | Medium / High | Duplicate attempts, partial writes, cross-user access, or exposed credentials appear in testing. | Run the authorization, transaction, retry, and credential checks in document 08. Block acceptance of affected Must requirements until corrected. | Daniyal |
| Review, merge, or contribution records are incomplete | Medium / Medium | Files exist but PR reviews, issue links, or ownership are unclear. | Update each task as work happens. Resolve conflicts in the task branch, use personal accounts for real contributions, and verify the submission commit. | Daniyal |
| Prototype cannot be opened during presentation | Low / High | Hosted access or network failure on the presentation device. | Keep the existing local prototype package and exported diagrams available, test opening them beforehand, and rehearse the local demonstration. | Rassul |
| Participants or relevance reviewers are unavailable later | Medium / Medium | Planned sessions cannot be booked for evaluation. | Recruit ahead of the stable build, prepare backup dates, and disclose any reduced sample or protocol change rather than claiming the original study occurred. | Rassul |

## 10. Immediate Actions and Review Record

The next actions are to review this management plan, verify current issue/PR
links, complete outstanding relevance evidence, obtain supervisor feedback,
and prepare an accurate submission record. Existing tasks should be reused.

- [ ] Rassul reviews the responsibility allocation and milestones.
- [ ] Both members confirm their active tasks and realistic dates.
- [ ] Actual issue and PR links are added.
- [ ] Pending research and supervisor feedback have owners and next actions.
- [ ] README status and documentation links are reconciled before submission.
- [ ] The submission record identifies the actual commit and remaining gaps.

**Management issue:** pending — add the actual YouTrack URL.  
**Management pull request:** pending — add the actual GitHub URL.  
**Team review:** pending.  
**Supervisor feedback:** record actual comments in document 10 when received.

