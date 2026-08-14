# Wren Campaign Context Architecture — v1

This file is a normative companion to `STATE_SCHEMA.md`. It defines how canonical campaign state, episodic history, compiled source knowledge, uploaded source material, recent conversation, and DM-only information are assembled into the bounded working context used for one adjudication, narration step, rules question, or Live Voice session.

It does not create a second source of truth. The compiled context is disposable and rebuildable.

## Core separation

Maintain these distinct layers:

1. **Canonical campaign state** — authoritative current campaign truth reconstructed from the materialized snapshot plus ordered checkpoints after `checkpoint_baseline`.
2. **Compiled source knowledge** — verified normalized published-source entities/assertions/procedures under `SOURCE_KNOWLEDGE_LAYER_POLICY.md`; derived from uploaded sources, not campaign truth.
3. **Episodic / retrieval material** — historical events, archived chronology, prior clues/interactions, source indexes, aliases, semantic candidates, and other retrieval context that helps identify authoritative campaign/source records but is not itself automatically authoritative.
4. **Uploaded source material** — ultimate authority for exact published rules/setting/adventure/source content.
5. **Compiled working context** — bounded, task-specific canonical state + relevant compiled source objects + relevant history + exact source excerpts when needed + recent conversation + operational instructions.

Never promote a retrieved historical summary, semantic match, conversation fragment, unverified extraction, or derived index entry into established authority beyond the layer that governs it.

Campaign facts resolve to canonical campaign state. Exact published facts resolve ultimately to Hiram's uploaded source corpus. A verified compiled source assertion may be used directly when its scope, verification, and exception flags make it sufficient; otherwise it routes to the exact uploaded source locator.

## Context Compiler

Treat context assembly as an explicit subsystem:

`Canonical Campaign State + Verified Compiled Source Objects + Retrieval/Indexes + Uploaded Source Material + Recent Conversation + Task Intent -> Context Compiler -> Disposable Turn/Voice Context`

The compiler optimizes for correctness first, then relevance, locality, compactness, latency, and retrieval cost.

## Event-driven procedure routing

Normal play must use event-driven, opt-in procedure routing rather than scanning or executing every available DM procedure/source family on every turn.

For each player utterance, state transition, or elapsed-time step:

1. classify the small set of event/procedure/source domains actually implicated;
2. evaluate only procedures whose trigger conditions could plausibly be affected;
3. do not load unrelated canonical shards, compiled source objects, sourcebooks, magazines, or procedure detail merely as a precaution;
4. use already-valid cached/derived state for fast-path checks when available;
5. when published information is required, prefer verified compiled source entities/assertions/projections before opening source PDFs;
6. escalate to exact uploaded source only when the compiled object is absent, stale, unverified, scope-uncertain, exception-sensitive, or marked `source_text_required`;
7. broaden source search only when no reliable entity/assertion/locator exists;
8. return to adjudication/narration without running unrelated background checks.

Examples:
- looking under a bed does not activate XP, encumbrance, travel, Dragon, World Builder, or broad source-search procedures;
- picking up a heavy object may activate inventory/encumbrance handling and use the verified PHB encumbrance source object;
- casting Armor may use the verified Armor spell object unless an unusual interaction requires exact source wording;
- declaring a multi-day journey may activate travel plus declared-action readiness and applicable regional/weather/encounter projections;
- receiving XP activates XP-threshold/advancement handling and uses the verified current class progression object;
- advancing time activates only clocks/effects/resources/projects/encounter schedules whose due triggers can be crossed.

The existence of a procedure, source family, compiled object, or article index is never itself a reason to execute/load it.

### Fast-path versus slow-path

Preferred runtime:

`utterance/event -> cheap routing -> valid runtime cache / canonical immediate state -> verified compiled source object if needed -> adjudicate/respond`

When exact source nuance is necessary:

`implicated domain -> compiled object locator/flags -> exact source section -> adjudicate -> refresh/compile if reusable`

Broad source search is last resort when the governing entity/source location is unknown.

Routine turns should normally stay on the fast path. Growth in procedures, source corpus size, or compiled-object count must not linearly increase per-turn work.

## Published-source lookup

Follow `SOURCE_KNOWLEDGE_LAYER_POLICY.md`, `SOURCE_KNOWLEDGE_SCHEMA.md`, `RULES_PROJECTION_POLICY.md`, and source-family policies.

For source-dependent questions prefer:

1. valid runtime cache when sufficient;
2. verified compiled source entity/assertion or existing structured projection from the active governing scope;
3. exact uploaded-source entry/section referenced by the compiled object;
4. targeted source-family search when entity/locator is missing;
5. broad source search only when necessary.

Compiled-object existence does not activate supplements, Dragon optional rules, settings, or variants. Scope/precedence still resolves before use.

A correct exact-source lookup that reveals reusable structured material may be compiled/queued after adjudication so future turns avoid repeating the same search.

## Rules dependency routing

For mechanical state changes, use `state/rulings/rules-dependency-registry.md`.

A change such as class, level, alignment, race/species, kit, ability score, equipment, spell state, magic-item use, campaign option, or source activation should first identify only affected rule/source entities and downstream caches.

Prefer an existing verified compiled assertion/projection. Create/queue new compiled material only when the normalized representation is reliable and reuse value justifies it. A missing compiled object never blocks gameplay if the authoritative source can be retrieved.

## Default priority order

As applicable, compile in this order:

1. mandatory campaign operating/persistence/growth/context/source-authority invariants;
2. Wren's core identity anchors plus immediate mechanical/resource state;
3. exact current chronology and location/scene;
4. currently present or immediately relevant NPCs, creatures, items, locations, factions, clues, projects, and clocks;
5. active threads/objectives whose consequences can affect the task;
6. DM-only truth/preparation required to adjudicate the immediate situation;
7. specifically mentioned off-scene entities resolved through canonical routing;
8. relevant episodic/history records retrieved for the current reference/decision;
9. exact verified compiled source objects/projection fields needed for rules, monsters, items, setting, adventure, World Builder, Dragon, or other source-dependent adjudication;
10. exact source excerpts only where compiled coverage is insufficient or wording/exception context matters;
11. recent conversational context needed to preserve the current exchange and pending transaction state.

Do not load material merely because it exists.

## Player-character identity anchors

The narration/roleplay and Live Voice contexts must always include a compact player-character identity block sourced from canonical character state, even when the full character record is not otherwise needed.

For Wren, current minimum identity anchors are:
- name: Wren;
- sex/gender: male;
- pronouns: he/him;
- age: 19;
- class/level: mage 1.

If any anchor changes canonically, regenerate it from canonical state rather than retaining a stale copy.

## Task-specific context

### Narration / roleplay
Prioritize current scene/location, present entities, relevant motives/knowledge, chronology, dangers/clocks, required DM preparation, recent conversation, and only the mechanics/source objects necessary for plausible adjudication.

### Mechanical adjudication
Prioritize exact character/creature state, conditions/resources, verified compiled rule/spell/item/monster objects, environmental modifiers, and secret mechanics. Escalate to exact source only for missing/exception-sensitive content.

### Canonical state update / checkpoint preparation
Prioritize pending delta register, verified canonical base/head, affected domains, knowledge boundaries, current resume, and durable changes. Compiled source-layer maintenance is not campaign-state change unless it also changes a campaign rules activation/ruling or world fact.

### Canonical fact retrieval
Prioritize explicit campaign routes/indexes and authoritative state files. Use episodic/semantic retrieval only to identify candidate records when a reference is fuzzy.

### Source fact retrieval
Prioritize stable source entity/assertion IDs and source-knowledge registry. Use relationship/domain/alias indexes next; exact source locator afterward; broad PDF/source search last.

### Live Voice preload
Before Voice, compile a practical working set broad enough for likely immediate play: Wren identity/immediate state, current scene/region, active threads, likely NPC/location/faction interactions, relevant clocks, required DM-only preparation, and source/rules material likely to be needed soon.

For latency-sensitive play, also preload a compact fast-path block including as applicable:
- current HP/AC/movement/combat values;
- memorized/available spell state;
- accessible consumables;
- encumbrance category and next breakpoint;
- XP and next-level threshold;
- active effects and lifecycle triggers;
- next relevant clocks/due events;
- small verified compiled source objects/fields likely to be queried repeatedly.

Examples for current Wren include the applicable wizard XP threshold, level-1 slot row, wizard THAC0 row, STR 9 encumbrance breakpoint, and Armor spell fields.

Do not preload whole source-object libraries, books, magazines, or adventure corpora.

During Voice, use loaded verified compiled objects directly when sufficient. If a source-governed exact fact is required but absent and retrieval is unavailable, preserve the pending lookup rather than guessing.

## Locality and relevance

Prefer information physically, temporally, causally, socially, mechanically, or source-semantically close to the current situation.

Useful signals include:
- present in current scene;
- adjacent/reachable within active horizon;
- explicitly named or naturally referenced by Hiram;
- linked to active thread/clue/clock/faction/adventure;
- recently interacted with and consequential;
- needed by governing rule/source procedure;
- scheduled to act within likely time horizon;
- exact entity/subject match in compiled source knowledge;
- necessary to preserve knowledge/secret/source-scope boundary.

Relevance ranking never overrides explicit canonical/source dependencies.

## Bounded context behavior

The campaign repository and compiled source corpus may grow without bound; normal working context should not.

When context pressure grows:
1. keep invariants, identity anchors, and immediate state;
2. prefer concise authoritative current-state records over history;
3. replace broad history with targeted episodic retrieval;
4. use direct campaign/source entity IDs instead of loading domain indexes wholesale;
5. load only exact compiled fields/assertions or source excerpts needed;
6. avoid duplicating a compiled object and its source excerpt unless verification/exception context requires both;
7. split mature state/object stores according to growth policy rather than expanding startup packets.

## Provenance

Every nontrivial compiled fact/rule should remain traceable to its authority category:
- canonical campaign state path/checkpoint;
- verified compiled source entity/assertion with uploaded-source provenance;
- exact uploaded published source/reference;
- recent same-conversation pending state;
- derived/retrieval candidate requiring authority resolution.

A future Context Inspector should expose which layer supplied a value and why escalation occurred.

## Context Inspector target

Future application observability should show, with DM/player filtering:
- canonical files/entities loaded;
- episodic memories retrieved;
- compiled source entities/assertions used;
- exact published/source excerpts retrieved;
- source-text-required escalations;
- why each item was selected;
- context/token budget by category;
- snapshot/checkpoint/source-object versions;
- omitted/compressed material.

Inspector output is never authority itself.

## Failure behavior

If an established campaign fact cannot be resolved, follow canonical retrieval escalation and preserve ambiguity rather than inventing it.

If a source-dependent fact cannot be resolved:
1. use valid runtime cache if sufficient;
2. use verified in-scope compiled source assertion/projection if sufficient;
3. retrieve its exact uploaded-source locator;
4. targeted/broader source search only if locator is unknown;
5. preserve uncertainty rather than inventing source content.

During Voice, follow deferred-lookup rules when required tools are unavailable.

## Maintenance interaction

Every maintenance run should evaluate:
- whether working-set manifests remain bounded;
- whether repeated source lookups justify additional compiled objects;
- whether compiled objects need verification/invalidation/re-sharding;
- whether source relationships/indexes would materially reduce search;
- whether new regional/adventure/Voice packets improve compilation;
- whether broad PDF scans are still occurring for already-reusable entities.

When routing/storage is reorganized, preserve stable semantic IDs/provenance so the Context Compiler resolves the same campaign/source meaning after compaction, migration, or index rebuild.
