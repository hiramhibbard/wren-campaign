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

### Magic / spell corpus
- [x] Tome of Magic
- [ ] Wizard's Spell Compendium volumes — bibliographic references found, but exact uploaded volume files not yet resolved/registered
- [ ] other spell compendia / spell collections

### Magic item / artifact / provenance corpus
- [x] Encyclopedia Magica Volume 1
- [x] Encyclopedia Magica Volume 2
- [x] Encyclopedia Magica Volume 3
- [x] Encyclopedia Magica Volume 4
- [x] The Magic Encyclopedia Volume 1 — product/page provenance index
- [x] Book of Artifacts

### Monster corpus
- [x] Monstrous Compendium Annual Volume 2
- [x] Monstrous Compendium Annual Volume 3
- [x] Mystara Monstrous Compendium Appendix
- [ ] discover/register other available Annuals and setting appendices

### PHBR specialist family
- [x] PHBR01 Complete Fighter's Handbook
- [x] PHBR02 Complete Thief's Handbook
- [x] PHBR03 Complete Priest's Handbook
- [x] PHBR04 Complete Wizard's Handbook
- [x] PHBR05 Complete Psionics Handbook
- [x] PHBR06 Complete Book of Dwarves
- [x] PHBR07 Complete Bard's Handbook
- [ ] PHBR08 Complete Book of Elves — previously observed; exact source ref to resolve/register
- [x] PHBR09 Complete Book of Gnomes & Halflings
- [ ] PHBR10 inventory/register if available
- [x] PHBR11 Complete Ranger's Handbook
- [ ] inventory/register remaining available PHBR books

### DMGR specialist family
- [x] DMGR1 Campaign Sourcebook and Catacomb Guide
- [x] DMGR2 Castle Guide
- [ ] inventory/register DMGR3 Arms and Equipment Guide
- [ ] inventory/register DMGR4 Monster Mythology
- [ ] inventory/register DMGR5 Creative Campaigning
- [ ] inventory/register remaining available DMGR books

### Dragon periodical inventory
- [x] Dragon #232
- [x] Dragon #235
- [x] Dragon #236
- [x] Dragon #240
- [ ] continue issue inventory and article-level extraction

### Worldbuilding
- [x] World Builder's Guidebook source family registered under `rules/worldbuilding/INDEX.md`

### Still to inventory/register
- [ ] remaining Dragon issues
- [ ] Dungeon issues/modules
- [ ] Wizard's Spell Compendium actual uploaded volumes if present
- [ ] remaining setting source families
- [ ] remaining monster appendices/annuals

## Extracted verified entity/procedure coverage

### Current Wren/core PHB fast path
- [x] Armor spell
- [x] wizard XP / Hit Dice progression
- [x] wizard spell-slot progression
- [x] Intelligence 18 row
- [x] character encumbrance table
- [x] wizard THAC0 progression

### Core movement / travel fast path
- [x] PHB base movement rates / Table 64
- [x] normal cross-country march fields
- [x] force-march fast fields with exact-source escalation for deeper consequences
- [x] DMG Table 73 extreme terrain round-movement modifiers

### Core saves / encounter interaction
- [x] PHB Table 60 complete class-group saving throw progression
- [x] DMG Table 59 encounter reaction matrix and interpretation categories

### Core proficiencies / combat / encounter opening
- [x] PHB Table 34 proficiency slot progression + nonproficient penalties
- [x] PHB Table 51 standard combat attack modifiers
- [x] DMG Table 57 surprise modifiers
- [x] DMG Table 58 encounter distances

### Existing compatible DMG projections
- [x] wilderness encounter checks
- [x] ship weather

### Source-family structural extraction
- [x] Monstrous Compendium Annual entry-field schema and scope warning
- [x] Encyclopedia Magica item/provenance entry-field schema
- [x] Tome of Magic source structure / optional-system activation boundary

### Cross-source magic-item graph starter
- [x] Winged Mask logical entity
- [x] separate Ruins of Myth Drannor assertion
- [x] separate Dragon #117 assertion
- [x] Dragon #33 oil-family provenance relationship
- [x] 12 Dragon #33 magical-oil assertions normalized from Encyclopedia Magica Volume 2

## Index / relationship work completed

- [x] stable source-document IDs for registered sources
- [x] source-object-first registry routing
- [x] typed provenance pattern demonstrated for one entity with multiple source treatments
- [x] anthology -> original-publication relationship pattern demonstrated
- [x] source-native monster and magic-item schemas established for future batch extraction
- [x] Dragon issue registration can retain bibliographic discovery without mistaking reviews/references for source authority

## Active extraction queue

1. core initiative / combat sequencing / cover / missile / attack / proficiency / exploration procedures;
2. full high-value monster metadata/stat extraction from generic core + anthology/setting variants;
3. Encyclopedia Magica alphabetical item metadata/provenance shards;
4. Tome of Magic spell-definition shards and optional-system dependency metadata;
5. equipment/weapon/armor tables;
6. adventure/module/Dungeon metadata;
7. broader Dragon issue/article metadata + entity relationships;
8. PHBR/DMGR specialist assertions/procedures;
9. setting entities/relationships;
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

Updates to Hiram must distinguish:
- source documents inventoried/registered;
- entities/assertions actually extracted;
- assertions verified;
- indexes/relationships built;
- remaining corpus work.

Registering a document is not equivalent to extracting all entities from it.
