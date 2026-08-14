# Wren Rules / Source Dependency Registry — v1

This registry maps campaign-state changes and DM procedure domains to verified compiled source objects/projections, exact source fallbacks, and downstream runtime caches that may need attention.

It is routing metadata, not published-rule authority. Exact published facts remain governed by Hiram's uploaded sources, with verified compiled objects used under `SOURCE_KNOWLEDGE_LAYER_POLICY.md` and `RULES_PROJECTION_POLICY.md`.

## General dispatch rule

On each relevant state change:

`changed fact -> implicated dependency domains -> valid runtime cache? -> verified in-scope compiled assertion/projection? -> exact source if needed -> refresh only affected values`

Do not scan every rules/source domain after an unrelated change.

If a verified compiled assertion/projection exists from a source active for the relevant scope and is sufficient, use it. If missing, stale, exception-sensitive, or marked `source_text_required`, retrieve the exact governing uploaded source. After correct adjudication, compile/refresh reusable structured material when worthwhile.

Uploaded supplements/Dragon articles/settings are **available, not automatically active**. Compilation never changes activation scope.

## Dependency routes

### XP changes
Impacts:
- next-level threshold comparison;
- advancement trigger only if threshold reached.

Prefer:
- current runtime `next-level XP threshold` cache;
- verified class advancement source assertion/projection.

Fallback:
- exact governing class advancement source table/section.

Current Wren fast path may resolve the mage threshold through `adnd2e.phb.table20.wizard-xp.v1` while his governing class remains mage.

### Level changes
Impacts, as applicable:
- next-level XP threshold;
- THAC0/attack progression;
- saving throws;
- Hit Dice/HP progression;
- spell-slot/spellcasting progression;
- proficiency-slot progression;
- class abilities/restrictions;
- other level-indexed mechanics.

Prefer existing verified class/source assertions from already governing sources. Read the new row/range and refresh only affected runtime caches. Do not rebuild source objects merely because level changed and do not activate a supplement merely because it contains alternate progression.

### Class / advancement-track changes
Impacts, as applicable:
- XP progression;
- THAC0;
- saving throws;
- Hit Dice/HP progression;
- proficiency progression;
- spellcasting progression;
- class abilities/restrictions;
- alignment requirements;
- equipment restrictions;
- item/spell interactions;
- dual-/multi-class rules.

Action:
- determine governing source set from established rules profile;
- resolve existing verified compiled entities/assertions for the new class/track only from sources active for that scope;
- lazily compile missing deterministic/reusable material after authoritative lookup when worthwhile;
- invalidate old runtime caches whose derivation depends on the former track;
- retrieve exact source text for exceptions/interactions not safely normalized;
- inactive supplements remain candidates only.

### Alignment changes
Impacts only rules that actually depend on alignment, such as class eligibility/continuation, alignment-restricted items, spells/effects, advancement consequences, or deity/setting restrictions.

Use only governing/explicitly adopted source assertions. Do not refresh THAC0, saves, encumbrance, or unrelated mechanics merely because alignment changed.

### Race/species / kit / dual-class / multi-class / deity or similar identity-track changes
Impacts only source-defined domains tied to that identity, potentially including class eligibility/limits, ability adjustments/limits, saving/perception modifiers, movement/senses, proficiencies/languages, spellcasting, equipment/magic restrictions, advancement, and special abilities.

Resolve/create only compiled assertions required by the new identity under sources active for that scope. Newly matching source availability is not activation.

### Ability-score changes
Impacts only values derived from the changed ability:
- Strength -> encumbrance/carrying, melee adjustments, exceptional-strength mechanics if applicable;
- Dexterity -> AC/reaction/missile adjustments;
- Constitution -> HP/system shock/resurrection/class values;
- Intelligence -> languages/spell-learning/max spell level/max spells per level where active;
- Wisdom -> magical defense/bonus spells and other source-defined values;
- Charisma -> reaction/loyalty/henchman limits.

Prefer verified ability-score source assertions and refresh only affected runtime caches.

For current Wren, the verified INT 18 assertion is `adnd2e.phb.table4.intelligence.18.v1`; its maximum-spells-per-level field applies only because campaign state separately enabled that option.

### Equipment / armor / shield / weapon changes
Impacts, as applicable:
- AC;
- carried load/encumbrance;
- movement;
- attack/damage/speed/reach;
- proficiency/nonproficiency use;
- class/race/alignment restrictions;
- magical-item effects/lifecycles.

Prefer verified equipment/item/weapon entities when in scope. Exact item/source text remains required for unusual interactions or incomplete objects.

### Carried-load changes
Impacts:
- encumbrance category/breakpoint;
- movement/combat consequences derived from encumbrance.

Prefer current breakpoint cache. If crossed/invalid, use governing encumbrance assertion/projection. Current core Table 47 compiled assertion is `adnd2e.phb.table47.character-encumbrance.v1`.

### Spell memorization / casting / spell acquisition changes
Impacts, as applicable:
- memorized/available spell state;
- spell-slot capacity;
- spellbook/known spell state;
- components/resources;
- active-effect lifecycle;
- learning limits/checks.

Prefer verified spell-progression and spell-definition entities from governing sources. Retrieve exact spell text when targeting, lifecycle, interaction, exception, or interpretation exceeds normalized fields.

Current Armor fast path: `adnd2e.phb.spell.armor.core.v1`.

### Magic item / potion / scroll / charged-item activation
Impacts resource/charge depletion, active effects, combat/movement/save/ability values, identification/use restrictions, and item-specific procedures.

Use the source governing the specific item. A supplement may govern that item without becoming campaign-wide. Compile recurring item definitions where faithful and useful; exact source remains fallback.

### Active effect / condition start, change, or end
Impacts only values/procedures explicitly modified by the effect. Use the registered effect dependency set and avoid unrelated recomputation.

### Campaign optional-rule change
Invalidation tier: campaign-rules-profile.

This route fires only when an optional rule is explicitly enabled/disabled/scope-changed. Uploading or compiling a source does not count.

Action:
- re-evaluate source precedence/applicability only for affected domains;
- activate/create applicable compiled assertions/projections;
- invalidate affected caches;
- preserve unrelated objects/caches.

### Sourcebook / supplement / setting / magazine availability
Availability alone causes no rules invalidation or precedence change.

Action:
- register source document/article/object metadata for retrieval when useful;
- compile reusable reference assertions if worthwhile without activating them;
- do not invalidate core projections/caches;
- later resolve scope when a case becomes consequential.

### Source explicit activation or removal
Invalidation tier: campaign-rules-profile, plus affected compiled/source projection applicability.

Requires explicit scope. Update only affected precedence routes/caches; preserve verified source objects as reference material outside active scope.

### Compiled assertion/projection correction or source-version change
Invalidation tier: source-knowledge/projection.

Action:
- mark only affected assertions stale/rejected/reverified;
- rebuild affected indexes;
- invalidate downstream runtime caches derived from them;
- revalidate consequential current values before further use.

Do not mutate canonical campaign state merely because a derived source object was corrected unless a previously persisted campaign value is proven wrong and requires explicit reconciliation.

## Procedure-to-source-object hints

Default hints:
- XP/advancement -> governing class advancement assertion.
- Level advancement -> class advancement + THAC0 + saves + HD + spell progression + proficiency/class abilities as applicable.
- Encumbrance -> Strength/encumbrance assertion.
- Combat attack -> cached THAC0 + weapon assertion; exact combat source for unresolved procedure/modifiers.
- Saving throw -> cached save value; governing save progression assertion on invalidation/uncertainty.
- Travel -> movement/exploration/resource assertions plus regional runtime.
- Light/fuel depletion -> light/resource-duration assertion.
- Spellcasting -> cached spell state + spell-definition assertion; exact source for interpretation/interaction.
- Item/potion use -> item definition + lifecycle; exact item entry when needed.
- NPC/monster mechanics -> scope-resolved creature entity/projection; exact source if missing/exception-sensitive.
- Worldbuilding/source procedure -> verified procedure object if present; otherwise exact World Builder/specialist/Dragon source as routed.
- Adventure discovery -> compiled adventure/article metadata first when available, then targeted source search.

## Compilation timing

Compiled source generation may occur:
- during initial campaign generation for governing high-frequency material;
- lazily when a dependency first becomes consequential;
- immediately after a reusable exact-source lookup;
- during maintenance/batch extraction;
- when a newly activated source introduces deterministic recurring material.

Do not preprocess every table in every book during ordinary play. Broad extraction is a maintenance/offline concern; gameplay uses demand-first compilation plus already populated high-value source objects.

## Player/DM visibility

Compiled published mechanics/source facts do not automatically become Wren's in-world knowledge. Context/knowledge filtering remains separate.

DM-only monster/item/adventure/source annotations and campaign-secret relationships must not leak merely because the source layer can retrieve them.
