# Learning protocols

Use these protocols to keep outputs and judgments consistent.

## Contents

1. Learning ladder
2. Resource selection
3. Vital 20 percent
4. Time-budget algorithm
5. Session and plan formats
6. Examiner rubric
7. Feynman protocol
8. One-page cheat sheet

## 1. Learning ladder

Default to five levels:

1. **Orientation**: recognize the problem space, essential vocabulary, and the shape of a correct result.
2. **Guided fundamentals**: explain and use core ideas with examples or scaffolding.
3. **Core application**: solve representative tasks without step-by-step instructions.
4. **Integrated project**: combine concepts, diagnose mistakes, and complete an end-to-end project.
5. **Independent transfer**: choose an approach, justify tradeoffs, handle novel cases, and improve the result.

Use four levels for a narrow skill. Use six or seven only when a broad field has distinct prerequisite or integration stages. Never add levels merely to appear comprehensive.

Present each level with:

| Field | Required content |
| --- | --- |
| Master | Concepts and skills that must be usable, not merely recognized |
| Produce | One observable task or artifact |
| Common mistakes | Two to five likely misconceptions or execution errors |
| Gate | A concrete assessment and artifact standard for entering the next level |

Pass a level only when the learner scores at least 4/5 on its gate, shows no critical misconception, and completes the required artifact. If evidence is mixed, remain at the level and prescribe the smallest repair task.

## 2. Resource selection

### Material-first

Inventory the supplied material before searching externally. Evaluate whether it covers prerequisites, vital concepts, practice, feedback, and the target project. Add 1-3 external resources only when a missing element blocks the outcome. State the gap beside each supplement.

### Topic-first

Research exactly five current, directly accessible resources. Prefer primary or official sources for technical facts and high-quality teaching sources for explanation and practice. Prefer free access unless the user explicitly allows paid resources.

Build a non-redundant portfolio across these roles:

1. Map or concise overview
2. Authoritative core source
3. Guided practice
4. Drill set or durable reference
5. Capstone or realistic project source

Score candidates internally on authority, fit to the goal, practice value, accessibility, currency, and redundancy. Do not show a fake mathematical ranking when evidence is qualitative.

For each selected resource provide:

| Resource | Suitable for | Difficulty | Role | Use these parts | Skip or defer | Why it earned a slot |
| --- | --- | --- | --- | --- | --- | --- |

Link directly to the source. Do not cite search-result pages. Avoid assigning irrelevant introductions, exhaustive appendices, deprecated versions, repeated explanations, or advanced branches outside the target.

## 3. Vital 20 percent

Start from the target project and work backward. Rank concepts using:

- **Outcome leverage**: directly changes whether the learner can complete the target.
- **Prerequisite centrality**: unlocks several later concepts.
- **Usage frequency**: appears repeatedly in real tasks.
- **Error cost**: misunderstanding causes costly or hard-to-diagnose failure.

Select roughly the highest-value fifth of the mapped concepts, but include a prerequisite when omitting it would make the core unusable. Label the result as “核心掌握” and explicitly place the remainder under “暂缓学习”. Do not equate 20 percent with the first 20 percent of a book or course.

For each core item state:

- Why it matters to the target
- What the learner must be able to do
- The smallest useful exercise
- The evidence that counts as mastered

## 4. Time-budget algorithm

Convert the budget to minutes and preserve the total exactly.

1. Reject a formal plan below 45 minutes and ask the user to raise the budget.
2. For 45-314 minutes, use the smallest number of sessions that keeps every session at or below 120 minutes. Schedule them across as many days as practical.
3. For 315-840 minutes, prefer seven sessions so every day has one formal session, provided each remains 45-120 minutes.
4. For 841-1680 minutes, use `ceil(total_minutes / 120)` sessions, between 8 and 14. Give each day one session before assigning any second session.
5. Distribute remaining minutes so session lengths are as even as practical and each stays 45-120 minutes. The sum must equal the input exactly.
6. Schedule no more than two sessions on any day. Separate two demanding sessions when possible.
7. Above 1680 minutes, do not force the budget into seven days. Ask whether to extend the calendar or use at most 1680 minutes as a narrower first phase.

An unassigned day is a rest or consolidation day, not a hidden study session. Optional activity must be labeled optional and must not be required for the promised outcome.

## 5. Session and plan formats

Begin with a brief outcome statement and the honest end-of-week capability. Then use:

| Day | Session | Minutes | Level and objective | Resource slice | Retrieval | Practice | Verifiable output | Review question |
| --- | --- | ---: | --- | --- | --- | --- | --- | --- |

Every session must contain actual retrieval and practice. Watching or reading alone is not a valid session. Map each session to a ladder level and at least one vital concept.

After the table include:

- Total scheduled minutes and hours
- Number of sessions per day, confirming none exceeds two
- Level gates attempted during the week
- Deferred content
- Contingency rule: when a session is missed, move it without creating a third session on another day

## 6. Examiner rubric

Ask exactly one question per turn. Prefer a question with high diagnostic value over trivia.

| Score | Evidence |
| ---: | --- |
| 0 | Cannot answer, is off-topic, or shows no usable understanding |
| 1 | Contains a major misconception that would break application |
| 2 | Recalls fragments but cannot connect or apply them |
| 3 | Mostly correct, but misses an important mechanism, boundary, or consequence |
| 4 | Correctly explains and applies the concept in a representative case |
| 5 | Transfers the idea, diagnoses failure, or justifies tradeoffs in a novel case |

After each normal answer respond in this order:

1. `得分：x/5`
2. `讲对了` — cite the useful parts of the learner’s answer
3. `错误` — list actual errors, or state “无关键错误”
4. `不完整` — list only material omissions
5. `只补这一点` — give the minimum repair explanation when needed
6. Ask the next single question

Difficulty control:

- Score 4-5: advance toward application, diagnosis, or transfer.
- Score 3: repair the omission, then ask a nearby application question.
- Score 1-2: repair the core misconception, then ask a simpler same-concept question.
- Score 0 or explicit “不知道”: declare the current knowledge boundary, explain only the missing point, and ask one narrower verification question.
- After the boundary verification: score it, record the result, summarize the boundary in one sentence, give the next learning action, and end the exam round. Do not continue escalating in that round.

Never penalize wording differences when the underlying model is correct. Never inflate a score to be encouraging.

## 7. Feynman protocol

Use this sequence:

1. Explain the concept as if speaking to a curious 12-year-old. Use a concrete analogy, causal chain, and simple example. Define unavoidable jargon immediately.
2. Ask the learner to explain it back without copying the wording.
3. Evaluate under exactly three headings: `讲对了`, `遗漏了`, `混淆了`.
4. If attempt one is sufficient, record success and stop.
5. If attempt one is insufficient, explain only the gaps and request attempt two.
6. Evaluate attempt two under the same headings. Never request attempt three.
7. If attempt two remains insufficient, provide the compact correct explanation, record the remaining weak points, and prescribe a later retrieval check.

Do not turn the teach-back into a vocabulary test. Judge causal understanding, boundaries, and the learner’s ability to produce an example.

## 8. One-page cheat sheet

Target approximately 800-1200 Chinese characters or a comparable single-A4 density in another language. Prefer compression over tiny details. Personalize common errors and self-tests from the record.

Use exactly this structure:

```markdown
# <Topic> 一页速查表

## 一句话定义

## 最重要的概念

## 三个真实例子

## 常见错误

## 使用前检查清单

## 五个快速自测问题
```

Keep derivations and the five answers out of the sheet. Store the answer key in the managed learning record. Refresh the sheet rather than appending multiple obsolete versions.
