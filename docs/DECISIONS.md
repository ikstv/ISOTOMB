# ISOTOMB — Design Decisions

## Document Purpose

This file is the canonical record of approved ISOTOMB game-design decisions, superseded decisions, proposals, and unresolved design questions.

- Approved decisions may only be changed by explicit owner approval.
- Proposals are not approved decisions.
- Example values used during brainstorming are not final balance values.
- Superseded decisions are preserved for context but are no longer active.
- GitHub is the canonical source of this record.

## Approved Decisions

### D-001 — Product Direction

Status: APPROVED DECISION

- Working title: ISOTOMB.
- Intended storefront/platform direction: Steam.
- Unity is the chosen engine direction.
- Quasimorph is the primary mechanics reference.
- A hostile anomalous exclusion-zone atmosphere is a key setting direction.
- ISOTOMB must remain an original project.
- Reference games may be studied, but their code, assets, maps, room geometry, names, dialogue, audio, and proprietary data must not be copied into ISOTOMB.

Do not claim final trademark clearance or final Unity version.

### D-002 — Project Languages

Status: APPROVED DECISION

- Repository documentation, code naming, comments, tasks, and specifications: English.
- Game localization: English and Ukrainian.
- Communication with the owner: Ukrainian.

### D-003 — Persistent Base and Roster

Status: APPROVED DECISION

- The player has a persistent upgradeable base.
- The base supports multiple stalkers.
- Stalkers have different statistics and perks.
- Only one selected stalker deploys on a raid at a time.
- The game is not designed around directly controlling a squad during a raid.

Do not invent base room types, roster size, recruitment cost, training systems, or progression numbers.

### D-004 — Permanent Character Death

Status: APPROVED DECISION

- A deployed stalker can die permanently.
- Death does not automatically return carried equipment or loot to the base.
- The dead stalker cannot be revived through the recovery mechanic.
- A later stalker may return to the same sector and try to recover remaining equipment and loot.

### D-005 — Persistent Sector State

Status: APPROVED DECISION

- Returning to a failed sector continues the same location state.
- The sector is not reset when another stalker enters.
- Killed enemies remain dead.
- Surviving NPCs retain their real state.
- Surviving NPC state includes, where applicable:
  - current health;
  - current armor condition;
  - current ammunition;
  - current inventory;
  - used or missing consumables;
  - damaged equipment.
- Enemies do not automatically heal, repair, respawn, or replenish because the player re-enters.

### D-006 — Loot Is Generated Once Per Location

Status: APPROVED DECISION

- On first creation/start of the raid location, loot is generated once.
- This includes:
  - loot in the environment;
  - loot in containers;
  - NPC inventories.
- Re-entering the location does not regenerate loot.
- Containers do not refill automatically.
- Dead enemies do not generate a fresh reward inventory.

### D-007 — Shared Finite Item Population

Status: APPROVED DECISION

- Items are persistent game objects/resources within the raid state.
- Player and NPCs use the same finite item population.
- Items can move between:
  - player inventory;
  - NPC inventory;
  - corpses;
  - containers;
  - world positions.
- Transferring an item does not duplicate it.
- Items carried into the sector from the base are campaign resources transferred into the location, not newly generated loot.

### D-008 — NPCs Can Loot and Use Real Items

Status: APPROVED DECISION

NPCs may loot and use available items from:

- the player's corpse;
- allied NPC corpses;
- other NPC corpses;
- accessible world loot;
- accessible containers, where appropriate.

NPCs may use, where compatible:

- weapons;
- ammunition;
- armor-related resources;
- armor plates;
- repair kits;
- medkits;
- anti-radiation consumables;
- food;
- other usable items.

NPCs must not receive infinite ammunition, infinite healing, or free replenishment merely because they are NPCs.

Do not define exact AI priorities yet.

### D-009 — Item Consumption and Condition Persist

Status: APPROVED DECISION

- Fired ammunition is removed from the real available ammunition supply.
- Used consumables are actually consumed.
- Used medkits do not reappear later.
- Used repair resources do not reappear later.
- Damaged equipment stays damaged unless actually repaired.
- Looting an item does not restore its condition.
- If an NPC loots player gear and later dies, only the NPC's actual remaining inventory can be recovered.

### D-010 — One Armor System

Status: APPROVED DECISION

- Armor is one unified armor system.
- Do not split combat armor and environmental protection into two separate armor durability bars.
- Combat can reduce armor.
- Armor plates and/or repair resources may restore armor according to future approved rules.
- Exact armor formulas are not finalized.

### D-011 — Radiation as Environmental Threat

Status: APPROVED DECISION

- Radiation is a core environmental hazard.
- Radiation is part of ISOTOMB's original design direction rather than a copy of Quasimorphosis.
- If a character lacks sufficient protection in a radioactive area, radiation can reduce health as game turns advance.
- Radiation can also contribute to deterioration of exposed equipment over turns.
- A damaged NPC can potentially die from radiation before the next stalker reaches it.

Do not claim exact real-world radiation physics.

### D-012 — Temporary Radiation Mitigation

Status: APPROVED DECISION

- Anti-radiation consumables can reduce radiation effects for a limited number of turns.
- Character perks may also reduce radiation effects.
- Exact duration, strength, stacking, refresh behavior, and immunity rules are not finalized.

### D-013 — Base Preparation Pauses the Sector

Status: APPROVED DECISION

- While the player is at the base selecting a stalker or preparing equipment, the active failed sector does not continue simulating.
- Sector state resumes when the next raid/deployment begins.

### D-014 — Active Raid Advances the Whole Location

Status: APPROVED DECISION

- During a raid, the whole active location advances under the turn system.
- NPCs outside the player's current field of view still exist and can act.
- Off-screen NPCs may:
  - move;
  - loot;
  - use resources;
  - suffer radiation/environmental effects;
  - die.

Do not give off-screen NPCs omniscient knowledge of loot or player position.

### D-015 — Action Points (ОХ)

Status: APPROVED DECISION

- Characters use an Action Point system.
- The owner calls these ОХ.
- Available AP may depend on:
  - character statistics;
  - perks;
  - equipped gear;
  - artifacts.
- Positive AP modifiers may have trade-offs or negative side effects.

The following are examples only, NOT final balance values:

- +1 AP with increased shot spread.
- +1 AP with increased radiation vulnerability.

Do not store example percentages as tuned values.

### D-016 — AP-Spending Actions

Status: APPROVED DECISION

The current owner-approved principle is:

- movement spends AP;
- shooting spends AP.

Do not automatically assign AP costs to unrelated actions.

Exact movement cost, shooting cost, weapon-specific AP cost, and AP limits remain open.

### D-017 — Free and Time-Neutral Actions

Status: APPROVED DECISION

The following actions are explicitly free in terms of AP and do not advance world time:

- viewing inventory;
- viewing item descriptions;
- viewing character information;
- looting/searching an accessible body or container;
- taking accessible items;
- using a medkit.

Consumables are still consumed.

Important:

- Reaching a corpse or container through movement still costs AP.
- Free actions do not trigger extra radiation ticks merely because the UI/action was used.

Do not reintroduce an AP cost for medkits or looting unless the owner explicitly changes this decision.

### D-018 — Turn Order

Status: APPROVED DECISION

- The stalker acts first.
- The stalker may spend available AP.
- After the player phase, NPCs act.
- NPCs do not take a full normal response after every individual player movement or player shot.

Exact ordering among multiple NPCs remains open.

### D-019 — Vision as a Build Attribute

Status: APPROVED DECISION

- Vision range can be modified by character perks and build choices.
- A stalker can potentially detect an enemy before that enemy detects the stalker.
- A vision perk may extend visible cells.
- The owner used "+4 cells" as an example concept, not a finalized balance value.
- Extended vision must not imply seeing through opaque walls.

### D-020 — Awareness Is Not Exact Position Knowledge

Status: APPROVED DECISION

- An NPC can realize it is under attack without knowing the exact location of the stalker.
- Exact player position requires justified information such as visual detection or another approved information source.
- A suppressed attack does not automatically reveal the player's exact coordinates to all enemies.
- NPC active reactions occur during the NPC phase, not as free mid-player-phase movement or counterfire.

Sound propagation, last-known position, communication, and search logic remain open.

### D-021 — Suppressed Long-Range Playstyle

Status: APPROVED DECISION

- Long-range weapons, extended vision, and suppressors may combine to create a stealth/sniper playstyle.
- A stalker may be able to attack an enemy before that enemy can visually detect the stalker.
- If the enemy lacks justified information about the shooter's position, it must not receive perfect knowledge of that position.

Do not encode exact range or accuracy numbers yet.

### D-022 — Powerful Weapons Can One-Shot Weak Targets

Status: APPROVED DECISION

- A sufficiently powerful late-progression weapon may kill a weak early-progression enemy in one hit.
- This is not a level-based automatic instant-kill rule.
- Exact damage, armor penetration, critical-hit, and armor-to-health transfer formulas are not finalized.

### D-023 — Anomalies, Artifacts, and Factions

Status: APPROVED DECISION

The game will include:

- anomalies;
- artifacts;
- factions;
- base progression.

These systems are intended to interact with:

- character builds;
- raid risk;
- equipment;
- resource decisions;
- progression.

Exact content, names, effects, faction structure, and implementation scope are not finalized.

### D-024 — Balance Is a Core Design Priority

Status: APPROVED DECISION

- Balance is a major project priority.
- Balance must be evaluated across interacting systems, not only individual numbers.
- Strong weapons may legitimately outperform weaker weapons.
- Balance should consider:
  - AP thresholds;
  - weapon effectiveness;
  - armor;
  - ammunition;
  - consumables;
  - visibility;
  - radiation;
  - perks;
  - artifacts;
  - economy;
  - recovery after failed raids.
- Automated correctness tests and gameplay balance testing are separate concerns.

Do not declare a mechanic balanced solely because its formula is mathematically correct.

## Superseded Decisions

### S-001 — One Action Equals One Turn

Status: SUPERSEDED DECISION

Earlier idea:

- one generic action = one turn.

Superseded by:

- variable AP budgets;
- player phase followed by NPC phase.

### S-002 — Medkits and Looting Cost AP

Status: SUPERSEDED DECISION

Earlier proposal:

- medkits and looting consume turns/AP.

Superseded by D-017:

- medkit use and looting are free and time-neutral.

### S-003 — Separate Armor and Environmental Suit Durability

Status: SUPERSEDED DECISION

Earlier proposal:

- separate combat armor durability and environmental suit durability.

Superseded by D-010:

- one unified armor system.

### S-004 — Automatic Enemy Recovery Between Attempts

Status: SUPERSEDED DECISION

Earlier proposal:

- surviving enemies may automatically recover between raids.

Superseded by D-005:

- actual state persists;
- healing and repair require real available resources/effects.

### S-005 — Loot and Enemy Regeneration on Re-entry

Status: SUPERSEDED DECISION

Earlier idea:

- re-entering could refresh enemies or loot.

Superseded by:

- persistent sector state;
- one-time loot generation;
- no automatic enemy respawn.

### S-006 — Real-Time Hours/Days as Main Degradation Clock

Status: SUPERSEDED DECISION

Earlier proposal:

- use real-time-like hours/days for lost-item degradation.

Superseded by:

- turn-based progression during active raids;
- sector paused while preparing at base.

### S-007 — Lost Gear Guaranteed to Remain on Player Corpse

Status: SUPERSEDED DECISION

Earlier assumption:

- lost player gear remains available at the original corpse.

Superseded by:

- NPCs may loot, use, move, consume, or later lose those items.

### S-008 — Attacked Enemy Automatically Knows Shooter Position

Status: SUPERSEDED DECISION

Earlier assumption:

- being attacked reveals the shooter's exact position.

Superseded by D-020:

- awareness and exact position knowledge are separate.

## Open Questions

Open questions are NOT approved decisions and must not be answered by the agent.

### OQ-001 — Exact Damage Formula

Status: OPEN QUESTION

- How damage interacts with armor and HP.
- Whether excess damage passes through destroyed armor in the same hit.
- Armor penetration.
- Critical hits.
- Damage types.

### OQ-002 — Exact AP Model

Status: OPEN QUESTION

- Base AP amount.
- Maximum AP.
- Movement AP cost.
- Shot AP cost.
- Weapon-specific AP costs.
- AP modifiers.
- Stacking.
- Carryover of unused AP.
- Recalculation when equipping/unequipping AP-changing gear.

### OQ-003 — Other Action Costs

Status: OPEN QUESTION

Need owner approval for exact treatment of:

- reloading;
- armor repair;
- armor plate use;
- anti-rad use;
- equipment swapping;
- aiming;
- opening doors;
- explicit wait action.

Do not silently assign AP costs.

### OQ-004 — Radiation and Armor Threshold

Status: OPEN QUESTION

- Does radiation damage HP only at zero armor?
- Does damaged armor give partial protection?
- How location radiation intensity affects damage?
- How anti-rad and perks combine?

### OQ-005 — World Tick Resolution

Status: OPEN QUESTION

- Exact point when radiation/environmental effects resolve.
- Exact point when item deterioration resolves.
- How player phase and NPC phases form one shared world round.
- Effects must not accidentally scale with number of NPCs.

### OQ-006 — NPC Phase Ordering

Status: OPEN QUESTION

- Order between multiple NPCs.
- Simultaneous vs sequential resolution.
- What happens when NPCs kill each other or loot the same item.
- Early end-of-phase behavior.

### OQ-007 — NPC Loot/Survival AI

Status: OPEN QUESTION

- How NPCs decide what to loot.
- How they choose weapons.
- When they use medkits.
- When they use anti-rad.
- When they repair armor.
- When they retreat.
- How they know that loot exists.

NPCs must not be omniscient.

### OQ-008 — Vision, Sound, and Detection

Status: OPEN QUESTION

- Base vision range.
- Lighting effects.
- Obstacles.
- Weapon range.
- Suppressor behavior.
- Sound propagation.
- Last-known-position memory.
- NPC communication.
- Search behavior.

### OQ-009 — Exact Armor Repair Rules

Status: OPEN QUESTION

- Difference between armor plates and repair kits.
- Repair amount.
- Limits.
- Item compatibility.
- Whether repair has condition loss or diminishing returns.

### OQ-010 — Item Deterioration

Status: OPEN QUESTION

- Exact deterioration formula.
- Which items deteriorate.
- Radiation dependence.
- Minimum condition.
- Destroyed-item behavior.

### OQ-011 — Base and Roster Systems

Status: OPEN QUESTION

- Starting roster.
- Recruitment.
- Training.
- Base upgrade tree.
- Recovery after multiple deaths.
- Economy and upkeep.

### OQ-012 — Factions

Status: OPEN QUESTION

- Faction count.
- Names.
- Reputation.
- Contracts.
- Trading.
- Territory control, if any.

### OQ-013 — Anomalies and Artifacts

Status: OPEN QUESTION

- Types.
- Detection.
- Interaction.
- Artifact acquisition.
- Artifact effects.
- Side effects.
- Research.
- Balance constraints.

### OQ-014 — Presentation

Status: OPEN QUESTION

- Final camera.
- 2D vs other presentation details.
- Art direction.
- Controls.
- Exact supported desktop OS targets.

Do not state that 2D top-down is finalized.

### OQ-015 — Unity Technical Baseline

Status: OPEN QUESTION

- Exact Unity version.
- Render pipeline.
- Scripting backend.
- Package list.
- Localization implementation.
- Build/test environment.
- Unity activation/licensing for CI.

### OQ-016 — First Prototype Scope

Status: OPEN QUESTION

- Exact content of the first playable prototype.
- Success criteria.
- Test location.
- Number of NPCs.
- Number of weapons/items.
- Which mechanics are included initially.

## Proposals

Proposals are discussed ideas, not approved decisions.

### P-001 — Excess Armor Damage Transfers to HP

Status: PROPOSAL

Proposal:
If an attack exceeds remaining armor durability, excess damage may transfer to HP in the same hit.

This is NOT approved yet.

### P-002 — Manual Test Sector Before Procedural Generation

Status: PROPOSAL

Proposal:
Validate the combat/extraction loop in a small manually authored test sector before building procedural generation.

This is NOT approved yet.

### P-003 — Room-Graph + Prefab Library Level Generation

Status: PROPOSAL

Proposal:
Later investigate a system using:

- mission graph;
- authored room library;
- configurable content placement.

This was inspired by reference research but is NOT an approved ISOTOMB architecture.

## Reference Notes

- Quasimorph is a mechanics reference.
- Reference findings must distinguish:
  1. public/documented behavior;
  2. directly reproduced behavior;
  3. hypothesis;
  4. proposed ISOTOMB behavior.
- Historical patch notes are not guaranteed to describe the current build.
- Installed libraries do not automatically become ISOTOMB dependencies.
- Do not copy private paths, user account data, or authorization details into this file.

## Document Maintenance Rules

- Add a new decision only after explicit owner approval.
- Never silently rewrite an approved decision.
- If a decision changes, mark the old one SUPERSEDED and add the replacement.
- Keep open questions separate.
- Keep balance examples marked as examples until explicitly approved.
- Update this file as part of the same reviewed task/PR when an approved design decision changes.
- Do not treat this file as permission to implement gameplay.
