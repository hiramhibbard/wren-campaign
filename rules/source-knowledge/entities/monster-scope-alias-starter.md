# Compiled Source Objects — Monster Scope / Alias Starter Graph

Status: verified routing assertions from uploaded AD&D 2e Monstrous Manual and Mystara Monstrous Compendium Appendix. These are source-routing objects, not campaign population facts.

## Core source-precedence assertion

- entity_id: `adnd2e.monster.source-precedence.generic-core`
- entity_type: `source-rule`
- assertion_id: `adnd2e.mm.introduction.supersession.v1`
- source_id: `adnd2e.document.monstrous-manual-deluxe`
- locator: `Monstrous Manual introduction / Other Worlds`
- verification_status: `verified`
- source_text_required: `false` for precedence statement; `true` for specific creature exceptions`

structured_data:
- `Monstrous Manual contains revised/updated material from MC Volumes 1-2 plus later creatures`
- `where Monstrous Manual conflicts with previously published generic data, Monstrous Manual supersedes the earlier data`
- `setting-specific Monstrous Compendium appendices remain relevant for creatures as treated in those worlds`
- `a setting tag in Monstrous Manual does not mean the creature cannot exist elsewhere; actual campaign presence remains DM/campaign state`

## Mystara aliases / specialized mappings

Source: `adnd2e.document.monstrous-compendium.mystara-appendix`
Locator: `Other Monsters of Mystara`
Scope: `Mystara only unless another active source explicitly adopts the mapping`
Verification: `verified`

relationships:
- `mystara.monster.aquatic-beholder --ALIAS_OF_IN_SCOPE--> adnd2e.monster.eye-of-the-deep`
- `mystara.monster.blast-spore --CORRESPONDS_TO_IN_SCOPE--> adnd2e.monster.gas-spore`
- `mystara.monster.dwilfish --ALIAS_OF_IN_SCOPE--> adnd2e.monster.ixitxachitl`
- `mystara.monster.haoou --SELF_NAME_OF_IN_SCOPE--> adnd2e.monster.aerial-servant`
- `mystara.monster.hulker --ALIAS_OF_IN_SCOPE--> adnd2e.monster.umber-hulk`
- `mystara.monster.wer-tree --ALIAS_OF_IN_SCOPE--> adnd2e.monster.hangman-tree`
- `mystara.monster.lamara --CORRESPONDS_TO_IN_SCOPE--> adnd2e.monster.lamia-noble`
- `mystara.monster.nekrozon --IDENTICAL_TO_IN_SCOPE--> adnd2e.monster.catoblepas`
- `mystara.monster.sshai --SELF_NAME_OF_IN_SCOPE--> adnd2e.monster.invisible-stalker`
- `mystara.monster.strangle-vine --ALIAS_OF_IN_SCOPE--> adnd2e.monster.choke-creeper`

## Mystara dragon specialization

- entity_id: `mystara.monster.dragon.scope-profile`
- entity_type: `monster-scope-profile`
- assertion_id: `adnd2e.mc-mystara.dragon-general.scope.v1`
- source_id: `adnd2e.document.monstrous-compendium.mystara-appendix`
- locator: `Dragon, General`
- verification_status: `verified`
- source_text_required: `true` for individual dragon statistics/abilities`

structured_data:
- `Mystara has setting-specific dragon species/treatments`
- `some familiar dragons use Monstrous Manual baseline with Mystara-specific variations`
- `Mystara crystalline dragons differ from similarly named dragons elsewhere`
- `Mystara has unique crystalline, jade, onyx, and ruby gem-dragon species`
- `brown dragon is known as amber dragon in Mystara, with stated appearance/alignment variation while otherwise closely following the Monstrous Manual treatment`
- `Mystaran dragon alignment emphasis differs from generic assumptions; exact source governs in Mystara scope`

## Routing contract

When a creature is referenced:
`name/alias -> active setting/adventure scope -> scope-specific alias/mapping -> governing monster assertion -> exact source if needed`

Do not collapse scoped aliases into global synonyms. Example: `hulker` may route to `umber hulk` under Mystara scope without teaching the generic entity that every world calls umber hulks "hulkers." Likewise, a setting-specific dragon treatment must not overwrite the generic Monstrous Manual creature.