# Wren Compiled Source Knowledge Registry

This is the routing root for `SOURCE_KNOWLEDGE_LAYER_POLICY.md` and `SOURCE_KNOWLEDGE_SCHEMA.md`.

Status: architecture active; population is incremental/batch-driven.

## Core rule

This registry indexes **entities and assertions**, not books as runtime units.

Uploaded source files remain authoritative. Compiled objects are verified derived source projections.

## Current entity families

Expected high-value families include:
- monsters and variants;
- spells;
- magic items/artifacts;
- mundane equipment;
- classes/kits/races/proficiencies;
- deities/priesthoods;
- setting places/regions/cultures/factions/NPCs;
- adventures/sites/encounters;
- hazards/traps/treasure tables;
- deterministic rules/procedures;
- worldbuilding procedures;
- Dragon articles and article-derived entities;
- Dungeon adventures/scenario components;
- maps/handouts/source assets.

## Lookup order

`stable entity/assertion ID -> typed relationship/domain query -> alias/full-text lookup -> semantic candidate lookup -> exact source locator -> broad source search`

Exact source lookup remains mandatory when a verified object is absent, stale, exception-sensitive, or explicitly marked `source_text_required`.

## Population strategy

### Immediate / lazy
When ordinary play repeatedly retrieves a reusable source fact, compile and verify the object if doing so materially reduces future lookup cost.

### Maintenance / batch
Maintenance may ingest source families in bulk, prioritizing:
1. core deterministic mechanics;
2. monsters;
3. spells/items/equipment;
4. class/race/proficiency material;
5. setting entities/relationships;
6. adventure metadata/sites/actors;
7. Dragon/Dungeon article-level metadata;
8. specialist and worldbuilding procedures.

## Indexes

Future derived indexes may be generated from this registry/object corpus:
- aliases/names;
- entity/domain tags;
- setting/scope;
- source provenance;
- relationships;
- full text over compact summaries;
- semantic embeddings;
- adventure/environment/risk facets;
- monster habitat/ecology facets;
- rules-domain/procedure triggers.

These indexes remain subordinate to verified assertions and uploaded sources.

## Current compiled projections already compatible with this layer

Existing structured rules/monster projections are grandfathered source-knowledge objects conceptually even if stored in their current directories. They need not be physically migrated immediately.

Examples include:
- `rules/encounters/dmg-wilderness-encounter-checks.md`;
- `rules/travel/dmg-ship-weather.md`;
- verified monster projections under `rules/monsters/`;
- other deterministic projections created under `RULES_PROJECTION_POLICY.md`.

Future maintenance may register stable entity/assertion IDs pointing at these existing projections rather than duplicating them.

## Physical storage

Do not explode the repository into millions of tiny Markdown files prematurely.

Use domain shards or machine-readable batches when volume grows. The semantic schema in `SOURCE_KNOWLEDGE_SCHEMA.md` is authoritative over any particular storage format.
