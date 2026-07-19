<div align="right">
  <a href="./README.md"><img alt="切换到中文" src="https://img.shields.io/badge/Language-%E4%B8%AD%E6%96%87-dc2626?style=for-the-badge"></a>
  <a href="./README_EN.md"><img alt="English README" src="https://img.shields.io/badge/README-English-2563eb?style=for-the-badge"></a>
</div>

# AI Learning Loop · learn-anything-loop

A persistent learning-system Skill for Codex. It turns “I want to learn this topic” into an executable, measurable workflow that can resume across conversations:

> Goal diagnosis → Learning ladder → Vital 20% → Time-boxed training → AI examiner → Feynman teach-back → One-page cheat sheet → Continuous review

## What it does

- **Builds a learning ladder**: creates five levels by default and adjusts to four through seven when the topic requires it. Every level has required knowledge, a practical artifact, common mistakes, and an observable gate.
- **Supports two starting routes**: uploaded material remains the primary source and receives only targeted gap-filling; a self-chosen topic gets exactly five current, high-value, preferably free resources.
- **Finds the vital 20%**: prioritizes concepts by outcome leverage, prerequisite centrality, usage frequency, and error cost.
- **Creates a time-boxed plan**: builds a seven-day plan with 45–120 minute sessions, no more than two sessions per day, and an exact total-time match.
- **Acts as an AI examiner**: asks one important question at a time, increases difficulty from evidence, scores every answer, and reteaches only the missing knowledge.
- **Runs Feynman teach-backs**: first explains the idea for a 12-year-old, then asks the learner to teach it back, with at most two attempts.
- **Generates a one-page cheat sheet**: compresses the definition, key concepts, real examples, common mistakes, a pre-use checklist, and five self-test questions.
- **Resumes across conversations**: stores the plan, scores, weak points, and next action for every topic in local Markdown records.

## Installation

### Option 1: Clone with Git

Run in PowerShell:

```powershell
git clone https://github.com/wenqingzhang1/learn-anything-loop.git "$env:USERPROFILE\.codex\skills\learn-anything-loop"
```

### Option 2: Install manually

1. Download this repository.
2. Place the complete folder at:

```text
C:\Users\<your-username>\.codex\skills\learn-anything-loop
```

3. Open a new Codex task and invoke `$learn-anything-loop`.

## Quick start

Start a new topic:

```text
$learn-anything-loop I am a complete beginner. Help me spend 10 hours learning to analyze a CSV with Python and create charts.
```

Start from uploaded material:

```text
$learn-anything-loop Build a learning ladder from the material I uploaded and create a seven-day plan.
```

Enter a focused mode:

```text
Continue my previous SQL topic
Quiz me until I cannot answer
Use the Feynman method to check my understanding of closures
Generate a one-page cheat sheet for this stage
```

The Skill asks only for missing intake fields: topic, target project or outcome, current level, and total study hours.

## Learning records

The default configuration targets Windows. After a topic is confirmed for the first time, the Skill creates:

```text
E:\<topic-name>-LearningDocs\
├── learning-record.md
└── cheatsheet.md
```

Examples:

```text
E:\Python-LearningDocs\
E:\Linear-Algebra-LearningDocs\
```

Key rules:

- The Skill remains on the C drive; learning records are kept separately on the E drive.
- An existing same-name directory without the management marker is never overwritten; the Skill tries `-2`, `-3`, and later suffixes instead.
- Uploaded material is referenced by its original path and is not copied, moved, or modified by default.
- If the E drive is unavailable, record creation stops and the Skill asks for another location instead of silently falling back to C.
- To change the default storage location, edit the storage contract in [`references/learning-record.md`](./references/learning-record.md).

## Seven-day plan constraints

| Rule | Default |
| --- | --- |
| Formal session | 45–120 minutes |
| Sessions per day | At most 2 |
| Seven-day capacity | At most 28 hours |
| Budget below 45 minutes | Ask the learner to increase it |
| Budget above 28 hours | Extend the calendar or narrow phase one |

Every formal session includes an objective, resource slice, retrieval prompt, practice task, verifiable output, and review question. Passive watching or reading alone is not a complete session.

## Repository structure

```text
learn-anything-loop/
├── SKILL.md
├── agents/
│   └── openai.yaml
├── references/
│   ├── learning-record.md
│   └── protocols.md
├── README.md
└── README_EN.md
```

- [`SKILL.md`](./SKILL.md): automatic routing and the core learning workflow.
- [`references/protocols.md`](./references/protocols.md): ladder, resource selection, scheduling, examiner, Feynman, and cheat-sheet protocols.
- [`references/learning-record.md`](./references/learning-record.md): E-drive record structure, collision protection, and resume behavior.
- [`agents/openai.yaml`](./agents/openai.yaml): Codex interface metadata for the Skill.

## Usage notes

- Resource recommendations for self-chosen topics require live web research to avoid stale material and broken links.
- Finishing content is not treated as mastery; progression requires both assessment evidence and a practical artifact.
- Learning records remain local and are not uploaded merely because this repository is public.

## Validation status

The Skill passes the official `quick_validate.py` check. It has also been tested for:

- 6-, 10-, and 20-hour seven-day schedules;
- handling budgets above 28 hours;
- one-question-at-a-time examiner behavior;
- E-drive directory collision protection;
- bidirectional Chinese/English README navigation.

