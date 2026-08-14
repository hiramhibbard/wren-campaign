# Wren Structured Rules Projection Registry

This directory contains verified source-derived rules projections used as runtime accelerators under `RULES_PROJECTION_POLICY.md`.

The uploaded published sources remain authoritative. A projection is never authoritative merely because it exists here.

## Registry status

No broad rules library has been pre-generated yet. Create projections demand-first, with proactive generation for high-frequency core rules when campaign generation, play, or maintenance demonstrates clear value.

Existing character/runtime caches may continue to cite uploaded source tables directly until a corresponding verified projection is created.

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
- frequently reused spell/item/monster structured fields where safe and useful.

Do not create empty family files merely to satisfy this list.
