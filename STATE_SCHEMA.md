# Wren Campaign State Architecture — Schema v1

## Purpose

This repository is the durable canonical state store for Wren's solo AD&D 2nd Edition campaign. It is designed for long-term growth: many sessions, NPCs, locations, factions, maps, secrets, clocks, rulings, adventures, and years of campaign history without requiring every session to load or rewrite the entire world.

## Core model

Current canonical state is reconstructed as:

`materialized state snapshot + ordered checkpoints after checkpoint_baseline`

The root `Wren_Campaign_Ledger.md` is a compact manifest/resume document, not the campaign encyclopedia.

### Invariants

1. Current-context absence is never evidence that campaign state is absent.
2. Established campaign facts must be retrieved from canonical repository state before they are asserted when they are not already verified in the current working set.
3. Hiram never needs to tell the DM to check campaign files.
4. Checkpoints are immutable after creation.
5. Ordinary saves append a checkpoint; they do not require rewriting the full campaign state.
6. Compaction materializes accumulated checkpoint deltas into domain state files and advances the baseline; historical checkpoints remain intact.
7. Exact published AD&D/source facts remain governed by Hiram's uploaded source material, not this repository.
8. Player-facing and DM-only knowledge boundaries must be preserved during retrieval, narration, summaries, checkpoints, and verification.
9. A write is not considered saved until its stored representation is independently read back and verified.
10. Concurrency or ambiguity causes stop/refetch/reconcile behavior, never blind overwrite.

## Repository layout

```text
Wren_Campaign_Ledger.md       # compact root manifest, resume packet, schema/baseline metadata
PROJECT_BOOTSTRAP.md          # backup of Project bootstrap instructions
STATE_SCHEMA.md               # this architecture/protocol

state/
  INDEX.md                    # compact deterministic entity/domain routing index
  character/
    wren.md
    inventory.md
    magic.md
  chronology/
    current.md
    sessions.md
  npcs/
    index.md
    <npc>.md
  factions/
    index.md
    <faction>.md
  locations/
    index.md
    <region-or-location>/...
  threads/
    active.md
    resolved.md
  rulings/
    adnd2e-campaign-rulings.md
  dm/
    secrets.md
    clocks.md
    prepared-world.md
    player-knowledge.md

checkpoints/
  <sequence>-<slug>.md

maps/
  player/
  dm/

legacy/
```

Directories/files are created organically. Do not create empty shards merely to satisfy the example layout.

## Root ledger responsibilities

`Wren_Campaign_Ledger.md` should remain bounded and contain:

- canonical repository/path/branch;
- `schema_version`;
- `snapshot_generation`;
- `checkpoint_baseline`;
- latest known checkpoint sequence;
- Current Resume Packet;
- current working-set manifest;
- authoritative index/state references;
- mandatory operating/persistence invariants;
- migration/recovery metadata where needed.

It should not accumulate detailed biographies, complete historical logs, every location description, or all prepared world material.

## Automatic canonical retrieval

Hiram should be able to speak and play naturally. He does not administer retrieval.

Whenever a question, declared action, narration, adjudication, NPC interaction, location, object, clue, relationship, historical event, spell/resource question, or other situation could depend on previously established campaign information, automatically ensure the relevant authoritative state is loaded before responding.

Retrieval escalation order:

1. Use already verified current working-set state if sufficient.
2. Follow explicit references from the root manifest/current files.
3. Consult `state/INDEX.md` and the appropriate domain index.
4. Fetch the authoritative entity/domain file.
5. If the reference is fuzzy or unnamed, search the canonical repository using distinctive concepts, then fetch matching canonical files.
6. Retrieve cross-referenced files as needed to resolve ambiguity.
7. Only after canonical retrieval cannot resolve a genuine ambiguity should Hiram be asked for clarification or told the established answer cannot be located.

Do not answer "I don't know" merely because a fact is absent from conversational context. Do not silently invent it either.

### Current working set

At session start the root ledger identifies the minimum files needed to resume accurately, typically:

- Wren's immediate mechanical/resource state;
- current chronology/location;
- active threads;
- currently relevant NPC/location/faction files;
- required DM clocks/secrets/prepared state;
- unapplied checkpoints after the baseline.

Do not load the entire campaign encyclopedia by default. Files fetched during a chat may be treated as cached verified state until a save/concurrency event makes refetch necessary.

## State-file design

State files are materialized current truth, optimized for future adjudication and retrieval rather than transcript preservation.

### Character

Keep stable identity/mechanics, current resources, inventory, and magic in bounded character-domain files. Exact sourced mechanics should retain source references or retrieval requirements when consequential.

### NPCs

Use `state/npcs/index.md` as a compact routing index. Significant recurring NPCs may receive individual files containing established identity, status, relationship, knowledge, motives, resources/capabilities where relevant, chronology anchors, player-known facts, DM-only references, and cross-links.

Shard indexes by region/faction later if size warrants it.

### Locations

Use hierarchical region/location files. Location indexes should route natural references and aliases to canonical files. Player-facing and DM-keyed information should be separated when spoiler risk warrants it.

### Factions

Track current goals, resources, relationships, clocks, and relevant members. Large factions may be subdivided organically.

### Threads

`active.md` contains unresolved actionable threads and clues. Resolved material moves to compact historical records when no longer needed for immediate adjudication.

### Chronology

`current.md` contains current date/time/sequence, immediate recent history, and chronology facts needed for play. Historical session/arc summaries may be sharded rather than allowing one infinite diary.

### DM state

DM-only files contain secrets, hidden clocks, prepared possibilities, hidden causality, encounter/world preparation, and explicit player-knowledge boundaries. Never expose their contents merely because they were loaded.

### Maps and play aids

Store campaign-created maps/play aids separately under `maps/` when appropriate. State files reference their paths. Published maps/handouts should normally reference Hiram's authoritative uploaded source rather than duplicating copyrighted source content into campaign state.

## Checkpoint protocol

Ordinary durable saves are append-only transactions.

Each checkpoint filename begins with a monotonically increasing zero-padded sequence, e.g. `000042-session-end.md`.

A checkpoint records, as applicable:

- sequence;
- checkpoint type/session identifier;
- timestamp if useful;
- `schema_version`;
- `snapshot_generation` it applies to;
- `checkpoint_baseline` observed at creation;
- previous checkpoint sequence/identity;
- canonical base/root SHA(s) observed before save when available;
- affected domains/files;
- player-facing durable deltas;
- DM-secret durable deltas;
- chronology/location changes;
- resource/mechanical changes;
- new/changed NPC, faction, location, thread, clue, ruling, and knowledge state;
- updated resume information;
- unresolved/pending items that intentionally remain unresolved.

The checkpoint must contain enough semantic detail to deterministically apply its delta to the materialized snapshot. Avoid vague prose such as "update Edric appropriately."

### Save transaction

At a checkpoint:

1. Fetch the root ledger and list/inspect the checkpoint directory sufficiently to establish the current baseline/latest sequence and detect concurrency.
2. Reconcile all pending player-facing and DM-secret durable changes from the current conversation.
3. Choose the next sequence only after verifying it is unused.
4. Create exactly one new immutable checkpoint containing the complete durable delta for that transaction.
5. Read the created checkpoint back from GitHub and verify sequence, identity, and critical intended changes.
6. Re-list or otherwise verify the checkpoint is discoverable in canonical `main` when needed.
7. Only then report the checkpoint as saved.

If the intended sequence already exists or canonical state advanced concurrently, stop, refetch, reconcile, and choose the correct next transaction. Never overwrite an existing checkpoint.

A failed checkpoint creation leaves canonical state unchanged and pending state unsaved.

## Loading checkpoints

The root ledger declares `checkpoint_baseline`. On load:

1. Fetch the root ledger.
2. Load its declared current working set/materialized files.
3. List checkpoints with sequence greater than `checkpoint_baseline`.
4. Apply them in strict numerical order.
5. Validate sequence/parent/generation metadata and detect gaps or conflicts.
6. Use the resulting reconstructed state as current canonical truth.

Historical checkpoints at or below the baseline are audit/recovery history and need not be replayed during ordinary startup.

## Compaction

Compaction is automatic DM infrastructure. Hiram does not need to request it.

Trigger compaction at a safe boundary when useful, including approximately:

- 5–10 completed sessions since the last compaction;
- 10–20 unapplied checkpoints;
- checkpoint-chain size becomes materially inefficient;
- major adventure/arc/region transition;
- periodic integrity audit;
- a domain shard becomes unwieldy and should be reorganized.

Thresholds are operational guidance, not campaign rules. Prefer bounded startup cost over rigid counts.

### Compaction transaction

Compaction is a larger maintenance operation and should normally occur at session end or another safe non-gameplay boundary.

1. Fetch the root ledger, affected state files, and all checkpoints after the current baseline.
2. Reconstruct current truth and validate the chain.
3. Materialize deltas into the appropriate domain state files; create/split indexes and entity files where warranted.
4. Verify each intended working representation before writes.
5. Use fresh SHA-guarded updates for existing files; create new files only at verified-unused paths.
6. Read back changed state files and verify critical facts and knowledge boundaries.
7. Update the root ledger last, advancing `snapshot_generation` and `checkpoint_baseline` to the highest successfully materialized checkpoint and refreshing the Current Resume Packet/working-set manifest.
8. Read the root ledger back and verify the new baseline/generation/resume state.
9. Do not delete historical checkpoints. Git history plus immutable checkpoints remain the audit/recovery trail.

If compaction fails before the root baseline advances, the old snapshot + checkpoint chain remains authoritative. Do not advance the baseline until all materialized writes have been verified.

## Sharding and growth rules

Shard organically when a file becomes expensive or awkward to retrieve/update. Examples:

- `npcs/index.md` -> regional/faction indexes plus individual NPC files;
- `locations/index.md` -> regional indexes and location directories;
- chronology -> arc/year/session-summary files;
- DM prepared state -> region/adventure/faction-specific files.

Indexes contain routing metadata and concise identifiers, not duplicate encyclopedic state.

Prefer explicit canonical references over semantic discovery. Repository search is a fallback for fuzzy natural-language references.

## Knowledge and truth categories

Preserve distinctions among:

- player-known established fact;
- rumor/hearsay;
- Wren's suspicion/inference;
- unresolved question;
- Prepared Possibility;
- Established DM Truth;
- source canon not yet instantiated into campaign canon.

A checkpoint or compaction must not accidentally promote uncertainty into truth or leak DM truth into player-facing state.

## Session end

Natural session-ending language triggers a checkpoint. Live Voice may accumulate pending state in the same conversation; after Voice ends and GitHub tools are available, checkpoint that pending state from the same conversation before giving saved sign-off.

After a successful checkpoint, decide automatically whether compaction thresholds warrant maintenance. Hiram should not need to ask.

## Recovery

Git history, immutable checkpoints, and `legacy/` are recovery/audit sources. Ordinary play always uses current `main` plus the declared snapshot/checkpoint chain.

Never repair uncertainty by guessing. Compare canonical generations/checkpoints/history and reconcile deliberately.