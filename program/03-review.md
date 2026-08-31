# Module 3: Reviewing AI-written code

**Objective 3.** Review an AI-authored diff with the checklist and find the named failure modes planted in it.

**Live time:** 120 minutes, the longest session. **Own time before the session:** about 45 minutes of reading.

## Pre-reading

- [Playbook guide 2: Reviewing AI-generated code](https://github.com/omarmaali/ai-dev-playbook/blob/main/docs/02-reviewing-ai-code.md), the whole guide. Participants should be able to name the seven failure modes from memory by the session; the activity assumes it.
- [The AI code review checklist](https://github.com/omarmaali/ai-dev-playbook/blob/main/templates/ai-code-review-checklist.md). Print it or have it open in a second window during the activity.
- [The review-a-diff prompt](https://github.com/omarmaali/ai-dev-playbook/blob/main/templates/review-a-diff.md), used in the last part of the activity.

## Why this is the long session

Review is the skill that transfers least from ordinary code review. Guide 2's argument is that a reviewer's usual heuristic for where to slow down has nothing to trigger on in generated code, so the module replaces the heuristic with a deliberate list, then makes participants run the list against a diff with real problems planted in it. The facilitator builds that diff beforehand; the recipe is in [facilitator/seeded-diff-recipe.md](../facilitator/seeded-diff-recipe.md).

## Session outline

| Time | Segment |
|---|---|
| 0:00 | Why it's a different job. Ten minutes, guide 2's argument, then the seven failure modes, named by participants from the pre-reading. |
| 0:15 | Running the pass in order: spec first, surprises second, correctness, trust boundaries, tests last. Why the order matters when attention runs out before the code does. |
| 0:30 | Activity part A: solo review of the seeded diff. |
| 1:00 | Activity part B: pair calibration. |
| 1:25 | Reveal. The facilitator lists what was planted. Discussion of what was found, what was missed, and what was flagged that wasn't a defect. |
| 1:45 | Activity part C: the model as second reviewer. |
| 1:55 | Knowledge check, homework. |

## Activity: the seeded diff

The facilitator provides a spec and a diff of 150 to 300 lines that implements it, with five to seven of guide 2's failure modes planted, and at least one section of the diff that is entirely fine. Participants don't know how many were planted.

**Part A (30 minutes, solo).** Review the diff with the checklist, in the checklist's order. Record findings as: location, failure mode, what you'd write in the review comment. Also record a verdict: comment line by line, or reject and regenerate from a tightened spec?

**Part B (25 minutes, pairs).** Compare findings. For every disagreement, the pair has to reach one answer and write down why. This is the part of the module that matters most for the team afterwards, because it's where reviewers' thresholds get aligned.

Reveal and discussion (20 minutes). The facilitator shows the plant list. Go through what was found by most pairs, what was found by few, and what was flagged in the clean section. Ask anyone who found the mock-mirroring test whether they read the tests first; if so, the order wasn't followed and that's worth saying out loud.

**Part C (10 minutes).** Run the diff and the spec through the review-a-diff prompt in a fresh session. Compare the model's findings to the pair's. Guide 2's claim is that it tends to catch drift, since it reads the spec without the reviewer's assumptions, and that it shares blind spots with the generator; check both against what happened.

Homework. Review the diff each participant generated in module 2 with the checklist, alone, and bring the completed checklist to module 4.

## What the facilitator is watching for

Reviewers who go to the spec last. Enforce the order in part A by asking people to show their spec-conformance section before they move on.

Also watch for the informal higher bar guide 4 warns about: participants nitpicking the seeded diff's formatting while missing the swallowed error.

## Knowledge check

1. Guide 2 says surface quality carries information when reviewing a colleague and doesn't when reviewing a model. What information, and why does it disappear?
2. Name the seven failure modes. For any two, describe the check that finds them.
3. The review pass starts from the spec rather than from the diff. Which failure mode does that catch, and why does starting from the diff miss it?
4. A diff has two of the failure modes in its first two checklist sections. What does guide 2 recommend, and what's the reasoning about cost?
5. Why should a model used as a second reviewer run in a fresh session rather than the one that generated the code?
