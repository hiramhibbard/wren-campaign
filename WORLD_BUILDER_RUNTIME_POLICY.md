# Wren World Builder Runtime Policy — v1

This policy defines how the AD&D 2e *World Builder's Guidebook* is used to generate new campaign material for Wren without overbuilding the world, contradicting established canon, or turning random tables into arbitrary truth.

## Source role and authority

`World Builders Guidebook.pdf` (TSR 9532, AD&D 2e) is an active **DM world-generation procedure source** for original/unresolved campaign space.

It does not override established Wren campaign facts, an active published campaign-setting source, an active published adventure/site source, governing PHB/DMG/monster mechanics, or explicit campaign rulings.

Use it to help answer questions the world genuinely needs answered and that remain unresolved. It is a toolkit, not a requirement to mechanize every creative decision.

## Core generation chain

Use:

`current causal need -> established constraints -> choose appropriate world-building approach -> retrieve only relevant Guidebook domain/table when useful -> specialist/adventure/source handoff if helpful -> constrained DM choice or genuine secret roll -> consistency check -> minimum necessary truth -> runtime/persistence`

Never begin with a random table and search for somewhere to force the result into the campaign.

## Default Wren design approach

Wren's current campaign uses the **microscopic approach** as the default: begin with the known local campaign area, settlements, sites, people, monsters, and adventures, then expand outward only as play makes farther geography/society/history consequential.

Other Guidebook approaches are routing modes:
- **sociological** — culture, kingdom, institution, political relationship;
- **character-based** — consequential PC/NPC background, homeland, family, order, or prime mover;
- **situation-based** — unusual magical, ecological, political, military, monster, or other dominant condition;
- **historical** — present facts depending on unresolved past events;
- **macroscopic** — continent/planet-scale dependencies only when genuinely consequential;
- **published-world interpretation** — active setting authority first, Guidebook only for compatible unresolved detail.

## Progressive detail rule

Generate at the smallest causal scale that can answer the current question:
- room/site before entire province;
- village institution before national government;
- route segment before full regional road map;
- local population/ecology before continent-wide demographics;
- local historical event before complete chronology;
- current settlement function before exact population census.

Do not generate unused world detail just because a Guidebook table exists.

## Domain routing

### Worlds / planetology
Use only when planetary shape, seas, tectonics, global climate, seasons, or equivalent large-scale facts become consequential and are not already governed by a setting source.

### Continents / geography
Use when coastlines, major landforms, climate bands, terrain, rivers/seas, or human-geography relationships must be resolved beyond already established regional substrate.

### Kingdoms / sociology
Use when culture, government, political structure, population/resources, or regional social organization becomes consequential.

### Cities and provinces / local campaign area
Default high-value Wren domain for active-region expansion: local terrain/climate expression, settlement placement/function, population scale when needed, towns/villages/cities, monsters/ecology, and sites of interest/adventure locations.

### History / mythology
Use progressively when beliefs, old events, legends, calendars, ruins, institutions, or active mysteries require historical or mythic support.

## Random-table discipline

Guidebook tables are creative/generation procedures, not independent authority.

Before consequential random generation:
1. list established constraints;
2. remove impossible/conflicting outcomes;
3. decide whether DM choice or randomness is appropriate;
4. if randomness is used, define the valid result space before rolling;
5. make a genuine secret roll;
6. accept the valid result rather than rerolling for convenience;
7. reject only outcomes that were invalid before the roll because they conflicted with established constraints/source authority.

## Specialist-source handoff

When Guidebook generation reveals a relevant specialist 2e domain, route through `SUPPLEMENT_SOURCE_RESOLUTION_POLICY.md` when that improves accuracy or depth. Consultation is not automatic activation of optional mechanics.

## Monster/ecology handoff

When local-area generation needs creatures/populations, use monster source/ecology policy before establishing durable population facts. Do not populate a region merely to ensure combat.

## Adventure/site handoff

When Guidebook local-area or site-of-interest generation creates a plausible need for a scenario/site, use `ADVENTURE_OPPORTUNITY_POLICY.md`.

Published adventures, Dungeon Magazine scenarios, setting sites, and sourcebook-embedded sites are valuable candidates when they fit naturally. They are **not mandatory prerequisites** to original DM creation.

The DM may create an original site/adventure immediately when existing campaign causality implies it, when no published material fits well, when published material would require excessive surgery, or when bounded improvisation is the cleaner and stronger choice.

Do not broad-search the library merely to avoid inventing something.

## Knowledge and truth

A generated possibility is not automatically player-known.

Distinguish Generation Candidate, Prepared Possibility, Established DM Truth, and player-known fact/rumor/inference. Before a generated detail produces consequences, establish the minimum needed DM Truth and reveal it only through legitimate play.

## Current-region activation rule

When a region/settlement/site crosses the activation horizon, perform a compact readiness pass:
1. what is already established;
2. what the current scene/action requires;
3. which Guidebook domain/approach fits, if any;
4. which unresolved details can remain deferred;
5. whether specialist, published-adventure, or original creation is the best route;
6. what minimum facts must now become durable.

Do not fully complete every Guidebook worksheet for every activated area.

## DM notebook mapping

The Guidebook's notebook categories map to existing Wren storage rather than creating a duplicate notebook: maps/media -> `assets/`; NPCs -> `state/npcs/`; adventures -> adventure/source registry plus checkpoints; PC -> `state/character/`; rules -> `state/rulings/` and `rules/`; monsters -> monster projections/runtime state; time -> chronology/world clocks; motivations/goals -> character/threads state; sites/customs/opportunities -> locations, regional runtime, clues/threads, adventure registry.

## Performance contract

Normal turns pay only a cheap world-building-need check.

When triggered:
`need -> existing canonical facts -> choose direct DM creation or narrow source/tool route -> bounded generation -> persist if consequential`

Do not preload the full Guidebook into ordinary or Voice context. Preserve compact source locators for repeatedly used tables/procedures when useful.

## Voice

Preload already-resolved active-region facts and immediately relevant constraints. Bounded original improvisation from established loaded context is allowed. If a consequential unresolved fact specifically requires source retrieval unavailable in Voice, preserve the pending lookup rather than guessing the source fact.

## Persistence

Infrastructure decisions and Prepared Possibilities do not by themselves require a real campaign checkpoint.

New generated **campaign facts** that materially affect world state, player knowledge, routes, settlements, populations, sites, factions, history, resources, or consequences become pending durable changes and are checkpointed under normal persistence rules.