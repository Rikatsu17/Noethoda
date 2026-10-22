# Oiqyn — Skill Model and Recommendation Design

**Project:** Development of a Literacy Platform with Personalized Learning Recommendation  
**Team:** Adilbekov Daniyal (SE-2414); Rassul Sakenov (SE-2403)  
**Prepared:** 23 October 2026  
**Status:** Proposed design; implementation, user validation, and supervisor review pending  
**Design configuration:** `recommendation-v0.1`

## 1. Purpose and Relationship to Requirements

This document specifies how Oiqyn will turn assessment evidence into a
recommended next learning activity. It develops the provisional method in
[05-technologies.md](05-technologies.md) and the rules in
[06-requirements.md](06-requirements.md), particularly FR-05–FR-08, FR-11,
FR-12, and NFR-02.

The target users are university students aged 18 and over across different
years of study. Year of study is not a recommendation input or a substitute
for assessment evidence.

The proposed method combines prerequisite rules with a deterministic score
based on learner needs and activity metadata. It requires no collaborative
training dataset. It is planned as a Python module inside the FastAPI backend.

All thresholds, weights, difficulty labels, and example content below are
initial design choices. They are not learned parameters, interview findings,
validated measures of competence, or evidence that personalization improves
learning. This document specifies behavior to implement and evaluate.

## 2. Inputs and Data Records

| Record | Required information |
|---|---|
| Skill | Stable ID, name, content area, definition, and version. |
| Activity | Stable ID, published version, title, primary target skill, difficulty, prerequisite skill IDs, publication status, and baseline order. |
| Question | Stable ID and version, one primary skill, answer key, and feedback. |
| Submitted attempt | Learner ID, attempt ID, server-assigned submission sequence, question versions, scored answers, skipped answers, and scoring-rule version. |
| Skill evidence | Skill ID, correct/scored counts, status, source attempt ID, and evidence date. |
| Completion record | Learner ID, activity version, and completion date; separate from assessment results. |
| Recommendation decision | Profile snapshot, catalogue snapshot, configuration version, eligible candidates, factor values, selected activity or empty state, and explanation inputs. |

For recommendation purposes, the profile snapshot packages both skill evidence
and the set of completed stable activity IDs from the same committed learner
state. Live requests use the latest committed profile and catalogue snapshots;
offline evaluation explicitly pins their versions.

For version 0.1, each activity has exactly one primary target skill. Additional
topic tags may be displayed but do not affect ranking. Supporting multi-skill
ranking later requires a documented aggregation rule and a new configuration.

The learner identity comes from authentication. The frontend does not supply
an authoritative skill score or choose another learner's profile. The
recommender does not use names, gender, university group, or year of study.

## 3. Constructing the Skill Profile

Apply the assessment rules in document 06:

1. For each skill, consider submitted attempts containing at least two scored
   responses for that skill.
2. Select the latest qualifying attempt by its server-assigned submission
   sequence. Retrying an existing submission does not create a new sequence.
3. Calculate `p = correct responses / scored responses`. A correct response
   scores 1; an incorrect response scores 0; a skipped question is excluded.
4. If `p >= 0.70`, assign **Target met**. Otherwise assign **Needs practice**.
5. If no qualifying attempt exists, assign **Insufficient evidence** and store
   a null score, not zero.

A later attempt with only one scored response does not overwrite an earlier
qualifying result. Its answers remain in the attempt history. Each displayed
skill status includes the evidence date when available.

The minimum of two responses and the 70% threshold come from the proposed
settings in document 06. With only two questions, the possible scores are
0%, 50%, and 100%; the threshold therefore distinguishes those coarse results.
It does not create a precise estimate of ability.

Assessment submission and the derived profile update must be committed
consistently. The recommendation reads a committed profile snapshot, so it
cannot combine an unfinished attempt with an older profile. Historical
attempts retain their original question and scoring-rule versions.

## 4. Example Skill and Activity Catalogue

The following catalogue is a **design fixture**, not a claim that lessons have
already been authored. The four skills illustrate one topic in each content
area. The six activities provide alternative candidates for testing ranking.

| Skill | Area | Example skill definition |
|---|---|---|
| S01 | IT and internet fundamentals | Identify the domain and relevant parts of a web address. |
| S02 | Information literacy | Check an online claim against identifiable, relevant sources. |
| S03 | Digital safety | Recognize suspicious links and common phishing indicators. |
| S04 | Digital productivity | Use a basic spreadsheet formula and verify its result. |

Two difficulty labels are proposed: **1 — foundational practice** and
**2 — guided application**. Labels are assigned by the content author and must
be reviewed; they are not empirically calibrated difficulty estimates.

| ID | Example activity | Target | Difficulty | Prerequisites | Baseline order |
|---|---|---|---|---|---|
| A01 | Understand a web address | S01 | 1 | None | 1 |
| A02 | Check the source of an online claim | S02 | 1 | None | 2 |
| A03 | Spot phishing warning signs | S03 | 1 | S01 | 3 |
| A04 | Calculate a spreadsheet total | S04 | 2 | None | 4 |
| A05 | Examine links in a suspicious message | S03 | 2 | S01 | 5 |
| A06 | Compare evidence from two sources | S02 | 2 | None | 6 |

The prerequisite relation is explicit: an activity targeting S03 can require
S01 to be at target. Before publishing, reject missing skill references,
self-dependencies, and cycles in the graph formed by prerequisite-to-target
skill links. Also reject missing assessment answer keys and duplicate active
versions of the same activity.

Changing the catalogue, prerequisite links, difficulty, or baseline order
creates a new catalogue snapshot. Evaluation runs must retain the snapshot
they used.

## 5. Eligibility Before Ranking

An activity enters the candidate set only when all these conditions hold:

- Its selected catalogue version is published and available.
- Its primary target skill is marked **Needs practice**.
- Every prerequisite skill is marked **Target met**.

An empty prerequisite list passes the prerequisite check. An unknown
prerequisite does not pass. A high ranking score cannot override these rules.

Previously completed activities remain eligible if the target skill still
needs practice. They are marked as **review**. For version 0.1, an activity
counts as previously completed if the learner has a completion record for any
version of its stable activity ID. This convention is stored with the ranking
configuration.

The internal decision trace records why each activity was excluded, such as
`not_published`, `target_unknown`, `target_already_met`, or
`prerequisite_not_met`.

## 6. Candidate Score and Tie-Breaking

For an eligible activity, let `p` be the assessment score for its target skill.

| Factor | Calculation | Purpose |
|---|---|---|
| Gap G | `(0.70 - p) / 0.70` | Give more priority to a larger observed gap below the proposed target. |
| Difficulty match D | 1 when activity difficulty matches the preferred level below; otherwise 0. | Prefer the proposed level of practice for the current score. |
| New activity N | 1 if the activity has never been completed; otherwise 0. | Give a small preference to another activity while keeping review possible. |

The proposed preferred difficulty is:

- `p < 0.35`: level 1.
- `0.35 <= p < 0.70`: level 2.

Difficulty match is a preference within the eligible set, not a prerequisite.
The 0.35 boundary and the weights below are authored heuristics to review.

The score is:

```text
score = 100 × (0.70 × G + 0.20 × D + 0.10 × N)
```

For eligible activities, the score is between 0 and 100. This is a selection
score, not a probability of success, a confidence estimate, or a competence
grade.

Sort candidates by:

1. Score, descending.
2. Baseline order, ascending.
3. Stable activity ID, ascending.

Compare scores before display rounding. The formula can be evaluated as
`70 - 100 × p + 20 × D + 10 × N`; rational arithmetic using the stored
correct/scored counts avoids accidental differences between true ties.

The proposed weights make observed skill gaps the largest single factor.
Difficulty match and prior completion can still change the order. Their
usefulness must be evaluated; the weights are not claimed to be optimal.

## 7. Algorithm and Empty States

```text
recommend(profile_snapshot, catalogue_snapshot, configuration):
    validate snapshot consistency and configuration
    build eligible candidates using Section 5

    if candidates exist:
        calculate G, D, N, and score for each candidate
        sort using Section 6
        select the first candidate
        return RECOMMENDED with activity, explanation, and decision trace

    gaps = skills marked Needs practice
    unknown = skills marked Insufficient evidence

    if gaps exist:
        return NO_ELIGIBLE_CONTENT with gaps and any unknown skills
    if unknown exists:
        return ASSESSMENT_REQUIRED with unknown skills
    return TARGETS_MET
```

The skill registry must be nonempty and every represented skill must have a
status. Invalid references, a corrupt snapshot, or missing configuration
produce a controlled error; they must not be interpreted as TARGETS_MET.

| State | Meaning and interface behavior |
|---|---|
| RECOMMENDED | Show the activity, reason, and a Start or Review action. Unknown unrelated skills may still be listed as needing assessment. |
| ASSESSMENT_REQUIRED | No demonstrated gaps are available for recommendations, but some skills lack evidence. Invite the learner to complete or retake assessment. |
| NO_ELIGIBLE_CONTENT | Known gaps exist, but every relevant activity is unavailable or blocked. Show the gap and relevant blockers. If unknown skills also exist, report the need for assessment as well. |
| TARGETS_MET | All skills represented in this profile meet the proposed target. Show progress and state that this refers only to the assessed content. |

If an activity becomes archived after a recommendation was issued, opening it
must recheck availability. Show an update message and request a new
recommendation instead of starting the archived activity. The old decision
remains available for audit.

## 8. Worked Example

Assume the six activities in Section 4 are published and none has been
completed. Each score below comes from a qualifying attempt.

| Skill | Correct / scored | Score p | Status |
|---|---|---|---|
| S01 | 2 / 2 | 1.00 | Target met |
| S02 | 1 / 2 | 0.50 | Needs practice |
| S03 | 0 / 2 | 0.00 | Needs practice |
| S04 | 1 / 2 | 0.50 | Needs practice |

A01 is excluded because S01 is already at target. S01 also satisfies the
prerequisite for A03 and A05.

| Candidate | G | D | N | Selection score |
|---|---|---|---|---|
| A02 | 2/7 | 0 | 1 | 30 |
| A03 | 1 | 1 | 1 | 100 |
| A04 | 2/7 | 1 | 1 | 50 |
| A05 | 1 | 0 | 1 | 80 |
| A06 | 2/7 | 1 | 1 | 50 |

The proposed method selects **A03**. The fixed-order baseline selects **A02**,
the first eligible item in its order.

A suitable learner-facing explanation is:

> Your latest qualifying phishing assessment was 0/2. This foundational
> activity matches that practice need. Your web-address result meets its
> prerequisite, and you have not completed this activity before.

The explanation uses the actual factors. It must not say that an activity
will guarantee improvement or that its ranking score is a success probability.

**After new evidence:** if a new qualifying S03 attempt scores 2/2, S03 becomes
Target met. A03 and A05 are excluded. A04 and A06 tie at 50, so baseline order
selects A04. Merely opening or completing A03 without new scored evidence
would not change S03's status.

**If A03 had already been completed:** its score would be 90 rather than 100,
so it would still be selected and labelled Review. Completion does not
automatically imply that its target skill has been demonstrated.

These arithmetic examples illustrate the specification. They are not
application test results or evidence that A03 is educationally better than A02.

## 9. Explanation and Response Contract

Use templates filled from the selected decision, without a generative model.
Every normal explanation identifies the skill, source assessment evidence,
and whether the activity is a first attempt or review. Mention difficulty
match and prerequisites only as supported by the recorded factors. When a tie
determines the winner, the detailed explanation records that the fixed order
resolved equal scores.

Example proposed learner API response:

```json
{
  "status": "RECOMMENDED",
  "activity_id": "A03",
  "activity_version": 1,
  "is_review": false,
  "target_skill_id": "S03",
  "explanation": "Your latest qualifying phishing assessment was 0/2. This foundational activity matches that practice need. Your web-address result meets its prerequisite, and you have not completed this activity before.",
  "decision_id": "example-decision-001"
}
```

The example IDs are illustrative. The backend keeps the profile version,
catalogue version, configuration version, evidence IDs, candidate scores,
exclusion reasons, and tie-breaking result in the protected decision record.
Do not expose another learner's evidence.

For an empty state, `activity_id` and `activity_version` are null, and the
response includes the relevant skill IDs and a human-readable next step.
For example, NO_ELIGIBLE_CONTENT can report S03 as needing practice and S01
as an unassessed prerequisite. It must not treat that unknown S01 score as zero.

## 10. Baseline and Planned Verification

The baseline uses the **same profile, catalogue, eligibility rules, completion
information, and empty-state policy**. It sorts eligible activities only by
baseline order and stable ID. It does not use the gap, difficulty-match, or
new-activity weights.

This is a fixed order after common eligibility filtering. It is not an
unconditional sequence that forces students to complete ineligible content.
Its explanation must accurately say that the activity is the next eligible
item in the fixed order, rather than claiming a personalized ranking reason.

FR-12 requires at least 20 prepared profiles. The following groups define the
intended coverage; actual fixtures and recorded runs belong in
`docs/08-verification-evaluation.md` and the later implementation.

| Group | Planned profile cases | Expected checks |
|---|---|---|
| Missing evidence: 4 | No responses; one response per skill; all skipped; mix of unknown and known skills. | Preserve unknown status; return assessment state or a valid recommendation without inventing gaps. |
| Status boundaries: 4 | 0/2; 1/2; 7/10; 10/10 for a target skill. | Correct status; 7/10 reaches the target exactly. |
| Prerequisites: 4 | Required skill unknown; below target; at target; multiple prerequisites with one below target. | Every selected activity satisfies every prerequisite. |
| Ranking and ties: 4 | Section 8 profile; equal-score alternatives; completed top candidate; new evidence changes the winner. | Correct factor values, review flag, tie resolution, and updated choice. |
| Empty content and completion: 4 | All targets met; gaps with no published matching content; gaps with all candidates blocked; gaps plus unknown skills and no candidate. | Correct explicit state, blockers, and next step. |

Additional checks use these profiles without claiming additional participants:
change only year of study; repeat the identical run; reorder API/database
candidate results; archive a previously selected activity; and retry an
assessment submission. The applicable output must remain deterministic or
change only for the documented reason.

Report prerequisite violations, invalid content selections, empty-state
correctness, explanation consistency, and agreement with expected fixtures.
Assess educational relevance separately using a review rubric fixed before
rating and reviewers who do not see which method produced each candidate.
Include cases where the two methods agree, disagree, and have only one
eligible item. Do not count a higher internal score as evidence of better
recommendation quality.

## 11. Limitations, Review, and Implementation Boundaries

The initial assessment supplies little evidence. Incorrect answers can reflect
misreading or unfamiliar wording, and repeated questions can reward recall.
A latest-attempt rule can also change a profile sharply. The evaluation must
report these limitations.

Authored difficulty levels, prerequisites, weights, and thresholds may be
inaccurate. A small catalogue may yield identical recommendations from both
methods. The design has no explicit model of forgetting, no learned estimate
of difficulty, and no guarantee against repeated recommendations when practice
does not improve a score. Review these outcomes before adding complexity.

Changing the assessment threshold or evidence minimum also requires updating
document 06. Changing ranking weights, tie rules, or completion semantics
requires a new recommendation configuration and rerunning the comparisons.
Do not silently rewrite historical decisions.

Before implementation:

- Review the skill definitions and content mappings with the supervisor.
- Use actual user evidence to check whether the proposed practice scenarios
  address relevant needs.
- Review the numerical settings and record the reasons for retaining or
  changing them.
- Link the design to the system diagrams, interface mockups, and evaluation
  plan.
- Record actual team review and supervisor comments when they occur.

**Current state:** the algorithm is specified as a draft. No production code,
user-study result, benchmark result, or supervisor approval is claimed.

