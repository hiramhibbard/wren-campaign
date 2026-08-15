# Wren Published Adventure Source Registry

This registry routes published adventure candidates for `ADVENTURE_OPPORTUNITY_POLICY.md`. It does not instantiate adventures and does not replace exact uploaded-source authority.

**Primary campaign-local inventory:** `state/sources/adventure-index.md`

Published-source routing is one branch of the broader adventure resolver; original DM-created material remains first-class when it fits campaign causality better.

## Runtime behavior

For actual published-adventure selection, use:

`campaign-local adventure inventory -> availability filter -> fit/risk ranking -> bounded local binding check for one promising unknown -> exact source inspection for finalist -> optional seeding`

Do **not** begin with a broad File Library semantic search. Do not infer Hiram's whole adventure collection from a handful of search hits.

Current facets may include:
- active setting/source scope;
- current/nearby region;
- terrain/environment;
- settlement/site type;
- active thread/faction/NPC/process;
- scenario form needed;
- source-stated level/risk range as world-danger metadata;
- tone;
- adaptation burden;
- assumed hook/player-compliance dependencies.

If an indexed source is `available`, retrieve its exact campaign-local source when it survives fit review. If an indexed source is `unknown`, perform at most one bounded local lookup using its issue/product/title/author metadata before player-facing selection. Preserve `unknown` when a declared corpus has a binding/index gap; do not falsely conclude the source is absent.

Dungeon Magazine is a first-class source family and should be indexed at the **individual adventure/article level**, because one issue can contain multiple adventures with different level ranges/settings.

## Source families

- `standalone-adventure-module`
- `setting-specific-adventure`
- `adventure-collection-scenario`
- `dungeon-magazine-adventure`
- `dungeon-magazine-side-trek`
- `boxed-set-scenario`
- `sourcebook-embedded-adventure-site`
- `sourcebook-embedded-scenario-seed`
- `published-mini-adventure-or-encounter`

## Compiled adventure metadata

Published adventure/article objects may record title/source family/product/issue, setting/edition, source-stated level/risk range, environment/site types, scenario-form/theme tags, source dependencies, assumed hooks, maps/handouts, compact summaries, exact locators, and verification metadata.

Compilation and inventory metadata do **not** seed the scenario into Wren's world and do not substitute for exact adventure text.

## Commitment state

Campaign-preparation state remains separate from source metadata:
- Candidate;
- Prepared Possibility;
- Seeded;
- Active;
- Dormant / Bypassed / Resolved.

## Population strategy

Ordinary play: use the persistent inventory and add/verify entries lazily when they become relevant.

Maintenance/source conversion: batch-extract adventure/module/Dungeon metadata and cross-links, prioritizing low-level adventures and other high-value routing metadata. Exact keyed prose/maps need not be copied; retain locators and fetch surviving candidate source sections when needed.

Absence from this registry or the partial inventory is never evidence that Hiram lacks a relevant published adventure source.
