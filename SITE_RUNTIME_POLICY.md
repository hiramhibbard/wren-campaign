# Wren Active Site / Dungeon Runtime Policy — v1

This policy governs dungeons, ruins, caves, lairs, mansions, forts, temples, ships, shipwrecks, towers, complexes, and other bounded sites whose internal state can matter across exploration and return visits.

AD&D 2nd Edition remains the governing ruleset. Exact exploration-time, encounter, surprise, detection, movement, light, listening, trap, combat, morale, and other mechanics must come from active 2e sources/rulings.

## Activation

Create or load an active-site runtime when Wren enters, commits to explore, materially interacts with, or is likely to return to a bounded site where one or more are consequential:
- layout/access and route choice;
- inhabitants/territories/patrols;
- exploration time;
- light, noise, visibility, doors, traps, hazards, or resources;
- keyed/source encounters;
- random encounter checks;
- alarms, pursuit, reinforcement, retreat, or recovery;
- persistent physical changes;
- treasure/clues whose location/ownership can change.

Do not create a full site runtime for a one-room incidental scene that cannot persist or branch meaningfully.

## Site state model

Track only as applicable:
- stable site id/name and source/adventure provenance;
- player-known and DM-only boundaries;
- current known/hidden layout, access points, blocked/opened routes;
- zones/rooms/areas with persistent state;
- current inhabitants and why they are present;
- lairs, territories, patrol routes, watch posts, sleeping/resting areas;
- social/ecological relationships among inhabitants;
- alarms, alert levels, pursuit state, defenses, reinforcements;
- environmental processes: flooding, fire, collapse, weather ingress, magical effects, rot, tides, etc.;
- light sources/darkness and relevant depletion;
- noise-producing events and who can plausibly hear/respond;
- exploration elapsed time and due checks/events;
- traps/hazards and triggered/disarmed/reset state;
- doors/locks/barriers and changed state;
- treasure/clues/items and current location/ownership;
- bodies/remains/evidence and whether discovery/decay/removal matters;
- exits, retreat routes, safe/rest areas if established;
- next reevaluation triggers for inhabitants/processes that can act independently.

## Source sites and keyed adventures

Published maps, keys, inhabitants, treasure, traps, timelines, and encounter instructions begin as source authority when the source is active.

Once instantiated into campaign play, campaign state overlays the source:
`published source state -> instantiated site baseline -> campaign consequences -> current active-site state`

Do not reread the source as though it resets rooms after Wren changes them. Use the source to understand unchanged/unvisited material and governing procedures; use campaign state/checkpoints for altered material.

## Site ecology and organization

Inhabitants should normally have a coherent relationship to the site and to each other when the source/world supports one. Use `state/rulings/creature-ecology-and-behavior.md`.

Ask only consequential questions:
- why does this creature/group occupy this area;
- what does it need from the site;
- what areas does it use and avoid;
- what is its relationship to neighboring inhabitants;
- what signs should exist before direct contact;
- what does it do when alarmed, wounded, hungry, displaced, or reinforced.

Exceptions may be intentionally strange, magical, trapped, summoned, undead, extradimensional, or otherwise ecologically abnormal. Preserve the actual source/cause rather than forcing mundane ecology onto everything.

## Exploration time

Site exploration is not timeless. Meaningful movement, searching, listening, forcing doors, resting, spell/effect durations, light/fuel, combat, recovery, and other procedures advance time according to governing 2e rules/rulings.

When elapsed time crosses a registered site or regional trigger, process it before dependent narration.

Do not make Hiram track meaningless seconds. Maintain enough temporal precision to resolve the next consequential threshold/check.

## Encounter and movement state

Random encounter checks are routed by governing site/source procedure, not by dramatic pacing desire.

Before a random encounter result is rolled, the eligible encounter content must already derive from:
- source-provided tables where active;
- currently present inhabitants/populations;
- patrol/reinforcement/activity state;
- environmental processes;
- valid special/keyed entries.

Encounter occurrence does not imply combat. Apply intent/reaction/morale/distance/surprise procedures as appropriate.

## Noise, alarms, and response

Consequential noise should be treated as a causal event when nearby inhabitants could plausibly react.

Do not automatically wake or summon the whole site. Determine propagation from established distance/layout/barriers/creature senses/source procedures and current alert state.

If an alarm becomes durable, record the changed state and downstream consequences.

## Persistent change / restocking

Sites do not reset after departure.

When Wren leaves or time passes, only active inhabitants/processes with relevant triggers are reevaluated. Possible consequences include:
- discovery/removal of bodies;
- tracking/searching for intruders;
- relocation or abandonment;
- repaired/barricaded doors;
- moved/hidden treasure;
- trap reset or modification where plausible;
- reinforcement or evacuation;
- predators/scavengers occupying vacancies;
- faction takeover;
- environmental deterioration/recovery.

Define the plausible causal space first. Use secret randomness only where multiple outcomes remain plausible. Persist consequential results.

Do not refill empty rooms merely because a random restocking table exists unless the governing source/rule and current ecology justify applying it.

## Site exit and dormancy

An active site may return to latent/dormant state when Wren leaves and no near-term process can affect current play. Preserve current durable site state; stop simulating irrelevant detail.

Re-activate when Wren returns, an actor/process reaches the site, a clue/thread depends on it, or elapsed time crosses a registered consequential trigger.

## Context / Voice

When likely play is inside an active site, Context Compiler/Voice preload should include a compact site fast-path block as applicable:
- current area and immediately connected routes;
- current exploration time / next check threshold;
- current light/resources;
- present/nearby known or DM-relevant inhabitants;
- current alert/noise/pursuit state;
- active environmental effects;
- immediate keyed/source procedures;
- next site due-event frontier entries.

Do not preload the entire dungeon key or monster book when only a bounded local slice is needed.

## Persistence

Consequential site changes are campaign state. They remain pending until persisted through normal checkpoint/readback protocol.

Site-runtime metadata that merely routes unchanged source material is infrastructure/derived context, not a substitute for source authority or campaign checkpoints.