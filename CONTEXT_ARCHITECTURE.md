# Wren Campaign Context Architecture — v1

This file is a normative companion to `STATE_SCHEMA.md`. It defines how canonical campaign state, episodic history, source material, recent conversation, and DM-only information are assembled into the bounded working context used for one adjudication, narration step, rules question, or Live Voice session.

It does not create a second source of truth. The compiled context is disposable and rebuildable.

## Core separation

Maintain three distinct layers:

1. **Canonical state** — authoritative current campaign truth reconstructed from the materialized snapshot plus ordered checkpoints after `checkpoint_baseline`.
2. **Episodic / retrieval material** — historical events, archived chronology, prior clues/interactions, and other retrievable context that may help identify relevant canonical records but is not itself automatically authoritative current truth.
3. **Compiled working context** — the bounded, task-specific set of canonical state, relevant history, source material, recent conversation, and operational instructions supplied to the DM for the current task.

Never promote a retrieved historical summary, semantic match, or conversation fragment into established truth without resolving it back to canonical authority.

## Context Compiler

Treat context assembly as an explicit subsystem:

`Canonical State + Retrieval + Source Material + Recent Conversation + Task Intent -> Context Compiler -> Disposable Turn/Voice Context`

The compiler should optimize for correctness first, then relevance, locality, compactness, and retrieval cost.

### Default priority order

As applicable, compile in this order:

1. mandatory campaign operating/persistence/growth/context invariants;
2. Wren's immediate mechanical/resource state;
3. exact current chronology and location/scene;
4. currently present or immediately relevant NPCs, creatures, items, locations, factions, clues, projects, and clocks;
5. active threads/objectives whose consequences can affect the current task;
6. DM-only truth/preparation required to adjudicate the immediate situation;
7. specifically mentioned off-scene entities resolved through canonical routing;
8. relevant episodic/history records retrieved for the current reference or decision;
9. exact published/source excerpts required for rules, adventure, map, monster, item, or setting adjudication;
10. recent conversational context needed to preserve the current exchange and pending transaction state.

Do not load material merely because it exists.

## Task-specific context

Different operations should receive different context slices.

### Narration / roleplay

Prioritize scene/location state, present entities, relevant personalities/knowledge/motives, current chronology, active dangers/clocks, applicable DM preparation, recent conversation, and only the mechanical state needed for plausible narration/adjudication.

### Mechanical adjudication

Prioritize exact character/creature mechanics, conditions/resources, governing rules/source material, encounter state, relevant environmental modifiers, and secret DM mechanics. Avoid unrelated lore/history.

### Canonical state update / checkpoint preparation

Prioritize the structured pending delta register, verified canonical base/head, affected state domains, knowledge boundaries, current resume state, and exact durable changes. Narrative flavor that does not alter durable state should not dominate save context.

### Canonical fact retrieval

Prioritize explicit routes/indexes and authoritative entity files. Use episodic/semantic retrieval only to identify candidate records when the reference is fuzzy.

### Live Voice preload

Before Voice, compile a practical working set broad enough for likely immediate play: Wren's immediate state, current scene/region, active threads, likely NPC/location/faction interactions, relevant clocks, required DM-only preparation, and any source/rules material likely to be needed soon.

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

Relevance ranking must not override explicit canonical dependencies. If a fact is required for correctness, retrieve it even if semantic/locality ranking scores it low.

## Bounded context behavior

The campaign repository may grow without bound; the normal working context should not.

When context pressure grows:

1. keep invariants and immediate state;
2. prefer authoritative concise current-state records over long history;
3. replace broad history with targeted episodic retrieval;
4. load entity files by direct route instead of entire domain indexes when possible;
5. retrieve only the exact source sections needed for the adjudication;
6. split mature state according to `GROWTH_POLICY.md` rather than accepting an indefinitely expanding startup packet.

If required context cannot be assembled reliably within practical limits, growth-driven maintenance may be recommended or required according to `GROWTH_POLICY.md`.

## Provenance

Every nontrivial compiled fact should remain traceable to its authority category:

- canonical campaign state path/checkpoint;
- uploaded published source/reference;
- recent same-conversation pending state;
- derived/retrieval candidate requiring canonical resolution.

A future application may expose this provenance through a Context Inspector. The current ChatGPT implementation need not display routine DM-only context/provenance to Hiram, but must preserve the distinction internally.

## Context Inspector target

For future application development, retain the architectural ability to expose a debug view showing, with DM/player visibility filtering:

- which canonical files/entities were loaded;
- which episodic memories were retrieved;
- which published/source excerpts were retrieved;
- why each item was selected;
- token/context budget by category;
- current snapshot/checkpoint/transaction identifiers;
- which material was omitted or compressed due to context constraints.

This is observability, not authority. Editing the inspector output must never directly mutate canonical state.

## Failure behavior

If the compiler cannot resolve a referenced established fact:

1. follow the canonical retrieval escalation in `STATE_SCHEMA.md`;
2. use derived retrieval/index candidates where available;
3. resolve candidates back to canonical records;
4. if canonical retrieval still cannot establish the answer, preserve the ambiguity rather than inventing a fact.

During Live Voice, follow the deferred-lookup rule when required tools are unavailable.

## Maintenance interaction

Every maintenance run should evaluate whether current working-set manifests remain bounded and whether new regional/adventure/Voice routing packets would materially improve compilation.

When state is reorganized, update canonical routing and working-set references so the compiler continues to resolve the same semantic truth after sharding/archival.
