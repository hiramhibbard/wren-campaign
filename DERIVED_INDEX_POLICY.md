# Wren Campaign Derived Retrieval Index Policy — v1

This file is a normative companion to `STATE_SCHEMA.md` and `CONTEXT_ARCHITECTURE.md`. It defines future full-text, semantic/vector, alias, graph/relationship, and other derived indexes used to accelerate retrieval as the campaign grows.

Derived indexes are rebuildable accelerators. They are never canonical campaign truth.

## Core invariant

A retrieval index may answer **where should I look?** It may not by itself answer **what is canonically true?**

Every retrieved candidate that matters to an established campaign assertion must resolve back to one or more authoritative canonical records or uploaded source references before the fact is treated as established.

## Distinction from compiled source knowledge

`SOURCE_KNOWLEDGE_LAYER_POLICY.md` defines a separate derived layer containing **verified normalized source entities/assertions/procedures**. Those objects may contain enough structured published information to answer a source-dependent question directly when their verification/scope permits.

That layer is not a retrieval index.

Use the distinction:
- **compiled source object** = verified normalized representation of published source content with provenance and source authority fallback;
- **derived index entry** = locator/ranking/filtering metadata pointing toward canonical campaign records or compiled/source records;
- **runtime cache** = disposable value derived for an active character/encounter/effect/context.

Indexes may point to compiled source objects. Compiled source objects point to uploaded-source provenance. Campaign indexes point to canonical campaign state. Do not flatten these layers.

## Supported derived index classes

As scale warrants, the campaign/application may maintain any combination of:

- full-text search index;
- alias/name/handle index;
- semantic/vector embeddings over canonical records, compiled source objects, and historical episodes;
- chronology/date/session index;
- location/region proximity index;
- entity-type/domain index;
- faction/organization membership index;
- typed relationship/graph index;
- clue/thread/adventure association index;
- source-provenance index;
- player-knowledge/DM-visibility metadata index;
- episodic-history index over checkpoints/archived chronology;
- compiled-source entity/assertion locator index;
- Context Compiler relevance/cache metadata.

These indexes may live outside GitHub in a future application so long as they remain derivable from canonical state/source data.

## Authority and resolution

Retrieval flow for a fuzzy campaign reference:

`natural-language reference -> derived index candidates -> canonical route/path -> authoritative record fetch -> answer/adjudication`

Retrieval flow for a fuzzy source-domain reference may be:

`natural-language source need -> derived index candidates -> compiled source entity/assertion -> scope/verification check -> exact source fallback if required -> answer/adjudication`

If an index result and canonical state/verified source object disagree, the authoritative underlying layer wins and the index is stale or defective.

Do not silently repair canon/source truth from an index. Repair or rebuild the index instead.

## Index records

A derived index entry should contain only enough data to identify, rank, filter, and resolve the authoritative record/object. Useful metadata may include:

- stable entity, source-object, or episode identifier;
- canonical path/reference or compiled-object path/reference;
- aliases and natural-language handles;
- entity/domain type;
- region/location/faction associations;
- chronology anchors;
- relationship edge types;
- knowledge/visibility category;
- source provenance;
- embedding/vector;
- compact search summary;
- canonical/source-object version/fingerprint used to build the entry.

Avoid duplicating complete canonical campaign records or compiled source objects into the retrieval layer unless a cache is explicitly versioned and invalidated.

## Semantic retrieval safety

Semantic similarity is especially useful for references such as:

- "the surveyor Wren met on the coast";
- "that ruined place someone mentioned";
- "the clue about silence before fog";
- "the person who owed Wren a favor";
- "that Dragon article about troll ecology";
- "the rule for how much a Strength 9 character can carry".

But semantic retrieval is probabilistic. Therefore:

1. retrieve multiple plausible candidates when confidence is not decisive;
2. use aliases, location, chronology, relationships, source scope, and active context to rerank;
3. fetch/resolve the authoritative canonical record or verified compiled source object for the leading candidate(s);
4. only assert established campaign/source fact after that authority check;
5. preserve genuine ambiguity when more than one candidate remains plausible.

## Episodic retrieval

Historical checkpoints and archived chronology may be indexed as episodic memory for questions about what happened previously.

Episodic retrieval must distinguish:

- historical fact that remains true now;
- historical fact later superseded;
- player belief/rumor/inference at that time;
- DM truth at that time;
- an event that changed current state.

When the user asks about current truth, episodic matches must be reconciled with current canonical state before answering.

## Typed relationship graph

A future application should support first-class typed relationships even if the physical storage is relational rather than a graph database.

Campaign examples:
- `Wren --KNOWS--> Aldrin Hale`
- `Aldrin Hale --MENTIONED--> Eastern Observatory`
- `NPC --MEMBER_OF--> Faction`
- `Clue --ABOUT--> Location`
- `NPC --KNOWS--> Clue`
- `FactionA --HOSTILE_TO--> FactionB`
- `Item --STORED_AT--> Boat`

Source-knowledge examples:
- `MONSTER --APPEARS_IN--> ADVENTURE`
- `ARTICLE --EXPANDS--> MONSTER`
- `DEITY --HAS_PRIESTHOOD--> PRIESTHOOD`
- `SPELL --BELONGS_TO_SCHOOL--> SCHOOL`

Campaign graph edges must resolve to canonical campaign truth. Source graph edges must resolve to verified source assertions. Derived graph projections must not invent relationships in either layer.

## Freshness and invalidation

Derived indexes must record enough version information to detect staleness.

A future implementation should rebuild or incrementally update affected entries after verified campaign transactions/compaction and after compiled-source extraction/reverification. If an index version is behind its authoritative layer and the stale portion could affect correctness, bypass or refresh it rather than trusting it.

A failed index update must never block canonical campaign writes, compiled-source correction, or source authority. The authoritative mutation commits first; index repair may follow.

## Rebuildability

A complete loss of the derived retrieval layer must not cause loss of campaign truth or compiled source truth.

Given canonical campaign state, checkpoint history, compiled source objects, and uploaded-source metadata, the application should be able to rebuild all derived indexes.

The compiled source layer itself is separately rebuildable from uploaded sources under `SOURCE_KNOWLEDGE_LAYER_POLICY.md`.

## Privacy and knowledge boundaries

Indexes must preserve DM/player visibility metadata.

Player-facing retrieval must not surface DM-only aliases, secrets, relationship edges, hidden locations, unrevealed adventure keys, or hidden source annotations merely because the retrieval engine matched them.

Published source objects are not automatically player knowledge. The Context Compiler/campaign visibility layer determines whether a source fact may be surfaced in play.

A future app should maintain separate filtered views or enforce visibility filters at query time.

## Performance strategy

Use the cheapest reliable retrieval path first:

1. direct canonical/compiled-source path or stable ID when already known;
2. explicit alias/router index;
3. structured filters/relationship lookup;
4. full-text search over canonical/compiled summaries;
5. semantic/vector retrieval for fuzzy references;
6. exact uploaded-source locator from the compiled object when needed;
7. broader repository/source search only when needed.

Semantic search should supplement deterministic routing, not replace it.

## Context Compiler integration

`CONTEXT_ARCHITECTURE.md` may use derived indexes to choose candidate campaign entities, compiled source objects, historical episodes, source references, and related state for a turn/Voice working set.

The compiler must preserve provenance: index material is a candidate/routing signal. A verified compiled source object may itself be usable source-derived content; a campaign index candidate still requires canonical campaign resolution.

## Maintenance / application migration

Current GitHub-backed Wren does not require an external vector or graph database yet. Introduce derived indexes only when scale or observed retrieval friction justifies them.

The new compiled-source layer may grow substantially before an external index is necessary; use explicit stable IDs, domain shards, and registries first.

`GROWTH_POLICY.md` should treat routine reliance on broad repository/source search, ambiguous aliases, large heterogeneous indexes, expensive source scans, or expensive context compilation as signals that stronger derived indexing may be useful.

For an eventual standalone application, derived retrieval should be a separate service/projection that can be rebuilt independently of the campaign event store, materialized canonical state, and compiled source-object store.
