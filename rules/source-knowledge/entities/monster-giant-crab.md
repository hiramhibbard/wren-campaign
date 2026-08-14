# Compiled Monster Object — Giant Crab

Status: verified structured assertion from uploaded AD&D 2e Monstrous Manual. This is published-source knowledge, not a statement that giant crabs inhabit Wren's Home Coast.

## Entity: Giant Crab

- entity_id: `adnd2e.monster.giant-crab`
- entity_type: `monster`
- canonical_name: `Giant Crab`
- assertion_id: `adnd2e.mm.giant-crab.v1`
- source_id: `adnd2e.document.monstrous-manual-deluxe`
- locator: `Crustacean, Giant -> Giant Crab, printed p. 50`
- source_role: `generic-core-monster-source`
- activation_requirement: `generic core creature treatment unless a more specific active setting/adventure source governs`
- verification_status: `verified`
- source_text_required: `true` for unusual carrying/grapple geometry, lair use, or source-specific variants`

structured_data:
- climate_terrain: `Any seashore`
- frequency: `Rare`
- organization: `Nil`
- activity_cycle: `Any`
- diet: `Omnivore`
- intelligence: `Non-intelligent (0)`
- treasure: `Nil`
- alignment: `Neutral`
- number_appearing: `2-12`
- armor_class: `3`
- movement: `9`
- hit_dice: `3`
- thac0_printed: `17`
- attacks: `2`
- damage: `2-8 / 2-8`
- special_attacks: `Nil`
- special_defenses: `Surprise`
- magic_resistance: `Nil`
- size: `L (8-15 feet)`
- morale: `Elite (13)`
- xp_value: `65`

combat:
- ambush: `prefers to sneak up on prey; opponents suffer -3 penalty to surprise roll`
- pincers: `each successful pincer attack inflicts 2d4 damage`
- feeding_behavior: `once holding edible prey, normally stops to eat unless attacked`
- withdrawal_with_prey: `if its meal is contested, may scuttle away carrying the prize toward a den`

habitat_society:
- habitat: `shoreline; beaches and adjacent water`
- respiration: `can breathe both air and water`
- foraging: `searches beaches for food and enters water for fish/aquatic life`
- carrion: `commonly feeds on large dead fish and other shoreline carrion`
- locomotion: `functions effectively on land and in water`
- concealment: `may burrow into sand during the day and emerge around dusk/dawn, though may hunt at any time`
- behavior: `instinct-driven and concerned primarily with survival`
- reproduction: `mates in autumn; females bury eggs in sand; eggs hatch in spring; juvenile mortality is high`

ecology:
- ecological_role: `scavenger that removes large carrion from seashores`
- diet_flexibility: `broad opportunistic eater`

## Relationships

- `adnd2e.monster.giant-crab --GOVERNED_BY_GENERIC_ASSERTION--> adnd2e.mm.giant-crab.v1`
- `adnd2e.mm.giant-crab.v1 --COLLECTED_IN--> adnd2e.document.monstrous-manual-deluxe`
- `adnd2e.monster.giant-crab --FAMILY--> adnd2e.monster-family.giant-crustacean`

## Runtime routing

`giant crab reference -> active setting/adventure scope -> more-specific assertion if any -> this generic MM assertion -> exact source for edge cases`

Do not infer a Home Coast population, encounter, or established local ecology merely because the generic source object exists.