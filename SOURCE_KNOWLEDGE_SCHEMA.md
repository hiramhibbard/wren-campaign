# Wren Compiled Source Knowledge Schema — v1

This schema operationalizes `SOURCE_KNOWLEDGE_LAYER_POLICY.md`.

It is intentionally storage-agnostic: current GitHub can hold Markdown/YAML/JSON projections; a future application may use relational tables, document storage, search indexes, or graph projections. Semantics and provenance matter more than physical representation.

## Core object model

### Source entity

Required conceptual fields:

```text
source_entity
  id                  # stable, namespaced identifier
  entity_type         # monster, spell, item, deity, rule, adventure, article, etc.
  canonical_name
  aliases[]
  tags[]
  parent_entity_id?   # optional specialization/hierarchy
  visibility          # source-public metadata; never campaign-secret by itself
```

Entity IDs should be source-layer stable and independent of campaign instance IDs.

Examples:
- `adnd2e.monster.troll`
- `adnd2e.spell.armor`
- `adnd2e.deity.<setting>.<name>`
- `dragon.article.236.<slug>`
- `dungeon.adventure.<issue>.<slug>`

### Source assertion

```text
source_assertion
  id
  entity_id
  assertion_type
  source_id
  locator
  system_edition
  publication_version?
  setting_scope?
  adventure_scope?
  domain_scope?
  source_role
  activation_requirement
  structured_data{}
  compact_summary?
  source_text_required   # boolean
  exceptions[]
  verification_status    # unverified | verified | rejected | stale
  source_fingerprint?
  supersedes[]
  conflicts_with[]
  notes?
```

`structured_data` must be shaped to the assertion type rather than becoming an untyped prose dump.

### Source relationship

```text
source_relationship
  id
  subject_entity_id
  predicate
  object_entity_id
  assertion_id
  scope?
  verification_status
```

Relationships must resolve to a source assertion or other provenance record.

### Source document

```text
source_document
  id
  title
  family              # core, PHBR, DMGR, setting, module, Dragon, Dungeon, etc.
  system_edition
  setting_scope?
  publication_metadata?
  uploaded_source_ref
  fingerprint?
  authority_role[]
```

The uploaded source reference is authoritative; this metadata object is a locator/router.

## Assertion types

Common assertion types may include:
- `stat-block`;
- `progression-table`;
- `spell-definition`;
- `item-definition`;
- `procedure`;
- `table`;
- `setting-fact`;
- `ecology`;
- `behavior`;
- `organization`;
- `relationship`;
- `geography`;
- `history`;
- `religion`;
- `culture`;
- `adventure-metadata`;
- `site-metadata`;
- `article-metadata`;
- `optional-rule`;
- `interpretive-summary`.

Add types organically when repeated structure justifies them.

## Structured payload examples

### Spell

```text
structured_data:
  level
  school_or_sphere
  components
  range
  duration
  casting_time
  area_of_effect
  saving_throw
  mechanical_effects
  special_conditions
```

If the spell text contains interactions too nuanced to normalize safely, set `source_text_required: true` and keep only faithful reusable fields.

### Monster

```text
structured_data:
  climate_terrain
  frequency
  organization
  activity_cycle
  diet
  intelligence
  treasure
  alignment
  number_appearing
  armor_class
  movement
  hit_dice
  thac0
  attacks
  damage
  special_attacks
  special_defenses
  magic_resistance
  size
  morale
  xp
  ecology_fields
```

Do not merge setting/adventure variants into the generic assertion; model them as separate scoped assertions/entities.

### Adventure metadata

```text
structured_data:
  recommended_level_or_range
  environment_tags[]
  site_types[]
  setting_assumptions[]
  major_actor_tags[]
  monster_tags[]
  theme_tags[]
  hook_assumptions[]
  source_dependencies[]
  maps_handouts[]
```

Level/range is discovery/risk metadata, not a promise to scale or gate Wren.

### Rule/procedure

```text
structured_data:
  trigger
  inputs
  deterministic_values_or_formula
  steps
  outputs
  exceptions
```

Complex prose-dependent procedures should retain `source_text_required: true`.

## Stable identity and deduplication

A single conceptual entity may have multiple source assertions.

Do not create separate core entities merely because different books discuss the same thing unless they are genuinely different variants/versions/scoped concepts.

Deduplication should use:
- normalized name/aliases;
- edition;
- setting scope;
- source-defined identity;
- explicit specialization/variant relationships.

When uncertain, preserve separate candidate entities until verification rather than collapsing them incorrectly.

## Scope and activation

Every assertion whose applicability is not universal must record scope.

`activation_requirement` examples:
- `core-default`;
- `active-setting-only`;
- `active-adventure-only`;
- `explicit-option-required`;
- `dm-case-use`;
- `inspiration-only`;
- `reference-only`.

Compiled existence never changes campaign rules profile.

## Verification states

- `unverified` — extracted or inferred but not checked against actual source.
- `verified` — checked against source/locator sufficiently for intended use.
- `rejected` — extraction was wrong or incompatible with represented identity/scope.
- `stale` — source fingerprint/version changed or provenance is no longer trustworthy.

Only `verified` assertions may serve as published authority without re-reading the source.

## Provenance locator quality

Prefer the strongest available locator:
1. stable named entry/table/section + printed page;
2. article title + issue + page;
3. adventure key/location number + page;
4. PDF page when printed locator unavailable;
5. searchable section/entry label.

The locator should make exact-source escalation cheap.

## Storage layout target

Current GitHub may use:

```text
rules/source-knowledge/
  INDEX.md
  entities/
  assertions/
  relationships/
  documents/
```

Do not create one file per tiny object if that causes repository/path overhead. Shard by domain or stable prefix when volume grows.

A future application may store the same model in database tables and build full-text/vector/graph projections from it.

## Campaign-reference pattern

Campaign state should reference source objects only when useful:

```text
source_basis:
  entity_id: ...
  assertion_id: ...
  source_locator: ...
```

Campaign state records current in-world truth separately. Never require a source object to represent campaign divergence.

## Invalidation

A source object/assertion becomes invalid or needs reverification when:
- underlying source file/version/fingerprint changes;
- extraction error is discovered;
- locator proves wrong;
- scope was misclassified;
- an assertion was merged with the wrong entity;
- a more precise source treatment changes supersession/conflict metadata.

Invalidate the affected source object/index entries, not unrelated campaign state.
