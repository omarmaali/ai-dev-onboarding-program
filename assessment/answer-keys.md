# Knowledge check answer keys

The knowledge checks aren't graded. These keys exist so a facilitator can read a stack of answers quickly and see which idea didn't land. Answers are indicative; a participant who reaches the same point by a different route is fine.

## Module 1

1. Any four of: how many retries, which errors count as retryable, backoff shape (fixed, exponential, jittered), whether retries are logged, what happens when retries run out, whether the retry is idempotent-safe for the operation, timeouts per attempt.
2. The acceptance checks. If you can't write two to six statements that could become tests without further discussion, the spec has an ambiguity in it, and writing the checks is the cheapest place to find that ambiguity because nothing has been generated yet.
3. Something like: "A request that fails validation returns 400 with body `{"error": "...", "field": "..."}` and no partial write occurs. A downstream timeout returns 503 and logs one warning." The test is that the rewrite names a status, a shape, and a side effect.
4. Model training data lags. Without a pinned version, the model may write against an older API surface, and the resulting code can look idiomatic while calling things that no longer exist or behave differently.
5. A generation miss: the spec was clear, the model didn't meet it; regenerate against the same spec quoting the failing check. A spec gap: the code is wrong because the spec allowed it; fix the spec first, then regenerate. Routed differently because patching the output of a spec gap leaves the ambiguity in place for the next change.

## Module 2

1. Two of: the whole repository (the model pattern-matches against everything, including code you'd rather it didn't imitate, and gets slower and vaguer); stale conversation history from earlier tasks (accumulated constraints and abandoned directions get weighted); files the task doesn't touch (noise, and a security exposure if the tool indexes them).
2. Long sessions accumulate stale constraints and half-abandoned directions. A fresh session with the spec pasted in costs a minute and avoids arguing with a context window.
3. The model rewrites files outside its list; it invents an API and defends it; it keeps fixing things you didn't raise.
4. Correct the plan before implementation. An approach is much cheaper to correct than a finished diff, and drift caught at plan stage never becomes a diff you have to review.
5. Whatever you edit, you own. The explanation bar applies to every merged line, and if the hand-patch worked around a spec gap, the gap goes into the spec before the task closes.

## Module 3

1. With a colleague, messy code marks where they struggled, and knowing the author tells you their blind spots. Model output is uniformly clean and confident with no author to know, so "slow down where it looks uncertain" has nothing to trigger on.
2. Invented APIs (verify any unrecognised call against the pinned version's docs); requirement drift (trace each acceptance check to the diff); scope creep (anything outside the file list is a reject); swallowed errors (each catch block: handle or hide?); over-engineering (abstractions with one caller, config nothing reads); tests that can't fail (name a change that would make it fail); trust-boundary carelessness (string-built queries, literal secrets, weakened defaults).
3. Requirement drift. Reading the diff top to bottom, you evaluate what's there and nod along; you don't notice what was quietly substituted, because the substitution is plausible. Starting from the spec forces you to look for each requirement and find it or not.
4. Reject wholesale and regenerate from a tightened spec. A regeneration costs a minute, so the sunk-cost reasoning that justifies fifteen comments on a colleague's PR doesn't apply.
5. The generating session will defend its own work. A fresh session reads the spec without the generator's assumptions, which is why it catches drift, and it still shares the model's blind spots, which is why it doesn't replace the human.

## Module 4

1. What leaves (secrets, code and data going out through prompts; e.g. a pasted connection string). What arrives (generated code bringing licence or security problems in; e.g. a dropped-in block structurally close to a GPL implementation). What's retained (what the vendor stores and trains on; e.g. a consumer free tier that trains on inputs).
2. Rotate the credential immediately and tell the team, no blame. Deletion isn't enough because the content has already left; retention and training terms vary by tier and the message being gone from the UI says nothing about the vendor's copy.
3. Consumer free tiers may train on inputs and retain by default: public information only. Enterprise agreements negotiate no-training, retention limits, region and audit: the default for company code. The second half of the answer is team-specific; the facilitator should know it and check the answers against it.
4. "Can any of these actually fail?" Pick the two or three tests that matter most, break the behaviour each covers (delete the check, loosen the threshold, invert the flag), run the suite, see if it goes red. Ten minutes for three tests.
5. Labels are unverifiable, decay into noise, and imply the review bar varies by author, which is backwards. Enforcement belongs in review: every line merges through the same process and the reviewer owns the merge. Adoption metrics, if wanted, come from the tools' admin consoles.
