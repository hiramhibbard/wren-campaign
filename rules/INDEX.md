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

## Projection lifecycle

Each projection should be registered here with:
- stable projection ID;
- path;
- source title/table/section locator;
- scope;
- verification status;
- source precedence/override notes when relevant;
- downstream dependency domains.

Use `state/rulings/rules-dependency-registry.md` to decide when a projection is needed, activated, invalidated, or bypassed for exact source text.

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
- frequently reused spell/item/monster structured fields where safe and useful.

Do not create empty family files merely to satisfy this list.