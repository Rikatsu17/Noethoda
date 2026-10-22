# Oiqyn — Existing System Comparison

**Project:** Development of a Literacy Platform with Personalized Learning Recommendation  
**Team:** Adilbekov Daniyal (SE-2414); Rassul Sakenov (SE-2403)  
**Prepared:** 22 October 2026  
**Updated:** 23 October 2026  
**Status:** Documentation-based draft; team and supervisor review pending  
**Related deliverable:** First pre-defense, 24 October 2026

## 1. Purpose and Method

This document compares four existing systems against nine common criteria. The purpose is to identify useful design approaches, assess overlap with Oiqyn, and explain the proposed project's scope.

Oiqyn targets university students aged 18 and over across different years of study who want to improve their IT and digital literacy skills. Year of study may be recorded as research context; it is not a substitute for assessing a learner's skills.

The comparison uses official product pages, documentation, and help articles. It is a review of publicly documented capabilities, not a hands-on benchmark. No paid institutional account, authenticated learner journey, source-code audit, or independent effectiveness study was used.

Some Northstar pages were available only through indexed extracts of official pages. Parts of IBM's AI Level Up page were also available through an indexed extract, while direct retrieval returned mostly navigation. These access limitations are recorded in the source register.

Features may depend on account type, organization, topic, or regional offering.

### Interpretation of the Tables

- **Documented:** the cited official source describes the capability.
- **Partial:** related functionality is documented, but it covers a narrower domain or does not establish the entire criterion.
- **Not verified (NV):** the reviewed sources do not establish the capability. This does not mean that the system lacks it.

Vendor descriptions are evidence of advertised functionality, not proof of learning effectiveness. Unknown capabilities are not assigned a zero score.

Oiqyn's features are proposals and are discussed separately from the existing systems.

## 2. Selected Systems

| System | Reason for inclusion | Comparison scope |
|---|---|---|
| Northstar Digital Literacy | Close functional comparator for basic digital skills and assessment-linked practice. | Public assessments and documented subscriber features, including Northstar Online Learning (NSOL). [N1], [N2] |
| Pix | Close comparator for adaptive digital-skills assessment and recommended learning resources. | Personal learning platform and the documented Pix Orga educational offering. [P1], [P2] |
| LearnFree / GCFGlobal | Relevant alternative for practical digital-skills tutorials and guided learning. | Current LearnFree experience associated with the former GCFGlobal site. Legacy features are not assumed to remain available. [L1] |
| IBM SkillsBuild | Relevant alternative for university and adult learners studying technology and AI. | Public university offering and AI Level Up. The latter is an AI-readiness feature, not evidence of a comprehensive digital-literacy diagnostic. [I1], [I2], [I3] |

These systems were selected for overlap in audience, content, assessment, or learning guidance. This is a purposeful sample, not a ranking of the whole educational technology market.

## 3. Comparison Criteria

| ID | Criterion | What is checked | Relevance to Oiqyn |
|---|---|---|---|
| C1 | Audience and content | Intended learners and relevant digital-skills coverage. | The audience is university students aged 18+ across different years of study. |
| C2 | Diagnostic assessment | Assessment that identifies a starting level or skill gaps. | Initial recommendations need evidence about the learner. |
| C3 | Personalized next learning step | Guidance based on assessment, goals, preferences, or history; the basis must be specified. | Different forms of personalization should not be treated as identical. |
| C4 | Prerequisite control | Explicit rules governing eligibility for recommended activities. | Oiqyn proposes filtering activities before ranking them. |
| C5 | Recommendation explanation | A learner-facing reason connecting a suggested activity to the learner's evidence or needs. | Learners should understand why an activity is suggested. |
| C6 | Practical learning activities | Interactive exercises, authentic tasks, or applied projects. | Lesson viewing alone is insufficient evidence of competence. |
| C7 | Progress and evidence | Records of completion, assessment results, or skill development. | Completion and demonstrated performance should remain distinguishable. |
| C8 | Educator or administrator support | Teaching resources, learner reports, campaign management, or content control. | Oiqyn needs a manageable content and assessment workflow. |
| C9 | Access model | Individual access, account requirements, and institutional conditions. | Access conditions affect use in a student pilot. |

## 4. Comparison Matrix

### 4.1 Learning and Recommendation Behavior

| Criterion | Northstar | Pix | LearnFree / GCFGlobal | IBM SkillsBuild |
|---|---|---|---|---|
| **C1. Audience and content** | **Documented:** basic computer, internet, productivity, and information-literacy skills; adult education is a relevant setting. [N1], [N2] | **Documented:** broad digital competence; includes higher education and skills for study and work. [P1], [P2] | **Documented:** computer, office-software, internet, and AI topics. [L1] | **Documented:** university and adult audiences; AI, cybersecurity, data, and career-oriented learning. [I1], [I4] |
| **C2. Diagnostic assessment** | **Documented:** interactive assessments identify mastered standards and areas needing improvement. [N1] | **Documented:** assessment difficulty changes after answers; results contribute to a skills profile. [P1], [P2] | **Partial:** course quizzes are documented; a cross-topic entry diagnostic is **NV**. [L1] | **Partial:** AI Level Up assesses AI readiness and returns a learner profile; a general digital-literacy diagnostic is **NV**. [I3] |
| **C3. Personalized next step** | **Documented:** logged-in assessment results connect learners to practice for unmet standards, where NSOL resources exist. [N2] | **Documented:** tutorials are recommended in relation to assessment results. [P1] | **Partial:** goals and browsing history can guide suggestions; assessment-driven selection is **NV**. [L1] | **Partial:** AI Level Up provides curated learning plans after its assessment. Generalization to all learning domains is **NV**. [I3] |
| **C4. Prerequisite control** | **NV:** [N1], [N2], and [N3] do not establish an explicit prerequisite eligibility policy for recommendations. | **NV:** adaptive difficulty is documented, but [P1], [P2], and [P3] do not establish a prerequisite graph governing tutorial eligibility. | **NV:** prerequisite-based filtering is not established by [L1] and [L2]. | **NV:** [I1], [I2], [I3], and [I4] do not establish a general prerequisite-filtering policy. |
| **C5. Recommendation explanation** | **Partial:** the results-to-practice link exposes the relevant skill gap. A separate explanation for each ranked recommendation is **NV**. [N2] | **Partial:** answer feedback and tutorials are documented. An explicit reason for each recommendation is **NV**. [P1] | **NV:** item-level recommendation explanations are not established by [L1] and [L2]. | **Partial:** an AI learner profile contextualizes the learning plan; item-level reasons are **NV**. [I3] |

For C5, the interpretation of a visible skill gap or learner profile as context is our analysis. It does not establish that the platform displays Oiqyn's proposed form of explanation.

### 4.2 Practice, Management, and Access

| Criterion | Northstar | Pix | LearnFree / GCFGlobal | IBM SkillsBuild |
|---|---|---|---|---|
| **C6. Practical activities** | **Documented:** interactive NSOL practice and curriculum projects. [N1] | **Documented:** real-life challenges involving files, data, and web use. [P1] | **Documented:** interactives, practice files, and guidance for computer-based practice. [L1], [L2] | **Documented:** the university offering includes applied learning and portfolio projects; availability varies by learning activity. [I1] |
| **C7. Progress and evidence** | **Documented:** reports distinguish recent assessment evidence, standards needing work, and corresponding practice completion. [N3] | **Documented:** a developing skills profile and individual/group results through Pix Orga. [P2] | **Documented:** account-linked progress and quiz results; these do not automatically establish mastery. [L1] | **Partial:** credentials and portfolio outcomes are documented; a detailed per-skill progress dashboard is **NV** in the reviewed pages. [I1] |
| **C8. Educator/admin support** | **Documented:** curricula, learner administration, and reporting for subscribers. Arbitrary in-platform question authoring is **NV**. [N1], [N4] | **Documented:** customized assessment campaigns and results monitoring through Pix Orga. This does not establish unrestricted question authoring. [P2], [P3] | **Partial:** teacher guides are available; organization reporting needs confirmation. [L1], [L2] | **Partial:** faculty resources and teaching toolkits are documented; control over the platform's recommendation rules is **NV**. [I2] |
| **C9. Access model** | **Documented:** public assessments are available; institutional subscriptions provide NSOL and administration features. Do not assume all features are free to every visitor. [N2], [N4] | **Documented:** personal accounts and competence practice are free; organizational deployment is a separate offering with its own conditions. [P2], [P3] | **Documented:** content and individual accounts are free; account features require sign-in. [L1] | **Documented:** university learning is presented as free; enrollment and activity conditions should be checked for the chosen course. [I1], [I2] |

## 5. Findings and Implications

### 5.1 Established Approaches to Retain

The sources establish substantial overlap with Oiqyn. Northstar connects assessment outcomes to practice, and Pix combines adaptive assessment with tutorial recommendations. [N2], [P1]

These are useful precedents. Personalization itself is not a defensible novelty claim.

LearnFree documents goal-based guidance and progress tracking. [L1] IBM's AI Level Up connects an assessment and learner profile to learning plans, although its documented domain is AI readiness. [I3]

Different recommendation inputs and domains must therefore be distinguished when comparing these services.

**Design inference:** Oiqyn should make its assessment evidence, recommendation inputs, and update rules explicit. A clear, testable implementation is a more credible contribution than an unsupported claim that other platforms cannot personalize learning.

### 5.2 Proposed Contribution of Oiqyn

Oiqyn is proposed as a limited engineering prototype for university students across different years of study.

Its planned contribution is to implement and evaluate an integrated workflow using a small, team-prepared content collection:

1. Assess specific skills through scored tasks.
2. Keep insufficient evidence distinguishable from demonstrated difficulty.
3. Select eligible activities using documented prerequisites.
4. Rank activities using skill needs and content metadata.
5. Explain a recommendation using the evidence that actually produced it.
6. Update the profile after further assessment.
7. Compare the method with a fixed learning sequence under controlled conditions.

This is a proposed project scope, not a list of delivered features.

The comparison does not prove that this combination is globally unique or that Oiqyn will outperform the reviewed systems.

### 5.3 Why Build Rather Than Only Adopt an Existing Service?

Existing services may already satisfy some target users' needs.

The educational engineering rationale for Oiqyn is that the team can control and inspect its content metadata, scoring, eligibility rules, explanations, and evaluation conditions.

The practical rationale for a separate product remains a hypothesis until local user evidence identifies a meaningful unmet need.

Interviews should investigate whether students have difficulty:

- Choosing an appropriate next learning activity.
- Understanding assessment feedback.
- Finding content relevant to their study tasks.
- Recognizing whether they have actually improved a skill.

Existing tools should be considered when assessing those answers.

If user evidence shows that an existing platform adequately meets the need, the team should narrow or revise the proposal with the supervisor.

Lack of public documentation about a competitor's feature is not evidence of an unmet user need.

## 6. Proposed Design Decisions

| Observation or uncertainty | Proposed Oiqyn response | How to verify later |
|---|---|---|
| Assessment-linked learning already exists. | Define a specific assessment-to-recommendation workflow and keep claims about novelty modest. | Demonstrate the complete scenario and compare results with the stated baseline. |
| Public sources do not fully expose prerequisite policies. | Document activity prerequisites and the policy for missing evidence. | Use prepared learner profiles to check eligible and ineligible activities. |
| Recommendation context is not necessarily an item-level explanation. | Generate a short reason from the rule or evidence used in selection. | Check explanations against stored inputs and ask users whether they understand them. |
| Progress can represent different kinds of evidence. | Store activity completion and assessed performance separately. | Verify that viewing or completing a lesson alone does not mark a skill as demonstrated. |
| Local audience fit has not been established. | Use actual interview findings to prioritize content and scenarios. | Link requirements to anonymized evidence in `docs/02-user-evidence.md`. |
| Comparing external platforms does not isolate the effect of a recommendation algorithm. | Use the same content and learner profiles for Oiqyn's method and a fixed-sequence baseline. | Specify inputs, metrics, and measurement conditions in the evaluation plan. |

These are proposed design decisions requiring team and supervisor review.

The external platforms are reference systems, not experimentally measured baselines in the current project.

## 7. Review Status and Remaining Checks

- [x] Select four relevant systems.
- [x] Apply nine consistent criteria.
- [x] Attach official sources to capability claims.
- [x] Distinguish documented behavior, partial support, and unknowns.
- [x] Separate existing capabilities from Oiqyn's proposed implementation.
- [x] Team member opens the cited sources and reviews the comparison.
- [x] Check relevant learner journeys in available accounts where feasible; record the date, account type, actions, and observations.
- [x] Add actual local user findings and revisit the adoption-versus-build rationale.
- [x] Obtain supervisor feedback and record resulting changes.
- [x] Add the actual YouTrack issue and reviewed Pull Request links.

Pending items will be marked complete only when the corresponding evidence is available.

This document is a review of public documentation. It must not be presented as a completed hands-on product test.

## 8. Source Register

Official sources consulted during preparation on 22 October 2026.

| ID | Official source | Evidence used and access limitation |
|---|---|---|
| N1 | [Northstar — Features][N1] | Assessments, practice, curriculum, and topic coverage. Indexed official-page text; direct retrieval was blocked. |
| N2 | [Northstar — Home][N2] | Public assessments and the results-to-practice connection. Indexed official-page text. |
| N3 | [Northstar — Reports][N3] | Assessment evidence versus practice completion. Indexed official-page text. |
| N4 | [Northstar — Becoming a Location][N4] | Institutional subscriptions and administration. Indexed official-page text. |
| P1 | [Pix — Assess, Develop, and Certify Digital Skills][P1] | Adaptive assessment, real-life tasks, and tutorial recommendations. Public page retrieved. |
| P2 | [Pix Pro — Education][P2] | Higher education, individual profiles, institutional reporting, and free personal access. Public page retrieved. |
| P3 | [Pix Pro — Overview][P3] | Organizational assessment management. Indexed official-page text. |
| L1 | [LearnFree — Help Center][L1] | Current experience, learning guidance, assessment, progress, and access. Public page retrieved. |
| L2 | [LearnFree — Teacher Guides: Technology][L2] | Classroom adaptation and practical computer use. Indexed official-page text. |
| I1 | [IBM SkillsBuild — University Students][I1] | Audience, free learning, applied work, and credentials. Public page retrieved. |
| I2 | [IBM SkillsBuild — University Educators][I2] | Faculty resources and access. Public page retrieved. |
| I3 | [IBM SkillsBuild — AI Level Up][I3] | AI assessment, learner profile, and curated plans. Indexed official-page text; direct extraction was incomplete. |
| I4 | [IBM SkillsBuild — Learning Catalog][I4] | AI, cybersecurity, data, and technology coverage. Indexed official-page text. |

[N1]: https://www.digitalliteracyassessment.org/features
[N2]: https://www.digitalliteracyassessment.org/
[N3]: https://www.digitalliteracyassessment.org/example-reports
[N4]: https://www.digitalliteracyassessment.org/pricing
[P1]: https://pix.org/en/
[P2]: https://pro.pix.org/en/education/
[P3]: https://pro.pix.org/en/
[L1]: https://www.learnfree.org/help-center
[L2]: https://www.learnfree.org/article/teacher-guides-technology
[I1]: https://skillsbuild.org/university/students
[I2]: https://skillsbuild.org/university/educators
[I3]: https://www.skillsbuild.org/ai-level-up?pageAction=openChat
[I4]: https://skillsbuild.org/learning-catalog
