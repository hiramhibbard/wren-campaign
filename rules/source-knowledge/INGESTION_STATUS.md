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
- [ ] Wizard's Spell Compendium volumes — bibliographic references found, exact uploaded volume files not yet resolved/registered
- [ ] other spell compendia / spell collections

### Magic item / artifact / provenance corpus
- [x] Encyclopedia Magica Volumes 1-4
- [x] The Magic Encyclopedia Volume 1 provenance index
- [x] Book of Artifacts

### Monster corpus
- [x] Monstrous Compendium Annual Volume 2
- [x] Monstrous Compendium Annual Volume 3
- [x] Mystara Monstrous Compendium Appendix
- [ ] discover/register other available Annuals and setting appendices

### PHBR specialist family
- [x] PHBR01 Fighter
- [x] PHBR02 Thief
- [x] PHBR03 Priest
- [x] PHBR04 Wizard
- [x] PHBR05 Psionics
- [x] PHBR06 Dwarves
- [x] PHBR07 Bard
- [ ] PHBR08 Elves — previously observed; exact source ref still to resolve/register
- [x] PHBR09 Gnomes & Halflings
- [ ] PHBR10 inventory/register if available
- [x] PHBR11 Ranger
- [ ] inventory/register remaining available PHBR books

### DMGR specialist family
- [x] DMGR1 Campaign Sourcebook and Catacomb Guide
- [x] DMGR2 Castle Guide
- [ ] DMGR3 Arms and Equipment Guide
- [ ] DMGR4 Monster Mythology
- [ ] DMGR5 Creative Campaigning
- [ ] remaining DMGR books

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

### Core movement / travel
- [x] PHB base movement rates
- [x] normal cross-country march fields
- [x] force-march fast fields with exact-source escalation
- [x] DMG extreme terrain round-movement modifiers

### Core saves / encounter interaction
- [x] complete class-group saving throw progression
- [x] encounter-reaction matrix and interpretation categories

### Core proficiencies / combat / encounter opening
- [x] proficiency slot progression + nonproficient penalties
- [x] standard combat attack modifiers
- [x] surprise modifiers
- [x] encounter distances
- [x] group initiative standard modifiers
- [x] optional action-specific initiative modifiers + activation boundary
- [x] multiple-attack sequencing
- [x] spellcasting/initiative timing fields
- [x] missile range categories and attack modifiers
- [x] missile ROF procedure
- [x] Strength/Dexterity missile rules
- [x] firing-into-melee weighted-target procedure
- [x] cover/concealment table and physical-damage spell save effects

### Core armor / spell parsing
- [x] core armor class ratings
- [x] common spell-entry field semantics

### Existing compatible DMG projections
- [x] wilderness encounter checks
- [x] ship weather

### Tome of Magic extraction
- [x] source structure / optional-system activation boundary
- [x] common spell normalization schema
- [x] first-level wizard starter shard: Conjure Spell Component, Fire Burst, Fist of Stone, Lasting Breath, Metamorphose Liquids, Murdock's Feathery Flyer, Nahal's Reckless Dweomer, Patternweave
- [x] first-level priest starter shard: Know Time, Log of Everburning, Mistaken Missive, Sacred Guardian, Speak With Astral Traveler, Thought Capture
- [ ] continue remaining 1st-level spells and higher levels in batches

### Monster source routing / structure
- [x] Monstrous Compendium Annual source-native entry schema
- [x] Monstrous Manual generic-core supersession/setting handoff assertion
- [x] Mystara-scoped monster alias/mapping starter graph
- [x] Mystara dragon specialization scope profile
- [ ] bulk stat/ecology entries by high-value/common/active-region priority

### Magic-item graph
- [x] Encyclopedia Magica item/provenance entry schema
- [x] Winged Mask logical entity with separate Ruins of Myth Drannor and Dragon #117 assertions
- [x] Dragon #33 oil-family provenance relationship
- [x] 12 Dragon #33 magical-oil assertions
- [ ] alphabetical Encyclopedia Magica extraction shards

## Index / relationship work completed

- [x] stable source-document IDs for registered sources
- [x] source-object-first registry routing
- [x] typed provenance pattern for multiple source treatments
- [x] anthology -> original-publication relationships
- [x] source-native monster and magic-item schemas
- [x] spell extraction schema with activation/source-text-required gates
- [x] scoped monster aliases that do not contaminate generic namespace
- [x] source-precedence handoff from generic Monstrous Manual to setting-specific appendices

## Active extraction queue

1. remaining core combat/exploration fast paths: visibility/light, climbing, weapon/equipment tables, turning undead, morale, common save modifiers;
2. bulk high-value monster stat/ecology extraction from core + annuals + setting variants;
3. Encyclopedia Magica alphabetical item metadata/provenance shards;
4. continue Tome of Magic spell-definition shards;
5. adventure/module/Dungeon metadata;
6. broader Dragon issue/article metadata + entity relationships;
7. PHBR/DMGR specialist assertions/procedures;
8. setting entities/relationships;
9. World Builder reusable tables/procedure objects.

## Quality gates

For each extracted assertion preserve, as applicable: stable IDs; source document; exact locator; edition/system; setting/adventure/domain scope; source role; activation requirement; structured fields; short summary; source-text-required flag; conflicts/supersession/variant relationships; verification state.

## Progress reporting

Updates to Hiram distinguish source registration, actual extraction, verification, relationship/index work, and remaining corpus work. Registering a document is not equivalent to extracting all entities from it.
