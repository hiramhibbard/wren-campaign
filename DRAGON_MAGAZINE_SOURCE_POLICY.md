# Wren Dragon Magazine Source Policy — v1

This policy defines how *Dragon Magazine* is used as an article-level AD&D source family for Wren.

## Core principle

*Dragon* is a **secondary article reservoir**, not a globally active rulebook.

Use:

`current consequential domain -> active campaign/setting/adventure scope -> relevant Dragon article family -> article role classification -> compatibility/authority check -> use as governing scoped fact, compatible guidance, optional mechanic, or inspiration -> persist only consequential campaign results`

Do not preload or scan entire issues during ordinary play.

## Article roles

Classify a retrieved Dragon article by what it is actually doing, not merely by magazine issue:
- `dragon-setting-lore` — setting-specific people, places, factions, religions, history, cosmology, institutions, or regional detail;
- `dragon-monster-ecology` — ecology, habitat, society, behavior, lifecycle, lairs, signs, interactions, or extended monster treatment;
- `dragon-monster-mechanics` — new monsters, variants, abilities, statistics, or mechanical extensions;
- `dragon-race-culture` — race/species culture, society, traditions, settlements, beliefs, or options;
- `dragon-class-profession` — class institutions, professions, kits, specialists, orders, training, or character options;
- `dragon-religion-priesthood` — deities, churches, cults, specialty priests, rites, religious organizations, or divine magic support;
- `dragon-magic-spell` — spells, magical theory, schools, wizard/priest traditions, spell variants, or magical procedures;
- `dragon-magic-item-artifact` — magic items, artifacts, cursed items, item lore, or item procedures;
- `dragon-npc-organization` — NPCs, organizations, guilds, villains, allies, patrons, societies, or institutional templates;
- `dragon-equipment-craft` — weapons, armor, equipment, craft, trade, or material-culture detail;
- `dragon-dm-procedure` — encounter, campaign, wilderness, stronghold, economics, travel, adjudication, or other DM procedure guidance;
- `dragon-worldbuilding` — settlements, cultures, environments, history, politics, cosmology, campaign design, or world-generation material;
- `dragon-adventure-seed` — short situations, locations, hooks, encounter ideas, mini-scenarios, or scenario components;
- `dragon-optional-rule` — explicit optional/variant/replacement mechanics;
- `dragon-inspiration` — useful ideas that are not authoritative for the active scope.

A single article may occupy multiple roles by section.

## Authority and precedence

Dragon material does not receive one universal authority level.

Resolve each article by scope:
1. established Wren campaign facts remain authoritative;
2. active adventure-specific treatment governs its case;
3. active setting-specific source governs explicit setting canon;
4. governing PHB/DMG/monster/supplement rules remain mechanically authoritative unless a Dragon rule has been explicitly adopted for the relevant scope;
5. a Dragon article that is itself clearly an official expansion of the active setting may supply scoped setting detail where compatible and not superseded;
6. generic Dragon lore/guidance may fill unresolved gaps but may not flatten active setting/adventure treatment;
7. optional rules, kits, spells, items, proficiencies, variants, and replacement systems are not activated merely by retrieval.

When provenance or intended scope is unclear, classify conservatively and do not silently promote the article to governing canon.

## Automatic consultation triggers

Consult Dragon automatically when a consequential domain has an unresolved gap and Dragon is plausibly rich in that material, including:
- monster ecology/behavior beyond the governing 2e entry;
- setting lore not sufficiently covered by currently loaded source material;
- religions, cults, specialty priesthoods, or deity-specific institutions;
- NPC organizations, villains, guilds, societies, professions, or unusual character types;
- spells, magical traditions, magical phenomena, items, artifacts, or cursed objects;
- race/class cultural enrichment;
- specialized DM procedures, campaign systems, environments, or worldbuilding ideas;
- adventure seeds or compact scenario components when a full published adventure is unnecessary;
- support material for settings whose product lines were supplemented by magazine articles.

Do not consult Dragon merely because it exists. The trigger is an actual unresolved/reusable domain need.

## Mechanics activation rule

Consultation != activation.

A Dragon mechanical article may be:
- `available-for-consideration`;
- `case-relevant but inactive`;
- `explicitly adopted for one case/domain/character/setting`;
- `campaign-active` only after an explicit decision consistent with `RULES_PROJECTION_POLICY.md` and `SUPPLEMENT_SOURCE_RESOLUTION_POLICY.md`.

Player-facing options such as kits, class/race changes, specialty priest mechanics, proficiencies, spell access, new powers, or replacement subsystems may not be silently imposed.

DM-side procedural guidance may be used case-specifically when compatible with governing AD&D 2e rules and established campaign policy, but a material mechanical replacement must still have explicit scope.

## Setting-specific Dragon material

When a campaign setting becomes active, Dragon articles explicitly written for that setting become a targeted secondary setting family.

Use them to enrich unresolved setting-local detail only after checking:
- issue/article setting scope;
- edition/timeframe compatibility;
- whether later or more specific published setting material supersedes or contradicts it;
- whether the campaign has already diverged from publication baseline.

Do not leak Mystara, Greyhawk, Forgotten Realms, Ravenloft, Dark Sun, Al-Qadim, Spelljammer, or other setting-specific assumptions into unrelated generic scope.

## Monster ecology routing

For consequential monster ecology:

`scope-resolved governing AD&D 2e monster source -> applicable setting/adventure monster treatment -> relevant Dragon ecology article -> other compatible inspiration -> campaign-specific resolved ecology`

Dragon ecology is normally **stronger contextual inspiration than modern fan ecology material** because it belongs to the AD&D-era design tradition, but it still does not automatically override a governing monster entry or active setting/adventure fact.

Use Dragon ecology for candidate details such as behavior, lifecycle, social organization, lairs, feeding, signs, territoriality, relationships, and material traces. Do not import conflicting monster mechanics unless explicitly adopted.

## Magic, items, and spells

Dragon may be searched for candidate spells, magical practices, magic items, artifacts, curses, and magical phenomena when the campaign needs one.

Before use:
- check whether a more authoritative source already governs the named spell/item/artifact;
- classify whether the article supplies canon, optional mechanics, or inspiration;
- do not silently add player spell access or campaign-wide item rules;
- once an original/scoped Dragon-derived item or spell becomes established in play, preserve its exact adopted mechanics/provenance.

## NPCs, organizations, religions, and worldbuilding

Dragon may provide building blocks for original Wren material.

The DM may adopt, adapt, or combine compatible article ideas with `WORLD_BUILDER_RUNTIME_POLICY.md`, NPC-generation policy, supplement routing, and active setting constraints.

A retrieved guild, cult, villain, priesthood, profession, culture, or organization is not automatically campaign truth. It becomes truth only when deliberately resolved/seeded into Wren's world.

## Adventure relationship

Dragon is not treated as a substitute for *Dungeon Magazine*'s first-class adventure role.

However, Dragon adventure seeds, locations, villains, organizations, magic, monsters, and worldbuilding articles may supply components for:
- original adventures;
- published-adventure adaptation;
- regional/site generation;
- factions and recurring situations.

Route full scenario needs through `ADVENTURE_OPPORTUNITY_POLICY.md`; use Dragon article components when they improve the fit.

## Article-level indexing

Index lazily, not issue-completely.

When a useful article is discovered, preserve lightweight derived metadata as useful:
- issue number/date;
- article title;
- author if relevant;
- page/source locator;
- edition/system;
- setting scope;
- article roles;
- subject tags;
- activation/authority notes;
- known conflicts/supersession;
- reusable source locator.

The index is a retrieval accelerator only. Exact uploaded article text remains the source.

## Search and performance contract

Normal turn:
`cheap domain-gap check -> no Dragon trigger = no magazine search`

Triggered:
`domain + setting + subject -> targeted Dragon search -> inspect small candidate set -> classify role/authority -> use or reject -> cache locator if reuse is likely`

Do not scan every Dragon issue or load whole magazines into ordinary/Voice context.

## Voice

Preload only already-resolved Dragon-derived campaign facts or compact locators likely to matter immediately.

If exact Dragon mechanics/lore become consequential during Voice and the article is not loaded, defer the source lookup rather than inventing the magazine content from memory.

Original improvisation remains allowed where no exact Dragon/source fact is being claimed.

## Persistence

Finding an article or marking it as a candidate does not alter campaign state.

When Dragon-derived material becomes a consequential Wren fact, persist the adopted result and provenance through normal campaign state/checkpoint procedures.
