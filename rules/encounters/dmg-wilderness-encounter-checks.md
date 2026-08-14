# Structured Rules Projection: DMG Wilderness Encounter Checks

projection_id: `adnd2e.dmg.encounters.wilderness-checks.v1`
status: verified-source-derived
system: AD&D 2nd Edition
source: Dungeon Master Guide (Deluxe/2013 reprint of 1995 2e text)
source_locator: Chapter 11, Encounter Checks, Table 56 — Frequency & Chance of Wilderness Encounters, printed page 138
source_file: uploaded `DD2_DMG_Deluxe.pdf`
activation: core rules; governing unless an explicitly active campaign/source rule supersedes the relevant scope

## Procedure summary

For random wilderness encounters:
- make checks only at the time-of-day slots marked for the applicable terrain;
- roll 1d10 when a check is due;
- an encounter occurs on the listed chance or less;
- Table 56 assumes unpopulated wilderness;
- if a region is patrolled or sparsely settled, DMG permits +1 to encounter chance; heavily populated permits +2, **but only if encounter tables have been specially prepared to reflect settled-land encounters**;
- noise, alarms, or other justified circumstances may modify chance or trigger an immediate check;
- planned/keyed encounters use their own triggers and do not require a random check.

## Table 56 normalized projection

Time slots:
- A = 7–10 a.m.
- B = 11 a.m.–2 p.m.
- C = 3–6 p.m.
- D = 7–10 p.m.
- E = 11 p.m.–2 a.m.
- F = 3–6 a.m.

| terrain | encounter_on_1d10 | check_slots |
|---|---:|---|
| Plain | 1 | A, C, E |
| Scrub/brush | 1 | A, C, D, F |
| Forest | 2 | A, B, C, D, E, F |
| Desert | 1 | A, D, F |
| Hills | 2 | B, D, F |
| Mountains | 3 | A, D, E |
| Swamp | 4 | A, B, C, D, E, F |
| Jungle | 3 | A, B, C, D, E |
| Ocean | 1 | B, E |
| Arctic | 1 | C, D |

## Runtime routing

Use this projection only after the current regional runtime profile identifies a qualifying wilderness terrain/travel segment or a comparable terrain classification.

A settlement interior, ordinary village conversation, or other non-wilderness scene does not activate Table 56 merely because time passes.

If terrain is mixed, uncertain, or not represented, determine the closest applicable classification from established geography or retrieve the exact source if interpretation is consequential.

Before applying population-density modifiers, ensure the local encounter content is actually prepared to represent settled/patrolled traffic. Increasing encounter chance with an all-monster wilderness table would misapply the DMG instruction.

## Encounter content

This projection determines **when/check chance**, not **what is encountered**.

Encounter content comes from:
- an explicitly active published local encounter table;
- a campaign regional/local encounter table;
- current world actors/ecology/dynamic overrides under `REGIONAL_RUNTIME_POLICY.md`.

Do not infer monster presence from Table 56.

## Source-text-required conditions

Retrieve the exact DMG encounter section when consequential interpretation is needed for:
- unusual/nonlisted terrain;
- dungeon encounter frequency/chance;
- encounter size;
- surprise/modifiers;
- encounter distance;
- reaction;
- special handling of excessive noise/alarms;
- ambiguity about whether a check/result should be used under the governing campaign procedure.

If this projection conflicts with the uploaded DMG, the uploaded source wins and this projection must be corrected.