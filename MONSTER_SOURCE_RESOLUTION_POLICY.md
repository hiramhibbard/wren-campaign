# Wren Monster Source Resolution Policy — v1

This normative companion to `MONSTER_PROJECTION_POLICY.md` and `RULES_PROJECTION_POLICY.md` defines how the DM selects the governing AD&D 2e monster source when the same creature, creature family, or variant appears across the Monstrous Manual, Monstrous Compendiums, setting appendices, annuals, adventures, or other active sources.

## Core principle: scope first, not core first

Resolve the creature's **active campaign scope before choosing a source**.

Do not assume that the Monstrous Manual automatically governs merely because it is core/general. Do not assume that a setting-specific or later Compendium version governs merely because it exists in Hiram's library.

The correct question is:

`What source treatment governs this creature here, in this active setting/adventure/region/case?`

Then select the most specific **actually active** source treatment for that scope.

## Bilateral protection rule

Source precedence must protect against both errors:

1. **Generic contamination of specialized play** — if an active setting/adventure/source explicitly establishes a setting-appropriate version of a creature, do not silently flatten it back to the generic Monstrous Manual treatment.
2. **Specialized contamination of generic play** — if no specialized source is active for the current scope, do not import a Ravenloft, Dark Sun, Planescape, Spelljammer, annual, adventure-specific, or other variant merely because it is available or interesting.

Availability, upload date, specificity, or novelty alone never establishes activation.

## Monster source families

Classify available monster-capable sources by role when needed:

- `core-monster-reference` — e.g. the AD&D 2e Monstrous Manual;
- `generic-monstrous-compendium` — generic Monstrous Compendium volumes/material not tied to a specialized campaign scope;
- `setting-monstrous-compendium` — setting-specific Compendium appendices or equivalent setting creature references;
- `monstrous-compendium-annual` — annual collections containing creatures from multiple prior sources/scopes;
- `active-adventure-monster-source` — adventure-specific monster entries, variants, keyed creature modifications, or scenario-specific treatments;
- `active-setting-source` — other setting books that explicitly modify or define a creature for that setting;
- `other-active-monster-source` — another explicitly active source that legitimately governs the case.

Classification is routing metadata, not a statement that every source in the library is active.

## Resolution order

For a consequential monster lookup, perform this sequence:

1. **Determine active scope**
   - current campaign setting, if established;
   - active adventure/module/source context;
   - current region/site where a specialized source applies;
   - explicitly adopted monster variant or source override;
   - otherwise generic/core campaign scope.

2. **Identify candidate active sources for that scope**
   - exact adventure-specific treatment, if the adventure explicitly governs the creature here;
   - exact setting-specific treatment/Compendium appendix, if active and applicable;
   - explicitly active specialized monster source/variant;
   - otherwise generic/core monster sources.

3. **Select governing entry**
   Prefer the most specific source that is actually active for the current scope and explicitly addresses the creature/case.

4. **Consult companion sources when useful**
   Non-governing sources may contribute non-conflicting ecology, society, descriptive, or historical detail only when their relationship to the governing entry is compatible and the additional material does not silently import mechanics, setting assumptions, or contradictions.

5. **Record provenance and precedence**
   A reusable projection must record which source governs, the active scope, relevant companion sources, and any conflict/override notes.

6. **Escalate unresolved conflicts**
   If two active sources materially conflict and precedence cannot be established from source hierarchy, explicit campaign activation, or the active adventure/setting context, retrieve both exact entries and resolve the source-precedence question before consequential adjudication. Do not guess.

## Generic/core handling

The Monstrous Manual is the normal generic/core monster reference when no more specific active source governs the case.

Where an earlier generic Monstrous Compendium entry and the Monstrous Manual conflict and the campaign has no specialized active override, follow the source's own revision/supersession relationship where established by the books. Earlier generic Compendium material may still be consulted for fuller non-conflicting ecology/society/descriptive detail when useful.

Do not assume every older Compendium field is additive. If the newer governing treatment changed, removed, or contradicts it, the governing treatment wins.

## Setting-specific handling

When an established active setting has its own monster treatment, that treatment governs within its stated scope even if a generic Monstrous Manual entry exists.

Examples of applicable scope signals include:
- a setting-specific Monstrous Compendium appendix;
- a setting book stating that its version of a creature differs from the generic form;
- a regional ecology or planar treatment explicitly changing abilities, behavior, society, rarity, or habitat;
- a setting-specific encounter table whose creature entry directs the DM to specialized material.

Do not use generic MM fields to overwrite specialized mechanics/behavior merely because the generic entry is easier to retrieve.

The generic entry may still be used for fields the specialized source explicitly inherits or leaves unchanged, but only when that relationship is supported rather than assumed.

## Adventure-specific handling

An active published adventure may establish:
- unique named individuals;
- altered statistics;
- special equipment;
- spell selections;
- local behavior/orders;
- exceptional abilities/weaknesses;
- population composition;
- keyed encounter conditions.

These adventure-specific facts govern those instantiated creatures/encounters even when the generic species projection differs.

Do not mutate the generic species projection to match one adventure-specific individual/group. Store adventure-specific differences in the encounter/site/population layer unless the adventure explicitly defines a reusable variant that merits its own scoped projection.

## Annuals and anthology sources

Monstrous Compendium Annuals and anthology-like sources may contain entries originally associated with different settings, products, or contexts.

Before treating an Annual entry as governing, determine its original/intended scope where relevant and whether that scope is active.

Do not treat inclusion in an Annual as permission to make every collected creature generic campaign canon.

An Annual entry may become governing when:
- it is the best active published treatment for the creature in the current generic scope;
- its original/source scope is active;
- Hiram/DM explicitly adopts it for the case;
- another active source directs the DM to it.

## Projection provenance requirements

Each monster projection should include, as applicable:
- `governing_source`;
- `source_family`;
- `active_scope`;
- `source_locator`;
- `source_activation_status`;
- `companion_sources` and what each is permitted to contribute;
- `precedence_notes`;
- `setting/adventure override` status;
- `source-text-required` conditions;
- verification status.

Projection identity should be scope-aware when different active treatments materially differ. A generic goblin projection and a setting-specific goblin projection may coexist if both are needed; the resolver chooses between them by active scope.

## Runtime lookup order

For monsters, use:

`encounter-instance state -> scope-resolved verified monster projection -> exact scope-resolved active monster source entry -> broader active monster-source-family search`

Do not search only the Monstrous Manual when the current scope may have a specialized Compendium/adventure/setting treatment.

Do not search every monster source every round. Resolve source scope once, cache the governing provenance, and reopen source selection only when scope changes, a conflict appears, an override activates, or the projection becomes invalid.

## Source activation relationship

This policy inherits `RULES_PROJECTION_POLICY.md`:
- uploading a supplement does not activate it;
- creating a projection does not activate it;
- encountering a creature name does not activate every source containing that creature;
- setting/adventure activation can make a specialized treatment governing for that scope;
- player-facing optional/campaign-wide substitutions cannot be silently imposed.

## Voice / Context Compiler

When a monster is imminent, preload the already resolved governing projection/source locator plus encounter state.

Do not preload every Compendium variant. If a scope change makes source precedence uncertain during Voice and retrieval is unavailable, preserve the pending lookup rather than defaulting blindly to the Monstrous Manual or a remembered setting variant.

## Persistence

Source-resolution metadata attached to generic projections is derived/source-routing state.

Campaign facts created from a resolved monster encounter—individuals, populations, site state, casualties, alliances, clues, treasure, etc.—remain normal canonical campaign state and persist independently of later projection rebuilds.