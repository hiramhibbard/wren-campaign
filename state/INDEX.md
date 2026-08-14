# Wren Campaign State Index

Schema version: 1
Snapshot generation: 1

This index routes canonical campaign state. Absence from the current working set does not mean absence from the campaign.

## Character
- Wren identity, ability scores, combat values, saves, proficiencies, personality, family, and player-facing witch/mentor state: `state/character/wren.md`
- Inventory, funds, encumbrance, inherited boat, boat-stored gear: `state/character/inventory.md`
- Spellbook, known/memorized magic, unresolved magic-rule items: `state/character/magic.md`

## Campaign context
- Campaign framing, low-level/earned-growth constraints, player discovery preference, setting status, and player-known wider-world peoples/race-species facts: `state/campaign/context.md`
- Mutable campaign tone/presentation profile: `state/campaign/tone.md`

Load `state/campaign/tone.md` for ordinary narration and Live Voice. Tone is a mutable presentation preference: it may be changed by Hiram at any time, but it does not override mechanics, source canon, established facts, fair consequences, NPC motives, hidden truth, or random outcomes.

## Chronology
- Current resume position and played chronology: `state/chronology/current.md`

## NPCs
- NPC routing and promotion guidance: `state/npcs/index.md`
- Aldrin Hale: `state/npcs/aldrin-hale.md`
- Edric Hale: `state/npcs/edric-hale.md`
- Mara, Elia, Wren's deceased father, and player-facing witch/mentor facts: `state/character/wren.md`
- DM-only witch/mentor truth: `state/dm/campaign.md`

## Threads and clues
- Active player-facing threads: `state/threads/active.md`
- Active player-facing clues, rumors, and inference boundaries: `state/clues/active.md`

## Locations / regional runtime
- Location routing index: `state/locations/index.md`
- Home Coast operational terrain/climate/travel/encounter/weather/lore substrate: `state/locations/home-coast/runtime-profile.md`
- Current harbor/boarding-house state: `state/locations/harbor/current.md`

After checkpoint replay establishes the true current location, if Wren is in or likely to interact with the Home Coast activation horizon, loading `state/locations/home-coast/runtime-profile.md` is **mandatory**, not optional background context. Load the corresponding relevant DM-only active-world runtime and derive the due-event frontier before advancing consequential time.

## Campaign assets / media
- Top-level campaign asset registry: `assets/INDEX.md`
- Map asset registry: `assets/maps/INDEX.md`
- Wren’s Home Coast map asset metadata: `assets/maps/asset-map-home-coast-001.md`
- Pending binary-ingest work requiring human transport: `assets/PENDING_INGEST.md`
- Normative campaign asset policy: `ASSET_LIBRARY.md`

When Hiram refers to an established map, portrait, handout, diagram, scene image, or other persistent campaign media, route through the asset registry before assuming the media is unavailable. Asset metadata is canonical; a payload marked `pending-ingest` is not yet durably retrievable and must not be described as fully saved.

## Rulings / DM procedures
- Campaign rulings and unresolved rule checks: `state/rulings/adnd2e-campaign-rulings.md`
- Dice protocol: `state/rulings/dice-protocol.md`
- DM procedure triggers for time, encounters, reaction/morale, NPC/henchmen, travel, downtime, clues, factions, significant items, published adventures, and checkpoint routing: `state/rulings/dm-procedure-triggers.md`
- Mandatory regional-runtime trigger extension for activation horizon, world motion, encounter refresh, weather, lore, and active-world creation: `state/rulings/regional-runtime-triggers.md`
- Rules dependency routing for class/level/alignment/ability/equipment/spell/item/source changes and automatic projection activation/creation/invalidation: `state/rulings/rules-dependency-registry.md`
- Context-first NPC generation, explicit race/species determination, alignment, mechanical coherence, personality, cognition, and portrayal protocol: `state/rulings/npc-generation-and-portrayal.md`
- Knowledge reliability, rumor/error/deception, deferred truth assignment, and social-belief procedure: `state/rulings/knowledge-reliability-and-rumors.md`

Whenever `state/rulings/dm-procedure-triggers.md` is loaded for normal play, treat `state/rulings/regional-runtime-triggers.md` as its mandatory companion for any current/likely regional, travel, encounter, weather, lore, faction/population, or elapsed-time interaction.

## Structured published-rules projections
- Normative structured-rules authority, creation, invalidation, fallback, and provenance policy: `RULES_PROJECTION_POLICY.md`
- Structured rules projection registry: `rules/INDEX.md`
- Core DMG wilderness encounter-check projection: `rules/encounters/dmg-wilderness-encounter-checks.md`
- Core DMG ship-weather projection: `rules/travel/dmg-ship-weather.md`

Runtime rules lookup order is: valid runtime cache -> applicable verified structured projection -> exact cited uploaded source section -> broader uploaded-source search. Uploaded published sources remain authoritative. Projection absence never permits guessing, and projection presence never overrides the governing source.

## DM-only
- Hidden established truths, prepared possibilities, outside forces, off-screen motion, and foreshadowing commitments: `state/dm/campaign.md`
- Home Coast active world elements, activation horizon, reevaluation cadences, dynamic dependencies, and hidden encounter/world-motion modifiers: `state/dm/home-coast-world-runtime.md`

Do not expose DM-only runtime records merely because they are loaded. Their observable consequences reach Wren only through legitimate play.

## Long-term state scaffolds
- Reusable NPC, henchman, world-clock, encounter, faction, clue, travel, downtime, item, source-registry, entity-promotion, and incremental-maintenance templates: `STATE_TEMPLATES.md`
- Reusable regional runtime, active-world element, population/ecology, environmental process, encounter-content, weather-state, claim/belief, activation-horizon, and due-event-frontier templates: `REGIONAL_RUNTIME_TEMPLATES.md`

These templates are operational schemas rather than live facts. Instantiate records only when play/source causality makes them relevant.

## Context and retrieval architecture
- Mandatory context-assembly policy: `CONTEXT_ARCHITECTURE.md`
- Mandatory regional-runtime/Voice/due-event context extension: `CONTEXT_REGIONAL_RUNTIME_EXTENSION.md`
- Mandatory derived-retrieval authority/safety policy: `DERIVED_INDEX_POLICY.md`
- Mandatory structured published-rules projection policy: `RULES_PROJECTION_POLICY.md`
- Mandatory regional runtime/lore/encounter/weather/world-motion policy: `REGIONAL_RUNTIME_POLICY.md`

Because this index is part of the always-loaded resume working set, resumed play must obey all of these policies. `CONTEXT_ARCHITECTURE.md` defines the disposable Context Compiler layer between canonical storage and the DM. `CONTEXT_REGIONAL_RUNTIME_EXTENSION.md` makes active-region loading, the due-event frontier, and Voice regional fast-path context explicit after checkpoint replay. `DERIVED_INDEX_POLICY.md` defines full-text/semantic/relationship indexes as rebuildable retrieval accelerators that must resolve matches back to canonical authority before established campaign facts are asserted. `RULES_PROJECTION_POLICY.md` defines verified normalized published-rule projections as derived rules accelerators subordinate to Hiram's uploaded sources. `REGIONAL_RUNTIME_POLICY.md` defines bounded regional activation, encounter derivation, weather relevance, progressive lore generation, and causally scheduled world motion.

## Regression / audit scenarios
- Regional runtime, encounter, weather, world-motion, rumor/reliability, NPC-individuality, supplement-precedence, activation-horizon, and map-authority regression scenarios: `tests/REGIONAL_RUNTIME_REGRESSION.md`

These are engineering/audit tests only. Running or reviewing them must not alter live campaign state.

## Engineering
- Architecture decisions, operational status, known limitations, validation plan, and prior future-work notes: `CAMPAIGN_ENGINEERING.md`
- Durable standalone-product evolution roadmap: `docs/APPLICATION_ROADMAP.md`
- DM runtime, provider/model routing, subscription, metering, and unit-economics roadmap module: `docs/DM_RUNTIME_AND_UNIT_ECONOMICS.md`
- Competitive landscape, product teardown, differentiation, and gap analysis: `docs/COMPETITIVE_LANDSCAPE.md`
- Campaign Asset Library and media-provenance roadmap module: `docs/ASSET_LIBRARY_ARCHITECTURE.md`
- Load engineering documents when Hiram asks to continue infrastructure, persistence, Voice workflow, memory, application/product development, maintenance, scaling, performance, model/provider strategy, subscriptions, pricing, competition, positioning, differentiation, assets/media, maps/images, or related system design.
- `docs/APPLICATION_ROADMAP.md` and its roadmap modules/research documents are deliberately non-canonical product planning. Runtime invariants belong in the normative policy/protocol files, not roadmap prose.

## Protocol
- Full operating protocol: `CAMPAIGN_BOOTSTRAP.md`
- State architecture: `STATE_SCHEMA.md`
- Persistence transaction hardening: `PERSISTENCE_PROTOCOL.md`
- Automatic growth/sharding policy: `GROWTH_POLICY.md`
- Context compiler architecture: `CONTEXT_ARCHITECTURE.md`
- Regional runtime Context Compiler/Voice extension: `CONTEXT_REGIONAL_RUNTIME_EXTENSION.md`
- Derived retrieval/index policy: `DERIVED_INDEX_POLICY.md`
- Structured rules projection policy: `RULES_PROJECTION_POLICY.md`
- Regional runtime/world-motion policy: `REGIONAL_RUNTIME_POLICY.md`
- Regional runtime reusable templates: `REGIONAL_RUNTIME_TEMPLATES.md`
- Rules dependency registry: `state/rulings/rules-dependency-registry.md`
- Regional runtime trigger extension: `state/rulings/regional-runtime-triggers.md`
- Knowledge reliability/rumor procedure: `state/rulings/knowledge-reliability-and-rumors.md`
- Campaign asset library policy: `ASSET_LIBRARY.md`
- State templates/scaffolds: `STATE_TEMPLATES.md`
- Engineering roadmap/design log: `CAMPAIGN_ENGINEERING.md`
- Standalone application evolution roadmap: `docs/APPLICATION_ROADMAP.md`
- DM runtime/unit-economics roadmap module: `docs/DM_RUNTIME_AND_UNIT_ECONOMICS.md`
- Competitive landscape/product gap research: `docs/COMPETITIVE_LANDSCAPE.md`
- Campaign asset/media architecture roadmap module: `docs/ASSET_LIBRARY_ARCHITECTURE.md`
- Root manifest/resume/baseline: `Wren_Campaign_Ledger.md`

Repository search is the fallback for fuzzy natural-language references when an explicit route is not sufficient. Derived retrieval may identify candidates, but canonical records remain authoritative.
