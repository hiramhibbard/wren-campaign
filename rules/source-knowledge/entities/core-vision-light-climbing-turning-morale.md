# Compiled Source Objects — Core Vision / Light / Climbing / Turning / Morale

Status: verified structured assertions from uploaded AD&D 2e PHB/DMG. Uploaded sources remain authoritative.

## Entity: Visibility ranges

- entity_id: `adnd2e.rule.vision.visibility-ranges`
- assertion_id: `adnd2e.phb.table62.visibility-ranges.v1`
- source_id: `adnd2e.document.phb-deluxe`
- locator: `Chapter 14: Vision and Light -> Table 62: Visibility Ranges, printed p. 155`
- verification_status: `verified`
- source_text_required: `true` for terrain obstruction, unusual worlds/planes, exceptional size/group effects, or identification disputes`

structured_data:
- columns: `[movement, spotted, type, id, detail]` in yards
- clear_sky: `[1500,1000,500,100,10]`
- dense_fog_or_blizzard: `[10,10,5,5,3]`
- light_fog_or_snow: `[500,200,100,30,10]`
- moderate_fog: `[100,50,25,15,10]`
- mist_or_light_rain: `[1000,500,250,30,10]`
- night_full_moon: `[100,50,30,10,5]`
- night_no_moon: `[50,20,10,5,3]`
- twilight: `[500,300,150,30,10]`
- small_creature_rule: `reduce movement/spotted/type one category; detail unchanged; source example clear conditions gives 1000/500/100/10/10`
- large_creature_rule: `double movement/spotted/type ranges`
- terrain_note: `terrain affects chance/line of sight, not the table's weather-condition identification ranges`

## Entity: Common light sources

- entity_id: `adnd2e.rule.light.common-sources`
- assertion_id: `adnd2e.phb.table63.light-sources.v1`
- source_id: `adnd2e.document.phb-deluxe`
- locator: `Chapter 14: Vision and Light -> Table 63: Light Sources, printed p. 155`
- verification_status: `verified`
- source_text_required: `true` for fuel handling, wind/water/extinguishing, magical-item exceptions, or campaign availability`

structured_data:
- beacon_lantern: `240 ft cone; 30 hours/pint; beam ~90 ft wide at far end`
- bonfire: `50 ft radius; 1/2 hour per armload`
- bullseye_lantern: `60 ft cone; 2 hours/pint; beam ~20 ft wide at far end`
- campfire: `35 ft radius; 1 hour per armload`
- candle: `5 ft radius; 10 minutes/inch`
- continual_light: `60 ft radius; indefinite`
- hooded_lantern: `30 ft radius; 2 hours/pint`
- light_spell: `20 ft radius; variable`
- torch: `15 ft radius; 30 minutes`
- magical_weapon: `5 ft if DM uses optional glowing-weapon rule; duration as desired`
- tactical_note: `a carried light makes its bearer/area visible to observers outside the illuminated radius before the bearer can necessarily see them`
- normal_vision_lightless: `impossible without a light source`
- infravision_default_cap: `60 ft unless otherwise noted; exact operating model depends on DM choice`

## Entity: Base climbing success

- entity_id: `adnd2e.rule.climbing.success`
- assertion_id: `adnd2e.phb.tables65-66.climbing-success.v1`
- source_id: `adnd2e.document.phb-deluxe`
- locator: `Chapter 14: Time and Movement -> Tables 65-66, printed p. 161`
- verification_status: `verified`
- source_text_required: `true` for fall timing, combat/spellcasting while climbing, tool setup, long-climb check frequency, and unusual surfaces`

structured_data:
- base_success:
  - `thief_with_mountaineering: climb-walls % +10%`
  - `thief: climb-walls %`
  - `mountaineering_proficiency: 40% +10% per proficiency slot`
  - `mountaineer_by_dm: 50%`
  - `unskilled: 40%`
- modifiers:
  - `abundant handholds: +40%`
  - `rope and wall: +55%`
  - `sloped inward: +25%`
  - `banded/splint armor: -25%`
  - `plate armor: -50%`
  - `scale/chain: -15%`
  - `studded leather/padded: -5%`
  - `dwarf: -10%`
  - `gnome: -15%`
  - `halfling: -15%`
  - `encumbrance: -5% per category above unencumbered or movement-rate point lost`
  - `slightly slippery: -25%`
  - `slippery: -40%`
  - `below half hp: -10%`
- race_note: `do not double-penalize thieves for racial modifiers already included in thief skill calculation`
- rope_wall_definition: `character braces feet against climbed surface while rope assists`

## Entity: Climbing rate

- entity_id: `adnd2e.rule.climbing.rate`
- assertion_id: `adnd2e.phb.table67.climbing-rate.v1`
- source_id: `adnd2e.document.phb-deluxe`
- locator: `Chapter 14: Time and Movement -> Table 67: Rates of Climbing, printed p. 163`
- verification_status: `verified`
- source_text_required: `true` for fall-catching, rappelling setup, combat, spellcasting, and tool requirements`

structured_data:
- rule: `table multiplier × current movement rate = feet climbed per round; thieves climb at double normal nonthief rate`
- dry/slightly_slippery/slippery multipliers:
  - `very smooth: 1/4 / special thief-only 1/4 / impossible`
  - `smooth cracked: 1/2 / 1/3 / 1/4`
  - `rough: 1 / 1/3 / 1/4`
  - `rough with ledges: 1 / 1/2 / 1/3`
  - `ice wall: impossible / impossible / 1/4`
  - `tree: 4 / 3 / 2`
  - `sloping wall: 3 / 2 / 1`
  - `rope and wall: 2 / 1 / 1/2`
- tool_requirement: `nonthieves need mountaineer status and appropriate tools for very smooth, smooth/cracked, and rough surfaces as marked by source`
- rappel: `supported rappel Climbing check +50; free rappel +30; speed equals normal dungeon movement`

## Entity: Turning undead

- entity_id: `adnd2e.rule.priest.turn-undead`
- assertion_id: `adnd2e.phb.table61.turning-undead.v1`
- source_id: `adnd2e.document.phb-deluxe`
- locator: `Chapter 9: Combat -> Turning Undead / Table 61, printed pp. 136-137`
- verification_status: `verified`
- source_text_required: `true` for evil-priest commanding, special undead, source-specific priest mythoi, or unusual control interactions`

structured_data:
- action: `one round/action on character's initiative; speech and gestures required; hands free; not interrupted merely by being attacked`
- attempts: `one attempt per character per encounter`
- paladin_level: `uses priest column two levels lower`
- success_roll: `1d20 equal to or above table number`; T=`automatic turn`; D=`destroy`; dash=`cannot turn`
- affected_number: `2d6 undead on successful turn/dispel; lowest HD affected first in mixed group`
- one_roll_multiple_types: `one d20 result is read separately against each undead type`
- table_rows_by_priest_level_1_2_3_4_5_6_7_8_9_10to11_12to13_14plus:
  - `skeleton_or_1HD: [10,7,4,T,T,D,D,D*,D*,D*,D*,D*]`
  - `zombie: [13,10,7,4,T,T,D,D,D*,D*,D*,D*]`
  - `ghoul_or_2HD: [16,13,10,7,4,T,T,D,D,D*,D*,D*]`
  - `shadow_or_3to4HD: [19,16,13,10,7,4,T,T,D,D,D*,D*]`
  - `wight_or_5HD: [20,19,16,13,10,7,4,T,T,D,D,D*]`
  - `ghast: [-,20,19,16,13,10,7,4,T,T,D,D]`
  - `wraith_or_6HD: [-,-,20,19,16,13,10,7,4,T,T,D]`
  - `mummy_or_7HD: [-,-,-,20,19,16,13,10,7,4,T,T]`
  - `spectre_or_8HD: [-,-,-,-,20,19,16,13,10,7,4,T]`
  - `vampire_or_9HD: [-,-,-,-,-,20,19,16,13,10,7,4]`
  - `ghost_or_10HD: [-,-,-,-,-,-,20,19,16,13,10,7]`
  - `lich_or_11plusHD: [-,-,-,-,-,-,-,20,19,16,13,10]`
  - `special: [-,-,-,-,-,-,-,-,20,19,16,13]`
- D_star: `destroys listed creatures plus additional 2d4 of that type`

## Entity: Morale procedure

- entity_id: `adnd2e.rule.morale.core`
- assertion_id: `adnd2e.dmg.morale.core.v1`
- source_id: `adnd2e.document.dmg-deluxe`
- locator: `DMG morale sections: NPC morale near Table 71 and Chapter 9 combat morale`
- verification_status: `verified`
- source_text_required: `true` for complete Table 71 loyalty modifiers, special NPC relationship modifiers, and situation-specific adjudication`

structured_data:
- npc_base_ratings:
  - `henchman: 12`
  - `hireling: 10`
- npc_morale_visibility: `DM-only/secret`
- combat_check_rule: `roll when combat rules or DM circumstances call for one; failure means retreat/flee or other context-appropriate loss of nerve`
- temptation_rule: `morale checks may adjudicate whether associated NPC succumbs to temptation`
- intelligent_monster_note: `monster entries supply morale category/rating; use that current 2e monster source rather than 1e percentile morale formulas`
- important_scope_note: `do not import AD&D 1e percentile morale procedure into the 2e campaign merely because a 1e DMG is present in the library`

## Runtime routing

`visibility/light need -> Table 62/63 object -> terrain/source exception if needed`

`climb declaration -> characterize surface/condition -> success object -> rate object -> exact source only for falls/tools/combat/rappel edge cases`

`turn undead -> current priest/paladin class scope -> Table 61 object -> exact source for special/commanding cases`

`morale trigger -> current NPC/monster morale source -> governing 2e morale procedure -> exact DMG relationship modifiers when consequential`
