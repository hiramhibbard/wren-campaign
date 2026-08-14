# DM Procedure Triggers

This file defines when the DM should recognize that an AD&D 2e procedure has become active. Exact mechanics, tables, modifiers, frequencies, costs, alignment restrictions, and thresholds remain governed by Hiram's uploaded source material and must be retrieved when consequential.

## Time advancement
- Track meaningful elapsed in-world time rather than treating scenes as timeless.
- When time advances enough to cross a scheduled NPC/faction/project/weather/adventure trigger, process the due hidden state before narrating dependent consequences.
- Character/creature active effects and resource-consumption processes that have time-based triggers participate in the same due-event processing; do not limit scheduled triggers to world/NPC events.
- Use relative time until an exact campaign calendar is established; do not invent dates merely to fill the record.

## Derived-state invalidation procedure
When a canonical input changes, identify which cached/derived values depend on that input and invalidate or refresh only those values before they are next used consequentially.

Common dependencies include:
- level/class/advancement track -> THAC0/attack progression, saving throws, Hit Dice/HP progression, spell progression, proficiency-slot progression, next-level XP threshold, and class abilities as applicable;
- armor/shield/equipment -> AC, movement/encumbrance, weapon attack/damage properties, available actions, and other equipment-derived values as applicable;
- ability score -> all derived values that use that ability, including relevant reaction, carrying, combat, proficiency, spell, or system-shock/resurrection values;
- carried load -> encumbrance category and any movement/combat consequences;
- active effect/condition start or end -> only the stats and procedures modified by that effect/condition.

Do not reread unrelated rules merely because one derived value became invalid. If a cached value is still valid under unchanged dependencies, use it directly.

## Encumbrance procedure
Whenever carried inventory, worn equipment, filled-container contents, treasure load, Strength, or an encumbrance-modifying effect changes:

1. update the best-supported carried-weight total without inventing precision for unknown/variable contents;
2. compare the load against the character's current verified encumbrance breakpoint/category cache;
3. if the load remains within the cached category, no source lookup is required merely for this check;
4. if a breakpoint is crossed, or the cache is missing/stale/uncertain, retrieve the governing encumbrance source, establish the new encumbrance category and mechanical consequences, and cache the next relevant boundary/provenance;
5. refresh any dependent movement/combat values immediately enough that subsequent adjudication uses the correct state.

Crossing an encumbrance threshold is an automatic DM trigger. Hiram does not need to ask whether Wren has become encumbered.

## Resource / depletion procedure
For any resource whose remaining quantity matters mechanically or fictionally, preserve canonical quantity/state and register the relevant consumption/depletion behavior when it becomes active.

Examples include lamp fuel, torches, rations, water, ammunition, charges, quantified spell components, healing supplies, vehicle supplies, air, or other source-governed limited resources.

Whenever the resource is used or a consumption interval elapses:
1. decrement/update the canonical remaining quantity according to the governing rule or established usage;
2. evaluate any registered warning, exhaustion, empty, breakage, or other threshold that the change can reach;
3. automatically apply or trigger the source-supported consequence when a threshold is crossed;
4. do not reread the source after every decrement if the consumption rate and next relevant trigger are already verified and unchanged;
5. refresh/retrieve the governing rule when the resource behavior changes, the next trigger is unknown, or an integrity mismatch appears.

Do not create artificial warning thresholds unless the rules or campaign procedure actually need them. Zero/depletion and source-defined thresholds must not be missed merely because Hiram did not ask.

## Active-effect lifecycle procedure
When a spell, poison, disease, magical protection, environmental effect, temporary modifier, injury state, or other active effect begins and its lifecycle is consequential, record enough source-backed trigger information to know when it must be reevaluated or end.

Effect termination is not assumed to be time-based. Governing triggers may include any combination of:
- elapsed rounds/turns/hours/days or a fixed ending time;
- a particular event or action;
- damage taken, damage absorbed, charges expended, or another resource threshold;
- a condition becoming true or false;
- a successful save/check;
- dispelling, curing, resting, removal, death, leaving an area, or another explicit game procedure;
- source-specific termination language that does not fit the categories above.

When time or an event occurs, evaluate only active effects whose registered triggers could actually be affected by that change. Do not force event-, damage-, resource-, or condition-based effects into an `expires_at` timestamp.

When an effect ends or changes phase, automatically remove/refresh its dependent derived values and persist any durable resulting state. Hiram should not need to remind the DM that an active effect's termination condition occurred.

## Encounter procedure
Recognize encounter procedure when Wren enters a planned encounter, triggers a keyed encounter, or reaches a point where the governing travel/location rules call for a random encounter check.

As applicable, determine from the governing source and established world state:
- whether an encounter occurs;
- encounter size/composition;
- encounter distance;
- surprise;
- initial reaction if genuinely uncertain;
- morale when called for;
- local/environmental modifiers;
- whether a prepared/special encounter or faction activity overrides a generic table result.

Do not skip encounter checks simply because no combat is planned. Do not manufacture checks where the rules/world state do not call for them.

## Reaction procedure
Use an NPC/creature reaction roll when initial disposition is genuinely uncertain and the governing AD&D/source procedure makes it appropriate.

Do not use a reaction roll to erase established motives, alignment, loyalties, hatred, friendship, orders, published adventure state, or obvious situational constraints. Interpret the result through alignment, personality, culture, goals, Charisma/reaction modifiers, and current circumstances.

## Morale / loyalty procedure
Recognize morale/loyalty checks when combat losses, fear, hopeless odds, temptation, abusive treatment, unpaid obligations, betrayal pressure, or the governing henchman/hireling rules make them appropriate.

Secret morale/loyalty values, modifiers, and rolls remain DM-only. A failed check produces behavior consistent with the NPC's personality, alignment, motives, and circumstances rather than generic robotic flight/betrayal.

## NPC generation procedure
When a new NPC requires durable or mechanically relevant detail, use the context-first generation order in `STATE_TEMPLATES.md`:

1. published/source facts;
2. established world context;
3. role requirements;
4. class/race/alignment/source constraints;
5. constrained random variation or DM choice;
6. personality/history synthesis;
7. consistency pass;
8. canonicalize consequential details.

Do not roll a full character sheet for every walk-on. Do not use unconstrained randomness to produce implausible occupations, mentors, leaders, experts, or social roles. Unusual combinations are welcome when they have a coherent explanation and fit established world conditions.

Once a generated stat, alignment, personality trait, motive, skill, secret, or other consequential detail has affected play, preserve it rather than regenerating it later for convenience.

## NPC / henchman procedure
When an NPC becomes recurring, mechanically relevant, or relationship-significant, promote the NPC according to `STATE_TEMPLATES.md`.

When a relationship plausibly becomes a henchman relationship, retrieve the governing PHB/DMG rules for:
- Charisma limits;
- loyalty/morale;
- treasure shares/compensation;
- obligations;
- degree of player control;
- advancement/bookkeeping.

Henchmen remain independent NPCs with their own alignment, personality, goals, knowledge, limits, and risk tolerance.

## Alignment procedure
For recurring/significant NPCs, establish alignment when source material, class/religion constraints, mechanical interaction, relationship development, or consistent portrayal makes it useful.

- Published alignment wins for published NPCs/creatures unless canonical play legitimately changes it.
- For original NPCs, alignment is determined from established role, culture, religion, faction, history, motives, and source constraints, with constrained randomness permitted where several alignments remain equally plausible.
- Alignment informs likely actions, moral/social assumptions, relationships, loyalties, conflicts, and some mechanical effects.
- Alignment is not a substitute for personality. NPCs of the same alignment must still differ in temperament, goals, habits, fears, profession, intellect, judgment, and circumstances.
- Do not expose hidden NPC alignment merely because it is in DM state. Wren learns alignment only through observable behavior, legitimate inference, or applicable magic/rules.
- If sustained behavior would plausibly indicate alignment drift/change and the distinction matters, retrieve the governing alignment rules before changing canonical alignment.

## NPC portrayal procedure
Before portraying a significant recurring NPC, use the loaded NPC record to ground:
- alignment/worldview;
- personality and motives;
- Intelligence/Wisdom/Charisma or qualitative cognitive profile;
- education, culture, occupation, social rank, languages and literacy;
- professional skills/knowledge;
- speech profile;
- what the NPC actually knows, believes, suspects, or conceals.

Low Intelligence should affect complexity of reasoning, learning, abstraction, and sometimes speech, while Wisdom and experience may still produce good practical judgment. High Intelligence does not grant information the NPC never learned. Charisma affects presence/persuasion rather than knowledge or morality. Alignment guides tendencies and values without dictating a single canned response.

Do not give every NPC the same vocabulary, sentence rhythm, confidence, sophistication, worldview, morality, or degree of articulateness.

## Travel / exploration procedure
When Wren undertakes meaningful overland, coastal, river, sea, dungeon, or other exploration travel, activate a travel record when useful and retrieve the governing movement/navigation/encounter rules.

Track as relevant:
- route/course and estimated distance;
- movement rate and terrain/water conditions;
- weather/season;
- navigation/getting-lost checks;
- encounter-check timing;
- watches/camp/rest;
- rations, water, light, fuel and other depleting resources;
- vehicle/boat condition;
- elapsed time and scheduled world events crossed.

## Downtime / project procedure
For multi-hour/day/week tasks, create or update a durable project when completion cannot be resolved immediately.

Examples include spell learning/research, training, healing, paid work, investigation, crafting, construction, teaching, and long social/faction projects.

Retrieve the exact source procedure when duration, cost, prerequisites, checks, interruption effects, or completion consequences matter.

## Clue / rumor procedure
When Wren learns, infers, hears, contradicts, or resolves information that may matter later, preserve the information with its epistemic category.

Do not promote rumor, hearsay, suspicion, or Wren's inference into Established DM Truth during narration, checkpointing, or compaction.

## Faction / off-screen procedure
When a faction or significant NPC has an established plan, resources, or timeline, allow it to progress off-screen as time and events warrant.

Update clocks/plans when Wren interferes, assists, delays, reveals information, or advances time enough for the next action to occur.

## Significant item procedure
Promote an item from ordinary inventory into a significant-item record when provenance, hidden properties, charges, identification state, alignment restriction, curse/intelligence, ownership history, clue value, or repeated mechanical use matters.

## Published adventure/source procedure
When published material is inspected, seeded, activated, changed, completed, or bypassed, maintain a DM-only registry entry using `STATE_TEMPLATES.md` so the same material is not accidentally duplicated, reset, or stripped of continuity.

Retrieve original maps, handouts, keys, encounters, treasure, NPCs, and mechanical details from Hiram's uploaded source rather than reproducing them from memory.

## XP procedure
Follow the XP policy in `state/rulings/adnd2e-campaign-rulings.md`: evaluate automatically at meaningful encounter/objective resolution and session end, retrieve governing sources where necessary, and checkpoint the award/basis/result.

After every XP change for an advancing character:
1. compare the resulting cumulative XP against that character's verified cached `next-level XP threshold`;
2. if current XP is below the threshold, no advancement-source lookup is required merely for this check;
3. if current XP meets or exceeds the threshold, automatically trigger the Level Advancement procedure below without waiting for Hiram to notice or ask;
4. if the threshold cache is missing, stale, invalidated, or uncertain, retrieve the governing advancement source and repair/verify the cache before deciding whether advancement triggers.

## Level Advancement procedure
When cumulative XP meets or exceeds the verified next-level threshold:

1. **Trigger automatically.** Do not require Hiram to ask whether the character gained a level.
2. **Retrieve governing sources.** Consult the exact uploaded class/setting/rules material required to determine the attained level and every advancement consequence. The cached threshold is a trigger accelerator, not sufficient authority for applying the level-up itself.
3. **Resolve advancement prerequisites/options.** Apply any established training rule, class restriction, setting modifier, alignment/dual-class/multi-class interaction, or other governing requirement. If an optional rule that materially affects advancement is genuinely unresolved, surface the decision rather than silently choosing it.
4. **Request only player-facing input.** Ask Hiram for physical dice rolls and genuine player choices required by the rules; resolve DM-only or deterministic consequences without making him prompt for each one.
5. **Apply the full mechanical delta.** Update level, hit points/Hit Dice, spell progression, attack values, saving throws, proficiency slots, class abilities, and any other values that actually change at the new level. Do not assume every category changes at every level; verify against sources.
6. **Refresh the cache.** Derive the next `next-level XP threshold` from the authoritative advancement source and persist its provenance/status.
7. **Loop for multi-level jumps.** Compare cumulative XP against the newly refreshed threshold and repeat the procedure if the same XP total legitimately qualifies for another level. Stop when XP is below the next threshold or a governing rule blocks further advancement.
8. **Persist advancement.** Treat the resulting character-mechanical changes and refreshed threshold as durable state for the next canonical checkpoint/readback cycle.

## Checkpoint routing
Each real checkpoint should include dirty-domain hints from `STATE_TEMPLATES.md` whenever applicable. Routine maintenance should use them for incremental compaction rather than rereading/rebuilding every world shard.