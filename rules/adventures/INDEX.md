# Wren Published Adventure Source Registry

This registry is a lightweight routing accelerator for `ADVENTURE_OPPORTUNITY_POLICY.md`. It does not instantiate adventures and does not replace exact uploaded-source retrieval.

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

Use:

`opportunity trigger -> current facets -> likely adventure families -> targeted uploaded-source search -> candidate fit review -> exact source inspection -> optional seeding`

Current facets may include:
- active setting/source scope;
- current/nearby region;
- terrain/environment;
- settlement/site type;
- active thread/faction/NPC/process;
- scenario form needed;
- approximate published level/risk range;
- tone;
- expected adaptation burden.

Do not broad-scan the entire adventure library every turn.

## Candidate metadata

For a repeatedly relevant candidate, lightweight derived metadata may record:
- title/source;
- source family;
- issue/module/product identity;
- setting/edition;
- stated level/risk range;
- environment/site type;
- short scenario-form tags;
- exact source locator;
- compatibility concerns;
- current commitment state: Candidate / Prepared Possibility / Seeded / Active / Dormant / Bypassed / Resolved.

Candidate metadata is routing/preparation state, not proof that the scenario exists in the campaign world.

## Registration policy

Do not pre-create entries for every adventure or every Dungeon issue merely for completeness. Add indexes/locators lazily when repeated retrieval friction or campaign relevance makes them useful.

Absence from this registry is never evidence that Hiram lacks a published adventure source. Search the uploaded source library when `state/rulings/adventure-opportunity-triggers.md` fires.
