# Compiled Source Knowledge Layer Regression Tests

These tests validate `SOURCE_KNOWLEDGE_LAYER_POLICY.md` and `SOURCE_KNOWLEDGE_SCHEMA.md`.

They do not alter campaign state.

## SKL-001 Entity-centric retrieval
Given a query about a known monster/spell/item/entity discussed in multiple books, runtime should resolve the entity first and then applicable source assertions rather than guessing a book and broad-scanning PDFs.

Failure: book-first retrieval is required despite a verified entity route.

## SKL-002 Source remains authority
Given a verified compiled assertion that conflicts with exact uploaded source text, the uploaded source wins and the compiled assertion is invalidated/repaired.

Failure: compiled object overrides source.

## SKL-003 Multiple assertions remain separate
Given core, supplement, setting, Dragon, and adventure treatments of the same conceptual entity, ingestion preserves separate scoped assertions.

Failure: extraction flattens them into one universal statement.

## SKL-004 Availability does not activate
Given an optional supplement/Dragon assertion compiled successfully, current campaign rules do not change until the relevant activation scope is explicitly established.

Failure: compiled existence silently activates rules.

## SKL-005 Campaign state remains separate
Given a source-defined NPC/site/monster instantiated in Wren and later changed by play, campaign state records current truth while source object preserves publication baseline.

Failure: source object resets or overwrites campaign consequences.

## SKL-006 Exact-source fallback
Given a compiled assertion marked `source_text_required`, runtime retrieves the exact source locator before consequential use when nuance matters.

Failure: compact summary is treated as sufficient despite the flag.

## SKL-007 Structured deterministic use
Given a verified deterministic table/procedure with complete normalized fields, runtime may adjudicate directly from the compiled object without reopening the PDF.

Failure: redundant source scan occurs absent ambiguity/invalidation.

## SKL-008 Verification boundary
Given an automatically extracted but unverified assertion, it may assist discovery but not serve as authoritative published fact.

Failure: unverified extraction is treated as source truth.

## SKL-009 Locator integrity
Every verified assertion has an exact enough source locator to support practical readback/verification.

Failure: verified object cannot be traced to a source entry/table/section/page/article/key.

## SKL-010 Conflict metadata
When two verified source assertions conflict materially, preserve conflict/scope metadata instead of silently choosing during ingestion.

Failure: ingest process hides conflict.

## SKL-011 Supersession metadata
When a later/more specific source clearly supersedes an earlier assertion within a known scope, record the relationship without deleting historical/source provenance.

Failure: old assertion disappears or global supersession is inferred beyond scope.

## SKL-012 Relationship provenance
Typed source relationships such as `MONSTER -> APPEARS_IN -> ADVENTURE` resolve to verified provenance.

Failure: graph edge is inferred without source basis and treated as authoritative.

## SKL-013 Setting contamination protection
Given setting-specific compiled assertions, generic play does not inherit them outside their setting scope.

Failure: setting facts leak across scope.

## SKL-014 Adventure metadata is not world truth
Compiling adventure actors/sites/level/environment metadata does not seed the adventure into Wren's world.

Failure: extraction itself creates campaign facts.

## SKL-015 Magazine article granularity
Given Dragon/Dungeon PDFs, runtime can register article/adventure objects independently of issue-level file organization.

Failure: all lookup must begin by loading/scanning an entire issue.

## SKL-016 Lazy extraction
Given a correct exact-source lookup during play for a reusable fact not yet compiled, the system may create/queue a compiled object after adjudication without blocking gameplay.

Failure: play stops until source library is fully ingested.

## SKL-017 Batch extraction
Maintenance may compile large source families without creating campaign checkpoints when no campaign-world truth/rules activation changes.

Failure: source compilation is treated as a gameplay state change.

## SKL-018 Rebuildability
Loss of the compiled layer leaves uploaded source authority and Wren campaign state intact and permits rebuilding.

Failure: campaign/source truth depends solely on compiled objects.

## SKL-019 Stale source fingerprint
If the underlying uploaded source/version changes, affected compiled assertions are marked stale/reverified before consequential reliance.

Failure: stale projection is trusted silently.

## SKL-020 Voice fast path
Given likely imminent Voice needs and verified compact source objects, preload only relevant objects/fields rather than whole PDFs or the whole source graph.

Failure: Voice requires broad source preload for routine deterministic lookups.

## SKL-021 Cross-book discovery
A domain query may surface related entities/assertions across core, supplements, settings, Dragon, Dungeon, and adventures through typed tags/relationships while preserving each source's scope.

Failure: retrieval remains restricted to one guessed book at a time.

## SKL-022 No second prose rulebook
Complex copyrighted/interpretive prose is represented by short faithful summary/metadata/locator and `source_text_required` where needed rather than wholesale duplication.

Failure: compiled layer becomes a readable replacement copy of sourcebooks.

## SKL-023 Existing projections integrate
Current verified structured rules and monster projections may act as compiled source objects without immediate physical migration.

Failure: architecture requires duplicate copies of all existing projections.

## SKL-024 Source graph does not expose DM secrets
Source-layer objects are publication metadata/facts; campaign DM-only secrecy remains enforced by campaign-state/context visibility filtering.

Failure: source graph bypasses campaign knowledge boundaries.
