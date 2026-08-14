# Wren Monster Projection and Encounter Runtime Policy — v1

This normative companion to `RULES_PROJECTION_POLICY.md` defines how AD&D 2e monster information is retrieved, normalized, cached, instantiated, and reused during play.

The governing uploaded AD&D 2e monster source remains authoritative. Monster projections are derived accelerators. Encounter instances and regional populations are campaign state and must never be confused with generic source data.

## Core layering

Use four distinct layers:

`uploaded active monster source -> verified monster projection -> campaign population/site group -> encounter instance`

Not every monster requires all four layers.

- **Source**: authoritative published monster entry.
- **Monster projection**: reusable normalized source facts for fast adjudication.
- **Population/site group**: campaign-specific durable group or population, if one actually becomes established.
- **Encounter instance**: the specific creatures currently encountered, with generated HP, equipment, injuries, morale context, knowledge, intent, and other temporary/persistent encounter state.

A random encounter with one group does not automatically establish a regional breeding population.

## First consequential use

When a monster type first becomes consequential and no adequate verified projection exists:

1. retrieve the exact active governing AD&D 2e monster entry from Hiram's uploaded source material;
2. use the source directly for the current adjudication;
3. determine whether a reusable projection is justified;
4. if justified and safely normalizable, create and verify the projection from that source;
5. if not justified, continue using source retrieval for that monster until reuse or latency makes projection worthwhile.

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
- source activation/scope;
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

## Source-text-required conditions

Retrieve the exact governing source instead of relying only on the projection when:
- an unusual special attack/defense interaction is not fully represented;
- spellcasting, spell-like powers, shapechanging, immunities, regeneration, aging, disease, poison, level drain, gaze, charm, possession, summoning, or other exception-heavy behavior needs exact wording;
- an adventure/setting source overrides the generic monster entry;
- the projection is missing, stale, ambiguous, unverified, or found inconsistent;
- treasure, ecology, society, or tactics depend on nuance intentionally omitted from the projection;
- a rules interaction could materially change survival or outcome and the normalized fields are insufficient.

## Encounter-instance state

When actual creatures are instantiated, create only the state needed for the encounter and likely persistence. As applicable:
- stable encounter/group id;
- monster projection/source reference;
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
2. use an applicable verified monster projection for generic reusable source fields;
3. retrieve the exact active source entry when projection fields are missing, exception-sensitive, stale, or marked `source-text-required`;
4. use broader uploaded-source search only if the exact governing entry/source cannot yet be located.

Do not reread the source every combat round when the needed values are already verified and unchanged.

## Voice / Context Compiler

When an encounter is active or imminent, preload only:
- the compact verified monster projection fields likely to matter;
- encounter-instance state for the actual creatures;
- relevant site/regional population/alert context;
- source locators/`source-text-required` flags for edge cases.

Do not preload full monster books or unrelated monster projections.

If Voice requires an unprojected exception and source retrieval is unavailable, preserve the pending lookup rather than guessing.

## Invalidation

Invalidate or rebuild a monster projection only when the underlying governing source/version changes, the projection is found incorrect/incomplete, or an explicitly active source override changes the monster for that scope.

Campaign injuries, deaths, equipment changes, population movement, or encounter outcomes do **not** alter the generic projection. They alter encounter/population state only.

## Persistence

Monster projections are derived source artifacts and are rebuildable from the uploaded sources.

Encounter-instance or population facts become durable campaign state when they materially affect play and must follow normal checkpoint/readback persistence.

Creating a generic monster projection by itself does not advance gameplay or create a monster in the world.