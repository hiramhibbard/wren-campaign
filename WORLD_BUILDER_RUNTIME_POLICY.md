# Wren World Builder Runtime Policy — v1

This policy defines how the AD&D 2e *World Builder's Guidebook* is used to generate new campaign material for Wren without overbuilding the world, contradicting established canon, or turning random tables into arbitrary truth.

## Source role and authority

`World Builders Guidebook.pdf` (TSR 9532, AD&D 2e) is an active **DM world-generation procedure source** for original/unresolved campaign space.

It does not override:
- established Wren campaign facts;
- an active published campaign-setting source;
- an active published adventure/site source;
- governing PHB/DMG/monster mechanics;
- explicit campaign rulings.

Use it to help answer questions the world genuinely needs answered and that remain unresolved.

## Core generation chain

Use:

`current causal need -> established constraints -> choose appropriate world-building approach -> retrieve only relevant Guidebook domain/table -> specialist source consultation if implicated -> constrained DM choice or genuine secret roll -> consistency check -> minimum necessary truth -> runtime/persistence`

Never begin with a random table and search for somewhere to force the result into the campaign.

## Default Wren design approach

Wren's current campaign uses the **microscopic approach** as the default: begin with the known local campaign area, settlements, sites, people, monsters, and adventures, then expand outward only as play makes farther geography/society/history consequential.

This follows the Guidebook's dungeon/town-outward method and matches Wren's discovery-through-play campaign structure.

Other Guidebook approaches are routing modes, not competing campaign settings:
- **sociological** — use when a culture, kingdom, institution, or political relationship is the main unresolved problem;
- **character-based** — use when a consequential PC/NPC background, homeland, family, order, or prime mover requires surrounding world structure;
- **situation-based** — use when an unusual magical, ecological, political, military, monster, or other world condition is the dominant causal constraint;
- **historical** — use when established present facts depend on a past event whose minimum truth must now be resolved;
- **macroscopic** — use only when continent/planet-scale conditions become genuinely consequential; do not generate them merely for completeness;
- **literary/published-world interpretation** — when a published setting becomes active, use its setting authority first and the Guidebook only to fill compatible unresolved local detail.

## Progressive detail rule

The Guidebook explicitly supports using only as much detail as the campaign needs. Wren adopts that as a hard runtime rule.

Generate at the smallest causal scale that can answer the current question:
- room/site before entire province;
- village institution before national government;
- route segment before full regional road map;
- local population/ecology before continent-wide demographics;
- local historical event before complete chronology;
- current settlement function before exact population census.

Do not generate unused world detail just because a Guidebook table exists.

## Domain routing

Use the Guidebook chapters selectively.

### Approaches
Use when deciding *how* to resolve a new world-building problem.

### Worlds / planetology
Use only when planetary shape, seas, tectonics, global climate, seasons, or equivalent large-scale facts become consequential and are not already governed by a setting source.

### Continents / geography
Use when coastlines, major landforms, climate bands, terrain, rivers/seas, or human-geography relationships must be resolved beyond already established regional substrate.

### Kingdoms / sociology
Use when culture, government, political structure, population/resources, or regional social organization becomes consequential.

### Cities and provinces / local campaign area
This is the **default high-value Wren domain** for active-region expansion:
- local terrain/climate expression;
- settlement placement/function;
- population scale when actually needed;
- towns/villages/cities;
- monsters/ecology;
- sites of interest/adventure locations.

### History / mythology
Use progressively when beliefs, old events, legends, calendars, ruins, institutions, or active mysteries require historical or mythic support.

## Random-table discipline

Guidebook tables are creative/generation procedures, not independent authority.

Before any consequential random generation:
1. list established constraints;
2. remove impossible/conflicting outcomes;
3. decide whether DM choice or randomness is appropriate;
4. if randomness is used, define the valid result space before rolling;
5. make a genuine secret roll;
6. accept the valid result rather than rerolling for convenience;
7. reconcile only by rejecting results that were invalid *before* the roll because they conflicted with established constraints/source authority.

This adapts the Guidebook's springboard philosophy to Wren's no-fudging campaign rule.

## Specialist-source handoff

When Guidebook generation reveals a domain with a relevant specialist 2e source, route through `SUPPLEMENT_SOURCE_RESOLUTION_POLICY.md`.

Examples:
- elf/dwarf/other race culture -> applicable PHBR/race specialist;
- class institution/tradition -> class specialist;
- castle/fortification -> applicable DMGR guide;
- catacomb/tomb/subterranean construction -> DMGR/site specialist;
- seafaring/ships/ports -> seafaring specialist;
- equipment/arms -> equipment specialist;
- villain/antagonist organization -> villain specialist.

Consultation is not automatic activation of optional mechanics.

## Monster/ecology handoff

When local-area generation needs creatures/populations:
1. resolve plausible ecological niche/current world need;
2. use `MONSTER_SOURCE_RESOLUTION_POLICY.md` for governing 2e monster treatment;
3. use `MONSTER_PROJECTION_POLICY.md` / ecology procedures;
4. use non-authoritative ecology inspiration only through `MONSTER_ECOLOGY_INSPIRATION_POLICY.md`;
5. do not populate a region merely to ensure combat.

## Adventure/site handoff

When Guidebook local-area or site-of-interest generation creates a plausible need for a scenario/site, route through `ADVENTURE_OPPORTUNITY_POLICY.md` before inventing a large adventure from scratch.

Published adventures, Dungeon Magazine scenarios, setting sites, and sourcebook-embedded sites may satisfy the need if they fit the active world with minimal surgery.

Guidebook generation may also produce an original site when no suitable published material exists or original material fits causality better.

## Knowledge and truth

A generated possibility is not automatically player-known.

Distinguish:
- Generation Candidate;
- Prepared Possibility;
- Established DM Truth;
- Player-known fact/rumor/inference.

Before a generated detail produces consequences, establish the minimum needed DM Truth. Reveal it only through legitimate observation, knowledge, source, rumor, or play.

## Current-region activation rule

When a region/settlement/site crosses the activation horizon, perform a compact world-building readiness pass:
1. what is already established;
2. what the current scene/action requires;
3. which Guidebook domain/approach fits;
4. which unresolved details can remain deferred;
5. whether a specialist/published-adventure source should be consulted;
6. what minimum facts must now become durable.

Do not fully complete every Guidebook worksheet for every activated area.

## DM notebook mapping

The Guidebook's DM-notebook categories map to existing Wren storage rather than creating a duplicate notebook:
- maps/media -> `assets/`;
- major/minor NPCs -> `state/npcs/` and character/DM shards;
- adventure records -> adventure/source registry plus checkpoints;
- PC record -> `state/character/`;
- rules/custom material -> `state/rulings/`, `rules/`, policy files;
- unusual monster notes -> monster projections/runtime state;
- time/calendar -> chronology/world clocks;
- PC motivations/goals -> player-facing character/threads state where actually established;
- sites/local customs/opportunities -> locations, regional runtime, clues/threads, adventure registry.

Do not duplicate authoritative facts solely to imitate paper forms.

## Performance contract

Normal turns pay only a cheap world-building-need check.

When triggered:
`need -> existing canonical facts -> domain/approach -> exact relevant Guidebook section/table -> result -> cache/persist if consequential`

Do not preload the full Guidebook into ordinary or Voice context. Preserve compact source locators for repeatedly used tables/procedures when useful.

## Voice

Preload already-resolved active-region facts and any immediately relevant compact generation constraints. Do not perform broad world generation in Voice.

If a consequential unresolved detail requires source retrieval unavailable in Voice, preserve the pending lookup and resolve it in text mode rather than guessing.

## Persistence

Infrastructure decisions and Prepared Possibilities do not by themselves require a real campaign checkpoint.

New generated **campaign facts** that materially affect world state, player knowledge, routes, settlements, populations, sites, factions, history, resources, or consequences become pending durable changes and are checkpointed under normal persistence rules.
