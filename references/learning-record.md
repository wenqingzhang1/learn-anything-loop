# Persistent learning records

Follow this specification whenever locating, creating, reading, or updating topic records.

## Contents

1. Storage contract
2. Topic name normalization
3. Discovery and collision handling
4. Initial files
5. Update rules
6. Resume behavior
7. Failure handling

## 1. Storage contract

Keep the Skill itself on C drive. Keep topic records directly under E drive using:

```text
E:\<topic-name>-LearningDocs\
```

Examples:

```text
E:\Python-LearningDocs\
E:\线性代数-LearningDocs\
```

Create the directory only after the topic is confirmed and the user actually starts that topic. Do not create a global `LearningHub` directory. Do not create a topic directory merely to answer a question about how the Skill works.

Every managed topic directory must contain:

- `learning-record.md`
- `cheatsheet.md`

Record source paths or URLs in `learning-record.md`. Do not copy uploaded source files unless the user explicitly requests copying.

## 2. Topic name normalization

Keep the human-readable Chinese or English subject name. Build a safe folder stem as follows:

1. Trim leading and trailing whitespace.
2. Replace Windows-invalid characters `< > : " / \ | ? *` and control characters with `-`.
3. Collapse repeated whitespace and repeated hyphens.
4. Remove trailing periods, spaces, and hyphens.
5. Limit the readable stem to 80 characters without cutting a surrogate pair.
6. If the result is empty, ask for a usable topic name.
7. If it equals a reserved Windows device name such as `CON`, `PRN`, `AUX`, `NUL`, `COM1`-`COM9`, or `LPT1`-`LPT9`, append `-Topic`.

Create a comparison key by Unicode-normalizing the topic, trimming it, collapsing whitespace, and comparing case-insensitively. Store both the display topic and comparison key in the record.

## 3. Discovery and collision handling

Before creating anything:

1. Confirm `E:\` exists and is accessible.
2. Inspect only direct child directories matching `*-LearningDocs*`.
3. Treat a directory as managed only when `learning-record.md` exists and its frontmatter contains `managed_by: learn-anything-loop`.
4. Compare the stored `topic_key` with the requested topic key.

Then act as follows:

- Exactly one managed match: reuse it, even when its directory ends in `-2` or another collision suffix.
- More than one managed match: show the topic names and paths and ask the user to choose.
- No managed match and the preferred path is absent: create `E:\<topic-name>-LearningDocs\`.
- No managed match and the preferred path exists but is unrecognized: leave it untouched and try `-2`, then `-3`, continuing until an unused path is found.

Never adopt or overwrite an unrecognized existing folder. Never delete collision directories.

## 4. Initial files

Initialize `learning-record.md` with this structure:

```markdown
---
managed_by: learn-anything-loop
record_version: 1
topic: "<display topic>"
topic_key: "<comparison key>"
status: active
created_at: "<ISO-8601 with timezone>"
updated_at: "<ISO-8601 with timezone>"
current_level: 1
target_hours: <number or null>
completed_minutes: 0
---

# <Topic> 学习档案

## 学习目标

## 当前状态

## 资料来源

## 学习阶梯

## 核心 20%

## 学习计划

## 训练日志

## 掌握度

| 概念 | 最近得分 | 证据 | 状态 | 下次复习 |
| --- | ---: | --- | --- | --- |

## 测评历史

## 费曼复述

## 速查表自测答案

## 薄弱点

## 下一步动作
```

Initialize `cheatsheet.md` with:

```markdown
---
managed_by: learn-anything-loop
record_version: 1
topic: "<display topic>"
updated_at: "<ISO-8601 with timezone>"
status: pending
---

# <Topic> 一页速查表

> 尚未生成。完成首个学习阶段或提出“生成速查表”后更新。
```

Quote frontmatter strings that may contain punctuation. Use the user’s local timezone for timestamps.

## 5. Update rules

- Read the current file before every update.
- Preserve user-authored notes, unknown fields, and prior history.
- Update `updated_at` after every meaningful change.
- Append dated entries to training, exam, and Feynman history instead of replacing earlier evidence.
- Replace the active ladder or plan only when explicitly revised; summarize the reason for revision.
- Update concept mastery from demonstrated evidence, not content consumption.
- Count `completed_minutes` only after the user confirms a session or exercise was completed.
- Keep planned time separate from completed time.
- Store exam prompts, concise answer evidence, scores, weak points, and the next check.
- Store the cheat-sheet self-test answer key in `learning-record.md`, never in `cheatsheet.md`.
- Refresh `cheatsheet.md` in place; do not create dated duplicate sheets unless requested.

Use atomic or patch-style edits where available. Do not rewrite unrelated user content.

## 6. Resume behavior

For “继续学习 <topic>”:

1. Find managed records by stored topic key, not folder spelling alone.
2. If exactly one match exists, read its goal, current level, weak points, latest evidence, and next action.
3. Briefly report the restored position and continue with the recorded next action.

For “继续学习” without a topic:

- If exactly one managed record exists, resume it.
- If several exist, show concise choices with topic, current level, last update, and next action; ask the user to select one.
- If none exist, start normal intake.

If the user changes the goal for an existing topic, retain history, record the new goal with a date, and rebuild only the affected ladder and plan sections.

## 7. Failure handling

- If E drive is absent, inaccessible, read-only, or full, stop record creation and ask the user for another location. Do not silently fall back to C drive.
- If a managed record is malformed, preserve it, report the problem, and ask before reconstructing fields that could alter meaning.
- If only `cheatsheet.md` is missing, recreate it from the record.
- If source files moved, keep the old reference, mark it unavailable, and ask for the new location when the source is needed.
- If a write fails, keep the learning interaction result in the response and clearly state that persistence did not succeed.
