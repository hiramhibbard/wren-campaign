# Compiled Monster Object — Stirge

Status: verified structured assertion from uploaded AD&D 2e Monstrous Manual. This is published-source knowledge, not a statement that stirges exist in Wren's current region.

## Entity: Stirge

- entity_id: `adnd2e.monster.stirge`
- entity_type: `monster`
- canonical_name: `Stirge`
- assertion_id: `adnd2e.mm.stirge.v1`
- source_id: `adnd2e.document.monstrous-manual-deluxe`
- locator: `Stirge entry, printed pp. 332-333`
- source_role: `generic-core-monster-source`
- activation_requirement: `generic core creature treatment unless a more specific active setting/adventure source governs`
- verification_status: `verified`
- source_text_required: `true` for unusual removal/armor-protection/adjudication and variant use`

structured_data:
- climate_terrain: `Forests or subterranean`
- frequency: `Uncommon`
- organization: `Clusters`
- activity_cycle: `Night`
- diet: `Blood`
- intelligence: `Animal (1)`
- treasure: `D`
- alignment: `Nil`
- number_appearing: `3-30`
- armor_class: `8`
- movement: `3, Fl 18 (C)`
- hit_dice: `1+1`
- thac0_printed: `17`
- attacks: `1`
- damage: `1-3`
- special_attacks: `Blood drain`
- special_defenses: `Nil`
- magic_resistance: `Nil`
- size: `S (2-foot wingspan)`
- morale: `Average (8)`
- xp_value: `175`

combat:
- attack_effective_hd: `attacks as 4-Hit-Die creature due to instinctive weak-point targeting`
- initial_hit: `proboscis inflicts 1-3 hp`
- attached_drain: `1d4 hp of blood each round after attachment`
- satiation: `after draining 12 total hp of blood, becomes bloated and flies away to digest`
- removal: `strong grip; normally must be killed to remove`
- missed_attack_on_attached_stirge: `make another attack roll against victim AC to determine whether attacker hits victim instead`

habitat_society:
- nesting: `attics, dungeons, and copses of trees`
- sleep_posture: `hang upside down`
- civilization_effect: `colonies prey on low-level humans, animals, and children and are treated as a serious local menace`
- captive_breeding: `possible with constant blood supply`

ecology:
- senses: `acute smell; dark vision stated in source; detects heat sources within 200 ft`
- thick_hide_interaction: `natural AC 3 or better usually prevents blood-draining penetration`
- feeding_rest: `after gorging, sleeps 1 day plus 1 day per 2 hp blood drained, maximum 7 days`
- sleeping_surprise: `silent attackers can impose -2 to stirge surprise roll during post-feeding sleep`
- preferred_prey: `large mammals broadly; some species prefer humans`
- territory: `colony territory about one mile in diameter; colonies move after draining local prey supply`
- field_sign: `mysteriously drained/dead animals can indicate a colony`

variants:
- jungle_stirge:
  - status: `reported/variant in core entry`
  - hit_dice: `2+2`
  - attack_effective_hd: `8`
  - additional_trait: `reported paralyzing poison in snout`
  - source_text_required: `true; source itself presents some details as rumor/unconfirmed`

## Relationships

- `adnd2e.monster.stirge --GOVERNED_BY_GENERIC_ASSERTION--> adnd2e.mm.stirge.v1`
- `adnd2e.mm.stirge.v1 --COLLECTED_IN--> adnd2e.document.monstrous-manual-deluxe`
- `adnd2e.monster.stirge.jungle --VARIANT_OF--> adnd2e.monster.stirge`

## Runtime routing

`stirge reference -> active setting/adventure scope -> more-specific source if any -> this generic MM assertion -> exact entry if an attached-stirge, armor-gap, colony-tracking, or jungle-variant edge case matters`

Do not infer a stirge population, colony, encounter, or Home Coast habitat merely because this source object exists.