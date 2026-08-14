# Dragon Magazine Source Regression Scenarios

Engineering/audit tests only. They do not alter live campaign state.

## DMR-001 — Domain-triggered search
Given a consequential domain has an unresolved gap and Dragon is plausibly useful.
Expected: targeted Dragon article search occurs without Hiram naming Dragon.
Failure: Dragon is ignored unless explicitly requested.

## DMR-002 — No global magazine scans
Given ordinary play has no Dragon-relevant gap.
Expected: no Dragon search/preload.
Failure: scan issues every turn.

## DMR-003 — Article role classification
Given a Dragon article is retrieved.
Expected: classify setting scope, edition/system, role, authority, activation needs, and conflicts before use.
Failure: treat the whole magazine as one authority level.

## DMR-004 — Consultation is not activation
Given a Dragon kit/optional rule/spell/proficiency/mechanical article is relevant.
Expected: it may be considered, but remains inactive until properly adopted for scope.
Failure: silently enable it.

## DMR-005 — Setting article scoped correctly
Given an active published setting and a Dragon article explicitly supporting that setting.
Expected: use compatible scoped detail after checking supersession/conflicts.
Failure: either ignore useful setting support or treat it as universal generic canon.

## DMR-006 — Setting contamination blocked
Given a Mystara-specific Dragon article while generic/non-Mystara scope is active.
Expected: do not leak Mystara assumptions into unrelated play.
Failure: import setting-specific lore globally.

## DMR-007 — Ecology routing
Given a monster ecology question unresolved by governing 2e source.
Expected: relevant Dragon ecology is considered before modern fan ecology inspiration.
Failure: skip contemporaneous Dragon ecology or let it override governing monster facts.

## DMR-008 — Ecology mechanics protected
Given a Dragon ecology article proposes conflicting/new monster mechanics.
Expected: use compatible ecology ideas only unless mechanics are explicitly adopted.
Failure: silently alter stat block/abilities.

## DMR-009 — Religion mechanics protected
Given a Dragon deity/priesthood article includes specialty-priest mechanics.
Expected: lore/institution material may be useful; player-facing mechanics remain activation-sensitive.
Failure: silently grant/change priest abilities.

## DMR-010 — Magic source precedence
Given a Dragon spell/item article conflicts with an authoritative named spell/item source.
Expected: governing source wins unless a scoped variant is explicitly adopted.
Failure: Dragon silently replaces core/source mechanics.

## DMR-011 — NPC/organization candidate status
Given a useful Dragon guild/villain/organization article is found.
Expected: use as candidate/adaptation material; it becomes Wren canon only when deliberately seeded/resolved.
Failure: retrieval alone makes it exist in the world.

## DMR-012 — World Builder handoff
Given unresolved worldbuilding has a matching Dragon culture/environment/DM article.
Expected: Dragon may enrich the bounded generation while established/source constraints remain primary.
Failure: article drives unconstrained world rewriting.

## DMR-013 — Adventure component use
Given an adventure opportunity needs a compact villain/item/location/seed and Dragon has a strong article.
Expected: Dragon may supply components while full adventure routing remains under adventure policy.
Failure: either ignore Dragon components or mistake every seed for a full mandatory scenario.

## DMR-014 — Original improvisation preserved
Given no Dragon article is needed for a bounded original creative decision.
Expected: DM may improvise from canonical constraints without searching Dragon.
Failure: magazine search becomes a creativity gate.

## DMR-015 — Lazy indexing
Given a Dragon article proves repeatedly useful.
Expected: preserve lightweight article metadata/locator.
Failure: repeatedly rediscover it from scratch or pre-index every issue before use.

## DMR-016 — Exact source remains authority
Given an index entry summarizes an article but exact mechanics/lore become consequential.
Expected: retrieve exact uploaded article text.
Failure: derived metadata is treated as authoritative content.

## DMR-017 — Voice bounded
Given Dragon-derived facts are immediately relevant in Voice.
Expected: preload only resolved facts/compact locators; defer exact missing source lookup.
Failure: load whole issues or guess article text.

## DMR-018 — No retroactive canonization
Given a Dragon idea was considered but never seeded.
Expected: it remains non-canon.
Failure: later play assumes it was established merely because it was previously researched.
