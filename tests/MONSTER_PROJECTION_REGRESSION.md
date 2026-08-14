# Monster Projection / Encounter Runtime Regression Scenarios

These are engineering/audit tests only. They do not alter live campaign state.

## MPR-001 — First consequential use retrieves authority
Given a monster becomes consequential and no verified projection exists.
Expected: retrieve the exact active AD&D 2e monster entry and adjudicate from it.
Failure: use model memory or invent missing stats/behavior.

## MPR-002 — One-off monster need not be projected
Given an obscure creature appears once and recurrence is unlikely.
Expected: source is used directly; no projection is required solely for symmetry.
Failure: every monster appearance creates infrastructure.

## MPR-003 — Recurring monster becomes projected
Given a monster is now common in an active site/region or likely to recur.
Expected: create a compact verified projection if safely normalizable.
Failure: repeatedly perform broad source searches for the same routine fields.

## MPR-004 — Projection does not replace source
Given a nuanced special ability is marked source-text-required.
Expected: retrieve exact source wording before consequential adjudication.
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
Expected: create/update regional/site population state linked to the generic monster projection.
Failure: store population range, local numbers, faction relations, or clocks in the generic projection.

## MPR-009 — Fast repeat combat
Given a verified projection and encounter-instance state already contain the routine values needed for a combat round.
Expected: adjudicate without reopening the monster source.
Failure: source lookup every round despite valid unchanged fields.

## MPR-010 — Source change invalidates projection, not campaign history
Given governing source/version or active override changes.
Expected: rebuild/verify affected generic projection while preserving already established campaign encounter/history facts unless legitimate rules reconciliation requires otherwise.
Failure: erase campaign events or retain known-wrong source-derived fields.

## MPR-011 — Voice preload remains bounded
Given an imminent encounter with one monster type.
Expected: preload relevant projection fields, encounter state, local context, and exception locator only.
Failure: preload the full Monstrous Manual or unrelated monster projections.

## MPR-012 — Supplement availability is not activation
Given an uploaded supplement contains a monster variant but is not active for the case.
Expected: governing core/active source projection remains applicable.
Failure: silently use supplement variant because it is more specific or recently uploaded.

## MPR-013 — Projection creation does not instantiate a monster
Given a generic monster projection is created for future reuse.
Expected: no creature/population is added to campaign world state merely from projection creation.
Failure: source-derived cache becomes hidden world fact.

## MPR-014 — Encounter state can outlive combat when consequential
Given survivors escape, surrender, are captured, or become recurring individuals.
Expected: preserve relevant instance/group state and promote as appropriate.
Failure: discard or regenerate consequential survivors after encounter end.