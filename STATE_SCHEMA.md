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
11. Automatic connector writes are best-effort; a blocked external write must fall back to an explicit human-transported transaction rather than losing pending state.
12. Hiram must be proactively reminded whenever manual action is required or maintenance is due.

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

### Live Voice retrieval rule

During ordinary Live Voice, GitHub/connected-app retrieval may be unavailable. Before entering Voice, load a practical current working set broad enough for likely play.

If a needed established fact is not already verified in the current conversation while Voice retrieval is unavailable:

1. Do not guess, invent, or claim the fact is absent.
2. Briefly tell Hiram that the detail needs a canonical lookup.
3. Preserve the pending lookup and the exact gameplay/question context in the same conversation.
4. When Voice ends and text-mode GitHub tools return, automatically perform the lookup without requiring Hiram to repeat the question or say "check GitHub."
5. Continue only after the canonical result is available or genuine ambiguity remains.

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
4. Construct exactly one complete immutable checkpoint containing the full durable delta for that transaction.
5. Attempt to create the checkpoint automatically in GitHub.
6. If creation succeeds, read the created checkpoint back and verify sequence, identity, and critical intended changes. Re-list/verify discoverability when needed.
7. Only after successful readback may the checkpoint be reported as saved.

If the intended sequence already exists or canonical state advanced concurrently, stop, refetch, reconcile, and choose the correct next transaction. Never overwrite an existing checkpoint.

A failed checkpoint creation leaves canonical state unchanged and pending state unsaved.

### Manual checkpoint fallback

OpenAI's external-write safety layer may block otherwise valid connector writes. Automatic GitHub mutation is therefore best-effort rather than assumed deterministic.

If an automatic checkpoint write is blocked or cannot be safely completed:

1. Do not discard or summarize away the pending transaction.
2. Preserve the exact complete checkpoint payload in the current conversation.
3. Immediately tell Hiram that manual intervention is required.
4. Provide the exact target path/filename and a ready-to-commit payload or downloadable artifact when available. Hiram should only transport the prepared transaction; he should not have to reconcile campaign facts himself.
5. Keep all session changes pending and do not say they are saved.
6. After Hiram reports the manual commit/upload complete, fetch that exact checkpoint from canonical `main` and verify sequence, identity, and critical player-facing/DM-secret changes.
7. Only after successful readback clear pending state and report the checkpoint saved.
8. If verification fails, tell Hiram exactly what remains unsaved and exactly what action is needed next.

Do not endlessly retry a write that the safety layer has blocked. Preserve the transaction and move to the human-transport fallback.

## Loading checkpoints

The root ledger declares `checkpoint_baseline`. On load:

1. Fetch the root ledger.
2. Load its declared current working set/materialized files.
3. List checkpoints with sequence greater than `checkpoint_baseline`.
4. Apply them in strict numerical order.
5. Validate sequence/parent/generation metadata and detect gaps or conflicts.
6. Use the resulting reconstructed state as current canonical truth.

Historical checkpoints at or below the baseline are audit/recovery history and need not be replayed during ordinary startup.

## Maintenance status and reminders

Maintenance status must be derived from canonical repository state, not remembered conversationally.

At session start and session end:

1. Read `checkpoint_baseline` from the root manifest.
2. Determine the latest real campaign checkpoint sequence from the canonical checkpoint directory.
3. Count uncompacted real campaign checkpoints after baseline. Administrative diagnostics/tests marked `state-change: none` do not count toward the threshold.
4. Apply the thresholds below and proactively remind Hiram when action is due.

### Default thresholds

- **Maintenance due:** 10 or more uncompacted real campaign checkpoints.
- **Early maintenance recommended:** major adventure/arc/region transition, materially expensive replay, or a state shard/index becoming unwieldy.
- **Maintenance required before further gameplay:** only when reconstruction/replay size, integrity uncertainty, checkpoint conflict/gap, or repository condition makes continued loading unsafe or materially unreliable.

When maintenance is due but play remains safe, the reminder should be concise and should not block play:

`Wren maintenance is due. Current state is still safe to play from. When convenient, open Work/Codex in the Wren Project and say: "Run Wren maintenance."`

After maintenance, a fresh ordinary Project chat must verify the new `snapshot_generation` and `checkpoint_baseline`. Once canonical state proves the maintenance completed, stop issuing that reminder.

## Required human-action reminders

The DM must proactively notify Hiram whenever progress depends on his action. Silent operational debt is not allowed.

Examples:

- automatic checkpoint write blocked -> provide exact manual commit/upload action;
- manually transported checkpoint awaits verification -> tell Hiram what must be done/verified;
- Live Voice lookup must wait for text-mode retrieval -> say so and automatically perform it afterward;
- maintenance due -> remind Hiram with the exact Work/Codex command;
- maintenance/recovery/verification failure -> state the exact next required action.

Once a required action is verified complete, remove that reminder from active operational state.

## Compaction

Compaction is automatic DM infrastructure. Hiram does not need to count checkpoints or decide when it is due.

Trigger compaction at a safe boundary when useful, including approximately:

- 10 or more uncompacted real campaign checkpoints;
- 5–10 completed sessions when that produces substantial accumulated deltas;
- checkpoint-chain size becomes materially inefficient;
- major adventure/arc/region transition;
- periodic integrity audit;
- a domain shard becomes unwieldy and should be reorganized.

Thresholds are operational guidance except for the default reminder threshold above. Prefer bounded startup cost over rigid maintenance for its own sake.

### Work/Codex maintenance role

Work/Codex is the maintenance console, not the normal game table.

When Hiram says `Run Wren maintenance` in the appropriate maintenance environment, the maintenance task is to:

1. Fetch the root manifest, affected materialized state files, and every real campaign checkpoint after the current baseline.
2. Reconstruct and validate current canonical truth.
3. Fold checkpoint deltas into the appropriate `state/` files.
4. Create/split NPC, faction, location, chronology, index, DM, and other shards where warranted by growth.
5. Refresh player-knowledge boundaries, DM-only truth, active threads/clocks, Current Resume Packet, and current working-set manifest.
6. Use fresh guarded writes for existing files and verified-unused paths for new files.
7. Read back changed state files and verify critical facts and knowledge boundaries.
8. Update the root ledger last, advancing `snapshot_generation` and `checkpoint_baseline` only through the highest successfully materialized checkpoint.
9. Read the root ledger back and verify the new generation, baseline, resume state, and working set.
10. Leave historical checkpoints intact.

If compaction fails before the root baseline advances, the old materialized snapshot + checkpoint chain remains authoritative. Do not advance the baseline until all intended materialized writes have been verified.

Normal gameplay should resume afterward in a fresh ordinary Project chat; conversational history is not required for continuity.

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

After a successful checkpoint, automatically derive maintenance status from the canonical baseline/checkpoint chain and remind Hiram if maintenance is due. Hiram should not need to ask.

If automatic persistence is blocked, invoke the manual checkpoint fallback immediately and remind Hiram until the transported checkpoint has been canonically read back and verified.

## Recovery

Git history, immutable checkpoints, and `legacy/` are recovery/audit sources. Ordinary play always uses current `main` plus the declared snapshot/checkpoint chain.

Never repair uncertainty by guessing. Compare canonical generations/checkpoints/history and reconcile deliberately.