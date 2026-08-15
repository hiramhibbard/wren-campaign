# Wren Campaign-Local Source Inventory

Status: live routing index, intentionally partial
Authority: routing/availability metadata only; exact uploaded source remains authority for published content
Engine policy: `policies/SOURCE_INVENTORY_POLICY.md` at the engine commit bound by `CAMPAIGN_INSTANCE.md`

## Critical invariant

Absence from this partial inventory is **never** evidence that Hiram lacks a source.

Do not infer Wren's complete uploaded library from one semantic File Library search. When a relevant source/family is not yet indexed, treat that as an indexing/binding gap and perform only the bounded campaign-local discovery allowed by the engine policy.

Generic runtime:

`this inventory -> domain/scope -> source-family child index if present -> availability -> compiled fast path if sufficient -> exact local source if required -> bounded discovery/update`

## High-value source families

### Adventures
- child inventory: `state/sources/adventure-index.md`
- source registry/router: `rules/adventures/INDEX.md`
- status: active partial inventory
- declared corpus: Hiram reports the complete AD&D 2e-era Dungeon Magazine collection is present in his uploaded library; individual issue bindings remain incrementally verified.
- declared corpus: Hiram reports several additional setting-specific adventures are present; enumeration is incomplete.
- rule: Dungeon is indexed at individual-adventure level, not merely by issue container.

### Core AD&D 2e rules
- portable compiled routing: engine `rules/source-knowledge/` and `rules/sources/INDEX.md`
- Wren compatibility compiled routing: `rules/source-knowledge/INDEX.md`
- inventory state: known high-value family; exact campaign-local document bindings are not exhaustively centralized here yet.
- rule: a missing title from a search is not evidence the core source is absent; use compiled verified fast path where sufficient, otherwise bounded exact-source retrieval.

### PHBR / class and race supplements
- router: `rules/sources/INDEX.md`
- trigger: `state/rulings/supplement-source-triggers.md`
- inventory state: family registered; title/binding enumeration incremental.
- activation rule: availability never silently activates kits/options/alternate mechanics.

### DMGR / DM specialist guides
- router: `rules/sources/INDEX.md`
- trigger: `state/rulings/supplement-source-triggers.md`
- inventory state: family registered; title/binding enumeration incremental.

### Dragon Magazine
- article router: `rules/dragon/INDEX.md`
- trigger: `state/rulings/dragon-magazine-triggers.md`
- inventory state: article-level metadata/availability indexing incremental.
- rule: do not infer absence of an issue/article from a failed one-shot library search.

### Monsters / Monstrous Compendium / Monstrous Manual
- router: `rules/monsters/INDEX.md`
- trigger: `state/rulings/monster-runtime-triggers.md`
- inventory state: compiled monster coverage exists but exact source-family binding inventory remains incremental.
- rule: resolve setting/scope before generic monster source.

### Magic / spells / magic items
- compiled source layer: `rules/source-knowledge/INDEX.md`
- inventory state: partial compiled coverage; exact book/volume bindings remain incrementally discoverable.
- rule: compiled deterministic facts may be used when sufficient; nuanced/source-text-required cases escalate to exact local source.

### Settings / world sourcebooks
- campaign scope authority: `state/campaign/context.md`
- source role router: `rules/sources/INDEX.md`
- inventory state: setting/sourcebook enumeration incremental.
- rule: setting-specific treatment outranks generic material in its active scope; availability does not imply activation.

### Worldbuilding / DM generation references
- router: `rules/worldbuilding/INDEX.md`
- inventory state: partial/incremental.

## Availability semantics

Use campaign-local states consistently:
- `available`: exact local binding verified;
- `unavailable`: positively known inaccessible;
- `unknown`: exact binding not established;
- `stale`: prior binding needs reverification;
- `declared-present`: Hiram reports a corpus/family exists, but individual member bindings are not all verified.

A failed bounded lookup inside a `declared-present` corpus remains an `unknown`/binding gap unless stronger evidence establishes `unavailable`.

## Population priorities

Populate without waiting for complete source conversion:
1. adventure/Dungeon inventory — active now;
2. exact core-rulebook bindings that are repeatedly required;
3. PHBR/DMGR title/binding inventory;
4. Dragon issue/article inventory;
5. monster-source family inventory;
6. magic/spell/item volumes;
7. setting/sourcebook inventories;
8. remaining low-frequency sources during maintenance/conversion.

Promote high-cardinality families into child indexes when it materially improves routing. Do not create bookkeeping merely for completeness.

## Persistence boundary

This file and child indexes are Wren-local. Private file handles, corpus declarations, and Hiram-specific availability information must never be copied into the shared engine or another campaign.
