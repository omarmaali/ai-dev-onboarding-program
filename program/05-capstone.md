# Capstone: one real task, the whole loop

The capstone is the programme's only graded assessment. It asks each participant to do, unpaired and on a real task, what the four modules practised in pieces. A team lead reading a completed capstone should be able to answer one question: is this person ready to work on AI-assisted tasks without a pair reviewer?

**Own time:** about three hours, spread over one to two weeks after module 4. The task itself should be sized at half a day or less.

## The task

Pick one item from your real backlog, in one of the three low-risk task classes from playbook guide 5: tests for existing code, a small refactor under existing tests, or scaffolding along an existing pattern. Your team lead approves the choice; anything touching authentication, payments, data deletion or permissions is out for the capstone, since nobody should ship a risky change under assessment conditions.

Run it through the loop: spec, generate, review, test. Merge it through the normal PR process if it passes your own review; if it doesn't pass, that's a valid capstone too.

## What to submit

Five artefacts, in one folder or one PR description.

1. The spec. The task-spec template, filled in, as it was when you handed it to the model. If you revised it after a loop-back, include both versions and say what changed.
2. The diff. What the model produced, before any hand-edits. If you hand-edited, include the edits separately and say why.
3. The completed review checklist. Every box either ticked or annotated with why it doesn't apply. Findings written as you'd write them in a real review.
4. Test evidence. For at least one acceptance check, the behaviour deliberately broken and the test result before and after. Command output or a screenshot is fine. If the suite stayed green, say so and say what you did about it.
5. A short note, 150 to 300 words, on what the model got wrong. Which failure modes appeared, which stop signal fired if one did, what you'd change in the spec next time.

## How it's assessed

The [rubric](../assessment/capstone-rubric.md) has five criteria, one per learning objective, at three levels: not yet, meets, strong. "Meets" on all five is the bar for working unpaired. "Not yet" on any criterion means a short conversation with the facilitator and a resubmission of that artefact.

The note in artefact 5 is weighted more than participants expect; assessors read it first.

## Ways a capstone falls short

The spec is written after the code, to fit it. The tell is acceptance checks that read like a description of the diff. If the spec changed during the task, submit both versions.

The test evidence shows a test being made to fail by editing the test. The change has to be to the code under test.

The checklist comes back with every box ticked and no findings at all. On a real generated diff of any size that's unlikely, and the rubric treats an empty findings list on a non-trivial diff as "not yet" on objective 3 unless the note explains it.
