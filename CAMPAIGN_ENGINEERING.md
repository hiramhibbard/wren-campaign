# Wren Campaign Engineering

This file is the durable design/roadmap layer for the campaign system. It exists so architecture work can continue across fresh chats without depending on conversational history.

It contains infrastructure decisions, operational status, known limitations, future-work notes, and test plans. It must not duplicate live campaign state, DM secrets, published source text, or ordinary session history.

## Authority and scope

- Canonical campaign facts remain in `Wren_Campaign_Ledger.md`, sharded `state/` files, and post-baseline checkpoints.
- Runtime/persistence rules remain governed by `CAMPAIGN_BOOTSTRAP.md` and `STATE_SCHEMA.md`.
- Reusable state structures remain governed by `STATE_TEMPLATES.md`.
- Exact AD&D 2e rules and published content remain governed by Hiram's uploaded source material.
- This engineering file records architecture intent, accepted design decisions, implementation status, and future work.
- Architecture work must not advance gameplay unless Hiram explicitly switches back into play.

## Fresh-chat engineering bootstrap

When Hiram asks to continue improving the campaign system, architecture, persistence, DM behavior, memory, Voice workflow, or maintenance design:

1. Load the normal canonical bootstrap/root/index required by the Project.
2. Load this file before proposing or implementing architecture changes.
3. Inspect the specific referenced implementation files before editing them.
4. Preserve existing campaign state and player/DM knowledge boundaries.
5. Treat repository state as authoritative for what has already been implemented; do not reconstruct engineering status from conversational memory.
6. Administrative architecture changes do not require a gameplay checkpoint unless they also change actual campaign state.
7. Verify every repository write by canonical readback before reporting it complete.

## Settled architecture decisions

### Canonical backend and retrieval
- GitHub repository `hiramhibbard/wren-campaign`, branch `main`, is the canonical campaign backend.
- `Wren_Campaign_Ledger.md` is the compact root manifest/resume layer.
- `STATE_SCHEMA.md` defines sharding, checkpoints, compaction, concurrency, recovery, maintenance, and manual-write fallback.
- `state/INDEX.md` is the primary canonical routing index.
- Established facts are retrieved automatically whenever they could affect narration, adjudication, NPC behavior, resources, history, clues, or consequences.
- Absence from the current conversation is never evidence that campaign state is absent.

### Persistence
- Ordinary saves use immutable append-only checkpoints after the materialized snapshot baseline.
- Writes are not considered saved until read back and verified.
- Connector safety blocks use a human-transport fallback with an exact prepared transaction; Hiram should not have to reconcile campaign facts manually.
- Compaction folds post-baseline checkpoint deltas into sharded state, updates the root last, and preserves historical checkpoints.
- Maintenance becomes due at 10 or more uncompacted real campaign checkpoints unless earlier intervention is warranted by size/integrity/arc transitions.

### Incremental maintenance
- Real checkpoints should include dirty-domain hints from `STATE_TEMPLATES.md`.
- Routine maintenance should update only affected shards plus required indexes/cross-links when safe.
- Broad integrity audits remain available when needed, but normal compaction should not repeatedly rebuild the whole campaign encyclopedia.

### Live Voice
- Ordinary Project chat/Live Voice is the game table; Work/Codex is the maintenance console.
- Before Live Voice, load a practical working set broad enough for likely play.
- If Voice cannot access GitHub and an obscure canonical fact is needed, do not guess. Preserve the pending lookup and automatically resolve it in text mode in the same conversation after Voice ends.
- Voice-session durable changes remain pending until a post-Voice checkpoint is written and verified.

### AD&D rules and dice
- Run actual AD&D 2e rather than generic modernized checks.
- Hiram rolls player-facing physical dice; the DM applies modifiers/adjudication.
- Hidden DM rolls use genuine randomized secret results, with no fudging, rerolls for convenience, discarded outcomes, or fake randomness.
- Exact consequential rules are retrieved from uploaded AD&D sources when needed.
- XP is evaluated automatically at meaningful encounter/objective resolution and session end using published AD&D 2e/applicable source rules.

### NPC generation and portrayal
- NPCs use significance tiers rather than automatic full character sheets.
- Original NPC generation follows a context-first hierarchy: published/source facts -> established world context -> role requirements -> mechanical profile -> alignment/ethos -> personality/history -> cognition/speech -> constrained variation -> consistency pass -> canonicalization.
- Randomness provides variation inside plausible constraints rather than overriding world logic.
- Once consequential hidden NPC details have informed play, they become durable state and are not regenerated for convenience.
- Jobs, training, social position, education, culture, class/race/source restrictions, ability scores, proficiencies, alignment, history, and resources should form a coherent whole.
- Unusual combinations are allowed when coherent; poverty or low social status does not dictate low innate Intelligence, and high status does not guarantee competence.
- Significant NPC speech and reasoning are grounded in Intelligence, Wisdom, Charisma, education, culture, occupation, languages/literacy, social position, emotional state, knowledge, and personality.
- Alignment informs values, methods, loyalties, conflict, relationships, and mechanical interactions without replacing personality.
- Hidden NPC alignment is not exposed merely because the DM knows it.
- Henchmen remain independent NPCs with motives, alignment, personality, loyalty, obligations, compensation/share, risk tolerance, and off-screen lives.

### Persistent-world scaffolds
Reusable templates now exist for:
- world clock and scheduled event queue;
- regional/planned/random encounters;
- reaction and morale/loyalty procedures;
- factions, resources, goals, and clocks;
- clues, rumors, inferences, false beliefs, and knowledge boundaries;
- travel/exploration state;
- downtime/long-running projects;
- significant items, provenance, identification, charges, curses/intelligence/alignment restrictions;
- published-adventure/source registry;
- entity promotion/demotion;
- checkpoint dirty-domain routing.

These are generally instantiated only when play makes them relevant rather than as empty folders/files.

## Implemented files of special engineering relevance

- `CAMPAIGN_BOOTSTRAP.md` — full runtime operating protocol.
- `STATE_SCHEMA.md` — persistence/state architecture.
- `STATE_TEMPLATES.md` — reusable long-term state scaffolds and entity templates.
- `state/rulings/dm-procedure-triggers.md` — automatic recognition of active AD&D/DM procedures.
- `state/rulings/npc-generation-and-portrayal.md` — context-first NPC generation, alignment, competence, cognition, personality, and portrayal.
- `state/rulings/dice-protocol.md` — player-facing/secret dice rules.
- `state/rulings/adnd2e-campaign-rulings.md` — campaign rules and XP policy.
- `state/clues/active.md` — instantiated player-facing clue/knowledge ledger.
- `state/npcs/index.md` — current NPC routing and promotion guidance.

## Operational status / completed tests

- Sharded snapshot generation 1 is active.
- Cold-start test passed: a fresh Project chat correctly loaded the canonical repository and resumed the proper state without relying on the previous conversation.
- Automatic canonical-retrieval test passed: a fuzzy historical question was checked against canonical state rather than answered from conversational memory.
- NPC state files have a consistent Markdown precedent and current routes use `state/npcs/edric-hale.md`.
- XP automation policy has been added and verified.
- Long-term DM scaffolds and NPC generation/alignment protocol have been added and verified.

## Next major validation work

### Live Voice continuity test
1. Start a fresh Project chat and load the campaign normally.
2. Enter Live Voice without advancing gameplay unless explicitly intended.
3. Verify the current state carries into Voice.
4. Ask about an obscure canonical fact that was deliberately not preloaded.
5. Expected behavior while Voice retrieval is unavailable: the DM says a canonical lookup is required and preserves the pending context instead of guessing.
6. End Voice and remain in the same chat.
7. Expected behavior in text mode: the DM automatically performs the pending GitHub lookup without requiring Hiram to repeat the question.

### First real append-only checkpoint test
- After the Voice workflow is validated, test a genuine post-baseline campaign checkpoint at a safe boundary.
- Verify sequence/concurrency, automatic create when possible, canonical readback, critical delta coverage, and maintenance counting.
- If connector safety blocks the write, exercise the exact manual checkpoint fallback and then read back the transported file.

## Known operational limitations

- GitHub connector writes can occasionally be blocked by OpenAI's external-write safety layer even when the requested mutation is valid. The system should retry only when sensible and otherwise use the explicit prepared manual fallback.
- GitHub/connected-app tools may be unavailable during Live Voice. The architecture therefore relies on preloading and deferred same-conversation lookup/checkpoint behavior.
- Published source retrieval can be expensive when exact rules or obscure module details are needed. Campaign state should store durable adaptations/references while leaving copyrighted source text in the uploaded source library.

## Future idea / decision log protocol

Use this section for engineering ideas that should survive chat boundaries but are not yet fully implemented.

Each entry should use one status:
- **Proposed** — worth considering; not accepted yet.
- **Accepted** — design agreed; implementation pending or partial.
- **Implemented** — repository implementation exists and has been verified.
- **Deferred** — intentionally postponed until play makes it relevant.
- **Rejected** — intentionally not pursuing; retain the reason if it prevents repeated reconsideration.

When an idea becomes implemented, update its status and point to the canonical implementation file. Do not leave completed work permanently described as pending.

### Current future-work notes
- **Accepted / test pending:** Live Voice continuity/deferred-lookup workflow.
- **Accepted / test pending:** first real post-baseline append-only campaign checkpoint.
- **Deferred:** stronghold, domain, mass-combat, advanced naval, planar, sage/spy/assassin, disease/aging, and extensive magic-item-construction subsystems until play makes them relevant. Exact published procedures should be retrieved and scaffolded when activated.
- **Deferred:** exact named setting/geography-dependent engineering until campaign canon establishes the setting sufficiently to make specialized support useful.

## Design principle for future improvements

Prefer infrastructure that reduces future interruptions at the game table: automatic procedure recognition, compact durable state, source-aware adjudication, meaningful hidden world motion, incremental maintenance, and explicit routing. Avoid speculative complexity that increases startup cost without improving likely play.
