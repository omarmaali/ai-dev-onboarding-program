# Module 4: Data rules, and tests that can fail

**Objective 4.** Decide, for a given piece of information, whether it may go into an AI tool at all, and at which tier, and apply the incident rule when it goes wrong.

**Objective 5.** Show whether a test can fail, by breaking the behaviour it claims to cover and reporting what the suite did.

**Live time:** 90 minutes, in two halves. **Own time before the session:** the module 3 homework, plus 40 minutes of reading.

## Pre-reading

- [Playbook guide 3: Security, IP and governance](https://github.com/omarmaali/ai-dev-playbook/blob/main/docs/03-security-and-ip.md), the whole guide.
- [Playbook guide 4: Evaluating AI-generated code](https://github.com/omarmaali/ai-dev-playbook/blob/main/docs/04-evaluating-ai-code.md), particularly "Coverage, and what it's worth".
- [The team working agreement template](https://github.com/omarmaali/ai-dev-playbook/blob/main/templates/team-working-agreement.md). If the team already has an adapted version, that one instead.

## Why two objectives share a module

They're the two places where an AI rollout gets hurt in a way the team can't quietly fix later, and each takes under an hour to teach, so they share the session.

## Session outline

| Time | Segment |
|---|---|
| 0:00 | Three directions of risk: what leaves, what arrives, what's retained. The tool tier table, and which tier the team's tools are actually on (the facilitator finds out beforehand). |
| 0:15 | Activity A: the paste sort. |
| 0:35 | The incident rule, and why it's phrased the way it is. |
| 0:45 | Tests that can't fail. The mutation result from the playbook README as the worked example. |
| 0:55 | Activity B: break something on purpose. |
| 1:20 | Debrief and knowledge check. |

## Activity A: the paste sort

20 minutes, small groups of three. The facilitator hands out twenty short scenarios, each a thing someone might paste into an assistant. Examples of the shape:

- A stack trace from production containing a customer's email address in the log line.
- The team's `docker-compose.yml`, which has a database password in it "for local only".
- A synthetic JSON payload with the same shape as customer records but made-up values.
- A design document for a feature that hasn't been announced.
- An expired API key, for context on how the old integration worked.
- Three hundred lines of internal service code, into the free tier of a consumer chat app, to ask what it does.

Each group sorts them into: never, approved tier only, or fine anywhere. Then, for the "never" pile, they write what they'd paste instead to get the same help. Groups compare; disagreements go to the working agreement's data rules for a ruling, and if the agreement is silent, that's a note for the agreement's owner.

The facilitator guide has a starter set of twenty scenarios; the better version uses scenarios from the team's own last month.

## Activity B: break something on purpose

25 minutes, individually, in the participant's own codebase.

1. Find a test that covers something that matters: a permission check, a validation guard, a rate limit, anything where failure is expensive. Generated or hand-written, doesn't matter.
2. Write down, before touching anything, what code change you believe would make that test fail.
3. Make the change. Disable the check, invert the condition, loosen the threshold.
4. Run the suite. Record: did the test go red? Did any test go red?
5. Revert.

Expect some participants to find a test that stays green. When I ran the same exercise on two of my own projects with [llmcheck](https://github.com/omarmaali/llmcheck), four guardrails turned out to have tests that couldn't fail, and those repos had been reviewed. It's not a comfortable result to share, so the debrief is framed around it: a test that can't fail was found before it mattered. Participants who found one say what the test was actually asserting. Usually it's one of the playbook's test red flags: asserting a mock, asserting a config flag, or exercising the line without asserting anything about the result.

**Homework.** Nothing new. The capstone starts after this session, and its test-evidence artefact is exactly activity B run on the capstone task.

## What the facilitator is watching for

In activity A, the argument that expired credentials are fine to paste. Guide 3's phrasing is that expired keys "have a way of not being", and the rule is deliberately absolute so nobody has to evaluate it under time pressure.

In activity B, participants who pick a trivially breakable test to avoid the risk of finding a bad one. Steer them to a guardrail.

## Knowledge check

1. Guide 3 sorts risk into three directions. Name them and give one example of each.
2. A colleague pastes a connection string into the approved-tier assistant, notices, and deletes the message. What does the incident rule say happens next, and why isn't deletion enough?
3. What's the difference between a consumer chat app's free tier and an enterprise agreement, in terms of what you can safely paste? Where does your team's current tool sit?
4. A generated test suite reports 94% coverage on its first run and everything is green. Guide 4 suggests a question to ask. What is it, and how would you answer it in ten minutes?
5. Mandatory "AI-assisted" labels on commits are proposed as governance. Give the argument against, from guide 3, and say where the enforcement should sit instead.
