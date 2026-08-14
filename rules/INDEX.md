# Wren Structured Rules Projection Registry

This directory contains verified source-derived rules projections used as runtime accelerators under `RULES_PROJECTION_POLICY.md`.

The uploaded published sources remain authoritative. A projection is never authoritative merely because it exists here.

## Registry status

Projection generation is demand-first, with proactive generation for high-frequency core rules when campaign generation, play, or maintenance demonstrates clear value.

Existing character/runtime caches may continue to cite uploaded source tables directly until a corresponding verified projection is created.

## Active verified projections

### Encounters
- `adnd2e.dmg.encounters.wilderness-checks.v1` — `rules/encounters/dmg-wilderness-encounter-checks.md`
  - Core DMG Chapter 11 / Table 56.
  - Wilderness encounter check times and 1d10 encounter chance by terrain, plus population-density routing constraints.
  - Determines when/chance, not local encounter content.

### Travel / weather
- `adnd2e.dmg.travel.ship-weather.v1` — `rules/travel/dmg-ship-weather.md`
  - Core DMG Chapter 14 / Tables 78–79.
  - Daily ship-weather generation by season and sailing/rowing movement effects.
  - Does not replace regional climate or non-sea weather generation.

## Specialist source routing

- General scope/domain supplement resolver: `SUPPLEMENT_SOURCE_RESOLUTION_POLICY.md`
- Source-role registry: `rules/sources/INDEX.md`
- Event-driven triggers: `state/rulings/supplement-source-triggers.md`

PHBR/race/class specialist books and DMGR/domain guides are consulted only when their domain becomes consequential. Consultation does not activate optional mechanics. Active setting/adventure scope is resolved before generic specialist guidance is applied.

Performance contract: cheap domain routing on normal turns; targeted retrieval only on trigger; cache useful locators/projections for recurring domains; never preload whole supplement families.

## Monster projection family

- Monster projection registry: `rules/monsters/INDEX.md`
- Normative monster projection/encounter-layer policy: `MONSTER_PROJECTION_POLICY.md`
- Normative scope-first monster source resolver: `MONSTER_SOURCE_RESOLUTION_POLICY.md`
- Monster ecology inspiration policy: `MONSTER_ECOLOGY_INSPIRATION_POLICY.md`
- Monster ecology inspiration registry: `rules/monsters/ecology-inspiration/INDEX.md`

Monster projections are created lazily from the scope-resolved active governing AD&D 2e monster source when recurrence, regional/site use, combat frequency, Voice latency, or consistency makes reuse worthwhile. Generic monster projections remain separate from encounter-instance state and campaign population/site-group state.

Monster lookup is source-family aware: core Monstrous Manual, generic Monstrous Compendium material, setting-specific Compendium appendices, Annuals/anthologies, active adventure treatments, and other explicitly active monster sources may be candidates. Resolve current scope before choosing.

## Projection lifecycle

Each projection should be registered with:
- stable projection ID;
- path;
- source title/table/section locator;
- source family;
- active scope;
- verification status;
- source precedence/override notes when relevant;
- downstream dependency domains.

Use `state/rulings/rules-dependency-registry.md` for invalidation/dependency routing, `state/rulings/supplement-source-triggers.md` for specialist supplement routing, and `state/rulings/monster-runtime-triggers.md` for monster-specific routing.

## Planned high-value projection families

Create when first justified/verified:
- class advancement / XP;
- THAC0 / attack progression;
- saving throws;
- Hit Dice / class level progression;
- spell-slot progression;
- proficiency progression;
- ability-score effects;
- encumbrance;
- weapon / armor / equipment statistics;
- movement / exploration;
- light and common resource durations;
- encounter surprise/distance/reaction fields when repeated use justifies projection;
- frequently reused spell/item/monster structured fields where safe and useful;
- frequently reused deterministic PHBR/DMGR specialist tables only after their source scope is actually active or their reference projection is clearly worthwhile.

Do not create empty family files merely to satisfy this list, and do not treat projection creation as supplement activation.
