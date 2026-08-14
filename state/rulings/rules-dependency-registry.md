# Wren Rules Dependency Registry — v1

This registry maps campaign-state changes and DM procedure domains to the structured rules projections, source fallbacks, and downstream runtime caches that may need attention.

It is routing metadata, not published-rule authority. Exact rules remain governed by Hiram's uploaded sources and `RULES_PROJECTION_POLICY.md`.

## General dispatch rule

On each relevant state change:

`changed fact -> implicated dependency domains -> valid projection/cache? -> refresh only affected values`

Do not scan every rules domain after an unrelated change.

If an applicable verified projection exists from a source active for the relevant scope, use it. If missing, apply the automatic projection-creation rule in `RULES_PROJECTION_POLICY.md`; otherwise fall back to the exact governing uploaded source.

Uploaded supplements are **available, not automatically active**. A dependency change may reveal that a supplement contains potentially relevant material, but that discovery does not make the supplement govern play or supersede core rules. Only explicitly adopted campaign/domain/case scope may do that.

## Dependency routes

### XP changes
Impacts:
- next-level threshold comparison;
- advancement trigger only if threshold reached.

Prefer:
- current runtime `next-level XP threshold` cache.

Fallback/refresh:
- applicable class advancement projection from the governing source;
- exact governing class advancement source table/section.

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

Prefer:
- existing class/advancement structured projections from sources already active for the character/rules scope.

Do not regenerate source projections merely because the level changed. Read the new row/range and refresh affected runtime caches. Do not activate a supplement merely because it contains alternate progression for the new level.

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
- determine the governing source set from the already established campaign/case rules profile;
- activate existing projections for the new class/track only from sources active for that scope;
- automatically create missing worthwhile projections when the governing source is available and the rule is deterministic/reusable;
- invalidate all old runtime caches whose derivation depends on the former track;
- retrieve exact source text for exceptions/interactions not safely represented structurally;
- if an uploaded supplement offers additional/alternate class rules but has not been explicitly adopted, treat it as a candidate for discussion only, not as governing authority.

### Alignment changes
Impacts only rules that actually depend on alignment, such as:
- class eligibility/continuation or advancement effects;
- alignment-restricted items;
- spell/magical effects keyed to alignment;
- source-defined XP/training/advancement consequences;
- deity/religion or setting restrictions where applicable.

Use only governing/explicitly adopted sources for those domains. Do not activate an alignment supplement merely because the new alignment matches material in it.

Do not refresh THAC0, saves, encumbrance, or other unrelated mechanics merely because alignment changed.

### Race/species / kit / dual-class / multi-class / deity or similar identity-track changes
Impacts only source-defined domains tied to that identity, potentially including:
- class eligibility and limits;
- ability adjustments/limits;
- saving throw or perception modifiers;
- movement/senses;
- proficiency/language progression;
- spellcasting;
- equipment/magic restrictions;
- advancement rules;
- special abilities.

Activate/create only projections actually required by the new identity state **under sources already active for that scope**. If a newly matching supplement/kit/source is merely available but not adopted, do not silently activate it.

### Ability-score changes
Impacts only values derived from the changed ability, such as:
- Strength -> encumbrance/carrying, melee adjustments, exceptional-strength mechanics if applicable;
- Dexterity -> AC/reaction/missile adjustments as applicable;
- Constitution -> HP/system-shock/resurrection or class-related values as applicable;
- Intelligence -> languages/spell-learning/max spell level or other wizard values as applicable;
- Wisdom -> magical defense/bonus spells or other source-defined values as applicable;
- Charisma -> reaction/loyalty/henchman limits and related values.

Prefer ability-score structured projection from the governing source. Refresh only affected runtime caches.

### Equipment / armor / shield / weapon changes
Impacts, as applicable:
- AC;
- carried load/encumbrance;
- movement;
- attack/damage/speed/reach properties;
- proficiency/nonproficiency use;
- class/race/alignment restrictions;
- magical item effects and active-effect lifecycles.

Prefer equipment/weapon/armor projection when verified and active for the relevant source scope. Complex magical properties use exact item source or an item-specific structured projection when recurring.

### Carried-load changes
Impacts:
- encumbrance category/breakpoint;
- movement/combat consequences derived from encumbrance.

Prefer current encumbrance breakpoint cache. If crossed/invalid, use the governing encumbrance projection; source fallback if projection missing or exception-sensitive.

### Spell memorization / casting / spell acquisition changes
Impacts, as applicable:
- memorized/available spell state;
- spell-slot capacity;
- spellbook/known spell state;
- components/resources;
- active-effect lifecycle registration;
- spell-learning limits/checks.

Prefer spell-progression projection for slot capacity and itemized spell projection for compact deterministic fields, using only governing/approved sources. Retrieve exact spell text whenever lifecycle, targeting, interaction, exception, or interpretation requires it.

### Magic item / potion / scroll / charged-item activation
Impacts, as applicable:
- resource/charge depletion;
- active-effect lifecycle;
- affected combat/movement/save/ability values;
- identification/usage restrictions;
- item-specific procedures.

Use the source that actually governs the specific item/effect. A supplement that is the established source of that specific item may be case-relevant for that item without becoming a campaign-wide rules override. Prefer an item-specific structured projection only when it faithfully covers the needed fields. Exact source text is required for unusual interactions or incomplete projection coverage.

### Active effect / condition start, change, or end
Impacts only values/procedures explicitly modified by the effect.

Use the registered effect dependency set. Do not recompute unrelated character mechanics.

### Campaign optional-rule change
Invalidation tier: campaign-rules-profile.

This route activates only when an optional rule is **explicitly enabled, disabled, or scope-changed** by an applicable player/DM decision. Uploading a book containing optional rules is not such a change.

Impacts:
- only projections/procedures governed or modified by the option;
- downstream runtime caches derived from those projections.

Action:
- re-evaluate source precedence/applicability;
- create/activate revised projections if deterministic and reusable;
- invalidate affected caches;
- preserve unrelated projections.

### Sourcebook / supplement / setting-rule availability
Availability alone causes no rules invalidation and no precedence change.

Action:
- index/register the source as available for future retrieval;
- do not activate its optional/variant rules;
- do not invalidate core-rule projections or runtime caches;
- if later play creates a case where the supplement may be useful, surface/adjudicate that case under the activation policy rather than silently adopting the source.

### Sourcebook / supplement / setting-rule explicit activation or removal
Invalidation tier: campaign-rules-profile, and structured-source-projection where source precedence changes.

This route requires an explicit activation/removal decision with a defined scope (campaign-wide, rules-domain, character/option, item/spell/location/setting case, or other clear scope).

Action:
- identify rules domains added, overridden, or removed within the approved scope;
- update only affected projection precedence/routes;
- generate newly useful structured projections lazily or during campaign-generation/maintenance passes;
- preserve core projections that remain valid outside the approved scope.

### Projection correction / source-version change
Invalidation tier: structured-source-projection.

Action:
- rebuild only affected projections;
- invalidate downstream runtime caches derived from them;
- revalidate consequential current character/campaign values before further use.

## Procedure-to-projection hints

These are default routing hints, not exhaustive authority:

- XP/advancement -> governing class advancement / XP projection.
- Level advancement -> governing class advancement + THAC0 + saves + Hit Dice + spell progression + proficiency progression + class abilities as applicable.
- Encumbrance -> governing Strength/encumbrance projection.
- Combat attack -> cached THAC0/attack value + governing weapon projection; exact combat source for unresolved modifiers/procedures.
- Saving throw -> cached save value; governing save progression projection only on invalidation or uncertainty.
- Travel -> governing movement/exploration/resource projections as implicated by the route and declared-action readiness check.
- Light/fuel depletion -> governing light-source/resource-duration projection.
- Spellcasting -> cached spell state + governing spell projection; exact spell entry for interpretation/interaction.
- Item/potion use -> established item source projection + active-effect/resource lifecycle; exact item entry when needed.
- NPC/monster mechanics -> relevant creature/source projection if already available and applicable; otherwise exact source, with projection creation only if repeated use justifies it.

## Projection creation timing

Projection generation may occur:
- during initial campaign generation for the core rules/options/classes explicitly selected or clearly governing immediate play;
- when a new dependency first becomes consequential during play;
- during maintenance when repeated source lookups reveal a worthwhile missing projection;
- when a new sourcebook/supplement is explicitly activated for a defined scope and its deterministic rules are likely to recur.

A newly uploaded but inactive supplement may be indexed and may even have reference projections generated for later use, but projection creation must never be treated as source activation.

Do not preprocess every table in every uploaded book if it is unlikely to be used. Prefer demand-driven breadth with proactive generation for high-frequency governing rules.

## Player/DM visibility

Rule projections must not accidentally expose hidden campaign facts. Published rule mechanics may be player-known according to normal campaign practice, but DM-only monster/item/adventure information and hidden source annotations must preserve their intended visibility when projected or preloaded.
