# Wren Regional Runtime Templates — v1

This normative companion to `STATE_TEMPLATES.md` defines reusable structures for regional activation, world-motion entities/processes, encounter derivation, weather state, and information-reliability records under `REGIONAL_RUNTIME_POLICY.md`.

Instantiate only what current play/source causality requires. Missing optional detail is preferable to invented precision.

## Regional runtime profile template

Use when a region crosses the activation horizon.

Track as applicable:
- stable region id/name and aliases;
- activation state: latent / active;
- player-known versus DM-only boundaries;
- established geographic anchors and explicit uncertainties;
- terrain/environment zones;
- settlement/population density assumptions;
- travel modes and route classes;
- climate baseline and current season status;
- weather procedure/source and current continuing weather state;
- navigation/getting-lost relevance;
- supply/readiness relevance;
- encounter-check applicability and governing projection/source;
- encounter ingredients/table references;
- active actors/populations/processes capable of modifying the region;
- lore substrate Wren reasonably knows;
- unresolved lore/geography intentionally deferred;
- dependent derived artifacts that must refresh after state change.

Do not let a player-facing map or decorative asset establish exact geography, travel time, population, history, or route relationships unless separately canonicalized.

## Active-world element template

Use for a faction, significant NPC project, organized group, monster population, migration, disease, trade pressure, supernatural force, environmental process, or similar element capable of independently changing consequential state.

Track as applicable:
- stable id/name/type;
- state: latent / active;
- authority/provenance: campaign-generated / published source / adventure / consequence;
- current location/reach;
- goals or governing process;
- resources/capabilities;
- pressures/constraints;
- known information and blind spots for intelligent actors;
- possible transition/action classes when useful;
- next reevaluation trigger: time, condition, event, threshold, or dependency;
- repeat cadence if any;
- immediate/event-driven triggers;
- affected regions/entities;
- downstream dependencies: encounter content, rumor state, routes, economy, ecology, weather, faction awareness, clues, etc.;
- player-known versus DM-only state;
- latest resolved action/state transition;
- next trigger after resolution if still active.

If an element cannot independently change consequential state, keep it latent/simple rather than adding a clock merely for completeness.

## Population / ecology process template

Use when a creature or mundane population materially affects regional state beyond a single encounter.

Track as applicable:
- population/group identity;
- current range and density category;
- habitat/resource needs;
- predators/prey/rivals/competitors;
- migration/displacement pressures;
- reproduction/depletion or seasonal behavior only when consequential;
- interaction with settlements/routes/factions;
- encounter eligibility/weight dependencies;
- reevaluation cadence/trigger;
- source/monster provenance;
- current player knowledge.

Do not instantiate a hostile population solely to provide combat.

## Environmental process template

Use for weather systems, storms, floods, fires, disease, tides when stateful, magical environmental effects, seasonal changes, or other non-intelligent processes that can propagate consequences.

Track as applicable:
- process identity/type;
- current state/intensity/reach;
- governing source or established causal model;
- start/last-change time;
- next reevaluation/ending/phase trigger;
- possible transitions bounded by current conditions;
- affected travel/navigation/visibility/exposure/encounter/resource domains;
- downstream regions/entities;
- observable evidence and resulting rumor channels;
- whether exact underlying cause is Established DM Truth, Prepared Possibility, or Open Question.

Do not force every environmental process into a fixed duration if its governing trigger is event/threshold based.

## Encounter-content template

Encounter content is a derived regional artifact, not primary authority for population existence.

Track as applicable:
- region/zone;
- governing occurrence-check projection/source;
- table/ingredient version or preparation timestamp;
- terrain/time/weather/season scope;
- ordinary social traffic;
- mundane ecology/wildlife;
- active faction/population entries;
- source/adventure/keyed entries;
- special/one-use entries and exhaustion state;
- dynamic weights/modifiers and their canonical causes;
- dependencies that invalidate/refresh this content;
- encounter distance/surprise/reaction/morale source routes.

Before rolling from newly generated encounter content, define the eligible entries/distribution first. Do not choose the encounter after seeing the occurrence roll.

## Weather-state template

Use only when weather is consequential or continuing.

Track as applicable:
- region/route/water area;
- climate/season basis;
- current conditions;
- start/last reevaluation;
- next reevaluation/ending trigger;
- movement/visibility/navigation/exposure/encounter consequences;
- boat/ship effects if applicable;
- source/projection used;
- affected active-world elements/events.

Inconsequential descriptive weather need not become a durable daily record.

## Consequential claim / belief template

Use with `state/rulings/knowledge-reliability-and-rumors.md` when a specific report, belief, rumor, memory, accusation, interpretation, or lie becomes durable.

Track as applicable:
- claim id/content;
- speaker/source;
- information access/basis;
- relevant expertise/limitations;
- speaker belief state;
- communicative intent;
- confidence if relevant;
- objective truth relation: accurate / partial / wrong explanation / outdated / distorted / mistaken / deliberate fabrication / unresolved;
- linked Established DM Truth if already fixed;
- distortion/error origin;
- who heard/knows/believes it;
- Wren's epistemic category for it;
- contradictions/retractions/superseding evidence;
- resolution status.

Truth relation may remain unresolved until a clue/action/clock/causal dependency requires the answer. Before a consequential dependent result is presented, establish the minimum required hidden truth first.

## Activation-horizon promotion check

Whenever a new entity/process/place is established or changes materially, ask:

1. Can it affect Wren's current/known-play area within a plausible active time/causal horizon?
2. Can it independently change consequential state later?
3. Does a current route/thread/adventure/source connect it to likely play?

If no, keep it latent/minimal.

If yes, promote only the necessary state, assign explicit reevaluation triggers, connect downstream dependencies, and route it into the regional runtime profile/DM event frontier.

## Due-event frontier template

The Context Compiler/Voice preload may derive a compact disposable frontier from active canonical state:
- event/actor id;
- next trigger relative to current chronology;
- trigger type;
- affected domain/region;
- whether deterministic, source-governed, or may require secret branching roll;
- canonical source path.

The frontier is derived routing metadata, not authority. Rebuild it whenever chronology or an active element's trigger changes.
