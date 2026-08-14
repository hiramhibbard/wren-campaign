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

The Encyclopedia Magica family is a high-priority entity/provenance corpus. The older Magic Encyclopedia is treated chiefly as a product/page locator crosswalk rather than complete mechanical authority. Book of Artifacts is a high-value artifact-definition/design source. Compilation never instantiates an item/artifact in Wren's world.

### Monster sources / anthologies
- `adnd2e.document.monstrous-compendium-annual.v2` -> `rules/source-knowledge/documents/monstrous-compendium-annual-v2.md`
- `adnd2e.document.monstrous-compendium-annual.v3` -> `rules/source-knowledge/documents/monstrous-compendium-annual-v3.md`
- `adnd2e.document.monstrous-compendium.mystara-appendix` -> `rules/source-knowledge/documents/mc-mystara-appendix.md`

Annual/anthology/setting creature entries remain scope-sensitive assertions; setting/adventure variants must not be flattened into generic monster definitions. Registering the Mystara appendix does not make Mystara Wren's active setting.

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

Compilation makes these specialists cheap to consult; it does not activate kits, optional combat systems, psionics, specialty-priest mechanics, racial substitutions, or other optional treatments.

### DMGR domain-guide sources
- `adnd2e.document.dmgr1.campaign-sourcebook-catacomb-guide` -> `rules/source-knowledge/documents/dmgr1-campaign-sourcebook-catacomb-guide.md`
- `adnd2e.document.dmgr2.castle-guide` -> `rules/source-knowledge/documents/dmgr2-castle-guide.md`

### Dragon Magazine issue containers
- `adnd2e.document.dragon.232` -> `rules/source-knowledge/documents/dragon-232.md`
- `adnd2e.document.dragon.235` -> `rules/source-knowledge/documents/dragon-235.md`
- `adnd2e.document.dragon.236` -> `rules/source-knowledge/documents/dragon-236.md`
- `adnd2e.periodical.dragon.240` -> `rules/source-knowledge/documents/dragon-240.md`

Issue registration is navigation only. Article-level role/scope/activation remains separate under `DRAGON_MAGAZINE_SOURCE_POLICY.md`. Bibliographic notices/reviews may aid source discovery but never substitute for the referenced publication.

### Worldbuilding / periodicals / adventures
- World Builder source family: `rules/worldbuilding/INDEX.md`
- Dragon article family: `rules/dragon/INDEX.md`
- Published adventure/Dungeon family: `rules/adventures/INDEX.md`
- Specialist source roles: `rules/sources/INDEX.md`

Individual source documents/articles/modules continue to be registered as bulk inventory proceeds.

## Current compiled entity/assertion shards

### Current-Wren PHB fast path
- `rules/source-knowledge/entities/wren-core-phb-fast-path.md`
  - `adnd2e.spell.wizard.armor`
  - `adnd2e.class.wizard` / Table 20 XP & Hit Dice progression
  - `adnd2e.class.wizard` / Table 21 spell-slot progression
  - `adnd2e.ability.intelligence` / Intelligence 18 source row
  - `adnd2e.rule.encumbrance.basic` / Table 47 breakpoints
  - `adnd2e.rule.thac0.calculated` / wizard THAC0 progression

### Core movement / travel
- `rules/source-knowledge/entities/core-movement-travel-fast-path.md`
  - `adnd2e.rule.movement.base-rates` / PHB Table 64
  - `adnd2e.rule.movement.cross-country` / normal march + force-march fast fields
  - `adnd2e.rule.movement.terrain-round` / DMG Table 73 extreme terrain movement

### Core saves / encounter reaction
- `rules/source-knowledge/entities/core-saves-encounter-reaction.md`
  - `adnd2e.rule.saving-throws.character` / PHB Table 60 complete class-group save progression
  - `adnd2e.rule.encounter.reaction` / DMG Table 59 encounter-reaction procedure

### Core proficiencies / combat / encounter opening
- `rules/source-knowledge/entities/core-proficiencies-combat-surprise.md`
  - `adnd2e.rule.proficiencies.slots` / PHB Table 34
  - `adnd2e.rule.combat.attack-modifiers.standard` / PHB Table 51
  - `adnd2e.rule.encounter.surprise-modifiers` / DMG Table 57
  - `adnd2e.rule.encounter.distance` / DMG Table 58

### Source-family structural schemas
- `rules/source-knowledge/entities/source-family-record-shapes.md`
  - `adnd2e.source-schema.monster-entry.mca` / Monstrous Compendium Annual source-native monster fields
  - `adnd2e.source-schema.magic-item.encyclopedia-magica` / Encyclopedia Magica item/provenance fields

These schemas allow bulk ingestion to preserve source-native fields and relationships instead of flattening monster ecology or magic-item provenance.

### Magic-item cross-source starter graph
- `rules/source-knowledge/entities/magic-items-cross-source-starter.md`
  - `adnd2e.magic-item.mask.winged` with separate *Ruins of Myth Drannor* and Dragon #117 assertions
  - Dragon #33 magical-oil family with individually normalized oil assertions
  - provenance relationships from anthology assertion back to original publication

This starter shard proves the intended cross-source behavior: one logical entity can retain multiple source assertions and typed provenance relationships without silently merging them.

## Existing verified projections registered conceptually

Existing structured projections remain valid source-knowledge assertions in their legacy paths; do not duplicate them merely for storage uniformity.

- `adnd2e.dmg.encounters.wilderness-checks.v1` -> `rules/encounters/dmg-wilderness-encounter-checks.md`
- `adnd2e.dmg.travel.ship-weather.v1` -> `rules/travel/dmg-ship-weather.md`
- verified monster projections under `rules/monsters/` as they are created.

## Current entity families

High-value families include monsters/variants; spells; magic items/artifacts; equipment; classes/kits/races/proficiencies; deities/priesthoods; setting places/regions/cultures/factions/NPCs; adventures/sites/encounters; hazards/traps/treasure tables; deterministic rules/procedures; worldbuilding procedures; Dragon articles; Dungeon scenarios; maps/handouts/source assets.

## Lookup order

`stable entity/assertion ID -> typed relationship/domain query -> alias/full-text lookup -> semantic candidate lookup -> exact source locator -> broad source search`

Exact source lookup remains mandatory when a verified object is absent, stale, exception-sensitive, or explicitly marked `source_text_required`.

## Population strategy

The campaign intentionally front-loads source compilation when doing so can reduce future game-table latency.

### Ordinary play
When a correct source lookup exposes reusable material not yet compiled, adjudicate first and compile/queue it when worthwhile.

### Bulk ingestion / maintenance
Bulk extraction is encouraged for high-value source families even when the maintenance job is expensive. Priority is roughly:
1. core deterministic mechanics/procedures;
2. monsters and scoped variants;
3. spells/items/equipment;
4. class/race/proficiency material;
5. adventure/module/Dungeon metadata;
6. Dragon article metadata/relationships;
7. setting entities/relationships;
8. specialist and worldbuilding procedures.

Optimize for later gameplay lookup cost rather than minimizing maintenance duration.

## Indexes

Derived indexes may be generated from this registry/object corpus: aliases/names, entity/domain tags, setting/scope, source provenance, relationships, compact-summary full text, semantic embeddings, adventure/environment/risk facets, monster habitat/ecology facets, and rules-domain/procedure triggers.

These indexes remain subordinate to verified assertions and uploaded sources.

## Physical storage

Do not explode the repository into millions of tiny Markdown files. Use domain/alphabetical shards or machine-readable batches as volume grows. The semantic schema in `SOURCE_KNOWLEDGE_SCHEMA.md` is authoritative over storage format.
