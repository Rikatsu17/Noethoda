# Oiqyn

### A personalized path to IT and digital literacy

Oiqyn is a diploma project focused on developing a web platform
that helps students improve their IT and digital literacy through
personalized learning recommendations.

The platform will assess a student's initial knowledge, track learning
progress, and recommend suitable learning activities based on identified
skill gaps and prerequisite knowledge.

**Current stage:** analysis, requirements definition, design, and planning.

**First pre-defense deadline:** 24 October 2026.

---

## 1. Academic Information

| Item | Details |
|---|---|
| University | Astana IT University |
| Educational program | Software Engineering |
| Group | SE-2414 |
| Project name | Oiqyn |
| Diploma topic | Development of a Literacy Platform with Personalized Learning Recommendation |
| Team members | Adilbekov Daniyal; Rasul Sakenov |
| Supervisor | Bakayeva Bakyt Bolatkyzy |

---

## 2. Problem Statement

Students enter university with different levels of digital knowledge.
A learner may be confident with everyday applications but struggle
with evaluating online information, protecting accounts, organizing
files, or using digital tools for academic work.

A fixed learning sequence may include material a student already
understands while providing insufficient support for weaker areas.

Our project investigates whether diagnostic assessment and
skill-based recommendations can help students identify relevant
learning activities and follow a clearer learning path.

These needs are currently working assumptions. User interviews,
survey responses, and the literature review will be used to refine
the problem and project requirements.

## 3. Target Users

The initial target audience is first-year university students
aged 18 and over who want to strengthen their practical digital skills.

The initial research and prototype will focus on this audience.
The scope may be refined after discussions with potential users
and the supervisor.

## 4. Project Aim

To develop and evaluate a web platform that recommends suitable
IT and digital literacy learning activities based on a student's
assessment results, learning progress, and prerequisite knowledge.

### Objectives

- Investigate the needs and difficulties of potential users.
- Review relevant research and compare existing learning platforms.
- Define functional and non-functional requirements.
- Design a skill model and a structured collection of learning materials.
- Implement diagnostic assessment and progress tracking.
- Develop a recommendation method for selecting the next learning activity.
- Explain recommendations in language that students can understand.
- Evaluate the system against a fixed learning sequence and defined criteria.

## 5. Planned Learning Areas

The initial content scope includes:

| Area | Example topics |
|---|---|
| IT and internet fundamentals | Basic computer concepts, browsers, online services |
| Information literacy | Search strategies, source evaluation, verification of AI-generated information |
| Digital safety | Account protection, phishing awareness, privacy |
| Digital productivity | File organization, spreadsheets, online collaboration |

The final topics, learning outcomes, and content volume will be
confirmed during requirements analysis.

## 6. Main User Journey

1. The student creates an account and completes an initial assessment.
2. The platform creates an initial skill profile from the assessment results.
3. The student receives a recommended learning activity and an explanation.
4. The student studies the material and completes a short assessment.
5. The platform updates the student's progress and skill profile.
6. The recommendation module selects the next suitable activity.

Students will be able to view completed activities, assessment results,
and areas that require further practice.

## 7. Project Scope

### Included in the planned MVP

- Student registration and authentication.
- Initial diagnostic assessment.
- Learning materials organized by topic and skill.
- Short assessments linked to learning activities.
- A skill profile for each student.
- Recommendations based on skill gaps and prerequisites.
- Explanations for recommended activities.
- A dashboard showing learning progress.
- Basic management of learning materials and assessment questions.
- A responsive web interface.

### Outside the initial MVP

- Native mobile applications.
- Paid subscriptions and payment processing.
- A public marketplace for third-party courses.
- Official certification of digital competence.
- Automated generation of all educational content.
- Training a large language model.
- Large-scale deployment across multiple universities.

A complete application is not required for the first pre-defense.
The October submission focuses on research, design, planning,
and evidence of individual contributions.

## 8. Recommendation Approach

The initial design combines knowledge-based rules with
content-based ranking.

Learning materials will be associated with skills, difficulty levels,
and prerequisites. The recommendation module will use assessment
results and learning history to identify relevant activities.

The proposed process is:

1. Identify skills that need further assessment or practice.
2. Filter activities according to prerequisite requirements.
3. Rank suitable activities by their relevance to the student's needs.
4. Present a recommendation with a short explanation.
5. Update future recommendations after new assessment results.

Example explanation:

> This activity is recommended because your recent answers show
> difficulty identifying phishing messages.

This approach is intended to work without a large historical dataset
of student interactions. The final rules and ranking method will be
documented and evaluated during development.

## 9. Proposed Technology Stack

These choices are provisional and will be justified through
a comparison of alternatives.

| Component | Proposed technology | Purpose |
|---|---|---|
| Frontend | React and TypeScript | Student interface and progress dashboard |
| Backend | Python and FastAPI | Application logic and API |
| Database | PostgreSQL | Users, learning content, assessments, and progress |
| Recommendation module | Python | Skill-based filtering and activity ranking |
| Version control | Git and GitHub | Development history and peer review |
| Project management | YouTrack | Tasks, responsibilities, priorities, and deadlines |
| User research | Google Forms and interviews | Collecting feedback from potential users |

## 10. Team Responsibilities

| Team member | Primary responsibilities |
|---|---|
| Adilbekov Daniyal Adilbekuly | Backend, database design, assessment logic, recommendation module, and technical evaluation |
| Rasul Sakenov | Frontend, interface design, user scenarios, progress visualization, and usability evaluation |

Both team members contribute to user research, literature analysis,
requirements, documentation, integration, and peer review.

Each meaningful task will have one primary owner in YouTrack.
Individual contributions will be recorded through separate accounts,
commits, and pull requests.

## 11. Project Documentation

Documentation will be maintained in the repository as it is prepared
and reviewed.

| Deliverable | Planned location |
|---|---|
| Project proposal and scope | `docs/01-proposal.md` |
| User research findings | `docs/02-user-evidence.md` |
| Literature review | `docs/03-literature-review.md` |
| Existing system comparison | `docs/04-existing-systems.md` |
| Technology comparison | `docs/05-technologies.md` |
| Requirements and acceptance criteria | `docs/06-requirements.md` |
| Recommendation design | `docs/07-recommendation-design.md` |
| Verification and evaluation plan | `docs/08-verification-evaluation.md` |
| Responsibilities, milestones, and risks | `docs/09-management.md` |
| Supervisor feedback and resulting changes | `docs/10-supervisor-feedback.md` |
| Submission checklist and limitations | `docs/11-submission.md` |
| Editable diagrams and readable exports | `diagrams/` |
| Interface mockups and prototype materials | `prototype/` |

These are planned locations. This table does not indicate that
every deliverable has been completed.

## 12. Repository Organization

| Directory | Purpose |
|---|---|
| `frontend/` | Web interface source code |
| `backend/` | API, application logic, and recommendation module |
| `docs/` | Research, requirements, design decisions, and project documentation |
| `diagrams/` | Editable diagram sources and exported images |
| `prototype/` | Interface mockups and interaction scenarios |
| `tests/` | Automated tests and supporting test materials |
| `config/` | Configuration examples and supporting settings |

Directories will be added as the corresponding work begins.

Passwords, API keys, participant contact details, and identifiable
raw research responses must not be committed to the repository.
Configuration examples will use placeholder values.

## 13. Project Management

Tasks are tracked in
[the Oiqyn YouTrack project](https://oiqyn.youtrack.cloud/issues/OIQ).

Each task should include:

- A clear description.
- One responsible team member.
- An expected result.
- Acceptance criteria.
- A priority and deadline.
- Links to the relevant deliverables or pull requests.

### Development workflow

1. Create or select a task in YouTrack.
2. Move the task to the appropriate active stage when work begins.
3. Create a separate Git branch for the task.
4. Record meaningful changes with descriptive commit messages.
5. Include the actual YouTrack task ID in the branch name
   and commit or pull request description.
6. Open a pull request and describe how the work was checked.
7. Have the other team member review the changes.
8. Address review comments before merging into `main`.
9. Link the pull request in YouTrack and close the task
   only when its acceptance criteria are met.

The `main` branch will contain reviewed work.
Documentation and design changes follow the same review process.

## 14. First Pre-defense: 24 October 2026

The planned submission includes:

- [ ] Completed project README.
- [ ] Project proposal, target users, objectives, and scope.
- [ ] Evidence from 3–5 discussions with potential users.
- [ ] Survey findings, if responses are available, with limitations stated.
- [ ] Literature review using at least 12 sources,
      including at least 8 scientific publications.
- [ ] Comparison of 3–5 existing systems using 6–10 consistent criteria.
- [ ] Comparison of at least 3 key technical decisions,
      with 2–3 alternatives for each.
- [ ] Functional and non-functional requirements with acceptance criteria.
- [ ] System context diagram.
- [ ] Use case diagram.
- [ ] Draft component diagram.
- [ ] Editable diagram sources and readable exports.
- [ ] Mockups of the main user scenarios.
- [ ] Verification and evaluation plan.
- [ ] Assigned and prioritized YouTrack tasks.
- [ ] Project milestones, risks, and dependencies.
- [ ] Recorded supervisor feedback and resulting revisions.
- [ ] Evidence of progressive contributions from both team members.
- [ ] Repository access for the supervisor and committee.
- [ ] Submission tag: `pre-defense-1`.

Checklist items will be marked complete only after the corresponding
work has been completed and checked.

## 15. Verification and Evaluation

The evaluation plan will cover:

- Functional correctness of authentication, assessments,
  recommendations, and progress tracking.
- Compliance of recommendations with prerequisite rules.
- Recommendation relevance compared with a fixed learning sequence.
- Usability of the main student scenarios.
- API performance under documented test conditions.

Metrics, test conditions, and acceptance thresholds will be specified
in the verification and evaluation plan.

Improved learning outcomes are an intended benefit, not an established
result. Any claims about effectiveness will depend on the evidence
collected during evaluation.

## 16. Setup and Execution

The project is currently in the analysis and design stage.
A runnable application is not yet available.

Installation, environment configuration, database setup, execution,
and testing instructions will be added when the first runnable
implementation is committed.

## 17. Submission Versions

The same repository will be maintained throughout the diploma project.

Submission versions will be identified using these Git tags:

- `pre-defense-1`
- `pre-defense-2`
- `final-pre-defense`

Each submission will include a summary of completed work,
known limitations, and outstanding tasks. Submitted tags will remain
unchanged while further development continues in new commits.
