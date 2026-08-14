# Wren Ordinary Game Procedure Coverage Audit

Status: infrastructure audit; no campaign facts changed.

Purpose: verify that ordinary AD&D 2e play has an explicit runtime procedure or intentional exact-source fallback for the situations a player/DM is likely to encounter. This audit tests **procedure coverage**, not whether every published table has already been compiled into the source-knowledge fast path.

## Rating scale

- **COVERED — FAST:** explicit trigger/routing exists and commonly needed mechanics are already compiled/cached.
- **COVERED — SOURCE FALLBACK:** explicit trigger/routing exists; exact mechanics may require targeted source retrieval.
- **PARTIAL:** neighboring procedures exist but the trigger/routing was not explicit enough before this audit.
- **MISSING:** no reliable procedure/routing found.
- **OPTIONAL / SCOPE-GATED:** procedure exists only if an optional/supplement/setting subsystem is canonically active.

## Audit basis

Canonical Wren procedure/policy files inspected:
- `state/rulings/dm-procedure-triggers.md`
- `state/rulings/dice-protocol.md`
- `state/rulings/perception-and-evidence.md`
- `state/rulings/adnd2e-campaign-rulings.md`
- `DM_CRAFT_POLICY.md`
- `SITE_RUNTIME_POLICY.md`
- `REGIONAL_RUNTIME_POLICY.md`
- `state/rulings/regional-runtime-triggers.md`
- `state/rulings/monster-runtime-triggers.md`
- `state/rulings/creature-ecology-and-behavior.md`
- source-routing/index architecture under `state/INDEX.md` and `rules/source-knowledge/INDEX.md`

Published-source basis checked against uploaded AD&D 2e PHB/DMG. Important PHB principle confirmed: simple jobs can succeed automatically; more complicated tasks may use a DM-assigned percentage, saving throw, or Ability check. Under nonweapon proficiencies, simple uses generally do not require a check while difficult/failure-prone uses do, with the individual proficiency entry governing details.

## Audit result summary

### Result before remediation
- Strong architecture existed for time, resources, encounters, reaction, morale, travel, NPCs, clues, factions, downtime, XP/advancement, active effects, sites, creatures, and persistence.
- Several ordinary-table domains were **functionally supported but not explicit enough as top-level triggers**: general action adjudication/when to roll, combat-entry trigger, tactical movement, light/visibility, social persuasion/negotiation, doors/barriers, traps/hazards, environmental danger, saving-throw trigger discipline.
- No catastrophic gameplay hole was found: these domains could fall back to exact source retrieval, but routing ambiguity could cause inconsistent calls or too many/too few rolls.

### Remediation performed
Created `state/rulings/core-gameplay-procedure-triggers.md` to make these ordinary-table triggers explicit without inventing new mechanics or silently activating optional rules.

### Result after remediation
**No ordinary high-frequency gameplay domain is currently rated MISSING.**

Most common play is now either `COVERED — FAST` or `COVERED — SOURCE FALLBACK`. Remaining work is primarily source compilation/performance and a few detailed edge-case procedure audits, not absence of a usable table-running framework.

## Detailed coverage matrix

### A. General adjudication / dice

| Domain | Status | Runtime route / note |
|---|---|---|
| When to roll at all | COVERED — FAST | `core-gameplay-procedure-triggers.md`: certainty -> routine competence -> specific procedure -> proficiency -> generic adjudication only if needed -> no-consequence no-roll. |
| Routine automatic success | COVERED — FAST | Explicitly grounded in PHB Chapter 5 principle; reinforced by DM craft/playability policy. |
| Ability checks | COVERED — SOURCE FALLBACK | Used only when no more specific procedure governs or source calls for one; exact modifiers/edge cases retrieved as needed. |
| Nonweapon proficiency checks | COVERED — SOURCE FALLBACK | PHB says simple uses often automatic, difficult/failure-prone uses check; individual proficiency entry governs. |
| Secret checks | COVERED — FAST | `dice-protocol.md` + `perception-and-evidence.md`. |
| Player-facing vs DM-facing roll ownership | COVERED — FAST | Hiram rolls player-facing dice; hidden DM rolls generated secretly. |
| Retry/repeated attempt discipline | COVERED — SOURCE FALLBACK | New explicit gate; exact source retry rules win. |
| No fudging | COVERED — FAST | Dice protocol + DM craft. |

### B. Encounter opening / combat

| Domain | Status | Runtime route / note |
|---|---|---|
| When an encounter becomes combat | COVERED — FAST | New combat trigger: hostile action/meaningful contested sequence, not merely danger nearby. |
| Encounter occurrence/check timing | COVERED — FAST | Base encounter trigger + DMG wilderness projection + site/regional runtime. |
| Encounter distance | COVERED — FAST | Compiled core encounter-distance object. |
| Surprise | COVERED — FAST | Compiled surprise modifiers + encounter procedure. |
| Reaction before combat | COVERED — FAST | Reaction trigger; motives/orders can make roll unnecessary. |
| Initiative | COVERED — FAST | Group initiative + optional action-specific initiative compiled; optional variant not autoactivated. |
| Attack rolls / THAC0 | COVERED — FAST | Character THAC0 cache + compiled attack modifiers; exact source for unusual cases. |
| Melee positioning/modifiers | COVERED — SOURCE FALLBACK | Standard modifiers compiled; unusual reach/facing/position source fallback. |
| Missile ranges / ROF | COVERED — FAST | Full PHB Table 45 fast path. |
| Firing into melee | COVERED — FAST | Compiled weighted-target procedure. |
| Cover/concealment | COVERED — FAST | Compiled Table 59. |
| Multiple attacks | COVERED — FAST | Compiled sequencing. |
| Spellcasting timing/interruption | COVERED — SOURCE FALLBACK | Casting-time lifecycle compiled; exact source for interruption/special cases. |
| Saves / MR / special defenses | COVERED — SOURCE FALLBACK | Complete class saves compiled; trigger discipline explicit; exact effect/monster source when needed. |
| Morale / withdrawal | COVERED — FAST | Morale trigger + 2e morale routing. |
| Injury / natural healing | COVERED — FAST | Core healing/death fast path. |
| Death / resurrection / massive damage | COVERED — FAST | Core fast path; optional death's-door remains scope-gated. |

### C. Movement / position / travel

| Domain | Status | Runtime route / note |
|---|---|---|
| Base movement | COVERED — FAST | PHB Table 64 compiled. |
| Encumbrance effects | COVERED — FAST | Breakpoint trigger + Wren cache + source fallback on crossing. |
| Tactical movement | COVERED — SOURCE FALLBACK | Explicit new trigger; exact special movement retrieved as needed. |
| Running | COVERED — SOURCE FALLBACK | PHB running Strength/Constitution procedure identifiable; not all fields compiled yet. |
| Charging | COVERED — SOURCE FALLBACK | Combat/tactical movement trigger identifies core combat source. |
| Climbing | COVERED — FAST | Success/modifier/rate tables compiled. |
| Swimming | COVERED — SOURCE FALLBACK | Explicit movement/environment route; exact PHB rule when consequential. |
| Jumping | COVERED — SOURCE FALLBACK | Exact source/proficiency route. |
| Mounted movement/combat | COVERED — SOURCE FALLBACK | Tactical movement + active source route; detailed fast path not yet compiled. |
| Overland march | COVERED — FAST | Cross-country/forced-march compiled. |
| Terrain movement | COVERED — FAST | DMG extreme-terrain projection + source fallback. |
| Navigation/getting lost | COVERED — SOURCE FALLBACK | Travel trigger explicitly tracks it; exact source when applicable. |
| Coastal/river/sea travel | COVERED — SOURCE FALLBACK | Travel + ship weather/runtime; vessel-specific mechanics exact-source. |
| Pursuit | COVERED — SOURCE FALLBACK | Combat/site/travel route; detailed source-specific pursuit not fully compiled. |

### D. Light / perception / exploration

| Domain | Status | Runtime route / note |
|---|---|---|
| Common light-source radius/burn time | COVERED — FAST | PHB Table 63 compiled. |
| Darkness / normal vision | COVERED — FAST | Light trigger + compiled normal-vision boundary. |
| Weather visibility | COVERED — FAST | PHB Table 62 compiled. |
| Infravision/special senses | COVERED — SOURCE FALLBACK | Default cap compiled; exact operating model/source for edge cases. |
| Carried light reveals bearer | COVERED — FAST | Explicit compiled tactical note. |
| Plainly visible information | COVERED — FAST | Perception/evidence: give it automatically. |
| Listening | COVERED — SOURCE FALLBACK | Explicit perception trigger; exact core/class/site procedure retrieved. |
| Searching | COVERED — SOURCE FALLBACK | Explicit perception trigger; exact procedure retrieved. |
| Secret/concealed doors | COVERED — SOURCE FALLBACK | Explicit perception/door route; race/class/source specifics retrieved. |
| Find/remove traps | COVERED — SOURCE FALLBACK | Trap trigger + thief/source procedure. |
| Noise propagation / alarms | COVERED — SOURCE FALLBACK | Site runtime handles causal propagation; exact distance/sense rules as needed. |
| Exploration time cadence | COVERED — SOURCE FALLBACK | Site runtime tracks meaningful elapsed time/check thresholds; detailed source cadence retrieved. |
| Pixel-hunting avoidance | COVERED — FAST | DM craft + perception procedure. |

### E. Social interaction

| Domain | Status | Runtime route / note |
|---|---|---|
| Initial NPC disposition | COVERED — FAST | Established motives/state first, reaction only if uncertain. |
| Reaction rolls | COVERED — FAST | Complete DMG reaction matrix compiled. |
| Charisma/reaction adjustment | COVERED — SOURCE FALLBACK | Routed through reaction/social procedure; exact character/source modifier when needed. |
| Persuasion | COVERED — SOURCE FALLBACK | No universal campaign persuasion skill. Resolve motives + roleplay + reaction + possessed active proficiency/source if any. |
| Bargaining/haggling | COVERED — SOURCE FALLBACK | Economy/social route; optional setting/supplement Bargain only if active and possessed. |
| Deception/bluff | COVERED — SOURCE FALLBACK | Knowledge/deception + social route; specific active proficiency/source if applicable. |
| Intimidation | COVERED — SOURCE FALLBACK | Motives/morale/reaction/source-specific ability; no invented universal check. |
| Hiring services | COVERED — SOURCE FALLBACK | Local availability/motive + service/economy source. |
| Hirelings/henchmen | COVERED — SOURCE FALLBACK | NPC/henchman procedure includes loyalty, compensation, control, advancement. |
| NPC spellcasting services | COVERED — SOURCE FALLBACK | DMG service availability/cost/motive route. |
| Loyalty | COVERED — SOURCE FALLBACK | Morale/loyalty procedure; secret where appropriate. |

### F. Hazards / survival

| Domain | Status | Runtime route / note |
|---|---|---|
| Falling | COVERED — SOURCE FALLBACK | Environmental trigger; exact damage/procedure source. |
| Drowning/suffocation | COVERED — SOURCE FALLBACK | Environmental + resource/depletion trigger. |
| Fire/heat/cold | COVERED — SOURCE FALLBACK | Environmental + active effects. |
| Starvation/dehydration | COVERED — SOURCE FALLBACK | Resource/depletion + readiness + environment. |
| Poison | COVERED — SOURCE FALLBACK | Save/effect lifecycle + exact poison source. |
| Disease | COVERED — SOURCE FALLBACK | Active effect/healing/environment + exact disease source. |
| Weather/exposure | COVERED — SOURCE FALLBACK | Regional runtime/weather + exact source as needed. |
| Unstable terrain/collapse | COVERED — SOURCE FALLBACK | Site/environment + source-specific adjudication. |

### G. Magic / character resources

| Domain | Status | Runtime route / note |
|---|---|---|
| Memorization / spell slots | COVERED — FAST | Character magic state + wizard slots compiled. |
| Spell casting fields | COVERED — FAST | Common spell-entry semantics compiled. |
| Spell duration/termination | COVERED — FAST | Origin-agnostic active-effect lifecycle. |
| Components / resource consumption | COVERED — SOURCE FALLBACK | Exact spell/item source + depletion procedure. |
| Spell saves / MR | COVERED — SOURCE FALLBACK | Saves compiled; exact spell/monster interaction source. |
| Learning spells | COVERED — SOURCE FALLBACK | Downtime/project + exact source. |
| Spell research | COVERED — SOURCE FALLBACK | Downtime/project + exact source. |
| Item identification | COVERED — SOURCE FALLBACK | Significant-item + magic/source route. |
| Charges/uses | COVERED — FAST | Resource/effect lifecycle supports depletion triggers. |
| Optional magic systems | OPTIONAL / SCOPE-GATED | Tome/PHBR/etc. never activated by availability alone. |

### H. Campaign management / world simulation

| Domain | Status | Runtime route / note |
|---|---|---|
| Time advancement | COVERED — FAST | Due-event frontier and explicit time trigger. |
| Rest/healing | COVERED — FAST | Healing fast path + active effects. |
| Resource tracking | COVERED — FAST | Generic depletion trigger. |
| Readiness before travel/project | COVERED — FAST | Declared-action readiness. |
| Downtime/projects | COVERED — SOURCE FALLBACK | Durable project trigger. |
| NPC generation | COVERED — FAST | Context-first NPC procedure. |
| NPC portrayal | COVERED — FAST | Cognitive/knowledge/personality grounding. |
| Factions/off-screen plans | COVERED — FAST | Clocks/world runtime. |
| Clues/rumors/inference | COVERED — FAST | Epistemic categories preserved. |
| Creature ecology/behavior | COVERED — FAST | Creature embodiment + monster runtime/source route. |
| Treasure provenance | COVERED — FAST | DM craft/significant item; exact source for treasure tables/items. |
| Persistent dungeons/sites | COVERED — FAST | Site runtime; source baseline -> campaign consequence overlay. |
| Random encounter integrity | COVERED — FAST | Correct trigger frequency; no fudge/discard for pacing. |
| Published adventures | COVERED — FAST | Opportunity + persistent-source-site procedures. |
| XP evaluation | COVERED — FAST | Automatic at meaningful resolution/session end. |
| Level advancement | COVERED — FAST | Automatic trigger on verified XP threshold. |
| Save/checkpoint | COVERED — FAST | Hardened append-only persistence/readback. |

## Specific findings worth keeping visible

1. **No universal Persuasion skill.** Core social resolution must not be collapsed into a generic Charisma/Persuasion check. Optional supplement proficiencies remain scope-gated.
2. **No universal "roll for uncertainty" rule.** Use specific AD&D procedures first. Simple tasks can be automatic; difficult proficiency uses may require a check; the DM can assign an ability check/percentage/save when the rules leave genuine consequential uncertainty unresolved.
3. **Combat begins on contested sequencing, not atmosphere.** Do not roll initiative merely because a potentially dangerous creature is present.
4. **Light is both perception and exposure.** Track what Wren can see and whether his own light makes him visible to others.
5. **Movement is only granular when position/time matters.** Avoid tactical bookkeeping for incidental movement; enforce exact movement when distance, pursuit, range, terrain, or exhaustion matters.
6. **Hidden checks stay hidden.** Listening/search/detection procedures must not leak failure by the act of rolling or narration.
7. **Optional rules are not silently active.** Compilation/source availability never turns on optional initiative, death's-door, specialist proficiencies, setting subsystems, or similar material.

## Remaining procedure-hardening backlog

These are not missing domains; they are candidates for stronger fast paths or exact-procedure projections:

- detailed core running/charging/tactical movement;
- swimming/jumping/falling/drowning/suffocation;
- exact doors/listening/search/secret-door procedure variants;
- thief lock/trap/search skill operational details;
- poison/disease/exposure tables;
- mounted combat and pursuit;
- hiring/service/economy tables;
- spell learning/research/identification procedures;
- detailed navigation/getting-lost rules;
- common saving-throw situational modifiers;
- broader equipment/weapon tables.

These should feed the source-compilation queue, but normal play does not need to wait for them because each has an explicit targeted source-fallback route.

## Regression scenarios

The following should remain true after future architecture changes:

1. Wren walks across an ordinary room with no meaningful positional stakes -> no movement roll and no tactical measurement.
2. Wren tries a simple task covered by ordinary competence -> no gratuitous check.
3. Wren attempts a difficult use of a known NWP -> use its exact proficiency check procedure.
4. Wren attempts an uncertain task with no specific rule -> DM selects an appropriate adjudication method rather than auto-defaulting to a generic skill roll.
5. A potentially hostile NPC speaks rather than attacks -> do not roll initiative solely because danger exists.
6. NPC motives already dictate refusal -> a reaction/Persuasion roll does not overwrite that truth.
7. Initial disposition is genuinely uncertain -> reaction procedure may apply.
8. Wren carries a lantern in darkness -> apply both illumination and visibility-to-others consequences.
9. Wren listens at a door with a hidden failure state -> use the governing hidden procedure without exposing the roll outcome.
10. Wren runs long enough for exhaustion checks -> call for governing Strength/Constitution checks automatically.
11. Wren's declared journey will outlast known supplies -> readiness warning before commitment, then normal depletion if he proceeds.
12. Wren walks into a keyed trap -> use the keyed/source trigger and applicable save/detection/disarm procedure, not a generic trap roll.
13. Wren casts a duration spell -> register all relevant termination triggers, not just elapsed time.
14. An encounter roll produces an inconvenient result -> accept the legitimate result; do not fudge for pacing.
15. A site is revisited -> apply elapsed-world/site consequences rather than resetting the key.
16. An optional supplement social proficiency exists in the library but is not active/possessed -> do not use it.
17. A player-facing check is required -> Hiram rolls physical dice.
18. A secret detection/reaction/world roll is required -> DM generates it secretly and fairly.

## Audit conclusion

The Wren campaign now has an explicit, coherent procedure/routing framework for essentially every ordinary game-table category likely to arise in regular AD&D 2e play. The remaining work is predominantly **mechanical fast-path compilation and edge-case specificity**, not foundational procedure absence.

Re-run this audit after major rules architecture changes, optional-system activation, or evidence from actual play that a recurring category is being adjudicated inconsistently.