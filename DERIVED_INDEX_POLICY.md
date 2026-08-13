# Wren Campaign Derived Retrieval Index Policy — v1

This file is a normative companion to `STATE_SCHEMA.md` and `CONTEXT_ARCHITECTURE.md`. It defines future full-text, semantic/vector, alias, graph/relationship, and other derived indexes used to accelerate retrieval as the campaign grows.

Derived indexes are rebuildable accelerators. They are never canonical campaign truth.

## Core invariant

A retrieval index may answer **where should I look?** It may not by itself answer **what is canonically true?**

Every retrieved candidate that matters to an established campaign assertion must resolve back to one or more authoritative canonical records or uploaded source references before the fact is treated as established.

## Supported derived index classes

As scale warrants, the campaign/application may maintain any combination of:

- full-text search index;
- alias/name/handle index;
- semantic/vector embeddings over canonical records and historical episodes;
- chronology/date/session index;
- location/region proximity index;
- entity-type/domain index;
- faction/organization membership index;
- typed relationship/graph index;
- clue/thread/adventure association index;
- source-provenance index;
- player-knowledge/DM-visibility metadata index;
- episodic-history index over checkpoints/archived chronology;
- Context Compiler relevance/cache metadata.

These indexes may live outside GitHub in a future application so long as they remain derivable from canonical state/source data.

## Authority and resolution

Retrieval flow for a fuzzy reference:

`natural-language reference -> derived index candidates -> canonical route/path -> authoritative record fetch -> answer/adjudication`

If an index result and canonical state disagree, canonical state wins and the index is stale or defective.

Do not silently repair canon from an index. Repair or rebuild the index instead.

## Index records

A derived index entry should contain only enough data to identify, rank, filter, and resolve the authoritative record. Useful metadata may include:

- stable entity or episode identifier;
- canonical path/reference;
- aliases and natural-language handles;
- entity/domain type;
- region/location/faction associations;
- chronology anchors;
- relationship edge types;
- knowledge/visibility category;
- source provenance;
- embedding/vector;
- compact search summary;
- canonical version/snapshot/checkpoint generation used to build the entry.

Avoid duplicating complete authoritative records into the retrieval layer unless a cache is explicitly versioned and invalidated.

## Semantic retrieval safety

Semantic similarity is especially useful for references such as:

- "the surveyor Wren met on the coast";
- "that ruined place someone mentioned";
- "the clue about silence before fog";
- "the person who owed Wren a favor".

But semantic retrieval is probabilistic. Therefore:

1. retrieve multiple plausible candidates when confidence is not decisive;
2. use aliases, location, chronology, relationships, and active context to rerank;
3. fetch the authoritative record for the leading candidate(s);
4. only assert the established fact after canonical verification;
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

Examples:

- `Wren --KNOWS--> Aldrin Hale`
- `Aldrin Hale --MENTIONED--> Eastern Observatory`
- `NPC --MEMBER_OF--> Faction`
- `Clue --ABOUT--> Location`
- `NPC --KNOWS--> Clue`
- `FactionA --HOSTILE_TO--> FactionB`
- `Item --STORED_AT--> Boat`

Relationship edges should resolve to canonical entity IDs/paths. Derived graph projections must not create relationships absent from canonical truth.

## Freshness and invalidation

Derived indexes must record enough version information to detect staleness.

A future implementation should rebuild or incrementally update affected entries after verified campaign transactions/compaction. If the index version is behind canonical state and the stale portion could affect correctness, bypass or refresh it rather than trusting it.

A failed index update must never block canonical writes or corrupt campaign state. The canonical transaction commits first; index repair may follow.

## Rebuildability

A complete loss of the derived retrieval layer must not cause loss of campaign truth.

Given canonical campaign state, checkpoint history, and source metadata, the application should be able to rebuild all derived indexes.

This property is mandatory for backup/export portability.

## Privacy and knowledge boundaries

Indexes must preserve DM/player visibility metadata.

Player-facing retrieval must not surface DM-only aliases, secrets, relationship edges, hidden locations, unrevealed adventure keys, or hidden source annotations merely because the retrieval engine matched them.

A future app should maintain separate filtered views or enforce visibility filters at query time.

## Performance strategy

Use the cheapest reliable retrieval path first:

1. direct canonical path/ID when already known;
2. explicit alias/router index;
3. structured filters/relationship lookup;
4. full-text search;
5. semantic/vector retrieval for fuzzy references;
6. broader repository/source search only when needed.

Semantic search should supplement deterministic routing, not replace it.

## Context Compiler integration

`CONTEXT_ARCHITECTURE.md` may use derived indexes to choose candidate entities, historical episodes, source references, and related state for a turn/Voice working set.

The compiler must preserve provenance: retrieved index material is a candidate/routing signal until its authoritative record is resolved.

## Maintenance / application migration

Current GitHub-backed Wren does not require an external vector or graph database yet. Introduce derived indexes only when scale or observed retrieval friction justifies them.

`GROWTH_POLICY.md` should treat routine reliance on broad repository search, ambiguous aliases, large heterogeneous indexes, or expensive context compilation as signals that a stronger derived index may be useful.

For an eventual standalone application, derived retrieval should be a separate service/projection that can be rebuilt independently of the event store and materialized canonical state.
