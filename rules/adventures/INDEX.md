# Wren Published Adventure Source Registry

This registry routes published adventure candidates for `ADVENTURE_OPPORTUNITY_POLICY.md`. It does not instantiate adventures and does not replace exact uploaded-source authority.

Published-source routing is one branch of the broader adventure resolver; original DM-created material remains first-class when it fits campaign causality better.

## Source families

- `standalone-adventure-module`
- `setting-specific-adventure`
- `dungeon-magazine-adventure`
- `dungeon-magazine-side-trek`
- `boxed-set-scenario`
- `sourcebook-embedded-adventure-site`
- `sourcebook-embedded-scenario-seed`
- `published-mini-adventure-or-encounter`

Dungeon Magazine is explicitly a first-class source family.

## Runtime behavior

When published search is promising, prefer:

`opportunity trigger -> current facets -> compiled adventure/article metadata if available -> likely source families -> targeted source search for missing candidates -> fit review -> exact source inspection only for surviving candidates -> optional seeding`

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

Do not broad-scan the entire adventure library every turn, and do not keep searching indefinitely when no strong fit emerges. `ADVENTURE_OPPORTUNITY_POLICY.md` may route to original creation instead.

## Compiled adventure metadata

Under `SOURCE_KNOWLEDGE_SCHEMA.md`, published adventure/article objects may record:
- stable adventure/entity ID;
- title/source family/product/issue;
- setting/edition;
- source-stated level/risk range;
- environment/site types;
- scenario-form/theme tags;
- major actors/factions/monsters;
- source dependencies;
- assumed hooks;
- maps/handouts;
- compact scenario summary;
- exact locators;
- compatibility/adaptation notes;
- typed relationships to other source entities;
- verification/fingerprint metadata.

Compilation does **not** seed the scenario into Wren's world.

## Commitment state

Campaign-preparation state remains separate from source metadata:
- Candidate;
- Prepared Possibility;
- Seeded;
- Active;
- Dormant / Bypassed / Resolved.

Source objects describe published material. Campaign DM state records whether/how a scenario has actually entered Wren's causality.

## Population strategy

Ordinary play: compile discovered adventure metadata lazily when reusable.

Maintenance/offline extraction: batch-extract adventure/module/Dungeon metadata and cross-links because it can make opportunity searches dramatically cheaper. Exact keyed prose/maps need not be copied; retain locators and fetch surviving candidate source sections when needed.

Absence from this registry is never evidence that Hiram lacks a relevant published adventure source.
