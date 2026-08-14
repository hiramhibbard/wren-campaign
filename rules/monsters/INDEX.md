# Wren Monster Projection Registry

This registry contains verified source-derived AD&D 2e monster projections created under `MONSTER_PROJECTION_POLICY.md` and resolved through `MONSTER_SOURCE_RESOLUTION_POLICY.md`.

The uploaded governing monster source remains authoritative. Projection existence does not instantiate a creature in the campaign and does not activate an otherwise inactive supplement.

## Status

Monster projections are demand-first and lazy. Create them when recurrence, combat frequency, regional/site population relevance, Voice latency, or consistency risk makes reuse worthwhile.

At present, no generic or setting-specific monster projections are required solely by this registry. Add entries as they are actually justified and verified.

## Source-family awareness

Monster lookup must recognize multiple source families rather than assuming the Monstrous Manual is the only monster source:
- core monster references;
- generic Monstrous Compendium material;
- setting-specific Monstrous Compendium appendices;
- Monstrous Compendium Annuals/anthologies;
- active adventure-specific monster treatments;
- other explicitly active setting/monster sources.

Source availability is not source activation. Use `MONSTER_SOURCE_RESOLUTION_POLICY.md` to resolve which treatment governs the current setting/adventure/region/case.

## Ecology inspiration layer

Non-authoritative monster ecology is routed separately through `MONSTER_ECOLOGY_INSPIRATION_POLICY.md`.

- inspiration registry: `rules/monsters/ecology-inspiration/INDEX.md`
- current registered source: `/r/DnDBehindTheScreen Monster Ecology Anthology`
- authority: inspiration-only; never governing
- required order: governing AD&D 2e source first, then identify an ecology gap, then consult inspiration candidates, then apply the old-school/2e compatibility filter, then resolve campaign-specific ecology

The ecology layer must not inject 5e mechanics, CR/party-level encounter balancing, modern cosmology, modern heroic-survivability assumptions, or unsupported setting lore into Wren.

## Entry requirements

Each projection registered here should include:
- stable projection id;
- path;
- monster identity;
- governing source title/family;
- exact source locator;
- active source scope;
- source activation status;
- companion sources and permitted contribution, if any;
- precedence/override notes;
- verification status;
- important `source-text-required` conditions;
- downstream encounter/site/regional domains likely to consume it.

If materially different generic and specialized treatments are both needed, register separate scope-aware projections rather than overwriting one with the other.

Fan/inspiration-derived campaign ecology normally belongs in population/site/DM campaign state, not the generic monster projection.

## Runtime rule

Use the lookup order defined in `MONSTER_PROJECTION_POLICY.md` and `MONSTER_SOURCE_RESOLUTION_POLICY.md`:

`encounter-instance state -> scope-resolved verified monster projection -> exact scope-resolved active source entry -> broader active monster-source-family search`

For unresolved ecology only, append:

`-> registered ecology inspiration candidates -> 2e compatibility filter -> resolved campaign ecology`

Do not promote encounter-specific HP, equipment, injuries, intentions, or population facts into a generic monster projection.

Do not default to a generic Monstrous Manual projection when an active setting/adventure-specific treatment governs, and do not import a specialized Compendium/Annual variant into generic play merely because it is available.