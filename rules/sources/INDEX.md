# Wren Specialist Source Role Registry

Lightweight scope/domain router for `SUPPLEMENT_SOURCE_RESOLUTION_POLICY.md` and the compiled source layer. It does not activate supplements and does not replace uploaded-source authority.

## Roles

- `core-rule-source`
- `race-specialist-source`
- `class-specialist-source`
- `dm-domain-guide`
- `setting-specific-source`
- `adventure-specific-source`
- `periodical-secondary-source`
- `optional-rules-source`
- `inspiration-reference-source`

A document/article may have multiple roles by section/assertion.

## High-value source families

### PHBR / brown books
Use as race/class specialist references when the corresponding race/class/domain becomes consequential. Appropriate material includes culture, institutions, professional practice, NPC generation, equipment traditions, and candidate options.

Kits/options/alternate mechanics remain inactive unless explicitly adopted for the relevant scope.

### DMGR / blue books
Use as event-driven DM-domain references for strongholds/sieges, catacombs/tombs/dungeons, arms/equipment, villains/organizations, seafaring/ships, and other covered DM specialist domains.

Compatible DM guidance may be case-relevant without activating every optional subsystem.

### Dragon Magazine
Route article-level material through `DRAGON_MAGAZINE_SOURCE_POLICY.md` / `rules/dragon/INDEX.md`. Dragon is a periodical secondary family, with article-specific role/scope/activation.

## Lookup behavior

Prefer:

`domain -> active setting/adventure/rules scope -> verified compiled source entity/assertion if available -> likely specialist family/title -> targeted uploaded-source search -> exact section -> compile reusable assertion when useful`

Do not load/scan entire source families during ordinary turns.

Once a source title/section/article repeatedly proves useful, compile/register stable document/entity/assertion IDs and exact locators under `rules/source-knowledge/` rather than repeating broad PDF search.

## Scope protection

Always resolve active setting/adventure scope first.

- generic specialist material must not overwrite explicit setting/adventure treatment;
- setting-specific assumptions must not leak into generic play;
- source-object existence and source availability never imply activation;
- conflicts remain separate scoped assertions until precedence is resolved.

## Population strategy

Individual source documents and assertions may be compiled lazily during play or in batches during maintenance/offline extraction.

Absence of a title/object from this compact router is never evidence that Hiram lacks the source. Targeted uploaded-source search remains fallback.
