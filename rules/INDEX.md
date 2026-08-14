# Wren Structured Rules / Source Knowledge Registry

This directory contains verified source-derived rules projections and compiled source-knowledge objects used as runtime accelerators.

The uploaded published sources remain authoritative. A projection/object is never authoritative merely because it exists here.

## Runtime source lookup order

Prefer:

`valid runtime cache -> verified compiled source entity/assertion or structured projection -> exact governing source locator -> broader uploaded-source search`

If an object is stale, unverified, exception-sensitive, or marked `source_text_required`, escalate to the exact source.

## Compiled source knowledge

- Architecture: `SOURCE_KNOWLEDGE_LAYER_POLICY.md`
- Schema: `SOURCE_KNOWLEDGE_SCHEMA.md`
- Registry: `rules/source-knowledge/INDEX.md`

The compiled layer organizes reusable published information by entity/assertion/relationship rather than by book layout. It preserves source scope, provenance, conflicts, supersession, activation requirements, and exact locators.

Current initial verified population includes:
- AD&D 2e PHB source-document metadata;
- Armor spell structured definition;
- wizard XP/Hit Dice progression;
- wizard spell-slot progression;
- Intelligence 18 source row;
- character encumbrance breakpoints;
- wizard THAC0 progression.

See `rules/source-knowledge/INDEX.md` for current coverage.

## Active verified projections

### Encounters
- `adnd2e.dmg.encounters.wilderness-checks.v1` — `rules/encounters/dmg-wilderness-encounter-checks.md`
  - Core DMG Chapter 11 / Table 56.
  - Wilderness encounter check times and 1d10 encounter chance by terrain, plus population-density routing constraints.
  - Determines when/chance, not local encounter content.

### Travel / weather
- `adnd2e.dmg.travel.ship-weather.v1` — `rules/travel/dmg-ship-weather.md`
  - Core DMG Chapter 14 / Tables 78–79.
  - Daily ship-weather generation by season and sailing/rowing movement effects.
  - Does not replace regional climate or non-sea weather generation.

These existing projections are conceptually compiled source assertions and need not be duplicated merely to satisfy the newer source-knowledge schema.

## Specialist source routing

- General scope/domain supplement resolver: `SUPPLEMENT_SOURCE_RESOLUTION_POLICY.md`
- Source-role registry: `rules/sources/INDEX.md`
- Event-driven triggers: `state/rulings/supplement-source-triggers.md`
- Dragon article-level secondary source resolver: `DRAGON_MAGAZINE_SOURCE_POLICY.md`
- Dragon registry: `rules/dragon/INDEX.md`

PHBR/race/class specialist books and DMGR/domain guides are consulted only when their domain becomes consequential. Consultation does not activate optional mechanics. Active setting/adventure scope is resolved before generic specialist guidance is applied.

Dragon is an article-level secondary source family: useful for setting support, ecology, religion, magic, organizations, DM procedures, worldbuilding, and adventure components, but never globally active merely because an article is compiled.

## Adventure / worldbuilding source routing

- Adventure opportunity/source-or-create resolver: `ADVENTURE_OPPORTUNITY_POLICY.md`
- Published adventure registry: `rules/adventures/INDEX.md`
- World Builder runtime: `WORLD_BUILDER_RUNTIME_POLICY.md`
- World-building registry: `rules/worldbuilding/INDEX.md`

Published adventures and Dungeon material remain first-class opportunities, while original DM creation remains permitted when it fits campaign causality better.

World Builder procedures are selectively consulted for unresolved world detail; they do not force exhaustive pre-generation.

## Monster projection family

- Monster projection registry: `rules/monsters/INDEX.md`
- Normative monster projection/encounter-layer policy: `MONSTER_PROJECTION_POLICY.md`
- Normative scope-first monster source resolver: `MONSTER_SOURCE_RESOLUTION_POLICY.md`
- Monster ecology inspiration policy: `MONSTER_ECOLOGY_INSPIRATION_POLICY.md`
- Monster ecology inspiration registry: `rules/monsters/ecology-inspiration/INDEX.md`

Monster projections are created lazily from the scope-resolved active governing AD&D 2e monster source when recurrence, regional/site use, combat frequency, Voice latency, or consistency makes reuse worthwhile. Generic monster projections remain separate from encounter-instance state and campaign population/site-group state.

Monster lookup should increasingly resolve through compiled monster entities/assertions as they are populated, with exact source fallback for uncompiled/exception-sensitive material.

## Projection / compiled-object lifecycle

Each reusable source projection/object should preserve:
- stable entity/projection/assertion ID;
- source title/document ID and exact locator;
- system/edition;
- source family/role;
- active or required scope;
- verification status;
- source precedence/override notes;
- exception/source-text-required conditions;
- downstream dependency domains where applicable;
- source fingerprint/version metadata when practical.

Use `state/rulings/rules-dependency-registry.md` for invalidation/dependency routing, `state/rulings/supplement-source-triggers.md` for specialist supplement routing, `state/rulings/monster-runtime-triggers.md` for monster-specific routing, and the compiled-source schema for broader reusable source entities.

## Population priority

Continue compiled-source population in roughly this order, adjusted by actual campaign/retrieval value:
1. current-character/core fast-path mechanics;
2. core deterministic tables and procedures;
3. monsters likely to recur or enter active regions/sites;
4. spells/items/equipment;
5. class/race/proficiency material;
6. setting entities and typed relationships;
7. adventure metadata/sites/actors;
8. Dragon/Dungeon article-level metadata and cross-links;
9. specialist/worldbuilding procedures.

Do not ingest by book cover order merely for completeness. Prefer entity/domain coverage that reduces repeated PDF search and improves cross-book discovery.

## Performance contract

Normal turns use cheap routing and already-verified objects first. Broad PDF/library search is a slow path, not the default.

When a correct exact-source lookup reveals reusable structured material not yet compiled, adjudicate correctly first and then compile/queue it if that materially reduces future lookup cost.

Do not preload whole source-object libraries into ordinary or Voice context. Voice should receive only compact relevant objects/fields.
