# Wren Campaign Growth & Sharding Policy — v1

This file is a normative companion to `STATE_SCHEMA.md`. Its purpose is to make long-term campaign growth self-managing: the DM should detect when state organization needs promotion, sharding, archival, or indexing changes without Hiram having to notice or request them.

It does not change campaign facts. It governs when and how canonical state organization evolves as the campaign grows.

## Core principle

Campaign growth should make the repository wider, not individual files indefinitely longer.

The normal session working set must remain bounded even if the campaign eventually contains hundreds of NPCs, locations, factions, years of chronology, many adventures, and extensive DM preparation.

Growth management is therefore automatic infrastructure:

- ordinary play may promote small records when the promotion is local, deterministic, and does not require broad restructuring;
- maintenance/compaction evaluates structural growth signals and performs larger reorganizations;
- Hiram is proactively notified only when maintenance is recommended, due, or required.

Absence of a dedicated shard is never evidence that an entity or fact is unimportant or nonexistent. Canonical retrieval rules still apply.

## Growth evaluation cadence

Evaluate growth status automatically:

1. at session start, using the current working set, root metadata, relevant indexes, and checkpoint/replay state;
2. at session end, after a successful checkpoint;
3. during every Work/Codex maintenance run, with repository-wide visibility;
4. immediately when a file, index, or retrieval path becomes materially awkward, ambiguous, expensive, or error-prone during play.

Do not require Hiram to ask whether sharding is needed.

## Action levels

### Level 0 — healthy

No restructuring is useful. Continue normal play.

### Level 1 — automatic local promotion

Perform during ordinary checkpointing or the next safe canonical write when all of the following are true:

- the change is local and deterministic;
- it does not require moving many existing records;
- it does not create broad index churn;
- canonical readback can verify the result safely.

Examples:

- promote a recurring named NPC from an inline location/checkpoint note to an individual NPC file;
- create a dedicated faction file when a faction first acquires durable goals, resources, clocks, or relationships;
- create a significant-item record when an item gains persistent mechanical, historical, investigative, or ownership state;
- create a dedicated adventure-instance or project record when a previously simple thread becomes multi-session state;
- add a deterministic routing entry to an existing bounded index.

These promotions are infrastructure and normally require no reminder to Hiram.

### Level 2 — maintenance recommended

Recommend restructuring at the next convenient maintenance boundary when play remains safe but one or more growth signals indicate that the current layout is becoming inefficient.

Use the standard reminder:

`Wren maintenance is recommended for state organization. Current state is still safe to play from. When convenient, open Work/Codex in the Wren Project and say: "Run Wren maintenance."`

A recommendation may coincide with the ordinary 10-checkpoint maintenance reminder; do not spam duplicate reminders.

### Level 3 — maintenance due

Maintenance is due when normal checkpoint thresholds are reached or structural growth has become materially inefficient. Current state may still be safe to play from.

Use the existing standard due reminder from `CAMPAIGN_BOOTSTRAP.md` / `STATE_SCHEMA.md`.

### Level 4 — maintenance required before play

Require maintenance before further gameplay only when continued loading, retrieval, checkpoint application, or knowledge-boundary preservation is materially unreliable.

Examples include unresolved index ambiguity affecting established facts, integrity conflicts, excessive replay that cannot be reconstructed safely within the working context, circular/broken routing, or a shard so large/entangled that reliable retrieval cannot be assured.

State the exact reason and exact Work/Codex action required. Do not improvise around an integrity risk.

## Automatic promotion signals

### NPC promotion

Promote an NPC to an individual file when any of these become durable:

- the NPC recurs across scenes/sessions;
- relationship trajectory, promise, debt, favor, obligation, hostility, or loyalty matters;
- the NPC carries a clue or knowledge state that may matter later;
- the NPC has independent motives, resources, scheduled actions, or faction ties;
- repeatable mechanics, spellcasting, combat, training, travel, or henchman potential becomes relevant;
- portrayal consistency now depends on persistent personality/voice/knowledge state.

Use the significance tiers in `STATE_TEMPLATES.md` to determine record depth. Do not generate unused statistics merely because a file is created.

### Faction promotion

Create or enrich a dedicated faction record when a group acquires two or more of the following, or any one becomes materially consequential:

- persistent goals/plans;
- independent resources or capabilities;
- territory/reach;
- recurring members;
- relationships with other factions;
- a clock or scheduled off-screen action;
- a durable relationship with Wren;
- hidden/public purpose distinctions.

### Location promotion

Create a dedicated location record/directory when a place becomes recurrent, contains multiple durable entities/clues, has persistent state that can change, has keyed/prepared material, or serves as a routing hub for nearby sites.

### Significant item promotion

Promote an item out of routine inventory when it gains any durable hidden property, charge/use state, curse/intelligence, provenance, ownership history, investigative role, unusual value, quest relevance, or separate storage/location state that future adjudication must retrieve independently.

### Adventure / project promotion

Create a dedicated adventure-instance, downtime-project, research-project, journey, or similar record when the activity spans multiple sessions or maintains its own progress, clocks, costs, prerequisites, cast, locations, unresolved events, or source references.

## Sharding signals

These are intentionally heuristic rather than rigid line-count laws. Structural complexity matters more than raw size.

Recommend or perform maintenance sharding when any of the following occurs:

- a top-level index contains enough heterogeneous entries that locating the correct route requires scanning rather than direct lookup;
- an index mixes multiple mature regions or factions that can be routed first by a smaller parent index;
- a state file repeatedly requires partial retrieval because most of its content is irrelevant to current play;
- one file combines many independent entities that are now updated on different schedules;
- repository search is being used routinely for known entities because explicit indexes are no longer sufficient;
- aliases/natural references collide often enough that routing becomes ambiguous;
- a normal Voice working set would need to load substantial unrelated material merely to cover the current region/situation;
- maintenance repeatedly touches only small portions of a very large file.

Preferred hierarchy examples:

- `state/npcs/index.md` -> compact router -> regional/faction indexes -> individual NPC files;
- `state/locations/index.md` -> region indexes -> settlement/site directories -> individual location files;
- `state/factions/index.md` -> compact router -> faction records or regional faction indexes;
- `state/dm/prepared-world.md` -> region/adventure/faction-specific preparation shards;
- broad clue/thread indexes -> active-domain/arc/region shards while preserving cross-links.

Do not shard merely to achieve cosmetic symmetry. Each split should improve routing, retrieval cost, update isolation, or integrity.

## Chronology growth

Keep `state/chronology/current.md` focused on current date/time, immediate recent history, active temporal anchors, and facts needed for present adjudication.

During maintenance, archive older chronology when it no longer needs to remain in the immediate working set. Prefer bounded historical shards such as arc/session/year records depending on how the campaign develops.

Promote chronology archival when:

- current chronology contains substantial completed material irrelevant to immediate play;
- finding the current temporal state requires scanning long history;
- an arc/region/adventure has clearly ended;
- historical chronology is valuable for later retrieval but not routine startup.

Historical chronology remains canonical and searchable; archival is organization, not deletion.

## Thread and clue growth

`active` files should contain unresolved actionable state, not an ever-growing campaign history.

During maintenance:

- move genuinely resolved threads/clues to bounded resolved/history shards;
- retain cross-links needed to explain current relationships or consequences;
- preserve contradictions, retractions, rumor/inference categories, and knowledge provenance;
- never archive something merely because Wren has not pursued it recently if it remains unresolved or can still develop independently.

Recommend splitting active state by arc/region/domain when unrelated active material makes immediate retrieval noisy.

## DM-state growth

DM-only state should be split before secrecy boundaries or practical retrieval suffer.

Promote dedicated shards for mature:

- regions;
- adventures;
- factions;
- recurring antagonists;
- world clocks/event queues;
- prepared encounter ecosystems;
- hidden investigations/mysteries.

A smaller top-level DM router should point to those shards. Do not duplicate hidden truth into player-facing indexes.

## Voice working-set packets

When a region, expedition, dungeon, voyage, or active adventure grows large enough that Live Voice would benefit from preloading more than the ordinary global working set, maintenance may create or refresh a compact working-set manifest for that context.

A Voice working-set packet is routing metadata, not a second source of truth. It should identify the canonical files required for likely play, including immediate mechanics/resources, relevant NPCs/locations/factions, active threads/clues, and required DM-only state.

Create one when repeated sessions occur in the same complex context and ad hoc preloading becomes materially expensive or omission-prone. Retire or update it when the context changes.

## Major transition signals

Recommend maintenance earlier than checkpoint-count thresholds at a major transition when doing so will materially simplify future loads, including:

- leaving a mature region for a substantially different one;
- completing a major adventure or campaign arc;
- entering a large published adventure/location with its own substantial state;
- a major faction/world-state transition;
- Wren acquiring a persistent party/henchman structure;
- a campaign-calendar or world-time system becoming newly established after long relative chronology.

Do not force maintenance at every geographic move or completed minor objective.

## Maintenance audit procedure

Every Work/Codex `Run Wren maintenance` operation must evaluate, in addition to checkpoint compaction:

1. whether any inline/walk-on entities now meet promotion criteria;
2. whether NPC, location, faction, clue, thread, chronology, ruling, item, adventure/project, or DM shards are too broad or heterogeneous;
3. whether top-level indexes still route directly and unambiguously;
4. whether resolved material can move out of immediate active working sets;
5. whether current Voice/startup working sets remain bounded and situation-focused;
6. whether cross-references and knowledge boundaries remain consistent after proposed moves;
7. whether a major-transition-specific packet/index would reduce future retrieval cost;
8. whether schema/index changes require a migration note or snapshot-generation update.

Apply only changes justified by the current repository. Do not pre-create empty hierarchies for hypothetical future growth.

## Structural integrity after reorganization

Every promotion/shard/archive operation must preserve semantic equivalence and canonical discoverability.

Required checks include, as applicable:

- old natural aliases still route to the canonical record;
- no established fact is lost or duplicated into conflicting truths;
- player-facing versus DM-only knowledge boundaries remain intact;
- active/resolved status remains correct;
- cross-links are updated;
- the root/current working-set manifest references the new paths when needed;
- checkpoint reconstruction before and after maintenance yields the same current campaign truth;
- changed files and indexes receive canonical readback verification before the root baseline/generation is advanced.

## Reminder behavior

Hiram should not receive routine implementation chatter for healthy automatic local promotions.

Proactively tell him when:

- growth-driven maintenance is recommended;
- maintenance is due;
- maintenance is required before further reliable play;
- a growth reorganization fails and needs human intervention.

Once canonical state proves the condition has been resolved, stop issuing that reminder.

## Long-term target

The repository may grow very large while normal play remains small-context.

A mature campaign should be able to contain hundreds of NPCs, many regions and locations, numerous factions, long chronology, completed and active adventures, maps, items, clocks, and secrets while a normal session still loads only:

- Wren's immediate state;
- current chronology/location;
- active local threads/clues;
- relevant local NPC/location/faction records;
- required DM-only state;
- unapplied checkpoints after baseline;
- compact routing/index metadata.

If total repository growth causes the normal working set to grow proportionally, the organization has failed this policy and maintenance should restructure it.