# Wren Compiled Source Knowledge Registry

This is the routing root for `SOURCE_KNOWLEDGE_LAYER_POLICY.md` and `SOURCE_KNOWLEDGE_SCHEMA.md`.

Status: architecture active; population is incremental/batch-driven and has begun.

## Core rule

This registry indexes **entities and assertions**, not books as runtime units.

Uploaded source files remain authoritative. Compiled objects are verified derived source projections.

## Current compiled source documents

- `adnd2e.document.phb-deluxe` -> `rules/source-knowledge/documents/adnd2e-phb-deluxe.md`
  - uploaded source: `DD2_PHB_Deluxe.pdf`
  - core Player's Handbook metadata/high-value locators.
- `adnd2e.document.dmg-deluxe` -> `rules/source-knowledge/documents/adnd2e-dmg-deluxe.md`
  - uploaded source: `DD2_DMG_Deluxe.pdf`
  - core Dungeon Master Guide metadata, encounter/travel/weather/treasure locator families.
- `adnd2e.document.monstrous-manual-deluxe` -> `rules/source-knowledge/documents/adnd2e-monstrous-manual-deluxe.md`
  - uploaded source: `DD2_MonstrousManual_Deluxe.pdf`
  - default generic core-monster source family subject to scope-first monster resolution.

## Current compiled entity/assertion shards

- `rules/source-knowledge/entities/wren-core-phb-fast-path.md`
  - `adnd2e.spell.wizard.armor`
  - `adnd2e.class.wizard` / Table 20 XP & Hit Dice progression
  - `adnd2e.class.wizard` / Table 21 spell-slot progression
  - `adnd2e.ability.intelligence` / Intelligence 18 source row
  - `adnd2e.rule.encumbrance.basic` / Table 47 breakpoints
  - `adnd2e.rule.thac0.calculated` / wizard THAC0 progression

These objects were source-verified against the uploaded PHB and eliminate repeated broad PDF lookup for current Wren fast-path mechanics.

## Existing verified projections registered conceptually

Existing structured projections remain valid source-knowledge assertions in their legacy paths; do not duplicate them merely for storage uniformity.

- `adnd2e.dmg.encounters.wilderness-checks.v1` -> `rules/encounters/dmg-wilderness-encounter-checks.md`
- `adnd2e.dmg.travel.ship-weather.v1` -> `rules/travel/dmg-ship-weather.md`
- verified monster projections under `rules/monsters/` as they are created.

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

Current implementation started with Wren-relevant PHB fast path and registered PHB/DMG/MM source documents. Continue outward by reuse value, cross-book discovery value, and observed lookup friction rather than book cover order.

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

## Physical storage

Do not explode the repository into millions of tiny Markdown files prematurely.

Use domain shards or machine-readable batches when volume grows. The semantic schema in `SOURCE_KNOWLEDGE_SCHEMA.md` is authoritative over any particular storage format.
