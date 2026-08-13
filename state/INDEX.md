# Wren Campaign State Index

Schema version: 1
Snapshot generation: 1

This index routes canonical campaign state. Absence from the current working set does not mean absence from the campaign.

## Character
- Wren identity, ability scores, combat values, saves, proficiencies, personality, family, and player-facing witch/mentor state: `state/character/wren.md`
- Inventory, funds, encumbrance, inherited boat, boat-stored gear: `state/character/inventory.md`
- Spellbook, known/memorized magic, unresolved magic-rule items: `state/character/magic.md`

## Campaign context
- Campaign framing, low-level/earned-growth constraints, player discovery preference, and setting status: `state/campaign/context.md`

## Chronology
- Current resume position and played chronology: `state/chronology/current.md`

## NPCs
- Aldrin Hale: `state/npcs/aldrin-hale.md`
- Edric Hale: `state/npcs/edric-hale.md`
- Mara, Elia, Wren's deceased father, and player-facing witch/mentor facts: `state/character/wren.md`
- DM-only witch/mentor truth: `state/dm/campaign.md`

`state/npcs/index.md` is not required for canonical loading in snapshot generation 1; use the routes in this file until that secondary index is refreshed.

## Threads
- Active player-facing threads: `state/threads/active.md`

## Locations
- Location routing index: `state/locations/index.md`
- Current harbor/boarding-house state: `state/locations/harbor/current.md`

## Rulings
- Campaign rulings and unresolved rule checks: `state/rulings/adnd2e-campaign-rulings.md`
- Dice protocol: `state/rulings/dice-protocol.md`

## DM-only
- Hidden established truths, prepared possibilities, outside forces, off-screen motion, and foreshadowing commitments: `state/dm/campaign.md`

## Protocol
- Full operating protocol: `CAMPAIGN_BOOTSTRAP.md`
- State architecture: `STATE_SCHEMA.md`
- Root manifest/resume/baseline: `Wren_Campaign_Ledger.md`

Repository search is the fallback for fuzzy natural-language references when an explicit route is not sufficient.
