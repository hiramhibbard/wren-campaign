# Wren Campaign State Index

Schema version: 1
Snapshot generation: 1

This index routes canonical campaign state. Absence from the current working set does not mean absence from the campaign.

## Character
- Wren identity/mechanics/family/player-facing mentor state: `state/character/wren.md`
- Inventory/funds/encumbrance/boat-stored gear: `state/character/inventory.md`
- Spellbook/known and memorized magic: `state/character/magic.md`

## Campaign context
- Campaign framing, low-level/earned-growth constraints, discovery preference, setting status, wider-world player-known facts: `state/campaign/context.md`
- Mutable narration/tone profile: `state/campaign/tone.md`

Load `state/campaign/tone.md` for ordinary narration and Live Voice. Tone never overrides mechanics, source canon, established facts, fair consequences, NPC motives, hidden truth, or random outcomes.

## Chronology
- Current resume position and played chronology: `state/chronology/current.md`

## NPCs
- NPC routing/promotion: `state/npcs/index.md`
- Aldrin Hale: `state/npcs/aldrin-hale.md`
- Edric Hale: `state/npcs/edric-hale.md`
- Mara, Elia, Wren's deceased father, player-facing mentor facts: `state/character/wren.md`
- DM-only mentor truth: `state/dm/campaign.md`

## Threads and clues
- Active player-facing threads: `state/threads/active.md`
- Active clues/rumors/inference boundaries: `state/clues/active.md`

## Locations / regional runtime
- Location routing: `state/locations/index.md`
- Home Coast runtime profile: `state/locations/home-coast/runtime-profile.md`
- Harbor/boarding-house state: `state/locations/harbor/current.md`

After checkpoint replay establishes current location, if Wren is in or can plausibly affect the Home Coast activation horizon, load `state/locations/home-coast/runtime-profile.md`, relevant DM-only active-world runtime, and derive the due-event frontier before advancing consequential time.

## Active sites / dungeons
- Mandatory bounded-site runtime: `SITE_RUNTIME_POLICY.md`

When a bounded site's internal state matters, load only the minimum applicable runtime. Published keys remain authority for unchanged/unvisited material; campaign consequences overlay source state and do not reset.

## Campaign assets / media
- Asset registry: `assets/INDEX.md`
- Map registry: `assets/maps/INDEX.md`
- Home Coast map metadata: `assets/maps/asset-map-home-coast-001.md`
- Pending ingest: `assets/PENDING_INGEST.md`
- Policy: `ASSET_LIBRARY.md`

## Rulings / DM procedures
- Campaign rulings: `state/rulings/adnd2e-campaign-rulings.md`
- Dice protocol: `state/rulings/dice-protocol.md`
- Base DM procedure triggers: `state/rulings/dm-procedure-triggers.md`
- Regional-runtime triggers: `state/rulings/regional-runtime-triggers.md`
- Site/DM-craft triggers: `state/rulings/site-and-craft-triggers.md`
- Monster projection/runtime triggers: `state/rulings/monster-runtime-triggers.md`
- Specialist supplement source triggers: `state/rulings/supplement-source-triggers.md`
- **Automatic published-adventure opportunity triggers: `state/rulings/adventure-opportunity-triggers.md`**
- Rules dependency routing: `state/rulings/rules-dependency-registry.md`
- NPC generation/portrayal: `state/rulings/npc-generation-and-portrayal.md`
- Knowledge reliability/rumors/deception: `state/rulings/knowledge-reliability-and-rumors.md`
- Perception/evidence: `state/rulings/perception-and-evidence.md`
- Creature ecology/behavior: `state/rulings/creature-ecology-and-behavior.md`

Whenever normal play loads `state/rulings/dm-procedure-triggers.md`, treat regional, site/craft, monster, supplement-source, and adventure-opportunity trigger extensions as mandatory companions **when their domains are implicated**. They are event-driven; do not scan all source families every turn.

Adventure opportunities must be recognized automatically. Hiram does not need to ask the DM to search for or introduce a published adventure. A plausible world need/opportunity may trigger targeted published-source discovery, but candidate material does not become campaign truth until actually seeded through `ADVENTURE_OPPORTUNITY_POLICY.md`.

## Published-source / supplement / adventure resolution
- Structured rules authority/projection policy: `RULES_PROJECTION_POLICY.md`
- General specialist supplement resolver: `SUPPLEMENT_SOURCE_RESOLUTION_POLICY.md`
- **Automatic published adventure opportunity/seeding policy: `ADVENTURE_OPPORTUNITY_POLICY.md`**
- Published adventure source-family registry: `rules/adventures/INDEX.md`
- Monster source resolver: `MONSTER_SOURCE_RESOLUTION_POLICY.md`
- Monster projection/runtime policy: `MONSTER_PROJECTION_POLICY.md`
- Monster ecology inspiration compatibility policy: `MONSTER_ECOLOGY_INSPIRATION_POLICY.md`

Supplement routing:
`current domain -> active setting/adventure/campaign scope -> relevant specialist source role -> guidance/mechanics classification -> governing-source decision -> projection/cache or exact source`

Adventure routing:
`world need/opportunity -> current setting/region/site/thread facets -> targeted adventure-source families -> candidate fit review -> exact source inspection -> optional minimal seeding -> normal world causality`

Dungeon Magazine adventures and side treks are first-class adventure-source families. Automatic consultation/search is not automatic activation or canonization. Candidate and Prepared Possibility states create no world facts. Seed only the minimum facts actually required by current causality.

Active setting/adventure treatments must not be flattened by generic specialist/adventure sources, and setting-specific assumptions must not leak into unrelated generic play.

## Structured published-rules / source projections
- Rules registry: `rules/INDEX.md`
- Specialist source-role registry: `rules/sources/INDEX.md`
- Published adventure source registry: `rules/adventures/INDEX.md`
- Monster registry: `rules/monsters/INDEX.md`
- Monster ecology inspiration registry: `rules/monsters/ecology-inspiration/INDEX.md`
- Wilderness encounter checks: `rules/encounters/dmg-wilderness-encounter-checks.md`
- Ship weather: `rules/travel/dmg-ship-weather.md`

General runtime lookup:
`valid runtime cache -> applicable verified projection -> exact scope-resolved governing source -> broader targeted source search`

Monster runtime lookup:
`encounter-instance state -> scope-resolved monster projection -> exact scope-resolved monster source -> broader active monster-source-family search`

Adventure discovery fast path:
`cheap opportunity check -> existing seeded/active scenario? -> if needed targeted family search -> shortlist -> inspect only surviving candidates`

Projection/index absence never permits guessing. Projection/index presence never overrides governing source or establishes campaign truth.

## DM-only
- Hidden truths/prepared possibilities/outside forces: `state/dm/campaign.md`
- Home Coast active-world runtime: `state/dm/home-coast-world-runtime.md`

Do not expose DM-only records merely because they are loaded. Prepared adventure candidates/possibilities are DM-only and must not be narrated as established facts before seeding.

## Long-term scaffolds
- General templates: `STATE_TEMPLATES.md`
- Regional runtime templates: `REGIONAL_RUNTIME_TEMPLATES.md`

Instantiate records only when play/source causality makes them relevant.

## Context / DM craft / retrieval architecture
- Always-on DM craft: `DM_CRAFT_POLICY.md`
- Active-site runtime: `SITE_RUNTIME_POLICY.md`
- Monster projection/runtime: `MONSTER_PROJECTION_POLICY.md`
- Monster source resolver: `MONSTER_SOURCE_RESOLUTION_POLICY.md`
- Monster ecology inspiration filter: `MONSTER_ECOLOGY_INSPIRATION_POLICY.md`
- Specialist supplement resolver: `SUPPLEMENT_SOURCE_RESOLUTION_POLICY.md`
- **Published adventure opportunity/seeding: `ADVENTURE_OPPORTUNITY_POLICY.md`**
- Context compiler: `CONTEXT_ARCHITECTURE.md`
- Regional Voice/due-event extension: `CONTEXT_REGIONAL_RUNTIME_EXTENSION.md`
- Derived retrieval/index safety: `DERIVED_INDEX_POLICY.md`
- Structured rules projections: `RULES_PROJECTION_POLICY.md`
- Regional runtime/world motion: `REGIONAL_RUNTIME_POLICY.md`

Because this index is part of the always-loaded resume working set, resumed play automatically discovers both specialist-source and adventure-opportunity routing. Normal performance remains bounded: cheap domain/opportunity checks, reuse cached routes/projections/locators, and retrieve source text only when a trigger actually fires.

`ADVENTURE_OPPORTUNITY_POLICY.md` inherits `DM_CRAFT_POLICY.md` scenario-before-story. Published scenarios provide situations, places, actors, hazards, clues, and pressures; they never dictate Wren's choices, survival, required scenes, or ending.

## Regression / audit
- Regional runtime: `tests/REGIONAL_RUNTIME_REGRESSION.md`
- DM craft/site runtime: `tests/DM_CRAFT_AND_SITE_RUNTIME_REGRESSION.md`
- Monster projection/source resolution: `tests/MONSTER_PROJECTION_REGRESSION.md`
- Specialist supplement source resolution/performance: `tests/SUPPLEMENT_SOURCE_RESOLUTION_REGRESSION.md`
- **Automatic adventure discovery/seeding/Dungeon Magazine behavior: `tests/ADVENTURE_OPPORTUNITY_REGRESSION.md`**

These tests never alter live campaign state.

## Engineering
- Engineering/status: `CAMPAIGN_ENGINEERING.md`
- Application roadmap: `docs/APPLICATION_ROADMAP.md`
- DM runtime/unit economics: `docs/DM_RUNTIME_AND_UNIT_ECONOMICS.md`
- Competitive landscape: `docs/COMPETITIVE_LANDSCAPE.md`
- Asset/media architecture: `docs/ASSET_LIBRARY_ARCHITECTURE.md`

## Protocol
- Full bootstrap: `CAMPAIGN_BOOTSTRAP.md`
- State schema: `STATE_SCHEMA.md`
- Persistence: `PERSISTENCE_PROTOCOL.md`
- Growth/sharding: `GROWTH_POLICY.md`
- Root manifest/resume: `Wren_Campaign_Ledger.md`

Repository search is fallback for fuzzy references when explicit routing is insufficient. Derived retrieval may identify candidates, but canonical records and governing uploaded published sources remain authoritative.
