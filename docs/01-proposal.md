# Oiqyn — Project Proposal

**Official diploma topic:** Development of a Literacy Platform with Personalized Learning Recommendation  
**Prepared:** 23 October 2026  
**First pre-defense:** 24 October 2026  
**Status:** Draft for team and supervisor review; user evidence and approval pending

## 1. Project Information

| Item | Details |
|---|---|
| Project name | Oiqyn |
| University | Astana IT University |
| Educational program | Software Engineering |
| Team member | Adilbekov Daniyal — SE-2414 |
| Team member | Rassul Sakenov — SE-2403 |
| Supervisor | Bakayeva Bakyt Bolatkyzy |
| Repository | [Rikatsu17/Oiqyn](https://github.com/Rikatsu17/Oiqyn) |
| Task board | [Oiqyn on YouTrack](https://oiqyn.youtrack.cloud/issues/OIQ) |

Oiqyn is a proposed web platform that helps students identify gaps in IT and
digital literacy and choose a suitable next learning activity. It connects
diagnostic assessment, short lessons, practice, progress records, and
recommendations with explanations.

This proposal defines the project purpose and boundaries. Detailed acceptance
criteria are maintained in [06-requirements.md](06-requirements.md).

## 2. Problem Statement and Evidence Status

The problem we intend to investigate is how a student can identify which digital
skills need practice and choose an appropriate learning activity.

Possible difficulties include checking an online claim, recognizing a suspicious
link, understanding a web address, or verifying a spreadsheet calculation.
A student may be comfortable with some of these tasks and unfamiliar with others.
Choosing material without knowing the student's current evidence and
prerequisite knowledge may lead to unsuitable starting points.

Oiqyn will investigate whether assessment-based recommendations provide more
appropriate next activities than a fixed order of eligible activities.

These are working assumptions about the target users, not findings from
completed interviews. The prevalence and importance of particular difficulties
must be checked through actual user discussions and the literature review.
The existing-system comparison will inform the rationale without assuming that
other platforms lack personalization or that Oiqyn is universally better.

For the first pre-defense, the team plans to collect 3–5 discussions with user
representatives, or a substantive agreement with an actual client, as required
by the supplied rubric. A supplementary survey may add context; no minimum
survey response count is specified in that rubric.

Findings will be recorded in `docs/02-user-evidence.md`, with supported needs
separated from assumptions. Changes arising from that evidence will be linked
to the affected requirements. No actual interview or survey results are claimed
in this proposal.

## 3. Target Users and Stakeholders

The primary audience is **university students aged 18 and over across different
years of study** who want to improve their IT and digital literacy skills.
The audience is not limited to first-year students.

Recommendations will use assessment evidence and learning history. Year of
study will not be used as a substitute for ability.

| Stakeholder / role | Intended interaction |
|---|---|
| Learner | Complete assessment, inspect skill evidence, study recommended activities, receive feedback, and review progress. |
| Content administrator | Maintain skills, lessons, questions, answer explanations, prerequisites, and published content versions. |
| Project team | Develop the application, prepare content, maintain documentation, and run evaluation scripts. |
| Academic supervisor | Review the project scope, engineering decisions, evaluation plan, and resulting work. |

Learner and content administrator are the two proposed application roles.
Running offline evaluation does not require an additional user role or dashboard.
A separate external client has not been confirmed in the available project
record.

## 4. Aim and Objectives

### Aim

To develop and evaluate a web platform that recommends suitable IT and digital
literacy learning activities based on a student's assessment results,
learning history, and prerequisite knowledge.

### Objectives

| Objective | Planned result |
|---|---|
| 1. Investigate potential users' needs. | An anonymized evidence summary identifying relevant difficulties, supported requirements, and remaining assumptions. |
| 2. Review research and existing solutions. | A critical literature review and a comparison of relevant platforms using consistent criteria and supporting sources. |
| 3. Specify the MVP. | Functional and non-functional requirements with priorities and verifiable acceptance criteria. |
| 4. Design the system and learning model. | Consistent architecture diagrams, user scenarios, a skill/content model, and versioned recommendation rules. |
| 5. Implement the main learning journey. | Accounts, assessment, feedback, skill profiles, learning activities, and persistent progress. |
| 6. Implement explained recommendations. | Prerequisite filtering and deterministic ranking that select an eligible activity and explain the evidence behind it. |
| 7. Evaluate the solution. | Functional verification, a reproducible comparison with a fixed-order baseline, and formative usability findings. |

These objectives describe the whole diploma project. The first pre-defense
covers the proposal, evidence, analysis, design, prototype, and plans; full
application implementation and evaluation follow in later stages.

## 5. Proposed Solution and Main Scenario

The planned learner journey is:

1. Register or sign in and read the diagnostic instructions.
2. Answer or explicitly skip questions linked to defined skills.
3. View a profile that distinguishes Target met, Needs practice, and
   Insufficient evidence.
4. Receive an eligible next activity with an explanation based on the recorded
   assessment evidence.
5. Study the lesson, record completion, and submit related practice.
6. Review feedback and updated progress, then receive the next recommendation.

**Illustrative scenario:** a fictional student meets the web-address prerequisite
but needs phishing practice. Oiqyn recommends a phishing activity and explains
which assessment result supports that choice. Completing the lesson records
completion. A later qualifying practice result may update the skill profile and
change the next recommendation.

Lesson completion and demonstrated skill are separate records. Skipped answers
supply no scored evidence; an unknown skill is not assigned a zero score.
When no eligible activity exists, the interface explains whether assessment is
needed, all represented targets are met, or available content cannot address
the current gaps.

The initial recommendation method combines prerequisite rules with a
deterministic ranking based on skill gaps, activity difficulty, and previous
completion. It is specified in
[07-recommendation-design.md](07-recommendation-design.md). Its thresholds and
weights are proposed settings requiring review, not validated measures or
learned parameters.

## 6. Project Scope

### Included in the MVP

| Area | Included behavior |
|---|---|
| Accounts and permissions | Learner registration, sign-in/out, protected personal records, and administrator authorization. |
| Diagnostic assessment | Questions across the four content areas, explicit skipping, server-side scoring, and answer explanations. |
| Skill profile | Evidence-based statuses, source dates, and preservation of earlier qualifying evidence when a later attempt is incomplete. |
| Learning activities | Short materials, objectives, separate completion records, practice assessments, and retakes. |
| Recommendations | Common eligibility rules, versioned ranking, understandable reasons, review labeling, and explicit empty states. |
| Progress | Persistent assessment history, scores, completion records, skill statuses, and the next step. |
| Content management | Drafting, publishing, archiving, prerequisite validation, and content versions that preserve historical results. |
| Interface quality | Responsive browser screens and the selected accessibility checks in the requirements. |
| Evaluation support | Reproducible fixtures and a comparison runner for the proposed method and fixed-order baseline. |

Progress filtering is a Should feature under FR-13. Other priorities and the
exact acceptance criteria remain those in document 06.

### Learning Content Boundaries

| Area | Example topic |
|---|---|
| IT and internet fundamentals | Interpreting web addresses and basic online-service concepts. |
| Information literacy | Checking online claims and verifying sources, including claims in AI-generated answers. |
| Digital safety | Recognizing phishing indicators and suspicious links. |
| Digital productivity | Using and checking basic spreadsheet formulas. |

The team will prepare a small content collection. The proposed minimum is one
defined skill and one learning activity in each area, with at least two
diagnostic and two activity-assessment questions per skill. The six activities
in the recommendation design provide a small catalogue for demonstrating
alternative choices.

This content supports an engineering demonstration. It is not comprehensive
digital-literacy coverage or an official competence assessment. Final topics,
question quality, prerequisites, and difficulty labels need review.

### Excluded from the Initial MVP

- Native mobile applications.
- Payments, subscriptions, or a public course marketplace.
- Official certification of digital competence.
- Automatic generation of all learning materials.
- Training a large language model.
- Integration with university information systems.
- Large-scale deployment across multiple universities.

## 7. Engineering Work and Provisional Architecture

The project involves coordinating assessment evidence, content versions,
recommendation decisions, and persistent user progress. The main engineering
challenges are:

- Keeping attempt submission and profile updates consistent, including failures
  and duplicate concurrent requests.
- Preserving historical scores and question versions when administrators edit
  or archive content.
- Enforcing authentication, ownership of personal records, and administrator
  permissions in the backend.
- Applying prerequisite constraints before ranking, handling missing evidence,
  and producing reproducible decisions with auditable explanations.
- Keeping the frontend, API, stored records, and evaluation fixtures consistent.

The provisional stack is:

| Component | Proposed technology |
|---|---|
| Frontend | React and TypeScript |
| Backend | Python and FastAPI |
| Database | PostgreSQL |
| Recommendation module | Python module inside the backend |
| Component interaction | HTTP API with JSON |

The alternatives and rationale are documented in
[05-technologies.md](05-technologies.md). System context, use cases, and component
relationships are described in the [diagram package](../diagrams/README.md).

The intended contribution is an implemented and evaluated system with traceable
learning evidence and explained next-activity selection. The proposal does not
claim a novel machine-learning algorithm.

## 8. Expected Outcomes and Evaluation

By the end of the diploma project, the team expects to deliver:

1. A working web application supporting the main learner and administrator
   scenarios.
2. A limited, versioned collection of skills, lessons, questions, and feedback.
3. A recommendation module with understandable explanations and reproducible
   decisions.
4. A comparison against a fixed activity order after the same eligibility filter.
5. Documented test results, usability observations, setup instructions, and
   limitations.

The [evaluation plan](08-verification-evaluation.md) specifies how these results
will be checked: acceptance tests, at least 20 synthetic recommendation cases,
independent relevance review, a formative usability test, and proposed API
performance measurements.

Synthetic profiles test specified behavior; they are not learner observations.
The baseline may perform equally well or better. A higher internal ranking score
does not prove a better educational choice.

Helping students choose relevant practice and improve their digital skills is
an intended benefit. Learning improvement will not be presented as a measured
outcome without an appropriate study.

## 9. Team Responsibilities and Feasibility

| Team member | Primary responsibility |
|---|---|
| Adilbekov Daniyal | Backend, database design, assessment logic, recommendation module, and technical evaluation. |
| Rassul Sakenov | Frontend, interface design, user scenarios, progress visualization, and usability evaluation. |

Both members contribute to research, requirements, integration, documentation,
and the defense. Each task has one primary owner and a reviewer.

A limited content catalogue, two application roles, a backend-contained
recommendation module, and a browser interface keep the proposed scope manageable.
The main dependencies are real user evidence, content and supervisor review,
team availability, and a stable integrated build for evaluation.

Responsibilities, provisional milestones, and risk responses are detailed in
[09-management.md](09-management.md). Changes to scope, priorities, or assessment
rules must be recorded with their rationale and effects on related documents.

## 10. Current Stage and Review

The project is in analysis, design, and planning, with an interactive
[browser prototype](../prototype/README.md) prepared to demonstrate the main
scenarios. The prototype uses fictional browser-side data. It does not establish
completion of production authentication, backend persistence, or full acceptance
testing.

Draft analysis, requirements, recommendation design, architecture, and evaluation
materials are available. Actual user findings, supervisor feedback, and the
full application evaluation remain pending in the available project record.

Before treating this proposal as the agreed implementation basis:

- [x] Rassul checks alignment with the README, requirements, and project scope.
- [x] The team incorporates findings from actual user discussions.
- [x] The supervisor reviews the problem, scope, engineering work, and evaluation.
- [x] Actual decisions and revisions are linked to their issue and PR.

**Proposal issue:** pending — add the actual YouTrack URL.  
**Proposal pull request:** pending — add the actual GitHub URL.  
**Team review:** pending.  
**Supervisor feedback:** pending.

