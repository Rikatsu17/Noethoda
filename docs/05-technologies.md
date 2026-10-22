# Oiqyn — Technology Comparison and Provisional Decisions

**Project:** Development of a Literacy Platform with Personalized Learning Recommendation  
**Team:** Adilbekov Daniyal (SE-2414); Rassul Sakenov (SE-2403)  
**Prepared:** 23 October 2026  
**Status:** Draft for team and supervisor review; implementation validation pending  
**Related deliverable:** First pre-defense, 24 October 2026

## 1. Purpose and Scope

This document compares alternatives for three key technical decisions:

1. Backend framework: two alternatives.
2. Primary database: three alternatives.
3. Recommendation method: three alternatives.

Oiqyn targets university students aged 18 and over across different years of
study. Recommendations should use assessment evidence and learning needs.
Year of study is not a substitute for skill assessment.

The comparison uses official technical documentation and the current project
proposal. Product capabilities are cited; judgments about suitability and
development effort are our design assessments. No comparative benchmarks,
implementation trials, user-study results, or supervisor approval are claimed.

All choices remain provisional. The initial requirements below are derived
from the README and must be refined using actual user evidence. Technical
documentation can establish that a capability exists; it cannot establish that
the complete Oiqyn implementation will satisfy its requirements.

## 2. Decision Drivers

These identifiers support traceability within this document. They are not
final functional-requirement identifiers.

| ID | Proposed requirement or constraint | Effect on technology selection |
|---|---|---|
| D1 | A browser interface exchanges accounts, assessments, activities, and progress with the backend. | Require validated API inputs and a clear frontend/backend contract. |
| D2 | Learners access their own records; authorized administrators manage content and questions. | Require authentication, authorization, and an administration workflow. |
| D3 | Store users, skills, activities, prerequisites, attempts, and results with explicit relationships. | Prefer a data model that makes relationships and integrity rules easy to inspect. |
| D4 | Related assessment writes must remain consistent when a request fails or is repeated. | Require transaction boundaries and an explicit duplicate-submission policy. |
| D5 | No substantial learner–activity interaction dataset is currently available. | The initial recommender must operate without collaborative training data. |
| D6 | Recommendations must respect prerequisites and provide an evidence-based explanation. | Require eligibility rules and a traceable selection process. |
| D7 | A two-person team must implement and evaluate a limited MVP. | Keep deployment and maintenance manageable; avoid unnecessary services. |
| D8 | Recommendations must be compared with a reproducible baseline. | Keep inputs, content versions, and evaluation conditions controlled. |

## 3. Decision T1 — Backend Framework

### Alternatives

- **FastAPI:** Python framework for an API-oriented backend.
- **Django with Django REST Framework (DRF):** Python application framework
  combined with an API toolkit.

Both alternatives can host the proposed Python recommendation module.
The choice does not depend on an assumption that only FastAPI supports Python
recommendation logic.

### Comparison

| Criterion | FastAPI | Django + DRF |
|---|---|---|
| API inputs and documentation — D1 | Type-based request validation and generated OpenAPI documentation support an explicit API contract. [1] | Serializers, API views, authentication policies, and a browsable API support structured API development. [3] |
| Persistence — D3–D4 | Database-library choice is separate; the official tutorial demonstrates SQLModel and allows other SQL or NoSQL libraries. [2] | DRF can serialize ORM and non-ORM data. Django's model-oriented ecosystem supports an integrated application structure. [3], [4] |
| Content administration — D2 | An administration interface or suitable integration must be selected and implemented in our proposed design. | Django supplies a model-driven administration interface for trusted internal users; tailored workflows may still need custom views. [4] |
| Recommendation integration — D5–D6 | Our proposed module can run inside the Python backend. | The same module can run inside the Python backend. |
| Work for this project — D7 | Design assessment: direct fit for the proposed API boundary, but authentication, permissions, persistence, and content management still require integration. | Design assessment: an attractive option if internal content administration becomes a major part of the workload. |
| Main uncertainty | Whether the team can deliver the required administration and authorization workflows within the implementation plan. | Whether the additional framework conventions benefit the small MVP enough to justify changing the current proposal. |

### Provisional decision: FastAPI

FastAPI matches the proposed separation between the React interface and a
Python API. Its documented validation and API-schema facilities support D1.
This is a fit-based decision, not a claim of measured performance superiority.

The main cost is assembling the rest of the backend application. FastAPI's
security tools do not automatically create a complete, correctly authorized
user-management system. [1] The implementation must explicitly address D2
and D4.

**Reconsider in favor of Django + DRF** if a custom administration workflow
becomes disproportionately expensive or the team demonstrates that Django's
internal admin covers the required content-management scenarios more directly.

**Validation during implementation:** complete one vertical slice containing
an assessment endpoint, rejected invalid input, authorized content editing,
and an attempt to access another learner's results. Record the observed
behavior and remaining work. No such slice has been implemented yet.

## 4. Decision T2 — Primary Database

### Alternatives

- **PostgreSQL**
- **MySQL with InnoDB**
- **MongoDB**

The core data includes many relationships: activities cover skills, questions
assess skills, attempts belong to learners, and activities may require several
prerequisite skills. The primary comparison therefore concerns integrity,
queries, and maintainability rather than an assumed need for web-scale storage.

### Comparison

| Criterion | PostgreSQL | MySQL / InnoDB | MongoDB |
|---|---|---|---|
| Data organization — D3 | Relational tables with primary and foreign keys suit the proposed linked entities. [5] | Relational tables with InnoDB foreign keys also suit these entities. [7] | Documents can embed or reference related data; design follows access patterns. [8] |
| Consistency of related writes — D4 | Transactions can commit or roll back a group of changes. [6] | InnoDB provides ACID transactions, commit, and rollback. [7] | Multi-document ACID transactions are supported; deployment and transaction configuration require attention. [9] |
| Enforcing relationships — D3 | Database constraints can reject invalid references and duplicate keys. Application rules are still needed for domain-specific conditions. [5] | InnoDB foreign keys enforce referential integrity. Domain rules still require application logic. [7] | Embedding can keep related data together; cross-document references and consistency must be deliberately designed. [8] |
| Fit for Oiqyn's queries | Design assessment: a direct fit for joining learners, attempts, skill evidence, and activity metadata. | Design assessment: also a direct fit; no measured shortfall is established. | Design assessment: feasible, but shared skill and prerequisite records make embedding/reference decisions more involved for this model. |
| Delivery implications — D7 | Requires schema migrations, indexes, connection management, backups, and deployment configuration. | Requires the same categories of relational database work. | Requires document-schema decisions and validation as well as an appropriate deployment for transaction use. [8], [9] |

### Provisional decision: PostgreSQL

PostgreSQL supports the relational integrity and transaction requirements
identified in D3–D4 and matches the database already proposed in the README.
Continuing with that design avoids an otherwise unmotivated change in the
current plan.

MySQL is a credible alternative and can meet the stated core requirements.
No benchmark or requirement currently demonstrates that PostgreSQL is uniquely
necessary. MongoDB is also technically feasible; its document model offers no
clear project-specific advantage for the current, strongly related data.

**Design consequences:**

- Keep assessment attempts and their results explicitly linked.
- Define when an attempt and any derived skill evidence are committed.
- Define how repeated submissions are detected or handled.
- Keep activity completion separate from assessed performance.
- Check prerequisite cycles in application/domain logic; ordinary foreign keys
  alone do not establish that a prerequisite graph is acyclic.
- Select migrations, backup, and restoration procedures before deployment.

**Validation during implementation:** create a representative schema, reject
an invalid skill reference, roll back a deliberately failed related write,
check repeated-submission behavior, and verify a backup restoration.

**Reconsider** if the chosen hosting environment imposes a different supported
database or new requirements materially change the data-access model.

## 5. Decision T3 — Recommendation Method

### Alternatives

**A. Knowledge-based rules only.** Identify a skill needing practice, apply
prerequisite rules, and choose an activity using an explicit priority order.

**B. Knowledge-based eligibility rules plus content-based ranking.** Filter
activities by prerequisites, then score eligible activities using the
learner's skill needs and activity metadata.

**C. Collaborative filtering with the same eligibility safeguards.** Use
patterns in learner–activity feedback to rank candidates, while retaining
explicit prerequisite checks.

Content-based methods use item features and a user representation; they need
not rely on other users' data. [10] Our proposed adaptation represents
*learning needs* rather than simply repeating a learner's preferences.
Whether this adaptation produces useful educational recommendations remains
to be evaluated.

Collaborative methods use information across users and items. A basic
matrix-factorization approach learns from a feedback matrix, and unseen users
or activities require a strategy for missing interaction evidence. [11], [12]

### Comparison

| Criterion | A. Rules only | B. Rules + content-based ranking | C. Collaborative filtering |
|---|---|---|---|
| Inputs — D5 | Assessment evidence, authored skill links, prerequisites, and activity priorities. | The same evidence plus consistent features such as skill coverage and difficulty. | Meaningful learner–activity feedback, plus the metadata required for shared eligibility checks. |
| Launch without interaction history — D5 | Feasible under the proposed rules once the diagnostic and content mappings exist. | Feasible using the diagnostic profile and authored activity metadata. | A pure collaborative ranker cannot be trained from an empty feedback dataset; a fallback or additional model is needed. [11], [12] |
| Prerequisites — D6 | Directly implemented as rules. | Rules remove ineligible activities before ranking. | Must remain a separate constraint layer; predicted preference does not establish readiness. |
| Explanation — D6 | Report the matching rule and evidence. | Report the relevant skill need and factors used to select the activity. | A model score alone is not the proposed educational explanation; additional explanation design is needed. |
| Adaptation after assessment | Change the applicable rules and selected priority. | Update skill needs and recompute candidate scores. | Requires a defined connection between new evidence, model inputs, and updates. |
| Main project trade-off — D7 | A useful simpler alternative, but growing exceptions may make priorities difficult to maintain. | More ranking parameters and metadata to validate, while remaining inspectable. | Adds data collection, feedback interpretation, model evaluation, and update procedures. |

Except where cited, these entries describe the proposed implementations and
our assessment of their consequences, not measured comparisons.

### Provisional decision: B — Rules plus content-based ranking

This option addresses the absence of interaction history while allowing the
team to study whether ranking multiple eligible activities adds value.

The first version is planned as a deterministic, feature-based scorer with
explicit rules. It is not a trained neural model. Rule-based behavior and
content-based scoring must be explained accurately in the defense.

**Proposed workflow:**

1. Read assessment evidence and distinguish missing evidence from difficulty.
2. Retrieve activities relevant to the skill needs.
3. Apply prerequisite and activity-availability checks.
4. Score eligible activities using documented features.
5. Resolve ties deterministically and return an activity with a reason.
6. Recompute after new assessment evidence.

Weights, thresholds, assessment rules, and tie handling are still to be
specified in `docs/07-recommendation-design.md`. If evidence is insufficient
or no eligible activity exists, the system must return an explicit state
rather than an unsupported recommendation.

Survey answers about general preferences are **not** a learner–activity
interaction dataset for collaborative filtering. Collecting 30 survey
responses would inform requirements, but would not by itself justify training
option C.

**Evaluation baseline:** use a fixed activity order with the same common
eligibility checks and the same content collection. Its order does not change
with skill-gap scores. This isolates the additional effect of adaptive ranking
more clearly than comparing unrelated platforms.

**Validation during implementation:** use prepared profiles to check
prerequisite violations, missing evidence, ties, empty candidate sets, and
whether the explanation matches the actual selection inputs. Evaluate
relevance separately using a documented review rubric. Prepared profiles do
not demonstrate learning gains.

**Reconsider:** simplify to option A if ranking adds no useful distinction
or cannot be justified; revisit option C only after suitable interaction
data and an evaluation protocol exist.

## 6. Decision Summary and Review Conditions

| Decision | Provisional choice | Main reason | Condition for reconsideration |
|---|---|---|---|
| T1: Backend | FastAPI | Fit with the proposed Python API and explicit request contracts. | Content administration or authorization work makes Django + DRF more practical. |
| T2: Database | PostgreSQL | Fit with linked educational records and consistency requirements. | Deployment constraints or a materially different data model favor an alternative. |
| T3: Recommendations | Rules + content-based ranking | Can use assessment evidence and authored metadata without collaborative training data. | Ranking does not add value, metadata is inadequate, or sufficient interaction data supports another approach. |

The other proposed architecture choices remain unchanged: a React/TypeScript
interface, HTTP/JSON communication, and the recommendation module inside the
backend. These are provisional supporting choices, not additional decisions
claimed to have been fully compared here.

Concrete supported software versions, package compatibility, ORM and migration
tools, deployment configuration, and numerical performance targets must be
selected before implementation or measurement. Versioned documentation below
identifies the capability reference used; it does not pin a project dependency.

## 7. Status and Next Actions

- [x] Compare three key technical decisions.
- [x] Include two or three reasonable alternatives for each.
- [x] Connect choices to explicit project requirements and constraints.
- [x] Cite official sources for technical capability claims.
- [x] Record trade-offs, uncertainty, and conditions for revisiting choices.
- [ ] Team reviews the rationale and resolves comments.
- [ ] Supervisor reviews the key decisions.
- [ ] Record the actual YouTrack issue and Pull Request links.
- [ ] During implementation, run the validation checks described above.

For the first pre-defense, this is a decision rationale and validation plan.
The unchecked implementation checks are future work, not completed test results.

## 8. References

Official sources consulted on 23 October 2026.

| Ref. | Source | Use |
|---|---|---|
| [1] | FastAPI — Features | Request validation, API schemas, and authentication tools. |
| [2] | FastAPI — SQL databases | Separation of framework and database-library choices. |
| [3] | Django REST Framework — Overview | API toolkit, serializers, authentication policies, and supported data sources. |
| [4] | Django documentation 5.2 — Admin site | Internal model-driven administration and customization limits. |
| [5] | PostgreSQL documentation — Constraints | Primary keys, foreign keys, and integrity rules. |
| [6] | PostgreSQL documentation — Transactions | Grouping related writes and rollback. |
| [7] | MySQL 8.4 manual — Introduction to InnoDB | Transactions and foreign-key support. |
| [8] | MongoDB manual — Data modeling | Documents, embedding/references, access patterns, and schema validation. |
| [9] | MongoDB manual — Transactions | Single-document atomicity and multi-document transactions. |
| [10] | Google Developers — Content-based filtering | Feature-based user/item representations and scoring. |
| [11] | Google Developers — Collaborative filtering | Feedback-based user–item modeling. |
| [12] | Google Developers — Collaborative filtering advantages and disadvantages | Feedback requirements and cold-start limitations. |

[1]: https://fastapi.tiangolo.com/features/
[2]: https://fastapi.tiangolo.com/tutorial/sql-databases/
[3]: https://www.django-rest-framework.org/
[4]: https://docs.djangoproject.com/en/5.2/ref/contrib/admin/
[5]: https://www.postgresql.org/docs/current/ddl-constraints.html
[6]: https://www.postgresql.org/docs/current/tutorial-transactions.html
[7]: https://dev.mysql.com/doc/refman/8.4/en/innodb-introduction.html
[8]: https://www.mongodb.com/docs/manual/data-modeling/
[9]: https://www.mongodb.com/docs/manual/core/transactions/
[10]: https://developers.google.com/machine-learning/recommendation/content-based/basics
[11]: https://developers.google.com/machine-learning/recommendation/collaborative/basics
[12]: https://developers.google.com/machine-learning/recommendation/collaborative/summary
