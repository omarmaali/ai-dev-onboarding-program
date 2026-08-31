# Facilitator guide

How to run the programme: preparation, the two delivery formats, what to do when a session goes sideways, and how to cut it for audiences that aren't developers. Written for a team lead or a trainer who has read the playbook and is delivering this for the first time.

## Preparation checklist

In rough order of how long each takes.

- The seeded diff for module 3. Two hours, more if you're building the small codebase it lives in from scratch. Recipe in [seeded-diff-recipe.md](seeded-diff-recipe.md). Do this first; it's the only preparation that can't be done the night before.
- Find out which tier the team's tools are on. Read the data-processing terms of whatever assistant people actually use. You'll present the answer in module 4 and it needs to be right. If the honest answer is "consumer free tier, and people paste internal code into it", say so plainly in the session.
- The working agreement. If the team has one, use it in module 4. If not, adapt the [playbook template](https://github.com/omarmaali/ai-dev-playbook/blob/main/templates/team-working-agreement.md) enough to have a tools table and a never-paste list; the rest can stay in brackets.
- Twenty paste scenarios for module 4. A starter set is at the bottom of this guide. Replace at least half with things from the team's own recent history.
- Two fallback tasks for module 1, for participants who arrive without a backlog item. Real tasks from the team's codebase, half a day each, in one of the three low-risk classes.
- Confirm each participant can run their test suite locally before module 4. Ask early.
- Send the pre-reading a week before each module, with the specific sections named. Participants who haven't read guide 2 by module 3 will hold the session back; the failure modes are assumed knowledge there.

## Two delivery formats

Weekly, alongside a pilot (recommended). One module per week for four weeks, capstone in weeks five and six. This fits the pilot cadence in playbook guide 5: the weekly retro ("what did the model get wrong this week") runs in the same slot, and the artefacts it produces feed the next session. Homework between modules is real work on real tasks. Total participant commitment: about seven hours live, four to five hours of reading and homework, three hours of capstone.

Two-day intensive. Day one: modules 1 and 2 in the morning, module 3 after lunch. Day two: module 4 in the morning, then a supervised start on the capstone in the afternoon, with submission a week later. Works for a distributed team that can only get everyone together once. The cost is that homework collapses into the session, so module 2's activity has to run on the module 1 spec written an hour earlier, and the specs are rougher. Expect module 2's activity to run long.

Session plans with timings are inside each module file. The module 3 plan has no slack.

## Framing the same material for different rooms

The thing I'd most want to pass on from running these sessions internally: the material barely changes between audiences, and the framing changes completely.

Developers want to know it won't slow them down. Open with the spec exercise's payoff (fewer regenerations, fewer review rounds) rather than with governance. Module 4's data rules land better after module 3 has shown them a diff with a literal secret in it.

QA engineers ask the sharpest questions, and the question is always some version of "how would you test that?". Module 4's break-something exercise is theirs, and in a mixed group, pair a QA engineer with a developer for module 3's calibration. They'll disagree about the mock-mirroring test.

Team leads and architects want the measurement conversation from guide 4. Give it to them at the end of module 4 rather than the start of module 1.

## Adapting for other audiences

Product, support, operations and other non-engineering teams use these tools too, usually with less guidance. They don't need the full programme.

Run module 1 with the spec reframed as "a brief for a task you're delegating", using their own tasks (a customer reply, a report, a process doc) instead of code. The gap-hunt exercise works unchanged. Then run module 4's first half, the data rules and the paste sort, with scenarios from their world: customer emails, contract text, HR information, unreleased roadmap. Skip modules 2 and 3 and the capstone. About three hours total.

The one idea to make sure survives the cut: whatever you paste, you're sending to a third party, and the incident rule applies to them the same as to engineers.

## When a session goes sideways

### The group wants a tool demo

Someone asks you to show the assistant's features. Decline, kindly, and say why: a feature tour teaches people to generate more, and generating isn't what the programme is for. If the appetite is real, offer a separate optional session and keep it out of the programme.

### The spec exercise runs long

Cut the module 1 debrief to ten minutes rather than cutting part B.

### Nobody found anything in the seeded diff

Either the plants are too subtle for the group's level, or people went to the spec last. Check which by asking one pair to show their spec-conformance section. If it's empty, run part A again for fifteen minutes with the order enforced. If it's full and they still found nothing, the diff needs a more obvious plant; add a swallowed error and move on.

### A participant argues that the rules are theatre

Often a senior who's been using the tools for a while without incident. Don't argue the general case. Ask them to bring a real generated diff of theirs to module 3 and review it with the checklist in front of the group.

### Module 4's break exercise finds nothing because everyone picked easy tests

Name it, and give everyone ten more minutes with the instruction "pick the test you'd least like to be wrong".

## Starter paste scenarios for module 4

Twenty, for sorting into never / approved tier only / fine anywhere. Answers in brackets; some are deliberately arguable.

1. A production stack trace whose log line includes a customer's email address. [never as-is; redact, then approved tier]
2. `docker-compose.yml` with a database password for local dev. [never; the password is a credential regardless of environment]
3. A synthetic JSON payload with customer-record shape and made-up values. [approved tier; shape is internal design]
4. Design document for an unannounced feature. [approved tier only]
5. An expired API key, for context on the old integration. [never]
6. 300 lines of internal service code into a consumer chat app's free tier. [never at that tier; approved tier is fine]
7. A public open-source library's source, to ask what a function does. [fine anywhere]
8. Pentest findings from last quarter, to ask for remediation ideas. [never]
9. A colleague's PR description, no code. [approved tier; it describes internal work]
10. Your own scratch notes on an algorithm, no company context. [fine anywhere]
11. The error message from a failing build, with file paths that reveal the repo structure. [approved tier]
12. A contract clause from a vendor agreement under NDA. [never]
13. Anonymised aggregate metrics (weekly active users, no identifiers). [approved tier; arguable]
14. A `.env.example` file with placeholder values. [approved tier; check the placeholders really are placeholders]
15. A screenshot of an internal dashboard. [approved tier; and check what's in the screenshot's corners]
16. A Stack Overflow question you're about to post publicly anyway. [fine anywhere]
17. Real customer support ticket text, to draft a reply. [never as-is; strip identifiers first, then approved tier]
18. Architecture diagram of the internal platform. [approved tier only]
19. A partner's API documentation that they sent under a confidentiality clause. [never]
20. Your own CV. [fine anywhere, and a good moment to talk about personal versus company data]

## After the programme

Keep the capstone notes and the artefacts from the retros. A cohort's worth of "what the model got wrong" is specific to your codebase in a way nothing in this repo can be, and playbook guide 5 treats a stack of those examples as the signal that the rollout is ready to expand.
