# Wren Supplement Source Resolution Policy — v1

This policy defines when and how AD&D 2e specialist supplements and periodical secondary sources are consulted without turning mere availability into automatic rules activation.

## Core principle

Use supplements by **domain and active scope**, not by global preload.

`current situation -> implicated domain -> active setting/adventure/campaign scope -> relevant specialist source family -> guidance/rules distinction -> governing source decision -> cached projection or exact source lookup`

Ordinary play should not scan or preload every supplement.

## Source roles

Classify useful sources by role when needed:
- `core-rule-source` — PHB/DMG/MM and other currently governing core sources;
- `race-specialist-source` — PHBR/race books such as elves, dwarves, gnomes/halflings, humanoids, etc.;
- `class-specialist-source` — PHBR/class books for fighters, thieves, wizards, priests, bards, rangers, paladins, druids, psionics, and similar specialties;
- `dm-domain-guide` — DMGR/blue-book and equivalent DM references for castles/strongholds, catacombs/dungeons, arms/equipment, villains, seafaring, and other situation domains;
- `periodical-secondary-source` — Dragon Magazine and comparable article-based AD&D material whose authority is classified article-by-article;
- `setting-specific-source` — an active campaign-setting treatment;
- `adventure-specific-source` — module/site/scenario material governing a particular case;
- `optional-rules-source` — material that introduces an optional or replacement subsystem;
- `inspiration-reference-source` — useful non-governing material.

A single book/article may occupy more than one role by section.

## Automatic consultation is not automatic activation

The DM may automatically **consult** a relevant specialist source when its subject becomes materially relevant.

Examples:
- fleshing out elf culture, society, NPCs, settlements, customs, race-specific outlook, or likely race-specific details -> consult the relevant elf specialist source;
- dwarf analog -> dwarf specialist source;
- a class-specific NPC, institution, training tradition, kit, class culture, or class-specific issue -> consult the relevant class specialist source;
- castle construction, siege, fortification, governance, or stronghold procedures -> consult the relevant DM-domain guide;
- catacombs/tombs/subterranean-site concerns -> consult the relevant DM-domain guide;
- detailed arms/equipment availability, use, provenance, or specialist equipment questions -> consult the relevant equipment guide;
- major villain design/motivation/organization -> consult the relevant villain guide;
- seafaring, ships, crews, ports, naval movement/combat, maritime hazards -> consult the relevant seafaring guide;
- a consequential domain with likely Dragon Magazine support -> route through `DRAGON_MAGAZINE_SOURCE_POLICY.md` at article level.

Consultation may inform lore, framing, DM preparation, source discovery, and compatible detail. It does **not** activate every option, kit, subsystem, table, proficiency, item, spell, or variant rule in that source.

## Guidance versus mechanics

Before applying supplement content, classify the retrieved material:

1. **Compatible guidance/lore** — descriptive, cultural, organizational, procedural, or worldbuilding material that does not materially alter governing mechanics. May be used automatically when compatible with active setting/adventure/core authority.
2. **Case-specific source fact** — a fact explicitly governing the active setting/adventure/location/NPC/item. Apply within that scope.
3. **Optional mechanic** — a new or alternate rule, subsystem, kit, proficiency, character option, combat procedure, construction system, naval system, etc. Do not silently activate if it changes player-facing or campaign-wide mechanics.
4. **DM-side procedure legitimately within DM authority** — may be adopted for the case when it is clearly a DM-facing elaboration compatible with existing campaign rules and does not silently replace an established player-facing rule; record the scope when consequential.
5. **Conflict/override** — if material conflicts with active core/setting/adventure authority, resolve precedence before use.

## Scope and precedence

Use scope-first precedence:

`active adventure-specific treatment -> active setting-specific treatment -> explicitly adopted specialist/optional treatment -> otherwise governing core rule`

This is not a blind hierarchy. A specialist book or Dragon article may supply compatible detail to an active setting only where it does not contradict or flatten the setting's own treatment.

Bilateral protection:
- do not flatten setting-specific elves, dwarves, ships, castles, villains, equipment, religions, monsters, etc. into generic specialist/article assumptions when the setting/adventure explicitly differs;
- do not import setting- or supplement-specific assumptions into generic play merely because they are available.

## Race and culture routing

When a race/species becomes consequential beyond a trivial mention, the DM should determine whether a race-specialist source is relevant for:
- physiology/lifespan/family structure where source-supported;
- worldview, social norms, settlements, crafts, warfare, religion, relations, language, names, customs, and material culture;
- race-specific class traditions or equipment;
- NPC portrayal and settlement generation;
- setting-compatible subgroups or variants.

Dragon race/culture articles may be consulted as secondary material after active setting/PHBR scope is resolved.

Do not automatically enable race kits, ability changes, optional proficiencies, alternate class limits, new powers, or other mechanics merely because the race book/article was consulted.

## Class routing

When a class or class institution is consequential, class-specialist books may be consulted for:
- training, organizations, social role, equipment traditions, mentors, guilds/orders, spellcasting culture, professional practices, and NPC portrayal;
- candidate kits/options when Hiram explicitly wants to consider them.

Dragon class/profession articles may enrich this domain under article-level authority classification.

Do not silently activate kits or alternate class mechanics.

## DM-domain routing

DMGR/blue-book, Dragon DM-procedure, or equivalent specialist DM material is event-driven. Consult only when the domain is active enough to affect play or preparation.

High-value domains include:
- strongholds/castles/sieges;
- catacombs/dungeons/tombs and specialized site design;
- arms/equipment and specialist gear;
- villain creation/organizations/long-term antagonists;
- seafaring/ships/crews/naval procedures;
- religions, magic, ecology, organizations, environments, and other relevant DM-specialist domains present in Hiram's source library.

If a source contains a large optional subsystem, load only the section needed and distinguish source guidance from a mechanics activation decision.

## Dragon relationship

`DRAGON_MAGAZINE_SOURCE_POLICY.md` is the normative article-level resolver for Dragon Magazine.

Dragon is neither globally active nor merely ignored inspiration. Its retrieved articles are classified by scope and role. Setting-specific articles can be strong scoped support; optional mechanics remain activation-sensitive; generic guidance/inspiration may fill compatible gaps.

## Performance contract

Normal turns use a cheap router only:
- identify whether a specialist domain trigger fired;
- reuse already-resolved source scope and valid caches;
- do nothing when no trigger fired.

On first meaningful use of a new domain:
- perform targeted retrieval from likely source families;
- establish source scope/precedence;
- create compact projections or source locators only when repeated use justifies them.

Repeated use should prefer cached source routing/projections rather than re-searching whole books or magazines.

Do not preload whole PHBR/DMGR lines or Dragon issue runs into ordinary or Voice context.

## Voice

Preload only specialist material likely to matter in the immediate scene. If an unpreloaded supplement/Dragon rule becomes consequential and retrieval is unavailable, defer the lookup rather than guessing or silently defaulting to remembered material.

## Relationship to existing policy

This policy inherits `RULES_PROJECTION_POLICY.md`:
- source availability != activation;
- core remains default where no explicit/scope-specific override governs;
- projections are derived accelerators;
- exact source text wins conflicts;
- supplemental rules may be active globally, by domain, by character/option, by location/setting, or for one case.

It also follows `MONSTER_SOURCE_RESOLUTION_POLICY.md`'s scope-first principle for non-monster specialist sources.
