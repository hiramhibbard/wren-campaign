# Compiled Source Objects — Wren/Core PHB Fast Path

Status: verified structured source assertions for high-frequency current-campaign use.

Source document: `adnd2e.document.phb-deluxe` (`DD2_PHB_Deluxe.pdf`).

These are derived accelerators under `SOURCE_KNOWLEDGE_LAYER_POLICY.md`. The uploaded PHB remains authoritative.

## Entity: Armor spell

- entity_id: `adnd2e.spell.wizard.armor`
- entity_type: `spell`
- canonical_name: `Armor`
- aliases: `armor spell`
- tags: `wizard`, `1st-level`, `conjuration`, `defense`, `force`

### Assertion: core spell definition

- assertion_id: `adnd2e.phb.spell.armor.core.v1`
- assertion_type: `spell-definition`
- source_id: `adnd2e.document.phb-deluxe`
- locator: `Chapter 7: Magic -> Wizard Spell Descriptions -> Armor`
- system_edition: `AD&D 2nd Edition`
- source_role: `core-rule-source`
- activation_requirement: `core-default`
- verification_status: `verified`
- source_text_required: `false` for ordinary casting/resource/effect lifecycle; `true` for unusual stacking/interaction disputes

structured_data:
- school: `Conjuration`
- level: `wizard 1`
- range: `Touch`
- components: `V, S, M`
- duration: `Special`
- casting_time: `1 round`
- area_of_effect: `1 creature`
- saving_throw: `None`
- granted_armor_class: `AC 6`
- no_effect_if_target_already: `armored or AC 6 or better`
- stacking:
  - `not cumulative with shield spell`
  - `cumulative with Dexterity`
  - `fighter/mage shield bonus may also apply as described by source`
- movement_or_spellcasting_hindrance: `none`
- weight_or_encumbrance: `none`
- ends_when:
  - `successfully dispelled`
  - `wearer sustains cumulative damage greater than 8 + caster level`
- damage_absorption: `none; wearer suffers successful attack damage normally`
- material_component: `piece of finely cured leather blessed by a priest`

## Entity: Wizard class advancement

- entity_id: `adnd2e.class.wizard`
- entity_type: `class`
- canonical_name: `Wizard`
- aliases: `mage`, `specialist wizard`

### Assertion: wizard XP/Hit Dice progression

- assertion_id: `adnd2e.phb.table20.wizard-xp.v1`
- assertion_type: `progression-table`
- source_id: `adnd2e.document.phb-deluxe`
- locator: `Chapter 3, Table 20: Wizard Experience Levels, printed p. 42`
- system_edition: `AD&D 2nd Edition`
- source_role: `core-rule-source`
- activation_requirement: `core-default`
- verification_status: `verified`
- source_text_required: `false`

structured_data:
- levels:
  - `1: xp 0; HD 1d4`
  - `2: xp 2,500; HD 2d4`
  - `3: xp 5,000; HD 3d4`
  - `4: xp 10,000; HD 4d4`
  - `5: xp 20,000; HD 5d4`
  - `6: xp 40,000; HD 6d4`
  - `7: xp 60,000; HD 7d4`
  - `8: xp 90,000; HD 8d4`
  - `9: xp 135,000; HD 9d4`
  - `10: xp 250,000; HD 10d4`
  - `11: xp 375,000; HD 10d4+1 hp`
  - `12: xp 750,000; HD 10d4+2 hp`
  - `13: xp 1,125,000; HD 10d4+3 hp`
  - `14: xp 1,500,000; HD 10d4+4 hp`
  - `15: xp 1,875,000; HD 10d4+5 hp`
  - `16: xp 2,250,000; HD 10d4+6 hp`
  - `17: xp 2,625,000; HD 10d4+7 hp`
  - `18: xp 3,000,000; HD 10d4+8 hp`
  - `19: xp 3,375,000; HD 10d4+9 hp`
  - `20: xp 3,750,000; HD 10d4+10 hp`

### Assertion: wizard spell-slot progression

- assertion_id: `adnd2e.phb.table21.wizard-spell-progression.v1`
- assertion_type: `progression-table`
- source_id: `adnd2e.document.phb-deluxe`
- locator: `Chapter 3, Table 21: Wizard Spell Progression, printed p. 43; Appendix 8 reproduction`
- system_edition: `AD&D 2nd Edition`
- source_role: `core-rule-source`
- activation_requirement: `core-default`
- verification_status: `verified`
- source_text_required: `false`

structured_data:
- slots_by_level:
  - `1: [1,0,0,0,0,0,0,0,0]`
  - `2: [2,0,0,0,0,0,0,0,0]`
  - `3: [2,1,0,0,0,0,0,0,0]`
  - `4: [3,2,0,0,0,0,0,0,0]`
  - `5: [4,2,1,0,0,0,0,0,0]`
  - `6: [4,2,2,0,0,0,0,0,0]`
  - `7: [4,3,2,1,0,0,0,0,0]`
  - `8: [4,3,3,2,0,0,0,0,0]`
  - `9: [4,3,3,2,1,0,0,0,0]`
  - `10: [4,4,3,2,2,0,0,0,0]`
  - `11: [4,4,4,3,3,0,0,0,0]`
  - `12: [4,4,4,4,4,1,0,0,0]`
  - `13: [5,5,5,4,4,2,0,0,0]`
  - `14: [5,5,5,4,4,2,1,0,0]`
  - `15: [5,5,5,5,5,2,1,0,0]`
  - `16: [5,5,5,5,5,3,2,1,0]`
  - `17: [5,5,5,5,5,3,3,2,0]`
  - `18: [5,5,5,5,5,3,3,2,1]`
  - `19: [5,5,5,5,5,3,3,3,1]`
  - `20: [5,5,5,5,5,4,3,3,2]`

## Entity: Intelligence ability

- entity_id: `adnd2e.ability.intelligence`
- entity_type: `ability`
- canonical_name: `Intelligence`

### Assertion: Intelligence 18 wizard limits

- assertion_id: `adnd2e.phb.table4.intelligence.18.v1`
- assertion_type: `table-row`
- source_id: `adnd2e.document.phb-deluxe`
- locator: `Table 4: Intelligence; Appendix 8 reproduction`
- system_edition: `AD&D 2nd Edition`
- source_role: `core-rule-source`
- activation_requirement: `core-default; maximum-spells-per-level usage remains governed by campaign option state`
- verification_status: `verified`
- source_text_required: `false` for row values; `true` for interpretation of optional/campaign activation if disputed

structured_data:
- score: `18`
- languages: `7`
- maximum_spell_level: `9th`
- chance_to_learn_spell: `85%`
- maximum_spells_per_level: `18`
- illusion_immunity: `none listed at 18`

## Entity: Character encumbrance

- entity_id: `adnd2e.rule.encumbrance.basic`
- entity_type: `rule`
- canonical_name: `Basic Encumbrance`

### Assertion: Character Encumbrance Table

- assertion_id: `adnd2e.phb.table47.character-encumbrance.v1`
- assertion_type: `table`
- source_id: `adnd2e.document.phb-deluxe`
- locator: `Chapter 6, Table 47: Character Encumbrance, printed p. 103`
- system_edition: `AD&D 2nd Edition`
- source_role: `core-rule-source`
- activation_requirement: `campaign encumbrance-profile applicability`
- verification_status: `verified`
- source_text_required: `false` for category breakpoints; `true` for unusual bulky-object adjudication or optional specific-encumbrance interactions

structured_data:
- categories: `[unencumbered, light, moderate, heavy, severe, max-carried]`
- rows:
  - `STR 2: 0-1 | 2 | 3 | 4 | 5-6 | 6`
  - `STR 3: 0-5 | 6 | 7 | 8-9 | 10 | 10`
  - `STR 4-5: 0-10 | 11-13 | 14-16 | 17-19 | 20-25 | 25`
  - `STR 6-7: 0-20 | 21-29 | 30-38 | 39-46 | 47-55 | 55`
  - `STR 8-9: 0-35 | 36-50 | 51-65 | 66-80 | 81-90 | 90`
  - `STR 10-11: 0-40 | 41-58 | 59-76 | 77-96 | 97-110 | 110`
  - `STR 12-13: 0-45 | 46-69 | 70-93 | 94-117 | 118-140 | 140`
  - `STR 14-15: 0-55 | 56-85 | 86-115 | 116-145 | 146-170 | 170`
  - `STR 16: 0-70 | 71-100 | 101-130 | 131-160 | 161-195 | 195`
  - `STR 17: 0-85 | 86-121 | 122-157 | 158-193 | 194-220 | 220`
  - `STR 18: 0-110 | 111-149 | 150-188 | 189-227 | 228-255 | 255`
  - `STR 18/01-50: 0-135 | 136-174 | 175-213 | 214-252 | 253-280 | 280`
  - `STR 18/51-75: 0-160 | 161-199 | 200-238 | 239-277 | 278-305 | 305`
  - `STR 18/76-90: 0-185 | 186-224 | 225-263 | 264-302 | 303-330 | 330`
  - `STR 18/91-99: 0-235 | 236-274 | 275-313 | 314-352 | 353-380 | 380`
  - `STR 18/00: 0-335 | 336-374 | 375-413 | 414-452 | 453-480 | 480`

## Entity: Calculated THAC0

- entity_id: `adnd2e.rule.thac0.calculated`
- entity_type: `rule`
- canonical_name: `Calculated THAC0s`

### Assertion: Wizard THAC0 progression

- assertion_id: `adnd2e.phb.table53.thac0.wizard.v1`
- assertion_type: `progression-table`
- source_id: `adnd2e.document.phb-deluxe`
- locator: `Table 53: Calculated THAC0s; Appendix 8`
- system_edition: `AD&D 2nd Edition`
- source_role: `core-rule-source`
- activation_requirement: `core-default`
- verification_status: `verified`
- source_text_required: `false`

structured_data:
- wizard_thac0_by_level:
  - `1:20, 2:20, 3:20`
  - `4:19, 5:19, 6:19`
  - `7:18, 8:18, 9:18`
  - `10:17, 11:17, 12:17`
  - `13:16, 14:16, 15:16`
  - `16:15, 17:15, 18:15`
  - `19:14, 20:14`

## Runtime shortcut for current Wren

Given current campaign state if Wren remains mage 1 / INT 18 / STR 9:
- next wizard level threshold: `2,500 XP` before campaign XP-bonus application logic;
- wizard spell slots at level 1: `one 1st-level slot`;
- base wizard THAC0 at level 1: `20`;
- STR 9 unencumbered breakpoint: `through 35 lb`;
- Armor ordinary result: `AC 6 before applicable Dexterity/other compatible modifiers` and damage-termination threshold based on caster level;
- INT 18 source row: `85% learn; maximum spell level 9th; 18 spells/level if that campaign option is active`.

This runtime shortcut is derived from the verified assertions above and current campaign identity facts; canonical Wren state remains authoritative for Wren's actual current level/abilities/options.
