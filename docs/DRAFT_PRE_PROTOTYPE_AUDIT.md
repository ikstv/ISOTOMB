# ISOTOMB — Pre-Prototype Audit Draft

> TEMPORARY WORKING NOTE
>
> This file is NOT a canonical design specification, NOT an implementation plan, and does NOT create approved gameplay decisions.
> It records the pre-prototype audit performed after PR #8 so that gaps and risks are not lost while the project moves toward the first playable prototype.
> Canonical design authority remains in `docs/DECISIONS.md`; current project status remains in `docs/PROJECT_STATE.md`.
> Delete this file once its useful items have been either resolved, moved into approved decisions/specifications, or consciously deferred.

## Audit Baseline

- Repository: `ikstv/ISOTOMB`
- Audited canonical branch: `main`
- Audited main SHA: `1aa723c9a67cdf782dbc0aec8adbd90f71af5032`
- Project stage: game-design brainstorming / pre-implementation
- Gameplay implementation: NOT approved
- Unity project: not scaffolded
- Gameplay code: none
- Prototype specification: not yet approved
- Implementation plan: not yet approved

## Current Strengths

The project already has unusually strong pre-production definition in several areas:

- persistent sectors and persistent world state;
- one active stalker per raid with permanent death;
- finite shared physical loot usable by player and NPCs;
- unified armor with durability, Armor Rating, repair, and condition;
- deterministic ordinary-bullet penetration starting model;
- non-duplicated penetration / absorption / overflow damage accounting;
- separate resistance, Pain, Bleeding, and local wound concepts;
- body-part-specific stopped-bullet blunt-wound consequences;
- persistent magazines with exact cartridge order and mixed compatible ammunition;
- distinct Evasion, Armor, and Cover;
- base workshops, physical crafting resources, and Tech Datapad progression;
- faction, sector-control, post-story, and world-event direction;
- strong documentation governance separating approved decisions, proposals, open questions, and superseded decisions.

The combat/armor/wound area is currently much more mature than the moment-to-moment spatial, AI, presentation, and technical layers.

## Highest-Priority Gaps Before Prototype Implementation

These are the areas most likely to block or destabilize the first playable prototype if left undefined.

### 1. Local-Wound Treatment Progression

Current next task in `docs/PROJECT_STATE.md`.

Need qualitative rules for:

- what Light, Moderate, and Severe local wounds can become during a raid;
- whether a Light wound can be cleared in-raid;
- whether Moderate / Severe can be reduced but not fully cleared;
- what treatment remains necessary at base;
- interaction with current wound severity and existing local penalties;
- distinction between wound treatment, HP healing, Bleeding control, and Pain suppression.

Do not assign final item values, AP costs, or balance numbers during this step.

### 2. First Playable Prototype Scope

The project needs a deliberately small vertical slice instead of implementing the full design.

Define:

- exact player goal for the prototype;
- one manually authored test sector or other agreed test space;
- entry and extraction conditions;
- minimum movement / turn / AP loop;
- minimum shooting loop;
- minimum armor / penetration / wound loop;
- minimum loot / inventory interaction;
- minimum enemy count and AI behavior;
- death and failure behavior;
- minimum persistence required between runs;
- explicit systems excluded from the prototype.

Existing proposal P-002 suggests validating the combat/extraction loop in a small manually authored test sector before procedural generation. It is still a PROPOSAL until owner approval.

### 3. Spatial / Grid Rules

The current design does not yet provide a complete spatial ruleset.

Need decisions on:

- grid topology;
- orthogonal and diagonal movement;
- movement legality;
- occupied-cell rules;
- collision;
- pathfinding expectations;
- doors and interactable blockers;
- line-of-sight tracing;
- line-of-fire tracing;
- corner cases around walls and diagonal gaps;
- how Cover relates to cell geometry;
- how exact grenade target cells interact with walkable / blocked cells.

This should be resolved before implementation architecture depends on assumptions.

### 4. Shooting / Accuracy Resolution

Damage after a hit is substantially more defined than how a shot becomes a hit.

Need a coherent shooting-resolution layer covering:

- accuracy;
- Evasion;
- range;
- aiming;
- weapon stability / handling;
- body-part hit selection;
- misses;
- projectile path after a miss where relevant;
- shotgun / multi-projectile behavior;
- interaction with intervening Cover;
- critical-hit behavior;
- deterministic versus random components.

Do not reopen already approved deterministic penetration rules while defining this.

### 5. Minimal Combat AI

The first prototype requires a small but complete enemy decision loop.

Need at least:

- target selection;
- movement toward / away from threats;
- attack decision;
- range management;
- simple Cover use if Cover is in prototype scope;
- reload behavior;
- response to lost target / last-known position if stealth is in scope;
- retreat / survival behavior only if needed for the prototype.

The complete faction/NPC simulation does NOT need to be solved before the prototype.

### 6. Save / Load and Persistence Boundary

This is a high technical risk because ISOTOMB combines:

- persistent sector state;
- permanent death;
- finite shared loot;
- NPC inventories/resources;
- persistent magazines;
- wounds;
- item condition;
- future destructible environment;
- future faction simulation.

Before production-scale persistence, define at least:

- what must survive save/load in the first prototype;
- when saving is allowed;
- autosave checkpoints;
- quitting during a raid;
- recovery after a crash;
- whether old-state reload behavior is intentionally restricted;
- save versioning expectations.

The prototype should test persistence architecture early rather than bolt it on later.

### 7. World-Time / Progression Clocks

The project currently mixes several future progression concepts.

Need to distinguish at least conceptually:

- combat / world tick;
- player and NPC phase resolution;
- raid-cycle progression;
- base recovery / workshop time;
- later faction research / world-event progression.

The full campaign clock can be deferred, but these categories should not be accidentally conflated in code.

### 8. Unity + Technical Baseline

Before scaffolding the Unity project, approve:

- exact Unity version;
- 2D / 3D presentation direction;
- render pipeline;
- scripting backend;
- input package;
- localization package / approach;
- test framework;
- build environment;
- save serialization direction;
- data-authoring direction;
- CI / Unity licensing approach where relevant.

Do not scaffold Unity before the required written specification and implementation plan are approved.

## Important Gaps That Can Follow the First Prototype

These matter for the full game, but they should not delay the first playable slice unless they become dependencies.

### Anomalies and Artifacts

This is currently one of the weakest-defined areas relative to the intended ISOTOMB identity.

Eventually define:

- anomaly categories;
- detection;
- interaction;
- danger / reward logic;
- artifact acquisition;
- artifact effects and side effects;
- research / progression connection.

This area is important for making ISOTOMB feel like its own game rather than only a detailed extraction-combat system.

### Character Progression

Still needs a coherent model for:

- base character attributes;
- progression;
- perks;
- training;
- roster differentiation;
- long-term value of surviving stalkers.

### Inventory UX

Mechanical concepts exist, but player-facing behavior still needs definition:

- list / slots / grid presentation;
- stack behavior;
- quick access;
- ground loot interaction;
- item comparison;
- chest-rig / backpack presentation;
- magazine inspection;
- full-inventory edge cases.

### Controls, Controller, Steam Deck, and Accessibility

Eventually define requirements for:

- keyboard and mouse;
- controller;
- key rebinding;
- readable text scale;
- non-color-only status communication;
- interface navigation;
- likely Steam Deck usability.

### Feedback and Combat Readability

The simulation is already complex enough that the player will need clear explanations.

Eventually define:

- combat log;
- hit / miss feedback;
- armor-stop feedback;
- penetration / overflow feedback;
- wound / Pain / Bleeding feedback;
- sound / VFX signaling;
- inspection / tooltip explanations.

A deterministic system can still feel random if the feedback layer does not explain outcomes.

### RNG and Reproducibility

Penetration is deterministic, while accuracy/Evasion may include randomness.

Plan for:

- seeded random generation where practical;
- reproducible combat tests;
- debug logging of resolved inputs;
- deterministic simulation tests for non-random subsystems.

### Balance / Simulation Tooling

The approved formulas would benefit from a small automated combat simulation harness later.

Useful checks include:

- large parameter sweeps for armor versus ammunition;
- discontinuity checks near penetration thresholds;
- durability / k calibration;
- resistance bounds;
- TraumaLoad threshold exploration;
- regression tests for damage accounting.

This tooling should support balancing and debugging rather than replace gameplay testing.

## Repository and Documentation Hygiene

### PROJECT_STATE Drift

`docs/PROJECT_STATE.md` still contains historical wording centered on early PRs in its Completed Work / Repository State section.

It should remain short and current rather than becoming a second historical log.

This is a documentation-maintenance issue, not a gameplay blocker.

### DECISIONS.md Size

`docs/DECISIONS.md` has become large.

For now it remains the canonical decision log. As system specifications are written, consider keeping the historical decision record while moving implementation-facing current rules into focused specs such as:

- combat;
- persistence;
- inventory;
- AI;
- prototype scope.

Do not split or reorganize the canonical file casually; do so only through a reviewed documentation task.

### README / Repository Skeleton

Before or during the transition into implementation, consider:

- expanding `README.md`;
- adding the correct Unity `.gitignore`;
- establishing build / test instructions;
- clarifying proprietary / licensing intent;
- documenting asset and source provenance expectations;
- adding CI only after the Unity baseline is known.

## Primary Architecture Risk

The largest foreseeable architecture risk is the interaction between:

- persistent sectors;
- finite physical loot;
- real NPC inventories/resources;
- persistent magazines;
- local wounds;
- item condition;
- destructible / penetrable environment;
- future faction simulation.

This combination creates a large persistent state graph.

Mitigation direction:

- prototype persistence early;
- keep gameplay state data-driven and serializable;
- separate simulation state from presentation;
- avoid storing critical state only inside scene objects;
- introduce schema/version thinking before many systems depend on save structure;
- test save/load round trips as soon as the prototype has meaningful persistent state.

These are risk-management notes, not approved implementation architecture.

## What Should NOT Block the First Prototype

Do not require final answers for all of the following before implementation starts:

- all faction identities;
- complete faction economy;
- full faction warfare simulation;
- endgame world-event generation;
- complete crafting economy;
- complete technology trees;
- procedural generation;
- all anomaly / artifact content;
- all weapon categories and items;
- final AP numbers;
- final loot tables;
- final armor / weapon balance;
- final strategic-map UX;
- full base progression.

These can remain open while the first playable loop is validated.

## Recommended Pre-Prototype Sequence

1. Finish qualitative local-wound treatment progression.
2. Decide the first playable prototype scope.
3. Approve the spatial / grid rules required by that prototype.
4. Approve the Unity technical baseline required by that prototype.
5. Define the minimum shooting / accuracy and combat-AI behavior required by the prototype.
6. Write the prototype design specification through the mandatory Superpowers workflow.
7. Owner reviews and approves the written specification.
8. Write the implementation plan.
9. Owner reviews the plan and chooses the execution method.
10. Begin implementation only after those gates are complete.

The sequence may be adjusted if a later discussion reveals a real dependency. Do not treat this draft as permission to implement.

## Deletion Condition

Delete this draft when:

- the prototype specification captures the relevant prototype requirements;
- important cross-cutting risks have been moved into durable specs or explicit tracked decisions;
- deferred items are intentionally recorded elsewhere or no longer useful.

Deletion removes the file from the current tree, but its historical Git commit may remain in repository history.
