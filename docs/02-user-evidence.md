# Oiqyn — Student Research: Survey and Interviews

**Project:** Development of a Literacy Platform with Personalized Learning Recommendation  
**University:** Astana IT University  
**Team:** Adilbekov Daniyal (SE-2414), Rassul Sakenov (SE-2403)  
**Prepared:** 23 October 2026  
**First pre-defense:** 24 October 2026  
**Status:** Survey analyzed; interview summaries documented for team review.

## 1. Why we did this research

Oiqyn is our diploma project: a web platform that helps students figure out which IT and digital skills they need to improve. The idea is to give students a short assessment, show them what they know and what still needs work, and recommend useful lessons and exercises.

Before building the platform, we wanted to understand how students actually deal with digital tasks. Do they know what to learn next? Where do they go when they get stuck? Would they find a skills test and personalized recommendations useful, or would they rather use the tools they already know?

We focused on everyday IT skills, finding and checking information, staying safe online, and using digital tools for study. We used a Google Forms survey and three semi-structured student interviews to explore these questions from different angles. We did not assume that students needed every planned feature of Oiqyn.

## 2. How we collected feedback

### 2.1 Student interviews

We spoke with three university students about their experience with digital tasks, online learning, and the features they would expect from Oiqyn. The conversations were semi-structured: we covered similar topics, but asked follow-up questions to understand the reasons behind each answer. We refer to the participants as P1, P2, and P3 rather than using their names.

P1 focused on everyday digital tasks and the difficulty of spotting knowledge gaps. P2 discussed online courses and learning at the right pace. P3 gave more critical feedback about the reliability of skill assessments, recommendation explanations, and privacy. We summarized their views below rather than reproducing full conversations.

### 2.2 Google Forms survey

**Survey:** [Oiqyn survey — Google Forms](https://forms.gle/Ay4iSbo7fCopG2dt5)  
**Data source:** Team-provided export `Новая форма.csv.zip` (CSV).  
**Collection date:** 23 October 2026 (timestamps in the submitted export).  
**Submissions:** 34; **eligible consenting respondents:** 33; **excluded:** 1 who selected "no" for the joint age/student/consent eligibility question. Unless indicated otherwise, percentages below use **N = 33**. The answer to the eligibility question was self-reported, not independently verified.

The questionnaire had 12 numbered items: eligibility, university year, help frequency, digital tasks causing difficulty (multiple selection), first help source, preferred learning device, biggest online-learning difficulty, checking skill mastery, lesson fit, likelihood of trying Oiqyn, valued platform features (up to two selections), and an open-ended example of a difficult task.

### 2.3 What students told us in the survey

| Survey item | Result among eligible respondents |
|---|---|
| Year of study | First-year bachelor 5; second-year 6; third-year 7; fourth-year or above 5; master's/doctoral 10 |
| Needed digital-task help in past four weeks | 1–2 times: 1/33 (3.0%); 3–5 times: 30/33 (90.9%); 6+ times: 2/33 (6.1%) |
| First response to getting stuck | Asked an AI assistant: 21/33 (63.6%); searched web: 12/33 (36.4%) |
| Preferred device for short lessons | Laptop: 32/33 (97.0%); desktop: 1/33 (3.0%) |
| Biggest difficulty learning digital skills online | Making time: 16/33 (48.5%); finding practical exercises: 10/33 (30.3%); finding appropriate difficulty: 3/33 (9.1%); knowing where to start: 2/33 (6.1%); finding clear/trustworthy explanations: 2/33 (6.1%) |
| How they check skill mastery | Complete a similar task independently: 32/33 (97.0%); ask someone to check: 1/33 (3.0%) |
| Fit of last online lesson | About right: 29/33 (87.9%); slightly too easy: 1; slightly too advanced: 1; much too advanced: 1; don't remember: 1 |
| Likelihood of trying Oiqyn, 1–5 | Score 4: 31/33 (93.9%); score 5: 1/33 (3.0%); score 3: 1/33 (3.0%); scores 1–2: 0 |
| Features selected (up to two) | Practical exercises with feedback: 33/33 (100%); initial assessment: 21/33 (63.6%); next-topic suggestions: 9/33 (27.3%); explanation of suggestions: 1/33; progress record: 1/33 |

For the digital-task difficulty multiple-select item, spreadsheet/document/presentation work and checking online/AI information appear repeatedly. Because respondents could select more than one, per-category percentages should not be interpreted as mutually exclusive.

### 2.4 What stood out to us

A few findings stood out. First, the most common problem was **finding time to study** (16 of 33 students). Another 10 students said it was hard to find practical exercises. That matters for Oiqyn: adding more material is not enough if students do not have time or opportunities to use it.

The preference for practice was even clearer in the feature question. **All 33 eligible respondents selected practical exercises with feedback** as one of the useful parts of the proposed platform. Also, 32 said they normally check whether they have learned something by completing a similar task on their own. Together, these answers support giving students short tasks and feedback, not just reading material.

When students described recent difficulties in their own words, many mentioned document formatting, citations and bibliographies, Excel formulas, pivot tables, and complex tables. They often searched online, watched tutorials, asked someone else, or used an AI assistant. These are examples the respondents reported; we did not observe them completing the tasks ourselves.

There were also results that challenged our assumptions. **29 of 33** said their last online lesson was about the right level. So we should not say that most students struggle with unsuitable course difficulty. And although **32 of 33** rated their likelihood of trying Oiqyn as 4 or 5 out of 5, that is only an expression of interest. It does not mean they will definitely use the finished product.

We also need to be careful with this survey. Responses came in close together, and several written answers are unusually similar. We cannot tell from the export why that happened. The group is small and was not randomly sampled, so these numbers describe our respondents, not all university students. We should confirm the survey collection process with the team before making stronger claims.

## 3. Student interview findings

### P1 — Digital learning challenges

P1 described their digital skills as average. While everyday tasks such as creating documents and presentations were easy, more advanced tasks, especially Excel formulas, sometimes caused difficulties. When facing unfamiliar problems, the student usually relied on ChatGPT, YouTube, or online searches. However, finding explanations at the right difficulty level was not always easy.

The participant liked the idea of a short diagnostic assessment that could identify weak areas and recommend suitable lessons. They preferred short learning activities with practical exercises and wanted to see explanations for incorrect answers and track their progress.

**Key finding:** Students may benefit from skill assessments, practical exercises, and clear progress tracking.

### P2 — Online learning experience

P2 had experience using Stepik and YouTube for university subjects and programming. The participant mentioned that some online courses were unnecessarily long, repeated familiar material, or moved too quickly into advanced topics. This sometimes made it difficult to stay motivated and complete courses.

The student supported personalized recommendations but emphasized that they should reflect actual knowledge. They also wanted the freedom to choose topics independently and preferred short lessons with practical tasks.

**Key finding:** Personalized learning paths should help students avoid unnecessary repetition while allowing flexibility in choosing topics.

### P3 — Assessment reliability and privacy

P3 considered their IT skills relatively strong but acknowledged difficulties in digital security and evaluating online information. The participant questioned whether a short test could accurately measure someone's abilities and suggested including practical questions rather than relying only on theory.

The student was interested in personalized recommendations but wanted explanations showing why certain lessons were suggested. They also emphasized keeping assessment results private and allowing students to retake tests to measure improvement.

**Key finding:** Reliable assessments, understandable recommendations, and privacy protection are important for student trust.

## 4. Shared themes and differences

The three participants brought different experiences, but several ideas appeared across the discussions. They wanted learning to be **practical and focused**. Rather than reading a long course from beginning to end, they were interested in working on a specific weakness and then checking whether they had improved. All three were interested in seeing the results of practice or assessment over time, although their reasons differed: P1 wanted to notice improvement, P2 wanted to avoid learning only for completion, and P3 wanted evidence that a skill had actually improved.

They also wanted **recommendations they could understand**. P1 valued knowing what to study; P2 worried about being sent back to familiar material; and P3 questioned how much a short diagnostic test could really prove. This is an important difference. Interest in personalization does not automatically mean trust in an algorithm. An explanation tied to a particular answer or skill could help users judge whether a recommendation is useful.

The interviews also show why the product needs a reasonable scope. P2 requested some freedom to choose a topic independently, while P3 emphasized privacy and a simple interface. These are useful considerations, but three interviews are not enough to establish which extra features should be prioritized above the core assessment–practice–feedback flow.

| Theme | Interview evidence | Implication |
|---|---|---|
| Recognizing personal skill gaps | P1 described discovering weaknesses only when doing a task; P2 was unsure when they were ready for the next topic | Present skill-specific assessment evidence rather than only an overall score |
| Avoiding unnecessary material | P1 mentioned overly basic tutorials; P2 described repetitive course content | Recommend the next suitable activity based on known needs |
| Practical learning | P1 and P2 preferred short lessons with tasks; P3 argued for practical assessment | Give practice and feedback a central role |
| Confidence in recommendations | P2 and P3 wanted to understand why a topic was suggested | Explain recommendations using assessment evidence |
| Tracking improvement | P1, P2 and P3 valued checking results after study | Keep assessment history and support reassessment |
| Privacy and simplicity | P3 explicitly raised private scores and a simple interface | Protect student records and avoid unnecessary steps |

## 5. How this feedback relates to Oiqyn requirements

We already have draft requirements in [`06-requirements.md`](06-requirements.md). The table connects themes from the interview summaries and the survey to the existing requirements. An interview can suggest a need, but it does not on its own establish how widely that need is shared.

| Question or potential need to investigate | Existing requirement(s) | Interview and survey findings | Decision after review |
|---|---|---|---|
| Students need to identify skill gaps | FR-03, FR-05 | P1 and P2 discussed uncertainty about gaps or readiness; survey: initial assessment 21/33 | Keep draft priority; review against interview summaries and supervisor feedback |
| Students need clear test results and mistakes explained | FR-04 | P1 and P3 wanted explanations of mistakes; survey: practice with feedback 33/33 | Keep draft priority; review against interview summaries and supervisor feedback |
| Suitable next activity should depend on skill evidence | FR-06 | P1 and P2 liked suggested next steps; P2 and P3 questioned their accuracy; survey: suggestions 9/33 | Keep draft priority; review against interview summaries and supervisor feedback |
| Reasons for recommendations should be understandable | FR-07 | P2 and P3 wanted reasons linked to test results; survey: explicit explanation option 1/33 | Keep draft priority; review against interview summaries and supervisor feedback |
| Short learning activities with practice and retakes | FR-08 | All three described a role for practice and checking progress; survey: practice with feedback 33/33 | Keep draft priority; review against interview summaries and supervisor feedback |
| Students want to review learning progress | FR-09, FR-13 | All three mentioned comparing learning results; survey: progress record 1/33 | Keep draft priority; review against interview summaries and supervisor feedback |
| Students want personal results kept private | FR-02, NFR-01 | P3 wanted test results and weak-skill information kept private; survey did not ask about privacy | Keep draft priority; review against interview summaries and supervisor feedback |
| Interface should be usable on typical devices | NFR-03, NFR-04 | Survey: laptop selected by 32/33 | Keep draft priority; review against interview summaries and supervisor feedback |

Requirements, priorities, and acceptance criteria remain in [`06-requirements.md`](06-requirements.md); user evidence is intended to inform their review, not silently redefine them. If evidence changes a requirement, record the rationale, affected IDs, supervisor review, and corresponding YouTrack / pull request links.

## 6. What this changes for our design

The research gives us a clearer reason to prioritize the core learning journey. Practical exercises and feedback are not just features we included in the proposal: they were also the strongest preferences in the survey, and the interviews help explain why students would value them. It is important that the platform shows mistakes and offers a chance to apply the material, instead of treating a completed lesson as proof of understanding.

The feedback also suggests that recommendations need to be modest and transparent. We should base them on recorded assessment evidence, explain the related skill gap, and show when there is not enough information to judge a skill confidently. At the same time, we should not claim that the interviews prove our recommendation method works better than a fixed learning path. That still requires evaluation.

Some suggestions, such as independently browsing or selecting topics, may be useful later. They should be reviewed against the limited MVP scope before becoming new requirements.

## 7. Limitations and privacy

Our survey provides useful early feedback, but it is only one small group of respondents. We have 33 eligible survey answers, not 33 observed tests of digital skills. We cannot use their self-reports to prove that Oiqyn improves learning or that its recommendations are accurate.

Interview descriptions are anonymized. The team should retain the original participant responses privately and confirm consent before using direct quotations or sharing records. The summaries here should be checked against those records before final submission.
