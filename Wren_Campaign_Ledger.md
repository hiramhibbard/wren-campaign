# Wren Campaign Ledger — Root Manifest

**Status:** Live canonical root manifest  
**Canonical backend:** GitHub  
**Repository:** `hiramhibbard/wren-campaign`  
**Branch:** `main`  
**Rules baseline:** AD&D 2nd Edition  
**Schema:** `STATE_SCHEMA.md`  
**Persistence transaction protocol:** `PERSISTENCE_PROTOCOL.md`  
**Growth and sharding policy:** `GROWTH_POLICY.md`  
**Full operating protocol:** `CAMPAIGN_BOOTSTRAP.md`

## Canonical State Metadata

- `schema_version`: **1**
- `snapshot_generation`: **1**
- `checkpoint_baseline`: **1**
- `checkpoint_head_at_snapshot`: **1**
- `real_campaign_checkpoint_head_at_snapshot`: **0**
- `migration_status`: **sharded snapshot generation 1 active**

Checkpoint `000001-persistence-protocol-test.md` is an administrative `state-change: none` test and is incorporated into the baseline. It does not alter Wren's campaign state and does not count toward maintenance thresholds.

The two checkpoint-head fields above describe the head incorporated when snapshot generation 1 was materialized; they are not a live head cache. Ordinary append-only saves do not rewrite this manifest. The authoritative current checkpoint head is discovered from canonical `checkpoints/` according to `PERSISTENCE_PROTOCOL.md`.

Current canonical truth is reconstructed as:

`materialized state files for snapshot_generation 1 + real campaign checkpoints with sequence > checkpoint_baseline`

The pre-sharding monolithic ledger remains recoverable in Git history and the earlier File Library provenance remains recovery/history only. Do not use conversational/model memory as canonical state.

## Session Start Integrity Procedure

Before gameplay:

1. Fetch and obey `CAMPAIGN_BOOTSTRAP.md`, `STATE_SCHEMA.md`, `PERSISTENCE_PROTOCOL.md`, and `GROWTH_POLICY.md`.
2. Fetch this root manifest and `state/INDEX.md`.
3. Load the Current Resume Working Set below.
4. List `checkpoints/` and apply every **real campaign** checkpoint with sequence greater than `checkpoint_baseline` in strict numerical order.
5. Validate checkpoint sequence/parent identity according to `PERSISTENCE_PROTOCOL.md`, then verify the Current Resume Packet against Wren's character/resources, chronology/location, active threads, relevant NPC state, and DM-only state.
6. If any conflict, missing canonical file, checkpoint gap, duplicate transaction, parent mismatch, or ambiguity is detected, stop and reconcile before advancing play.
7. Derive maintenance status from the baseline and real checkpoints according to `STATE_SCHEMA.md`.
8. Evaluate structural growth status according to `GROWTH_POLICY.md`; perform safe local promotions automatically and remind Hiram only when growth-driven maintenance is recommended, due, or required.

## Current Resume Packet

**Canonical snapshot:** generation 1, migrated administratively on 2026-08-13 without advancing gameplay.  
**Latest played checkpoint:** session ended 2026-08-12.  
**Play status:** Wren is staying at Mrs. Tansy's boarding house in the harbor settlement while assisting Edric Hale for several days.

### Wren — Immediate State
- Level 1 mage; XP: **0 / no awards yet**.
- HP: **3/3**.
- AC: **10**, unarmored.
- Base THAC0: **20**.
- Movement: **12**.
- Current purse: **27 gp, 4 sp, 8 cp**. This is provisional only in the narrow sense that a later sourced/rule-supported cost for Armor spell components may require reconciliation.
- Spellbook: simple book associated with/provided through the witch relationship.
- Known spell: **Armor**.
- Memorization capacity: **one 1st-level spell/day** at mage level 1.
- Intended current memorized spell: **Armor**.
- No established current injuries or conditions.
- Normal known carried baseline: **16.5 lb** before variable/unlisted contents; STR 9 remains unencumbered through **35 lb** under the recorded table.
- Boat-stored baseline: **50 ft hemp rope, hooded lantern, two one-pint lamp-oil flasks**; 24 lb fixed listed weight; 12 total hours of lantern fuel.
- Wren owns his late father's modest small coastal working boat; treasured, weathered, nonmagical, suitable for solo fishing and local coastal travel.

### Resume Position
- Wren is seated at the desk in his rented room at **Mrs. Tansy's boarding house** in the harbor settlement.
- He agreed to assist **Edric Hale** for several days and is staying locally rather than returning to his village each night.
- He is studying Edric's field journals and charts and practicing cartography.
- He has begun rudimentary field notes and a map of the voyage from his village to the harbor: coastline sketches, landmarks, harbor approach, estimated distances, and improvised hazard symbols.
- He noticed a journal reference to **unusual silence before fog** and privately connected it to the unnatural stillness he experienced while fishing. He may later ask the witch about it.
- Wren's mother is **Mara** and younger sister is **Elia**.
- Exact named campaign setting and village remain unestablished.
- Immediate unresolved rules item: whether the optional maximum-spells-per-level rule is in use.

### Active Threads
- **Edric Hale:** Wren is assisting him locally and studying his journals/charts.
- **Cartography/navigation:** Wren is beginning to learn through Edric's materials and his own field notes/map.
- **Silence before fog:** possible connection between Edric's journal reference and the unnatural stillness Wren experienced while fishing.
- **Aldrin Hale:** friendly traveling measurer/mapmaker/surveyor; Wren learned rudimentary sighting, shared fish and ale, and discussed travel, magic, and the unknown. Aldrin mentioned a reportedly half-ruined observatory in the eastern hills, about 10–12 days away on foot; he did not recruit Wren.
- **The witch/mentor:** obligation-laden background relationship and source of magical teaching; exact name and ultimate agenda are not player-established facts.
- **Character drive:** Wren strongly wants to leave the familiar coast, discover the wider world, and pursue magic/the unknown.

## Current Resume Working Set

Always load for resumed play:

- `PERSISTENCE_PROTOCOL.md`
- `GROWTH_POLICY.md`
- `state/INDEX.md`
- `state/character/wren.md`
- `state/character/inventory.md`
- `state/character/magic.md`
- `state/chronology/current.md`
- `state/threads/active.md`
- `state/clues/active.md`
- `state/locations/harbor/current.md`
- `state/npcs/edric-hale.md`
- `state/dm/campaign.md`
- `state/rulings/dm-procedure-triggers.md`

Load when immediately relevant or referenced:

- `state/npcs/index.md`
- `state/npcs/aldrin-hale.md`
- `state/locations/index.md`
- `state/rulings/adnd2e-campaign-rulings.md`
- `state/rulings/dice-protocol.md`
- `STATE_TEMPLATES.md`

Exact published rules/source content remain governed by Hiram's uploaded AD&D 2e materials.

## Canonical Routing

`state/INDEX.md` is the authoritative routing index for snapshot generation 1. Follow explicit routes first; use domain indexes where relevant; use repository search only as a fallback for fuzzy references. Current-context absence never establishes campaign absence.

`STATE_TEMPLATES.md` is the long-term operational scaffold for NPC/henchman, world-clock, encounter, faction, clue, travel, downtime, significant-item, source-registry, entity-promotion, and incremental-maintenance state. It is consulted automatically when those records become relevant.

`PERSISTENCE_PROTOCOL.md` is the normative transaction-hardening companion to `STATE_SCHEMA.md`. It governs stable transaction identity, structured pending deltas, Voice transaction continuity, exactly-once/idempotent saves, parent checkpoint identity, concurrency reconciliation, checkpoint envelopes, and readback state transitions.

`GROWTH_POLICY.md` is the normative automatic-growth companion to `STATE_SCHEMA.md`. It governs entity promotion, sharding, archival, regional/index growth, Voice working-set packets, major-transition maintenance, and the thresholds for healthy, recommended, due, and required structural maintenance.

## Knowledge Boundaries

Preserve distinctions among player-known established fact, rumor/hearsay, Wren's suspicion/inference, unresolved question, Prepared Possibility, Established DM Truth, and source canon not yet instantiated into campaign canon.

DM-only state is stored separately under `state/dm/` and must never be surfaced merely because it was loaded or verified.

## Persistence

Use the append-only checkpoint architecture in `STATE_SCHEMA.md` together with the stricter transaction rules in `PERSISTENCE_PROTOCOL.md`. Ordinary saves create one immutable checkpoint with a stable transaction ID, explicit parent checkpoint identity, structured semantic deltas, idempotency checks, and canonical readback verification.

Real checkpoints should include applicable dirty-domain routing hints from `STATE_TEMPLATES.md` so routine maintenance can update only affected shards plus necessary indexes/cross-links.

If an automatic connector write is blocked, preserve the exact prepared transaction and its transaction ID, invoke the explicit manual transport fallback, and keep all changes pending until the transported checkpoint is fetched and reaches `VERIFIED`. Do not create a second logical checkpoint merely because an acknowledgement was lost or a retry is needed.

At session start and session end, derive maintenance status from canonical checkpoint state. At **10 or more uncompacted real campaign checkpoints**, proactively remind Hiram to run maintenance in Work/Codex according to `CAMPAIGN_BOOTSTRAP.md`.

Also evaluate `GROWTH_POLICY.md` automatically at session start/end. Structural growth can recommend maintenance before the checkpoint threshold, or require maintenance if retrieval/integrity is no longer reliable. Safe local entity promotion should happen without burdening Hiram with routine infrastructure decisions.

## Migration / Provenance

- Original pre-GitHub File Library source remains recovery/history only.
- Library file id at GitHub migration: `file_00000000ba88822fbf4aa0094eb5ee58`.
- Retrieved Library version id: `1`.
- Materialized source size: 58,833 bytes; 694 lines.
- Historical SHA-256: `bad86ee53c2b987ebba9bcdd138d4757b9cbdd48bc387965575aa27a949998ef`.
- Git history preserves the complete pre-sharding monolithic GitHub ledger.
- Snapshot generation 1 migration did **not** advance gameplay, chronology, character resources, NPC relationships, clues, factions, or DM-secret truth.

## Pending Changes

- **None at snapshot-generation-1 activation.**