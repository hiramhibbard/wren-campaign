# Regional Runtime Regression Scenarios

Purpose: compact engineering/audit scenarios for validating that regional runtime, world motion, encounter routing, weather, lore generation, and information reliability are triggered by explicit state/procedures rather than DM recollection or pacing desire.

These are **not campaign events** and do not alter Wren's canonical state when reviewed. They are acceptance tests for future maintenance, audits, Context Compiler work, or application implementation.

## RRT-001 — Safe settlement fast path

Given:
- Wren spends one ordinary hour inside Lowcove;
- no keyed event, active actor trigger, alarm, public incident, or continuing weather consequence is due.

Expected:
- no wilderness random encounter check;
- no source lookup merely because time passed;
- only due clocks/effects/resources, if any, are evaluated.

Failure if:
- a monster/random encounter check occurs solely because the DM wants activity;
- every regional system is rescanned.

## RRT-002 — Wilderness check routing

Given:
- Wren begins meaningful wilderness travel in a region whose terrain classification and encounter profile are established;
- elapsed travel crosses a check slot in the governing verified encounter projection.

Expected:
- applicable terrain/check slot is selected;
- local encounter content exists or is prepared before the encounter-result roll;
- secret occurrence roll is made using the governing chance;
- no unrelated region/source is loaded.

Failure if:
- check is skipped because no combat was planned;
- generic monster content is invented after seeing the occurrence roll.

## RRT-003 — Settled-land modifier safety

Given:
- travel is through a settled/patrolled wilderness route;
- a population-density modifier would apply under the core DMG procedure.

Expected:
- modifier is used only if local encounter content has been specially prepared to reflect settled-land traffic.

Failure if:
- increased encounter chance is applied to an all-monster wilderness table.

## RRT-004 — Due-event frontier

Given current runtime anchor day 0 and Home Coast active clocks:
- +3 day elements exist;
- +7 day elements exist.

When:
- exactly 3 in-world days elapse.

Expected:
- only elements due by +3 days are evaluated;
- +7 day elements are not advanced merely because world-motion processing ran;
- each still-active resolved element receives its next trigger.

Failure if:
- all factions/processes are rescanned or advanced.

## RRT-005 — Immediate event trigger

Given:
- an active actor has a later scheduled reevaluation;
- Wren creates an established event listed as an immediate trigger for that actor.

Expected:
- actor reevaluates immediately without waiting for cadence;
- later schedule is reconciled/replaced as appropriate.

Failure if:
- only elapsed-time clocks can advance actors.

## RRT-006 — Migration invalidates encounter content

Given:
- a creature population is canonically active outside a region;
- a valid world-motion resolution moves it into that region.

Expected:
- population's new range is persisted;
- only affected regional encounter ingredients/weights and related rumors/ecology dependencies are invalidated/refreshed;
- unrelated regions are unchanged.

Failure if:
- the encounter table creates the migration retroactively;
- every campaign encounter table is rebuilt.

## RRT-007 — No combat pacing quota

Given:
- Wren has had no combat for an extended span;
- no source, actor, encounter roll, reaction, consequence, or adventure state creates a hostile encounter.

Expected:
- no hostile population/encounter is created merely to provide combat.

Failure if:
- absence of recent combat is itself used as a trigger.

## RRT-008 — Dangerous result not suppressed

Given:
- a legitimate encounter/world-state procedure produces danger;
- Wren is low level.

Expected:
- result is resolved using source/world logic, distance, surprise, reaction, morale, avoidance, and player choice;
- no plot-protection cancellation or fudging.

Failure if:
- result is quietly removed solely because it may be dangerous.

## RRT-009 — Sea-weather activation

Given:
- Wren undertakes consequential sea travel;
- current season is canonically known.

Expected:
- core ship-weather projection is used where applicable;
- weather persists for the relevant daily interval;
- movement/safety effects route correctly;
- exact source is retrieved for unsupported craft/seaworthiness/off-course details.

Failure if:
- weather is regenerated every scene;
- inactive supplement weather silently overrides core.

## RRT-010 — Inconsequential weather fast path

Given:
- Wren spends a quiet indoor day;
- no environmental process or downstream system depends on daily weather.

Expected:
- no unused daily weather record/roll is required.

Failure if:
- weather tables are rolled simply because a day passed.

## RRT-011 — Sincere mistaken report

Given:
- an NPC has plausible but imperfect access to an event;
- context/random resolution establishes that the NPC sincerely believes a false explanation.

Expected:
- information access, belief, communicative intent, and objective truth remain separate;
- NPC may truthfully report what they believe while being objectively wrong;
- result becomes durable if consequential.

Failure if:
- sincerity is treated as proof of truth;
- NPC is retroactively made deceptive to preserve mystery.

## RRT-012 — Deferred rumor truth

Given:
- an NPC repeats a rumor;
- no clue, action, clock, encounter, or causal dependency currently requires the rumor's underlying truth.

Expected:
- rumor/source/belief can be preserved while objective truth remains unresolved.

When later a consequential clue depends on it:
- establish the minimum required underlying truth before presenting the consequence.

Failure if:
- every rumor receives a secret encyclopedic answer immediately;
- truth is decided after the dependent clue is narrated.

## RRT-013 — NPC individuality remains active

Given:
- two NPCs share occupation/social context.

Expected:
- their personality, alignment/ethos, cognitive profile, motives, biases, knowledge, and speech may differ through context-first generation plus constrained genuine randomness;
- established differences inform later reliability/attitude behavior.

Failure if:
- profession becomes a complete personality template;
- the knowledge-reliability layer replaces individual NPC generation.

## RRT-014 — Supplement precedence

Given:
- an uploaded supplement contains alternate encounter/weather/travel rules;
- supplement is available but not explicitly active for the relevant scope.

Expected:
- core governing rule/projection remains active;
- supplement may be retrieved for reference but does not silently override.

Failure if:
- specificity or recent upload is treated as automatic activation.

## RRT-015 — Region activation horizon

Given:
- an off-screen actor outside Wren's immediate location becomes capable of materially affecting the known region within the active time horizon.

Expected:
- actor/region is promoted from latent to active as needed;
- explicit reevaluation trigger and dependencies are created;
- only necessary regional state is instantiated.

Failure if:
- nothing is created until Wren physically discovers the actor;
- the entire distant region is exhaustively simulated.

## RRT-016 — Map asset authority boundary

Given:
- the player-facing Home Coast map depicts a road, distance-like placement, settlement, or terrain feature not separately established in canonical state.

Expected:
- asset is used for player-facing orientation/identity only;
- exact geography/travel time/history/population remains unestablished until canonicalized.

Failure if:
- visual layout silently becomes exact campaign geography.

## Audit use

During maintenance or implementation testing:
1. select representative scenarios affected by changed runtime/context code or policy;
2. inspect canonical routes/projections/triggers that should fire;
3. verify expected behavior without modifying live campaign state;
4. record failures as engineering defects rather than altering campaign facts to make a test pass.
