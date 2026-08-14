# Monster Projection / Encounter Runtime Regression Scenarios

These are engineering/audit tests only. They do not alter live campaign state.

## MPR-001 — First consequential use retrieves authority
Given a monster becomes consequential and no verified projection exists.
Expected: resolve active source scope, retrieve the exact governing AD&D 2e monster entry, and adjudicate from it.
Failure: use model memory, assume the Monstrous Manual without checking applicable scope, or invent missing stats/behavior.

## MPR-002 — One-off monster need not be projected
Given an obscure creature appears once and recurrence is unlikely.
Expected: source is used directly; no projection is required solely for symmetry.
Failure: every monster appearance creates infrastructure.

## MPR-003 — Recurring monster becomes projected
Given a monster is now common in an active site/region or likely to recur.
Expected: create a compact verified scope-aware projection if safely normalizable.
Failure: repeatedly perform broad source searches for the same routine fields.

## MPR-004 — Projection does not replace source
Given a nuanced special ability is marked source-text-required.
Expected: retrieve exact governing source wording before consequential adjudication.
Failure: flatten or guess the exception from the compact projection.

## MPR-005 — Encounter HP stays instance-specific
Given four creatures are instantiated with generated HP.
Expected: preserve those HP values for those creatures; generic monster projection remains unchanged.
Failure: regenerate HP each round/session or write individual HP into generic source projection.

## MPR-006 — Encounter equipment stays instance-specific
Given a patrol has generated/keyed equipment differing from another patrol.
Expected: equipment belongs to the encounter/group instance.
Failure: mutate generic monster projection to make that equipment universal.

## MPR-007 — One encounter does not create ecology
Given a wandering group appears once.
Expected: no regional breeding population/lair is inferred without source/circumstantial support.
Failure: encounter table result silently rewrites regional ecology.

## MPR-008 — Population layer remains separate
Given repeated evidence establishes a durable local population.
Expected: create/update regional/site population state linked to the applicable monster projection/source.
Failure: store population range, local numbers, faction relations, or clocks in the generic projection.

## MPR-009 — Fast repeat combat
Given a verified projection for the active scope and encounter-instance state already contain the routine values needed for a combat round.
Expected: adjudicate without reopening monster sources.
Failure: source lookup every round despite valid unchanged fields.

## MPR-010 — Source change invalidates projection, not campaign history
Given governing source/version or active override changes.
Expected: rebuild/verify affected projection while preserving already established campaign encounter/history facts unless legitimate rules reconciliation requires otherwise.
Failure: erase campaign events or retain known-wrong source-derived fields.

## MPR-011 — Voice preload remains bounded
Given an imminent encounter with one monster type.
Expected: preload relevant scope-resolved projection fields, encounter state, local context, source locator, and exception metadata only.
Failure: preload the full Monstrous Manual, every Compendium variant, or unrelated monster projections.

## MPR-012 — Supplement availability is not activation
Given an uploaded supplement contains a monster variant but is not active for the case.
Expected: governing generic/other active treatment remains applicable.
Failure: silently use supplement variant because it is more specific, newer, recently uploaded, or interesting.

## MPR-013 — Projection creation does not instantiate a monster
Given a generic or setting-specific monster projection is created for future reuse.
Expected: no creature/population is added to campaign world state merely from projection creation.
Failure: source-derived cache becomes hidden world fact.

## MPR-014 — Encounter state can outlive combat when consequential
Given survivors escape, surrender, are captured, or become recurring individuals.
Expected: preserve relevant instance/group state and promote as appropriate.
Failure: discard or regenerate consequential survivors after encounter end.

## MSR-001 — Scope first, not core first
Given play occurs in an active setting with an explicitly applicable setting-specific monster treatment and a generic Monstrous Manual entry also exists.
Expected: resolve the active setting treatment as governing for its scope.
Failure: default to the Monstrous Manual merely because it is core/general.

## MSR-002 — No specialized contamination of generic play
Given generic campaign scope and a setting-specific Compendium variant exists in the library but is not active.
Expected: use the applicable generic/core treatment.
Failure: import the setting variant merely because it exists.

## MSR-003 — No generic contamination of specialized play
Given an active setting/adventure explicitly changes a creature from its generic form.
Expected: specialized treatment remains governing for that scope.
Failure: silently fill conflicting fields from the generic Monstrous Manual and erase the specialized version.

## MSR-004 — Companion ecology may supplement only when compatible
Given an older/generic Compendium entry contains fuller ecology prose than the governing treatment.
Expected: use only non-conflicting compatible detail, with provenance if consequential.
Failure: merge superseded/contradictory mechanics or setting assumptions into the governing entry.

## MSR-005 — Annual entry requires scope resolution
Given a Monstrous Compendium Annual contains a creature originally associated with another setting/source.
Expected: determine whether its original/intended scope or explicit adoption makes it applicable before treating it as governing.
Failure: assume Annual inclusion makes the creature universally generic.

## MSR-006 — Adventure-specific individual does not mutate species
Given a module gives one named monster altered HP, spells, gear, abilities, or orders.
Expected: store those differences in encounter/site/adventure state unless the module explicitly defines a reusable variant.
Failure: mutate the generic species projection.

## MSR-007 — Separate scoped projections may coexist
Given both generic and setting-specific versions of the same monster are relevant in the campaign/library.
Expected: keep separate scope-aware projections and choose by active scope.
Failure: one projection overwrites the other globally.

## MSR-008 — Unresolved active-source conflict stops guessing
Given two active sources materially conflict and precedence is not established.
Expected: retrieve both exact entries and resolve source precedence before consequential adjudication.
Failure: choose whichever source was retrieved first or whichever version seems preferable.

## MSR-009 — Scope change selects rather than corrupts
Given Wren moves from generic-scope play into a setting/adventure scope with a different monster treatment.
Expected: resolver selects the applicable scoped projection/source without rewriting the previous projection.
Failure: mutate shared generic cache based on the new location.

## MSR-010 — Search family is broader than Monstrous Manual
Given the active scope plausibly has a setting Compendium/adventure treatment.
Expected: monster source search considers the active monster-source family, not only the Monstrous Manual.
Failure: conclude no specialized treatment exists because only the MM was checked.

## MEI-001 — 2e source always precedes ecology inspiration
Given a registered fan/5e ecology article exists for a monster.
Expected: resolve/retrieve governing AD&D 2e/setting source first and identify an actual ecology gap before consulting inspiration.
Failure: fan ecology becomes the starting definition of the monster.

## MEI-002 — 5e mechanics are rejected
Given the ecology source proposes CR scaling, legendary/lair actions, advantage/disadvantage, modern conditions, proficiency-bonus logic, or other 5e mechanics.
Expected: reject those mechanics completely unless independently supported by governing AD&D 2e material.
Failure: modern mechanics leak into Wren.

## MEI-003 — No level-balanced monster ecology
Given an ecology article suggests scaling a monster/variant to match party level.
Expected: reject the balancing premise; use governing 2e creature/world logic and legitimate encounter procedures.
Failure: monster danger is adjusted to protect or appropriately challenge Wren.

## MEI-004 — Edition-neutral ecology may be adapted
Given the source suggests a plausible diet, nesting behavior, waste pattern, predator relationship, or lifecycle detail not contradicted by 2e/setting canon.
Expected: treat it as a candidate, adapt to 2e idiom, and establish only if needed through campaign resolution.
Failure: reject useful ecology merely because the inspiration document was written in the 5e era, or accept it automatically as canon.

## MEI-005 — Inspiration cannot establish hidden truth directly
Given an anthology states a specific origin, cosmology, reproductive fact, ancient empire, religion, or universal social structure absent from governing 2e/setting sources.
Expected: keep it as a candidate unless separately resolved into campaign truth.
Failure: article text is silently promoted to Established DM Truth.

## MEI-006 — Resolved ecology produces evidence
Given a compatible campaign-specific feeding/lair/activity pattern has been established.
Expected: evidence and encounter behavior may derive causally from that resolved ecology.
Failure: evidence is copied directly from inspiration regardless of actual local state.

## MEI-007 — Generic monster projection stays source-derived
Given a fan-derived ecology idea becomes true for one local population.
Expected: store it in population/site/DM campaign state, not the generic monster projection.
Failure: local fan-inspired trait silently becomes universal species canon.

## MEI-008 — Old-school danger and agency preserved
Given modern inspiration implies a curated heroic set piece or survivability expectation.
Expected: preserve 2e reaction, morale, random danger, avoidance, retreat, low-level fragility, and no-fudging rules.
Failure: ecology enrichment changes the campaign into encounter-balanced 5e-style play.

## MEI-009 — Voice does not improvise from remembered fan lore
Given a consequential unresolved ecology question arises in Voice without source access.
Expected: defer canonical lookup/resolution.
Failure: answer from remembered anthology/5e lore and make it campaign truth.