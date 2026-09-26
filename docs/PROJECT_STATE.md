# ISOTOMB — Project State

## Current Stage

- Project stage: game-design brainstorming / pre-implementation.
- Initial project-governance and design-decision documentation has been prepared.
- Gameplay implementation has NOT been approved.
- No Unity project has been scaffolded.
- No gameplay code exists yet.
- No implementation plan has been approved.
- No final gameplay specification has been approved.

## Project Direction

- Working title: ISOTOMB.
- Intended storefront: Steam.
- Engine direction: Unity.
- Repository/development documentation language: English.
- Game localization target: English and Ukrainian.
- Main mechanics reference: Quasimorph.
- Setting direction: original anomalous exclusion-zone.
- Core structure: one active stalker per raid with a persistent upgradeable base and roster.

Canonical approved mechanics are maintained in `docs/DECISIONS.md`.

## Canonical Documentation

Reading order:

1. `AGENTS.md`
   - Agent workflow and project governance.
2. `docs/PROJECT_STATE.md`
   - Current project stage and next task.
3. `docs/DECISIONS.md`
   - Canonical approved design decisions, superseded decisions, proposals, and open questions.
4. Relevant future Superpowers specification
   - Only when one exists for the current task.

Repository documents override old chat assumptions or agent memory.

## Completed Work

- GitHub repository created.
- `README.md` exists.
- `AGENTS.md` has been created on the current documentation branch and is part of PR #1.
- `docs/DECISIONS.md` has been created on the current documentation branch and is part of PR #1.
- Initial mechanics/reference brainstorming has been documented in `docs/DECISIONS.md`.
- A read-only Quasimorph installation audit was previously used as reference research, but its findings do not constitute ISOTOMB implementation or architecture.

## Repository State

- Canonical branch: `main`.
- Initial documentation was prepared through PR #1.
- Agents must inspect the actual repository branch/ref and PR state at the start of every session.
- Do not rely on branch names, commit SHAs, or PR status stored in an older project-state snapshot.

## Important Approved Direction

- Persistent upgradeable base and roster.
- One stalker deployed per raid.
- Permanent stalker death.
- Persistent failed sectors.
- Loot generated once per location.
- Finite shared item population usable by player and NPCs.
- NPC inventories/resources are real and persistent.
- One armor system.
- Radiation is a core environmental hazard.
- Turn/AP combat with player phase before NPC phase.
- Movement and shooting spend AP.
- Inventory viewing, accessible looting, and medkit use are currently free/time-neutral.
- Vision, suppressors, artifacts, anomalies, factions, and balance are important design areas.

For exact wording and status, see `docs/DECISIONS.md`.

## Not Yet Decided

- Exact Unity version and technical baseline.
- Exact damage and armor formula.
- Exact AP values and action costs.
- Radiation/armor thresholds and formulas.
- NPC AI priorities and phase ordering details.
- Vision, sound, stealth, and detection details.
- Base economy and roster progression.
- Faction systems.
- Anomalies and artifacts.
- Final presentation/camera/art direction.
- First playable prototype scope.

## Current Blockers / Dependencies

Implementation should not begin until:

- the relevant design block has completed the required Superpowers brainstorming/design process;
- the owner has approved the written specification;
- the implementation plan has been written and reviewed;
- the owner has selected the execution method.

Additional open dependencies:

- exact Unity technical baseline is still open;
- first playable prototype scope has not yet been approved.

These are intentional design gates, not technical failures.

## Next Recommended Task

Continue game-design brainstorming in small steps and define the next unresolved core combat rule before creating the first playable prototype specification.

## Handoff Rule

When handing the project to another chat or agent:

- inspect the actual repository first;
- read `AGENTS.md`, `docs/PROJECT_STATE.md`, and `docs/DECISIONS.md`;
- verify branch/ref;
- do not rely only on chat memory;
- update `docs/PROJECT_STATE.md` whenever the current project stage or next task materially changes.
