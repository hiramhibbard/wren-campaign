# Wren — Inventory, Funds, Encumbrance

Materialized from `Wren_Campaign_Ledger.md` without changing campaign facts.

## Funds
- Rolled wizard starting-equipment funds: 40 gp.
- Known priced starting equipment: 12 gp, 5 sp, 2 cp.
- Current/provisional purse: **27 gp, 4 sp, 8 cp**.
- Armor components have no assigned source-supported starting cost yet; reconcile later if a source/ruling establishes one.
- One day's opening food is a home provision.
- Spellbook, ordinary clothing, personal stone, inherited boat are background possessions not charged to the 40 gp budget.

## Normally carried / personal gear
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

## Normally stored aboard Wren's boat
- 50 ft hemp rope — 20 lb; 1 gp.
- Hooded lantern — 2 lb; 7 gp.
- Lamp oil — two one-pint flasks, 1 lb each, 6 cp each; 12 total hours of fuel at 6 hours/flask.

Items may move between carried and boat-stored inventory during play; ownership does not imply immediate access.

## Encumbrance
- Known normal carried baseline including clothing/quarterstaff but excluding variable/unlisted contents: **16.5 lb**.
- Boat-stored rope + lantern + oil: **24 lb**.
- STR 9 unencumbered through **35 lb** under the recorded PHB table.
- Current encumbrance category: **unencumbered**, subject to unresolved variable/unlisted contents remaining below the breakpoint.
- Current next encumbrance breakpoint cache: **35 lb maximum for unencumbered status**.
  - Cache status: `derived-recorded` from the governing PHB encumbrance table already used for this character state.
  - Fast-path trigger: whenever carried load changes, compare the best-supported carried total against 35 lb. A load of more than 35 lb crosses the current cached breakpoint and requires source-backed determination of the new category, consequences, and next relevant breakpoint.
  - Invalidate/recompute this cache if Strength changes, the governing encumbrance rule changes, an effect modifies carrying/encumbrance, or an integrity check finds uncertainty/mismatch.
- Do not falsely treat the 16.5 lb baseline as a precise total while spellbook weight, Armor-component weight/quantity, carried food, water contents, or other variable/unlisted contents remain unresolved. Resolve those only when consequential to a breakpoint or another rule.

## Boat
- Wren owns his late father's modest small coastal working boat.
- Treasured, weathered, nonmagical, suitable for solo fishing and local coastal travel.

## Inventory rulings
- Keep PHB-listed fixed weights exact; do not invent precision for unlisted/variable contents.
- Distinguish carried inventory from boat-stored gear.
- Any change to carried load must automatically run the encumbrance fast-path check defined in `state/rulings/dm-procedure-triggers.md`; Hiram does not need to request an encumbrance check.