# Adventure Opportunity / Scenario Regression Scenarios

These are engineering/audit tests only. They do not alter live campaign state.

## AOR-001 — Opportunity without player request
Given Wren enters a newly relevant region with unresolved scenario space.
Expected: DM evaluates the adventure/site/situation opportunity automatically without Hiram asking for an adventure, including whether targeted published search or original creation is the better path.
Failure: scenario material is considered only after explicit player request.

## AOR-002 — No adventure quota
Given several sessions pass without dungeon/combat but no causal opportunity trigger occurs.
Expected: no forced adventure search or inserted dungeon merely for pacing.
Failure: scenario introduced because campaign seems due for action.

## AOR-003 — Dungeon Magazine is first-class
Given a local site/problem/side trek would naturally fit current geography and scope.
Expected: Dungeon Magazine adventures/side treks are included among primary candidate families when published search is promising.
Failure: search only standalone modules or setting books.

## AOR-004 — Targeted search, not magazine scan
Given a coastal exploration opportunity for which published material is plausibly useful.
Expected: search by coast/maritime/site/risk/setting facets against likely adventure sources.
Failure: load or scan every Dungeon issue.

## AOR-005 — Candidate is not canon
Given a promising Dungeon adventure is found.
Expected: remains Candidate/Prepared Possibility until minimum facts are actually seeded.
Failure: its town, villains, history, or treasure silently become world truth.

## AOR-006 — Minimal seeding
Given current causality needs only a rumor and location sign from a selected scenario.
Expected: instantiate only those facts; do not silently instantiate every keyed room/NPC event.
Failure: whole adventure becomes active merely from a rumor.

## AOR-007 — Setting compatibility
Given a generic adventure conflicts materially with active setting treatment.
Expected: reject or minimally adapt only where coherent; active setting source governs explicit conflicts.
Failure: generic module flattens setting canon.

## AOR-008 — Low-level Wren meets high-risk possibility
Given an excellent-fit published or original scenario is intended/naturally suited for much stronger characters.
Expected: it may exist as dangerous world content; do not downscale automatically. Provide ordinary causal warning signs when plausible.
Failure: rebalance it merely to make a fair level-1 encounter.

## AOR-009 — Player agency survives hook
Given a module or original setup suggests a patron's mission.
Expected: present opportunity/pressure; Wren may refuse, ignore, negotiate, investigate independently, or walk away.
Failure: narration assumes acceptance or forces required scene order.

## AOR-010 — Scenario survives bypass
Given Wren learns of a seeded scenario and ignores it.
Expected: scenario/world actors continue or go dormant according to causality; no reset and no repeated forced hook.
Failure: adventure waits frozen forever or is repeatedly shoved at Wren.

## AOR-011 — Published state overlays source
Given Wren enters a module site, kills an inhabitant, moves treasure, triggers alarms, and retreats.
Expected: campaign state preserves all consequences and overlays the original keyed baseline.
Failure: source resets when Wren returns.

## AOR-012 — Existing thread can recruit published material
Given an original Wren campaign thread now needs a compatible ruin/site/faction location.
Expected: targeted adventure-source search may provide a published site if it fits naturally and efficiently.
Failure: published material is considered only as standalone quests.

## AOR-013 — Published material can remain unrelated
Given a source contains an attractive adventure but no active-world reason supports its presence.
Expected: keep it unseeded rather than inserting it because it is good content.
Failure: library availability becomes world causality.

## AOR-014 — Off-screen motion after seeding
Given a seeded scenario has actors with goals and time passes.
Expected: process them through regional/site/faction/world-motion rules when due whether the material was published or original.
Failure: scenario actors freeze until Wren enters their scene.

## AOR-015 — Search facets respect current context
Given a published-source search is chosen for an opportunity in a coastal human settlement with no established setting override.
Expected: use known geography, environment, tone, risk, current threads, and source scope as search facets; do not invent missing exact geography solely to make a module fit.
Failure: modify established/unresolved world boundaries to force a candidate.

## AOR-016 — Repeat-use performance
Given the same magazine/module index or source family has yielded useful candidates repeatedly.
Expected: retain lightweight derived locators/tags/compiled metadata while exact source remains authority.
Failure: repeat expensive broad search for already-known source routing.

## AOR-017 — Voice bounded
Given a seeded adventure is active during Live Voice.
Expected: preload only relevant current scenario state/source objects/locators.
Failure: preload entire magazine/module library or mine new adventures continuously in Voice.

## AOR-018 — No plot protection
Given a legitimate scenario consequence could kill Wren or close an opportunity.
Expected: adjudicate causally under governing rules; no fudging to preserve the scenario.
Failure: alter outcomes so a planned/published story can continue.

## AOR-019 — High danger is telegraphed when causally visible
Given level-1 Wren approaches a scenario intended for exceptionally powerful characters and the surrounding world would plausibly bear evidence of its danger.
Expected: present player-discoverable in-world warning evidence such as aftermath, credible reports, monster signs, devastation, defenses, magical residue, or similar causal signals.
Failure: conceal obvious danger merely to surprise the player, or present only a metagame level warning.

## AOR-020 — Warning is not a level gate
Given Wren has received credible evidence that a site is catastrophically dangerous and Hiram chooses to enter anyway.
Expected: allow the declared action and adjudicate normally under AD&D 2e/world causality.
Failure: lock the entrance, refuse the action, relocate the site, downscale it, or otherwise prevent entry solely because Wren is underleveled.

## AOR-021 — No guaranteed warning where none exists
Given a lethal danger is genuinely hidden, newly arrived, deceptive, isolated, or otherwise lacks plausible warning channels.
Expected: do not fabricate a convenient safety warning solely to protect Wren.
Failure: guarantee danger telegraphing regardless of world causality.

## AOR-022 — No repetitive paternal warning
Given Hiram understands an established player-known risk and explicitly proceeds.
Expected: stop repeating the same unchanged warning; surface only new evidence or materially changed circumstances.
Failure: repeatedly interrupt play to discourage the choice.

## AOR-023 — Warning stays in-world
Given a dangerous scenario has a source-stated or DM-understood risk far above Wren.
Expected: translate relevant risk into observable evidence and credible in-world knowledge when available.
Failure: tell Hiram "this is a level 20 dungeon" as the ordinary warning mechanism.

## AOR-024 — Retreat remains real play
Given Wren enters a dangerous site, learns more, and retreats without resolving it.
Expected: retreat is legitimate; preserve site/world consequences and allow later return if causality permits.
Failure: force continued progress because the adventure has begun or treat retreat as module failure requiring reset.

## AOR-025 — Original creation is first-class
Given campaign causality clearly implies a specific site/situation and no exact published source is governing it.
Expected: DM may create original material directly when that is the stronger, cleaner choice.
Failure: DM is prohibited from creating until a published-module search has been exhausted.

## AOR-026 — Reasonable published search can terminate
Given a targeted published search produces no strong low-surgery fit.
Expected: stop searching after a reasonable candidate pass and create original material rather than broad-scanning the library indefinitely.
Failure: source-library size becomes an adventure-preparation bottleneck.

## AOR-027 — Strong published fit wins naturally
Given a targeted search quickly finds a published scenario that fits active geography, tone, scope, and causal need with minimal surgery.
Expected: published material remains a strong first-class candidate and may be selected/seeded rather than defaulting automatically to invention.
Failure: original material is always preferred merely because improvisation is allowed.

## AOR-028 — Original scenario receives same persistence/world-motion discipline
Given an original scenario becomes consequential.
Expected: persist its established facts, actors, site changes, clocks, treasure movement, alarms, and consequences exactly as for published material.
Failure: original improvisation is treated as disposable/noncanonical scenery.

## AOR-029 — Compiled adventure metadata is fast path, not canon
Given source-knowledge objects contain verified Dungeon/module adventure metadata.
Expected: use them to shortlist candidates without reopening every PDF; exact source is retrieved only for surviving candidates/needed details, and metadata does not seed the adventure by itself.
Failure: broad source scan occurs despite adequate metadata, or compiled metadata becomes campaign truth automatically.
