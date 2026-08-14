# Core Gameplay Procedure Triggers

Purpose: explicit event-driven routing for the ordinary table-facing situations that recur across normal AD&D 2e play. Exact mechanics, tables, modifiers, optional-rule activation, and source-specific exceptions remain governed by verified compiled source objects or Hiram's uploaded source material.

This file complements `state/rulings/dm-procedure-triggers.md`. It exists to remove ambiguity about when the DM should call for checks, enter combat procedure, apply movement/light rules, resolve social uncertainty, or escalate to a source-specific subsystem.

## 1. General action adjudication / when to roll

Use this order whenever Wren attempts something whose outcome might matter:

1. **Established fact / impossible fact.** If canonical state and governing source make the result certain, resolve it without a roll.
2. **Routine competence.** If the task is simple, ordinary for a competent character, and no governing rule requires a check, resolve success without a roll. Do not roll merely to create suspense.
3. **Specific governing procedure.** If a class ability, nonweapon proficiency, thief skill, saving throw, attack roll, reaction roll, morale check, surprise roll, spell rule, movement rule, environmental rule, or other explicit AD&D/source procedure governs the uncertainty, use that procedure instead of inventing a generic check.
4. **Proficiency check.** When an applicable known proficiency says difficult/failure-prone use requires a check, call for the proficiency check and use its source-defined ability/modifier, timing, retry, and consequence rules.
5. **Ability check / DM-assigned chance.** If no more specific procedure governs but the outcome is genuinely uncertain and consequential, use an ability check, percentage chance, saving throw, or other DM-adjudicated method consistent with the PHB/DMG. Choose the method that best models the uncertainty; do not automatically default every uncertain action to a d20 ability check.
6. **No consequence, no meaningful check.** If failure cannot materially change information, time, position, resources, danger, relationships, or another consequential state, normally resolve without a roll.

Source basis: PHB Chapter 5 states that simple jobs may succeed automatically; complicated tasks may use a DM-assigned percentage, saving throw, or Ability check. Under nonweapon proficiencies, simple uses generally do not require a proficiency check, while difficult or failure-prone uses do, with individual proficiency descriptions controlling details.

### Roll ownership
- Player-facing Wren checks: Hiram rolls physical dice and reports the raw result.
- Hidden uncertainty whose failure/success should not be known: DM rolls secretly according to `state/rulings/dice-protocol.md`.
- Do not call for a visible roll when merely making the roll would reveal hidden information the governing procedure expects to remain uncertain.

### Retry / repeated-attempt gate
Do not assume unlimited retries. If the source defines retries, time cost, worsening odds, or a one-attempt limit, use it. If the source is silent and repeated attempts would trivially guarantee success, decide first whether anything materially changes between attempts (time, noise, tools, position, risk, evidence, resources). If nothing changes and the first attempt already represented the character's best reasonable effort, do not convert the task into repeated die-spam.

## 2. Combat trigger and sequence

Enter combat procedure when hostile action is initiated or imminent enough that action order, attacks, movement, spell timing, or interruption can materially differ by sequence.

Before initiative, when applicable:
- determine encounter distance and surprise if not already established;
- establish actor intent/disposition rather than assuming every encounter is combat;
- apply reaction only if disposition is genuinely uncertain;
- establish relevant visibility, cover, terrain, footing, elevation, readiness, and active effects.

During combat route only implicated mechanics:
- initiative procedure actually active in the campaign/case;
- movement/position;
- melee or missile attack procedure;
- weapon proficiency/nonproficiency;
- range/cover/concealment/firing-into-melee when relevant;
- spell casting time/components/interruption/effect lifecycle;
- multiple attacks and sequencing;
- saving throws/MR/special defenses when triggered;
- morale/withdrawal/pursuit when circumstances call for it;
- injury/death/healing consequences.

Do not roll initiative before there is a meaningful contested sequence. Conversation, observation, or a one-sided uncontested action does not become combat merely because danger exists nearby.

## 3. Tactical movement

Trigger tactical movement procedure when exact position, distance, rate, terrain, footing, obstacles, encumbrance, charging/running, climbing, swimming, mounted/vehicle movement, pursuit, or reach can change the outcome.

Fast path:
- use current verified movement rate if dependencies are unchanged;
- apply source-defined terrain/condition modifiers only when implicated;
- running/forced exertion uses its governing Strength/Constitution or proficiency checks rather than generic checks;
- exact unusual movement (swimming, jumping, mounted action, special terrain, vehicle maneuver) escalates to the governing source if not already compiled.

Do not measure incidental scene movement in combat-scale detail when position cannot matter.

## 4. Exploration / overland movement

Trigger travel/exploration procedure for meaningful overland, coastal, river, sea, dungeon, or wilderness movement where elapsed time, navigation, encounter timing, resources, weather, terrain, or getting lost may matter.

Use:
- base movement + encumbrance;
- terrain/weather modifiers;
- march/forced-march rules;
- navigation/getting-lost procedure when applicable;
- encounter-check schedule from active source/runtime;
- resource depletion and declared-action readiness;
- watches/rest and due-world events.

Do not compress travel past a consequential threshold without processing the relevant checks/events first.

## 5. Light, darkness, and visibility

Trigger light/visibility procedure whenever illumination or atmospheric conditions can affect what can be seen, identified, targeted, searched, navigated, or noticed.

Track as applicable:
- ambient condition (daylight/twilight/night/fog/rain/snow/etc.);
- active light sources, radius/cone, remaining fuel/duration;
- line of sight and physical obstruction;
- normal-vision limits;
- infravision or other special senses only under their governing source model;
- the tactical fact that a carried light may reveal the bearer to observers beyond the bearer's own illuminated radius.

Use verified Table 62/63 source objects for ordinary visibility and common light sources. Escalate to exact source for unusual planes, magical darkness/light, special senses, obstruction disputes, or source-specific exceptions.

## 6. Perception, listening, searching, and hidden information

Route through `state/rulings/perception-and-evidence.md` when Wren examines, searches, listens, scouts, tracks, studies, or otherwise investigates.

Mechanically:
- automatically provide plainly perceptible information;
- use source-specific detection/listening/search/secret-door/trap/thief/proficiency procedures when they govern;
- keep checks secret when the governing rule expects uncertainty about failure;
- ask for method/position/tool clarification only when it materially changes risk, time, noise, or what can be discovered;
- do not require pixel hunting for trivial competent substeps.

If exact listening/searching/door/trap mechanics are not compiled, retrieve the governing core/class/site source at the moment they become consequential.

## 7. Social interaction / persuasion / negotiation

There is no campaign-wide universal "Persuasion check" that overrides roleplay, established NPC motives, or reaction procedure.

Resolve social interaction in this order:
1. established relationship, motives, orders, alignment, knowledge, incentives, fears, obligations, and obvious situational constraints;
2. what Wren actually says/does and what the NPC can perceive or understand;
3. reaction roll when initial disposition is genuinely uncertain and the AD&D/source procedure makes it appropriate;
4. Charisma/reaction adjustments and applicable source-defined modifiers;
5. specific active proficiency/class/source procedure only when Wren actually has it and its scope applies;
6. DM-adjudicated ability/proficiency check only when no more specific rule governs and uncertainty remains genuinely consequential.

A successful social roll cannot force an NPC to do something contrary to established absolute constraints unless the governing source explicitly allows that effect. A failed roll does not erase established friendship, loyalty, or obvious mutual interest.

Optional supplement proficiencies such as Bargain, Persuasion, Acting, Debate, etc. remain inactive unless their source scope is explicitly active for the character/campaign. Their existence in the library is not permission to use them generically.

## 8. Doors, locks, barriers, and physical interaction

Trigger the appropriate procedure when opening, forcing, breaking, picking, lifting, bending, moving, or bypassing a barrier has meaningful uncertainty or cost.

Use specific source procedure where available (Open Doors/Bend Bars/Lift Gates, thief Open Locks, spell/item effect, siege/structural rules, etc.). Ordinary unlocked doors require no roll unless another condition makes them consequential.

For repeated force/search attempts, account for time/noise/alert consequences and source-defined retry behavior.

## 9. Traps and hazards

Trigger trap/hazard procedure when a source-keyed or established hazard can affect Wren, or when Wren deliberately searches, tests, disarms, avoids, or interacts with it.

Use in order:
- established/source-keyed trigger and physical state;
- applicable perception/search/thief/proficiency procedure;
- saving throw/attack/damage/special effect required by source;
- ongoing active-effect/resource/condition lifecycle;
- persistent site consequences.

Do not invent a generic "trap check" where the governing source/class procedure is more specific.

## 10. Environmental danger

Trigger the governing environmental procedure when falling, drowning/suffocation, fire/heat/cold, starvation/dehydration, poison, disease, exposure, weather, unstable terrain, or similar conditions can produce consequences.

If the exact mechanic is not already a verified compiled object, retrieve the relevant PHB/DMG/setting/source rule before consequential resolution. Track ongoing consequences through active-effect/resource procedures rather than resolving only the initial exposure.

## 11. Saving throws and resistance

Do not ask for a saving throw just because something is dangerous. Trigger the save when the attack/effect/hazard/source specifies a save or the DM is explicitly using a saving throw as the adjudication method for an otherwise unresolved situation.

Use the character's verified current save category/value and source-defined modifiers. Apply magic resistance or special defenses only when the governing creature/effect source calls for them.

## 12. Magic

Trigger magic procedure when casting, memorizing, learning, researching, identifying, dispelling, activating an item, consuming a charge/component, or resolving an ongoing magical effect.

Use exact source data for spell/item fields when consequential. Track:
- declared target/area and range;
- components and resource consumption;
- casting time/initiative interaction;
- save/MR;
- duration and non-time termination triggers;
- dispel/interaction exceptions;
- item charges/uses/attunement-like restrictions if any source defines them.

Compiled source objects accelerate lookup but do not activate optional magic systems.

## 13. Social/economic services, hiring, and bargaining

When hiring labor, henchmen, specialists, lodging, transport, spellcasting, or services:
- use established local availability and NPC motives first;
- retrieve relevant PHB/DMG/equipment/service costs when price or availability matters;
- use reaction/loyalty/henchman procedure where applicable;
- do not assume a listed service is automatically available in every settlement;
- optional Bargain/Persuasion-type proficiencies apply only if active and possessed.

## 14. Outcome persistence

Whenever an adjudication changes durable campaign truth—HP/resources, NPC attitude/obligation, discovered clue, site state, alarm, faction plan, ongoing effect, treasure ownership, chronology/location, or another persistent fact—place the semantic delta into the pending checkpoint state. Ordinary transient rolls need not be persisted unless their result establishes durable state.

## Performance invariant

This router should answer "what procedure is active?" without loading every source. Runtime order:

`declared event -> this trigger router / domain companion -> valid verified cache/compiled assertion -> exact governing source only if needed -> adjudicate -> persist durable consequence`

Do not perform a broad source scan when the governing subsystem/source is already identifiable.