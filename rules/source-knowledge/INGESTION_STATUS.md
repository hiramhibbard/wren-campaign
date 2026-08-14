# Wren Compiled Source Ingestion Status

Purpose: operational progress tracker for bulk source compilation. This file records ingestion coverage and queue state only; it is not campaign truth and does not activate source material.

## Current mode

- strategy: `front-load-for-gameplay-performance`
- priority: optimize later game-table latency even when maintenance ingestion is expensive
- authority: uploaded source corpus remains ultimate published authority
- storage: domain/alphabetical shards preferred over one-file-per-entity explosion
- verification: only verified assertions may satisfy source-dependent gameplay without exact-source fallback

## Registered source documents

### Core
- [x] Player's Handbook Deluxe
- [x] Dungeon Master Guide Deluxe
- [x] Monstrous Manual Deluxe

### Magic item corpus
- [x] Encyclopedia Magica Volume 1
- [x] Encyclopedia Magica Volume 2
- [x] Encyclopedia Magica Volume 3
- [x] Encyclopedia Magica Volume 4

### Monster anthology corpus
- [x] Monstrous Compendium Annual Volume 2
- [x] Monstrous Compendium Annual Volume 3
- [ ] discover/register other available Monstrous Compendium Annuals and setting appendices

### Worldbuilding
- [x] World Builder's Guidebook source family already registered under `rules/worldbuilding/INDEX.md`

### Periodicals / adventures / specialist books
- [ ] inventory Dragon issues
- [ ] inventory Dungeon issues/modules
- [ ] inventory PHBR family
- [ ] inventory DMGR family
- [ ] inventory setting source families
- [ ] inventory spell compendia / Tome of Magic / other spell sources

## Extracted verified entity/procedure coverage

### Current Wren/core PHB fast path
- [x] Armor spell
- [x] wizard XP / Hit Dice progression
- [x] wizard spell-slot progression
- [x] Intelligence 18 row
- [x] character encumbrance table
- [x] wizard THAC0 progression

### Existing compatible DMG projections
- [x] wilderness encounter checks
- [x] ship weather

## Active extraction queue

1. core combat/save/ability/proficiency/movement/exploration fast-path procedures;
2. full high-value monster metadata/stat extraction from generic core + anthology/setting variants;
3. Encyclopedia Magica item metadata/provenance shards;
4. spell corpus discovery and spell-definition shards;
5. equipment/weapon/armor tables;
6. adventure/module/Dungeon metadata;
7. Dragon article metadata + entity relationships;
8. PHBR/DMGR specialist assertions/procedures;
9. active or likely setting entities/relationships;
10. World Builder reusable tables/procedure objects.

## Quality gates

For each extracted assertion, preserve as applicable:
- stable entity/assertion ID;
- source document ID;
- exact locator;
- edition/system;
- setting/adventure/domain scope;
- source role;
- activation requirement;
- structured fields;
- short normalized summary;
- source-text-required flag;
- conflicts/supersession/variant relationship;
- verification state.

## Progress reporting

Updates to Hiram should distinguish:
- source documents inventoried/registered;
- entities/assertions actually extracted;
- assertions verified;
- indexes/relationships built;
- remaining corpus work.

Do not imply that registering a document equals extracting all entities from it.
