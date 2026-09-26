# ISOTOMB — Project State

## Current Stage

- Project stage: game-design brainstorming / pre-implementation.
- Project-governance documentation is established on `main`.
- A substantial first block of gameplay-design decisions has been reviewed and merged.
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
   - Current project stage and exactly one recommended next task.
3. `docs/DECISIONS.md`
   - Canonical approved design decisions, superseded decisions, proposals, and open questions.
4. Relevant future Superpowers specification
   - Only when one exists for the current task.

Repository documents override old chat assumptions or agent memory.

## Completed Work

- GitHub repository created.
- `README.md` exists.
- PR #1 was merged into `main` and established:
  - `AGENTS.md`;
  - `docs/DECISIONS.md`;
  - `docs/PROJECT_STATE.md`.
- PR #2 was squash-merged into `main` and expanded the canonical design record through the current combat/equipment/crafting/faction/endgame decision block.
- The merged design block covers, at a high level:
  - armor overflow and ballistic dependencies;
  - ammunition, weapon wear, persistent magazines, mixed ammunition, and magazine knowledge;
  - carried weight, backpacks, chest rigs, Evasion, Cover, and destructible/penetrable cover;
  - explosive radius/falloff and deterministic grenade target-cell placement;
  - Armor Rating degradation and multiple armor-repair methods;
  - Weapon Workshop, Armor Workshop, and Fabrication Workshop directions;
  - crafting requirements and Tech Datapad progression;
  - story completion with optional endless post-story play;
  - five major factions, technological specializations, hybrid research, persistent faction enclaves, visible sector control, faction trading, and temporary traders.
- A read-only Quasimorph installation audit was previously used as reference research, but its findings do not constitute ISOTOMB implementation or architecture.

For exact approved wording, proposal status, and open questions, use `docs/DECISIONS.md`.

## Repository State

- Canonical branch: `main`.
- PR #1 and PR #2 are merged.
- The current work remains design/documentation only.
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
- One unified armor system with Armor Durability and Armor Rating behavior.
- Radiation is a core environmental hazard.
- Turn/AP combat with player phase before NPC phase.
- Movement and shooting spend AP.
- Inventory viewing, accessible looting, medkit use, cartridge loading/unloading, Armor Plate use, improvised armor repair, and Armor Repair Kit use are currently free/time-neutral where specified by `docs/DECISIONS.md`.
- Ballistic behavior depends on weapon, caliber, and ammunition.
- Magazines are persistent items and may contain mixed compatible ammunition in exact cartridge order.
- Evasion, Armor, and Cover are mechanically distinct.
- Carried weight affects mobility/Evasion.
- Cover may be penetrated or destroyed depending on material and attack capability.
- Explosive/area effects use grid-cell radius and distance falloff.
- Weapon and armor modification is base-based and requires materials.
- Crafting progresses through a Fabrication Workshop and requires facility capability, learned technology, and materials.
- Tech Datapads are physical raid loot; one datapad unlocks one technology after successful extraction to base.
- Main technologies are not permanently missable.
- Story completion does not end the save; post-story play may continue indefinitely.
- Five major factions are in the initial design scope and all begin at technology level 1.
- Factions have different technological specializations and can progress through world/system causes.
- The player can influence faction technology and sector control directly and indirectly.
- Major factions retain at least one protected base/stronghold/enclave and cannot be permanently removed from the campaign simulation.
- The global map visibly shows faction sector control.
- Faction trade prices can depend on relations.
- Temporary faction traders are approved.
- Rich additional strategic sector information remains a proposal, not an approved decision.
- Global HP remains shared while body-part hit locations carry localized wounds.
- Body-part coverage remains within the unified armor system.
- Armor Rating and damage-type resistances are distinct systems.
- Ordinary bullet hits now have four approved starting-model choices in `docs/DECISIONS.md`: deterministic penetration fraction, proportional armor wear, fully restored-maximum condition normalization, and nonlinear Armor Rating degradation.
- These formulas are approved starting models for balance evaluation, not validated final gameplay balance; they do not replace the unified armor system or shared global HP pool.
- Resistances use numeric percentages and may be positive, zero, or negative, with bounded caps.
- Blunt Trauma, Bleeding, and Pain are approved design directions.
- Persistent wounds require time/resources for base recovery.
- Food, water, alcohol, energy drinks, and temporary raid states are approved survival-consumable directions.
- Medical items are specialized by purpose, including bleeding control, HP restoration, wound treatment, pain suppression, and radiation management.
- Ordinary bullet hit resolution has an approved conceptual order: pre-hit inputs, potential character hit, cover along the path, armor/penetration, health-damage or stopped-hit trauma branch, then consequences.
- Ordinary bullet penetration is deterministic and uses the pre-hit defense state.
- Ordinary bullet damage uses a shared damage budget so penetration-derived HP damage and overflow are not duplicated.
- Ordinary bullet resistance applies once after armor distribution.
- Blunt Trauma is an alternative fully stopped-hit branch, not extra damage on top of penetration or armor-breaking overflow.
- Stopped-bullet Blunt Trauma causes no direct global HP damage or automatic Bleeding; TraumaLoad drives Pain and local wound severity, with no hidden sub-threshold accumulator.
- Stopped-bullet blunt wounds have qualitative body-part-specific functional effects: Head affects Vision/aiming, Torso affects general physical performance, Arms affect arm-dependent weapons/actions, and Legs affect mobility/movement-related Evasion.
- Stopped-bullet blunt-wound severity scales effect strength without automatic hard-disable; local wound effects coexist with Pain, Pain suppression does not remove local wound penalties, and current wound severity controls the current functional penalty.
- Bilateral and multiple stopped-bullet blunt-wound effects may combine, with exact stacking still open.

For exact wording and status, see `docs/DECISIONS.md`.

## Not Yet Decided

Major unresolved areas include:

- Exact Unity version and technical baseline.
- Exact damage calibration, `k`, rounding, coverage aggregation, critical-hit, and non-bullet damage-type formulas.
- Exact numerical body-part blunt-wound penalties, bilateral/same-function stacking, TraumaLoad thresholds, Pain coefficient p, BaseTraumaReduction balance values, treatment progression, and remaining resistance interaction.
- Exact AP values and remaining action costs.
- Radiation/armor thresholds and formulas.
- NPC AI priorities and phase ordering details.
- Vision, sound, stealth, detection, and search behavior.
- Exact armor-repair amounts, compatibility, Max Durability behavior, and repair economy.
- Exact carrying-capacity/Evasion formulas.
- Exact weapon/armor upgrade trees and crafting economy.
- Exact magazine/reload edge cases and inspection rules.
- Exact cover penetration/destruction formulas.
- Exact explosive resolution.
- Exact Tech Datapad distribution and technology rollout rates.
- Exact faction identities, reputation, contracts, trading rules, research simulation, and sector-capture rules.
- Exact endgame world-event generation and behavior.
- Exact base recovery duration/costs, nutrition model, survival-consumable effects, and medical-item rules.
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

Continue Superpowers brainstorming for OQ-029 by defining qualitative local-wound treatment progression during a raid, including how treatment may reduce or clear Light, Moderate, and Severe wounds and what must remain for base recovery, without assigning final item values, AP costs, or balance numbers.

## Handoff Rule

When handing the project to another chat or agent:

- inspect the actual repository first;
- read `AGENTS.md`, `docs/PROJECT_STATE.md`, and `docs/DECISIONS.md`;
- verify branch/ref;
- do not rely only on chat memory;
- update `docs/PROJECT_STATE.md` whenever the current project stage or next task materially changes.
