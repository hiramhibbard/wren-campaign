# Compiled Source Objects — Core Movement / Travel Fast Path

Status: verified structured assertions from uploaded AD&D 2e PHB/DMG for common movement routing. Uploaded sources remain authoritative.

## Entity: Base movement rates

- entity_id: `adnd2e.rule.movement.base-rates`
- entity_type: `rule`
- assertion_id: `adnd2e.phb.table64.base-movement-rates.v1`
- source_id: `adnd2e.document.phb-deluxe`
- locator: `Chapter 14: Time and Movement -> Table 64: Base Movement Rates, printed p. 157`
- source_role: `core-rule-source`
- activation_requirement: `core-default unless a more specific race/creature/source treatment governs`
- verification_status: `verified`
- source_text_required: `false` for listed base rates

structured_data:
- human: `12`
- dwarf: `6`
- elf: `12`
- gnome: `6`
- half-elf: `12`
- halfling: `6`

## Entity: Cross-country movement

- entity_id: `adnd2e.rule.movement.cross-country`
- entity_type: `procedure`
- assertion_id: `adnd2e.phb.cross-country-movement.v1`
- source_id: `adnd2e.document.phb-deluxe`
- locator: `Chapter 14: Time and Movement -> Cross-Country Movement, printed p. 157`
- source_role: `core-rule-source`
- verification_status: `verified`
- source_text_required: `true` for detailed force-march continuation/exhaustion consequences beyond the fields below

structured_data:
- normal_march_day_hours: `10`
- normal_clear_terrain_miles_per_day: `2 x movement rate`
- example_unencumbered_movement_12: `24 miles/day`
- force_march_miles_per_day: `2.5 x movement rate`
- force_march_daily_check: `Constitution check at end of each day`

## Entity: Extreme terrain effects on round movement

- entity_id: `adnd2e.rule.movement.terrain-round`
- entity_type: `rule`
- assertion_id: `adnd2e.dmg.table73.terrain-effects.v1`
- source_id: `adnd2e.document.dmg-deluxe`
- locator: `Chapter 14: Time and Movement -> Table 73: Terrain Effects on Movement, printed p. 167`
- source_role: `core-dm-rule-source`
- activation_requirement: `DMG terrain-effects rule; source labels this section optional`
- verification_status: `verified`
- source_text_required: `true` when choosing unsafe faster movement, direction-loss, or interaction of multiple conditions`

structured_data:
- darkness: `movement reduced by 1/3; faster movement possible`
- heavy_brush_or_forest: `movement reduced by 2/3`
- ice_or_slippery_footing: `movement reduced by 1/3; faster movement possible`
- rugged_or_rocky_ground: `movement reduced by 1/2`
- soft_sand_or_knee_deep_snow: `movement reduced by 1/3`
- waist_deep_water_or_snow: `movement reduced by 1/2`
- shoulder_deep_water_or_snow: `movement reduced by 2/3`
- multiple_conditions_same_round: `use worst adjustment`

## Runtime use

For ordinary travel/movement routing:
`current creature/race movement -> encumbrance/current modifiers -> base movement assertion -> cross-country rule if overland -> DMG terrain/overland source assertion as implicated -> exact source only for unresolved exceptions`

For current Wren, his canonical movement state remains authoritative; this source shard merely supplies reusable published derivations.
