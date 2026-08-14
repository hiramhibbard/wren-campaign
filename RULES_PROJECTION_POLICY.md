# Wren Structured Rules Projection Policy — v1

This file defines the source-derived rules layer used to accelerate AD&D 2e adjudication without replacing Hiram's uploaded published sources as authority.

## Core authority chain

Use the following hierarchy:

`uploaded published source -> verified structured rules projection -> campaign rules profile/dependency selection -> character/runtime derived cache`

The uploaded source is authoritative. Structured projections, campaign selections, and runtime caches are derived accelerators.

If any derived layer conflicts with the governing uploaded source, the source wins. Correct or rebuild the derived layer before consequential adjudication continues.

## Purpose

Structured rules projections exist to avoid repeated broad PDF/source search for deterministic, reusable rules that can be represented faithfully in compact structured form.

Typical projection material includes:
- class XP/advancement tables;
- THAC0/attack progression;
- saving throws;
- Hit Dice and class progression;
- spell-slot progression;
- proficiency progression;
- ability-score effects;
- encumbrance breakpoints;
- weapon/equipment statistics;
- movement and exploration rates;
- light/fuel/resource durations;
- encounter frequencies or other deterministic tables;
- item/spell/monster fields that are compact, repeatedly consulted, and source-verifiable.

Do not convert whole rulebooks into a second prose rulebook merely to avoid source retrieval. Complex exceptions, interpretive prose, interactions, and one-off edge cases should continue to resolve against the exact uploaded source.

## Projection record requirements

Each structured rule projection must preserve enough provenance and validity metadata to audit or rebuild it. As applicable record:
- stable rule/projection ID;
- system/edition;
- source title;
- exact table, chapter, section, page, spell/item/monster entry, or other source locator available from the uploaded source;
- normalized structured values/formula/procedure fields;
- scope and prerequisites;
- known exceptions or explicit `source-text-required` conditions;
- source-set/version fingerprint or equivalent freshness marker when available;
- verification status;
- dependencies/overrides from supplements or campaign options.

A projection may summarize or normalize source rules, but it must not silently invent a value absent from the governing source.

## Runtime lookup order

For a consequential rules question or trigger, use the cheapest reliable path:

1. **Valid runtime cache** — use an already-verified character/encounter/effect value whose dependencies have not changed.
2. **Applicable structured rules projection** — perform a direct deterministic lookup by rule/projection ID.
3. **Exact cited source section** — retrieve the governing uploaded source when the projection is insufficient, ambiguous, invalidated, exception-sensitive, or explicitly marks source text as required.
4. **Broader source search** — use only when the exact governing source location is not yet known.

Do not bypass an adequate verified projection merely to reread the source. Do not trust a projection when an exception or unresolved interaction requires source text.

## Rules dependency registry

Campaign state changes may alter which projections apply or which downstream caches remain valid. `state/rulings/rules-dependency-registry.md` defines the active dependency-routing rules.

When a canonical state change touches a dependency-bearing fact:

1. identify the implicated rules domains from the dependency registry;
2. invalidate only downstream caches/projections whose applicability actually depends on the changed fact;
3. locate existing verified projections for the new state;
4. if a needed projection is missing, decide whether to generate it using the automatic projection-creation rule below;
5. if generation is not warranted or cannot be completed immediately, retrieve the exact uploaded source and adjudicate from authority;
6. refresh only the affected campaign/runtime derived state;
7. preserve provenance for every newly cached value.

## Automatic projection creation

A missing projection should normally be created or queued automatically when all of the following are true:
- the rule is deterministic or faithfully normalizable;
- the rule is likely to be consulted repeatedly in the current campaign or by the runtime;
- a structured form materially reduces latency, repeated search, or consistency risk;
- the governing uploaded source can be identified and verified;
- the projection can preserve exceptions/provenance without pretending to replace interpretive source text.

Examples likely worth projecting when first needed:
- a newly relevant class's progression tables after class/dual-class/multi-class change;
- a newly relevant race/kit progression or restriction table when source-supported and repeatedly consequential;
- a campaign option that changes a frequently used deterministic table;
- a newly relevant equipment/weapon/item table that will be consulted repeatedly;
- setting/supplement overrides to core progression or common procedures.

Do not create a new projection for:
- a one-off interpretive ruling unlikely to recur;
- complex prose whose meaning would be lost by flattening it;
- hidden information that cannot be safely represented in the intended visibility layer;
- trivial calculations already available from loaded valid values.

Gameplay must not stop solely because a projection does not yet exist. Fall back to the authoritative source, then create the projection when worthwhile and safe.

## Invalidation tiers

Distinguish three scopes of invalidation:

### 1. Runtime-cache invalidation — common
Triggered by character/encounter/effect facts such as level, class, ability score, equipment, carried load, active condition/effect, current spell state, or resource state. Recompute only affected runtime values.

### 2. Campaign-rules-profile invalidation — uncommon
Triggered by enabling/disabling an optional rule, changing a campaign rules assumption, adopting a setting-specific modifier, or changing which source/supplement governs a domain. Re-evaluate applicability/routing for affected projections and downstream caches.

### 3. Structured-source-projection invalidation — rare
Triggered when the underlying source set/version changes, a projection is found incorrect/incomplete, source provenance changes, or a supplement explicitly overrides the projected rule. Rebuild/replace the affected projection; do not regenerate unrelated projections.

A level gain normally causes tier-1 refreshes from existing projections. It should not rebuild the class's source table.

## Class, alignment, race/species, kit, and similar changes

A class/advancement-track change must automatically evaluate dependencies including, as applicable:
- XP/advancement track;
- THAC0/attack progression;
- saving throws;
- Hit Dice/HP progression;
- proficiency progression;
- spellcasting progression;
- class abilities and restrictions;
- allowed equipment or magic interactions;
- alignment requirements or consequences;
- downstream runtime caches derived from any of the above.

An alignment change does not automatically regenerate broad rules material. It routes only to rules whose applicability actually depends on alignment, such as class eligibility/continuation, item/spell effects, advancement modifiers, or other source-defined restrictions.

Race/species, kit, dual-class/multi-class status, deity/religion, setting, or similar identity changes follow the same dependency-driven pattern: activate/create only the projections whose applicability changes.

## Source overrides and precedence

Structured projections must be able to represent precedence such as:

`campaign-selected supplement/setting override -> core rule fallback`

The campaign rules profile determines which source governs when multiple uploaded books contain applicable material. If precedence is unresolved and consequential, retrieve the exact sources and surface the unresolved campaign-rule decision rather than silently choosing.

## Voice and latency

Voice fast-path context may preload only the compact structured rule rows/values likely to be needed immediately, plus current runtime caches. Do not preload entire projection libraries merely because they exist.

When a Voice turn needs an unpreloaded rule and external retrieval is unavailable, follow the canonical deferred-lookup rule rather than guessing. A future application may make structured projections locally queryable during Voice.

## Rebuildability and portability

Structured rules projections are derived artifacts. Loss of the projection layer must not destroy campaign state or published source authority.

Given the uploaded source library, campaign rules profile, and projection definitions, the application should be able to rebuild the projection layer. Campaign export should distinguish source-derived projections from original uploaded source files and from canonical campaign state.

## Relationship to other architecture

- `STATE_SCHEMA.md` remains authoritative for campaign-state architecture and explicitly leaves exact published facts governed by uploaded source material.
- `CONTEXT_ARCHITECTURE.md` governs task-specific loading and fast/slow runtime paths.
- `DERIVED_INDEX_POLICY.md` governs retrieval indexes used to find campaign/source records; a structured rules projection differs because it contains verified normalized rule values, but it remains derived and subordinate to the uploaded source.
- `state/rulings/dm-procedure-triggers.md` determines which rules procedure becomes active.
- `state/rulings/rules-dependency-registry.md` maps state changes/procedure domains to likely rule projections and invalidation behavior.
