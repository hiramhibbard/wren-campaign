# Wren Campaign State Templates and Long-Term Scaffolds

This file is a normative companion to `STATE_SCHEMA.md`. It defines reusable structures for campaign growth without requiring empty live-state files. Instantiate only the fields and entity files that play actually needs.

Exact AD&D 2e mechanics, modifiers, tables, class rules, alignment restrictions, morale values, henchman limits, encounter frequencies, travel rates, training costs, spell research rules, and similar sourced details remain governed by Hiram's uploaded source material. These templates define what campaign state to preserve and when to retrieve the governing source.

## General entity rules

- Store current durable truth, not transcript prose.
- Preserve player-known fact, rumor, inference, unresolved question, Prepared Possibility, Established DM Truth, and source canon as distinct categories.
- Do not invent exact statistics or history merely to fill a template.
- Published NPCs, monsters, adventures, locations, and rules must be sourced from the uploaded material when exact details matter.
- Create only as much detail as play requires. Promote entities to richer records when their importance grows.
- A field may be `unestablished`, `unknown to Wren`, or omitted. Missing optional detail is preferable to invented precision.

## NPC generation and adjudication protocol

NPCs should be generated context-first rather than by unconstrained random rolls. Randomness is useful for variation, but the resulting person must fit the established world and the role they plausibly occupy.

Use this order when a new NPC requires more than walk-on detail:

1. **Published/source facts first.** If the NPC comes from published material, preserve published identity, alignment, class, level, abilities, personality, motives, relationships, equipment, and other established details. Fill only genuinely unspecified gaps.
2. **Established world context.** Determine what is already constrained by location, culture, race/species, age, social class, religion, faction, occupation, education/access to training, local institutions, economic conditions, and why this NPC is present.
3. **Role requirements.** Determine the capabilities the role plausibly requires. A skilled mapmaker should possess relevant knowledge; an experienced ship captain should be competent at seamanship; a scholarly magical mentor must satisfy the mental, magical, educational, and source-rule requirements of that role. Do not give an NPC a job or status that their established capabilities cannot plausibly support unless there is an intentional explanation.
4. **Class/race/alignment constraints.** When class, kit, race/species, religion, spell access, magical item use, or published setting rules impose restrictions or strong tendencies, retrieve and honor them before finalizing the NPC.
5. **Constrained variation.** Use randomness or DM choice to determine remaining uncertain details inside the plausible space: exact ability values, age, temperament, appearance, secondary skills, background events, resources, quirks, and similar variation. Avoid repeatedly producing the same convenient archetype.
6. **Personality/history synthesis.** Reconcile ability profile, alignment, occupation, culture, education, social position, relationships, life history, and current pressures into a coherent individual. Personality is not mechanically dictated by one score or by alignment.
7. **Consistency pass.** Before the NPC becomes consequential, ask whether the person could plausibly have reached the established position with these abilities, skills, resources, history, alignment, and relationships. If an unusual combination appears, either establish a plausible hidden explanation or revise it before the NPC affects play.
8. **Canonicalize when consequential.** Once a generated ability, alignment, personality trait, motive, professional skill, relationship, secret, or other detail has informed meaningful play, treat it as fixed hidden/player-facing state as appropriate. Do not regenerate it later for convenience.

Unusual people should exist. A brilliant laborer, illiterate genius, charismatic criminal, foolish noble, highly wise but poorly educated fisher, or unexpectedly compassionate evil-aligned NPC can all be coherent when their circumstances support them. Social position and opportunity influence education, vocabulary, profession, resources, and exposure; they do not rigidly determine innate ability scores.

## NPC significance tiers

### Tier 0 — walk-on
Use for one-scene or incidental NPCs. Keep inline in a location, encounter, or checkpoint unless they become durable.

Minimum useful state:
- name or descriptive handle if known;
- role/job;
- physical impression if relevant;
- one or two personality/behavior cues;
- immediate attitude/motive;
- location/affiliation;
- alignment only if already sourced, mechanically relevant, or needed as a quick behind-the-screen guide.

Do not generate a full character sheet for an innkeeper, groom, dock worker, shopkeeper, or similar walk-on unless mechanics become relevant.

### Tier 1 — recurring NPC
Promote when the NPC recurs, carries a clue, has an ongoing relationship, makes a promise/debt, develops a motive, or may affect future play independently.

Add as relevant:
- canonical name and aliases;
- race/species, culture/origin, age, sex/gender when established/relevant;
- occupation, profession, social role, rank/title;
- alignment/worldview when established or useful, with player-knowledge status kept separate;
- relationship to Wren and relationship trajectory;
- what the NPC knows about Wren;
- what Wren knows/believes about the NPC;
- motives, priorities, loyalties, fears, dislikes, ambitions;
- current location/status;
- promises, debts, favors, obligations;
- important possessions/resources;
- last significant interaction;
- cross-links to factions, locations, clues, projects, adventures;
- player-facing and DM-only knowledge boundaries.

### Tier 2 — significant/mechanically relevant NPC
Use when the NPC may adventure, fight, cast spells, perform difficult tasks, train Wren, travel with Wren, lead a faction, or otherwise require repeatable adjudication.

Add only what is relevant and established/prepared:
- class/kit and level, or monster/NPC type;
- alignment and any class/religion/item restrictions it affects;
- ability scores or qualitative ability profile;
- AC, HP, THAC0/attack routine, saves, movement, morale when needed;
- proficiencies, languages, literacy, professional skills, spell access, special abilities;
- weapons, armor, equipment, spellbook/memorized spells, consumables, notable magic;
- wages, treasure share, expenses, or service terms if applicable;
- tactics, risk tolerance, combat priorities, surrender/retreat behavior;
- secret mechanical information kept DM-only when appropriate.

### Tier 3 — henchman / long-term companion / major recurring NPC
Use Tier 2 plus a persistent relationship and independence model:
- relationship status: acquaintance / ally / potential henchman / henchman / estranged / former henchman / other;
- loyalty/morale basis and current modifiers when the governing rules make them relevant;
- treatment history that could affect loyalty;
- agreed compensation, treasure share, room/board, equipment, training, healing, or other obligations;
- degree of player control currently appropriate;
- personal goals and lines the NPC will not cross;
- alignment/worldview tensions or affinities that can affect the relationship;
- secrets kept from Wren;
- advancement/XP if the rules require it;
- independent off-screen actions and scheduled obligations;
- consequences if neglected, exploited, humiliated, betrayed, or endangered.

Henchmen remain NPCs with their own personalities and interests. Increased player control never erases the DM's responsibility to overrule behavior that would be out of character or inconsistent with established loyalty/motives/alignment.

## NPC personality and portrayal schema

Significant NPCs should carry enough portrayal state that their voice remains distinct across months or years.

Use as relevant:

### Core personality
- dominant traits;
- values/ethics;
- ambitions/goals;
- fears/anxieties;
- likes/dislikes;
- habits/quirks;
- emotional baseline;
- patience/temper;
- confidence/insecurity;
- humor style if any;
- trust style;
- attitude toward authority, wealth, danger, magic, religion, foreigners, social class, etc. when relevant.

### Alignment and worldview
Alignment is a durable AD&D game trait when established. It should inform tendencies in moral judgment, social assumptions, loyalties, methods, conflicts, reactions, and relationship compatibility, and it may have direct mechanical consequences under class, spell, religion, monster, or magical-item rules.

Use alignment as a guide to likely choices rather than a complete personality script. NPCs should generally act consistently with alignment, while still possessing individual motives, contradictions, habits, affections, prejudices, fears, professional duties, and situational pressures. Two NPCs of the same alignment should not therefore sound or behave identically.

Track as relevant:
- exact alignment, if established;
- whether that alignment is source-canonical, generated/prepared, or later changed through play;
- class/religion/faction implications;
- strong alignment convictions versus loose practical adherence;
- recurring ethical principles or methods that express the alignment;
- known tensions between alignment and personal goals/relationships;
- alignment change/drift only when supported by sustained actions or governing rules;
- whether Wren knows, suspects, misreads, or has no knowledge of the NPC's alignment.

Do not narrate hidden alignment directly unless Wren has a legitimate source of that knowledge. Alignment detection and related magic use the exact governing source rules.

### Cognitive profile
Ability scores are mechanical facts when established, but they also inform portrayal.

- **Intelligence:** memory, reasoning, learning, ability to grasp abstraction/novel ideas, vocabulary breadth, and complexity of explanation. Low Intelligence may produce slower comprehension, simpler reasoning, difficulty with complex abstractions, impulsive conclusions, or limited vocabulary. High Intelligence may produce rapid pattern recognition, precise distinctions, sophisticated explanations, or strategic reasoning.
- **Wisdom:** judgment, common sense, intuition, perceptiveness, self-control, practical understanding, and awareness of consequences. A clever NPC can still have poor judgment; a less scholarly NPC can be very wise.
- **Charisma:** social presence, force of personality, persuasiveness, leadership, magnetism, or intimidation. High Charisma does not imply kindness, education, or eloquence; low Charisma does not imply low Intelligence.

Do not reduce portrayal to one ability score. Alignment, education, culture, occupation, age, language fluency, personality, emotional state, social rank, and lived experience should also shape how the NPC thinks and speaks.

Avoid caricature. A low-Intelligence NPC should sound and reason consistently with limited mental acuity without becoming a comic stereotype unless that personality is separately established. A brilliant NPC should not automatically know facts they have had no opportunity to learn.

### Speech/voice profile
Record for recurring NPCs when useful:
- vocabulary: plain / technical / educated / archaic / regional / trade-specific / other;
- sentence complexity and pace;
- verbosity/terse tendencies;
- formality;
- favorite idioms or metaphors;
- hesitations, bluntness, indirectness, sarcasm, humor, evasiveness;
- accent/dialect only when it can be represented respectfully and consistently;
- subjects on which the NPC becomes more or less articulate;
- language fluency and literacy.

The DM should use these fields to generate dialogue rather than giving every NPC the same modern, articulate conversational voice.

### Knowledge model
For significant NPCs distinguish:
- established facts known;
- false beliefs;
- rumors heard;
- suspicions/inferences;
- secrets they know;
- information they would refuse to share;
- information they might share only under specific conditions;
- professional expertise and blind spots.

NPC dialogue must be constrained by this knowledge model. Intelligence does not grant omniscience.

## Relationship / henchman progression

Relationships evolve from events rather than from arbitrary status changes. Track durable causes such as:
- repeated fair treatment;
- trust and confidences;
- rescue or protection;
- shared danger;
- generosity or exploitation;
- fulfilled or broken promises;
- payment and treasure shares;
- ideological/alignment affinity or conflict;
- humiliation, betrayal, neglect, or abuse.

When a relationship plausibly crosses into henchman status, retrieve the governing AD&D 2e henchman/Charisma/loyalty rules before finalizing mechanical consequences.

## World clock and event queue

Use the chronology domain for player-facing time and a DM-only event queue for hidden developments.

Track as established:
- calendar/date system once established;
- current date and approximate/exact time when consequential;
- elapsed days/turns/hours;
- current season and weather context if relevant;
- scheduled event id;
- trigger time/date or trigger condition;
- affected entities/locations/factions;
- hidden/player-known status;
- action to resolve when trigger is crossed;
- whether the event repeats;
- source/adventure reference when applicable.

Whenever in-world time advances across a scheduled trigger, resolve or update due events before narrating consequences that depend on them. NPCs, factions, weather, journeys, research, healing, wages, rumors, and adventures should not remain frozen while Wren acts elsewhere.

If the campaign's exact calendar is still unestablished, maintain relative elapsed time until a calendar becomes canonical rather than inventing dates.

## Encounter-region scaffold

Regional encounter state may include:
- region/location and terrain type;
- source table/reference;
- encounter-check frequency/chance source requirement;
- time-of-day/weather/season modifiers;
- planned encounters and triggers;
- random encounter table reference or locally prepared table;
- special encounters already prepared;
- exhausted/one-use results;
- local faction/patrol activity;
- current alarms/noise/pursuit modifiers;
- recent encounter consequences that change the table;
- encounter distance/surprise/reaction/morale procedures to retrieve when needed.

Random encounters supplement prepared world state. They do not replace prepared locations, motives, faction activity, or adventure content.

## Reaction and morale scaffold

Use reaction procedures when an NPC/creature's initial response is genuinely uncertain and not already fixed by established motive, circumstance, or published adventure state. Interpret the result through the NPC's alignment, personality, goals, knowledge, culture, and current situation.

Use morale when the governing combat/NPC rules or circumstances call for it, including fear, losses, hopeless danger, temptation, betrayal pressure, or continued service where applicable. Preserve secret morale/loyalty values and rolls as DM-only information.

A reaction or morale roll must not erase established identity or force an impossible action merely because a table result was rolled.

## Faction scaffold

For a durable faction track as relevant:
- name/aliases;
- type and identity;
- leadership/key members;
- territory/reach;
- public purpose;
- Established DM Truth about purpose;
- dominant ethos/alignment tendencies where meaningful without assuming every member shares one alignment;
- resources and capabilities;
- current goals;
- current plan/next actions;
- clocks/progress;
- allies/rivals/enemies;
- relationship to Wren;
- what Wren knows/believes;
- clues/rumors tied to faction;
- source/adventure provenance;
- scheduled off-screen events.

Faction clocks advance from time and events even when Wren is absent.

## Clue / rumor / knowledge scaffold

For durable investigative information track:
- id/short label;
- statement/content;
- category: established player-known fact / rumor / hearsay / Wren inference / unresolved question / false belief / DM clue / Established DM Truth;
- source NPC/location/item/event;
- learned/created when;
- who knows it;
- related entities/threads;
- reliability if known to the DM;
- contradiction/retraction/superseding information;
- resolved status.

Never silently promote a rumor or Wren inference into objective truth during compaction.

## Travel / exploration scaffold

Instantiate for meaningful journeys:
- origin/destination/route or intended course;
- travel mode and party composition;
- movement rate/source;
- terrain/roads/water conditions;
- navigation method and navigator;
- watches/camp plan;
- provisions/water/light/fuel and other depleting resources;
- current weather/season;
- encounter-check schedule/source;
- getting-lost/navigation procedure/source;
- elapsed time and distance estimate;
- planned route encounters/landmarks;
- boat/vehicle condition when relevant;
- temporary modifiers such as pursuit, stealth, haste, injury, overload.

The DM automatically recognizes when travel procedures become active and retrieves exact AD&D/source rules when consequential.

## Downtime / project scaffold

Use for multi-hour/day/week tasks such as:
- spell research or learning;
- copying spells;
- training/advancement;
- healing/recovery;
- paid work;
- research/investigation;
- crafting/item research;
- construction;
- teaching/training others;
- long social or faction projects.

Track:
- project name/type;
- responsible characters/NPCs;
- start time;
- required duration/source;
- elapsed/progress;
- costs/resources/components;
- prerequisites/facilities/teachers;
- interruptions and consequences;
- rolls/checks still due;
- expected completion trigger;
- resulting durable state when complete.

## Significant item / treasure provenance scaffold

Use when an item has durable mechanical, narrative, financial, or investigative importance:
- canonical id/name and aliases;
- physical description;
- current owner/location/container;
- where/how acquired;
- apparent properties;
- identified properties;
- hidden/unknown properties kept DM-only;
- charges/uses/durability/condition;
- curse/intelligence/ego or other special state when applicable;
- alignment restrictions/affinities when applicable;
- known/estimated value;
- source reference;
- linked clues/history/owners;
- whether player-facing identification is complete.

Routine commodities remain in inventory rather than becoming individual entity records.

## Adventure / source registry scaffold

Use DM-only registry entries when published material is inspected, seeded, or instantiated:
- source file/title and page/section references;
- adventure/module/article identifier;
- status: uninspected / inspected / candidate / seeded / active / completed / bypassed / altered;
- canonical campaign location/setting adaptation;
- entry hooks/rumors already seeded;
- NPC/location/faction cross-links;
- player-facing handouts/maps available;
- DM-only maps/keys/spoiler references;
- continuity adaptations already made;
- clocks/off-screen developments;
- material already consumed/changed by play.

Do not duplicate copyrighted source text into campaign state. Store references, campaign adaptations, and state deltas.

## Entity promotion and demotion rules

Promote a walk-on into an individual shard when one or more become true:
- recurring interaction is likely;
- the entity has an independent motive or timeline;
- it carries a durable clue, secret, debt, promise, relationship, resource, or mechanical state;
- it joins/travels with Wren;
- it becomes a faction leader/member of consequence;
- exact retrieval by name/reference is likely to matter later.

Compact or demote resolved entities into indexes/history when their detailed state no longer affects future adjudication. Never delete unique historical facts needed to understand current relationships, consequences, ownership, or knowledge.

## Checkpoint dirty-domain hints

Every real checkpoint should include compact routing metadata when applicable:
- `affected_entities`;
- `affected_npcs`;
- `affected_locations`;
- `affected_factions`;
- `affected_items`;
- `affected_clues`;
- `affected_projects`;
- `affected_adventures`;
- `world_time_advanced`;
- `scheduled_events_changed`;
- `mechanics_changed`;
- `inventory_changed`;
- `magic_changed`;
- `knowledge_boundaries_changed`;
- `resume_changed`.

Maintenance should use these hints to update only dirty shards whenever safe, then validate cross-links and indexes. This reduces compaction cost as the world grows.

## Maintenance behavior

Normal maintenance should be incremental:
1. reconstruct snapshot + post-baseline checkpoints;
2. collect dirty-domain hints;
3. update only affected shards plus necessary indexes/cross-links;
4. promote/split entities only when thresholds justify it;
5. update root manifest last;
6. verify all writes before advancing baseline.

A major integrity audit may intentionally perform a broader scan, but routine compaction should not repeatedly rewrite the entire campaign world.