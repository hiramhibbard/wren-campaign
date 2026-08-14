# Wren Rules Dependency Registry — v1

This registry maps campaign-state changes and DM procedure domains to the structured rules projections, source fallbacks, and downstream runtime caches that may need attention.

It is routing metadata, not published-rule authority. Exact rules remain governed by Hiram's uploaded sources and `RULES_PROJECTION_POLICY.md`.

## General dispatch rule

On each relevant state change:

`changed fact -> implicated dependency domains -> valid projection/cache? -> refresh only affected values`

Do not scan every rules domain after an unrelated change.

If an applicable verified projection exists, use it. If missing, apply the automatic projection-creation rule in `RULES_PROJECTION_POLICY.md`; otherwise fall back to the exact uploaded source.

## Dependency routes

### XP changes
Impacts:
- next-level threshold comparison;
- advancement trigger only if threshold reached.

Prefer:
- current runtime `next-level XP threshold` cache.

Fallback/refresh:
- applicable class advancement projection;
- exact class advancement source table/section.

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
- existing class/advancement structured projections.

Do not regenerate source projections merely because the level changed. Read the new row/range and refresh affected runtime caches.

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
- activate existing projections for the new class/track;
- automatically create missing worthwhile projections when the source is available and the rule is deterministic/reusable;
- invalidate all old runtime caches whose derivation depends on the former track;
- retrieve exact source text for exceptions/interactions not safely represented structurally.

### Alignment changes
Impacts only rules that actually depend on alignment, such as:
- class eligibility/continuation or advancement effects;
- alignment-restricted items;
- spell/magical effects keyed to alignment;
- source-defined XP/training/advancement consequences;
- deity/religion or setting restrictions where applicable.

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

Activate/create only projections actually required by the new identity state.

### Ability-score changes
Impacts only values derived from the changed ability, such as:
- Strength -> encumbrance/carrying, melee adjustments, exceptional-strength mechanics if applicable;
- Dexterity -> AC/reaction/missile adjustments as applicable;
- Constitution -> HP/system-shock/resurrection or class-related values as applicable;
- Intelligence -> languages/spell-learning/max spell level or other wizard values as applicable;
- Wisdom -> magical defense/bonus spells or other source-defined values as applicable;
- Charisma -> reaction/loyalty/henchman limits and related values.

Prefer ability-score structured projection. Refresh only affected runtime caches.

### Equipment / armor / shield / weapon changes
Impacts, as applicable:
- AC;
- carried load/encumbrance;
- movement;
- attack/damage/speed/reach properties;
- proficiency/nonproficiency use;
- class/race/alignment restrictions;
- magical item effects and active-effect lifecycles.

Prefer equipment/weapon/armor projection when verified. Complex magical properties use exact item source or an item-specific structured projection when recurring.

### Carried-load changes
Impacts:
- encumbrance category/breakpoint;
- movement/combat consequences derived from encumbrance.

Prefer current encumbrance breakpoint cache. If crossed/invalid, use encumbrance projection; source fallback if projection missing or exception-sensitive.

### Spell memorization / casting / spell acquisition changes
Impacts, as applicable:
- memorized/available spell state;
- spell-slot capacity;
- spellbook/known spell state;
- components/resources;
- active-effect lifecycle registration;
- spell-learning limits/checks.

Prefer spell-progression projection for slot capacity and itemized spell projection for compact deterministic fields. Retrieve exact spell text whenever lifecycle, targeting, interaction, exception, or interpretation requires it.

### Magic item / potion / scroll / charged-item activation
Impacts, as applicable:
- resource/charge depletion;
- active-effect lifecycle;
- affected combat/movement/save/ability values;
- identification/usage restrictions;
- item-specific procedures.

Prefer item-specific structured projection only when it faithfully covers the needed fields. Exact source text is required for unusual interactions or incomplete projection coverage.

### Active effect / condition start, change, or end
Impacts only values/procedures explicitly modified by the effect.

Use the registered effect dependency set. Do not recompute unrelated character mechanics.

### Campaign optional-rule change
Invalidation tier: campaign-rules-profile.

Impacts:
- only projections/procedures governed or modified by the option;
- downstream runtime caches derived from those projections.

Action:
- re-evaluate source precedence/applicability;
- create/activate revised projections if deterministic and reusable;
- invalidate affected caches;
- preserve unrelated projections.

### Sourcebook / supplement / setting-rule activation or removal
Invalidation tier: campaign-rules-profile, and structured-source-projection where source precedence changes.

Action:
- identify rules domains added, overridden, or removed;
- update only affected projection precedence/routes;
- generate newly useful structured projections lazily or during campaign-generation/maintenance passes;
- preserve core projections that remain valid.

### Projection correction / source-version change
Invalidation tier: structured-source-projection.

Action:
- rebuild only affected projections;
- invalidate downstream runtime caches derived from them;
- revalidate consequential current character/campaign values before further use.

## Procedure-to-projection hints

These are default routing hints, not exhaustive authority:

- XP/advancement -> class advancement / XP projection.
- Level advancement -> class advancement + THAC0 + saves + Hit Dice + spell progression + proficiency progression + class abilities as applicable.
- Encumbrance -> Strength/encumbrance projection.
- Combat attack -> cached THAC0/attack value + weapon projection; exact combat source for unresolved modifiers/procedures.
- Saving throw -> cached save value; save progression projection only on invalidation or uncertainty.
- Travel -> movement/exploration/resource projections as implicated by the route and declared-action readiness check.
- Light/fuel depletion -> light-source/resource-duration projection.
- Spellcasting -> cached spell state + spell projection; exact spell entry for interpretation/interaction.
- Item/potion use -> item projection + active-effect/resource lifecycle; exact item entry when needed.
- NPC/monster mechanics -> relevant creature/source projection if already available; otherwise exact source, with projection creation only if repeated use justifies it.

## Projection creation timing

Projection generation may occur:
- during initial campaign generation for the core rules/options/classes likely to be used immediately;
- when a new dependency first becomes consequential during play;
- during maintenance when repeated source lookups reveal a worthwhile missing projection;
- when a new sourcebook/supplement is activated and its deterministic rules are likely to recur.

Do not preprocess every table in every uploaded book if it is unlikely to be used. Prefer demand-driven breadth with proactive generation for high-frequency core rules.

## Player/DM visibility

Rule projections must not accidentally expose hidden campaign facts. Published rule mechanics may be player-known according to normal campaign practice, but DM-only monster/item/adventure information and hidden source annotations must preserve their intended visibility when projected or preloaded.
