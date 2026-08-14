# Wren Monster Projection Registry

This registry contains verified source-derived AD&D 2e monster projections created under `MONSTER_PROJECTION_POLICY.md`.

The uploaded governing monster source remains authoritative. Projection existence does not instantiate a creature in the campaign and does not activate an otherwise inactive supplement.

## Status

Monster projections are demand-first and lazy. Create them when recurrence, combat frequency, regional/site population relevance, Voice latency, or consistency risk makes reuse worthwhile.

At present, no generic monster projections are required solely by this registry. Add entries as they are actually justified and verified.

## Entry requirements

Each projection registered here should include:
- stable projection id;
- path;
- monster/source identity;
- exact source locator;
- active source scope;
- verification status;
- important `source-text-required` conditions;
- downstream encounter/site/regional domains likely to consume it.

## Runtime rule

Use the lookup order defined in `MONSTER_PROJECTION_POLICY.md`:

`encounter-instance state -> verified monster projection -> exact active source entry -> broader source search`

Do not promote encounter-specific HP, equipment, injuries, intentions, or population facts into a generic monster projection.