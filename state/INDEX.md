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
- NPC routing and promotion guidance: `state/npcs/index.md`
- Aldrin Hale: `state/npcs/aldrin-hale.md`
- Edric Hale: `state/npcs/edric-hale.md`
- Mara, Elia, Wren's deceased father, and player-facing witch/mentor facts: `state/character/wren.md`
- DM-only witch/mentor truth: `state/dm/campaign.md`

## Threads and clues
- Active player-facing threads: `state/threads/active.md`
- Active player-facing clues, rumors, and inference boundaries: `state/clues/active.md`

## Locations
- Location routing index: `state/locations/index.md`
- Current harbor/boarding-house state: `state/locations/harbor/current.md`

## Rulings / DM procedures
- Campaign rulings and unresolved rule checks: `state/rulings/adnd2e-campaign-rulings.md`
- Dice protocol: `state/rulings/dice-protocol.md`
- DM procedure triggers for time, encounters, reaction/morale, NPC/henchmen, travel, downtime, clues, factions, significant items, published adventures, and checkpoint routing: `state/rulings/dm-procedure-triggers.md`
- Context-first NPC generation, alignment, mechanical coherence, personality, cognition, and portrayal protocol: `state/rulings/npc-generation-and-portrayal.md`

## DM-only
- Hidden established truths, prepared possibilities, outside forces, off-screen motion, and foreshadowing commitments: `state/dm/campaign.md`

## Long-term state scaffolds
- Reusable NPC, henchman, world-clock, encounter, faction, clue, travel, downtime, item, source-registry, entity-promotion, and incremental-maintenance templates: `STATE_TEMPLATES.md`

These templates are operational schemas rather than live facts. Instantiate records only when play makes them relevant.

## Engineering
- Architecture decisions, operational status, known limitations, validation plan, and future-work roadmap: `CAMPAIGN_ENGINEERING.md`
- Load that file when Hiram asks to continue infrastructure, persistence, Voice workflow, memory, DM behavior, maintenance, or related system design.

## Protocol
- Full operating protocol: `CAMPAIGN_BOOTSTRAP.md`
- State architecture: `STATE_SCHEMA.md`
- State templates/scaffolds: `STATE_TEMPLATES.md`
- Engineering roadmap/design log: `CAMPAIGN_ENGINEERING.md`
- Root manifest/resume/baseline: `Wren_Campaign_Ledger.md`

Repository search is the fallback for fuzzy natural-language references when an explicit route is not sufficient.