# Wren Campaign Ledger

**Status:** Canonical campaign-state record  
**Canonical backend:** GitHub  
**Repository:** `hiramhibbard/wren-campaign`  
**Canonical path:** `Wren_Campaign_Ledger.md` on `main`  
**Rules baseline:** AD&D 2nd Edition  
**Migrated to GitHub:** 2026-08-13

This file is the live authoritative campaign-state record. Uploaded rulebooks and setting sources remain authoritative for published rules, setting canon, adventures, maps, handouts, tables, and spell/rules text. The pre-GitHub Library ledger is retained only as a recovery/history source; provenance is recorded in `legacy/README.md`.

## Mandatory DM Operating Protocol

1. **LOAD before play.** At the start of a play session, after a new chat/branch, or whenever exact established state matters, fetch this exact GitHub file from `hiramhibbard/wren-campaign` on `main`. Do not use model memory, Project history, Saved Memory, a similarly named file, or the old Library ledger as the authority.
2. **Capture the current blob SHA.** Every load that may lead to a save must retain the blob SHA returned by GitHub. A later save must use the then-current SHA from a fresh fetch.
3. **Session-start integrity check.** Before narrating resumed play, verify the Current Resume Packet against the detailed canonical sections for HP, XP/level, purse, spellbook/memorization, carried/stored inventory, location, chronology, conditions, active threads, relevant NPC state, and DM-secret state. If there is a conflict, stop and reconcile it before gameplay.
4. **Never invent established values.** If a statistic, modifier, spell, item, NPC fact, relationship, chronology point, clue, location, XP value, money total, injury, secret, or other persistent fact should already exist, retrieve it. If absent or ambiguous, preserve the uncertainty rather than guessing.
5. **Rules come from sources.** For exact AD&D 2e rules, spell text, tables, published setting facts, adventures, Dragon/Dungeon material, maps, and handouts, retrieve the user's source material when consequential. Do not silently substitute remembered rules.
6. **Source canon and campaign canon are separate.** Published material determines source canon; this ledger records what is actually true, discovered, changed, prepared, or established in Wren's campaign.
7. **Gameplay first.** Run AD&D 2e as a game, not collaborative novel-writing. The player controls Wren. The DM controls NPCs, world state, opposition, hidden information, encounters, and consequences. Use actual mechanics when meaningful uncertainty exists; do not manufacture checks for routine competence.
8. **No fudging / no plot protection.** Failure stands. Predetermined mechanical outcomes and genuine random results are not altered to protect Wren, force a scene, preserve an NPC, or improve pacing. Wren is not a chosen one and has no predetermined narrative arc.
9. **Persistent world.** Maintain prepared locations, NPC motives/capabilities, factions, dangers, secrets, clues, timelines, encounters, and likely developments. Randomness and improvisation supplement prepared world state rather than replacing it. Durable improvisation must be consistent with established geography, rules, NPCs, themes, and hidden causality.
10. **Published AD&D material is usable as real campaign material.** Draw freely from uploaded adventures and Dragon/Dungeon material when they fit naturally. Preserve substantive scenario content, locations, NPCs, encounters, mysteries, dangers, treasure, mechanical character, maps, handouts, diagrams, and illustrations. Do not announce OOC that a published module has been entered unless asked. Protect all DM-only keys, traps, secret doors, concealed areas, and spoilers.
11. **Preserve uncertainty and knowledge boundaries.** Keep player-known fact, rumor, suspicion, inference, Prepared Possibility, Open Question, and Established DM Truth distinct. Do not leak DM-only material during narration, summaries, or save verification.
12. **Pending-change register.** The moment a durable campaign fact changes, treat it as pending until the GitHub save and post-write readback succeed. Pending changes include character/mechanical state, inventory/money, spells/resources, XP, injuries/conditions, chronology/location, NPC relationships/actions, clues, rulings, obligations, faction/clock changes, promoted secrets, hidden consequences, and changes to what Wren knows.
13. **Checkpoint triggers.** Checkpoint at session end and after any consequential durable change where losing the change could alter play or fairness. During a long session, checkpoint at the next natural scene break if several durable changes accumulate. A fired checkpoint takes precedence over unrelated campaign work.
14. **Live Voice behavior.** During Live Voice, maintain coherent pending state in the same conversation. Do not claim external persistence while Live Voice tools are unavailable. When the player ends Live Voice but remains in the same conversation, ordinary text-mode tools may return; use that exact same conversation context for the SAVE operation rather than reconstructing the session through Personal Context or shared snapshots.
15. **Session-end trigger.** Natural session-ending language such as “goodnight,” “let’s stop here,” “end session,” or equivalent triggers a checkpoint. If the player ends Voice before the checkpoint can be written, do not give a false saved sign-off; after Voice ends, complete the save in the same chat when GitHub tools are available.
16. **SAVE workflow — mandatory and guarded.** At a checkpoint: (a) fetch the current canonical file from GitHub, (b) capture its fresh blob SHA, (c) reconcile every pending player-facing and DM-secret change into the full replacement content, (d) update `Wren_Campaign_Ledger.md` using that exact SHA, (e) receive the new commit/content SHA, (f) fetch the canonical file again from `main`, and (g) verify the intended checkpoint plus critical changed values. Only then may the DM say the checkpoint is saved.
17. **Conflict behavior.** If the update fails because the SHA is stale or the file changed, stop and refetch/reconcile. Never force-overwrite a concurrent change and never silently choose one version.
18. **Post-write readback is mandatory.** GitHub returning a successful commit is necessary but not sufficient. Read back enough of the newly stored canonical file to verify the checkpoint, resume packet, player-facing state, and that DM-secret changes were persisted. Player-facing confirmation must not expose secrets.
19. **Explicit persistence requests.** “Save that,” “lock that in,” “make that permanent,” “don’t forget this,” and equivalent explicit requests authorize an immediate canonical GitHub update when the requested material is campaign state/rules. One request is enough. Never say “saved,” “locked in,” or “permanent” until write + readback succeed.
20. **Do not make the player administer the ledger.** Routine loading/checkpointing is the DM's responsibility. The player may simply play, then end the session; no special bookkeeping phrase is required.
21. **Periodic audit.** After every three completed play sessions, and at major adventure/arc or phase boundaries, reconcile current character sheet, resources, chronology, NPC state, threads, rulings, established secrets, hidden clocks, delivered clues, and player knowledge against recent checkpoints/Git history.
22. **Historical recovery.** Git history and the original Library ledger are recovery tools. Do not substitute them for current `main` during ordinary play. Recovery requires deliberate comparison/reconciliation.

## Current Resume Packet

**Checkpoint:** Latest verified session checkpoint from 2026-08-12; GitHub migration completed administratively on 2026-08-13 without advancing gameplay.  
**Play status:** Session ended with Wren staying at Mrs. Tansy's boarding house in the harbor settlement while assisting Edric Hale for several days.

### Wren — Immediate State
- Level 1 mage; XP: **0 / no awards yet**.
- HP: **3/3**.
- AC: **10**, unarmored.
- Base THAC0: **20**.
- Movement: **12**.
- Current purse: **27 gp, 4 sp, 8 cp**. This remains provisional only in the narrow sense that a later sourced/rule-supported cost for Armor spell components must be reconciled rather than invented.
- Spellbook: simple book associated with/provided through the witch relationship.
- Known spell: **Armor** (1st-level wizard spell).
- Memorization capacity: **one 1st-level spell/day** at mage level 1.
- Intended current memorized spell: **Armor**.
- No established current injuries or conditions.
- Normal known carried baseline: **16.5 lb** before variable/unlisted contents; STR 9 remains unencumbered through **35 lb**.
- Boat-stored baseline: **50 ft hemp rope, hooded lantern, two one-pint lamp-oil flasks**; 24 lb fixed listed weight; 12 total hours of lantern fuel.
- Wren owns his late father's modest small coastal working boat; treasured, weathered, nonmagical, suitable for solo fishing and local coastal travel.

### Resume Position
- Wren is seated at the desk in his rented room at **Mrs. Tansy's boarding house** in the harbor settlement.
- He agreed to assist **Edric Hale** for several days and is staying locally rather than returning to his village each night.
- He is studying Edric's field journals and charts and practicing cartography.
- He has begun rudimentary field notes and a map of the voyage from his village to the harbor: coastline sketches, landmarks, harbor approach, estimated distances, and improvised hazard symbols.
- He noticed a journal reference to **unusual silence before fog** and privately connected it to the unnatural stillness he experienced while fishing. He has filed the observation away and may ask the witch about it after returning home.
- Wren's mother is **Mara** and younger sister is **Elia**.
- Exact named campaign setting and village remain unestablished unless later established/retrieved.
- Immediate unresolved rules item: whether the optional maximum-spells-per-level rule is in use. Exact consequential mechanics must be checked against the uploaded AD&D 2e sources when uncertain.

### Active Threads
- **Edric Hale:** Wren is assisting him in the harbor settlement for several days and studying his journals/charts.
- **Cartography/navigation:** Wren is beginning to learn through Edric's materials and his own field notes/map.
- **Silence before fog:** possible connection between Edric's journal reference and the unnatural stillness Wren experienced while fishing; Wren may later ask the witch.
- **Aldrin Hale:** friendly traveling measurer/mapmaker/surveyor who uses an astrolabe. Wren befriended him, learned rudimentary sighting, shared fish and ale, disclosed his interest in magic and desire to leave the coast. Aldrin mentioned a reportedly half-ruined observatory in the eastern hills, about 10–12 days away on foot, as a place he might visit; he did not recruit Wren.
- **The witch/mentor:** established obligation-laden background relationship and source of magical teaching; exact name and ultimate agenda are not player-established facts.
- **Character drive:** Wren strongly wants to leave the familiar coast, discover the wider world, and pursue magic/the unknown.

## Player Character — Wren

### Identity / Appearance
- Name: **Wren**
- Age: **19**
- Sex: male
- Class: mage, level 1
- Build: slight
- Hair: dark, longish
- Eyes: hawk-like

### Personality
- Restless and intensely curious.
- Affable but somewhat standoffish.
- Uncomfortable with mundane village life and strongly drawn beyond it.
- Often looks toward the horizon and wants to see more of the world.
- Studies things and people with unusual intensity, sometimes enough to make others uncomfortable.
- Not fundamentally angry.
- Recognizes danger/manipulation but sometimes suppresses caution when freedom, discovery, or magical knowledge pulls harder.

### Family
- **Mara**, mother: alive; early-to-mid forties; dark hair beginning to gray at the temples, usually tied back; weathered hands, strong features; practical, warm with Wren, perceptive.
- Father: deceased from illness or similar cause; his former coastal boat now belongs to Wren.
- **Elia**, younger sister: alive, roughly 15–16; shorter often-untidy dark hair, expressive face, quick grin; more openly social and comfortable with village life than Wren; fond of teasing him.
- Wren is close to his family; they understand that he is itching to leave and see the wider world.

### Coastal Life
- Comes from a small/remote coastal or waterside community.
- Sometimes pilots a small boat alone.
- Practical proficiencies reflect water, weather, fishing, ropes, and self-sufficiency.

### Witch / Mentor — Player-facing established facts
- Older female witch/mentor figure; pretty, wild-looking, unkempt, cunning, alluring.
- Villagers fear her; she keeps largely to herself.
- Wren has helped her and learned some magic from her over roughly 2–3 years through obligations/errands and informal magical teaching.
- Her teaching is not simple kindness and is not free.
- Wren suspects manipulation or a darker motive may exist, but his desire for knowledge/freedom outweighs much of his caution.
- Her exact name, ultimate motive, and full agenda are not player-established prior facts.

## Ability Scores / Derived Values

| Ability | Score |
|---|---:|
| Strength | 9 |
| Dexterity | 14 |
| Constitution | 13 |
| Intelligence | 18 |
| Wisdom | 14 |
| Charisma | 15 |

- CON 13: HP adjustment 0; system shock 85%; resurrection survival 90%; poison save adjustment 0; regeneration nil.
- INT 18: 7 languages/bonus proficiency slots under the recorded proficiency rules; maximum wizard spell level 9th; chance to learn spell 85%; maximum spells per spell level 18 **if that optional rule is used**; no illusion immunity. A +10% prime-requisite XP bonus was previously recorded but must be verified against the PHB when first applied.
- WIS 14: magical defense adjustment 0; no bonus priest spells; priest spell failure 0%; no spell immunity.
- CHA 15: maximum henchmen 7; loyalty base +3; reaction adjustment +3.

## Combat / Saves / Weapons

- Hit Die: 1d4
- HP: 3 current / 3 maximum
- AC: 10 unarmored
- Base THAC0: 20
- Movement: 12
- Armor: none
- Shield: none

### Level-1 Wizard Saving Throws
- Paralyzation/Poison/Death Magic: 14
- Rod/Staff/Wand: 11
- Petrification/Polymorph: 13
- Breath Weapon: 15
- Spell: 12

### Weapon Proficiency
- Proficient weapon: **Knife**
- Knife THAC0: 20 before situational/range modifiers
- Damage vs S/M: 1d3
- Damage vs L: 1d2
- Speed factor: 2
- Size: S
- Type: piercing/slashing
- Weight: 1/2 lb
- Thrown rate of fire: 2/round
- Thrown ranges: 10/20/30 yards; verify medium/long penalties from PHB when relevant.
- A quarterstaff is owned/carried but **no quarterstaff proficiency is established**.

## Nonweapon Proficiencies

Starting slot accounting: mage initial NWP slots 4 + INT 18 bonus slots 7 = 11 total; all 11 allocated.

| Proficiency | Slots | Relevant check |
|---|---:|---:|
| Spellcraft | 1 | INT -2 = 16 |
| Herbalism | 2 | INT -2 = 16 |
| Swimming | 1 | STR +0 = 9 |
| Weather Sense | 1 | WIS -1 = 13 |
| Seamanship | 1 | DEX +1 = 15 |
| Direction Sense | 1 | WIS +1 = 15 |
| Fishing | 1 | WIS -1 = 13 |
| Reading/Writing | 1 | INT +1 = 19 |
| Rope Use | 1 | DEX +0 = 14 |
| Fire-building | 1 | WIS -1 = 13 |

## Magic
- Spellbook: simple spellbook associated with/provided through the witch relationship.
- Known spell: **Armor**.
- 1st-level memorization capacity: 1 spell/day.
- Intended current memorized spell: Armor.
- Exact components/effects/duration must be retrieved from the uploaded AD&D 2e PHB when needed.

## Inventory / Funds / Encumbrance

### Normally carried / personal gear
- Quarterstaff — 4 lb; PHB table used did not provide purchase price.
- Knife — 1/2 lb; 5 sp.
- Spellbook — witch-associated; weight not assigned by the PHB table used.
- Small belt pouch — 1/2 lb; 7 sp.
- Basic spell components for Armor — exact quantity/cost/weight unassigned; do not invent.
- Backpack — 2 lb; 2 gp.
- Winter blanket/simple sleeping roll — 3 lb; 5 sp.
- Flint and steel — negligible listed weight; 5 sp.
- Wineskin/waterskin — 1 lb empty; 8 sp; filled-water weight tracked separately if relevant.
- One large sack — 1/2 lb; 2 sp.
- One day's ordinary food packed from home at campaign opening; not charged to starting budget.
- Small smooth beach stone of personal significance.
- Ordinary clothing — count 5 lb for PHB encumbrance.
- No armor; no shield.

### Normally stored aboard Wren's boat
- 50 ft hemp rope — 20 lb; 1 gp.
- Hooded lantern — 2 lb; 7 gp.
- Lamp oil — two one-pint flasks, 1 lb each, 6 cp each; 12 total hours of fuel at 6 hours/flask.

Items may move between carried and boat-stored inventory during play; ownership does not imply immediate access.

### Funds / starting accounting
- Rolled wizard starting-equipment funds: 40 gp.
- Known priced starting equipment: 12 gp, 5 sp, 2 cp.
- Current/provisional purse: **27 gp, 4 sp, 8 cp**.
- Armor components have no assigned source-supported starting cost yet; reconcile later if a source/ruling establishes one.
- One day's opening food is a home provision.
- Spellbook, ordinary clothing, personal stone, inherited boat are background possessions not charged to the 40 gp budget.
- Known normal carried baseline including clothing/quarterstaff but excluding variable/unlisted contents: 16.5 lb.
- Boat-stored rope + lantern + oil: 24 lb.
- STR 9 unencumbered through 35 lb under the recorded PHB table.

### Rulings
- Wren may clean and cook a simple fish meal without Cooking NWP; Cooking represents accomplished cooking, not basic food preparation.
- Keep PHB-listed fixed weights exact; do not invent precision for unlisted/variable contents.
- Distinguish carried inventory from boat-stored gear.

## NPC State

### Aldrin Hale
- Role: traveling measurer/mapmaker/surveyor; uses and repairs an astrolabe.
- Appearance known to Wren: older, wind-burned face, trim gray beard, dark traveling cloak.
- Session-1 location: temporary camp in a small coastal hollow near low cliffs, accessible from a sheltered shingle cove.
- Relationship: friendly new acquaintance; shared meal and conversation with Wren.
- Aldrin knows Wren is a local fisherman, eager to leave the coast, curious about travel/navigation, studies magic, and is drawn to the unknown.
- Wren knows Aldrin is long-traveled, originally from inland hill country but no longer strongly identifies a home, works with maps/measurements, expected to remain locally perhaps a day or two, and may next seek a reportedly half-ruined observatory in the eastern hills.
- Promises/debts: none. Aldrin welcomed Wren back to his fire if their paths cross again.
- Last significant interaction: fish and ale at Aldrin's fire on the night of Session 1.

### Edric Hale
- Established current thread: Wren is assisting Edric in the harbor settlement for several days.
- Wren is staying at Mrs. Tansy's while studying Edric's journals/charts and practicing field mapping/cartography.
- Do not invent additional Edric facts not yet present in canonical play/state.

### Family / Witch
- Mara, Elia, deceased father, and the witch/mentor are as described above.

## Chronology — Session 1 / First Played Day

- Morning: Wren performed minor repairs/maintenance on his inherited boat, set out, checked fishing nets/traps. Catch modest; one net showed ordinary fraying/torn mesh.
- Late morning: noticed a thin column of dark smoke along a sparsely inhabited coast and rowed closer.
- Landed in a sheltered shingle cove, tied the boat, followed a faint trail, met Aldrin Hale at a campfire repairing a brass astrolabe.
- Aldrin described his trade as measuring/mapping/settling questions about where things are and taught Wren rudimentary astrolabe sighting.
- Wren said he would take the first real chance he got to leave the coast. Aldrin did not recruit him.
- Wren fished for a couple more hours, returned to the village, sold part of his catch, used those proceeds to buy a stoneware jug of local ale, then returned by boat with ale and fish for supper with Aldrin. No deduction from the recorded starting purse is applied; exact sale/ale values remain unestablished.
- Wren cautiously disclosed that he studies magic and that the unknown draws him to it. Aldrin reacted without fear/condemnation.
- Aldrin mentioned a possibly half-ruined observatory in the eastern hills, roughly 10–12 days away on foot, which he might visit next. This was conversation, not recruitment.
- Night: Wren returned home. No injury, combat, spell expenditure, XP award, or other known mechanical change.

## Campaign Style / Setting Constraints
- Long-term solo AD&D 2e campaign.
- Preserve fragile low-level play, meaningful danger, and gradual earned growth in power.
- The player prefers discovering the world/adventure through play rather than inventing much of it.
- Mystara has been strongly considered as starting setting but is **not locked** unless established in play.
- Ravenloft has been discussed only as a possibility, not a locked destination.
- Campaign may begin remote and eventually develop a stronger home-base feeling.

## DM-ONLY CAMPAIGN STATE — DO NOT REVEAL TO PLAYER

This section contains established behind-the-screen truths and prepared possibilities. Do not quote, summarize, hint at, or expose it merely because it exists. Reveal only what Wren could reasonably discover. Established truths may not be changed merely to defeat a correct player inference.

### Established hidden situation at campaign start
- The apparently ordinary errand connected to Wren's witch/mentor is not arbitrary. She chose Wren because she needs a capable, curious person with local coastal knowledge who is not yet entangled in established magical institutions.
- The immediate errand is intended to place Wren near evidence of a larger coastal mystery without initially explaining its significance; the opening should feel mundane before anomaly emerges.
- Something old and magical is interacting with the coast and nearby waters. Manifestations are intermittent, not an openly visible catastrophe, allowing rumors, missing objects/people, odd tides, lights, wreckage, altered animals, or displaced things to accumulate gradually.
- The phenomenon is not simply the witch's spell gone wrong. She knows more than Wren does but neither created nor fully controls the underlying problem.

### Witch / mentor — hidden agenda
- Her interest in Wren mixes genuine intellectual/affectionate interest, self-interest, and deliberate manipulation. Do not flatten her into secretly benevolent or straightforward villain.
- She recognized signs connected to the coastal phenomenon before campaign start and believes Wren can investigate places/people that would react differently to her presence.
- She is withholding material information from Wren, partly from operational caution and partly to keep leverage.
- She wants knowledge first, not immediate destruction of the phenomenon.
- If forced to choose between Wren's safety and uniquely valuable magical information, her choice is genuinely uncertain and should depend on how the relationship develops.
- Her exact name remains deliberately unset until naturally introduced.

### Long-arc established truths
- The coastal mystery is a doorway into a wider network of old magical sites, lost routes, and competing interests rather than a self-contained first adventure. Wren can disengage, but consequences and other actors can continue.
- At least one intelligent outside party is already searching for the same underlying knowledge. This party is not initially aware of Wren personally; first contact need not be hostile.
- The old phenomenon has a discoverable history and internally consistent cause. Plant clues before full explanation; do not invent a contradictory answer merely for surprise.
- Wren's father's boat has no secret magical nature. Its emotional importance is real; never turn it into a chosen-one artifact.
- Wren is not secretly predestined/chosen. Importance must arise from choices, relationships, competence, discoveries, and consequences.

### Prepared factions / forces
- **Mentor's private inquiry:** currently one person plus plausible contacts/resources; goal to understand and potentially exploit the phenomenon before rivals.
- **Outside seekers:** an initially distant intelligent group/individual pursuing related old knowledge. Capable of negotiation as well as conflict. Their existence is established; exact identity/name/institutional form remains prepared-but-unfixed until setting details are locked.
- **Local community pressures:** villagers/fishers have incomplete observations/folklore; fear, superstition, practical economic concerns, and personal loyalties create believable reactions without making the whole village a conspiracy.
- **Phenomenon itself:** not a conventional faction and not necessarily sentient; effects must remain consistent with eventual underlying mechanism.

### Foreshadowing commitments
- Before explaining the coastal mystery, provide multiple independent clue types: at least one physical/environmental clue, one human report/rumor, and one magical/knowledge clue.
- Some early oddities have mundane explanations; not everything unusual belongs to the main arc.
- The witch should occasionally reveal knowledge she could not plausibly have learned from Wren alone.
- Outside seekers should leave evidence of activity before Wren necessarily meets them.

### Off-screen motion
- Coastal phenomenon continues intermittently if ignored; escalation follows campaign time/consequences rather than DM pacing desire.
- Witch continues her inquiry off-screen; significant actions/discoveries must be checkpointed.
- Outside seekers continue independently. Once concrete identity/starting position is established, maintain explicit progress clock or dated action log.
- Do not punish Wren for unrelated interests; off-screen motion changes circumstances/opportunities rather than forcing him onto a plot.

### Prepared possibilities — NOT YET TRUE
- Exact setting/geography remain unlocked; adapt names, institutions, cosmology, ancient history only after setting is established. Mystara remains a strong possibility but is not secretly locked.
- Exact nature of the old coastal magical mechanism is intentionally not finalized until setting is locked and relevant source material can be consulted. Before clues depend on the answer, promote the necessary answer to Established DM Truth and save it.
- Ravenloft remains only a possible future direction.
- Specific villains, betrayals, romances, deaths, and endgame outcomes are not predetermined.

### DM fairness / secret-state rules
- Label new secret material as **Established DM Truth**, **Prepared Possibility**, or **Open Question**.
- Once Established DM Truth and clues/actions rely on it, do not change it solely because the player guessed correctly.
- When a Prepared Possibility becomes true or supports a consequential clue, promote and checkpoint it.
- Preserve player beliefs separately from underlying truth.
- Random results may alter circumstances but cannot overwrite established secret causality.
- Before presenting a consequential clue that depends on an unresolved Prepared Possibility/Open Question, resolve the necessary hidden answer, label it Established DM Truth, and persist it.
- At session end, checkpoint hidden NPC/faction actions, clock positions, unrevealed consequences, delivered clues, promoted truths, and changes to Wren's knowledge.
- Save verification must not expose DM secrets to the player.

## Dice Protocol
- Player-facing rolls: Hiram rolls physical dice for Wren and other appropriately player-facing rolls, then reports the unmodified die result when needed; DM applies verified modifiers/rules.
- Hidden DM rolls: generate genuinely randomized programmatic results for rolls that should remain behind the screen.
- Uniform faces; independent compound dice unless rule specifies otherwise.
- No fudging, selective rerolls, discarded results, or narrative choice presented as a roll.
- Generate raw result first; apply modifiers/table interpretation separately.
- Do not reveal hidden rolls merely because generated; reveal only perceptible information.
- If a hidden roll establishes durable campaign state, hidden NPC/faction action, timed development, fixed treasure/content, or other lasting fact, persist the resulting fact as DM-secret state.
- Randomness cannot silently rewrite established truth.

## Campaign Ruling Log
- Basic fish preparation: Wren may clean/cook a simple fish meal without Cooking NWP; Cooking represents accomplished cooking rather than basic food preparation.
- Equipment bookkeeping: keep PHB-listed fixed weights exact; do not invent false precision for unlisted/variable contents; adjudicate when thresholds matter.
- Inventory locality: carried inventory and boat-stored gear are distinct.
- Starting-budget treatment: background possessions, witch-provided spellbook, personal stone, inherited boat, and one day's home food are not charged against the 40 gp starting equipment budget.
- Optional maximum-spells-per-level rule remains unresolved.
- Prime-requisite XP bonus recorded as +10% but must be verified against PHB when first applied.

## Change / Checkpoint History
- **Checkpoint 0 — 2026-08-11:** first persistent ledger; character generation substantially complete; play not yet begun.
- **Checkpoint 1 — 2026-08-11:** 40 gp starting-equipment roll; lantern/oil; carried-vs-boat storage; cost/weight reconciliation; purse 27 gp 4 sp 8 cp provisional; inherited boat; basic fish preparation ruling; persistence strengthened.
- **Checkpoint 2 — 2026-08-11:** session-start integrity checks, pending-change register, resume snapshot, fact domains, ruling log, periodic audits, no-memory fallback, Current Resume Packet, post-write readback, checkpoint precedence, resume-conflict rule.
- **Checkpoint 3 — 2026-08-11:** session-end sign-off barrier established.
- **Checkpoint 4 — 2026-08-11:** initial DM-only campaign state created; coastal situation, witch agenda, long-arc structure, outside seekers, foreshadowing, off-screen motion; no chosen-one/secret-magical-boat retcons.
- **Checkpoint 5 — 2026-08-11:** DM-secret state given same persistence/fairness standard as player-facing state.
- **Checkpoint 6 — 2026-08-11:** dice protocol established; physical player-facing dice, programmatic hidden dice, no fudging, raw-before-modifiers, hidden-roll privacy/persistence.
- **Checkpoint 7 — 2026-08-11:** end of Session 1; first played day and Aldrin Hale relationship recorded; no combat/injury/spell use/XP; monetary uncertainty preserved.
- **Checkpoint 8 — 2026-08-11:** clarified ale bought from that day's fish-sale proceeds; recorded purse unchanged.
- **Checkpoint 9 — 2026-08-12:** Mara and Elia established with descriptions/personality.
- **Checkpoint 10 — 2026-08-12:** prior Library canonical-ledger safeguard established.
- **Checkpoint 11 — 2026-08-12/13:** gameplay-first, prepared-world, published-material/map/handout, explicit persistence, and robust write/readback rules locked.
- **Session checkpoint — 2026-08-12:** Wren stays at Mrs. Tansy's while assisting Edric Hale, studying field journals/charts, practicing cartography; silence-before-fog observation connected privately to fishing stillness; resume at desk in rented room.
- **Administrative migration — 2026-08-13:** canonical persistence backend moved from ChatGPT File Library to GitHub after an end-to-end create/read/SHA-guarded-update/readback test succeeded. Gameplay state and chronology were not advanced by migration.

## Migration / Provenance
- Historical pre-GitHub Library source remains preserved as recovery evidence.
- Library file id at migration: `file_00000000ba88822fbf4aa0094eb5ee58`.
- Retrieved Library version id: `1`.
- Materialized source size: 58,833 bytes; 694 lines.
- SHA-256: `bad86ee53c2b987ebba9bcdd138d4757b9cbdd48bc387965575aa27a949998ef`.
- See `legacy/README.md` for provenance.
- From this migration forward, ordinary live state is `hiramhibbard/wren-campaign` → `Wren_Campaign_Ledger.md` on `main`. The Library source is recovery/history only.

## Pending Changes
- **None at migration completion.** No gameplay, mechanical, chronology, NPC, clue, faction, or DM-secret state was intentionally changed by migration.
