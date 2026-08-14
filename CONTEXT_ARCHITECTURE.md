# Wren Campaign Context Architecture — v1

This file is a normative companion to `STATE_SCHEMA.md`. It defines how canonical campaign state, episodic history, source material, recent conversation, and DM-only information are assembled into the bounded working context used for one adjudication, narration step, rules question, or Live Voice session.

It does not create a second source of truth. The compiled context is disposable and rebuildable.

## Core separation

Maintain three distinct layers:

1. **Canonical state** — authoritative current campaign truth reconstructed from the materialized snapshot plus ordered checkpoints after `checkpoint_baseline`.
2. **Episodic / retrieval material** — historical events, archived chronology, prior clues/interactions, and other retrievable context that may help identify relevant canonical records but is not itself automatically authoritative current truth.
3. **Compiled working context** — the bounded, task-specific set of canonical state, relevant history, source material, structured source-derived rules projections, recent conversation, and operational instructions supplied to the DM for the current task.

Never promote a retrieved historical summary, semantic match, conversation fragment, or derived projection into established authority beyond the layer that governs it. Campaign facts resolve to canonical campaign state; exact published rules resolve ultimately to Hiram's uploaded source material.

## Context Compiler

Treat context assembly as an explicit subsystem:

`Canonical State + Retrieval + Source Material + Structured Rules Projections + Recent Conversation + Task Intent -> Context Compiler -> Disposable Turn/Voice Context`

The compiler should optimize for correctness first, then relevance, locality, compactness, latency, and retrieval cost.

## Event-driven procedure routing

Normal play must use event-driven, opt-in procedure routing rather than scanning or executing every available DM procedure on every turn.

For each player utterance, state transition, or elapsed-time step:

1. classify the small set of event/procedure domains actually implicated by the action or change;
2. evaluate only those procedures whose trigger conditions could plausibly be affected;
3. do not load source material, canonical shards, structured rule projections, or unrelated procedure detail merely as a precaution;
4. use already-valid cached/derived state for fast-path checks when available;
5. escalate through the structured-rules lookup path only when the implicated procedure requires information that is missing, stale, invalidated, uncertain, or newly consequential;
6. after resolving the implicated procedures, return to narration/adjudication without running unrelated background checks.

Examples:
- looking under a bed does not activate XP, encumbrance, travel, or depletion procedures;
- picking up a heavy object may activate inventory/encumbrance handling;
- casting a spell may activate spell-resource and active-effect lifecycle handling;
- declaring a multi-day journey may activate travel plus declared-action readiness;
- receiving XP activates XP-threshold/advancement handling;
- advancing time activates only clocks, active effects, resources, projects, encounter schedules, or other due-event domains whose registered triggers could be crossed.

The existence of a procedure in `state/rulings/dm-procedure-triggers.md` is not itself a reason to execute it. Procedures are dormant until routed by a relevant event or dependency change.

### Fast-path versus slow-path

Prefer a two-stage runtime pattern:

`utterance/event -> cheap routing + valid cached checks -> adjudicate/respond`

When a rule value must be refreshed or obtained, prefer:

`implicated domain -> valid structured rule projection -> adjudicate/refresh cache`

Use the slower source path only when necessary:

`implicated domain -> missing/invalid/incomplete projection or exception-sensitive interaction -> exact cited uploaded source -> adjudicate/refresh projection or cache`

Use broader source search only when the exact governing source location is not yet known.

Routine turns should normally stay on the fast path. Increasing the number of available procedures or structured projections must not linearly increase per-turn work.

## Structured published-rules lookup

Follow `RULES_PROJECTION_POLICY.md` and `state/rulings/rules-dependency-registry.md`.

For exact rules/mechanics, the runtime preference order is:

1. valid already-loaded runtime cache;
2. applicable verified structured rules projection;
3. exact cited uploaded source section/entry;
4. broader uploaded-source search.

A state change such as class, level, alignment, race/species, kit, ability score, equipment, spell state, magic-item use, campaign option, or sourcebook activation should first route through the dependency registry. Activate/create only the projections actually implicated by that change and refresh only downstream caches that depend on them.

A missing projection does not block gameplay. Retrieve the governing source, adjudicate correctly, and create/queue a projection automatically only when the rule satisfies the creation criteria in `RULES_PROJECTION_POLICY.md`.

## Default priority order

As applicable, compile in this order:

1. mandatory campaign operating/persistence/growth/context/rules-projection invariants;
2. Wren's core identity anchors plus immediate mechanical/resource state;
3. exact current chronology and location/scene;
4. currently present or immediately relevant NPCs, creatures, items, locations, factions, clues, projects, and clocks;
5. active threads/objectives whose consequences can affect the current task;
6. DM-only truth/preparation required to adjudicate the immediate situation;
7. specifically mentioned off-scene entities resolved through canonical routing;
8. relevant episodic/history records retrieved for the current reference or decision;
9. exact structured rule rows/fields or uploaded-source excerpts required for rules, adventure, map, monster, item, or setting adjudication;
10. recent conversational context needed to preserve the current exchange and pending transaction state.

Do not load material merely because it exists.

## Player-character identity anchors

The compiled narration/roleplay and Live Voice contexts must always include a compact player-character identity block sourced from canonical character state, even when the full character record is not otherwise needed.

For Wren, the current minimum identity anchors are:

- name: Wren;
- sex/gender: male;
- pronouns: he/him;
- age: 19;
- class/level: mage 1.

These anchors are small correctness-critical facts and should not be dropped merely to save context. If any identity anchor later changes canonically, the compiled block must be regenerated from canonical state rather than retaining a stale copy.

This pattern should generalize to future player characters: include the smallest stable identity facts needed to prevent narration drift while keeping the full character record separately authoritative.

## Task-specific context

Different operations should receive different context slices.

### Narration / roleplay

Always include the player-character identity anchors. Prioritize scene/location state, present entities, relevant personalities/knowledge/motives, current chronology, active dangers/clocks, applicable DM preparation, recent conversation, and only the mechanical state needed for plausible narration/adjudication.

### Mechanical adjudication

Prioritize exact character/creature mechanics, conditions/resources, applicable structured rule rows/fields, governing source material when projection coverage is insufficient, encounter state, relevant environmental modifiers, and secret DM mechanics. Avoid unrelated lore/history.

### Canonical state update / checkpoint preparation

Prioritize the structured pending delta register, verified canonical base/head, affected state domains, knowledge boundaries, current resume state, and exact durable changes. Narrative flavor that does not alter durable state should not dominate save context.

### Canonical fact retrieval

Prioritize explicit routes/indexes and authoritative entity files. Use episodic/semantic retrieval only to identify candidate records when the reference is fuzzy.

### Live Voice preload

Before Voice, compile a practical working set broad enough for likely immediate play: Wren's core identity anchors, immediate state, current scene/region, active threads, likely NPC/location/faction interactions, relevant clocks, required DM-only preparation, and any source/rules material likely to be needed soon.

For latency-sensitive Voice play, also preload a compact **fast-path runtime block** containing the small, frequently consulted state that can prevent routine external retrieval. As applicable, this includes current HP/AC/movement and other immediate combat values, memorized/available spell state, current carried/accessible consumables, current encumbrance category and next breakpoint, current XP and next-level threshold, active conditions/effects with their registered lifecycle triggers, and the next immediately relevant clocks/due events.

Where likely play will need a deterministic published rule, preload only the compact applicable structured projection row/fields rather than the entire sourcebook or entire projection library. Examples might include the current class progression row, current save/THAC0 range, relevant encumbrance breakpoint, weapon fields, or an active item's lifecycle fields.

This fast-path block is derived from canonical state and source-derived rules projections and is disposable, not a second source of truth. It should contain values already needed or likely to be checked repeatedly, not broad speculative rules/lore. Refresh only the affected entries when their dependencies change.

During Voice, a routine turn should first route against this loaded working set. Do not perform or defer a canonical/source lookup merely because a procedure exists if the needed valid state/projection is already loaded and no dependency/threshold requires escalation. If an established fact or exact rule genuinely required for correctness is absent and tools are unavailable, follow the deferred-lookup rule rather than guessing.

When `GROWTH_POLICY.md` calls for a Voice working-set packet, use it as routing metadata to compile this context; the packet remains non-authoritative.

## Locality and relevance

Prefer information physically, temporally, causally, or socially close to the current situation.

Useful relevance signals include:

- present in the current location/scene;
- adjacent or reachable within the active travel/exploration horizon;
- explicitly named or naturally referenced by Hiram;
- linked to an active thread, clue, obligation, clock, faction, or adventure;
- recently interacted with and still consequential;
- needed by a governing rule or source procedure;
- scheduled to act before or during the likely time horizon;
- necessary to preserve an established knowledge boundary or secret causal chain.

Relevance ranking must not override explicit canonical/source dependencies. If a fact or exact rule is required for correctness, retrieve it even if semantic/locality ranking scores it low.

## Bounded context behavior

The campaign repository and rules projection library may grow without bound; the normal working context should not.

When context pressure grows:

1. keep invariants, player-character identity anchors, and immediate state;
2. prefer authoritative concise current-state records over long history;
3. replace broad history with targeted episodic retrieval;
4. load entity files by direct route instead of entire domain indexes when possible;
5. load only the exact structured projection rows/fields or exact source sections needed for the adjudication;
6. split mature state according to `GROWTH_POLICY.md` rather than accepting an indefinitely expanding startup packet.

If required context cannot be assembled reliably within practical limits, growth-driven maintenance may be recommended or required according to `GROWTH_POLICY.md`.

## Provenance

Every nontrivial compiled fact/rule should remain traceable to its authority category:

- canonical campaign state path/checkpoint;
- verified structured rules projection with uploaded-source provenance;
- uploaded published source/reference;
- recent same-conversation pending state;
- derived/retrieval candidate requiring canonical resolution.

A future application may expose this provenance through a Context Inspector. The current ChatGPT implementation need not display routine DM-only context/provenance to Hiram, but must preserve the distinction internally.

## Context Inspector target

For future application development, retain the architectural ability to expose a debug view showing, with DM/player visibility filtering:

- which canonical files/entities were loaded;
- which episodic memories were retrieved;
- which structured rule projections/rows were used;
- which published/source excerpts were retrieved;
- why each item was selected;
- token/context budget by category;
- current snapshot/checkpoint/transaction identifiers;
- which material was omitted or compressed due to context constraints.

This is observability, not authority. Editing the inspector output must never directly mutate canonical state or published-rule authority.

## Failure behavior

If the compiler cannot resolve a referenced established fact:

1. follow the canonical retrieval escalation in `STATE_SCHEMA.md`;
2. use derived retrieval/index candidates where available;
3. resolve candidates back to canonical records;
4. if canonical retrieval still cannot establish the answer, preserve the ambiguity rather than inventing a fact.

If the compiler cannot resolve a required exact rule:

1. use a valid runtime cache if sufficient;
2. use the applicable verified structured projection if sufficient;
3. retrieve the exact uploaded source entry/section;
4. broaden source search only if the governing source location is unknown;
5. preserve uncertainty rather than inventing a rule if authority cannot be established.

During Live Voice, follow the deferred-lookup rule when required tools are unavailable.

## Maintenance interaction

Every maintenance run should evaluate whether current working-set manifests remain bounded, whether repeated source lookups justify new structured rules projections, and whether new regional/adventure/Voice routing packets would materially improve compilation.

When state or projection routing is reorganized, update canonical/source routing and working-set references so the compiler continues to resolve the same semantic truth and governing rules after sharding/archival/rebuild.
