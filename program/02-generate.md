# Module 2: Generating with discipline

**Objective 2.** Run a generation session with curated context, and recognise the signals that mean the session should be restarted rather than argued with.

**Live time:** 90 minutes. **Own time before the session:** the homework from module 1, plus 20 minutes of reading.

## Pre-reading

- [Playbook guide 1, section 2 "Generate"](https://github.com/omarmaali/ai-dev-playbook/blob/main/docs/01-workflow.md#2--generate) and section "When the loop kicks back".
- The prompt templates: [implement from spec](https://github.com/omarmaali/ai-dev-playbook/blob/main/templates/implement-from-spec.md), [refactor](https://github.com/omarmaali/ai-dev-playbook/blob/main/templates/refactor.md), [write tests](https://github.com/omarmaali/ai-dev-playbook/blob/main/templates/write-tests.md), [debug](https://github.com/omarmaali/ai-dev-playbook/blob/main/templates/debug.md). Skim all four; read implement-from-spec properly.

## What this module is and isn't

This is the module participants expect to be about prompting tricks. It isn't. The craft in the generate stage is mostly subtraction: fewer files in context, one task per session, a plan before any code, and a set of rules for when to stop.

It has the least new content of the four modules, so most of the session is practice.

## Session outline

| Time | Segment |
|---|---|
| 0:00 | Homework review. Three volunteers show what their assistant produced from the module 1 spec. The room looks for one thing only: did the output do anything the spec didn't ask for? |
| 0:20 | Context discipline. Why the whole repo is the wrong input, and the three-to-eight-file rule. Demonstrate the same spec with the whole repo versus a curated set, if the facilitator has a codebase where the difference shows. |
| 0:35 | Plan-first. Walk the implement-from-spec template and the reason the plan comes before code. |
| 0:45 | Activity. |
| 1:15 | Debrief around one question: at what moment did you decide the session was done, and what told you? |
| 1:25 | Knowledge check. |

## Activity: plan, generate, and catch the drift

Individually, 30 minutes, on the participant's own machine with their own approved tool (see module 4 on what "approved" means; for this session the facilitator confirms the tool tier in advance).

1. Take the revised spec from module 1. Choose the files the model needs: the ones it will change and the interfaces it must call. Write the list down before opening the tool. Aim for three to eight.
2. Start a fresh session. Use the implement-from-spec template and ask for the plan only.
3. Check the plan against the spec's file list and out-of-scope section. If the plan touches anything outside, correct the plan before implementation starts.
4. Let it implement. While it runs, keep a two-column log: things the output did that the spec asked for, and things it did that the spec didn't.
5. Stop the session at the first of: the model edits a file outside the list, invents an API it can't point to in the pinned docs, or "fixes" something you didn't raise. Note which signal fired, and how many minutes in.

Participants who don't hit any stop signal within 30 minutes keep the diff for module 3 anyway.

## What the facilitator is watching for

The tempting behaviour is to argue with drift: "no, I said not to touch that file", then again, then again. Guide 1's rule is that restarting with a tighter spec is cheaper than arguing. The activity's stop rule forces the restart at least once.

Watch also for participants pasting the whole repo because curating felt like effort. Ask them afterwards what the model imitated that they'd rather it hadn't.

## Knowledge check

1. Guide 1 says context discipline is "mostly subtraction". Name two things you should leave out of a generation session and what goes wrong when each is included.
2. Why start a new session for each task rather than continuing a long conversation?
3. List the three behaviours that mean a session is done and the spec needs work.
4. You asked for a plan first and the plan proposes changing a file outside the spec's list. What do you do, and why is it cheaper to do it now?
5. The model produced a diff that hand-patching would fix in two minutes. Guide 1 allows the hand-patch. What obligation comes with it?
