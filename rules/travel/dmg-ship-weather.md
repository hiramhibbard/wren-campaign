# Structured Rules Projection: DMG Ship Weather

projection_id: `adnd2e.dmg.travel.ship-weather.v1`
status: verified-source-derived
system: AD&D 2nd Edition
source: Dungeon Master Guide (Deluxe/2013 reprint of 1995 2e text)
source_locator: Chapter 14, Weather and Ship Travel; Tables 78–79, printed pages 170–171
source_file: uploaded `DD2_DMG_Deluxe.pdf`
activation: core rules; governing for applicable ship/sea weather unless an explicitly active campaign/source rule supersedes the relevant scope

## Daily weather procedure

The DMG treats weather as generally consistent within a single day for ship travel.

When sea/ship weather is consequential, the DM may choose appropriate conditions or determine them randomly. For random determination, roll 2d6 on Table 79 using the current season.

Do not invent the current season merely to make this table usable; derive it from canonical chronology once established.

## Table 79 normalized projection

| 2d6 | Spring/Fall | Summer | Winter |
|---:|---|---|---|
| 2 | Becalmed | Becalmed | Becalmed |
| 3 | Becalmed | Becalmed | Light breeze |
| 4 | Light breeze | Becalmed | Light breeze |
| 5 | Favorable | Light breeze | Favorable |
| 6 | Favorable | Light breeze | Strong winds |
| 7 | Strong winds | Favorable | Strong winds |
| 8 | Storm | Favorable | Storm |
| 9 | Storm | Strong winds | Storm |
| 10 | Gale | Storm | Gale |
| 11 | Gale | Gale | Gale |
| 12 | Hurricane* | Hurricane* | Hurricane* |

`*` Hurricane occurs only if the previous day's weather was Gale; otherwise treat the result as Gale.

## Table 78 movement effects

| weather condition | sailing modifier | rowing modifier | special |
|---|---:|---:|---|
| Adverse | ×1/2 | ×1 | — |
| Becalmed | NA | ×1 | sailing vessel cannot rely on sail movement |
| Favorable (average) | ×2 | ×1 | — |
| Favorable (strong) | ×3 | ×1 | seaworthiness check required |
| Gale | ×4 | ×1/2 | seaworthiness check required |
| Light breeze | ×1 | ×1 | — |
| Storm | ×3 | ×1/2 | seaworthiness check required |
| Hurricane | ×5 | ×1/2 | seaworthiness check with -45% penalty |

Adverse-wind determination and off-course effects should use the exact DMG source text when consequential; do not silently flatten them into a generic speed modifier.

## Runtime routing

Use this projection when:
- Wren or relevant actors undertake meaningful sea/ship travel;
- wind/weather affects sailing movement or safety;
- a continuing sea-weather state must be preserved across the day;
- a weather result can affect navigation, encounter context, visibility, or world events.

Do not roll ship-weather daily during ordinary inland/village scenes merely because the table exists.

For a small craft whose exact classification/mechanical handling is uncertain, retrieve the governing boat/water-movement source before applying ship-specific seaworthiness or sailing assumptions.

## Climate relationship

Table 79 is a core ship-travel weather abstraction, not a complete regional climate generator. Campaign climate/season constrains ordinary descriptive weather under `REGIONAL_RUNTIME_POLICY.md`.

If a more specific explicitly active setting/adventure/source weather rule applies, use the source-activation/precedence rules in `RULES_PROJECTION_POLICY.md` rather than allowing an uploaded supplement to supersede this projection automatically.

## Source-text-required conditions

Retrieve the exact DMG section when consequential for:
- seaworthiness checks and bonuses;
- adverse wind determination;
- off-course consequences;
- vessel type/base movement/emergency movement;
- rowing/sailing distinctions;
- unusual craft;
- aerial-weather procedures;
- any ambiguity or interaction not represented here.

If this projection conflicts with the uploaded DMG, the uploaded source wins and this projection must be corrected.