# Wren Structured Rules Projection Policy — v1

This file defines the source-derived rules layer used to accelerate AD&D 2e adjudication without replacing Hiram's uploaded published sources as authority.

## Core authority chain

Use the following hierarchy:

`uploaded published source -> verified structured rules projection -> campaign rules profile/dependency selection -> character/runtime derived cache`

The uploaded source is authoritative. Structured projections, campaign selections, and runtime caches are derived accelerators.

If any derived layer conflicts with the governing uploaded source, the source wins. Correct or rebuild the derived layer before consequential adjudication continues.

## Core-source and supplement activation policy

The mere presence or upload of a supplement, setting book, optional-rules book, class book, splatbook, adventure, magazine article, or other secondary source does **not** activate its rules and does **not** allow it to supersede core-book rules.

Default behavior:
- core campaign rules already established as governing remain in force;
- newly uploaded supplemental material is available for retrieval and consideration, but is inactive for rules precedence unless explicitly adopted;
- a supplement may become active globally, by rules domain, for a specific character/class/kit/item/spell/location/setting situation, or for one isolated adjudication, but only when Hiram and/or the DM explicitly establishes that scope as appropriate;
- DM-only activation is appropriate only where the source itself governs hidden DM-side material or a case that is legitimately within DM authority; player-facing optional rules, character options, and campaign-wide rule substitutions must not be silently imposed merely because the source is available;
- relevance for lore, monsters, adventures, equipment, spells, or setting content does not automatically imply that every optional or variant rule in the same supplement is active.

A source may therefore be **available**, **case-relevant**, **partially active**, or **campaign-active**. These states are distinct and should be recorded when consequential.

If a supplemental rule conflicts with a currently governing core rule and no explicit activation/precedence decision exists, the core rule remains the default. Retrieve the conflicting source text if necessary and surface the choice when it materially affects play rather than silently applying the supplement.

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
- source activation state/scope when the projection derives from a supplement or optional source;
- known exceptions or explicit `source-text-required` conditions;
- source-set/version fingerprint or equivalent freshness marker when available;
- verification status;
- dependencies/overrides from supplements or campaign options.

A projection may summarize or normalize source rules, but it must not silently invent a value absent from the governing source.

## Runtime lookup order

For a consequential rules question or trigger, use the cheapest reliable path:

1. **Valid runtime cache** — use an already-verified character/encounter/effect value whose dependencies have not changed.
2. **Applicable structured rules projection** — perform a direct deterministic lookup by rule/projection ID, but only from sources active for the relevant scope.
3. **Exact cited source section** — retrieve the governing uploaded source when the projection is insufficient, ambiguous, invalidated, exception-sensitive, or explicitly marks source text as required.
4. **Broader source search** — use only when the exact governing source location is not yet known.

Do not bypass an adequate verified projection merely to reread the source. Do not trust a projection when an exception or unresolved interaction requires source text. Do not treat an inactive supplement projection as applicable merely because it exists.

## Rules dependency registry

Campaign state changes may alter which projections apply or which downstream caches remain valid. `state/rulings/rules-dependency-registry.md` defines the active dependency-routing rules.

When a canonical state change touches a dependency-bearing fact:

1. identify the implicated rules domains from the dependency registry;
2. invalidate only downstream caches/projections whose applicability actually depends on the changed fact;
3. locate existing verified projections from sources active for the relevant scope;
4. if a needed projection is missing, decide whether to generate it using the automatic projection-creation rule below;
5. if generation is not warranted or cannot be completed immediately, retrieve the exact governing uploaded source and adjudicate from authority;
6. refresh only the affected campaign/runtime derived state;
7. preserve provenance for every newly cached value.

## Automatic projection creation

A missing projection should normally be created or queued automatically when all of the following are true:
- the underlying source is already active for the relevant rules scope, or the projection is being created for reference without activating that source;
- the rule is deterministic or faithfully normalizable;
- the rule is likely to be consulted repeatedly in the current campaign or by the runtime;
- a structured form materially reduces latency, repeated search, or consistency risk;
- the governing uploaded source can be identified and verified;
- the projection can preserve exceptions/provenance without pretending to replace interpretive source text.

Creating a projection from an inactive supplement does **not** activate that supplement. Projection existence and source activation are separate facts.

Examples likely worth projecting when first needed:
- a newly relevant class's progression tables after class/dual-class/multi-class change, from the source actually governing that class;
- a newly relevant race/kit progression or restriction table when that option/source has been explicitly adopted and is repeatedly consequential;
- a campaign option that has been explicitly enabled and changes a frequently used deterministic table;
- a newly relevant equipment/weapon/item table that will be consulted repeatedly;
- explicitly adopted setting/supplement overrides to core progression or common procedures.

Do not create a new projection for:
- a one-off interpretive ruling unlikely to recur;
- complex prose whose meaning would be lost by flattening it;
- hidden information that cannot be safely represented in the intended visibility layer;
- trivial calculations already available from loaded valid values.

Gameplay must not stop solely because a projection does not yet exist. Fall back to the authoritative governing source, then create the projection when worthwhile and safe.

## Invalidation tiers

Distinguish three scopes of invalidation:

### 1. Runtime-cache invalidation — common
Triggered by character/encounter/effect facts such as level, class, ability score, equipment, carried load, active condition/effect, current spell state, or resource state. Recompute only affected runtime values.

### 2. Campaign-rules-profile invalidation — uncommon
Triggered by explicitly enabling/disabling an optional rule or supplement scope, changing a campaign rules assumption, adopting a setting-specific modifier, or changing which already-approved source governs a domain. Re-evaluate applicability/routing for affected projections and downstream caches.

Simply uploading or making a supplement available does not trigger campaign-rules-profile invalidation.

### 3. Structured-source-projection invalidation — rare
Triggered when the underlying source set/version changes, a projection is found incorrect/incomplete, source provenance changes, or an **active** supplement explicitly overrides the projected rule within its approved scope. Rebuild/replace the affected projection; do not regenerate unrelated projections.

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

The dependency check determines which **already governing or explicitly adopted** sources apply. A class change does not automatically activate every uploaded class supplement that mentions the new class.

An alignment change does not automatically regenerate broad rules material or activate alignment-related supplements. It routes only to rules from governing/approved sources whose applicability actually depends on alignment, such as class eligibility/continuation, item/spell effects, advancement modifiers, or other source-defined restrictions.

Race/species, kit, dual-class/multi-class status, deity/religion, setting, or similar identity changes follow the same dependency-driven pattern: activate/create only the projections whose applicability changes under sources that are actually active for that scope. A newly matching supplement is not automatically adopted.

## Source overrides and precedence

Structured projections must represent source activation and precedence explicitly.

Default precedence is:

`explicitly approved case/domain/campaign supplement override -> otherwise currently governing core rule`

A supplement can override core material only within an explicitly established scope. Uploading it, indexing it, generating projections from it, or discovering that it contains a more specific rule is not by itself an activation decision.

The campaign rules profile determines which source governs when multiple uploaded books contain applicable material. Record enough scope to distinguish, for example:
- supplement available but inactive;
- supplement active only for a named kit/class/item/spell/setting case;
- supplement active for one rules domain;
- supplement active campaign-wide where explicitly adopted.

If precedence is unresolved and consequential, retrieve the exact relevant sources and surface the unresolved campaign-rule decision rather than silently choosing. Until a conflicting supplement is explicitly adopted for that scope, retain the currently governing core rule.

## Voice and latency

Voice fast-path context may preload only the compact structured rule rows/values likely to be needed immediately, plus current runtime caches. Do not preload entire projection libraries merely because they exist, and do not preload inactive supplement rules as though they govern play.

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
