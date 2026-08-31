# Module 1: The loop and the spec

**Objective 1.** Write a one-page task spec, with acceptance checks, that a second person could turn into tests without asking a question.

**Live time:** 90 minutes. **Own time before the session:** about 40 minutes of reading.

## Pre-reading

- [Playbook guide 1: The workflow](https://github.com/omarmaali/ai-dev-playbook/blob/main/docs/01-workflow.md), the whole guide.
- [The task-spec template](https://github.com/omarmaali/ai-dev-playbook/blob/main/templates/task-spec.md), including the filled example at the bottom. Participants should arrive having read the example closely enough to say what its out-of-scope list is protecting against.

## Why this module comes first

The programme opens on the spec because every later module depends on it. Review in module 3 starts from the spec's acceptance checks. The test exercise in module 4 needs acceptance checks to turn into tests.

The session's central idea, from guide 1: a model never leaves a gap open. Every decision the spec doesn't make, the model makes, and it makes it plausibly. The exercise is designed so participants see how many decisions they were delegating.

## Session outline

| Time | Segment |
|---|---|
| 0:00 | Why the loop, why now. The four stages in ten minutes, with the diagram. Not a lecture on the guide; participants have read it. Instead, ask the room for the stage they personally skip most often and why. |
| 0:15 | Walk through the filled example in the template. For each of the six sections, ask: what goes wrong if this section is empty? |
| 0:30 | Activity part A, solo writing. |
| 0:55 | Activity part B, the swap. |
| 1:15 | Debrief. What kinds of gaps did partners find? Collect them on a shared board; they become the team's own spec checklist. |
| 1:25 | Knowledge check, then close with the homework. |

## Activity: the gap hunt

**Part A (25 minutes, solo).** Each participant picks one real item from their current backlog, sized at half a day or less, and writes a task spec for it using the template. Real items only; a made-up task has no context to get wrong. The facilitator can supply two fallback tasks for anyone who arrives without one.

**Part B (20 minutes, pairs).** Swap specs. Each partner reads the other's spec as if they were the model, and lists every decision the spec leaves open: anything they would have to guess to implement it. Then, separately, they try to write one test per acceptance check. Any check they can't turn into a test without asking a question gets marked.

The two lists come back to the author, who revises the spec on the spot. A long list of open decisions is the expected result of a first spec.

**Homework.** Run the revised spec through your assistant before module 2 and keep the output; module 2 starts from it. Don't review or merge it yet.

## What the facilitator is watching for

Specs that describe the solution ("add a retry loop in the client class") rather than the contract. Redirect them to observable behaviour: what does a caller see? Also, out-of-scope sections left empty because the author didn't think of anything; send them back to the partner's list.

## Knowledge check

Five questions, written answers, about ten minutes. Not graded; the facilitator reads them before module 2.

1. A spec says "add retry logic to the payment client" and nothing else about retries. List four decisions the model will make on the author's behalf.
2. What is the readiness test for a spec, according to guide 1? Why is that section the one that reveals ambiguity earliest?
3. Your partner wrote an acceptance check: "the endpoint handles errors gracefully". Rewrite it so it could become a test.
4. Why does the template ask for pinned versions? What goes wrong without them?
5. The loop kicked a task back at review. Describe the two kinds of failure guide 1 distinguishes, and why they're handled differently.
