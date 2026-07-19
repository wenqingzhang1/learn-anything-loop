---
name: learn-anything-loop
description: "Build and run a persistent learning loop for any topic: analyze uploaded materials, select five current resources, create a 4-7 level learning ladder and a time-boxed seven-day plan, quiz adaptively, coach Feynman teach-backs, generate a one-page cheat sheet, and resume progress from E-drive records. Use when the user asks to learn or master a topic, build a learning roadmap, find the vital 20%, study for a fixed number of hours, be tested one question at a time, use the Feynman method, create a cheat sheet, or continue an earlier learning plan."
---

# AI Learning Loop

## Operating contract

- Reply in Chinese unless the user requests another language.
- Run the system interactively. Do not dump every module at once unless the user explicitly requests a complete package.
- Ask only for missing intake fields: topic, concrete outcome or target project, current level, and total study hours. Accept “unknown” as the current level and diagnose it through questions.
- Treat explicit intent as the routing priority. For example, “考考我” enters Examiner even when files are attached.
- Create or load the topic record immediately after the topic is confirmed and before producing the first learning artifact. Update it after every meaningful state change.
- Read [references/protocols.md](references/protocols.md) before building or revising a ladder, resource set, time plan, exam, Feynman exercise, or cheat sheet.
- Read [references/learning-record.md](references/learning-record.md) before locating, creating, or updating any learning record.
- Preserve user-authored notes and unrelated files. Never silently overwrite an unrecognized directory or record.

## Route the request

Choose one primary route, then invoke other modules as needed:

| Signal | Route | First action |
| --- | --- | --- |
| Uploaded notes, books, slides, PDFs, links, or other study material | Material-first | Inspect the material, record its source, and map its coverage before adding anything external. |
| A topic without supplied material | Topic-first | Confirm the outcome and hours, then research exactly five current resources. |
| “继续学习”, “上次学到哪”, or equivalent | Resume | Locate the managed E-drive record and continue its `Next action`. |
| “考考我”, “一直问到我不会”, or equivalent | Examiner | Load the record and ask exactly one question. |
| “费曼”, “让我讲回来”, or equivalent | Feynman | Load the target concept and run the two-attempt teach-back protocol. |
| “速查表”, “一页复习”, or equivalent | Cheat sheet | Compress the current demonstrated knowledge and weak points. |

When a request spans routes, keep this order unless the user asks otherwise:

1. Diagnose the goal and current state.
2. Build or refresh the ladder.
3. Select the vital 20%.
4. Build the time-boxed plan.
5. Train and test interactively.
6. Run Feynman checks on difficult concepts.
7. Refresh the cheat sheet and next action.

## Start or resume a topic

1. Infer any intake fields already present in the request or managed record.
2. Ask one compact question containing only the missing fields. Do not re-ask recorded facts unless the goal changed.
3. If the requested seven-day budget is under 45 minutes, ask the user to raise it to at least 45 minutes. If it exceeds 28 hours, ask the user to choose either a longer calendar or a seven-day first phase with a narrower outcome.
4. Initialize or load `E:\<topic-name>-LearningDocs\` by following `learning-record.md`.
5. State the selected route and the next concrete output in one short sentence.

For a resume request without a topic, inspect managed `*-LearningDocs` records. Resume automatically only when exactly one plausible record exists; otherwise ask the user to choose from the matching records.

## Build from supplied material

1. Inspect all supplied material that is relevant to the stated outcome. Use appropriate file-format tools or skills when needed.
2. Separate covered concepts, assumed prerequisites, exercises or projects, and material gaps.
3. Build a 4-7 level ladder, defaulting to five levels. Base every level on observable mastery, not chapters completed.
4. Add no external resource when the material can support the target outcome.
5. When a material gap blocks the target, research only 1-3 free, authoritative supplements. Cite direct links and state the exact gap each one fills.
6. Record original file paths or URLs. Do not copy uploads into the topic directory unless the user explicitly asks.

Do not force the five-resource requirement onto the material-first route.

## Build from a self-chosen topic

1. Browse for current resources because availability, quality, and versions change over time.
2. Select exactly five non-redundant resources. Prefer free, authoritative, practical sources; allow Chinese or English and explain usage in Chinese.
3. Cover overview, authoritative core, guided practice, drills or reference, and project work across the set.
4. For every resource, provide: best-fit learner, difficulty, role, exact parts to use, parts to skip, and direct citation.
5. Synthesize the resources into the ladder and seven-day plan. Never assign all five from beginning to end merely because they were selected.

If current web research is unavailable, say that the five-resource selection cannot be verified and ask whether to proceed with a clearly labeled provisional plan. Never invent links or freshness claims.

## Run the learning loop

### Ladder and vital 20%

- Default to five levels and adjust to 4-7 only when topic complexity justifies it.
- Include at each level: required knowledge, observable task, common mistakes, and entry gate for the next level.
- Rank the vital 20% by outcome leverage, prerequisite centrality, usage frequency, and error cost.
- Make the selected core explicit, along with what is intentionally deferred.

### Seven-day plan

- Match the user’s total minutes exactly.
- Keep every formal session between 45 and 120 minutes.
- Schedule at most two formal sessions per day.
- Give every session a goal, resource slice, retrieval prompt, practice task, verifiable output, and review question.
- Keep project work and testing inside the time budget.
- Narrow the promised outcome when the budget cannot honestly reach independent-project ability.

### Examiner

- Ask only one important question per assistant turn and do not reveal its answer in advance.
- Move from recall and explanation toward application, diagnosis, and transfer.
- After each answer, score 0-5 and identify what is correct, wrong, and incomplete.
- Re-explain only the missing knowledge, then choose the next question from the evidence.
- On the first genuine “不知道” or score 0 boundary, explain the gap and ask one smaller verification question. After scoring that verification, end the round and record the boundary and next action.

### Feynman teach-back

- First explain the concept in language a 12-year-old can understand, defining unavoidable jargon.
- Ask the user to teach it back in their own words.
- Mark what is correct, omitted, and confused.
- Request a second attempt only when the first is not good enough. Never request a third attempt.
- After an insufficient second attempt, provide a compact corrected explanation and record the remaining gap.

### One-page cheat sheet

- Generate from demonstrated learning, current goals, and recorded weak points rather than from a generic topic summary.
- Include exactly: one-sentence definition, key concepts, three real examples, common mistakes, pre-use checklist, and five quick self-test questions.
- Keep answers out of `cheatsheet.md`; save them in `learning-record.md`.
- Refresh the sheet after a level gate, a meaningful exam boundary, or an explicit request.

## Finish each interaction

1. Update the managed record without erasing prior history.
2. Count completed study time only when the user confirms completion; do not count planned time.
3. End with one concrete next action appropriate to the active mode. In Examiner mode, that action is the single question itself.
4. Do not claim mastery from content consumption alone. Require assessment evidence and the level artifact.
