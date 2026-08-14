# Wren Monster Projection and Encounter Runtime Policy — v1

This normative companion to `RULES_PROJECTION_POLICY.md` defines how AD&D 2e monster information is retrieved, normalized, cached, instantiated, and reused during play.

The governing uploaded AD&D 2e monster source remains authoritative. Monster projections are derived accelerators. Encounter instances and regional populations are campaign state and must never be confused with generic source data.

Monster source selection is governed by `MONSTER_SOURCE_RESOLUTION_POLICY.md`. Resolve active setting/adventure/region/case scope before selecting a generic or specialized monster source.

## Core layering

Use four distinct layers:

`uploaded scope-resolved active monster source -> verified monster projection -> campaign population/site group -> encounter instance`

Not every monster requires all four layers.

- **Source**: authoritative published monster entry selected for the active scope.
- **Monster projection**: reusable normalized source facts for fast adjudication, with scope/provenance metadata.
- **Population/site group**: campaign-specific durable group or population, if one actually becomes established.
- **Encounter instance**: the specific creatures currently encountered, with generated HP, equipment, injuries, morale context, knowledge, intent, and other temporary/persistent encounter state.

A random encounter with one group does not automatically establish a regional breeding population.

## First consequential use

When a monster type first becomes consequential and no adequate verified projection exists:

1. determine the active campaign/setting/adventure/region/case scope;
2. resolve the governing monster source under `MONSTER_SOURCE_RESOLUTION_POLICY.md`, including relevant Monstrous Compendium, setting, annual, adventure, or core sources rather than assuming the Monstrous Manual;
3. retrieve the exact governing AD&D 2e monster entry from Hiram's uploaded source material;
4. use the source directly for the current adjudication;
5. determine whether a reusable projection is justified;
6. if justified and safely normalizable, create and verify the projection from that source;
7. if not justified, continue using source retrieval for that monster until reuse or latency makes projection worthwhile.

Gameplay must not pause merely because a projection does not already exist.

## When to create a monster projection

Create or queue a projection when one or more are true and the entry is safely normalizable:
- the monster is likely to recur in the current region/site/adventure;
- the monster belongs to a durable population or faction;
- repeated combat or reaction/morale adjudication is likely;
- the monster has compact source fields that would materially reduce repeated retrieval;
- Voice play would benefit from a compact fast-path record;
- the monster is common enough in active encounter content that repeated source lookup would be wasteful or omission-prone.

Do not create a projection merely because a monster appeared once.

## Projection fields

A projection may include only source-supported fields that are useful and faithfully normalizable. As applicable:
- stable projection id and monster/source identity;
- edition and source title;
- exact source locator;
- source family;
- active setting/adventure/region/case scope;
- source activation status;
- governing source and permitted companion sources;
- precedence/override notes;
- verification status and source fingerprint/version metadata where available;
- Armor Class;
- Movement;
- Hit Dice;
- THAC0;
- number of attacks;
- damage/attack forms;
- special attacks;
- special defenses;
- magic resistance;
- size;
- morale;
- XP value when source-supported and relevant;
- Intelligence;
- alignment;
- climate/terrain;
- frequency;
- organization;
- activity cycle;
- diet;
- number appearing;
- treasure fields;
- compact Combat behavior/tactics that can be faithfully summarized;
- compact Habitat/Society and Ecology facts that materially constrain runtime behavior;
- explicit `source-text-required` flags for nuanced abilities, exceptions, interactions, or prose that should not be flattened.

Do not reproduce the entire monster entry as a second prose monster manual.

Projection identity should be scope-aware when materially different generic and specialized treatments both matter. Do not overwrite a generic projection with a setting-specific version or vice versa; allow separate scoped projections and let the resolver choose the applicable one.

## Source-text-required conditions

Retrieve the exact governing source instead of relying only on the projection when:
- an unusual special attack/defense interaction is not fully represented;
- spellcasting, spell-like powers, shapechanging, immunities, regeneration, aging, disease, poison, level drain, gaze, charm, possession, summoning, or other exception-heavy behavior needs exact wording;
- an adventure/setting source overrides the generic monster entry;
- source precedence or scope is unresolved;
- the projection is missing, stale, ambiguous, unverified, or found inconsistent;
- treasure, ecology, society, or tactics depend on nuance intentionally omitted from the projection;
- a rules interaction could materially change survival or outcome and the normalized fields are insufficient.

## Encounter-instance state

When actual creatures are instantiated, create only the state needed for the encounter and likely persistence. As applicable:
- stable encounter/group id;
- monster projection/source reference;
- active source scope/provenance when important;
- number present;
- individual current/max HP when necessary;
- generated or source-keyed equipment/armor/weapons;
- current injuries/conditions/effects;
- current morale context and check state;
- surprise/reaction/initiative state where relevant;
- current intent/goal/orders;
- what the group knows or believes about Wren/current situation;
- leader/special individual identity;
- spells/charges/limited abilities already used;
- carried treasure versus lair/owned treasure;
- retreat/pursuit/alarm state;
- site/population/faction affiliation if established.

Do not repeatedly regenerate individual HP, equipment, spell state, morale consequences, or other instantiated facts once they have affected play.

Adventure-specific individual/group modifications belong here or in site/population state unless the source explicitly defines a reusable scoped variant worth projecting.

## Population/site-group state

Promote an encountered group into durable regional/site population state only when source/circumstances establish or support it.

Campaign population state may track:
- population/group identity;
- range/lair/site affiliation;
- approximate numbers or density as justified;
- leadership/social structure;
- goals/pressures;
- ecology/resources;
- relations with settlements/factions/other creatures;
- patrols/activity areas;
- reevaluation triggers;
- encounter-table dependencies;
- evidence/rumor footprint.

Population state belongs under regional/site runtime policy, not in the generic monster projection.

## Runtime lookup order

For a monster-related adjudication:

1. use valid encounter-instance state for already-instantiated facts;
2. determine/confirm the active monster source scope when needed;
3. use the applicable scope-resolved verified monster projection for generic reusable source fields;
4. retrieve the exact scope-resolved active source entry when projection fields are missing, exception-sensitive, stale, or marked `source-text-required`;
5. use broader active monster-source-family search only if the exact governing entry/source cannot yet be located.

Do not reread the source every combat round when the needed values are already verified and unchanged.

Do not search only the Monstrous Manual when an active setting/adventure/Compendium treatment may govern. Do not search every Compendium every round once governing scope has been resolved.

## Voice / Context Compiler

When an encounter is active or imminent, preload only:
- the compact verified scope-resolved monster projection fields likely to matter;
- encounter-instance state for the actual creatures;
- relevant site/regional population/alert context;
- governing source locator, scope/precedence metadata, and `source-text-required` flags for edge cases.

Do not preload full monster books or unrelated monster projections/variants.

If Voice requires an unprojected exception or unresolved source scope and retrieval is unavailable, preserve the pending lookup rather than guessing or defaulting blindly to core/general material.

## Invalidation

Invalidate or rebuild a monster projection only when the underlying governing source/version changes, the projection is found incorrect/incomplete, the active source scope changes materially, or an explicitly active source override changes the monster for that scope.

Campaign injuries, deaths, equipment changes, population movement, or encounter outcomes do **not** alter the generic projection. They alter encounter/population state only.

A scope change may select a different existing scoped projection without invalidating either projection.

## Persistence

Monster projections and their source-resolution metadata are derived source artifacts and are rebuildable from the uploaded sources.

Encounter-instance or population facts become durable campaign state when they materially affect play and must follow normal checkpoint/readback persistence.

Creating a generic or setting-specific monster projection by itself does not advance gameplay or create a monster in the world.