# Competitive Landscape — Solo AI TTRPG Engines

**Status:** Product / engineering research. Not campaign canon.  
**Parent roadmap:** `docs/APPLICATION_ROADMAP.md`  
**Initialized:** 2026-08-13.

## Purpose

Track the competitive landscape for solo-first AI tabletop RPG products and adjacent campaign/VTT systems. The goal is to identify genuine differentiation opportunities, avoid rebuilding features competitors already execute well, and capture architectural/product ideas worth adapting.

This document should be refreshed periodically because the category is moving quickly.

## Product thesis under evaluation

Potential Wren-derived positioning:

**The persistent solo tabletop campaign.**

Core promise:

- the user is genuinely the player and the AI is genuinely the GM;
- actual game procedures and deterministic mechanics govern outcomes;
- campaign state is authoritative and survives independently of chat history;
- NPCs, factions, locations, clocks, resources, clues, and consequences persist over long campaigns;
- source rules/adventures can be used with provenance and system fidelity;
- the campaign can scale for years without requiring the model to remember the entire history in one prompt;
- Voice can feel like sitting at a table;
- failures, death, missed clues, changing relationships, and world consequences are real rather than protected by narrative convenience.

Do not position the product merely as an "AI dungeon master." That phrase is already crowded.

## Competitive categories

### A. Solo-first AI RPG engines

Most strategically relevant because they solve the same core user problem: wanting to play a tabletop-like campaign without coordinating a group or human GM.

Primary products currently worth tracking:

- Wanderhold
- D20 Mind
- Aeveth
- RoleMIAster
- Friends & Fables (also supports multiplayer/world-building)

### B. AI interactive-fiction / storytelling platforms

Relevant for model routing, memory, context management, pricing, and narrative UX, but generally weaker matches for strict tabletop simulation.

Primary reference:

- AI Dungeon

### C. Human-GM VTT / campaign platforms with AI assistants

Relevant for source libraries, campaign UX, maps, notes, multiplayer, publishing/licensing, credits, and integrations. These are not the product category to compete with head-on.

Primary reference:

- Quest Portal
- Foundry VTT
- Roll20

The Wren-derived product should differentiate by being solo-first rather than attempting to become a feature-complete general-purpose VTT.

## Competitive matrix

Legend:

- **Strong** — prominently supported and central to public product behavior.
- **Partial** — exists, but with narrower scope or less evidence of depth.
- **Unknown** — public material does not establish enough to judge.
- **No / not focus** — appears outside current product intent.

| Dimension | Wanderhold | D20 Mind | Friends & Fables | Aeveth | RoleMIAster | AI Dungeon | Quest Portal |
|---|---|---|---|---|---|---|---|
| Solo-first AI GM | Strong | Strong | Strong/partial | Strong | Strong | Partial (story-first) | No (human-GM assistant) |
| Persistent campaign state | Strong | Strong | Strong | Claimed strong | Strong | Memory/story persistence | Strong campaign data, human GM |
| Deterministic mechanics outside narration | Strong | Strong | Strong/agentic game engine | Claimed rules/dice | Strong | Weak for TTRPG simulation | Dice/VTT tools, human adjudication |
| Existing published-system fidelity | Custom/simple system | 5e SRD | D&D-inspired / system engine | Open ORC rules | Custom Fantasy/Cyberpunk | Story systems | Many systems + source library |
| Multi-system architecture | Multiple custom worlds | Primarily 5e | Broad world-building | Genre-flexible, rules unclear | Two custom systems | Broad storytelling | Very broad VTT/system support |
| Long-term memory/retrieval architecture exposed | Partial | Partial | Strong | Claimed | Strong semantic RAG | Strong memory system | Campaign/library context |
| Context inspector / observability | Unknown | Unknown | Strong (`View Context`) | Unknown | Unknown | Context/memory tooling | AI assistant/library references |
| Source PDF/book support | No public emphasis | No public emphasis | Custom lore/world tools | Open rules only | Local/custom | Story cards/memory | Strong PDF + marketplace library |
| Source citations/provenance | No public emphasis | Rules integrated | Partial | Unknown | Unknown | Limited | Strong relative to field |
| Voice-first AI GM | No evidence found | No evidence found | TTS, not established full Voice GM | Claims voiced characters | Audio/multimedia, local AI | Voice features vary, not core TTRPG GM | Human campaign voice chat, AI co-pilot |
| Maps/location state | Limited / world-specific | Strong visible discovered map | Areas/POIs + scene | Unknown | Persistent world entities | Story-oriented | Strong VTT maps |
| NPC/faction world simulation | Persistent narrative/crew | NPC moods/locations | Strong entity model | Claimed | Persistent generated entities | Story memories | Human-managed campaign entities |
| Multiplayer | No / solo design | No / solo design | Strong | No / solo design | Planned | Multiplayer/story modes historically | Strong |
| Export / portability | Journal export | Unknown | Unknown | Unknown | Local app gives some independence | Story export tools | Campaign data within platform |
| Local/offline AI | No | No | No | No | Strong | No | No |
| Subscription/monetization | Free + $9.99/$29.99 plans | credits + monthly pass | $19.95/$29.95/$39.95 | Private beta | One-time local purchase / BYO quota on mobile | $14.99–$99.99 tiers | subscription + credits |
| Automated evaluation/regression publicly described | Strong | Unknown | Unknown | Unknown | Unknown | Mature model eval likely, not product-specific public detail | Unknown |

## Product-by-product teardown

### Wanderhold

**Why it matters:** Closest strategic competitor to the current product thesis.

Public positioning:

- explicitly solo-first;
- persistent campaigns across sessions;
- AI is used for narrative while rules/oracle systems establish constraints and outcomes;
- cloud auto-save;
- custom worlds and mechanics;
- journal export;
- browser-based;
- public pricing includes Free, Saga ($9.99/month), and Chronicle ($29.99/month).

Especially important architectural/product ideas:

1. **AI writes last.** Oracle/mechanical systems establish mission type, objective, location details, incidents/themes, and other constraints before narration. This reduces narrative hallucination and gives the generated prose a deterministic scaffold.
2. **Narration does not determine success.** Character sheet/dice determine outcomes; AI narrates those outcomes.
3. **Regression testing of prompts.** Wanderhold publicly describes complete automated gameplay loops and rubric-based evaluations before prompt updates ship. This strongly validates putting an evaluation harness early in the Wren application roadmap.
4. **Simple user promise.** "Show up and play" and "world exactly where you left it" communicate persistence without exposing engineering complexity.

Potential weaknesses/gaps relative to Wren thesis:

- intentionally simpler/custom mechanics rather than fidelity to existing tabletop systems;
- no public emphasis on user-owned rulebook/adventure source integration;
- no public evidence of deep source provenance/citations;
- no public Voice-first AI table experience found;
- no public evidence of inspectable canonical/event architecture;
- narrative scene structure may be more constrained than fully freeform tabletop exploration.

**Strategic lesson:** Do not compete by merely adding persistent state and deterministic dice; Wanderhold already understands those. Differentiate on real TTRPG system fidelity, source-backed play, long-campaign world integrity, freeform tabletop agency, Voice, and inspectability.

### D20 Mind

**Why it matters:** Very direct "play pen-and-paper solo" positioning with visible mechanics and persistent state.

Public positioning:

- solo AI Game Master;
- real 5e SRD rules;
- visible dice/results;
- persistent HP, inventory, NPC moods, discovered places, and knowledge;
- discovered-world map;
- browser-based;
- free trial, one-time credit purchases, monthly passes starting around €9.99 with higher tiers.

Notable ideas:

1. **"World as canon" UX.** Public material emphasizes that the map and the world state cannot disagree. This is an excellent user-facing expression of canonical-state integrity.
2. **Visible rules trust.** Open rolls, conditions, spell slots, and combat state are surfaced rather than hidden behind prose.
3. **"What I know" presentation.** A player-facing structured knowledge list is prominently shown. This aligns directly with Wren's knowledge-boundary architecture and suggests the future Player Journal should make known facts/rumors/relationships a first-class UI.

Potential gaps:

- 5e-centric rather than system-adapter architecture;
- no public evidence of sourcebook/PDF adventure instantiation;
- no strong public evidence of Voice-first play or context inspection;
- current public scale/long-campaign architecture is unclear.

**Strategic lesson:** Trust should be visible in UX, not only implemented internally. Expose mechanics, state, and player knowledge cleanly.

### Friends & Fables

**Why it matters:** Closest architectural competitor found.

Public architecture/features:

- explicitly describes an **Agentic Campaign Engine (ACE)** rather than one chatbot call;
- often performs 10+ requests to different models per player interaction;
- keeps structured campaign entities including characters, locations, items, monsters, factions, areas, and points of interest;
- compiles a **Current Scene** using locality/relevance, with nearby characters receiving more context;
- creates compressed long-term memories every five turns;
- retrieves memories semantically by location/characters/relevance;
- maintains a running Plot and ephemeral per-turn Plan;
- uses automatically researched **Working Context Blocks** with budgets, priorities, expiration, active/idle/archive states;
- allows players to inspect `View Context`;
- narration and state-update operations receive different context;
- supports multiplayer, TTS, encounters, worlds, and image generation;
- subscriptions currently range from free to $19.95/$29.95/$39.95 monthly tiers, with plan-dependent context limits and credits.

Strong ideas worth retaining/adapting:

1. **Context budget groups.** Allocate soft budgets per context class (scene, lore, memories, mechanics, etc.) rather than one undifferentiated token pool.
2. **Context block lifecycle.** Candidate context can be active, idle, or archived; newer/relevant blocks can displace older material without deleting it.
3. **Automatic research pass.** A cheaper/research-oriented model can search lore/entities/memories before the higher-quality narrator executes.
4. **Task-specific context.** Narration context differs from a mechanical/state-update context.
5. **Inspectable context.** Users can diagnose why the GM forgot or misunderstood something.
6. **Explicit admission that semantic memory retrieval is fallible.** Their docs expose failure modes rather than pretending memory is perfect.

Potential Wren differentiation:

- Wren aims for stricter distinction between retrieval candidate and canonical truth;
- immutable transaction/event history and independent readback verification are stronger integrity goals;
- source-book/adventure fidelity and provenance can become much stronger;
- actual system adapters rather than a primarily D&D-inspired campaign engine;
- long-term campaign state should not require users to manually correct/edit working context for correctness;
- Voice-first play can be a primary interaction mode rather than TTS layered on text play.

**Strategic lesson:** Context compilation should probably become a real multi-stage runtime earlier than originally planned. The Context Inspector is not optional at product scale; it is an important debugging/trust tool.

### Aeveth

**Why it matters:** Very close marketing thesis to Wren even though it remains a private beta.

Public positioning:

- one-player AI Game Master;
- distinct character voices;
- dice the GM cannot fudge;
- claims faithful rules play;
- persistent world memory across sessions;
- multiple genres;
- built on Claude;
- open/ORC-licensed rules content;
- granular content/limits controls;
- private beta/self-funded.

Potential differentiation/gaps:

- public technical/state architecture is not exposed;
- source/adventure library support appears constrained to open rules;
- no evidence found of user-owned PDF/source instantiation;
- no public pricing/product maturity yet.

**Strategic lesson:** "Honest dice," "real GM," and no plot protection are not unique differentiators by themselves. They remain essential table stakes for the category we want.

### RoleMIAster

**Why it matters:** Technically adventurous competitor with several architectural ideas overlapping ours.

Publicly described architecture/features:

- local AI on desktop, with Qwen-family/local model stack;
- semantic RAG that can retrieve distant turns;
- specialist-agent architecture for combat/story/NPC responsibilities;
- persistent generated NPCs/items/locations;
- nested physical storage model (objects in containers in rooms/locations);
- a multi-layer validation system described as a "reality sheriff" to ensure narration and mechanical state agree;
- tactical/narrative combat;
- inventory/weight and other deterministic mechanics;
- multimedia generation/selection;
- one-time Steam purchase rather than hosted inference subscription;
- future BYO-quota mobile strategy;
- multiplayer planned but recognized as a major engine restructuring.

Strong ideas worth adapting:

1. **Narrative-state validator.** After narration, a deterministic/structured validator should ensure claimed state changes are mechanically possible and represented canonically.
2. **Physical containment hierarchy.** Location/storage/ownership relationships should be first-class rather than only textual metadata.
3. **Local/BYO inference as an eventual power-user option.** This may become strategically useful for privacy/cost resilience.

Potential weaknesses/gaps:

- current product has a very small early-access user/review base;
- local model hardware requirements create substantial adoption friction;
- custom systems rather than existing-system fidelity;
- public UI/product maturity appears early;
- architectural claims should be treated as product statements rather than independently verified internals.

**Strategic lesson:** Add a future **Narrative-State Reconciliation / Reality Validator** to the roadmap. It should compare narrated consequences against structured mechanical/canonical deltas before commit.

### AI Dungeon

**Why it matters:** Mature benchmark for AI narrative economics, memory, tiering, and context limits, even though it is not trying to be a strict tabletop simulator.

Relevant features:

- tiered memory-bank sizes;
- tiered context windows;
- membership ladder from free through high-cost premium tiers;
- episodic memory retrieval;
- explicit distinction in its own documentation between AI Dungeon storytelling memory and the more structured "game state" approach used in Voyage-style RPG experiences.

Lessons:

- context/memory is expensive enough to be a direct subscription differentiator;
- power users will pay substantially more for larger context/model capability;
- avoid tying product value purely to raw context size: a good Context Compiler should make small high-quality context outperform brute-force prompt stuffing.

### Quest Portal

**Why it matters:** Strong adjacent product for source integration, campaign UX, AI-assistant monetization, and VTT interoperability—but a different strategic category.

Relevant features:

- human-GM-first VTT;
- many game systems/no-code sheets;
- maps/tokens/fog/lighting/voice chat;
- AI GM Assistant for rules, prep, encounters, lore, notes, art;
- imported PDFs and marketplace books can be used by the Assistant;
- campaign library/source-backed answers;
- model selector balancing power/speed/cost;
- credit-based metering and campaign boosting/sharing;
- player accounts can remain free while a GM unlocks AI/campaign features.

Lessons for Wren app:

1. **Source library UX matters enormously.** Uploading/owning a book should make its rules/adventure content available without manual prompt engineering.
2. **Model selection can be exposed carefully.** Power users may value quality/speed/cost choice, though default automatic routing should remain simple.
3. **Credits are useful internally but potentially awkward as primary UX.** Consider hidden usage allowances and only expose credits/top-ups where necessary.
4. **Do not compete on VTT completeness.** Integrate/export to VTTs later instead of recreating every map/lighting/collaboration feature.

## High-value ideas discovered during research

### 1. Narrative-State Reconciliation layer

Add a formal validation step after AI narration/action interpretation and before canonical transaction commit.

Conceptual pipeline:

`Player Intent -> Adjudication/Mechanics -> Narration -> Candidate State Delta -> Reality Validator -> Canonical Transaction`

The validator checks that narration and structured state agree. Examples:

- narration says an item was given -> ownership/inventory delta must exist;
- narration says a door was unlocked -> location/object state changes;
- narration says a spell was cast -> spell/resource/condition updates exist;
- narration says an NPC left -> location/relationship/clock state reflects it;
- narration contradicts deterministic roll/mechanics -> reject/regenerate/correct before commit.

This is distinct from checkpoint readback verification. Readback proves persistence; the Reality Validator proves semantic coherence between narration and the proposed state change.

### 2. Multi-stage per-turn orchestration

Do not assume one expensive model call per player turn.

Potential pipeline:

1. intent classification;
2. canonical/direct retrieval;
3. context research/ranking;
4. deterministic rules/mechanics procedures;
5. high-quality DM adjudication/narration;
6. structured delta extraction;
7. reality validation;
8. pending transaction update;
9. optional cheap episodic/index projection.

Each stage can use the cheapest reliable mechanism: deterministic code first, small model when appropriate, premium reasoning/narration model only where its quality matters.

### 3. Context budgets by semantic class

The future Context Compiler should consider soft budgets/priority per class, e.g.:

- mandatory invariants;
- immediate mechanics;
- current scene;
- present NPCs/entities;
- active threats/clocks;
- relevant DM truth;
- episodic history;
- source excerpts;
- recent conversation.

This is better than simply requesting the largest available model context.

### 4. Trust UX

Internally correct architecture is not enough. Expose trust in player-friendly ways:

- visible dice/procedure outcomes where appropriate;
- clear character/resources/conditions;
- "What I know" / player journal;
- exact resume state;
- source citations when rules matter;
- optional Context Inspector for debugging;
- save/transaction health without technical Git terminology in the consumer product.

### 5. Evaluation harness earlier

Move automated evaluation/regression earlier in the roadmap.

Before prompt/model/runtime changes ship, run synthetic campaigns and complete gameplay loops across:

- combat;
- investigation;
- social play;
- travel/hexcrawl;
- downtime;
- source-adventure execution;
- long-memory retrieval;
- failure/death;
- faction clocks;
- Voice transcripts;
- context-pressure cases.

Score rules fidelity, continuity, agency, knowledge leakage, narration quality, state consistency, and retrieval correctness.

## Defensible differentiation opportunities

### 1. Existing TTRPG fidelity rather than proprietary-light rules

The app should let AD&D 2e feel like AD&D 2e and Dolmenwood feel like Dolmenwood. The engine should execute each system's procedures, calendars, encounter rules, advancement, magic, travel, faction systems, etc., through adapters and source-backed rules.

Competitors often simplify mechanics or center one custom/5e-like ruleset.

### 2. Source-backed campaign instantiation

User-owned or licensed rulebooks/adventures become first-class source material. Published entities/templates are referenced, and live campaign instances record divergence.

This supports playing actual adventures/systems instead of only AI-generated worlds.

### 3. Long-campaign integrity as a product promise

Design for years of play and hundreds/thousands of entities from the beginning:

- event history;
- materialized projections;
- stable entity IDs;
- derived indexes;
- bounded context compiler;
- growth/sharding policy;
- audit/recovery/export.

The differentiator is not "it has memory" but "the campaign remains reconstructable and internally coherent as it grows."

### 4. Voice as a table experience

A true low-latency conversational GM with reliable state/tool transitions could be a major differentiator if competitors remain primarily text/scene driven.

Desired UX:

- sit down;
- say what you do;
- roll physical dice optionally;
- interrupt naturally;
- switch text/Voice freely;
- receive private/visible rules and maps only when useful;
- leave knowing the campaign was durably saved.

### 5. Inspectable provenance and knowledge boundaries

Build trust through:

- canonical fact provenance;
- source citations;
- player/DM visibility classification;
- context inspector;
- event/audit history;
- explicit uncertainty categories.

### 6. Portability / user ownership

Campaign export should include enough event/state/source metadata to avoid lock-in. Git-style human-readable export may remain a differentiator even after runtime storage moves to a database.

## Things that are no longer differentiators by themselves

The competitive research suggests these are becoming category table stakes:

- "AI remembers NPCs";
- persistent inventory/HP;
- AI-generated NPCs and locations;
- real dice;
- no-railroad marketing;
- campaign resumes across sessions;
- AI-generated portraits/images;
- basic deterministic mechanics;
- "not just a chatbot" messaging.

They remain necessary, but they should not anchor positioning.

## Current positioning hypothesis

A concise product framing worth testing:

**A persistent solo tabletop RPG engine where the AI is the GM, the actual game rules determine what happens, and the campaign remains a real world you can return to for years.**

Supporting message pillars:

1. **Play the real game.** System procedures and source material matter.
2. **Just be the player.** The engine handles GM responsibilities and bookkeeping.
3. **The world is real state.** NPCs, resources, factions, locations, clocks, and consequences persist.
4. **Your choices stay changed.** No reset when the context window ends.
5. **The GM can surprise you.** DM truth remains genuinely hidden.
6. **Come back anytime.** Exact durable resume across devices/sessions.
7. **Built for campaigns, not chats.** Long-term scale is an architectural requirement.

## Product strategy recommendation

Do not attempt to beat Foundry or Roll20 at VTT features.

Do not attempt to beat AI Dungeon at unconstrained collaborative fiction.

Do not rely on generic "AI DM" positioning.

Focus product development around a narrow first wedge:

**solo TTRPG players who want to play a real campaign tonight without becoming their own GM.**

The first user experience should make creating/resuming a campaign dramatically easier than assembling ChatGPT + PDFs + notes + random tables + character sheets manually.

## Recommended roadmap adjustments

Based on this teardown:

1. Promote **evaluation/regression harness** earlier, alongside the first Context Compiler prototype.
2. Add **Narrative-State Reconciliation / Reality Validator** as a first-class runtime layer.
3. Add **context-class soft budgets/priorities** to the Context Compiler design.
4. Add a player-facing **What I Know / Journal** as an early UX concept.
5. Add **physical containment / ownership edges** to structured relationship design (`CONTAINS`, `OWNED_BY`, `CARRIED_BY`, `STORED_AT`).
6. Prototype **multi-stage per-turn orchestration** and measure cost/latency before assuming one-model-call architecture.
7. Treat **Voice latency and Voice tool continuity** as explicit competitive benchmarks.
8. Add competitor/regression benchmarking to product research: periodically replay standardized scenarios against leading products where possible.
9. Keep VTT/maps integration later and integration-oriented rather than feature-parity oriented.

## Products to monitor closely

### Tier 1 — direct strategic competitors

- Wanderhold
- D20 Mind
- Aeveth
- RoleMIAster
- Friends & Fables

### Tier 2 — adjacent architectural/business references

- AI Dungeon
- Quest Portal

### Tier 3 — ecosystem / integration incumbents

- Foundry VTT
- Roll20

## Research limitations

This analysis is based primarily on current public product pages, documentation, pricing, help centers, press materials, and store listings as of 2026-08-13. Public claims do not prove private implementation details. Where a product says it has persistence, memory, rules fidelity, or multi-agent architecture, treat that as an externally stated capability unless verified through hands-on testing.

A future competitive pass should include actual accounts/playtests in the leading products, recording:

- onboarding time;
- solo agency;
- handling of freeform actions;
- mechanical correctness;
- failure/death behavior;
- long-session state consistency;
- cross-session memory;
- NPC consistency;
- context failure recovery;
- source support;
- Voice experience;
- latency;
- exportability;
- pricing friction.

## Sources reviewed in this pass

Public materials reviewed included current Wanderhold product/how-it-works/pricing/press pages; D20 Mind product/pricing material; Friends & Fables pricing and documentation for Current Scene, Memories, Working Context Blocks, context limits, Plot/Plan and ACE game-state context; Aeveth's current product/private-beta site; RoleMIAster's official site and Steam Early Access listing; AI Dungeon memory/membership documentation; and Quest Portal Assistant/pricing/PDF/library/credits documentation.
