# Wren Compiled Source Knowledge Registry

This is the routing root for `SOURCE_KNOWLEDGE_LAYER_POLICY.md` and `SOURCE_KNOWLEDGE_SCHEMA.md`.

Status: architecture active; bulk population is underway with gameplay-latency reduction as the primary optimization target.

Operational progress: `rules/source-knowledge/INGESTION_STATUS.md`.

## Core rule

This registry indexes **entities and assertions**, not books as runtime units.

Uploaded source files remain authoritative. Compiled objects are verified derived source projections.

## Current compiled source documents

### Core
- `adnd2e.document.phb-deluxe` -> `rules/source-knowledge/documents/adnd2e-phb-deluxe.md`
- `adnd2e.document.dmg-deluxe` -> `rules/source-knowledge/documents/adnd2e-dmg-deluxe.md`
- `adnd2e.document.monstrous-manual-deluxe` -> `rules/source-knowledge/documents/adnd2e-monstrous-manual-deluxe.md`

### Magic / spell source
- `adnd2e.document.tome-of-magic` -> `rules/source-knowledge/documents/tome-of-magic.md`
  - spell source, magic-item source, and optional magic-system source;
  - availability does not activate wild magic, elementalists, expanded priest spheres, quest spells, or other campaign-impacting options.

### Magic-item / artifact / provenance corpus
- `adnd2e.document.encyclopedia-magica.v1` -> `rules/source-knowledge/documents/encyclopedia-magica-vol1.md`
- `adnd2e.document.encyclopedia-magica.v2` -> `rules/source-knowledge/documents/encyclopedia-magica-vol2.md`
- `adnd2e.document.encyclopedia-magica.v3` -> `rules/source-knowledge/documents/encyclopedia-magica-vol3.md`
- `adnd2e.document.encyclopedia-magica.v4` -> `rules/source-knowledge/documents/encyclopedia-magica-vol4.md`
- `adnd2e.document.magic-encyclopedia.v1` -> `rules/source-knowledge/documents/magic-encyclopedia-vol1-provenance-index.md`
- `adnd2e.document.book-of-artifacts` -> `rules/source-knowledge/documents/book-of-artifacts.md`

### Monster sources / anthologies
- `adnd2e.document.monstrous-compendium-annual.v2` -> `rules/source-knowledge/documents/monstrous-compendium-annual-v2.md`
- `adnd2e.document.monstrous-compendium-annual.v3` -> `rules/source-knowledge/documents/monstrous-compendium-annual-v3.md`
- `adnd2e.document.monstrous-compendium.mystara-appendix` -> `rules/source-knowledge/documents/mc-mystara-appendix.md`

### PHBR specialist sources
- PHBR01 Fighter -> `rules/source-knowledge/documents/phbr01-complete-fighters-handbook.md`
- PHBR02 Thief -> `rules/source-knowledge/documents/phbr02-complete-thiefs-handbook.md`
- PHBR03 Priest -> `rules/source-knowledge/documents/phbr03-complete-priests-handbook.md`
- PHBR04 Wizard -> `rules/source-knowledge/documents/phbr04-complete-wizards-handbook.md`
- PHBR05 Psionics -> `rules/source-knowledge/documents/phbr05-complete-psionics-handbook.md`
- PHBR06 Dwarves -> `rules/source-knowledge/documents/phbr06-complete-book-of-dwarves.md`
- PHBR07 Bards -> `rules/source-knowledge/documents/phbr07-complete-bards-handbook.md`
- PHBR09 Gnomes/Halflings -> `rules/source-knowledge/documents/phbr09-complete-gnomes-halflings.md`
- PHBR11 Rangers -> `rules/source-knowledge/documents/phbr11-complete-rangers-handbook.md`

### DMGR sources
- DMGR1 -> `rules/source-knowledge/documents/dmgr1-campaign-sourcebook-catacomb-guide.md`
- DMGR2 -> `rules/source-knowledge/documents/dmgr2-castle-guide.md`

### Dragon issue containers
- Dragon #232 -> `rules/source-knowledge/documents/dragon-232.md`
- Dragon #234 -> `rules/source-knowledge/documents/dragon-234.md`
- Dragon #235 -> `rules/source-knowledge/documents/dragon-235.md`
- Dragon #236 -> `rules/source-knowledge/documents/dragon-236.md`
- Dragon #240 -> `rules/source-knowledge/documents/dragon-240.md`
- Dragon #243 -> `rules/source-knowledge/documents/dragon-243.md`

Issue registration is navigation only; article role/scope/activation remains separate.

## Current compiled entity/assertion shards

- `rules/source-knowledge/entities/wren-core-phb-fast-path.md`
  - Armor spell; wizard XP/HD; wizard spell slots; INT 18; encumbrance; wizard THAC0.
- `rules/source-knowledge/entities/core-movement-travel-fast-path.md`
  - base movement; cross-country movement; terrain-round movement.
- `rules/source-knowledge/entities/core-saves-encounter-reaction.md`
  - character saving throws; encounter reaction.
- `rules/source-knowledge/entities/core-proficiencies-combat-surprise.md`
  - proficiency slots; standard combat attack modifiers; surprise modifiers; encounter distance.
- `rules/source-knowledge/entities/core-armor-and-spell-entry-schema.md`
  - core armor ratings; spell-entry normalization semantics.
- `rules/source-knowledge/entities/core-initiative-missile-cover.md`
  - group initiative; optional action initiative modifiers; multiple-attack/spellcasting sequencing; missile range/ROF/ability modifiers; firing into melee; cover/concealment.
- `rules/source-knowledge/entities/core-vision-light-climbing-turning-morale.md`
  - visibility ranges; common light sources/fuel durations; climbing success/modifiers/rates; turning undead; core 2e morale routing.
- `rules/source-knowledge/entities/core-healing-death-fast-path.md`
  - natural healing; magical-healing cap; raising/resurrection survival; massive damage; optional death's-door routing.
- `rules/source-knowledge/entities/core-missile-equipment-fast-path.md`
  - complete PHB Table 45 missile ranges/ROF; generic weapon-field semantics; Wren-common Table 44 price/weight lookup without altering campaign inventory.
- `rules/source-knowledge/entities/tome-of-magic-first-level-starter.md`
  - verified Tome wizard/priest first-level spell starter assertions with activation/source-text-required metadata.
- `rules/source-knowledge/entities/source-family-record-shapes.md`
  - Monstrous Compendium Annual and Encyclopedia Magica source-native record shapes.
- `rules/source-knowledge/entities/monster-scope-alias-starter.md`
  - Monstrous Manual precedence plus Mystara-scoped aliases/mappings and dragon specialization routing.
- `rules/source-knowledge/entities/monster-stirge-starter.md`
  - verified generic-core stirge stats, combat behavior, colony ecology, senses, feeding/rest cycle, field signs, and jungle-variant relationship.
- `rules/source-knowledge/entities/monster-giant-crab.md`
  - verified generic-core giant-crab stats, ambush/feeding behavior, shoreline habitat, air/water respiration, reproduction, and scavenger ecology.
- `rules/source-knowledge/entities/magic-items-cross-source-starter.md`
  - Winged Mask multi-source assertions; Dragon #33 magical-oil family; typed provenance edges.

## Existing verified projections registered conceptually

- `adnd2e.dmg.encounters.wilderness-checks.v1` -> `rules/encounters/dmg-wilderness-encounter-checks.md`
- `adnd2e.dmg.travel.ship-weather.v1` -> `rules/travel/dmg-ship-weather.md`
- verified monster projections under `rules/monsters/` as created.

## Lookup order

`stable entity/assertion ID -> typed relationship/domain query -> alias/full-text lookup -> semantic candidate lookup -> exact source locator -> broad source search`

Exact source lookup remains mandatory when a verified object is absent, stale, exception-sensitive, or explicitly marked `source_text_required`.

## Population strategy

Front-load source compilation when doing so reduces future game-table latency. Prefer core deterministic mechanics, monsters/scoped variants, spells/items/equipment, class/race/proficiency material, adventure metadata, Dragon article metadata, setting entities, then specialist/worldbuilding procedures.

Do not ingest by cover order merely for completeness. Prefer entity/domain coverage that reduces repeated PDF search and improves cross-book discovery.

## Physical storage

Do not explode the repository into millions of tiny Markdown files. Use domain/alphabetical shards or machine-readable batches as volume grows. The semantic schema in `SOURCE_KNOWLEDGE_SCHEMA.md` is authoritative over storage format.
