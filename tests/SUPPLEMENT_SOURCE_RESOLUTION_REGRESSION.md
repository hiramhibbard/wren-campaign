# Supplement Source Resolution Regression Scenarios

These are engineering/audit tests only. They do not alter live campaign state.

## SSR-001 — Elf culture triggers race source
Given an elf settlement or consequential elf NPC culture is being created.
Expected: consult applicable elf specialist source after resolving active setting/adventure scope.
Failure: rely only on generic memory or ignore available specialist 2e material.

## SSR-002 — Dwarf culture trigger
Given dwarf social/material culture becomes consequential.
Expected: consult applicable dwarf specialist source when available.
Failure: treat dwarves as generic humans with cosmetic traits or skip relevant source support.

## SSR-003 — Consultation is not activation
Given a race/class specialist source is consulted for lore.
Expected: kits, optional proficiencies, alternate abilities, class limits, or other mechanics remain inactive unless separately adopted.
Failure: silently activate the book's optional rules.

## SSR-004 — Setting beats generic specialist where explicit
Given an active setting explicitly defines elves differently from the generic elf specialist book.
Expected: setting treatment governs that scope; compatible specialist detail may supplement only when non-conflicting.
Failure: flatten setting elves into generic PHBR assumptions.

## SSR-005 — Generic specialist does not leak setting material
Given generic campaign scope and a setting-specific specialist treatment exists in the library.
Expected: do not import setting-specific assumptions without active scope.
Failure: specialized contamination of generic play.

## SSR-006 — Class culture versus class mechanics
Given a wizard guild/training tradition is being fleshed out.
Expected: class specialist guidance may inform institutions and practices; alternate class mechanics/kits require activation.
Failure: treat consultation as global rules adoption.

## SSR-007 — Castle domain trigger
Given a castle construction/siege/fortification question materially affects play.
Expected: consult applicable stronghold/castle DM-domain source plus governing core/setting material.
Failure: ignore specialist source or globally load unrelated DMGR books.

## SSR-008 — Catacomb/site trigger
Given a tomb/catacomb-specific site problem becomes consequential.
Expected: consult applicable catacomb/dungeon specialist guide together with SITE_RUNTIME_POLICY.
Failure: replace persistent site runtime with generic supplement prose or ignore the specialist domain.

## SSR-009 — Arms/equipment trigger
Given unusual/repeated equipment detail matters.
Expected: consult applicable equipment guide; use exact governing source for mechanics and preserve activation status.
Failure: invent stats or silently replace core equipment rules.

## SSR-010 — Villain guide cannot script story
Given a recurring antagonist is being designed.
Expected: compatible villain guidance can deepen motives/resources/organization, but scenario-before-story remains controlling.
Failure: predetermine Wren's choices, required scenes, or villain survival.

## SSR-011 — Seafaring trigger
Given sustained shipboard travel/naval operations become consequential.
Expected: consult applicable seafaring guide and governing core/setting sources.
Failure: either ignore specialist seafaring material or silently activate a replacement naval subsystem.

## SSR-012 — Optional subsystem requires explicit scope
Given a DMGR/PHBR book introduces a substantial alternate subsystem.
Expected: treat it as optional until explicitly adopted for a defined scope.
Failure: use it merely because the book is relevant.

## SSR-013 — DM-side compatible elaboration
Given a DM-facing procedure elaborates an unresolved domain without conflicting with established player-facing mechanics.
Expected: DM may use it case-specifically when legitimate, recording scope if consequential.
Failure: either forbid all DM supplement use or silently make it campaign-wide.

## SSR-014 — No global scans
Given an ordinary scene with no specialist-domain trigger.
Expected: no PHBR/DMGR source lookup.
Failure: scan the whole supplement library every turn.

## SSR-015 — First-use targeted lookup
Given a specialist domain becomes active for the first time.
Expected: perform narrow retrieval against likely source family, resolve scope/precedence, and cache useful locators/projections.
Failure: broad library preload or repeated full searches.

## SSR-016 — Repeat-use fast path
Given the same domain/source route is already resolved and valid.
Expected: reuse cached route/projection and retrieve exact text only for exceptions.
Failure: rediscover the same book/section every scene.

## SSR-017 — Voice bounded context
Given an imminent scene implicates one supplement domain.
Expected: preload only immediately relevant specialist material.
Failure: preload entire PHBR/DMGR lines.

## SSR-018 — Scope change re-resolves, does not corrupt
Given play moves into a setting/adventure where specialist-source precedence differs.
Expected: select the newly applicable route without rewriting generic source assumptions globally.
Failure: corrupt cached generic or setting-specific source treatment.
