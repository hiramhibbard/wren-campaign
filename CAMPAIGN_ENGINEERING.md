# Wren Campaign Engineering

Durable engineering/status layer for Wren's campaign runtime. This file records architecture decisions, implementation status, known limits, audits, and future validation work. It must not duplicate live campaign truth, DM secrets, sourcebook prose, or session history.

## Authority

- Campaign truth: root/state/checkpoints under `STATE_SCHEMA.md` and `PERSISTENCE_PROTOCOL.md`.
- Runtime bootstrap: `CAMPAIGN_BOOTSTRAP.md`.
- Published authority: Hiram's uploaded source corpus.
- Compiled published-source acceleration: `SOURCE_KNOWLEDGE_LAYER_POLICY.md` / `SOURCE_KNOWLEDGE_SCHEMA.md`.
- Working-context assembly: `CONTEXT_ARCHITECTURE.md`.
- Growth/maintenance: `GROWTH_POLICY.md`.

Architecture work does not advance gameplay unless Hiram explicitly resumes play. Infrastructure/source compilation normally creates no real campaign checkpoint unless it also changes campaign truth or an active rules decision.

## Engineering bootstrap

When Hiram asks to improve/audit the campaign system:
1. load normal canonical bootstrap/root/index;
2. load this file;
3. inspect exact implementation files before editing;
4. preserve campaign truth and player/DM visibility boundaries;
5. treat current repository state as implementation authority;
6. verify writes by canonical readback before reporting completion.

For gameplay, the single word `Wren` remains the shorthand for canonical load/reconstruction + practical Voice-ready working-set preparation without advancing play.

## Current architecture

### Canonical campaign backend / persistence
- GitHub `hiramhibbard/wren-campaign`, `main`.
- Root ledger is bounded resume/manifest, not encyclopedia.
- Materialized state + ordered post-baseline checkpoints reconstruct current truth.
- Real saves use stable transaction IDs, explicit parent identity, idempotency checks, retry/reconciliation discipline, and readback verification.
- Write acknowledgement alone is not saved state.
- Manual transport fallback preserves exact prepared transaction if connector write is blocked.
- Real campaign checkpoints have been exercised successfully; the old "first real checkpoint test pending" note is retired.

### Context / performance
- `state/INDEX.md` is a compact always-loaded deterministic router.
- Event-driven procedure routing prevents linear per-turn scans as capabilities grow.
- Context Compiler loads only immediate canonical state, relevant DM state, exact relevant source objects, and recent conversation.
- Voice uses a compact fast-path block and only relevant verified source objects/projections.
- Broad PDF/source search is a slow path.

### Compiled source knowledge
Implemented:
- `SOURCE_KNOWLEDGE_LAYER_POLICY.md`
- `SOURCE_KNOWLEDGE_SCHEMA.md`
- `rules/source-knowledge/INDEX.md`
- `tests/SOURCE_KNOWLEDGE_LAYER_REGRESSION.md`

Model:
`uploaded source -> verified source entities/assertions/relationships -> retrieval indexes -> scope/precedence -> campaign/runtime use -> exact source fallback`

Principles:
- organize by reusable entity/domain, not book layout;
- preserve multiple scoped assertions rather than flattening conflicting books;
- source-object existence never activates optional/supplement/setting rules;
- verified structured facts may be used directly;
- nuanced/exception-sensitive material carries exact locator / `source_text_required`;
- no second prose copy of the books;
- layer is rebuildable from uploaded sources.

Initial populated core coverage now includes:
- PHB source document;
- DMG source document;
- Monstrous Manual source document;
- Armor spell structured definition;
- wizard XP/Hit Dice progression;
- wizard spell-slot progression;
- INT 18 source row;
- core character encumbrance breakpoints;
- wizard THAC0 progression;
- existing DMG wilderness encounter and ship-weather projections registered conceptually as compiled source assertions.

Population strategy is mixed:
- lazy after useful play lookups;
- batch/offline/maintenance extraction for high-value source families.

### Rules and supplements
- `RULES_PROJECTION_POLICY.md` remains the specialized deterministic-mechanics projection policy inside the broader source-knowledge architecture.
- `SUPPLEMENT_SOURCE_RESOLUTION_POLICY.md`: domain/scope consultation without automatic activation.
- PHBR/DMGR specialists are event-driven.
- Active setting/adventure treatment protects specialized scope from generic contamination.
- Rules/source dependency routing now prefers verified compiled assertions/projections before source PDF lookup.

### Monsters / ecology
- Scope-first monster source resolver prevents generic/specialized cross-contamination.
- Monster projections separate species/source definition from campaign population/site/encounter-instance state.
- Ecology order: governing 2e source -> applicable Dragon ecology -> other compatible inspiration -> campaign-specific resolved ecology.
- No hostile population is generated merely to produce combat.

### Adventure generation
- `ADVENTURE_OPPORTUNITY_POLICY.md` treats published modules/Dungeon material and original DM creation as complementary first-class paths.
- Dungeon Magazine remains actively considered when a likely fit exists.
- Published search is targeted and may terminate when no strong fit appears; it is not a bottleneck on original creation.
- Scenario-before-story: no forced hooks/endings.
- No automatic level scaling.
- Gross danger is legible through causal in-world evidence when plausible, never a level gate.
- Published/original scenarios persist and participate in normal world motion after becoming consequential.

### World Builder
- *World Builder's Guidebook* is active DM-generation machinery for unresolved world space.
- Microscopic/local approach is default for current Wren play.
- Generate only smallest necessary causal truth.
- Constraints precede random generation; valid consequential rolls are accepted.
- World Builder procedures can themselves be compiled into reusable source objects without generating campaign facts.

### Dragon Magazine
- Dragon is an article-level secondary source family, not a globally active rulebook.
- Automatic targeted consultation for setting support, ecology, religion, magic, NPCs/organizations, DM procedures, worldbuilding, and adventure components.
- Article-level compiled metadata/relationships are supported; batch metadata extraction is appropriate during maintenance/offline work.
- Optional mechanics remain activation-sensitive.

### Regional runtime / DM craft
- Home Coast bounded regional runtime + active world clocks implemented.
- Site runtime preserves changed sites; publication baseline never resets campaign consequences.
- DM craft is scenario-before-story, observation-before-interpretation, intent-before-initiative, no pixel hunting, no fudging.
- NPC generation/portrayal, knowledge reliability, perception/evidence, creature ecology, encounter/weather routing are implemented as event-driven procedures.

## 2026-08-14 rapid-change integrity/performance audit

Audit scope included current root/policy routers, `state/INDEX.md`, `rules/INDEX.md`, source registries, trigger directory, regression suite, Context Compiler, dependency registry, compiled-source schema/registry, and initial source extraction paths.

### Problems found and corrected

1. **`rules/INDEX.md` lagged behind new architecture.**
   - Fixed: now routes compiled knowledge, Dragon, World Builder, published-or-original adventure flow, and current populated objects.

2. **Derived-index policy could be read as forbidding rich compiled source objects.**
   - Fixed: explicit separation between compiled source objects, retrieval indexes, and runtime caches.

3. **Context Compiler knew structured rule projections but not general compiled source entities.**
   - Fixed: source-object-first path now covers rules, monsters, items, setting, adventures, Dragon, World Builder, etc.

4. **Rules dependency registry was projection-centric.**
   - Fixed: dependency routing now prefers verified compiled assertions/projections, exact source only when needed.

5. **World Builder regression test still required published search before original creation.**
   - Fixed: aligns with current source-or-create policy.

6. **Adventure regression suite did not cover original creation freedom / search termination.**
   - Fixed: expanded published-or-original coverage and compiled-adventure metadata fast path.

7. **Adventure, Dragon, World Builder, and specialist source registries were still primarily PDF-search-first.**
   - Fixed: registries now prefer compiled object/article/adventure metadata and use targeted source search as fallback.

8. **Always-loaded `state/INDEX.md` had accumulated duplicated explanatory prose.**
   - Fixed: compacted into a route-focused index while preserving all current paths and invariants. This reduces startup/context overhead as systems expand.

9. **Engineering status itself was stale.**
   - Fixed by this revision; obsolete "first real checkpoint pending" and pre-source-knowledge assumptions removed.

### Integrity checks passed

Confirmed current repository paths exist for:
- regional/site/monster/supplement/adventure/World Builder/Dragon trigger companions;
- all current regression suites;
- `rules/adventures`, `rules/dragon`, `rules/worldbuilding`, `rules/source-knowledge`, `rules/sources`, monster/encounter/travel registries;
- source-knowledge policy/schema/registry;
- current Context/Derived Index/Rules policies;
- PHB/DMG/Monstrous Manual source-document records.

No broken canonical campaign-state path or gameplay checkpoint dependency was found in this audit.

## Performance invariants going forward

1. **No capability scan per turn.** Route event/domain first.
2. **No book-first lookup when an entity route exists.** Stable entity/assertion -> scope -> source fallback.
3. **No duplicate source storage.** Existing projections can satisfy source-knowledge schema conceptually.
4. **No broad source scan for known locators.** Exact source locator first.
5. **No exhaustive adventure search.** Small candidate shortlist, then original creation if appropriate.
6. **No whole-magazine preload.** Article/entity metadata first.
7. **No whole-world generation.** Activation horizon + minimum useful truth.
8. **No compiled graph preload.** Context Compiler selects small relevant slices.
9. **No indexing as authority.** Index -> verified object/canonical state.
10. **No source compilation as campaign canon.** Source object and Wren instance remain separate.

## Source-population roadmap

Continue actual compiled-source extraction by expected runtime value rather than cover order:

1. remaining current-character/core combat/save/ability/proficiency fast-path mechanics;
2. common/core movement, exploration, light, resource, surprise/distance/reaction procedures;
3. active-region / candidate-adventure monsters;
4. frequently useful spells, mundane equipment, magic items;
5. PHBR/DMGR specialist entities and procedures;
6. adventure/module/Dungeon metadata for cheap candidate filtering;
7. Dragon article metadata and entity relationships;
8. setting entities/relationships once a setting becomes active;
9. World Builder reusable procedures/tables.

Batch extraction should use domain shards/machine-readable batches rather than millions of tiny Markdown files.

## Remaining validation / optimization work

- Continue source population; architecture is active but corpus coverage is still small relative to Hiram's library.
- As extraction volume grows, measure whether GitHub path/file overhead warrants larger machine-readable shards.
- Add external full-text/vector/graph projection only when deterministic routers + compiled object registry stop being sufficient; do not add infrastructure merely because the schema supports it.
- Validate Voice with a session that uses compiled PHB fast-path values without PDF retrieval, then forces one source-text-required escalation.
- During Work/Codex maintenance, audit source fingerprints/verification and batch-extract high-value source families alongside normal campaign compaction when useful.

## Known operational limitations

- GitHub/connected tools may be unavailable during Live Voice; preload + deferred lookup remain necessary.
- Connector writes can occasionally fail/stale; persistence retry/idempotency/fallback rules apply.
- Current compiled-source population is GitHub-backed and manually/model-extracted; large-scale corpus ingestion will eventually benefit from an offline/application pipeline with automated extraction + verification tooling.
- Exact source prose/maps remain outside compiled objects when structured normalization would lose important meaning.

## Decision-log statuses

Use: Proposed / Accepted / Implemented / Deferred / Rejected.

Current:
- **Implemented:** compiled source entity/assertion architecture and initial real population.
- **Implemented:** published-or-original adventure routing.
- **Implemented:** World Builder and Dragon event-driven source resolvers.
- **Implemented:** source-object-aware Context Compiler/dependency routing.
- **Implemented:** current rapid-change integrity/performance audit and router compaction.
- **Accepted / ongoing:** continued batch/lazy source extraction.
- **Accepted / validation pending:** dedicated Voice latency test of compiled-source fast path.
- **Deferred:** stronghold/domain/mass-combat/advanced naval/planar/sage/spy/disease/aging/etc. until causally relevant unless batch extraction cheaply captures reusable metadata.
- **Deferred:** setting-specific deep indexing until a setting is active, while generic source metadata may still be compiled in advance.

## Design principle

Prefer infrastructure that makes the game table disappear into the background: direct canonical routing, entity-centric source lookup, bounded working context, causal world motion, exact source fallback only when needed, and durable persistence. Optimization should reduce interruption and correctness risk rather than add machinery for its own sake.
