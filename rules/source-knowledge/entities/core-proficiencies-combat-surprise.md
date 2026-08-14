# Compiled Source Objects — Core Proficiencies, Combat Modifiers, Surprise / Encounter Distance

Status: verified structured assertions from uploaded AD&D 2e PHB/DMG. Uploaded sources remain authoritative.

## Entity: Proficiency slot progression

- entity_id: `adnd2e.rule.proficiencies.slots`
- entity_type: `rule`
- assertion_id: `adnd2e.phb.table34.proficiency-slots.v1`
- source_id: `adnd2e.document.phb-deluxe`
- locator: `Chapter 5: Proficiencies -> Table 34: Proficiency Slots, printed p. 71`
- source_role: `core-rule-source`
- activation_requirement: `weapon proficiencies core as governed by campaign rules; nonweapon proficiencies optional unless campaign/source scope activates them`
- verification_status: `verified`
- source_text_required: `true` for specialization, crossover, teacher/training, or source-specific proficiency exceptions`

structured_data:
- groups:
  - `Warrior: weapon initial 4; +1 every 3 levels; nonproficient weapon penalty -2; nonweapon initial 3; +1 every 3 levels`
  - `Wizard: weapon initial 1; +1 every 6 levels; nonproficient weapon penalty -5; nonweapon initial 4; +1 every 3 levels`
  - `Priest: weapon initial 2; +1 every 4 levels; nonproficient weapon penalty -3; nonweapon initial 4; +1 every 3 levels`
  - `Rogue: weapon initial 2; +1 every 4 levels; nonproficient weapon penalty -3; nonweapon initial 3; +1 every 4 levels`
- multiclass_note: `source states multi-class characters use the most beneficial Table 34 line for initial proficiencies and gain rate`
- nonweapon_option_note: `PHB explicitly states nonweapon proficiencies are optional even if weapon proficiencies are used`

## Entity: Standard combat attack modifiers

- entity_id: `adnd2e.rule.combat.attack-modifiers.standard`
- entity_type: `rule`
- assertion_id: `adnd2e.phb.table51.combat-modifiers.v1`
- source_id: `adnd2e.document.phb-deluxe`
- locator: `Chapter 9: Combat -> Table 51: Combat Modifiers, printed p. 120`
- source_role: `core-rule-source`
- activation_requirement: `core-default`
- verification_status: `verified`
- source_text_required: `true` for unusual positioning/visibility/automatic-kill context beyond table fields`

structured_data:
- attacker_on_higher_ground: `+1 attack roll`
- defender_invisible: `-4`
- defender_off_balance: `+2`
- defender_sleeping_or_held: `automatic hit; source includes special automatic-slay context when no normal melee continues`
- defender_stunned_or_prone: `+4`
- defender_surprised: `+1`
- missile_long_range: `-5`
- missile_medium_range: `-2`
- rear_attack: `+2`

## Entity: Surprise modifiers

- entity_id: `adnd2e.rule.encounter.surprise-modifiers`
- entity_type: `procedure`
- assertion_id: `adnd2e.dmg.table57.surprise-modifiers.v1`
- source_id: `adnd2e.document.dmg-deluxe`
- locator: `Chapter 11: Encounters -> Table 57: Surprise Modifiers, printed p. 139`
- source_role: `core-dm-rule-source`
- activation_requirement: `use only when surprise is actually possible/uncertain; prior warning or lack of concealment may eliminate need for a roll`
- verification_status: `verified`
- source_text_required: `true` for base surprise procedure and unusual situational comparison not represented below`

structured_data:
- other_party:
  - `silenced: -2`
  - `invisible: -2`
  - `distinctive odor: +2`
  - `every 10 members: +1`
  - `camouflaged: -1 to -3`
- pc_party:
  - `fleeing: -2`
  - `poor light: -1`
  - `darkness: -4`
  - `panicked: -2`
  - `anticipating attack: +2`
  - `suspicious: +2`
- conditions:
  - `rainy: -1`
  - `heavy fog: -2`
  - `extremely still: +2`
- definitions:
  - `anticipating attack: good cause to suspect immediate danger and likely general direction`
  - `suspicious: grounds to believe another group may make a hostile move`

## Entity: Encounter distance

- entity_id: `adnd2e.rule.encounter.distance`
- entity_type: `procedure`
- assertion_id: `adnd2e.dmg.table58.encounter-distance.v1`
- source_id: `adnd2e.document.dmg-deluxe`
- locator: `Chapter 11: Encounters -> Table 58: Encounter Distance, printed p. 139`
- source_role: `core-dm-rule-source`
- activation_requirement: `after an encounter occurs and initial notice distance matters`
- verification_status: `verified`
- source_text_required: `true` for visibility/identification edge cases beyond listed terrain`

structured_data:
- both_groups_surprised: `3d6 feet`
- one_group_surprised: `4d6 feet`
- no_surprise:
  - `smoke_or_heavy_fog: 6d6 feet`
  - `jungle_or_dense_forest: 1d10 x 10 feet`
  - `light_forest: 2d6 x 10 feet`
  - `scrub_brush_bush: 2d12 x 10 feet`
  - `grassland_little_cover: 5d10 x 10 feet`
  - `nighttime_or_dungeon: limit of sight`
- open_no_cover_note: `encounter normally occurs at limit of vision unless special circumstances dictate otherwise`

## Runtime use

- Proficiency state should derive from current class/group + campaign option activation, not from this source object alone.
- Standard attack modifiers may be applied directly when their factual preconditions are established.
- Surprise should not be rolled merely because an encounter occurs; first determine whether warning/concealment makes surprise possible.
- Encounter distance follows surprise state + terrain/visibility and may still require exact-source adjudication for identification distance or unusual conditions.
