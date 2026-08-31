# Capstone rubric

Five criteria, one per learning objective. Three levels each. "Meets" on all five is the bar for working unpaired on AI-assisted tasks. A "not yet" on any criterion means resubmitting that artefact after a short conversation.

Assessors: read artefact 5 (the note) first.

## Criterion 1: The spec (objective 1)

*Artefact: the task spec.*

| Not yet | Meets | Strong |
|---|---|---|
| Describes a solution rather than a contract, or acceptance checks can't be turned into tests without asking the author something. Out-of-scope section empty or generic. | Contract states observable behaviour. Versions pinned where they matter. File list explicit. Each acceptance check could become a test as written. Out of scope names at least one real temptation for this task. | As "meets", and the spec was revised after a loop-back with both versions submitted and the gap named. Or: a partner or reviewer could find no open decisions. |

## Criterion 2: The generation session (objective 2)

*Artefacts: the diff, and the note.*

| Not yet | Meets | Strong |
|---|---|---|
| Whole repo given as context, or no evidence of a plan step, or the note shows the author argued with drift for several rounds instead of restarting. | Context list written before the session and kept to the files the task needed. Plan requested and checked against the spec before implementation. Any stop signal that fired is named in the note. | As "meets", and the note identifies something the model imitated from the provided context that the author then removed from context on a restart. |

## Criterion 3: The review (objective 3)

*Artefact: the completed checklist.*

| Not yet | Meets | Strong |
|---|---|---|
| Checklist ticked through with no findings on a non-trivial diff, or findings that are formatting nitpicks while a swallowed error or scope creep sits unflagged. Pass run out of order (tests read first, spec last). | Pass run in the checklist's order. Every acceptance check traced to a line in the diff. At least one substantive finding, named by failure mode, with the review comment written as it would be sent. Lines the author can't explain are flagged rather than waved through. | As "meets", and the author made a reject-and-regenerate call with the reasoning, or ran the model as a second reviewer and reports what it caught and missed relative to their own pass. |

## Criterion 4: Data handling (objective 4)

*Artefacts: the diff, the spec, the note. Assessed by what's absent as much as what's present.*

| Not yet | Meets | Strong |
|---|---|---|
| Anything from the never-paste list appears in the spec, the context, or the prompt transcript. Or the tool used isn't at the approved tier for the code involved. | Tool and tier named in the note and consistent with the working agreement. Spec and context contain nothing from the never-paste list; where real data shape was needed, it was synthesised. | As "meets", and the note records a moment where the author caught themselves about to paste something and what they did instead. Or the author proposed a change to the working agreement based on the task. |

## Criterion 5: Test evidence (objective 5)

*Artefact: the broken-behaviour run.*

| Not yet | Meets | Strong |
|---|---|---|
| No evidence, or the "break" edited the test rather than the code, or the suite stayed green and the note doesn't mention it. | At least one acceptance check's test made to fail by changing the behaviour under test, with before and after output. Revert confirmed. | As "meets", for a test on a check that matters (a guard, a boundary, an error path). Or: the suite stayed green, the author explains what the test was really asserting, and submits a replacement test that goes red. |

## Recording the outcome

One line per participant is enough: five levels, and whether the bar for unpaired work is met. Keep the notes (artefact 5) somewhere the team can reread them.
