# Wren Campaign Checkpoint — Regional Runtime Foundation

- sequence: 000006
- transaction-id: wren-tx-20260814T151925Z-7c4e2a91
- kind: campaign-configuration
- state-change: real
- schema-version: 1
- persistence-protocol-version: 1
- snapshot-generation: 1
- checkpoint-baseline-observed: 1
- base-root-blob-sha: 65c1201636503cade706f7ba19415ae0054120f1
- parent-checkpoint-sequence: 000005
- parent-checkpoint-blob-sha: 56d71cd480b0d766205e6ae59bde81c1f71e546b
- affected-domains: locations/regional-runtime, encounters, weather, lore/knowledge reliability, DM world-motion, world clocks/events, rulings/procedures, structured-rules projections, routing indexes

## chronology_location

- No gameplay action or additional in-world time is advanced by this checkpoint.
- Resume remains the morning after checkpoint 000005 at Wren's family home in Lowcove; exact campaign date/time remains unestablished.
- This checkpoint establishes runtime scaffolding around already-established Home Coast geography without changing Wren's physical location.

## locations_factions_world

- Establish `state/locations/home-coast/runtime-profile.md` as the canonical operational regional substrate for currently known/nearby Home Coast play.
- Establish a **temperate maritime/coastal** Home Coast operational climate baseline, with season still unestablished until chronology/source play fixes it.
- Establish bounded runtime zones for Lowcove/immediate settled shore, inland/Bridgefordward travel, Bridgeford, Saltwick/harbor approaches, remote coast/coves, coastal waters/open sea, and eastern-hills/observatory approaches.
- These zones are procedure-routing categories, not new exact cartographic boundaries.
- Preserve checkpoint 000005's geography boundary: Bridgeford's exact distance/route, Wren's personal travel history there, and detailed relationship to other features remain unestablished.
- Preserve map-asset boundary: player-facing map labels do not independently establish detailed geography, travel times, population, lore, or route relationships.
- The coastal inlet/three-worked-stones site from checkpoint 000004 is included in the remote-coast activation horizon but retains its previously established exact facts and unresolved geography.

## rulings_sources

- Add normative `REGIONAL_RUNTIME_POLICY.md` governing regional activation horizons, latent/active world elements, event-driven world motion, encounter derivation, weather relevance, progressive lore generation, epistemic categories, and dependency propagation.
- Add mandatory trigger extension `state/rulings/regional-runtime-triggers.md` so region activation, world-element creation, due-event processing, encounter-table preparation/refresh, weather, lore generation, and information reliability are automatically recognized rather than dependent on DM recollection.
- Add `state/rulings/knowledge-reliability-and-rumors.md` separating information access, speaker belief, communicative intent, objective truth relation, hidden weighted randomness, and deferred truth assignment.
- Rumors/beliefs may be accurate, partly accurate, distorted, outdated, mistaken, deliberately deceptive, or unresolved; do not retroactively choose truth status for dramatic convenience.
- Random encounters are not a pacing quota for combat. No procedure triggers merely because Wren has not fought recently.
- Valid dangerous results are not suppressed merely because Wren is low level; normal source/world-state reaction, morale, distance, avoidance, and consequences apply.

### Core source-derived projections created

- `adnd2e.dmg.encounters.wilderness-checks.v1` in `rules/encounters/dmg-wilderness-encounter-checks.md`, verified from core AD&D 2e DMG Chapter 11 / Table 56.
  - Records encounter check slots and 1d10 chance by wilderness terrain.
  - Separates occurrence frequency/chance from local encounter content.
  - Preserves DMG condition that settled/patrolled chance modifiers require specially prepared settled-land encounter tables.
- `adnd2e.dmg.travel.ship-weather.v1` in `rules/travel/dmg-ship-weather.md`, verified from core AD&D 2e DMG Chapter 14 / Tables 78–79.
  - Records daily seasonal ship-weather generation and sailing/rowing movement effects.
  - Does not serve as a complete regional climate generator.
- Uploaded supplements remain subject to `RULES_PROJECTION_POLICY.md`: availability/projection existence does not activate a supplement or allow it to supersede core rules without explicit approved scope.

## dm_truth_preparation

- Establish `state/dm/home-coast-world-runtime.md` as the DM-only active-world runtime for the current Home Coast activation horizon.
- Reuse rather than duplicate already-established hidden forces: coastal magical phenomenon, mentor's private inquiry, outside seekers, and local community pressures.
- No new goblin/bandit/pirate/wolf/other hostile population is established merely to populate encounters. Absence from this runtime is not proof such populations do not exist; their presence remains unestablished until valid source/activation/encounter/clue causality determines it.
- Consequential off-screen regional change must arise from established actors/processes, ecology/environment, source/adventure timelines, predeclared random world procedures, or consequences of established events—not from a desire to create drama/combat.
- Active world elements must have explicit reevaluation triggers; latent elements are promoted automatically when causal relevance crosses the activation horizon.

## world_clocks_events

Relative anchors use the current resume morning after checkpoint 000005 as `runtime-anchor day 0`; no exact calendar date is invented.

- Coastal magical phenomenon: next scheduled reevaluation at **runtime-anchor +3 in-world days**, then every 3 days while current low/intermittent phase and Home Coast activation remain applicable, with immediate event-triggered reevaluation when established causes require it.
- Mentor's private inquiry: next scheduled reevaluation at **runtime-anchor +3 in-world days**, then every 3 days while active, plus immediate clue/relationship/rival-information triggers.
- Outside seekers: next scheduled reevaluation at **runtime-anchor +7 in-world days** while distant; cadence becomes every 3 days only after established state places them within practical Home Coast influence, with immediate major-information/resource/awareness triggers.
- Local community pressures: next periodic reevaluation at **runtime-anchor +7 in-world days** while relevant unusual/economic pressure exists, plus immediate public-incident/rumor/disruption triggers.
- Weather: no unused current daily weather roll is created by this configuration checkpoint. Consequential sea travel uses the core ship-weather projection; consequential overland/coastal travel generates/preserves weather consistent with the regional climate/season and registers continuing weather triggers when needed.
- When a due trigger is crossed, resolve only that actor/process and propagate only actual dependent state; do not scan all world systems every turn.

## threads_clues_knowledge

- Existing clues/threads from checkpoints 000004–000005 remain unchanged.
- Future consequential NPC reports/rumors/beliefs use the new knowledge-reliability procedure and retain explicit epistemic status.
- Underlying truth may remain unresolved when no clue/action/clock depends on it; before a consequential clue depends on an unresolved hidden answer, establish and persist the minimum necessary Established DM Truth first.

## resume_state

- Gameplay resume is unchanged from checkpoint 000005: morning at Wren's family home in Lowcove.
- Runtime infrastructure now exists to determine automatically when Home Coast weather, travel, encounter, lore/reliability, faction/population, and off-screen world-motion procedures become active.
- During future Live Voice preparation in this region, load the Home Coast regional runtime and relevant DM-only world runtime/due triggers alongside Wren's immediate state.

## unresolved_pending

- Exact wider published campaign setting remains unestablished.
- Exact current season/date/time remains unestablished.
- Detailed Bridgeford geography/route/travel time and Wren's personal familiarity remain unestablished.
- Full local encounter tables are intentionally not pre-generated. Create them before the first applicable check in a zone, from then-current ecology/social traffic/active actors/source material, and preserve them if repeated use warrants it.
- Deeper Home Coast history, religion, authorities, politics, ecology, and monster populations remain progressively generated rather than silently fixed by this checkpoint.

## dirty_domains

- REGIONAL_RUNTIME_POLICY.md
- RULES_PROJECTION_POLICY.md (dependency only; no semantic change in this transaction)
- rules/INDEX.md
- rules/encounters/dmg-wilderness-encounter-checks.md
- rules/travel/dmg-ship-weather.md
- state/INDEX.md
- state/locations/index.md
- state/locations/home-coast/runtime-profile.md
- state/rulings/regional-runtime-triggers.md
- state/rulings/knowledge-reliability-and-rumors.md
- state/dm/home-coast-world-runtime.md
- future chronology/world-clock compaction should preserve the relative runtime-anchor schedule