# Compiled Source Objects — Core Saving Throws and Encounter Reaction

Status: verified structured assertions from uploaded AD&D 2e PHB/DMG. Uploaded sources remain authoritative.

## Entity: Character saving throw progression

- entity_id: `adnd2e.rule.saving-throws.character`
- entity_type: `rule`
- assertion_id: `adnd2e.phb.table60.character-saving-throws.v1`
- source_id: `adnd2e.document.phb-deluxe`
- locator: `Chapter 9: Combat -> Table 60: Character Saving Throws, printed p. 134`
- source_role: `core-rule-source`
- activation_requirement: `core-default unless a more specific active source explicitly governs`
- verification_status: `verified`
- source_text_required: `true` for unusual category-priority questions or source-specific modifiers; `false` for table lookup itself

structured_data:
- categories_ordered:
  - `paralyzation-poison-death-magic`
  - `rod-staff-wand`
  - `petrification-polymorph`
  - `breath-weapon`
  - `spell`
- priest:
  - `1-3: [10,14,13,16,15]`
  - `4-6: [9,13,12,15,14]`
  - `7-9: [7,11,10,13,12]`
  - `10-12: [6,10,9,12,11]`
  - `13-15: [5,9,8,11,10]`
  - `16-18: [4,8,7,10,9]`
  - `19+: [2,6,5,8,7]`
- rogue:
  - `1-4: [13,14,12,16,15]`
  - `5-8: [12,12,11,15,13]`
  - `9-12: [11,10,10,14,11]`
  - `13-16: [10,8,9,13,9]`
  - `17-20: [9,6,8,12,7]`
  - `21+: [8,4,7,11,5]`
- warrior:
  - `0: [16,18,17,20,19]`
  - `1-2: [14,16,15,17,17]`
  - `3-4: [13,15,14,16,16]`
  - `5-6: [11,13,12,13,14]`
  - `7-8: [10,12,11,12,13]`
  - `9-10: [8,10,9,9,11]`
  - `11-12: [7,9,8,8,10]`
  - `13-14: [5,7,6,5,8]`
  - `15-16: [4,6,5,4,7]`
  - `17+: [3,5,4,4,6]`
- wizard:
  - `1-5: [14,11,13,15,12]`
  - `6-10: [13,9,11,13,10]`
  - `11-15: [11,7,9,11,8]`
  - `16-20: [10,5,7,9,6]`
  - `21+: [8,3,5,7,4]`
- notes:
  - `polymorph wand attacks use rod/staff/wand category rather than petrification/polymorph`

## Entity: Encounter reaction procedure

- entity_id: `adnd2e.rule.encounter.reaction`
- entity_type: `procedure`
- assertion_id: `adnd2e.dmg.table59.encounter-reactions.v1`
- source_id: `adnd2e.document.dmg-deluxe`
- locator: `Chapter 11: Encounters -> Table 59: Encounter Reactions, printed p. 140`
- source_role: `core-dm-rule-source`
- activation_requirement: `DM adjudicative aid when creature/NPC reaction is genuinely uncertain; never mandatory when motives/context already determine behavior`
- verification_status: `verified`
- source_text_required: `true` for interpretation/context or modifiers not represented below

structured_data:
- roll: `2d10 plus applicable modifiers`
- behavior_columns: `[friendly, indifferent, threatening, hostile]`
- result_categories: `[flight, friendly, indifferent, cautious, threatening, hostile]`
- rows:
  - `2-or-less: [friendly,friendly,friendly,flight]`
  - `3: [friendly,friendly,friendly,flight]`
  - `4: [friendly,friendly,cautious,flight]`
  - `5: [friendly,friendly,cautious,flight]`
  - `6: [friendly,friendly,cautious,cautious]`
  - `7: [friendly,indifferent,cautious,cautious]`
  - `8: [indifferent,indifferent,cautious,cautious]`
  - `9: [indifferent,indifferent,cautious,threatening]`
  - `10: [indifferent,indifferent,threatening,threatening]`
  - `11: [indifferent,indifferent,threatening,threatening]`
  - `12: [cautious,cautious,threatening,threatening]`
  - `13: [cautious,cautious,threatening,hostile]`
  - `14: [cautious,cautious,threatening,hostile]`
  - `15: [cautious,threatening,threatening,hostile]`
  - `16: [threatening,threatening,hostile,hostile]`
  - `17: [threatening,threatening,hostile,hostile]`
  - `18: [threatening,threatening,hostile,hostile]`
  - `19: [hostile,hostile,hostile,hostile]`
  - `20: [hostile,hostile,hostile,hostile]`
- interpretation:
  - `flight: avoidance/panic/terror/surrender`
  - `friendly: kind/helpful/conciliatory/non-aggressive`
  - `indifferent: neutral/bored/businesslike/unconcerned/unimpressed/oblivious`
  - `cautious: suspicious/wary/dubious/paranoid/guarded/untrusting/mildly conciliatory`
  - `threatening: boastful/bravado/blustering/intimidating/short-tempered/bluffing`
  - `hostile: irritable/hot-tempered/aggressive/violent`
- dm_constraint: `the table is an aid; do not use a result the DM cannot justify from the situation`

## Runtime use

- Character save lookup should resolve directly from class group + level + category, then apply only implicated modifiers/effects.
- Encounter reaction is invoked only when the NPC/creature's established motives, knowledge, morale, orders, alignment/ethos, and immediate situation do not already settle the reaction.
- For current Wren while mage 1, the base save row is `[14,11,13,15,12]`; canonical current character state remains the authority for whether modifiers/effects alter those values.
