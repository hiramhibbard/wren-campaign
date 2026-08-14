# AD&D 2e Campaign Rulings and Unresolved Checks

## Established campaign rulings
- Basic fish preparation: Wren may clean and cook a simple fish meal without Cooking NWP; Cooking represents accomplished cooking rather than basic food preparation.
- Equipment bookkeeping: keep PHB-listed fixed weights exact; do not invent false precision for unlisted or variable contents; adjudicate when thresholds matter.
- Inventory locality: carried inventory and boat-stored gear are distinct.
- Starting-budget treatment: background possessions, witch-provided spellbook, personal stone, inherited boat, and one day's home food are not charged against the 40 gp starting equipment budget.

## Derived state, cache, and trigger policy
- Frequently consulted values may be persisted as verified derived runtime state when doing so avoids repeated source lookups or repeated deterministic calculation during ordinary play.
- Governing published/source rules plus the canonical facts they operate on remain authoritative. A cached derived value is an accelerator, not a replacement source of truth.
- Every persisted derived value should have identifiable dependencies and, when useful, provenance sufficient to reconstruct or audit it.
- Ordinary play should use a valid cache directly. Reconsult the governing source only when a dependency changes, the cache is missing/stale/uncertain, a trigger boundary is crossed and new derived state must be established, or an integrity audit finds a mismatch.
- When a dependency changes, invalidate or refresh only the derived values that actually depend on it rather than broadly rereading unrelated rules.
- If cached derived state conflicts with governing source material, the source wins and the cache must be corrected before consequential adjudication continues.
- Threshold/event caches should be checked automatically whenever their relevant input changes. Hiram should not need to remind the DM that a threshold, depletion point, expiry condition, or other registered trigger has been reached.
- Do not cache a value merely because it can be calculated. Cache values that are repeatedly consulted, expensive or error-prone to reconstruct, useful as trigger boundaries, or important for reliable runtime behavior.
- Pure display conveniences that are trivial to calculate from already-loaded values, such as `XP to next level`, normally remain computed on demand unless a future implementation has a concrete reason to persist them.

### Typical dependency examples
- XP changes -> compare against cached next-level threshold.
- Carried-load changes or Strength/encumbrance-rule changes -> refresh/check encumbrance state and relevant breakpoint.
- Equipment, ability, level, condition, or effect changes -> refresh only affected derived combat/movement/save/spell values.
- Resource use or elapsed consumption -> decrement canonical resource quantity and evaluate registered depletion/exhaustion triggers.
- Active-effect-relevant time/events/damage/conditions/removal procedures -> evaluate only the termination triggers that actually govern that effect.

## XP award policy
- Published AD&D 2e XP rules and applicable setting/class/source rules are authoritative. This campaign does not use a custom XP economy unless one is later explicitly established.
- The DM must evaluate XP automatically at meaningful encounter or objective resolution and again at session end. Hiram does not need to ask whether Wren earned XP.
- Consider every applicable published award category, including monster/group awards, story or objective awards, and class/individual awards when supported by the governing sources.
- Do not award XP merely for elapsed play time, routine competence, or actions that do not qualify under the applicable published rules.
- When the amount, category, eligibility, or timing of an XP award is consequential or uncertain, retrieve the relevant uploaded AD&D 2e source before applying it rather than relying on remembered rules.
- For each award, record enough canonical information to preserve the basis of the award, the raw XP awarded, any verified applicable adjustment or bonus, and Wren's resulting cumulative XP.
- XP changes are durable campaign state and must be included in the next checkpoint. Never retroactively invent an XP award without canonical evidence of the qualifying event.

## Advancement threshold cache policy
- Each advancing character may persist a `next-level XP threshold` as a verified derived runtime value so routine XP awards do not require rereading the class advancement table every time.
- The governing published/source advancement rule remains authoritative. The cached threshold is valid only while the character's class/advancement track, current level, and all rules that modify advancement requirements remain unchanged.
- After every XP change, compare the resulting cumulative XP against the cached threshold. This comparison is the normal fast-path level-up trigger.
- Recompute and verify the threshold from the governing uploaded source when the character gains a level, changes class/advancement track, becomes subject to a rule that changes XP requirements, or an integrity/maintenance audit detects uncertainty or mismatch.
- If the cached value conflicts with the governing source, the source wins. Correct the cache before resolving advancement consequences.
- `XP to next level` is normally computed on demand from `next-level XP threshold - current XP`; it need not be persisted unless a future implementation has a concrete reason to cache it.
- Persist enough provenance with the threshold to identify the source/table or rule from which it was derived. Avoid untraceable "mystery numbers."
- Wren's current mage level-1 next-level threshold is 2,500 XP, verified from the uploaded AD&D 2e Player's Handbook, Table 20: Wizard Experience Levels.

## Unresolved / source-check required
- Optional maximum-spells-per-level rule remains unresolved.
- Prime-requisite XP bonus was recorded as +10% but must be verified against the PHB when first applied.
- Exact Armor spell components/effects/duration must be retrieved from the uploaded AD&D 2e PHB when consequential.
- Exact Armor component cost/quantity/weight is unassigned; do not invent it. Current purse remains provisional only in the narrow sense that a later source-supported component cost may require reconciliation.

Exact published rules and tables remain governed by Hiram's uploaded AD&D 2e sources rather than this summary.