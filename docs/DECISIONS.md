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

### D-025 — Armor Overflow Damage

Status: APPROVED DECISION

- Armor absorbs incoming damage first.
- If a hit deals more damage than the target's remaining armor can absorb, the remaining damage continues into HP during the same hit.
- One remaining point of armor must not automatically absorb an arbitrarily powerful hit.
- Exact damage formulas, armor penetration formulas, critical hits, and damage-type multipliers remain open.

Example numbers must not be treated as final balance.

### D-026 — Ballistic Performance Depends on Weapon, Caliber, and Ammunition

Status: APPROVED DECISION

Ballistic effectiveness must not depend on weapon alone.

Armor penetration and damage behavior may depend on the combination of:

- weapon;
- caliber;
- ammunition type.

Caliber is mechanically meaningful and also determines ammunition compatibility.

Examples:

- different calibers may have different baseline ballistic potential;
- ammunition of the same caliber may have different penetration/damage characteristics.

Do not create final numerical penetration values yet.

### D-027 — Ammunition Types and Weapon Wear

Status: APPROVED DECISION

- Different ammunition types of the same caliber may affect weapon wear differently.
- Ammunition choice may therefore trade ballistic performance against equipment durability.
- Exact wear multipliers and ammunition categories are not finalized.

Do not treat AP/FMJ/HP/subsonic examples discussed during brainstorming as a finalized complete ammunition list.

### D-028 — Weapon and Armor Modification

Status: APPROVED DECISION

- Weapons can be modified/upgraded.
- Armor can be modified/upgraded.
- Permanent modification is performed at the base, not during a raid.
- Available modification capability depends on base progression.
- Modifications require actual materials/resources recovered through gameplay.
- A modified item remains the same persistent item with its installed upgrades, current condition, and other state.
- If an NPC loots a modified weapon or armor item, it receives that same modified item.

Exact upgrade trees and numerical bonuses remain open.

### D-029 — Separate Weapon and Armor Workshops

Status: APPROVED DECISION

The base has two separate progression modules:

- Weapon Workshop
- Armor Workshop

They follow the same high-level principle:

- higher module progression unlocks more advanced modification capability;
- upgrades still require appropriate materials;
- upgrading the facility does not generate materials automatically.

The exact player-facing names may be refined later, but the two systems remain separate.

Do not merge them into one generic workshop without owner approval.

### D-030 — Shared and Specialized Upgrade Materials

Status: APPROVED DECISION

- Some crafting/upgrade materials may be usable across multiple systems.
- Other materials are specialized for weapon or armor work.
- Materials must have logical mechanical use rather than functioning as one universal abstract upgrade currency.

Owner example:
gunpowder-related material may be relevant to ammunition/weapon systems but not to upgrading an armor plate.

Specific final material names and recipes remain open.

### D-031 — All Raid Items Use the Shared Inventory and Weight System

Status: APPROVED DECISION

- Upgrade materials are normal physical loot.
- They do not go into a separate weightless resource inventory.
- Weapons, armor, ammunition, magazines, consumables, materials, artifacts, and ordinary loot contribute to carried weight as applicable.
- Carrying more valuable loot can therefore reduce combat mobility.

Exact inventory layout and stacking rules remain open.

### D-032 — Weight Influences Mobility and Evasion

Status: APPROVED DECISION

- Carried weight affects character mobility.
- Weight affects Evasion.
- Heavy load can make a character easier to hit.
- Equipment and carried loot therefore create a risk/reward trade-off.

Strength may increase comfortable carrying capacity slightly, but Strength must not be treated as the sole or dominant carrying-capacity system.

Exact weight thresholds and formulas remain open.

### D-033 — Backpacks, Chest Rigs, and Armor Are Distinct Equipment

Status: APPROVED DECISION

The equipment system includes distinct concepts for:

- backpack;
- chest rig / load-bearing equipment;
- armor vest/body armor.

Backpacks can have different capacities and weights.

Chest rigs provide fast-access equipment functionality rather than being just another generic storage bag.

Armor remains governed by the existing unified armor decision.

Exact equipment slot layouts and item lists remain open.

### D-034 — Magazine Reloading Uses AP, Magazine Loading Does Not

Status: APPROVED DECISION

- Replacing/swapping the weapon magazine is an AP-consuming combat action.
- The exact AP cost is not finalized.
- Loading individual cartridges into a magazine costs 0 AP.
- Removing individual cartridges from a magazine costs 0 AP.
- Loading/unloading individual cartridges does not advance world time under the current free-action principle.
- The owner explicitly considers the exact reload-cost design still open to further balancing.

### D-035 — Chest Rig Can Improve Reload Efficiency

Status: APPROVED DECISION

- A chest rig can reduce the AP cost of magazine replacement when the required magazine is stored in an appropriate fast-access location.
- The benefit should depend on actual equipment/inventory placement, not apply magically to magazines stored deep in a backpack.
- The previously discussed "-1 AP" is a design example and must NOT yet be stored as a final tuned balance value.

Exact chest-rig layouts and reload modifiers remain open.

### D-036 — Magazines Are Persistent Items

Status: APPROVED DECISION

- Magazines are separate persistent inventory items.
- Each magazine has its own ammunition state.
- Magazine capacity and compatibility matter.
- Reloading swaps actual magazine items rather than consuming an abstract global ammunition counter.
- A partially used magazine remains partially used.
- NPCs and player characters use the same magazine/item rules.

Exact magazine families and capacities remain open.

### D-037 — Mixed Ammunition in a Magazine

Status: APPROVED DECISION

- A single compatible magazine may contain multiple ammunition types of the same compatible caliber.
- The magazine stores the exact cartridge order.
- The next fired cartridge is determined by that stored order.
- Loading and unloading cartridges individually can modify that order.

Do not simplify magazines into one ammunition-type label if they contain mixed ammunition.

### D-038 — Magazine Information Knowledge

Status: APPROVED DECISION

- A magazine prepared by the player's stalker may have fully known ammunition information.
- A newly found or looted magazine does not automatically reveal the exact complete internal cartridge sequence.
- Initial knowledge may be limited.
- Inspecting/manually checking the magazine can reveal more information.
- Exact inspection rules and what information is visible at each knowledge level remain open.

Do not give the player perfect knowledge of every unknown magazine automatically.

### D-039 — Evasion Is Separate from Armor and Cover

Status: APPROVED DECISION

Three concepts must remain mechanically distinct:

- Armor: protection after a hit reaches the character.
- Evasion: affects how difficult the character is to hit.
- Cover: physical environmental protection that can intercept/block a shot.

Do not collapse them into one generic defense stat.

### D-040 — Movement Can Improve Evasion

Status: APPROVED DECISION

- Character movement during the player's phase can increase Evasion during the following NPC phase.
- A mobile character can therefore be harder to hit than a stationary character.
- Weight/load can reduce this benefit.

Exact scaling, caps, and whether the bonus uses cells moved or AP spent remain open.

### D-041 — Cover Is a Major Firefight Mechanic

Status: APPROVED DECISION

- Cover is a major tactical element of gunfights.
- Cover is separate from Evasion.
- Cover physically affects the shot path between shooter and target.
- Different cover materials may provide different ballistic protection.

Exact hit/cover calculation remains open.

### D-042 — Cover Can Be Penetrated or Destroyed

Status: APPROVED DECISION

- Cover is not universally indestructible.
- Some cover can be penetrated by sufficiently capable weapon/caliber/ammunition combinations.
- Some cover can lose durability and eventually be destroyed.
- Destroyed cover must stop providing its previous protection.
- Material type influences ballistic resistance.

Some very hard objects may resist ordinary small-arms fire and require heavy weapons/explosives to destroy.

Exact material values and destruction formulas remain open.

### D-043 — Explosive and Area Effects Use Cell Radius

Status: APPROVED DECISION

Explosive and area-effect weapons and devices use a radius measured in grid cells.

This includes concepts such as:

- grenades;
- mines;
- grenade-launcher explosives;
- incendiary devices such as Molotov cocktails.

Effect strength can depend on distance from the center/impact cell.

Exact radii and damage/falloff values are not finalized.

### D-044 — Explosive Effect Falls Off with Distance

Status: APPROVED DECISION

- Effects are strongest near the center.
- Effect strength decreases with cell distance.
- Targets outside the effect radius receive no effect from that event unless another mechanic applies.
- Cover/material interaction with blast, fragments, and fire remains to be designed in detail.

### D-045 — Thrown Grenades Land on the Selected Cell

Status: APPROVED DECISION

- Under the current design, thrown grenades land on the player-selected target cell.
- Do not add random rolling, bouncing, or scatter to normal grenade placement unless the owner later changes this decision.

Exact throwing range and AP/action rules remain open.

### D-046 — Armor Rating Degrades with Armor Durability

Status: APPROVED DECISION

- Armor has both current durability and an Armor Rating / protection-quality characteristic.
- Armor Rating is part of the same unified armor system, not a second armor bar.
- Armor Rating gradually degrades as armor durability becomes heavily damaged.
- The relationship must not be linear 1:1.
- Near-full armor should retain most of its protection quality.
- Heavily damaged armor should provide noticeably worse resistance to penetration.
- At zero effective armor durability, armor no longer provides its normal protection.
- Exact thresholds and degradation curve remain open.

### D-047 — Armor Plate Repair

Status: APPROVED DECISION

- Armor Plates restore current Armor only up to the current Max Durability.
- Armor Plates do not reduce Max Durability.
- Armor Plates do not repair the permanently lost/red Max Durability portion.
- Armor Plates do not have a negative Armor Rating penalty merely from being used.
- Using an Armor Plate costs 0 AP and does not advance world time.
- Exact repair percentage per plate remains a balance value and is not finalized.
- The previously discussed "~25%" is an example only.

### D-048 — Improvised Armor Repair

Status: APPROVED DECISION

- Improvised materials found in raids may be used to restore some current Armor.
- Improvised repair reduces the armor's Max Durability.
- The lost Max Durability is represented as a permanently damaged/red portion until fully repaired through an approved full-repair method.
- Improvised repair costs 0 AP and does not advance world time.
- Exact repair amount and Max Durability loss depend on future balancing.
- The earlier example of a metal pipe restoring "~15%" while reducing max durability from "100%" to "90%" is illustrative only.

### D-049 — Armor Repair Kit

Status: APPROVED DECISION

- Armor Repair Kit is a rare and expensive repair item.
- It is lighter and more slot-efficient than carrying many Armor Plates.
- It can restore current Armor.
- It can also restore the lost/red Max Durability portion.
- It can be used during a raid or at the base.
- It costs 0 AP and does not advance world time.
- The kit has multiple uses / repair capacity rather than being strictly single-use.

The earlier concept:

- about 3 uses;
- about 150% total repair capacity;

is a balance example only, not a final tuned value.

### D-050 — Armor Workshop Professional Repair

Status: APPROVED DECISION

- At the base, damaged armor may be left at the Armor Workshop for professional repair.
- Professional repair can restore lost/red Max Durability.
- The armor is unavailable while being repaired.
- The service costs coupons.
- Repair duration is measured in future raids, not real-world time.
- The earlier example of 2-3 raids is a balance example only.
- This service is an alternative to consuming an Armor Repair Kit.

Exact price and repair duration remain open.

### D-051 — Multiple Economic Repair Choices

Status: APPROVED DECISION

The player may face several valid repair choices:

- consume a rare Armor Repair Kit;
- use Armor Plates for ordinary field repair;
- use improvised repair at the cost of Max Durability;
- leave armor at the Armor Workshop and pay coupons;
- acquire or craft new repair resources;
- buy repair resources from traders when available.

No single option should automatically dominate all others.

### D-052 — Progressive Crafting System

Status: APPROVED DECISION

- ISOTOMB includes crafting.
- Crafting capability progresses through base development.
- Early crafting begins with crude/basic equipment.
- Higher progression unlocks increasingly advanced equipment.
- Crafting must require actual materials.
- Base progression alone must not create items or bypass resource requirements.

The example of a crude single-shot improvised pistol made from pipe-like parts and tape is thematic inspiration, not a mandatory exact item.

### D-053 — Fabrication Workshop

Status: APPROVED DECISION

- Crafting progression is handled through a dedicated base module.
- Working name: Fabrication Workshop.
- Higher Fabrication Workshop progression enables more advanced crafting capability.
- Exact final player-facing name may be refined later.

Do not merge this system into Weapon Workshop or Armor Workshop without owner approval.

### D-054 — Crafting Requires Technology + Facility + Materials

Status: APPROVED DECISION

A craftable advanced item requires:

- sufficient Fabrication Workshop capability;
- the relevant learned technology;
- the required physical materials/resources.

Facility level alone does not automatically unlock every recipe.

### D-055 — Tech Datapad

Status: APPROVED DECISION

- Advanced technologies are discovered through physical Tech Datapads found in raids.
- A Tech Datapad is a persistent physical loot item.
- A technology does not unlock merely because the player sees or picks up the datapad.
- The Tech Datapad must be successfully extracted to the base before the technology can be learned.
- If the carrying stalker dies, the Tech Datapad remains in the persistent sector as loot.
- A later stalker may recover and extract it.
- NPCs may loot/move the Tech Datapad under the same shared finite-item rules.

### D-056 — One Datapad Unlocks One Technology

Status: APPROVED DECISION

- One Tech Datapad corresponds to one specific technology/recipe unlock.
- A single datapad does not unlock an entire technology branch.
- Technology trees are built from many individual discoveries.

### D-057 — Datapad Knowledge Status

Status: APPROVED DECISION

- The UI must indicate whether the technology on a Tech Datapad is already learned by the player's base.
- A duplicate datapad remains useful even if the player has already learned that technology.
- Duplicate datapads may be sold, traded, or given to factions.
- Exact UI presentation remains open.

### D-058 — Technology Is Not Permanently Missable

Status: APPROVED DECISION

- Main technologies must not become permanently unavailable because one datapad was given away, lost, or acquired by another faction.
- Relevant Tech Datapads can appear again after the technology enters the appropriate progression/loot pool.
- Rarity may differ by technology tier.
- Giving a datapad away can delay the player, but must not permanently lock that technology out of the campaign.

### D-059 — Weapon Technology Branches

Status: APPROVED DECISION

Weapon progression includes distinct technology branches such as:

- pistols;
- shotguns;
- assault rifles;
- sniper rifles;
- electric weapons.

These are broad category directions.
Exact item lists and sub-branches remain open.

### D-060 — Late-Game Electric Weapons

Status: APPROVED DECISION

- Electric weapons are a very late-game/high-technology weapon class.
- They use specialized battery-based ammunition/energy units.
- They are extremely expensive to acquire/use.
- They are intended to have exceptionally high penetration.
- They may penetrate top-tier armor and some heavy cover/walls depending on final balance.
- They should not become ordinary mid-game equipment.

Exact stats, ammunition system, and penetration rules remain open.

### D-061 — Story Completion Does Not End the Save

Status: APPROVED DECISION

- ISOTOMB has a story with a meaningful ending.
- Completing the story does not end the save.
- The player may continue playing afterward.
- Endgame is intended to be open-ended / effectively endless if the player wishes to continue.

### D-062 — Dynamic Endgame World Events

Status: APPROVED DECISION

Endgame includes dynamic world events that can change sectors and raid conditions.

- Approved examples include anomalous surges and faction conflicts.

Exact event list and frequency remain open.

Events must create meaningful reasons to choose specific sectors, not only increase difficulty numerically.

### D-063 — Faction Power Is Dynamic

Status: APPROVED DECISION

- Faction power changes over time.
- Technology affects faction power.
- Faction strength must not be a static fixed number.

### D-064 — Factions Have Technological Specializations

Status: APPROVED DECISION

- Major factions have different technology specializations.
- Specialization provides an advantage in particular research/technology branches.
- Specialization is not an absolute restriction.
- Factions may later acquire technologies outside their specialty through research, trade, captured resources, Tech Datapads, or events.

Exact faction identities and specializations remain open.

### D-065 — Five Major Factions at Initial Design Scope

Status: APPROVED DECISION

- Initial design scope includes 5 major factions.
- More may be added later.
- All 5 begin at technology level 1.
- No faction begins with an arbitrary overall technology-level advantage.

Do not invent faction names yet unless separately approved.

### D-066 — Faction Research Is Hybrid

Status: APPROVED DECISION

Factions may progress technologically without direct player help, but progression must come from world/system causes such as:

- controlled research facilities;
- controlled industrial facilities;
- resource strength;
- research progress;
- Tech Datapads;
- trade;
- captures from other factions;
- global/story events.

Do not grant technologies simply because a hidden timer elapsed.

### D-067 — Player Can Influence Faction Technology

Status: APPROVED DECISION

- The player may sell or give Tech Datapads to factions.
- Doing so can accelerate that faction's technological progress.
- A faction that receives a technology may later field related weapons, armor, or equipment.
- Giving a datapad to a faction does not permanently remove that technology from the player's campaign; another copy may later be found.

### D-068 — Story-Gated Technology Eras

Status: APPROVED DECISION

- The world may have story/progression gates that control when very advanced technology enters the global progression pool.
- Factions cannot randomly obtain endgame technologies far earlier than intended.
- These gates exist to preserve progression and balance.

Exact eras and story gates remain open.

### D-069 — Faction Control Cannot Permanently Eliminate a Major Faction

Status: APPROVED DECISION

- A major faction may lose most external sectors.
- Each major faction retains at least one protected base/stronghold/enclave.
- A weakened faction has a path to recover over time.
- Major factions are not permanently deleted from the campaign simulation.

### D-070 — Global Map Shows Faction Sector Control

Status: APPROVED DECISION

- The global map visibly shows which faction controls each sector.
- Sector control changes are visible to the player.
- The map is part of strategic decision-making, not only a mission-selection menu.

Exact UI layout remains open.

### D-072 — Player Can Influence Sector Control Directly and Indirectly

Status: APPROVED DECISION

Player influence over faction control is mixed.

Direct influence may include:

- faction contracts;
- raids supporting a faction;
- future story missions.

Indirect influence may include:

- resource trade;
- Tech Datapads;
- technology transfer;
- economic support;
- weakening rival forces.

Exact capture rules and mission structures remain open.

### D-073 — Faction Trade Prices Depend on Relations

Status: APPROVED DECISION

- Trade prices and/or markups can depend on faction relations.
- Poor relations may produce very large markups.
- The previously discussed "up to +90%" is a balance example only, not a finalized value.
- Better relations may improve prices.

Exact price formula remains open.

### D-074 — Temporary Faction Traders

Status: APPROVED DECISION

- Factions may temporarily visit/trade with the player's base or become available for a limited number of raids.
- Pricing may depend on faction relations.
- Exact visit duration and trader rotation rules remain open.

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
- Exact Armor Rating degradation thresholds and curve as armor durability decreases.
- Armor penetration.
- Critical hits.
- Damage types.
- Exact armor overflow calculation after D-025.
- Damage-type multipliers.

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

- exact AP cost of magazine replacement;
- anti-rad use;
- equipment swapping;
- aiming;
- opening doors;
- explicit wait action.

Currently approved:

- magazine replacement consumes AP, with exact cost still open;
- loading individual cartridges into a magazine costs 0 AP;
- removing individual cartridges from a magazine costs 0 AP;
- individual cartridge loading/unloading does not advance world time under the current free-action principle.
- Armor Plate use costs 0 AP and does not advance world time.
- Improvised armor repair costs 0 AP and does not advance world time.
- Armor Repair Kit use costs 0 AP and does not advance world time.

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

- Item compatibility.
- Mechanical repair amounts for Armor Plates, Armor Repair Kits, and improvised repair.
- Interaction with Armor Rating.
- Whether any repair option has diminishing returns.
- Exact Max Durability behavior where still unresolved.

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

- Names.
- Contract types, generation, and rewards.
- Exact reputation model.
- Exact trading rules.
- Exact specialization definitions.
- Exact technology progression.
- Exact sector-control rules.

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

### OQ-017 — Carry Weight and Evasion Formula

Status: OPEN QUESTION

- Base carrying capacity.
- Comfortable load.
- Overweight thresholds.
- Strength contribution.
- Backpack contribution.
- Evasion penalties.
- Movement/AP penalties.
- Maximum overload behavior.

### OQ-018 — Weapon and Armor Upgrade Trees

Status: OPEN QUESTION

- Workshop progression levels.
- Upgrade categories.
- Prerequisites.
- Material recipes.
- Modification limits.
- Trade-offs.
- Whether modifications can be removed/replaced.
- Repair interaction with modified items.

### OQ-019 — Magazine and Reload Rules

Status: OPEN QUESTION

- Exact AP cost of magazine replacement.
- Chest-rig reload modifiers.
- Magazine compatibility.
- Magazine condition/wear if any.
- Chambered-round behavior.
- Tactical reload behavior.
- What happens to removed magazines when inventory/rig is full.
- Exact magazine inspection information.

### OQ-020 — Cover and Destruction

Status: OPEN QUESTION

- Cover material categories.
- Ballistic resistance.
- Cover durability.
- Penetration calculation.
- Residual bullet damage after penetration.
- Destruction thresholds.
- Interaction with line of sight.

### OQ-021 — Explosive Resolution

Status: OPEN QUESTION

- Exact cell radius per device.
- Damage falloff curve.
- Fragmentation.
- Blast interaction with cover/walls.
- Fire duration.
- Mine trigger rules.
- Grenade/grenade-launcher AP costs.
- Explosive damage to armor, characters, objects, and environment.

### OQ-022 — Armor Repair Economy

Status: OPEN QUESTION

- Armor Repair Kit capacity/charges where relevant to resource economy.
- Armor Workshop coupon cost.
- Armor Workshop repair duration.
- Relative rarity/availability of repair resources.
- Crafting/acquisition economics for repair resources.

### OQ-023 — Crafting Economy

Status: OPEN QUESTION

- Exact Fabrication Workshop progression.
- Craft time, if any.
- Recipe costs.
- Material categories.
- Whether crafting uses coupons in addition to materials.
- Item quality/condition on crafted items.
- Whether crafted items can have variants.

### OQ-024 — Tech Datapad Distribution

Status: OPEN QUESTION

- Exact loot-pool gating.
- Drop rarity.
- Sector/facility associations.
- Duplicate frequency.
- Whether some datapads are faction-specific.
- Exact UI markers for learned/unknown tech.

### OQ-025 — Faction Technology Simulation

Status: OPEN QUESTION

- Exact research-progress model.
- Specialization bonuses.
- Facility effects.
- Resource effects.
- Time/raid-cycle resolution.
- Technology adoption delay after learning.
- Field-equipment rollout rate.
- Candidate contributors to faction power requiring explicit approval: resources, controlled sectors, losses, research/production capability, and trade/player influence.

### OQ-026 — Faction Warfare and Sector Capture

Status: OPEN QUESTION

- Exact rules for attacking/defending sectors.
- Combat-resolution model outside player raids.
- Sector-value calculation.
- Recovery mechanics for weakened factions.
- Protected enclave behavior.
- Direct player mission effects.

### OQ-027 — Endgame World Events

Status: OPEN QUESTION

- Event generation.
- Frequency.
- Duration.
- Stacking.
- Player notification.
- Anomaly changes.
- Rewards.
- Interaction with faction control.
- Interaction with persistent sectors.
- Candidate event types such as quarantines/blockades, lost expeditions, and anomaly storms.

### OQ-028 — Global Map UX

Status: OPEN QUESTION

- Exact map layout.
- Sector icons.
- Faction colors.
- Presentation of approved faction sector control.
- Whether proposed rich strategic sector information is shown.
- Event markers.
- Information visibility.
- Filters.
- History of control changes.

## Proposals

Proposals are discussed ideas, not approved decisions.

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

### P-004 — Rich Strategic Sector Information

Status: PROPOSAL

Proposal:
The global map may additionally show:

- threat level;
- important facility/object type;
- active anomaly/world event;
- faction conflict;
- temporary trader/caravan;
- special raid opportunity.

Exact information visibility and UI remain open.

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
