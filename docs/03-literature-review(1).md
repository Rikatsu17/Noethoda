# Oiqyn — Literature Review

**Project:** Development of a Literacy Platform with Personalized Learning Recommendation  
**Team:** Adilbekov Daniyal (SE-2414); Rassul Sakenov (SE-2403)  
**Prepared:** 23 October 2026  
**Status:** Draft for team and supervisor review  
**Related deliverable:** First pre-defense, 24 October 2026

## 1. Purpose and Review Scope

This review examines three questions relevant to Oiqyn:

1. How should digital competence be defined and assessed?
2. Which approaches can recommend learning activities when interaction data are limited?
3. How should recommendation quality and learning outcomes be evaluated?

The target audience is university students aged 18 and over across different
years of study. Their skill levels and needs must be investigated rather than
inferred from their year of study.

The selected set contains **12 sources: eight peer-reviewed journal articles
[1–8], one research preprint [9], and three official framework or standards
documents [10–12]**. The preprint is supplementary and is not counted toward
the eight journal articles.

This is a targeted narrative review for project design, not an exhaustive
systematic review. Web searches were conducted on 23 October 2026 using terms
such as “digital competence higher education systematic review,” “digital
competence performance assessment,” “educational recommender systems
evaluation,” and “knowledge tracing survey.” References were checked against
publisher pages, original research records, and the issuing organizations.

Sources were selected for their connection to assessment, recommendation,
evaluation, or the planned learning content. The main recent evidence is from
2022–2025. Two 2021 reviews [1, 5] are retained as background syntheses; they
fall just outside a strict five-year window measured from the review date.
The source set is not claimed to cover every relevant publication from 2026.

**Access limitations:** claims about [1, 6, 8] are restricted to the verified
abstracts and publication metadata. For [5], the accessible publisher text
covered the review scope, approach, and methodological sections. The framework
discussion uses official publication records and explanatory pages. No
unavailable experimental details or numerical effect sizes are assumed.
Several reviews may cover overlapping studies; their sample counts must not
be added together as independent evidence.

## 2. Structured Analysis of Scientific Publications

The final two columns contain our assessment of transferability and proposed
design implications. These implications are not experimental findings of Oiqyn.

### 2.1 Digital competence and assessment

| Ref. | Evidence and approach | Relevant contribution | Limitation for Oiqyn | Proposed use |
|---|---|---|---|---|
| [1] Zhao et al. (2021) | Review of higher-education research from 2015–2021. | Examines definitions, assessment dimensions, methods, and research limitations; reports predominantly basic competence in the reviewed student and teacher populations. | Broad findings do not establish the skill level or needs of AITU students across different years of study. | Define specific skills and investigate the local audience before finalizing content. |
| [2] Saltos-Rivas et al. (2022) | Mapping study of 88 primary studies. | Finds frequent reliance on perception questionnaires and incomplete reporting of reliability and validity. | Its evidence base ends in July 2020; it does not validate a new Oiqyn assessment. | Document what each task measures, review scoring criteria, and pilot the diagnostic questions. |
| [3] González-Mujico (2024) | Development, expert validation, and implementation of two assessment rubrics. | Combines self-assessment with external observation and task-performance evidence; reports reliability for the developed instruments. | Implementation used a small convenience sample at one Spanish university: 20 lecturers and 26 students. Transfer requires adaptation. | Use concrete task answers as assessment evidence and keep self-reported confidence separate. |
| [4] Schaal et al. (2025) | Cross-sectional survey of 269 health-related students in Germany, Ukraine, and Kazakhstan. | Provides regional context and compares self-ratings with reported information-search practices. | Convenience sampling and self-report; no behavioral performance tasks. Its health-related student sample does not establish the needs of AITU students across different years of study. | Ask local participants for concrete examples, then assess skills through tasks rather than treating survey confidence as mastery. |

### 2.2 Educational recommendations and learner modelling

| Ref. | Evidence and approach | Relevant contribution | Limitation for Oiqyn | Proposed use |
|---|---|---|---|---|
| [5] Urdaneta-Ponte et al. (2021) | Review of 98 studies published during 2015–2020. | Organizes educational recommendation targets and techniques, including collaborative, content-based, and hybrid approaches. | Broad, older coverage cannot establish which algorithm will work best for a new digital-literacy platform. | Compare methods according to available data and the learning activity being recommended. |
| [6] da Silva et al. (2023) | Review of 16 selected studies from 756 candidates, covering 2015–2020. | Reports frequent hybrid approaches and accuracy-focused evaluation, with limited investigation of pedagogical effectiveness. | A selective historical sample is not evidence that every current system has the same weakness. | Separate technical relevance, usability, and learning effectiveness in the evaluation plan. |
| [7] Abdelrahman et al. (2023) | Survey of knowledge-tracing methods, assumptions, datasets, and applications. | Explains how interaction histories can inform estimated knowledge states and compares traditional and deep approaches. | Prediction performance on established datasets does not guarantee valid estimates for new skills or a small new platform. | Store task-to-skill links and assessment history; describe the MVP profile as an estimate rather than a validated knowledge-tracing model. |
| [8] Song et al. (2025) | Sequential-pattern method for MOOC learning-resource recommendations; abstract reports evaluation on a real dataset. | Uses learning histories, grades, engagement, and study duration to identify suitable sequences. | Abstract-only analysis here. Historical-data requirements limit immediate use at launch; no transfer effect to Oiqyn is established. | Treat sequence mining as a later alternative if sufficient interaction data become available. |

### 2.3 Supplementary research

| Ref. | Evidence and approach | Relevant contribution | Limitation for Oiqyn | Proposed use |
|---|---|---|---|---|
| [9] Askarbekuly and Luković (2024) | Research preprint reviewing 28 selected papers on educational recommendation evaluation. | Distinguishes rating-based relevance from learning-based evaluation and identifies limited outcome-based assessment. | A peer-reviewed publication was not verified. Its selected sample does not describe all educational recommenders. | Use it as supporting evidence for an evaluation plan that does not equate engagement or relevance with learning gains. |

## 3. Official Frameworks and Standards

These sources guide content and interface requirements. They are not empirical
evidence that Oiqyn will improve learning.

| Ref. | Source and role | Relevant contribution | Limitation | Proposed use |
|---|---|---|---|---|
| [10] Cosgrove and Cachia (2025), DigComp 3.0 | Official European digital competence framework. | Defines competence areas, learning outcomes, proficiency levels, and AI-related knowledge, skills, and attitudes. | A general framework is not a ready-made test or evidence of local needs. | Map selected Oiqyn skills to explicit outcomes; document that the MVP covers a subset. |
| [11] Miao, Shiohira, and Lao (2024), UNESCO | Official AI competency framework for students. | Addresses human judgement, ethical use, AI applications, and system design across progression levels. | Designed for curriculum guidance, not a validated university diagnostic or recommendation algorithm. | Inform limited activities on checking AI-generated information and making responsible use decisions. |
| [12] W3C (2023), WCAG 2.2 | Web accessibility standard; dated Recommendation used for reference. | Supplies testable criteria for keyboard access, contrast, labels, and input assistance. | Passing selected checks is not proof of full conformance or educational effectiveness. | Derive explicit accessibility checks for assessment forms and the student dashboard. |

## 4. Critical Synthesis

### 4.1 Define teachable skills before choosing an algorithm

The higher-education review [1] supports treating digital competence as a
research and teaching problem that requires clear definitions. DigComp 3.0
[10] provides a current reference structure. For Oiqyn, these sources support
breaking broad subjects into assessable outcomes, such as choosing appropriate
document permissions or judging whether a source supports a claim.

Our four proposed content areas are a product organization, not an exact
reproduction of every DigComp area. Each selected skill should have an outcome,
at least one assessment task, and relevant learning content. This mapping will
remain provisional until local user findings and supervisor comments are
incorporated.

### 4.2 Survey responses and task performance serve different purposes

The assessment mapping [2] raises concerns about the evidential quality of
perception-based measures. The rubric study [3] offers a way to supplement
self-report with observed performance, but its small sample limits direct
generalization. The multinational study [4] is relevant because it includes
Kazakhstan; nevertheless, its own evidence is based on reported competence
and practices, not a behavioral test.

Consequently, our interviews will inform needs and usability assumptions.
The platform's diagnostic tasks will serve a different purpose: gathering
evidence about selected skills. Neither three interviews nor a short quiz
will justify a claim that we have measured the digital competence of all
AITU students.

### 4.3 Method complexity must match the available evidence

The educational recommendation review [5] provides alternatives rather than a
universal winning method. Knowledge tracing [7] can model learning histories,
while the sequence-mining approach [8] explicitly uses historical behavior.
These methods expose a practical constraint: Oiqyn begins without a substantial
interaction dataset.

Our proposed starting point is therefore prerequisite filtering with
content-based ranking using diagnostic results and activity metadata.
This is an engineering choice under current data constraints, not a result
proving that rules outperform learned methods. Its weaknesses include manual
content tagging, dependence on the quality of prerequisite rules, and limited
ability to discover patterns beyond the designed skill structure.

### 4.4 Useful recommendations are not automatically effective teaching

The review by da Silva et al. [6] and the supplementary preprint [9] both
motivate careful evaluation of the educational objective. A recommendation
can be judged relevant without demonstrating improved knowledge.

We therefore propose separate checks for functional correctness, prerequisite
compliance, recommendation relevance, and usability. A fixed sequence will
provide a simple baseline using the same activity collection. If learning
gains are studied, they will require their own assessment design and stated
limitations. The report must distinguish prepared-profile tests from
experiments involving real learners.

### 4.5 Content quality and accessibility are part of the design

UNESCO's framework [11] helps define the intended scope of activities about
AI-generated information: learners should practise critical judgement, rather
than merely learn interface commands. This does not require Oiqyn to train or
integrate a language model.

WCAG [12] provides concrete interface checks. For example, the team can test
keyboard operation, visible focus, and labelled input fields. For ordinary
text, the referenced contrast criterion uses a 4.5:1 minimum, with defined
exceptions including large text. These checks support accessible interaction,
but they must be accompanied by task-based usability evaluation.

## 5. Literature-to-Design Traceability

The following are proposed decisions for the requirements and design stage.
They must be reviewed alongside user evidence, project resources, and
supervisor feedback.

| Proposed decision | Supporting references | Planned implementation or verification |
|---|---|---|
| Define outcomes for each selected digital skill. | [1, 10] | Maintain a skill–outcome–task–activity mapping and review content coverage. |
| Base diagnostic results on answers to concrete tasks. | [2, 3, 4] | Record scoring rules; pilot questions; retain an “insufficient evidence” state where appropriate. |
| Begin with metadata and prerequisite rules. | [5, 7, 8] | Test candidate filtering and ranking on prepared profiles; record required inputs. |
| Explain the reason for each recommendation. | [5, 7] | Show the actual rule or evidence used. This is our transparency proposal; its usefulness must be tested. |
| Keep completion, assessment results, and estimated skill state distinct. | [2, 7, 9] | Store separate records and check dashboard wording. |
| Compare recommendations with a fixed activity order. | [6, 9] | Specify identical content, evaluation profiles, and relevance criteria for both approaches. |
| Include a small number of critical AI-literacy activities. | [10, 11] | Align each activity with an explicit objective and obtain content review. |
| Make key student scenarios accessible and testable. | [12] | Check keyboard use, labels, focus, contrast, and understandable feedback; document remaining issues. |

## 6. Project Positioning and Remaining Questions

The reviewed literature already contains adaptive learning and educational
recommendation approaches. Oiqyn should not claim to invent personalized
learning or to be the first digital-literacy platform.

The proposed contribution is a working, explainable learning workflow for a
defined student audience, supported by a small structured content collection
and a documented evaluation. Whether this particular solution is needed
locally must still be supported by user discussions and the comparison of
existing systems.

Before implementation, the team should resolve:

- Which skills are most relevant to the interviewed students?
- How many diagnostic tasks can be completed without excessive burden?
- Who will review question wording, answer keys, and prerequisite relationships?
- How will a recommendation be rated as relevant during evaluation?
- What evidence would justify updating a skill estimate?
- Is there sufficient time and participation for a learning-gain study?

The literature review supports the proposed direction. It does not replace
user research, the system comparison, a full requirements specification, or
supervisor review.

## 7. References

All links were checked on 23 October 2026. Journal issue years are used where
they differ from online-first dates.

[1] Zhao, Y., Pinto Llorente, A. M., & Sánchez Gómez, M. C. (2021).
Digital competence in higher education research: A systematic literature review.
*Computers & Education, 168*, 104212.
[DOI](https://doi.org/10.1016/j.compedu.2021.104212).
[Publisher](https://www.sciencedirect.com/science/article/pii/S0360131521000890).
**Type:** Peer-reviewed journal review.

[2] Saltos-Rivas, R., Novoa-Hernández, P., & Serrano Rodríguez, R. (2022).
How Reliable and Valid are the Evaluations of Digital Competence in Higher Education:
A Systematic Mapping Study.
*SAGE Open, 12*(1).
[DOI and article](https://doi.org/10.1177/21582440211068492).
**Type:** Peer-reviewed journal mapping study.

[3] González-Mujico, F. de L. (2024).
Measuring student and educator digital competence beyond self-assessment:
Developing and validating two rubric-based frameworks.
*Education and Information Technologies, 29*, 13299–13324.
[DOI and article](https://doi.org/10.1007/s10639-023-12363-7).
Published online in December 2023.
**Type:** Peer-reviewed journal empirical study.

[4] Schaal, T., Tischendorf, T., Sydorenko, O., Karagulova, M.,
Chettykbayev, R., & Brauweiler, H.-C. (2025).
Self-assessed vs. reported digital competence among health students in Germany,
Ukraine and Kazakhstan: a DigComp 2.2–based cross-sectional study.
*Frontiers in Health Services, 5*, 1673120.
[DOI and article](https://doi.org/10.3389/frhs.2025.1673120).
**Type:** Peer-reviewed journal empirical study.

[5] Urdaneta-Ponte, M. C., Mendez-Zorrilla, A., & Oleagordia-Ruiz, I. (2021).
Recommendation Systems for Education: Systematic Review.
*Electronics, 10*(14), 1611.
[DOI and article](https://doi.org/10.3390/electronics10141611).
**Type:** Peer-reviewed journal review.

[6] da Silva, F. L., Slodkowski, B. K., da Silva, K. K. A., & Cazella, S. C. (2023).
A systematic literature review on educational recommender systems for teaching
and learning: research trends, limitations and opportunities.
*Education and Information Technologies, 28*, 3289–3328.
[DOI and publisher](https://doi.org/10.1007/s10639-022-11341-9).
Published online in September 2022.
**Type:** Peer-reviewed journal review.

[7] Abdelrahman, G., Wang, Q., & Nunes, B. P. (2023).
Knowledge Tracing: A Survey.
*ACM Computing Surveys, 55*(11), Article 224, 1–37.
[DOI and article](https://doi.org/10.1145/3569576).
**Type:** Peer-reviewed journal survey.

[8] Song, W., Zhang, Q., Fong, S., & Li, T. (2025).
Recommendation of Learning Resources for MOOCs Based on Historical Sequential Behaviours.
*Expert Systems, 42*(5), e70034.
[DOI and publisher abstract](https://doi.org/10.1111/exsy.70034).
**Type:** Peer-reviewed journal algorithm study; abstract-level use in this review.

[9] Askarbekuly, N., & Luković, I. (2024).
Learning Outcomes, Assessment, and Evaluation in Educational Recommender Systems:
A Systematic Review.
*arXiv*, 2407.09500.
[Preprint](https://arxiv.org/abs/2407.09500).
**Type:** Research preprint; not counted among the eight peer-reviewed articles.

[10] Cosgrove, J., & Cachia, R. (2025).
*DigComp 3.0: European Digital Competence Framework — Fifth Edition*.
Publications Office of the European Union. JRC144121.
[Publication record](https://publications.jrc.ec.europa.eu/repository/handle/JRC144121).
[Official framework overview](https://joint-research-centre.ec.europa.eu/scientific-activities/key-competences-lifelong-learning/digital-competence-framework-digcomp/digcomp-30_en).
**Type:** Official competence framework.

[11] Miao, F., Shiohira, K., & Lao, N. (2024).
*AI competency framework for students*. UNESCO.
[Official publication page](https://www.unesco.org/en/articles/ai-competency-framework-students).
[Publication record](https://unesdoc.unesco.org/ark:/48223/pf0000391105).
**Type:** Official competency framework.

[12] World Wide Web Consortium. (2023).
*Web Content Accessibility Guidelines (WCAG) 2.2*.
W3C Recommendation, 5 October 2023.
[Dated standard](https://www.w3.org/TR/2023/REC-WCAG22-20231005/).
[Current publication](https://www.w3.org/TR/WCAG22/).
**Type:** Official web standard; selected accessibility criteria used here.

