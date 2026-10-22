# Oiqyn — UX Prototype

**Project:** Development of a Literacy Platform with Personalized Learning Recommendation  
**Team:** Adilbekov Daniyal (SE-2414); Rassul Sakenov (SE-2403)  
**Prepared:** 23 October 2026  
**Status:** Interactive prototype for review; user testing and supervisor feedback pending

## 1. Purpose and Audience

This prototype demonstrates how an adult university student, from any year of
study, can move from assessment evidence to an explained learning activity and
updated progress. It also shows a limited content-administration scenario.

It supports the UX / prototype deliverable for the first pre-defense.
The prototype is implemented with HTML, CSS, and JavaScript for easy review.
The planned application architecture remains React/TypeScript, FastAPI, and
PostgreSQL, as documented in `docs/05-technologies.md`.

All learner records are fictional. The prototype does not establish user
demand, measured learning improvement, or completion of the backend requirements.

## 2. Run the Prototype

Keep these files together:

- `index.html` — prototype entry point.
- `styles.css` — responsive interface styles.
- `app.js` — demo content, screen navigation, and browser-side interactions.
- `README.md` — this guide, scenario mapping, and review notes.

Open `index.html` in a browser. No dependency installation is required.
The interface loads its assets from the same folder and does not need a content
API or an external font service.

The initial screen uses the **Sample profile** scenario. The top demonstration
bar offers a new-learner journey and other prepared states. Selecting a scenario
resets the sample profile, catalogue edits, completion records, and new attempt
history. All changes are demonstration data.

State is stored in the current browser session when session storage is
available. If storage is unavailable for local files, the prototype still
works in memory, but a refresh resets that state.

## 3. Screens and Requirement Mapping

| Screen or interaction | What the reviewer can inspect | Related requirements |
|---|---|---|
| Registration / sign-in preview | Sample account fields and entry into the learner journey. | FR-01; real authentication is not implemented. |
| Diagnostic assessment | Eight questions covering four skills, answer selection, explicit skipping, and navigation. | FR-03, FR-04 |
| Assessment feedback | Correct, incorrect, and skipped answers; explanations; scored-answer count. | FR-04 |
| Skill profile | Target met, Needs practice, and Insufficient evidence; visible source labels. | FR-05 |
| Overview and recommendation | Recommended activity, reason, and next action. | FR-06, FR-07 |
| Activity and practice | Short learning content, a completion action, and two practice questions. | FR-08 |
| Progress | New attempts, completed activities, feedback review, and skill filtering. | FR-09, FR-13 |
| Administrator preview | Catalogue, selected metadata edits, publication, archive action, and prerequisite validation. | Selected interactions from FR-10 and FR-11; full content authoring is future work. |
| Responsive layout | Main screens adapt to a narrow viewport. | Design support for NFR-03, NFR-04, and NFR-06; formal acceptance remains separate. |

The prototype follows the scenarios and actor separation in `diagrams/`.
The administration toggle is a demonstration control, not the intended
production permission system. The offline evaluation runner from the component
diagram does not require its own web screen.

## 4. Demonstration Scenarios

### A. New learner and initial evidence

1. Select **New learner journey**.
2. Review the registration screen. The sample fields are read-only; no real
   credentials are collected and no real account is created.
3. Select **Create demo profile**.
4. Answer or explicitly skip the eight diagnostic questions.
5. Review feedback, then select **See my next step**.
6. Inspect the skill statuses and the recommendation or assessment prompt.

Each skill needs at least two scored answers to receive a new status. A skipped
question is not scored as incorrect. An all-skipped attempt has no percentage
score. A later incomplete attempt preserves earlier qualifying evidence.

### B. Recommendation, activity, and updated progress

1. Select **Sample profile** in the Preview menu.
2. The profile contains S01 = 2/2, S02 = 1/2, S03 = 0/2, and S04 = 1/2.
   The next activity is A03, **Spot phishing warning signs**.
3. Read **Why this activity?**, then select **Start activity**.
4. Select **Mark lesson complete**. The lesson completion changes, while the
   phishing skill remains Needs practice.
5. Select **Start practice** and answer both questions correctly.
6. After feedback, select **See my next step**.
7. The phishing skill is now at target, and A04, **Calculate a spreadsheet
   total**, becomes the next recommendation.
8. Open **Progress** to inspect the separate completion and attempt records.

The recommendations use the version 0.1 rules from
`docs/07-recommendation-design.md`: prerequisite filtering followed by
70% gap, 20% difficulty match, and 10% new-activity preference, with fixed-order
tie-breaking. This browser implementation demonstrates the interaction; the
production scoring and authorization belong in the backend.

### C. Missing evidence and blocked recommendations

Use the Preview menu:

| Scenario | Expected interface |
|---|---|
| Missing evidence | Unknown skill statuses, no percentage estimate, and an invitation to start assessment. |
| Blocked prerequisite | Phishing needs practice but web-address evidence is missing; explain the blocker without recommending the blocked activity. |
| All targets met | Explain that the currently represented skills are at target and offer progress review. |

The interface must not turn an unknown skill into a zero score or imply that
reaching these limited targets certifies overall digital competence.

### D. Content administration

1. Load **Sample profile**, then open **Content admin preview**.
2. Select an activity using **Edit**.
3. Inspect its title, target skill, difficulty, and prerequisites.
4. Try assigning its target skill as its own prerequisite. **Save & publish**
   displays an error instead of publishing.
5. Restore valid metadata and publish a new sample version.
6. Archive A03 and return to **Learner view**.
7. The next recommendation excludes A03; with the default profile, A05 becomes
   the next candidate.

The prototype also checks cycles across the published prerequisite links.
It does not implement a complete question editor, draft-authoring workflow,
database version history, or server-side access control.

## 5. Short Presentation Script

> This is our interactive UX prototype. It uses a fictional student profile
> to demonstrate the main learning journey.
>
> The overview shows an activity and the evidence behind its recommendation.
> In this example, the student needs practice with phishing and has already
> met the web-address prerequisite.
>
> Completing a lesson updates completion history. It does not automatically
> change the assessed skill. After a qualifying practice result, the profile
> and next recommendation are updated.
>
> We also show missing-evidence and blocked-prerequisite states. The interface
> keeps uncertainty visible instead of inventing a score.
>
> The prototype helps us review the scenarios before implementing the full
> backend and conducting usability testing with target users.

## 6. Prototype Checks Completed

These checks were performed on the prototype on 23 October 2026. They are
technical checks, not a participant usability study.

| Check | Observed result |
|---|---|
| Default sample recommendation | A03 selected with the expected skill evidence and prerequisite explanation. |
| Lesson completion | Completion recorded while phishing remained Needs practice. |
| Correct phishing practice | 2/2 feedback, updated phishing status, and next recommendation A04. |
| No answer selected | Next action displayed guidance to choose an answer or explicitly skip. |
| All diagnostic questions skipped | No percentage score; eight skipped answers retained as missing evidence. |
| Partially completed diagnostic | Two correct web-address answers updated S01; the other three skipped skills remained unknown. |
| Blocked prerequisite and all-targets-met states | Distinct messages and suitable next actions appeared. |
| Invalid self-prerequisite | Publication was rejected with an explanatory message. |
| Valid metadata publication | The sample activity version increased. |
| Archived A03 | A03 was removed from new recommendations and A05 became the next candidate. |
| Desktop and 360 × 800 CSS-pixel embedded viewport | Main layout, new-learner entry, question selection, skipping, and feedback were inspected; mobile question navigation kept the next question visible. |
| JavaScript syntax | The source passed a JavaScript syntax check. |

Only the available Chrome preview was inspected. Physical-device testing,
Firefox testing, a complete keyboard/screen-reader audit, contrast auditing,
and the planned formative usability study remain pending. These checks do not
constitute acceptance of all NFRs in document 06.

## 7. Scope and Limitations

- All accounts, answers, progress, and content edits are browser-side sample
  data. There is no FastAPI or PostgreSQL connection in this prototype.
- The sample sign-in and role toggle demonstrate screens; they provide no
  real authentication or security boundary.
- The content catalogue is small and manually authored. The assessment items
  and difficulty labels have not been validated.
- Source labels such as “Sample diagnostic” and “Latest demo attempt” stand in
  for the detailed dates and evidence references of the planned application.
- Assessment snapshots are retained within demo history. This is not the
  complete server-side content-versioning or concurrent-submission design.
- Repeated practice questions can support memorisation; correct demo answers
  do not establish general learning improvement.
- Scenario switching resets sample changes. The prototype is intended for
  review and presentation, not participant data collection.

## 8. Review Still Required

- [ ] Rassul reviews the screens and main scenarios.
- [ ] The team addresses review comments through the linked pull request.
- [ ] Target users try the main journey under the planned usability protocol.
- [ ] The supervisor reviews the prototype and its alignment with requirements.
- [ ] Actual comments and resulting changes are recorded.

Add the actual YouTrack issue and Pull Request links after creating them.

