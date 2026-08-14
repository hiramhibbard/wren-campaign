# DM Procedure Triggers

This file defines **campaign-state and lifecycle triggers** that the DM should recognize automatically. Exact mechanics, tables, modifiers, frequencies, costs, alignment restrictions, and thresholds remain governed by verified compiled source objects or Hiram's uploaded source material.

Ordinary table-facing adjudication—**when to roll, combat entry, tactical movement, light/visibility, perception/searching, social resolution, doors/barriers, traps/hazards, environmental danger, saving-throw trigger discipline, and ordinary magic interaction**—is routed through:

- `state/rulings/core-gameplay-procedure-triggers.md`

Do not duplicate those procedures here. This file owns the cross-cutting campaign/runtime responsibilities below.

## Time advancement
- Track meaningful elapsed in-world time rather than treating scenes as timeless.
- When time advances enough to cross a scheduled NPC/faction/project/weather/adventure trigger, process the due hidden state before narrating dependent consequences.
- Character/creature active effects and resource-consumption processes with time-based triggers participate in the same due-event processing.
- Use relative time until an exact campaign calendar is established; do not invent dates merely to fill the record.

## Derived-state invalidation
When a canonical input changes, identify which cached/derived values depend on it and invalidate or refresh only those values before consequential reuse.

Common dependencies include:
- level/class/advancement track -> THAC0/attack progression, saving throws, Hit Dice/HP progression, spell progression, proficiency slots, next-level XP threshold, class abilities;
- armor/shield/equipment -> AC, movement/encumbrance, weapon properties, available actions;
- ability score -> reaction, carrying, combat, proficiency, spell, system-shock/resurrection, and other dependent values;
- carried load -> encumbrance category and movement/combat consequences;
- active effect/condition start/end -> only stats/procedures modified by that effect.

Do not reread unrelated rules because one derived value became invalid.

## Encumbrance
Whenever carried inventory, worn equipment, filled-container contents, treasure load, Strength, or an encumbrance-modifying effect changes:
1. update the best-supported carried-weight total without inventing precision for unknown/variable contents;
2. compare against the current verified encumbrance breakpoint/category cache;
3. if still within the cached category, no source lookup is required merely for the check;
4. if a breakpoint is crossed, or cache is missing/stale/uncertain, retrieve the governing source, establish the new category/consequences, and cache the next relevant boundary/provenance;
5. refresh dependent movement/combat values before subsequent adjudication.

Crossing an encumbrance threshold is an automatic DM trigger.

## Resource / depletion
For any resource whose remaining quantity matters mechanically or fictionally, preserve canonical quantity/state and register relevant consumption/depletion behavior when active.

Examples: lamp fuel, torches, rations, water, ammunition, charges, quantified spell components, healing supplies, vehicle supplies, air, or other source-governed limited resources.

Whenever the resource is used or a consumption interval elapses:
1. decrement/update canonical quantity according to the governing rule or established usage;
2. evaluate source-defined warning, exhaustion, empty, breakage, or other thresholds;
3. automatically apply/trigger the consequence when crossed;
4. do not reread the source after every decrement if rate and next trigger remain verified;
5. refresh/retrieve the rule when behavior changes, next trigger is unknown, or integrity mismatch appears.

## Declared-action readiness
Before committing Wren to a declared action whose foreseeable duration, distance, environment, or method materially depends on supplies, equipment, money, spell resources, tools, transport, or another player-known prerequisite, perform a compact readiness check before advancing time or irreversibly starting the action.

Examples include multi-day travel, sea travel, prolonged darkness, sustained light/fuel use, planned ammunition use, costly/component-dependent magic, and long projects.

1. infer only requirements Wren could reasonably know or estimate;
2. compare known requirements against current canonical carried/accessible resources and cached state;
3. if there is a material shortfall, likely depletion, missing prerequisite, or obvious logistical risk a competent character would notice, tell Hiram before commitment;
4. where useful, state the scale of mismatch without exposing hidden dangers or DM-only information;
5. offer obvious player-known alternatives;
6. advisory only—Hiram may proceed and accept normal consequences;
7. do not interrupt routine actions with trivial warnings;
8. do not repeat an unchanged warning unless circumstances materially change.

## Active-effect lifecycle
When a consequential active effect begins, record enough source-backed trigger information to know when it must be reevaluated, change phase, or end.

The lifecycle is origin-agnostic: spells, potions, scrolls, charged or worn items, curses, artifacts, monster/class abilities, poisons, diseases, environmental magic, injuries, and temporary modifiers all use the same lifecycle model.

Preserve as applicable:
- effect/source identity and target;
- mechanical/fictional state modified;
- remaining duration, charges, absorption, uses, or other lifecycle resource;
- every source-defined trigger that can alter/suspend/terminate it;
- dependent cached/derived values.

Termination may depend on elapsed time, an event/action, damage/resource threshold, equipment state, a save/check, dispelling/curing/rest/removal/death/leaving an area, or other source-specific language. Evaluate only effects whose registered triggers are implicated by the current event. Do not force non-time effects into an `expires_at` timestamp.

When an effect ends or changes phase, automatically refresh dependent state and persist durable consequences.

## NPC generation
When a new NPC requires durable or mechanically relevant detail, use the context-first order in `STATE_TEMPLATES.md`:
1. published/source facts;
2. established world context;
3. role requirements;
4. class/race/alignment/source constraints;
5. constrained random variation or DM choice;
6. personality/history synthesis;
7. consistency pass;
8. canonicalize consequential details.

Do not roll a full sheet for every walk-on. Once a generated consequential detail affects play, preserve it rather than regenerating it later.

## NPC / henchman promotion
When an NPC becomes recurring, mechanically relevant, or relationship-significant, promote the NPC according to `STATE_TEMPLATES.md`.

When a relationship plausibly becomes a henchman relationship, retrieve governing rules for Charisma limits, loyalty/morale, treasure shares/compensation, obligations, degree of player control, and advancement/bookkeeping. Henchmen remain independent NPCs.

## Alignment
For recurring/significant NPCs, establish alignment when source material, class/religion constraints, mechanical interaction, relationship development, or consistent portrayal makes it useful.

- Published alignment governs published NPCs/creatures unless play legitimately changes it.
- Original NPC alignment derives from established role, culture, religion, faction, history, motives, and source constraints; constrained randomness is allowed where several results remain plausible.
- Alignment informs tendencies and mechanical interactions but does not replace personality.
- Hidden NPC alignment is not exposed merely because it exists in DM state.
- If sustained behavior may indicate alignment drift/change and the distinction matters, retrieve governing rules before changing canonical alignment.

## NPC portrayal
Before portraying a significant recurring NPC, use the loaded NPC record to ground alignment/worldview, personality/motives, cognitive profile, education/culture/occupation/rank, languages/literacy, professional knowledge, speech profile, and what the NPC actually knows/believes/suspects/conceals.

Intelligence affects reasoning complexity but does not grant unlearned information; Wisdom/experience may still produce practical judgment; Charisma affects presence/persuasion rather than knowledge or morality.

## Downtime / projects
For multi-hour/day/week tasks, create or update a durable project when completion cannot be resolved immediately.

Examples: spell learning/research, training, healing, paid work, investigation, crafting, construction, teaching, long social/faction projects.

Run declared-action readiness when known costs, materials, tools, spell resources, access, or time requirements could prevent or complicate completion. Retrieve exact source procedure when duration, cost, prerequisites, checks, interruption effects, or completion consequences matter.

## Clue / rumor
When Wren learns, infers, hears, contradicts, or resolves information that may matter later, preserve it with its epistemic category. Do not promote rumor, hearsay, suspicion, or Wren's inference into Established DM Truth during narration, checkpointing, or compaction.

## Faction / off-screen action
When a faction or significant NPC has an established plan, resources, or timeline, allow it to progress off-screen as time/events warrant. Update clocks/plans when Wren interferes, assists, delays, reveals information, or advances enough time for the next action.

## Significant items
Promote an item from ordinary inventory into a significant-item record when provenance, hidden properties, charges, identification state, alignment restriction, curse/intelligence, ownership history, clue value, or repeated mechanical use matters.

## Published adventure/source continuity
When published material is inspected, seeded, activated, changed, completed, or bypassed, maintain a DM-only registry entry using `STATE_TEMPLATES.md` so the same material is not duplicated, reset, or stripped of continuity. Retrieve maps, handouts, keys, encounters, treasure, NPCs, and mechanical details from Hiram's uploaded source rather than memory.

## XP
Follow `state/rulings/adnd2e-campaign-rulings.md`: evaluate automatically at meaningful encounter/objective resolution and session end, retrieve governing sources where necessary, and checkpoint the award/basis/result.

After every XP change:
1. compare cumulative XP against the verified cached next-level threshold;
2. if below threshold, no advancement lookup is required merely for this check;
3. if threshold is met/exceeded, automatically trigger Level Advancement;
4. if threshold cache is missing/stale/uncertain, retrieve source and repair it first.

## Level advancement
When cumulative XP meets/exceeds the verified next-level threshold:
1. trigger automatically;
2. retrieve governing sources for attained level and all consequences;
3. resolve training/rule/setting prerequisites and any genuinely unresolved optional decisions;
4. request only player-facing dice rolls and genuine player choices;
5. apply the full verified mechanical delta—level, HP/HD, spells, attacks, saves, proficiency slots, class abilities, and other actual changes;
6. refresh next-level threshold and provenance;
7. loop if the same XP total legitimately qualifies for another level;
8. persist the resulting durable state.

## Checkpoint routing
Each real checkpoint should include dirty-domain hints from `STATE_TEMPLATES.md` whenever applicable. Routine maintenance should use them for incremental compaction rather than rebuilding every shard.

## Routing boundary
For ordinary table play, route first through `state/rulings/core-gameplay-procedure-triggers.md`. Use this file only when the event implicates one of the cross-cutting state/lifecycle responsibilities above.