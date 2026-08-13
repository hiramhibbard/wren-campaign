# DM Procedure Triggers

This file defines when the DM should recognize that an AD&D 2e procedure has become active. Exact mechanics, tables, modifiers, frequencies, costs, alignment restrictions, and thresholds remain governed by Hiram's uploaded source material and must be retrieved when consequential.

## Time advancement
- Track meaningful elapsed in-world time rather than treating scenes as timeless.
- When time advances enough to cross a scheduled NPC/faction/project/weather/adventure trigger, process the due hidden state before narrating dependent consequences.
- Use relative time until an exact campaign calendar is established; do not invent dates merely to fill the record.

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

## Checkpoint routing
Each real checkpoint should include dirty-domain hints from `STATE_TEMPLATES.md` whenever applicable. Routine maintenance should use them for incremental compaction rather than rereading/rebuilding every world shard.