# Compiled Source Objects — Core Initiative, Missile Combat, Cover / Concealment

Status: verified structured assertions from uploaded AD&D 2e PHB/DMG. Uploaded sources remain authoritative.

## Entity: Group initiative

- entity_id: `adnd2e.rule.combat.initiative.group`
- entity_type: `procedure`
- assertion_id: `adnd2e.phb.initiative.group.v1`
- source_id: `adnd2e.document.phb-deluxe`
- locator: `Chapter 9: Combat -> Initiative / Tables 55-56, printed pp. 124-126`
- source_role: `core-rule-source`
- activation_requirement: `group initiative core procedure; optional action-specific modifiers only when the campaign/procedure uses them`
- verification_status: `verified`
- source_text_required: `true` for ties, waiting, interruptions, and special sequencing not represented below

structured_data:
- base_roll: `1d10 per side`
- winner: `lowest modified roll acts first`
- standard_modifiers_table55:
  - `hasted: -2`
  - `slowed: +2`
  - `on higher ground: -1`
  - `set to receive a charge: -2`
  - `wading or slippery footing: +2`
  - `wading in deep water: +4`
  - `foreign environment: +6`
  - `hindered: +3`
  - `waiting: +1`
- group_modifier_constraint: `everyone in the side/party involved in the round must qualify for a standard group modifier`

## Entity: Optional action-specific initiative modifiers

- entity_id: `adnd2e.rule.combat.initiative.action-modifiers`
- entity_type: `procedure`
- assertion_id: `adnd2e.phb.table56.optional-initiative-modifiers.v1`
- source_id: `adnd2e.document.phb-deluxe`
- locator: `Chapter 9: Combat -> Table 56: Optional Modifiers to Initiative, printed p. 125`
- source_role: `core-rule-source`
- activation_requirement: `optional initiative procedure; do not assume active merely because compiled`
- verification_status: `verified`
- source_text_required: `true` for magic-item exceptions and weapon-speed interactions beyond listed fields

structured_data:
- `attacking with weapon: add weapon speed factor`
- `breath weapon: +1`
- `casting spell: add numeric casting time`
- natural_weapon_creature_size:
  - `tiny: +0`
  - `small: +3`
  - `medium: +3`
  - `large: +6`
  - `huge: +9`
  - `gargantuan: +12`
- `innate spell ability: +3`
- magic_items:
  - `miscellaneous magic: +3`
  - `potion: +4`
  - `ring: +3`
  - `rod: +1`
  - `scroll: spell casting time`
  - `staff: +2`
  - `wand: +3`
- individual_initiative: `optional variant; each PC/NPC/monster rolls and modifies individually`

## Entity: Multiple attacks and spellcasting sequence

- entity_id: `adnd2e.rule.combat.sequence.multiple-attacks-spellcasting`
- entity_type: `procedure`
- assertion_id: `adnd2e.dmg.multiple-attacks-spellcasting-initiative.v1`
- source_id: `adnd2e.document.dmg-deluxe`
- locator: `Chapter 9: Combat -> Multiple Attacks / Spellcasting and Initiative, printed pp. 80-81`
- source_role: `core-dm-rule-source`
- verification_status: `verified`
- source_text_required: `true` for interruption, weapon-speed, casting-time, and special action edge cases`

structured_data:
- different_attack_forms: `resolve together at actor's initiative position`
- true_multiple_same_weapon_attacks: `staggered; everyone completes first action/attack before subsequent attack cycles`
- second_attack_cycle: `after ordinary first attacks/actions; ordering retains initiative relationship`
- numeric_spell_casting_time: `add to initiative when that optional procedure is in use`
- casting_time_one_round: `takes effect at end of current round; no normal initiative roll`
- casting_time_more_than_one_round: `effect occurs at end of final required round; disturbance can lose spell`

## Entity: Missile combat range / rate of fire / ability modifiers

- entity_id: `adnd2e.rule.combat.missile.core`
- entity_type: `procedure`
- assertion_id: `adnd2e.phb.missile-combat-core.v1`
- source_id: `adnd2e.document.phb-deluxe`
- locator: `Chapter 9: Combat -> Missile Weapons in Combat, printed pp. 131-132`
- source_role: `core-rule-source`
- verification_status: `verified`
- source_text_required: `true` for weapon-specific ranges/ROF and unusual missile forms not normalized here`

structured_data:
- range_attack_modifiers:
  - `short: 0`
  - `medium: -2`
  - `long: -5`
  - `beyond long: out of range`
- range_source: `weapon-specific ranges come from PHB Table 45 / equipment entry`
- rate_of_fire_examples:
  - `darts/light thrown weapons: up to 3/round where listed`
  - `bows/arrows: commonly up to 2/round where listed`
  - `heavy crossbow: may fire every other round where listed`
- multiple_missile_shots: `handled like other multiple attacks for initiative sequencing`
- strength:
  - `hurled weapon attack/damage uses Strength modifiers`
  - `bows use Strength modifiers only if specially prepared for that Strength`
  - `crossbows/similar mechanical devices do not receive Strength bonus`
- dexterity: `Dexterity attack modifier applies to hand-held missile weapons, not siege engines`

## Entity: Firing into melee

- entity_id: `adnd2e.rule.combat.missile.into-melee`
- entity_type: `procedure`
- assertion_id: `adnd2e.phb.firing-into-melee.v1`
- source_id: `adnd2e.document.phb-deluxe`
- locator: `Chapter 9: Combat -> Firing into a Melee, printed p. 132`
- source_role: `core-rule-source`
- verification_status: `verified`
- source_text_required: `true` for determining exactly which figures count as immediate targets in unusual geometry`

structured_data:
- target_weight_by_size:
  - `small: 0.5`
  - `medium: 1`
  - `large: 2`
  - `huge: 4`
  - `gargantuan: 6`
- process: `sum eligible figures' size weights; randomize actual target proportionally; then roll normal attack against the selected target`
- dm_information: `DM need not reveal who the actual randomized target is before resolving a successful shot`

## Entity: Cover and concealment

- entity_id: `adnd2e.rule.combat.cover-concealment`
- entity_type: `rule`
- assertion_id: `adnd2e.phb.table59.cover-concealment.v1`
- source_id: `adnd2e.document.phb-deluxe`
- locator: `Chapter 9: Combat -> Table 59: Cover and Concealment Modifiers, printed p. 132; DMG Table 44 equivalent`
- source_role: `core-rule-source`
- verification_status: `verified`
- source_text_required: `true` for adjudicating degree/direction of cover or unusual spell geometry`

structured_data:
- attack_roll_modifiers_against_target:
  - `25% cover: -2`
  - `50% cover: -4`
  - `75% cover: -7`
  - `90% cover: -10`
  - `25% concealment: -1`
  - `50% concealment: -2`
  - `75% concealment: -3`
  - `90% concealment: -4`
- definitions:
  - `cover = hard protection that can physically block missile`
  - `concealment = soft screening that makes target harder to locate but does not stop missile`
- physical_damage_spell_save_bonus: `cover modifier also functions as saving-throw bonus when cover actually lies between source/effect and target`
- ninety_percent_cover_damage_rule: `half normal damage on failed save; no damage on successful save when applicable cover actually intercepts effect`

## Runtime use

For ordinary combat, resolve only the implicated subprocedure. Do not load all initiative/missile/cover rules every round.

Preferred routing:
`declared action -> initiative procedure actually active -> action-specific modifier if active -> attack/missile procedure -> cover/concealment only if present -> exact source on edge case`

Compilation of optional initiative modifiers does not activate them campaign-wide.