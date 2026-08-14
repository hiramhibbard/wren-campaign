# Wren Campaign State Index

Schema version: 1
Snapshot generation: 1

Compact deterministic router for canonical campaign state and event-driven procedure/source policies. **Absence from this index or current working set is never evidence that a fact/source does not exist.**

## Core campaign state

### Character
- Wren identity/mechanics/family/player-facing mentor: `state/character/wren.md`
- Inventory/funds/encumbrance/stored gear: `state/character/inventory.md`
- Spellbook/known/memorized magic: `state/character/magic.md`

### Campaign / chronology
- Campaign framing/setting status/world-knowledge constraints: `state/campaign/context.md`
- Narration/tone profile: `state/campaign/tone.md`
- Current chronology/resume: `state/chronology/current.md`

### NPCs
- NPC router: `state/npcs/index.md`
- Aldrin Hale: `state/npcs/aldrin-hale.md`
- Edric Hale: `state/npcs/edric-hale.md`
- Mara/Elia/father/player-facing mentor: `state/character/wren.md`
- DM-only mentor truth: `state/dm/campaign.md`

### Threads / clues
- Active threads: `state/threads/active.md`
- Active clues/rumors/inference boundaries: `state/clues/active.md`

### Locations / Home Coast
- Location router: `state/locations/index.md`
- Home Coast runtime: `state/locations/home-coast/runtime-profile.md`
- Harbor/boarding-house: `state/locations/harbor/current.md`
- DM Home Coast world runtime: `state/dm/home-coast-world-runtime.md`
- DM world-building readiness audit: `state/dm/home-coast-worldbuilding-readiness.md`

After checkpoint replay establishes the current position, load only location/region/DM runtime relevant to the active horizon and derive due events before consequential time advances.

### DM-only
- Hidden campaign truth/preparation/outside forces: `state/dm/campaign.md`
- Home Coast world motion/clocks: `state/dm/home-coast-world-runtime.md`

Never expose DM-only material merely because it is loaded.

## Assets

- Asset registry: `assets/INDEX.md`
- Map registry: `assets/maps/INDEX.md`
- Home Coast map metadata: `assets/maps/asset-map-home-coast-001.md`
- Pending ingest: `assets/PENDING_INGEST.md`
- Asset policy: `ASSET_LIBRARY.md`

## Event-driven rulings / trigger routers

Base:
- Campaign rulings: `state/rulings/adnd2e-campaign-rulings.md`
- Dice: `state/rulings/dice-protocol.md`
- Base DM triggers: `state/rulings/dm-procedure-triggers.md`
- Core ordinary-gameplay triggers (checks/combat/movement/light/social/hazards): `state/rulings/core-gameplay-procedure-triggers.md`
- Rules/source dependency routing: `state/rulings/rules-dependency-registry.md`

Domain companions — load **only when implicated**:
- Regional runtime: `state/rulings/regional-runtime-triggers.md`
- Site/DM craft: `state/rulings/site-and-craft-triggers.md`
- Monsters: `state/rulings/monster-runtime-triggers.md`
- Supplements/PHBR/DMGR: `state/rulings/supplement-source-triggers.md`
- Adventure/scenario opportunity: `state/rulings/adventure-opportunity-triggers.md`
- World Builder: `state/rulings/world-builder-triggers.md`
- Dragon Magazine: `state/rulings/dragon-magazine-triggers.md`
- NPC generation/portrayal: `state/rulings/npc-generation-and-portrayal.md`
- Knowledge/rumors/deception: `state/rulings/knowledge-reliability-and-rumors.md`
- Perception/evidence: `state/rulings/perception-and-evidence.md`
- Creature ecology/behavior: `state/rulings/creature-ecology-and-behavior.md`

**Performance invariant:** loading the base trigger router does not mean executing/loading every companion. Route from the event/domain first.

## Source knowledge and published-source routing

### Compiled source layer
- Policy: `SOURCE_KNOWLEDGE_LAYER_POLICY.md`
- Schema: `SOURCE_KNOWLEDGE_SCHEMA.md`
- Registry: `rules/source-knowledge/INDEX.md`
- Rules/source registry: `rules/INDEX.md`
- Retrieval-index policy: `DERIVED_INDEX_POLICY.md`
- Context compiler: `CONTEXT_ARCHITECTURE.md`

General source lookup:
`runtime cache -> verified in-scope compiled entity/assertion/projection -> exact source locator if required -> targeted source search -> broad search last`

Compiled source objects are derived accelerators. Uploaded published sources remain authority. Object existence never activates optional/supplement/setting rules.

### Core/supplement rules
- Structured rules policy: `RULES_PROJECTION_POLICY.md`
- Specialist supplement resolver: `SUPPLEMENT_SOURCE_RESOLUTION_POLICY.md`
- Source-role registry: `rules/sources/INDEX.md`

### Monsters
- Source resolver: `MONSTER_SOURCE_RESOLUTION_POLICY.md`
- Projection/runtime: `MONSTER_PROJECTION_POLICY.md`
- Monster registry: `rules/monsters/INDEX.md`
- Ecology inspiration filter: `MONSTER_ECOLOGY_INSPIRATION_POLICY.md`
- Other ecology inspiration registry: `rules/monsters/ecology-inspiration/INDEX.md`

Monster lookup:
`encounter instance -> scope-resolved compiled monster/projection -> exact governing monster source -> Dragon ecology if gap -> other compatible inspiration if needed`

### Adventures
- Opportunity / published-or-original resolver: `ADVENTURE_OPPORTUNITY_POLICY.md`
- Published source registry: `rules/adventures/INDEX.md`

Adventure routing:
`causal opportunity -> existing seeded/active material -> compiled published metadata / targeted source search when promising -> use/adapt strong fit OR create original -> normal world motion`

Dungeon Magazine remains first-class published material. Original creation remains first-class when it is the stronger fit. No adventure quota.

### World generation
- Runtime policy: `WORLD_BUILDER_RUNTIME_POLICY.md`
- Source registry: `rules/worldbuilding/INDEX.md`

World Builder routing:
`unresolved consequential detail -> existing constraints -> verified compiled procedure if available -> smallest useful Guidebook/source path or direct bounded creation -> establish minimum truth`

### Dragon Magazine
- Policy: `DRAGON_MAGAZINE_SOURCE_POLICY.md`
- Article registry: `rules/dragon/INDEX.md`

Dragon routing:
`consequential domain gap -> compiled article/entity if available -> targeted article search -> role/scope/activation classification -> compatible use or rejection`

Dragon is a secondary article source family, not a globally active rulebook.

## Existing high-frequency projections

- Wilderness encounter checks: `rules/encounters/dmg-wilderness-encounter-checks.md`
- Ship weather: `rules/travel/dmg-ship-weather.md`
- Current compiled-source coverage/PHB fast path: `rules/source-knowledge/INDEX.md`

Exact source is required when compiled coverage is missing, stale, unverified, exception-sensitive, or marked `source_text_required`.

## Site / scenario persistence

- Site runtime: `SITE_RUNTIME_POLICY.md`
- DM craft: `DM_CRAFT_POLICY.md`

Published keys are baseline authority for unchanged material; campaign consequences overlay source state and never reset because Wren leaves/bypasses a site.

## Context / Voice

- Context compiler: `CONTEXT_ARCHITECTURE.md`
- Regional Voice/due-event extension: `CONTEXT_REGIONAL_RUNTIME_EXTENSION.md`

Normal/Voice context should contain only immediate canonical state + relevant DM state + small verified source objects likely to be needed. Never preload entire policy/source/object libraries.

## Growth / templates / protocol

- General templates: `STATE_TEMPLATES.md`
- Regional runtime templates: `REGIONAL_RUNTIME_TEMPLATES.md`
- Growth/sharding: `GROWTH_POLICY.md`
- Full bootstrap: `CAMPAIGN_BOOTSTRAP.md`
- State schema: `STATE_SCHEMA.md`
- Persistence: `PERSISTENCE_PROTOCOL.md`
- Root manifest/resume: `Wren_Campaign_Ledger.md`

Instantiate/promote records only when play/source causality warrants them.

## Regression / audit suites

- Architecture routing/performance: `tests/ARCHITECTURE_ROUTING_REGRESSION.md`
- Ordinary gameplay procedure coverage: `tests/GAME_PROCEDURE_COVERAGE_AUDIT.md`
- Regional runtime: `tests/REGIONAL_RUNTIME_REGRESSION.md`
- DM craft/site: `tests/DM_CRAFT_AND_SITE_RUNTIME_REGRESSION.md`
- Monsters: `tests/MONSTER_PROJECTION_REGRESSION.md`
- Supplements: `tests/SUPPLEMENT_SOURCE_RESOLUTION_REGRESSION.md`
- Adventures: `tests/ADVENTURE_OPPORTUNITY_REGRESSION.md`
- World Builder: `tests/WORLD_BUILDER_RUNTIME_REGRESSION.md`
- Dragon: `tests/DRAGON_MAGAZINE_SOURCE_REGRESSION.md`
- Compiled source knowledge: `tests/SOURCE_KNOWLEDGE_LAYER_REGRESSION.md`

Tests alter no live campaign facts.

## Engineering references

- Status: `CAMPAIGN_ENGINEERING.md`
- Application roadmap: `docs/APPLICATION_ROADMAP.md`
- Runtime/unit economics: `docs/DM_RUNTIME_AND_UNIT_ECONOMICS.md`
- Asset architecture: `docs/ASSET_LIBRARY_ARCHITECTURE.md`

Repository/file-library search is fallback for fuzzy references when explicit routing/compiled metadata is insufficient. Never guess because an index lacks an entry.