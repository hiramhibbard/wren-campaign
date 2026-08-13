# Wren Campaign Persistence Protocol — Transaction Hardening v1

This file is a normative companion to `STATE_SCHEMA.md`. It governs hardened save transactions: stable transaction identity, idempotency, checkpoint-parent identity, concurrency reconciliation, Voice pending-state serialization, and readback verification. Where this file is stricter than the general checkpoint language in `STATE_SCHEMA.md`, follow this file for persistence operations.

It does not change campaign facts. It governs how durable campaign changes become canonical.

## Core persistence model

Treat a play session or explicit save as one open transaction against a verified canonical base:

`canonical base -> open transaction -> structured pending deltas -> prepared checkpoint -> append -> readback verification -> committed canonical state`

A transaction is not complete merely because gameplay ended, a payload was prepared, a write was attempted, or GitHub reported success. It is complete only after canonical readback verification succeeds.

## Persistence state machine

Operational states:

- `CLEAN`: no known durable changes are pending in the current conversation.
- `PENDING`: meaningful durable changes exist only in the current conversation.
- `PREPARED`: one complete checkpoint transaction has been assembled against a freshly verified canonical head and has a stable `transaction_id`.
- `WRITTEN_UNVERIFIED`: checkpoint creation reported success, but canonical readback has not verified it.
- `MANUAL_TRANSPORT_REQUIRED`: automatic persistence was blocked or could not be safely completed; the exact prepared transaction remains pending and Hiram must transport it.
- `VERIFICATION_FAILED`: a purported write cannot yet be verified as the intended canonical checkpoint.
- `VERIFIED`: canonical readback verified checkpoint identity, chain metadata, transaction identity, and critical intended deltas.

Normal transition:

`CLEAN -> PENDING -> PREPARED -> WRITTEN_UNVERIFIED -> VERIFIED -> CLEAN`

Fallback transitions include:

`PREPARED -> MANUAL_TRANSPORT_REQUIRED`

`WRITTEN_UNVERIFIED -> VERIFICATION_FAILED`

`MANUAL_TRANSPORT_REQUIRED -> VERIFIED -> CLEAN`

Only `VERIFIED` permits the DM to say the transaction is saved, checkpointed, locked in, permanent, or otherwise canonically persisted. Pending state must not be cleared before `VERIFIED`.

## Voice session transaction rule

Entering Live Voice does not create a separate persistence system. The same conversation carries one open campaign transaction.

Before Voice, session-start loading establishes a verified canonical base: snapshot generation, checkpoint baseline, root blob SHA, and current checkpoint head identity.

During Voice:

1. Meaningful durable changes move the transaction from `CLEAN` to `PENDING`.
2. Maintain those changes as structured pending deltas in the same conversation.
3. GitHub unavailability during Voice does not trigger reconstruction from another source.
4. Do not claim pending Voice changes are externally saved.
5. If a canonical lookup is needed but unavailable in Voice, preserve the pending lookup with its exact gameplay context.

After Voice ends in the same conversation:

1. Perform deferred canonical lookups first where they affect the transaction.
2. Serialize the existing pending delta register; do not reconstruct the session from Personal Context, another conversation, shared-chat snapshots, or model memory when same-conversation state is available.
3. Prepare and persist the checkpoint using this protocol.
4. Keep the transaction open until readback reaches `VERIFIED` or Hiram has been given an exact required manual action.

## Structured pending delta register

While `PENDING`, organize durable changes under these buckets as applicable; omit empty buckets and never invent content merely to populate them:

- `chronology_location`: elapsed time, current time/date if established, current location, travel position, session boundary.
- `character_mechanics`: HP, XP, conditions, spell state, memorization, and other mechanical changes.
- `resources_inventory`: purse, ammunition, light/fuel, provisions, carried/stored items, significant-item state.
- `npcs_relationships`: new NPCs, changed status, promises, debts, favors, attitudes, knowledge, motives, relationship trajectory.
- `locations_factions_world`: durable location changes, faction state, alarms, resources, territory, independent consequences.
- `threads_clues_knowledge`: active/resolved threads, clues, rumors, inferences, false beliefs, player-known facts, knowledge-boundary changes.
- `dm_truth_preparation`: Established DM Truth, hidden causality, secret clocks, prepared possibilities that became durable or changed through play.
- `world_clocks_events`: scheduled events, triggered or advanced clocks, off-screen developments crossed by elapsed time.
- `rulings_sources`: new campaign ruling, source-dependent unresolved rule item, source reference required later.
- `resume_state`: exact practical resume position and immediately relevant state for the next session.
- `unresolved_pending`: facts deliberately still uncertain, unresolved decisions, deferred lookups, or unreconciled costs/rules.
- `dirty_domains`: canonical shards/indexes maintenance would need to materialize from this checkpoint.

Preserve uncertainty categories exactly. A rumor, inference, Prepared Possibility, unresolved question, or hidden truth must not change category merely because it is serialized.

## Stable transaction identity

Every real campaign checkpoint must have a stable `transaction_id` independent of checkpoint sequence.

1. Generate the ID exactly once when the transaction first reaches `PREPARED`.
2. Keep the same ID across automatic retry, concurrency reconciliation, manual fallback, and readback verification for the same logical save.
3. A new logical save gets a new ID.
4. The ID must be collision-resistant within this campaign; a UUID or UTC timestamp plus opaque suffix is acceptable.
5. Never derive transaction identity only from filename or sequence.

Recommended format: `wren-tx-YYYYMMDDTHHMMSSZ-<opaque-suffix>`.

## Idempotency / exactly-once behavior

Before creating a checkpoint for a `PREPARED` transaction, and before retrying after any ambiguous result:

1. Search or inspect canonical checkpoints for the exact `transaction_id`.
2. If none contains it, continue with normal head/concurrency validation.
3. If exactly one contains it, do not create another checkpoint. Fetch and verify that checkpoint. If it matches the prepared transaction, complete verification instead of duplicating the save.
4. If the same transaction ID exists with materially different semantic deltas, stop with an integrity error and reconcile.
5. If more than one checkpoint contains the same transaction ID, stop with an integrity error; do not guess which duplicate is authoritative.

This prevents duplicate saves when a write succeeds but acknowledgement is lost, a retry follows a transient error, or a manually transported transaction is later rediscovered.

## Canonical head and concurrency

The live checkpoint head is derived from canonical `checkpoints/`, never from a root-manifest field that can become stale between compactions.

Before `PREPARED`:

1. Fetch the current root manifest from `main` and record its blob SHA.
2. Inspect the checkpoint namespace enough to determine the highest checkpoint sequence, including administrative checkpoints.
3. Fetch the current head checkpoint when one exists and record its blob SHA/identity.
4. Determine the next unused zero-padded sequence.
5. Verify the transaction ID is not already present.
6. Reconstruct/apply any newly discovered real campaign checkpoint not part of the transaction's previously verified base.
7. If canonical state advanced since the transaction base was established, reconcile pending deltas against the new state before preparing the envelope.

Immediately before creation, the prepared parent/head identity must still be current. If the intended sequence is occupied or the head changed, discard only stale envelope metadata, not the logical pending transaction. Refetch, reconcile, choose the correct sequence, retain the same `transaction_id`, and prepare again. Never overwrite an existing checkpoint.

## Mandatory real-checkpoint envelope

Every new real campaign checkpoint must contain these metadata fields before semantic delta sections:

```text
- sequence: <zero-padded integer>
- transaction-id: <stable transaction_id>
- kind: <session-end | explicit-save | milestone | other descriptive type>
- state-change: real
- schema-version: <current schema version>
- persistence-protocol-version: 1
- snapshot-generation: <generation observed during prepare>
- checkpoint-baseline-observed: <baseline observed during prepare>
- base-root-blob-sha: <root manifest blob SHA observed during prepare>
- parent-checkpoint-sequence: <immediate prior canonical checkpoint sequence or none>
- parent-checkpoint-blob-sha: <immediate prior canonical checkpoint blob SHA or none>
- affected-domains: <compact list of dirty domains/shards>
```

Additional audit metadata may be included when useful. The semantic body must contain enough detail to deterministically apply the delta to the verified base. Avoid transcript dumping and vague instructions such as "update the NPC appropriately." Administrative diagnostics marked `state-change: none` need not use the full real-campaign envelope, but must never masquerade as campaign state.

## Parent chain semantics

Checkpoint sequence establishes order; parent checkpoint SHA establishes identity.

- `parent-checkpoint-sequence` is the immediately preceding canonical checkpoint sequence, whether real or administrative.
- `parent-checkpoint-blob-sha` is the GitHub blob SHA of that exact parent file.
- The first checkpoint may use `none` for both parent fields.

On load, sequence continuity and parent identity must agree. A mismatched parent SHA, missing expected sequence, duplicate sequence, or impossible generation/baseline relationship is an integrity failure requiring reconciliation before gameplay continues.

Historical checkpoints at or below the compaction baseline remain part of the audit chain even when their semantic deltas no longer require replay during ordinary startup.

## Root-manifest head metadata

Append-only ordinary saves intentionally do not rewrite the root manifest. Therefore the root must not present a snapshot-time checkpoint value as if it were the live current head.

If the root records checkpoint-head metadata, label it explicitly as snapshot-time metadata, for example:

- `checkpoint_head_at_snapshot`
- `real_campaign_checkpoint_head_at_snapshot`

The authoritative current head is always discovered from canonical `checkpoints/` during load/save integrity work.

## Prepare procedure

To transition from `PENDING` to `PREPARED`:

1. Resolve deferred canonical lookups required to interpret the pending transaction.
2. Reconcile the structured pending delta register into one complete logical transaction.
3. Fetch current root/head state and resolve concurrency.
4. Generate or reuse the stable `transaction_id`.
5. Verify that transaction ID does not already exist canonically; if it does, follow idempotency rules instead of creating a duplicate.
6. Choose the next unused sequence.
7. Construct the mandatory envelope plus semantic deltas, preserving player-facing/DM-only boundaries.
8. Validate that critical resource changes, chronology, NPC obligations, clues, hidden consequences, resume state, and dirty-domain routing are not omitted when applicable.

Only then is the transaction `PREPARED`.

## Automatic write and readback

For a `PREPARED` transaction:

1. Attempt to create exactly one new checkpoint at the prepared unused path.
2. If creation reports success, transition to `WRITTEN_UNVERIFIED`, not directly to saved.
3. Fetch the exact created checkpoint from canonical `main`.
4. Verify at minimum filename/sequence, exact transaction ID, `state-change: real`, snapshot generation and observed baseline, base root SHA, parent sequence and blob SHA, affected domains, every critical intended player-facing delta, every critical intended DM-secret delta, and resume/unresolved state when applicable.
5. When useful, re-list/search checkpoints to verify discoverability and transaction-ID uniqueness.
6. Only after successful verification transition to `VERIFIED`, clear pending state, and report the transaction saved.

## Automatic write failure / manual fallback

If automatic creation is blocked, rejected by the external-write safety layer, or cannot be safely completed:

1. Do not regenerate the logical transaction from memory.
2. Preserve the exact prepared payload and transaction ID.
3. Transition to `MANUAL_TRANSPORT_REQUIRED`.
4. Tell Hiram immediately that manual action is required.
5. Give the exact target path and complete ready-to-commit payload/artifact. Hiram should only transport it, not reconcile or rewrite campaign facts.
6. Do not say the transaction is saved.
7. After Hiram reports manual commit/upload, search first by exact transaction ID, fetch the discovered checkpoint, and perform the same readback verification.
8. Only `VERIFIED` clears pending state.

If the expected path becomes occupied before manual transport, do not ask Hiram to hand-edit sequence or parent metadata. Refetch/reconcile and provide a newly prepared exact payload using the same transaction ID.

## Verification failure

If readback cannot find the checkpoint, finds a different transaction ID, finds mismatched critical deltas, detects a parent/head conflict, or detects duplicate transaction IDs:

1. Transition to `VERIFICATION_FAILED`.
2. Keep the pending transaction intact.
3. State precisely what could not be verified.
4. Do not create another checkpoint blindly.
5. Search by transaction ID and inspect canonical head state before deciding whether to retry verification, reconcile concurrency, or prepare manual transport.
6. Tell Hiram the exact required action only when human intervention is genuinely necessary.

## Session end behavior

Natural session-ending language triggers transaction finalization when durable changes are pending.

1. Resolve due in-world clocks/events crossed by elapsed time into pending state where applicable.
2. Evaluate/include XP, resource, and mechanical changes required by governing campaign/source rules.
3. Prepare one complete checkpoint for the session's pending durable deltas.
4. Persist and verify it using this protocol.
5. Derive maintenance status from canonical baseline and real campaign checkpoint count after successful verification.
6. If persistence is blocked, give the exact manual transport action immediately; the session may stop narratively, but the campaign transaction remains operationally pending until verified.

## Compaction interaction

Compaction may materialize verified checkpoints into state shards and advance `checkpoint_baseline`, but it does not alter transaction identity or historical checkpoint files.

Compaction must preserve immutable checkpoint history, transaction IDs, sequence/parent audit chain, player/DM knowledge boundaries, and semantic equivalence between pre-compaction reconstructed truth and post-compaction materialized truth.

After compaction, snapshot-time root metadata may be refreshed to the checkpoint head incorporated into that snapshot. Future ordinary checkpoints still derive the live head from `checkpoints/`, not from those snapshot-time fields.
