# Wren Application Evolution Roadmap

**Status:** Product / engineering roadmap. Not campaign canon.  
**Repository role:** Durable record of product ideas and migration direction derived from the Wren campaign prototype.  
**Last initialized:** 2026-08-13.

## Vision

Evolve the Wren campaign architecture from a robust single-campaign GitHub-backed prototype into a reusable AI-assisted tabletop RPG platform that can support long-running campaigns, multiple game systems, large worlds, persistent NPCs/factions, exact source-book retrieval, Live Voice, deterministic mechanics, observability, and eventually multiple users.

The product should preserve the qualities that make the current Wren campaign trustworthy:

- canonical state independent of chat history;
- deterministic reconstruction;
- immutable durable history;
- explicit player-facing versus DM-only knowledge boundaries;
- exact source retrieval when published rules/material matter;
- bounded working context despite a growing world;
- idempotent, readback-verified persistence;
- no silent invention of established facts;
- portable/exportable campaign data.

## Architectural north star

```text
                    Source Library
              books / adventures / maps
                         |
                         | reference / instantiate
                         v
Player / GM ---> Campaign Runtime / Command Layer
                         |
                         | verified transactions
                         v
                  Immutable Event Store
                         |
              projection / materialization
             ____________|_____________
            |            |             |
            v            v             v
      Current State   Entity/Relation  Episodic Index
       Projections       Projection    FTS + vectors
            \            |            /
             \___________|___________/
                         |
                         v
                  Context Compiler
                         |
                         v
                    AI DM Runtime
               narration / tools / rules
```

The current GitHub implementation is a prototype of this model:

- immutable checkpoints approximate the event store;
- materialized `state/` shards approximate projections;
- canonical routing indexes approximate structured read models;
- uploaded RPG books/adventures are the source library;
- `CONTEXT_ARCHITECTURE.md` defines the future Context Compiler contract;
- `DERIVED_INDEX_POLICY.md` defines future rebuildable retrieval projections.

## Product principles

### 1. Canon first

Generated prose is not state. State changes become durable only through explicit structured transactions and verified persistence.

### 2. Storage, retrieval, and context are separate concerns

Canonical truth, derived search/indexes, episodic history, and per-turn model context must remain distinct layers.

### 3. Source canon is not campaign instance state

Published/source entities and adventure templates remain immutable references. When instantiated into a campaign, campaign-specific state records divergence without modifying the source definition.

### 4. Event history remains auditable

Campaign state should be reconstructable from ordered durable events plus snapshots/materialized projections.

### 5. Derived systems are disposable

Search indexes, embeddings, caches, graph projections, summaries, and compiled context can be deleted and rebuilt without losing campaign truth.

### 6. Knowledge boundaries are data, not prompt etiquette

Player-visible, character-known, rumor/inference, prepared possibility, and DM-secret truth should be represented structurally and enforced by retrieval/query layers.

### 7. System rules are adapters

The campaign engine should eventually support AD&D 2e, Dolmenwood, and other systems through game-system adapters rather than hard-coding one ruleset into the state engine.

## Phase 0 — Prove Wren in real play

**Current phase.**

Goals:

- run normal Wren sessions using the hardened GitHub architecture;
- use Live Voice under real conditions;
- observe persistence, source retrieval, context assembly, NPC continuity, clocks, travel, and maintenance behavior;
- record actual friction before engineering speculative complexity.

Exit signals:

- several genuine sessions checkpoint cleanly;
- fresh-chat reconstruction continues to work;
- real Voice sessions persist correctly;
- enough friction data exists to prioritize the next phase.

Do not skip this phase merely because product development is exciting.

## Phase 1 — Prototype Context Compiler

Build an explicit context-assembly implementation around `CONTEXT_ARCHITECTURE.md`.

Capabilities:

- task-specific context bundles for narration, mechanics, retrieval, saving, and Voice;
- relevance/locality ranking;
- direct routing to canonical entity files;
- bounded token/context budget;
- explicit source/canonical provenance;
- deterministic inclusion of mandatory immediate state;
- optional contextual packets for regions/adventures.

Prototype can initially remain inside ChatGPT/GitHub workflows.

Success criteria:

- context size remains bounded as repository state grows;
- important nearby/active entities are reliably present;
- unrelated history is not routinely loaded;
- missing-context failures are observable and reproducible.

## Phase 2 — Context Inspector / observability

Create a developer/GM debugging view inspired by context viewers in mature AI narrative systems.

Show, subject to visibility filtering:

- current canonical snapshot/checkpoint head;
- files/entities loaded;
- historical episodes retrieved;
- source-book excerpts retrieved;
- why each item was selected;
- context/token allocation by category;
- hidden versus player-visible classification;
- omitted/compressed candidates;
- transaction state (`CLEAN`, `PENDING`, etc.).

Important product distinction:

- DM/developer inspector may reveal secret data;
- player inspector must be filtered to avoid spoilers.

This feature becomes essential for debugging "why did the GM forget/know this?" issues.

## Phase 3 — Structured entity IDs and first-class relationships

Introduce stable IDs independent of filenames/display names.

Candidate entity domains:

- character;
- NPC/creature;
- faction/organization;
- location;
- item;
- clue/knowledge record;
- adventure instance;
- project/downtime task;
- event/clock;
- source entity.

Introduce typed relationships such as:

- `KNOWS`;
- `LOCATED_AT`;
- `MEMBER_OF`;
- `OWNS`;
- `STORED_AT`;
- `ABOUT`;
- `KNOWS_CLUE`;
- `ALLY_OF`;
- `HOSTILE_TO`;
- `PARENT_LOCATION`;
- `INSTANCE_OF_SOURCE_ENTITY`.

Initial implementation may remain relational/files-based. Do not adopt a graph database until queries justify it.

## Phase 4 — Derived retrieval service

Implement `DERIVED_INDEX_POLICY.md` as an external/rebuildable projection.

Start with:

- canonical alias index;
- full-text search;
- structured entity/type/region/faction filters;
- relationship lookup;
- chronology/session index.

Add semantic/vector retrieval only after deterministic routing/full-text are insufficient.

Potential technology path:

- PostgreSQL full-text search first;
- `pgvector` or dedicated vector service later if justified;
- relational edge table for typed relationships;
- optional graph projection later.

Required properties:

- versioned against canonical campaign head;
- asynchronous rebuild/incremental projection;
- loss of index does not lose campaign state;
- DM/player visibility enforced during retrieval.

## Phase 5 — Source Library and Campaign Instance model

Formalize the relationship between uploaded/published RPG material and instantiated campaign state.

Model:

`SourceEntity / AdventureTemplate -> CampaignInstance`

Examples:

- published NPC -> campaign NPC instance;
- published dungeon -> campaign site instance;
- published magic item -> campaign item instance;
- adventure template -> adventure instance with current progress/state.

Campaign instances should record only campaign-specific state/deltas where practical while retaining a stable source reference.

Needed features:

- source document registry;
- page/section/map provenance;
- entity extraction/registration workflow;
- exact source citations;
- source-version identity;
- spoiler/DM visibility controls;
- source-derived mechanics refresh without erasing campaign divergence.

## Phase 6 — Database-backed runtime

Move runtime persistence from GitHub files to an application backend while preserving GitHub/export compatibility.

Suggested initial stack:

- PostgreSQL for campaign/event/state metadata;
- object storage for PDFs/images/maps/assets;
- transactional append-only event table;
- materialized projection tables;
- worker/queue for projections/index updates;
- optional Redis only where demonstrated useful for ephemeral caching/leases.

Possible event record fields:

- event ID;
- campaign ID;
- transaction ID;
- expected campaign version;
- sequence/version;
- actor/source;
- timestamp;
- event type;
- semantic payload;
- visibility classification;
- source provenance;
- schema version.

Projection examples:

- current character state;
- inventory;
- NPC state;
- location state;
- faction state;
- active threads/clues;
- current chronology;
- relation edges;
- search documents.

Keep periodic snapshots for fast reconstruction and disaster recovery.

## Phase 7 — Production concurrency and transaction service

Generalize current checkpoint parent-SHA/idempotency behavior into application transaction semantics.

Use:

- one stable `transaction_id` per logical save;
- optimistic concurrency via `expected_campaign_version`;
- exactly-once logical behavior through idempotency keys;
- transactional event append;
- write lease/serialization where needed;
- retry-safe side effects;
- verification that projections eventually reach the committed event version.

Multiple reads may happen concurrently. Conflicting writes must reconcile rather than silently overwrite.

## Phase 8 — Deterministic mechanics service

Separate rules/mechanics resolution from freeform narration.

Capabilities may include:

- dice/randomness service with auditable seeds/results where appropriate;
- character resources/conditions;
- initiative/combat rounds;
- travel/exploration clocks;
- encounter checks;
- reaction/morale;
- spell/resource consumption;
- XP/economy calculations;
- system-specific procedures.

The AI DM decides when a procedure applies and explains/narrates outcomes; deterministic code performs calculations/randomized mechanical steps where appropriate.

Support player-facing physical dice as a configurable mode.

## Phase 9 — Game-system adapter framework

Extract rules-specific behavior behind adapters.

Core engine owns:

- persistence;
- entities/relationships;
- knowledge boundaries;
- events/clocks;
- source registry;
- context compilation;
- retrieval;
- transactions;
- Voice/multiplayer orchestration.

System adapter owns:

- character schema;
- dice conventions;
- combat procedures;
- travel/exploration rules;
- advancement;
- spell/magic structure;
- system-specific source semantics;
- optional tables/procedures.

Early targets:

1. AD&D 2nd Edition — Wren reference implementation.
2. Dolmenwood — useful second target because it stresses calendars, factions, hexcrawls, travel, procedures, and a distinct ruleset.

A successful second adapter validates that the core architecture is genuinely system-agnostic.

## Phase 10 — Voice-first runtime

Turn the current same-conversation Voice workflow into a first-class application session.

Capabilities:

- precompiled Voice working set;
- live transcript/event capture;
- structured pending delta accumulation while speaking;
- deferred tool/source retrieval when necessary;
- post-Voice transaction finalization;
- explicit save/readback status;
- low-latency scene/mechanics lookup;
- interruption handling without losing pending state.

Long-term goal: Voice should feel like sitting at a table, while persistence remains invisible and reliable.

## Phase 11 — Maps / VTT integration

Potential capabilities:

- campaign-created maps;
- fog-of-war / player vs DM layers;
- tokens/positions;
- location/entity linking;
- encounter maps;
- hex exploration;
- travel routes;
- clickable campaign entities;
- source-map references;
- Foundry/Roll20/other import/export bridges where licensing/API terms allow.

Maps should be projections/interfaces over canonical state, not independent contradictory truth stores.

## Phase 12 — Multiplayer campaigns

Add multiple human players and possibly co-GMs.

New requirements:

- per-player knowledge/visibility;
- private messages/secret checks;
- turn/initiative coordination;
- invitation/auth/roles;
- simultaneous reads;
- serialized campaign-changing transactions;
- player-character ownership/control boundaries;
- configurable GM authority versus AI authority;
- audit trail of human/AI actions.

## Phase 13 — Campaign portability and open format

Keep user trust high by avoiding lock-in.

Provide:

- full campaign export;
- source-reference manifest;
- event history;
- materialized state;
- maps/assets metadata;
- system-adapter metadata;
- knowledge classifications;
- optional Git repository export compatible in spirit with the Wren prototype.

Import should validate schema/version/provenance before accepting state.

Git can remain an excellent human-readable backup/export format even after it is no longer the primary runtime store.

## Phase 14 — Evaluation and regression harness

Create repeatable tests for AI-GM correctness rather than relying only on subjective play quality.

Test categories:

- fresh-session reconstruction;
- fuzzy entity retrieval;
- knowledge-boundary leaks;
- rumor/inference preservation;
- checkpoint/event idempotency;
- concurrent-write conflicts;
- source-rule retrieval accuracy;
- context compiler recall/precision;
- long-campaign scale tests;
- NPC voice/knowledge consistency;
- world-clock advancement;
- adventure/source-instance divergence;
- Voice pending-state persistence;
- export/import round trip.

Build synthetic large campaigns to test hundreds/thousands of entities without waiting years for Wren to reach that size.

## Phase 15 — Performance / scale targets

Eventually define measurable SLOs rather than vague "fast enough" goals.

Candidate targets to benchmark:

- session bootstrap latency;
- entity lookup latency;
- context compilation latency;
- source retrieval latency;
- Voice turn latency;
- transaction commit latency;
- projection lag;
- index freshness;
- maximum working-context size;
- reconstruction time at large event counts;
- campaign export/import time.

Use observed workloads before choosing hard numbers.

## Potential future optimizations

Evaluate only when profiling demonstrates need:

- incremental projection workers;
- snapshot cadence tuning;
- read-through entity cache;
- regional/context packet cache;
- precomputed relationship neighborhoods;
- semantic search reranking;
- background source indexing;
- parallel independent retrieval;
- compact binary storage internally with human-readable export;
- hot/warm/cold historical partitions;
- adventure/region prefetch based on current travel direction;
- model selection/routing by task (narration vs extraction vs summarization vs rules lookup).

## Product UX ideas

### Campaign dashboard

Show:

- current scene;
- party state;
- active threads;
- timeline/calendar;
- known NPCs/locations/factions;
- maps;
- recent session summaries;
- pending save/maintenance health.

### GM / developer health panel

Show:

- canonical version;
- pending transaction state;
- projection/index freshness;
- context compiler diagnostics;
- maintenance/growth warnings;
- source retrieval provenance;
- integrity-check status.

### Player journal

Provide a filtered player-facing view of:

- known facts;
- rumors;
- personal notes/inferences;
- discovered locations;
- relationships;
- quests/threads;
- maps;
- chronology.

Do not expose DM truth by deriving this view from unrestricted model output; derive it from classified state.

## Security / privacy / licensing considerations

Before becoming a public product, explicitly design for:

- campaign/user data isolation;
- encrypted secrets/credentials;
- authorization at campaign/entity/source level;
- DM-only information boundaries;
- audit logging;
- source-book copyright/licensing constraints;
- user-provided content handling;
- deletion/export rights;
- model-provider data boundaries;
- prompt/tool injection defenses for uploaded source material.

Published source ingestion must respect licensing and should generally store/access user-provided or licensed content rather than redistributing protected text.

## Business / positioning questions to explore later

Possible positions:

- AI GM for solo play;
- AI co-GM / campaign memory for human GMs;
- persistent campaign operating system;
- campaign backend/API for VTTs;
- local-first/open campaign format with optional hosted AI;
- multi-system world/campaign manager with AI runtime.

Do not choose positioning before validating which part users value most.

## Near-term backlog

After real Wren play validates the current architecture:

1. collect concrete friction from several sessions;
2. prototype Context Compiler instrumentation using the existing GitHub backend;
3. define stable entity IDs without forcing premature database migration;
4. build a small Context Inspector artifact/tool;
5. design source-entity / campaign-instance records around one real published adventure use case;
6. create a synthetic large-campaign benchmark repository;
7. evaluate PostgreSQL event/projection schema in a separate prototype;
8. test Dolmenwood as the second system to expose core-vs-adapter boundaries;
9. decide whether the first standalone prototype is local/dev-only, web, or hybrid.

## Ideas explicitly deferred until evidence exists

- Neo4j or another dedicated graph database;
- separate vector database;
- Redis-heavy architecture;
- microservices;
- Kubernetes;
- complex distributed event infrastructure;
- autonomous background world simulation beyond clearly modeled clocks/events;
- automatic extraction of every entity/stat from entire book libraries.

These may eventually be useful, but none should be introduced merely because they sound scalable.

## Roadmap maintenance

This roadmap is deliberately non-canonical and may change frequently.

When product/engineering work produces a significant decision:

- update this document with the decision and rationale;
- move durable runtime invariants into the appropriate normative protocol/policy file rather than relying on roadmap prose;
- preserve rejected/abandoned ideas when the reasoning may prevent repeating the same exploration later;
- periodically split detailed implementation plans into `docs/` design documents as the project grows.

The Wren campaign must remain playable even while application development is paused or experimental branches fail.
