# World Builder Runtime Regression Scenarios

Engineering/audit tests only. They do not alter live campaign state.

## WBR-001 — Microscopic default
Given Wren is operating in the Home Coast with only local anchors established.
Expected: resolve new local details from the smallest relevant Chapter Five/local procedure and expand outward only as needed.
Failure: generate the planet/continent/kingdom for completeness.

## WBR-002 — Existing canon constrains generation
Given a table result would contradict Lowcove being a small coastal village or the established Home Coast climate.
Expected: exclude the contradictory outcome before consequential rolling/use.
Failure: overwrite canon because a table produced it.

## WBR-003 — Valid consequential roll is accepted
Given constraints define several valid outcomes and a genuine secret roll selects one.
Expected: accept the result and persist if consequential.
Failure: reroll because another result would be more dramatic/convenient.

## WBR-004 — Unneeded detail remains unresolved
Given Wren is having breakfast at home and no action depends on national government, exact regional population, or continental geography.
Expected: leave those facts unresolved.
Failure: generate them merely because the Guidebook supports them.

## WBR-005 — Bridgeford activation is bounded
Given Wren first travels to or investigates Bridgeford.
Expected: establish only route/terrain/settlement/social/resource facts needed for current play; do not silently populate the whole province.
Failure: fully map and census the region before the first relevant scene.

## WBR-006 — Setting source precedence
Given a published campaign setting becomes active and explicitly defines a relevant geography/culture fact.
Expected: setting source governs; Guidebook fills only compatible unresolved gaps.
Failure: random generation overwrites setting canon.

## WBR-007 — Specialist handoff
Given new world generation requires detailed elf culture or castle construction.
Expected: use Guidebook for structural need, then consult the appropriate specialist source under supplement routing.
Failure: either ignore the specialist source or activate all of its optional mechanics.

## WBR-008 — Adventure handoff
Given local campaign-area generation requires an adventure site.
Expected: trigger targeted published-adventure/Dungeon search before building a large original scenario; use original material if published fit is poor.
Failure: never consider available published scenarios or force one despite bad fit.

## WBR-009 — Monster ecology handoff
Given a generated wilderness area needs a durable creature population.
Expected: resolve monster source and ecology before establishing population/world effects.
Failure: roll a monster name and treat it as an established breeding population without ecological support.

## WBR-010 — Character-based world building does not protagonist-warp world
Given Wren's background raises an unresolved institutional question.
Expected: generate only surrounding context implied/needed by his established history.
Failure: make unrelated geography/factions exist solely to center Wren.

## WBR-011 — Situation-based generation follows causality
Given the coastal magical phenomenon requires a newly resolved consequence/location relationship.
Expected: derive possibilities from established phenomenon reach/behavior and active geography before rolling.
Failure: introduce arbitrary phenomenon effects unrelated to existing causal constraints.

## WBR-012 — Historical minimum truth
Given a clue depends on who built a ruin.
Expected: establish only enough history to support the consequential clue and future consistency.
Failure: write a complete ancient chronology unless needed.

## WBR-013 — Knowledge boundary
Given the DM establishes a hidden local fact via generation.
Expected: keep it DM-only until Wren legitimately learns evidence/report/truth.
Failure: narrate generated DM Truth as automatic player knowledge.

## WBR-014 — Paper notebook not duplicated
Given Guidebook recommends maps, NPC logs, adventure records, time notes, monster notes, and motivations.
Expected: route these categories to existing Wren state/assets/rules/checkpoint architecture.
Failure: create a second conflicting canonical notebook.

## WBR-015 — Performance bounded
Given an ordinary turn has no unresolved consequential world detail.
Expected: no Guidebook source lookup.
Failure: scan world-building tables every turn.

## WBR-016 — Voice defers exact lookup
Given a consequential new world fact is required during Voice but the source procedure is unavailable.
Expected: preserve pending lookup and resolve in text mode.
Failure: invent a permanent world fact from memory.

## WBR-017 — Home Coast geography boundary survives
Given Guidebook procedures could generate roads/rivers/distances among Lowcove, Bridgeford, Saltwick, and eastern hills.
Expected: do not establish them until current play/source causality needs them; checkpoint 000005 boundary remains intact.
Failure: fill the blank map proactively just because generation is available.

## WBR-018 — No worldbuilding quota
Given the existing Home Coast already supplies sufficient people/places/threads/adventure opportunities for current play.
Expected: do not add settlements, ruins, monster populations, factions, or crises merely to make the world feel fuller.
Failure: generate new content without causal need.
