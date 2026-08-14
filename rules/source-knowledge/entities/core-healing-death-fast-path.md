# Compiled Source Objects — Core Healing / Death Fast Path

Status: verified structured assertions from uploaded AD&D 2e Dungeon Master Guide. Uploaded source remains authoritative.

## Entity: Natural healing

- entity_id: `adnd2e.rule.healing.natural`
- entity_type: `procedure`
- assertion_id: `adnd2e.dmg.natural-healing.v1`
- source_id: `adnd2e.document.dmg-deluxe`
- locator: `Chapter 9: Combat -> Injury and Death -> Healing -> Natural Healing, printed p. 102`
- source_role: `core-dm-rule-source`
- activation_requirement: `core-default`
- verification_status: `verified`
- source_text_required: `false` for ordinary natural-healing calculation; `true` for unusual deprivation, disease, poison, or campaign-specific recovery interactions`

structured_data:
- normal_rest: `1 hp per day`
- rest_definition: `low activity; riding or ordinary travel is compatible`
- strenuous_activity_breaks_rest: `fighting, fleeing/running, heavy lifting, or similar exertion prevents natural healing for that day`
- complete_bed_rest: `3 hp per complete day`
- complete_week_bed_rest: `21 hp base plus Constitution hit-point bonus, if any`
- prerequisites: `adequate food, water, and sleep`
- deprived_day: `no natural hit-point recovery`
- maximum: `healing never raises current hp above normal maximum`

## Entity: Magical healing cap

- entity_id: `adnd2e.rule.healing.magical-cap`
- entity_type: `rule`
- assertion_id: `adnd2e.dmg.magical-healing-cap.v1`
- source_id: `adnd2e.document.dmg-deluxe`
- locator: `Chapter 9: Combat -> Injury and Death -> Healing -> Magical Healing, printed p. 102`
- source_role: `core-dm-rule-source`
- verification_status: `verified`
- source_text_required: `false` for cap; individual spell/item source still governs amount/effect`

structured_data:
- maximum: `magical healing cannot raise current hp above original/current maximum hp`
- effect_source: `spell, potion, or item definition governs actual healing amount and special conditions`

## Entity: Raising the dead / resurrection survival

- entity_id: `adnd2e.rule.death.raising`
- entity_type: `procedure`
- assertion_id: `adnd2e.dmg.raising-the-dead.v1`
- source_id: `adnd2e.document.dmg-deluxe`
- locator: `Chapter 9: Combat -> Injury and Death -> Raising the Dead`
- source_role: `core-dm-rule-source`
- verification_status: `verified`
- source_text_required: `true` for spell-specific restoration conditions, poison/disease persistence, and unusual resurrection effects`

structured_data:
- ordinary_healing_on_dead: `ineffective`
- return_methods: `raise dead, resurrection, or equivalent device/effect`
- check: `player rolls Constitution-based resurrection survival percentage from PHB Table 3`
- success: `returns in condition specified by governing spell/device`
- constitution_cost: `Constitution permanently reduced by 1 on successful return to life`
- hp_recalculation: `if Constitution hit-point bonus decreases, maximum hp is reduced accordingly for levels that benefited`
- hard_limit: `Constitution 0 means character can no longer be raised`

## Entity: Massive damage

- entity_id: `adnd2e.rule.death.massive-damage`
- entity_type: `rule`
- assertion_id: `adnd2e.dmg.massive-damage.v1`
- source_id: `adnd2e.document.dmg-deluxe`
- locator: `Chapter 9: Combat -> Injury and Death -> Death from Massive Damage`
- source_role: `core-dm-rule-source`
- verification_status: `verified`
- source_text_required: `false` for ordinary threshold/check`

structured_data:
- trigger: `50 or more hp from a single attack`
- check: `save vs. death`
- failure: `immediate death; hp becomes 0`
- multiple_attacks: `multiple separate attacks totaling 50+ in one round do not trigger this rule`
- independent_hp_rule: `successful save does not prevent normal death if hp loss itself reduces character to the campaign's death threshold`

## Entity: Hovering on death's door

- entity_id: `adnd2e.rule.death.deaths-door`
- entity_type: `optional-rule`
- assertion_id: `adnd2e.dmg.hovering-on-deaths-door.v1`
- source_id: `adnd2e.document.dmg-deluxe`
- locator: `Chapter 9: Combat -> Injury and Death -> Hovering on Death's Door (Optional Rule)`
- source_role: `core-optional-rule-source`
- activation_requirement: `explicit campaign activation required; compilation does not activate it`
- verification_status: `verified`
- source_text_required: `true` for full post-stabilization limitations and later recovery details`

structured_data:
- alive_until: `-10 hp`
- at_0_or_below: `falls unconscious`
- bleed_rate: `loses 1 hp per round until stabilized or dead`
- stabilization: `companion spends at least one round tending wounds before -10`
- binding_only: `stops further automatic hp loss but does not restore hp`
- cure_after_stabilization: `first cure restores character to 1 hp, no more`
- further_cures: `ineffective until at least one day of rest`
- immediate_condition: `weak/feeble; cannot fight or cast spells; barely mobile; exact limitations require source text`

## Runtime routing

`damage/injury -> current hp/death-rule campaign profile -> natural or magical healing assertion as applicable -> exact spell/item/death source only when exception-sensitive`

The optional death's-door rule remains inert unless canonically activated. This shard does not alter Wren's current hp/death-rule state.