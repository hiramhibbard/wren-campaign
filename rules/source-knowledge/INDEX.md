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

### PHBR class/race specialist sources
- `adnd2e.document.phbr01.complete-fighters-handbook` -> `rules/source-knowledge/documents/phbr01-complete-fighters-handbook.md`
- `adnd2e.document.phbr02.complete-thiefs-handbook` -> `rules/source-knowledge/documents/phbr02-complete-thiefs-handbook.md`
- `adnd2e.document.phbr03.complete-priests-handbook` -> `rules/source-knowledge/documents/phbr03-complete-priests-handbook.md`
- `adnd2e.document.phbr04.complete-wizards-handbook` -> `rules/source-knowledge/documents/phbr04-complete-wizards-handbook.md`
- `adnd2e.document.phbr05.complete-psionics-handbook` -> `rules/source-knowledge/documents/phbr05-complete-psionics-handbook.md`
- `adnd2e.document.phbr06.complete-book-of-dwarves` -> `rules/source-knowledge/documents/phbr06-complete-book-of-dwarves.md`
- `adnd2e.document.phbr07.complete-bards-handbook` -> `rules/source-knowledge/documents/phbr07-complete-bards-handbook.md`
- `adnd2e.document.phbr09.complete-gnomes-halflings` -> `rules/source-knowledge/documents/phbr09-complete-gnomes-halflings.md`
- `adnd2e.document.phbr11.complete-rangers-handbook` -> `rules/source-knowledge/documents/phbr11-complete-rangers-handbook.md`

### DMGR domain-guide sources
- `adnd2e.document.dmgr1.campaign-sourcebook-catacomb-guide` -> `rules/source-knowledge/documents/dmgr1-campaign-sourcebook-catacomb-guide.md`
- `adnd2e.document.dmgr2.castle-guide` -> `rules/source-knowledge/documents/dmgr2-castle-guide.md`

### Dragon Magazine issue containers
- `adnd2e.document.dragon.232` -> `rules/source-knowledge/documents/dragon-232.md`
- `adnd2e.document.dragon.235` -> `rules/source-knowledge/documents/dragon-235.md`
- `adnd2e.document.dragon.236` -> `rules/source-knowledge/documents/dragon-236.md`
- `adnd2e.periodical.dragon.240` -> `rules/source-knowledge/documents/dragon-240.md`

Issue registration is navigation only. Article-level role/scope/activation remains separate under `DRAGON_MAGAZINE_SOURCE_POLICY.md`.

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
  - core armor class ratings; common spell-entry field semantics for consistent PHB/Tome/Spell-Compendium extraction.
- `rules/source-knowledge/entities/source-family-record-shapes.md`
  - Monstrous Compendium Annual and Encyclopedia Magica source-native record shapes.
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
