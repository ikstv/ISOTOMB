# AGENTS.md

## 1. Project Overview

ISOTOMB is a turn-based extraction RPG for Steam set in an original hostile anomalous exclusion-zone setting.

Quasimorph is a primary gameplay and mechanics reference. S.T.A.L.K.E.R.-like anomalous-zone atmosphere is a reference direction. ISOTOMB must remain an original project.

Reference games may be studied to understand mechanics and design patterns. Do not copy or import source code, assets, maps, room geometry, names, dialogue, audio, or proprietary data from reference games.

## 2. Language Rules

- Repository documentation: English.
- Code identifiers and comments: English.
- Development tasks and specifications: English.
- Game localization: English and Ukrainian.
- Communication with the owner: Ukrainian.

## 3. Mandatory Superpowers Workflow

Superpowers is mandatory for this project.

Before performing work:

1. Determine whether a Superpowers skill applies.
2. Invoke the relevant skill before implementation.
3. Follow its approval gates.
4. Do not bypass brainstorming, design, or planning gates when they apply.

For new systems or architectural work, use this sequence:

1. Brainstorming/design.
2. Owner approval.
3. Written specification.
4. Owner review of the specification.
5. Implementation plan.
6. Owner review and selection of execution method.
7. Implementation.

Do not interpret discussion of an idea as permission to implement it. Do not claim Superpowers was used unless it was actually available and invoked in the execution environment.

## 4. Start-of-Session Procedure

Before changing anything, the agent must:

1. Inspect the actual repository and current branch/ref.
2. Read `AGENTS.md`.
3. Read `docs/PROJECT_STATE.md` if it exists.
4. Read `docs/DECISIONS.md` if it exists.
5. Read the specification relevant to the current task if one exists.
6. Identify missing documentation instead of inventing its contents.
7. State the actual current project stage before beginning substantial work.

Repository contents always override assumptions from an old chat or agent memory.

## 5. Decision Management

Agents must distinguish clearly between:

- APPROVED DECISION
- PROPOSAL
- OPEN QUESTION
- SUPERSEDED DECISION

Rules:

- Never convert an agent proposal into an approved decision without explicit owner approval.
- Never silently change an approved mechanic.
- When a new owner decision replaces an older one, record the supersession explicitly.
- Example numerical values used during brainstorming are not balance values unless explicitly approved.
- Do not invent answers to unresolved design questions.

## 6. Small-Step Development

Work must be split into small, reviewable tasks.

Each task should have:

- one clear goal;
- limited scope;
- explicit success criteria;
- appropriate tests or verification;
- no unrelated refactoring.

Do not implement several independent game systems in one task.

## 7. Verification Rules

Require evidence before completion claims.

Do not say `done`, `fixed`, `tested`, `committed`, `pushed`, `PR created`, or `build passes` unless that claim has been verified in the actual environment.

For repository changes, report:

- changed files;
- branch;
- commit SHA;
- test/verification performed;
- PR URL/number if a PR was created.

A chat draft is not the same as a GitHub file. A workspace file is not the same as a commit. A commit on a branch is not the same as merged `main`.

## 8. Documentation Continuity

Once these files exist, use them as follows:

- `docs/DECISIONS.md`: canonical record of approved design decisions, superseded decisions, and open questions.
- `docs/PROJECT_STATE.md`: short current-state document containing the current stage, latest completed work, blockers, current branch/ref when relevant, and exactly one recommended next task.
- Specifications: `docs/superpowers/specs/`.
- Implementation plans: use the location required by the applicable Superpowers workflow.

Do not duplicate the full design history inside `AGENTS.md`.

## 9. Reference Research Rules

When researching Quasimorph or another reference game, distinguish:

1. Documented behavior from an authoritative/public source.
2. Behavior directly reproduced in a specific game build.
3. Interpretation or hypothesis.
4. Proposed ISOTOMB behavior.

Always record the build/version when relevant.

Do not assume that a library present in another game must be used in ISOTOMB, that historical patch notes describe the current build exactly, or that an installed game directory is the original Unity project.

## 10. Owner Approval

The project owner is the final authority on game-design decisions.

If a requirement is ambiguous and materially changes gameplay or architecture:

1. Stop.
2. Describe the ambiguity.
3. Ask the owner one focused question.

Do not silently choose on the owner's behalf.

## 11. Current Restrictions

At the time `AGENTS.md` is created:

- Implementation has not been approved.
- No Unity project should be scaffolded by this task.
- No gameplay code should be written.
- Exact Unity version is not finalized.
- Camera/presentation direction is not finalized.
- Balance numbers are not finalized.
- Current work is still design/documentation.

Keep this section easy to update later.
