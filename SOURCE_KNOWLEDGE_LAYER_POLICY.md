# Wren Compiled Source Knowledge Layer Policy — v1

This policy defines a derived, provenance-preserving knowledge layer compiled from Hiram's uploaded published AD&D source library.

## Core principle

Do **not** recreate sourcebooks as another prose corpus.

Instead compile reusable source knowledge into structured entities, assertions, relationships, procedures, and locators that can be searched and linked independently of book layout.

Use:

`uploaded source corpus -> source ingestion/extraction -> compiled source objects -> derived indexes/relationships -> scope/precedence resolution -> campaign/runtime use -> exact source fallback when required`

The uploaded source remains the ultimate published authority.

## Separation of layers

Maintain these distinct layers:

1. **Uploaded source corpus** — authoritative published books, magazines, adventures, maps, and other source material.
2. **Compiled source knowledge layer** — verified normalized objects derived from those sources.
3. **Derived retrieval indexes/graph projections** — rebuildable accelerators over compiled objects and canonical campaign state.
4. **Campaign rules/source profile** — which source assertions are active for a case/domain/setting/character/campaign.
5. **Canonical Wren campaign state** — what is actually true in this campaign.
6. **Runtime caches/context** — disposable task-specific values and working context.

Do not merge published-source truth with campaign truth merely because a source object exists.

## Why entity-centric rather than book-centric

Book organization is optimized for reading, not runtime adjudication.

The compiled layer should organize reusable material by entity/domain while retaining exact source provenance. Examples:
- monster;
- monster variant;
- spell;
- magic item/artifact;
- mundane equipment;
- class;
- kit;
- race/species;
- proficiency;
- deity;
- priesthood;
- faction/organization;
- named NPC;
- place/region/plane;
- culture;
- historical event;
- adventure;
- adventure site/location;
- encounter/table;
- hazard/trap;
- treasure table;
- rule/procedure;
- worldbuilding procedure;
- ecology assertion;
- magazine article;
- map/handout/source asset.

A source object may collect assertions from many books without flattening them into one universal answer.

## Source assertions, not flattened truth

When multiple publications discuss the same entity, preserve separate assertions.

A source assertion should retain, as applicable:
- stable assertion ID;
- entity ID;
- source ID/title;
- exact locator: chapter/section/page/table/entry/article/map key/etc.;
- edition/system;
- publication date/version when relevant;
- setting/adventure/domain scope;
- source role;
- activation requirement;
- normalized structured data;
- compact semantic summary;
- whether exact source text is required for use;
- exceptions/conditions;
- supersession relationship;
- known conflict relationship;
- verification status/fingerprint.

Do not silently reconcile contradictory assertions during ingestion. Scope/precedence resolution occurs at runtime or campaign configuration time.

## Source relationships

Compiled objects may carry typed relationships such as:
- `SPELL -> BELONGS_TO_SCHOOL -> SCHOOL`;
- `MONSTER -> APPEARS_IN -> ADVENTURE`;
- `MONSTER_VARIANT -> SPECIALIZES -> MONSTER`;
- `DEITY -> HAS_PRIESTHOOD -> PRIESTHOOD`;
- `NPC -> MEMBER_OF -> ORGANIZATION`;
- `LOCATION -> LOCATED_IN -> REGION`;
- `ARTICLE -> EXPANDS -> ENTITY`;
- `ITEM -> ASSOCIATED_WITH -> FACTION`;
- `ADVENTURE -> REQUIRES_OR_ASSUMES -> SETTING`;
- `RULE -> MODIFIES -> RULE_DOMAIN`;
- `SOURCE_ASSERTION -> CONFLICTS_WITH -> SOURCE_ASSERTION`;
- `SOURCE_ASSERTION -> SUPERSEDES -> SOURCE_ASSERTION`.

Relationships are source-derived assertions with provenance. A derived graph does not create source canon absent an assertion.

## Extraction coverage

The long-term target is broad extraction of **reusable** source knowledge, not selective extraction limited only to currently active Wren material.

Prioritize high-value, highly reusable, or highly structured content first:
- deterministic rules tables;
- monster stat/ecology fields;
- spells;
- items;
- equipment;
- class/race/kit/proficiency data;
- encounter/treasure tables;
- procedures;
- setting entities and relationships;
- adventure metadata, site/actor relationships, level/risk/environment tags;
- Dragon article metadata and reusable claims;
- Dungeon adventure metadata and reusable site/scenario objects.

Complex interpretive prose may be represented by a compact summary, tags, relationships, and exact locator rather than copied wholesale.

## No second prose rulebook

Do not duplicate long copyrighted/interpretive prose simply to avoid source retrieval.

Prefer:
- normalized fields;
- short faithful summaries;
- structured procedures/tables;
- exception flags;
- semantic tags;
- exact source locator;
- `source-text-required: true` when nuance or wording matters.

Exact source text remains the slow-path authority for ambiguous interactions, nuanced setting prose, adventure room text, unusual exceptions, atmosphere, long essays, and anything whose meaning would be materially lost by normalization.

## Authority and activation

Compiled-object existence never activates a source.

The runtime must still resolve:
`campaign facts -> active adventure/setting scope -> explicitly adopted supplement/optional scope -> governing core/source rule -> compatible secondary/inspiration material`

A more specific object does not automatically outrank an active governing source merely because it has more detail.

## Verification requirements

A compiled object/assertion may be marked `verified` only when its normalized content can be traced to the actual uploaded source and checked against the source locator.

Machine/model extraction without source confirmation is `unverified` and cannot be used as authoritative published fact.

For deterministic fields used in consequential mechanics, verification should be strict enough to catch table alignment, footnotes, exception clauses, and edition/scope errors.

## Runtime lookup order

For source-dependent questions prefer:
1. valid runtime cache;
2. direct compiled entity/assertion by stable ID;
3. structured relationship/domain query over compiled objects;
4. full-text/semantic index over compiled objects;
5. exact uploaded source section referenced by the object;
6. broader uploaded-source search only when no adequate object/locator exists.

If exact wording or an exception is required, escalate directly from the compiled object to its source locator.

## Ingestion and lazy/eager balance

The architecture supports both:
- **eager batch extraction** during maintenance/offline processing for large source families;
- **lazy extraction** when play/source lookup discovers a reusable object not yet compiled.

Do not require ordinary gameplay turns to perform broad source-library ingestion.

A useful object discovered during play may be compiled after correct adjudication so future lookups are cheaper.

## Campaign integration

Compiled source objects are not campaign state.

When a source object is instantiated in Wren's world, canonical campaign state should reference the source object/assertion/provenance where useful while recording the campaign-specific current truth and divergences.

Once campaign state diverges from a source baseline, campaign state wins for the affected in-world instance.

## Adventure integration

Adventure objects may include reusable metadata such as:
- source/issue/module;
- setting;
- geography/environment;
- level/risk band as source metadata, not a balance promise;
- site types;
- important actors/factions/monsters;
- key themes/tags;
- assumed hooks;
- source dependencies;
- maps/handouts;
- compact scenario summary;
- source locators.

Do not flatten complete keyed adventures into globally active world facts. Published adventure material becomes Wren campaign truth only through normal seeding/activation policy.

## Magazine integration

Dragon and Dungeon should be indexed primarily at article/adventure/object level rather than only as issue PDFs.

Issue/date/title remain provenance metadata; runtime retrieval should normally query subject/entity/article/scenario objects.

## Context Compiler / Voice

The Context Compiler should prefer compact compiled objects over broad PDF excerpts whenever the object is verified and sufficient.

Voice preload may include the exact small source objects likely to matter in the immediate scene. This is one of the primary latency benefits of the layer.

Do not preload the whole compiled source graph.

## Rebuildability

The compiled source layer is derived and rebuildable from the uploaded source corpus plus extraction definitions.

Loss/corruption of the compiled layer must not destroy campaign truth or published-source authority.

Store source/version fingerprints sufficient to identify stale compiled objects after source replacement or correction.

## Maintenance and performance

Maintenance may batch-extract high-value source families, rebuild indexes, detect duplicate entities, create relationship edges, validate locators, and reverify objects.

Observed repeated PDF search, repeated scanning of the same source sections, cross-book discovery friction, or Voice latency are signals to expand compiled coverage.

## Copyright / storage discipline

The layer is for Hiram's private campaign runtime and should preserve structured facts, short summaries, and locators rather than wholesale source reproduction.

The architectural goal is fast retrieval and faithful normalization, not creation of a substitute readable copy of the books.
