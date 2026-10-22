# Oiqyn

**A personalized path to IT and digital literacy**

Oiqyn is a diploma project for a web platform that helps students identify gaps
in their digital skills and choose what to learn next. The planned platform
will combine diagnostic tasks, short learning activities, progress tracking,
and recommendations based on assessment results and prerequisite knowledge.

**Current stage:** analysis, requirements definition, design, and planning.  
**First pre-defense:** 24 October 2026.  
**Project board:** [Oiqyn on YouTrack](https://oiqyn.youtrack.cloud/issues/OIQ).

The repository currently contains the project overview. The application,
supporting research, diagrams, and prototype are planned deliverables.
Features described below are not yet implemented.

## 1. Academic Information

| Item | Details |
|---|---|
| University | Astana IT University |
| Educational program | Software Engineering |
| Group | Adilbekov Daniyal - SE-2414, Sakenov Rassul - SE-2403|
| Project name | Oiqyn |
| Diploma topic | Development of a Literacy Platform with Personalized Learning Recommendation |
| Team members | Adilbekov Daniyal; Rassul Sakenov |
| Supervisor | Bakayeva Bakyt Bolatkyzy |

## 2. Problem and Target Users

Using a phone or social media regularly does not necessarily mean that a student
is confident with digital tasks required for university study. Possible
difficulties include checking information sources, recognizing phishing,
managing document permissions, organizing files, and using spreadsheets.

A fixed sequence of lessons may repeat familiar material while moving too
quickly through topics where a student needs more practice. Oiqyn will explore
whether assessment-based recommendations can help students find relevant
learning activities.

The initial target audience is **first-year university students aged 18 and
over**. Their needs, preferred topics, and learning difficulties are working
assumptions to be checked through user discussions and relevant research.

User interviews and the survey have not yet been conducted. Findings will be
recorded separately from assumptions and used to refine the requirements.

## 3. Aim, Objectives, and Expected Outcomes

### Aim

To develop and evaluate a web platform that recommends suitable IT and digital
literacy learning activities based on a student's assessment results,
learning history, and prerequisite knowledge.

### Objectives

1. Investigate the needs of potential users and define the problem.
2. Review relevant research and compare existing learning platforms.
3. Specify functional and non-functional requirements with acceptance criteria.
4. Design the system architecture, skill model, and learning content structure.
5. Implement diagnostic assessment, learning activities, and progress tracking.
6. Develop a recommendation method with understandable explanations.
7. Evaluate functionality, recommendation quality, and usability.

### Expected Outcomes

By the end of the diploma project, we plan to deliver:

- A working web platform covering the main student learning journey.
- A limited, structured collection of learning materials and assessment tasks.
- A recommendation module that selects suitable next activities and explains why.
- An evaluation comparing recommendations with a fixed learning sequence.
- Technical documentation covering requirements, architecture, setup, and testing.

Improved learning outcomes are an intended benefit. They will not be presented
as an established result without an appropriate evaluation.

## 4. Learning Content

The proposed content scope covers four areas:

| Area | Example learning tasks |
|---|---|
| IT and internet fundamentals | Understand basic computer concepts, browsers, and online services |
| Information literacy | Compare sources and check the reliability of online information, including AI-generated answers |
| Digital safety | Recognize phishing, protect accounts, and manage access permissions |
| Digital productivity | Organize files, use basic spreadsheet functions, and collaborate on documents |

Each area will be divided into specific skills. Learning activities will have
skill tags, difficulty levels, and prerequisites where needed.

The MVP will use a small collection of materials prepared by the team.
The final topics, content volume, and assessment rules will be agreed during
requirements analysis and supervisor review.

## 5. MVP Scope

### Included

| Feature | Planned behavior |
|---|---|
| Student accounts | Register, sign in, and access personal learning records |
| Initial assessment | Complete tasks linked to defined digital skills |
| Skill profile | View an initial estimate based on available assessment evidence |
| Learning activities | Read short lessons and complete related practice |
| Assessment feedback | See results and explanations for assessed tasks |
| Recommendations | Receive a suitable next activity based on skill gaps and prerequisites |
| Recommendation explanations | Understand the reason for the suggested activity |
| Progress dashboard | View completed activities and assessment results |
| Content management | Allow an administrator to manage materials, questions, and skill links |
| Responsive interface | Use the platform through desktop and mobile browsers |

Completing a lesson and demonstrating a skill will be recorded separately.
Opening a page will not be treated as proof of mastery.

### Outside the Initial MVP

- Native mobile applications.
- Payments, subscriptions, and a public course marketplace.
- Official certification of digital competence.
- Automatic generation of all learning content.
- Training a large language model.
- Integration with university information systems.
- Large-scale deployment across multiple universities.

The first pre-defense focuses on research, requirements, design, mockups,
and planning. Implementation is a later project stage.

## 6. Main Student Journey

1. Create an account and complete the initial assessment.
2. View the initial skill profile and areas needing further practice.
3. Receive a recommended activity with a short explanation.
4. Study the material and complete the related assessment.
5. Review feedback and updated progress.
6. Receive the next recommendation based on the new results.

A short assessment provides limited evidence. Skills with insufficient
assessment data should remain distinguishable from skills with demonstrated
difficulties.

## 7. Recommendation Design

The proposed approach combines **knowledge-based rules** with
**content-based ranking**. It is intended to work before a large history of
student interactions is available.

| Input | Examples |
|---|---|
| Assessment results | Correct and incorrect answers linked to specific skills |
| Learning history | Completed activities and previous attempts |
| Content metadata | Skill tags, difficulty, prerequisites, and learning objectives |

The planned process is to:

1. Identify skills needing practice or further assessment.
2. Find relevant activities in the content collection.
3. Filter activities against prerequisite requirements.
4. Rank eligible activities according to the student's needs.
5. Return the next activity and an explanation.
6. Update future recommendations after new assessment results.

Example explanation:

> This activity is recommended because your recent answers show difficulty
> identifying phishing messages.

Scoring rules, prerequisite thresholds, and handling of missing assessment
data will be specified and tested during development. The system will also
need a defined response when no suitable activity is available.

The recommendation method will be compared with a fixed learning sequence.
We do not assume that personalization will outperform this baseline before
evaluation.

## 8. Proposed Architecture and Technologies

The initial design separates the student interface, backend application,
recommendation logic, and data storage. The recommendation module is planned
as part of the backend; a separate microservice is not required for the MVP.

| Component | Proposed technology | Responsibility |
|---|---|---|
| Web interface | React and TypeScript | Assessment screens, lessons, recommendations, and progress |
| Backend application | Python and FastAPI | Authentication, content access, assessment processing, and API |
| Recommendation module | Python within the backend | Prerequisite filtering, ranking, and explanations |
| Database | PostgreSQL | Accounts, skills, content, assessment attempts, and progress |
| Component interaction | HTTP API with JSON | Communication between the frontend and backend |
| Version control | Git and GitHub | Change history and pull request review |
| Task tracking | YouTrack | Ownership, priorities, deadlines, and deliverable links |

These choices are provisional. The technology comparison will evaluate
2–3 alternatives for at least three key decisions, such as the backend
framework, data storage, and recommendation method. Decisions will be
justified against project requirements and team constraints.

## 9. Verification and Evaluation Plan

| Area | Planned method | Measures to define and report |
|---|---|---|
| Functional correctness | Test authentication, assessment submission, result storage, and progress updates | Passed and failed acceptance criteria |
| Recommendation constraints | Check prepared profiles with different skill gaps and prerequisites | Prerequisite violations and handling of unavailable activities |
| Recommendation relevance | Compare the proposed method and a fixed sequence using the same profiles and content | Relevance ratings under a documented review rubric |
| Usability | Ask target users to complete the main scenarios | Task completion, difficulties, and user feedback |
| Performance | Measure API behavior under documented conditions | Response times and error rates at a specified workload |

The detailed evaluation plan will define test cases, sample sizes, measurement
conditions, acceptance thresholds, and baseline behavior before testing.
Prepared profiles will support technical checks; they will not be presented
as evidence of real students' learning improvement.

If learning gains are evaluated, that study will use a separate design with
appropriate assessments and stated limitations.

## 10. Team Responsibilities

| Team member | Primary responsibilities |
|---|---|
| Adilbekov Daniyal | Backend, database design, assessment logic, recommendation module, and technical evaluation |
| Rassul Sakenov | Frontend, interface design, user scenarios, progress visualization, and usability evaluation |

Both members will contribute to user research, literature analysis,
requirements, integration, documentation, and the defense. Each task will
have one primary owner, with supporting contributions recorded separately.

Individual contributions will be traceable through personal accounts,
commits, pull requests, reviews, and linked YouTrack tasks.

## 11. Documentation Plan

The README is the project overview. Detailed evidence and decisions will be
maintained in the following locations as they are prepared.

| Deliverable | Planned location |
|---|---|
| Proposal, target users, objectives, and scope | `docs/01-proposal.md` |
| Anonymized user research findings and limitations | `docs/02-user-evidence.md` |
| Literature analysis and references | `docs/03-literature-review.md` |
| Existing system comparison and supporting sources | `docs/04-existing-systems.md` |
| Technology alternatives and decision rationale | `docs/05-technologies.md` |
| Prioritized requirements and acceptance criteria | `docs/06-requirements.md` |
| Skill model and recommendation rules | `docs/07-recommendation-design.md` |
| Tests, metrics, conditions, and baseline | `docs/08-verification-evaluation.md` |
| Responsibilities, milestones, risks, and dependencies | `docs/09-management.md` |
| Supervisor comments and resulting revisions | `docs/10-supervisor-feedback.md` |
| Submission status and known limitations | `docs/11-submission.md` |
| Context, use case, and component diagrams | `diagrams/` |
| Key screen mockups and prototype scenarios | `prototype/` |

These paths are a plan, not links to completed documents. Actual links will
be added when the files exist and have been checked.

Implementation folders will be added when needed: `frontend/`,
`backend/`, `tests/`, and `config/`.

## 12. First Pre-defense Checklist

**Deadline: 24 October 2026.** Items will be marked complete only after the
corresponding evidence has been prepared and checked.

- [ ] **Project proposal:** title, team, supervisor, problem, users, aim,
      objectives, expected outcomes, and realistic scope.
- [ ] **Relevance evidence:** 3–5 discussions with user representatives,
      or a substantive agreement with an actual client; distinguish verified
      findings from assumptions.
- [ ] **Literature review:** at least 12 meaningfully used sources,
      including at least 8 scientific publications, with a structured analysis
      table and critical synthesis. For rapidly evolving topics, prioritize
      the last five years while retaining essential foundational works.
- [ ] **Existing systems:** compare 3–5 relevant systems against 6–10
      consistent criteria and support capability claims with evidence.
      Justify a smaller set if fewer comparable systems exist.
- [ ] **Technology comparison:** at least three key decisions, with
      2–3 reasonable alternatives for each.
- [ ] **Requirements:** functional and non-functional requirements,
      priorities, and verifiable acceptance criteria.
- [ ] **Architecture:** consistent system context, use case, and draft
      component diagrams aligned with requirements and scenarios.
- [ ] **UX/prototype:** mockups showing the main user scenarios.
- [ ] **Evaluation plan:** testing approach, outcome metrics, measurement
      conditions, and a baseline for comparison.
- [ ] **Project management:** Git repository, YouTrack project,
      responsibilities, milestones, risks, and dependencies.
- [ ] **Supervisor feedback:** substantive comments on key deliverables,
      decisions on how to address them, and resulting changes.

A survey may provide additional evidence. It will supplement user discussions;
no minimum survey response count is specified in the supplied pre-defense
criteria.

## 13. Project Workflow

Tasks are managed in the
[Oiqyn YouTrack project](https://oiqyn.youtrack.cloud/issues/OIQ).
Each task should state its owner, expected result, acceptance criteria,
priority, deadline, and links to the work.

For each meaningful change:

1. Select the relevant YouTrack task and update its status.
2. Create a branch and include the actual task ID in its name.
3. Commit the work with a descriptive message referencing the task.
4. Open a pull request explaining the change and how it was checked.
5. Have the other team member review it and address any comments.
6. Merge the reviewed work and link the pull request in YouTrack.
7. Close the task when all its acceptance criteria are met.

Research and documentation changes follow the same review process.
Reviews and task completion must reflect work that actually took place.

Submission snapshots are planned as Git tags:
`pre-defense-1`, `pre-defense-2`, and `final-pre-defense`.
Each snapshot will identify completed work and outstanding limitations.
Further development will continue in new commits without moving submitted tags.

Passwords, API keys, participant contact details, and identifiable raw research
responses must not be committed. Public research summaries will use participant
codes and anonymized findings.

## 14. Setup and Execution

A runnable application is not yet available.

Installation instructions, environment variables, database migrations,
run commands, and test commands will be added with the first working
implementation.
