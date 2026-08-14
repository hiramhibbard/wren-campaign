# Wren Architecture Routing / Performance Regression Scenarios

Engineering/audit tests only. They do not alter campaign state.

## ARR-001 — Always-loaded router stays compact
Given new source/procedure capabilities are added.
Expected: `state/INDEX.md` remains primarily a path/router document; detailed policies live in their own files and are loaded only when implicated.
Failure: each new subsystem adds enough prose to make startup context grow linearly with capability count.

## ARR-002 — Trigger companions are event-driven
Given `state/rulings/dm-procedure-triggers.md` is loaded for normal play.
Expected: regional/site/monster/supplement/adventure/World Builder/Dragon companions are loaded only when their domains are implicated.
Failure: all companions are loaded/executed every turn.

## ARR-003 — Compiled source before PDF search
Given a verified in-scope compiled entity/assertion fully answers a reusable source question.
Expected: use it directly; do not reopen/broad-search the PDF.
Failure: book/PDF search remains mandatory despite adequate verified object.

## ARR-004 — Exact source escalation remains available
Given compiled content is stale, unverified, scope-ambiguous, exception-sensitive, or `source_text_required`.
Expected: escalate to exact source locator/text.
Failure: compact object is treated as infallible authority.

## ARR-005 — Index is not source object
Given derived semantic/full-text/graph index returns a candidate source entity.
Expected: resolve to verified compiled assertion or exact source before treating it as published fact.
Failure: retrieval ranking becomes authority.

## ARR-006 — Source object is not campaign state
Given a module/monster/item/location is compiled from publication.
Expected: it remains source baseline/reference until normal campaign seeding/instantiation establishes Wren-world facts.
Failure: compilation itself changes campaign canon.

## ARR-007 — Source availability is not activation
Given PHBR/DMGR/Dragon/setting optional material is compiled.
Expected: active rules profile remains unchanged unless scope is explicitly adopted or legitimately governs the case.
Failure: extraction silently changes mechanics.

## ARR-008 — Source-family registries prefer compiled metadata
Given adventure, Dragon, World Builder, or specialist metadata has already been compiled.
Expected: registry lookup uses compiled object/locator first, then targeted source search only when needed.
Failure: registry remains PDF-first and ignores populated source knowledge.

## ARR-009 — Adventure resolver is not a source-search bottleneck
Given a causal adventure opportunity occurs.
Expected: use compiled metadata/targeted published search when promising; stop after reasonable candidate review and create original material when it is the stronger path.
Failure: broad library scan is required before original creation.

## ARR-010 — Published opportunity remains first-class
Given a strong low-surgery published candidate is surfaced quickly.
Expected: it remains a genuine selectable/seedable option.
Failure: original improvisation silently disables published-content use.

## ARR-011 — World generation does not imply whole-world scan
Given one unresolved settlement/route/site fact becomes consequential.
Expected: resolve the smallest needed domain using compiled procedure/source or bounded DM creation.
Failure: World Builder/source graph causes broad world/source preload.

## ARR-012 — Monster source scope stays bilateral
Given generic core monster and specialized setting/adventure variants both exist in compiled form.
Expected: scope resolver selects the applicable assertion without contaminating either direction.
Failure: entity deduplication flattens variants into one universal monster definition.

## ARR-013 — Voice preload stays bounded
Given compiled source coverage grows large.
Expected: Voice receives only immediate character/runtime data and likely relevant small source objects.
Failure: compiled corpus growth causes proportional Voice context growth.

## ARR-014 — Current-Wren fast path is derivable, not canonical duplication
Given `wren-core-phb-fast-path.md` contains a current-Wren shortcut.
Expected: canonical Wren character/rules-option state determines applicability; shortcut is regenerated/ignored if Wren's level/ability/source scope changes.
Failure: shortcut overrides newer campaign state.

## ARR-015 — Existing projections remain usable
Given older verified DMG/monster projection files predate the source-knowledge schema.
Expected: treat them as compatible compiled assertions without mandatory duplicate migration.
Failure: source layer requires two copies of every projection.

## ARR-016 — Source corrections invalidate narrowly
Given one source assertion/locator is found wrong or its source fingerprint changes.
Expected: mark/rebuild that assertion/index and dependent runtime caches only.
Failure: broad campaign state or unrelated source corpus is rebuilt unnecessarily.

## ARR-017 — Campaign writes outrank index maintenance
Given a canonical campaign checkpoint succeeds but a derived source/index refresh fails.
Expected: checkpoint remains valid; repair index/source projection separately.
Failure: derived index failure corrupts/rolls back canonical campaign persistence.

## ARR-018 — Registry path integrity
Expected current routes exist for:
- `SOURCE_KNOWLEDGE_LAYER_POLICY.md`
- `SOURCE_KNOWLEDGE_SCHEMA.md`
- `rules/source-knowledge/INDEX.md`
- `rules/INDEX.md`
- `rules/sources/INDEX.md`
- `rules/adventures/INDEX.md`
- `rules/worldbuilding/INDEX.md`
- `rules/dragon/INDEX.md`
- all domain trigger files listed by `state/INDEX.md`.
Failure: an always-used route points to a missing/renamed file.

## ARR-019 — Regression-suite alignment
Given policy behavior changes materially.
Expected: affected regression tests are updated in the same engineering pass.
Failure: tests encode superseded behavior, such as mandatory published search before original adventure creation.

## ARR-020 — Engineering status is current
Expected: `CAMPAIGN_ENGINEERING.md` describes implemented architecture rather than obsolete pending tests/old retrieval assumptions.
Failure: fresh engineering chat reconstructs an outdated system design.
