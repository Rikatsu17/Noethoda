# Oiqyn — Supervisor Feedback

**Project:** Development of a Literacy Platform with Personalized Learning Recommendation  
**University:** Astana IT University  
**Team:** Adilbekov Daniyal (SE-2414); Rassul Sakenov (SE-2403)  
**Academic supervisor:** Bakayeva Bakyt Bolatkyzy  
**Feedback confirmation recorded:** 23 October 2026  
**Document updated:** 24 October 2026  
**Stage:** First pre-defense — proposal, research, and design

## 1. Review Focus

The supervisor confirmed the comments summarized below. The review focused on
the connection between student needs and project requirements, the interpretation
of assessment results, the rationale for recommendations, and the evaluation
approach. This document records the team's responses and incorporates the
student-research findings available on 24 October 2026.

Oiqyn is designed for university students aged 18 and above across different
years of study. Its core journey combines an initial assessment, a skill
profile, explained learning recommendations, practical activities, and
progress tracking.

## 2. Supervisor Feedback and Team Responses

### SF-01 — Connect project requirements to student experiences

**Supervisor feedback:** Support the proposed requirements with student
discussions. Identify recurring difficulties and explain how the findings
inform the platform's features.

**Team response:** We conducted three semi-structured interviews and analyzed
a Google Forms survey. The survey received 34 submissions; 33 eligible,
consenting responses were included in the analysis. Interview participants
are identified anonymously as P1, P2, and P3.

The findings support a focus on practical exercises, feedback, assessment,
and understandable recommendations. Section 5 of the research document links
the findings to the existing functional and non-functional requirements.
The team retains the current requirement priorities for the proposal stage.

**Recorded outcome:** Interviews, survey findings, shared themes, and the
requirement mapping are documented in
[02-user-evidence.md](02-user-evidence.md).

**Responsibility:** Rassul Sakenov coordinates user research; Adilbekov Daniyal
handles its connection to technical requirements.

### SF-02 — Define how assessment results should be interpreted

**Supervisor feedback:** Explain the purpose of the initial assessment
thresholds and the level of confidence supported by a short test. Review
question quality and use practical questions relevant to each skill.

**Team response:** The initial assessment provides a starting indication of
the learner's skills. The prototype uses a minimum of two scored answers
per skill and a 70% target. With exactly two scored answers, the possible
results are 0%, 50%, and 100%; reaching the target requires both answers
to be correct.

These settings are provisional design choices. Skill status is based on
assessment evidence, while lesson completion is tracked separately. P3's
comments about short-test reliability reinforce the decision to explain the
meaning of results and include practical assessment tasks.

**Recorded outcome:** The assessment interpretation is clarified in this
record and connected to the research findings. Question wording, skill
alignment, and answer keys will be reviewed during content development.

**Related documents:** [06-requirements.md](06-requirements.md) and
[07-recommendation-design.md](07-recommendation-design.md).

**Responsibility:** Adilbekov Daniyal handles scoring and question review;
Rassul Sakenov handles learner-facing explanations.

### SF-03 — Explain and evaluate the recommendation settings

**Supervisor feedback:** Explain the purpose of the ranking weights and
difficulty boundary, and evaluate recommendations against a suitable baseline.

**Team response:** The initial configuration gives 70% weight to the observed
skill gap, 20% to difficulty match, and 10% to an activity not yet completed.
This prioritizes identified learning needs while accounting for activity
difficulty and repetition. The difficulty boundary of 0.35 and the ranking
weights are provisional settings.

P2 and P3 emphasized recommendations based on actual knowledge and clear
reasons. The design therefore ties recommendation explanations to assessment
evidence. During evaluation, the personalized ranking will be compared with a
fixed-order baseline using the same eligibility rules. Independent relevance
ratings will assess recommendation usefulness.

**Recorded outcome:** The design rationale, user-evidence connection, and
comparison approach are documented. The configuration will be versioned for
the implementation-stage comparison.

**Related documents:** [07-recommendation-design.md](07-recommendation-design.md)
and [08-verification-evaluation.md](08-verification-evaluation.md).

**Responsibility:** Adilbekov Daniyal handles ranking and comparison;
Rassul Sakenov checks the clarity of recommendation explanations.

### SF-04 — Distinguish the purposes of different evaluations

**Supervisor feedback:** Separate technical correctness, recommendation
relevance, and usability. Interpret each result according to what the
evaluation actually measures.

**Team response:** The completed interviews and survey describe student needs
and preferences. The implementation-stage evaluation is organized into three
activities: technical checks using 20 prepared cases and application tests,
independent recommendation-relevance review, and usability sessions with five
adult students across at least two years of study.

Research findings, prototype demonstrations, and evaluation results will be
reported separately. Interest in trying the platform describes stated
intention; learning improvement would require a study designed to measure it.

**Recorded outcome:** The evaluation plan distinguishes each activity's purpose,
conditions, and measures.

**Related documents:** [08-verification-evaluation.md](08-verification-evaluation.md)
and [prototype/README.md](../prototype/README.md).

**Responsibility:** Adilbekov Daniyal handles technical evaluation;
Rassul Sakenov handles usability sessions.

## 3. Research Findings Incorporated into the Response

Survey results below use the 33 eligible responses.

| Finding | Implication for Oiqyn |
|---|---|
| 33/33 selected practical exercises with feedback. | Keep practice and feedback central to the learning journey. |
| 21/33 selected an initial assessment. | Retain assessment as the starting point for identifying learning needs. |
| 16/33 identified making time as their main online-learning difficulty; 10/33 selected finding practical exercises. | Favor focused activities with practical tasks. |
| 29/33 considered their last lesson's difficulty appropriate. | Describe difficulty mismatch as an individual experience rather than a problem shared by most respondents. |
| P2 and P3 questioned recommendation accuracy or requested understandable reasons. | Explain suggestions using the learner's assessment evidence. |
| P3 raised assessment reliability and privacy. | Explain score interpretation and protect personal learning records. |

These are exploratory findings from a small, non-random sample. Sampling,
self-report, and collection considerations are documented in Sections 2.4
and 7 of [02-user-evidence.md](02-user-evidence.md).

## 4. Decisions and Development Stages

| Feedback | Proposal-stage result | Next development activity |
|---|---|---|
| SF-01 | Student research and links to requirements documented. | Use the findings when reviewing content and feature priorities. |
| SF-02 | Assessment interpretation and provisional settings explained. | Review questions, answer keys, and scoring settings during content development. |
| SF-03 | Ranking rationale and baseline comparison defined. | Implement the versioned configuration and run the comparison. |
| SF-04 | Needs research and product evaluation distinguished. | Conduct technical, relevance, and usability evaluations on the implementation. |

## 5. Feedback Record Checklist

This checklist covers the preparation of this feedback record for the first
pre-defense.

- [x] Identify the project, team, and academic supervisor.
- [x] Record the supervisor-confirmed comments.
- [x] Provide a team response for each comment.
- [x] Incorporate the three interviews and analyzed survey.
- [x] Link research findings to the relevant requirements.
- [x] Explain the assessment and recommendation design decisions.
- [x] Identify responsibilities and subsequent development activities.
- [x] Link the supporting project documents.
- [x] Update the feedback record for 24 October 2026.

