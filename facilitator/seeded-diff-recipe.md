# Building the seeded diff for module 3

Module 3 needs a spec and a diff that implements it with several of guide 2's failure modes planted. A weak seeded diff makes the review exercise feel like a quiz, so it's worth doing properly. Budget two hours, less if you already have a small codebase to plant it in.

## What you need to end up with

- A task spec, filled in with the playbook template, for a task of half a day or less.
- A diff of 150 to 300 lines that implements the spec, in the language the team actually works in.
- A plant list: five to seven failure modes, each with a location and a one-line description of what a correct finding looks like.
- At least one section of the diff that is completely fine, so the exercise has negatives as well as positives.

Keep the plant list in a file only you have. Participants don't get told how many plants there are.

## Choosing the task

The task needs enough surface for plants to hide in: some input handling, at least one external call (a database, a queue, an HTTP client), an error path, and tests. The playbook's filled example, per-client rate limiting on an endpoint, is a good shape. So is "add an export-to-CSV endpoint with a row limit", or "add a retry wrapper around the notification client".

Write the spec first, properly, because the review exercise starts from it.

## Getting a base diff

Easiest route: give the spec to an assistant and let it implement, exactly as module 2 teaches. You may get one or two real failure modes for free, and those are the most convincing plants because they're what the tool actually did. Note them.

Then plant the rest by hand. A spread to aim for, adjusted to the team's level:

| Failure mode | What to plant |
|---|---|
| Invented API | A call to a method that doesn't exist in the pinned version of a library the team uses, with the right naming style. Check it really doesn't exist. |
| Requirement drift | One acceptance check satisfied with a near-neighbour: rounding half-up where the spec says banker's, a 60-second fixed window where the spec says rolling, a 500 where the spec says 429. |
| Scope creep | A small refactor of a helper the task didn't touch, with a subtle behaviour change inside it. |
| Swallowed error | A broad catch that logs and continues past a failure the caller needs to know about, on the external call. |
| Over-engineering | A config option nothing reads, or an abstraction with one caller. |
| Test that can't fail | A test that configures a mock to return X and asserts X. Or a test of the rate limit that sets the limit to a large number in setup. |
| Trust boundary | A string-built query, or a secret as a default value in config. |

Six is a comfortable number.

## The clean section

Leave one part of the diff that's correct and idiomatic and does exactly what the spec says. In the reveal, ask who flagged something in that section. The conversation about false positives is as useful as the one about misses, because it's the informal higher bar from guide 4 showing up in practice.

## Packaging

Participants need the spec, the diff, and enough of the surrounding code to check the diff against (the helper that was refactored, the interface the invented API pretends to belong to). A small repo with the base code on `main` and the diff as a branch works well; so does a single markdown file with the spec, the diff, and the relevant existing files pasted in. The repo version lets participants run the tests, which makes the mock-mirroring test discoverable by running it.

Don't reuse a diff across cohorts on the same team without changing the plants.

## After the session

Save the plant list, the group's aggregate findings (what was found by most, by few, by none), and any false positives. That record tells you whether to make the next cohort's diff harder or easier.
