# Compiled Source Objects — Tome of Magic First-Level Starter Shard

Status: verified structured spell assertions from uploaded `DD2_TomeofMagic.pdf`. Tome availability does not itself activate optional subsystems such as wild magic or expanded priest spheres.

Source document: `adnd2e.document.tome-of-magic`.

## Wizard 1st-level spells

### Conjure Spell Component
- entity_id: `adnd2e.spell.wizard.conjure-spell-component`
- assertion_id: `adnd2e.tome.wizard1.conjure-spell-component.v1`
- school: `Conjuration/Summoning`
- range: `1 mile/level`
- components: `V, S`
- duration: `1 round`
- casting_time: `1`
- area_of_effect: `3 components/level`
- saving_throw: `None`
- locator: `Chapter 2: Wizard Spells -> First-Level Spells -> Conjure Spell Component`
- verification_status: `verified`
- source_text_required: `true`
- effect_summary: `teleports naturally occurring, locally available, low-value spell components the wizard knows to the caster; restrictions apply to depth, value, alteration/manufacture, possession, and animal body parts.`

### Fire Burst
- entity_id: `adnd2e.spell.wizard.fire-burst`
- assertion_id: `adnd2e.tome.wizard1.fire-burst.v1`
- school: `Alteration, Evocation`
- range: `5 yards/level`
- components: `V, S`
- duration: `Instantaneous`
- casting_time: `1`
- area_of_effect: `10-foot-radius circle around a nonmagical fire source`
- saving_throw: `Negates`
- locator: `Chapter 2: Wizard Spells -> First-Level Spells -> Fire Burst`
- verification_status: `verified`
- source_text_required: `false` for ordinary use; `true` for unusual fire-source qualification`
- effect_summary: `causes a nonmagical fire source to flare; creatures within 10 feet suffer 1 hp/caster level, max 10, negated by save.`

### Fist of Stone
- entity_id: `adnd2e.spell.wizard.fist-of-stone`
- assertion_id: `adnd2e.tome.wizard1.fist-of-stone.v1`
- school: `Alteration`
- range: `0`
- components: `V, S`
- duration: `1 round/level`
- casting_time: `1`
- area_of_effect: `caster's hand`
- saving_throw: `None`
- locator: `Chapter 2: Wizard Spells -> First-Level Spells -> Fist of Stone`
- verification_status: `verified`
- source_text_required: `true`
- effect_summary: `one hand becomes stone and can strike/crush as Strength 18/00 for fist use; while active the wizard cannot cast spells requiring somatic components.`

### Lasting Breath
- entity_id: `adnd2e.spell.wizard.lasting-breath`
- assertion_id: `adnd2e.tome.wizard1.lasting-breath.v1`
- school: `Alteration`
- range: `5 yards/level`
- components: `V, S`
- duration: `1d4 rounds + 1 round/level`
- casting_time: `1`
- area_of_effect: `1 creature/level`
- saving_throw: `None`
- locator: `Chapter 2: Wizard Spells -> First-Level Spells -> Lasting Breath`
- verification_status: `verified`
- source_text_required: `true` for full interaction with breath-holding rules`
- effect_summary: `extends time a character can hold breath; variable duration is secretly determined and recipient does not know exact endpoint.`

### Metamorphose Liquids
- entity_id: `adnd2e.spell.wizard.metamorphose-liquids`
- assertion_id: `adnd2e.tome.wizard1.metamorphose-liquids.v1`
- school: `Alteration`
- range: `Touch`
- components: `V, S, M`
- duration: `Permanent`
- casting_time: `1 round`
- area_of_effect: `1-foot cube/level`
- saving_throw: `Special`
- locator: `Chapter 2: Wizard Spells -> First-Level Spells -> Metamorphose Liquids`
- verification_status: `verified`
- source_text_required: `true`
- effect_summary: `transmutes one liquid into equal amount of another nonmagical liquid; magical liquids and elemental-water creatures have special resistance/damage rules; cannot create magical liquid.`

### Murdock's Feathery Flyer
- entity_id: `adnd2e.spell.wizard.murdocks-feathery-flyer`
- assertion_id: `adnd2e.tome.wizard1.murdocks-feathery-flyer.v1`
- school: `Alteration`
- range: `0`
- components: `V, S, M`
- duration: `1 round/level`
- casting_time: `1`
- area_of_effect: `caster`
- saving_throw: `None`
- locator: `Chapter 2: Wizard Spells -> First-Level Spells -> Murdock's Feathery Flyer`
- verification_status: `verified`
- source_text_required: `true`
- effect_summary: `creates feathered membranes for flight; weight/load and expiration/falling details require exact entry.`

### Nahal's Reckless Dweomer
- entity_id: `adnd2e.spell.wizard.nahals-reckless-dweomer`
- assertion_id: `adnd2e.tome.wizard1.nahals-reckless-dweomer.v1`
- school: `Invocation/Evocation`
- range: `Special`
- components: `V, S`
- duration: `Special`
- casting_time: `5`
- area_of_effect: `Special`
- saving_throw: `Special`
- locator: `Chapter 2: Wizard Spells -> First-Level Spells -> Nahal's Reckless Dweomer`
- activation_requirement: `wild-mage/wild-magic subsystem must govern caster/case`
- verification_status: `verified`
- source_text_required: `true`
- effect_summary: `wild-mage last-resort attempt to shape a released wild surge into a declared spell effect; outcome depends on Wild Surge table and caster level.`

### Patternweave
- entity_id: `adnd2e.spell.wizard.patternweave`
- assertion_id: `adnd2e.tome.wizard1.patternweave.v1`
- school: `Divination`
- range: `10 yards`
- components: `V, S, M`
- duration: `1 round`
- casting_time: `3`
- area_of_effect: `10-foot square`
- saving_throw: `Special`
- locator: `Chapter 2: Wizard Spells -> First-Level Spells -> Patternweave`
- verification_status: `verified`
- source_text_required: `true`
- effect_summary: `reveals patterns in tangible apparent chaos such as shards, trails, or parts; uses secret save checks for pattern recognition and reconstruction.`

## Priest 1st-level spells

### Know Time
- entity_id: `adnd2e.spell.priest.know-time`
- assertion_id: `adnd2e.tome.priest1.know-time.v1`
- sphere: `Time`
- range: `0`
- components: `V, S`
- duration: `Instantaneous`
- casting_time: `1`
- area_of_effect: `caster`
- saving_throw: `None`
- locator: `Chapter 3: Priest Spells -> First-Level Spells -> Know Time`
- verification_status: `verified`
- source_text_required: `false`
- effect_summary: `caster knows precise current time and calendar date to nearest minute.`

### Log of Everburning
- entity_id: `adnd2e.spell.priest.log-of-everburning`
- assertion_id: `adnd2e.tome.priest1.log-of-everburning.v1`
- sphere: `Elemental Fire, Plant`
- range: `Touch`
- components: `V, S`
- duration: `1 hour/level`
- casting_time: `1`
- area_of_effect: `up to 1 cubic foot wood/level`
- saving_throw: `None`
- locator: `Chapter 3: Priest Spells -> First-Level Spells -> Log of Everburning`
- verification_status: `verified`
- source_text_required: `false` for ordinary use
- effect_summary: `enchanted wood burns brightly without being consumed for duration and gives twice normal heat; must still be ignited normally and crumbles to ash afterward; works on torches.`

### Mistaken Missive
- entity_id: `adnd2e.spell.priest.mistaken-missive`
- assertion_id: `adnd2e.tome.priest1.mistaken-missive.v1`
- sphere: `Chaos`
- range: `Touch`
- components: `V, S, M`
- duration: `Permanent`
- casting_time: `1`
- area_of_effect: `1 page/level`
- saving_throw: `None`
- locator: `Chapter 3: Priest Spells -> First-Level Spells -> Mistaken Missive`
- verification_status: `verified`
- source_text_required: `true`
- effect_summary: `progressively alters ink over six days until a coherent message contrary to original intent forms; spellbook/scroll interactions have special false-formula behavior.`

### Sacred Guardian
- entity_id: `adnd2e.spell.priest.sacred-guardian`
- assertion_id: `adnd2e.tome.priest1.sacred-guardian.v1`
- school: `Enchantment/Charm`
- sphere: `Guardian`
- range: `Touch`
- components: `V, S, M`
- duration: `1 day/level`
- casting_time: `1`
- area_of_effect: `creature touched`
- saving_throw: `None`
- locator: `Chapter 3: Priest Spells -> First-Level Spells -> Sacred Guardian`
- verification_status: `verified`
- source_text_required: `false` for ordinary use
- effect_summary: `alerts priest when recipient is in danger regardless of distance; at priest level 3+ provides a mental image of situation but not location.`

### Speak With Astral Traveler
- entity_id: `adnd2e.spell.priest.speak-with-astral-traveler`
- assertion_id: `adnd2e.tome.priest1.speak-with-astral-traveler.v1`
- school: `Alteration`
- sphere: `Astral`
- range: `Touch`
- components: `V, S`
- duration: `1 round/level`
- casting_time: `1 round`
- area_of_effect: `one creature`
- saving_throw: `None`
- locator: `Chapter 3: Priest Spells -> First-Level Spells -> Speak With Astral Traveler`
- verification_status: `verified`
- source_text_required: `false` for ordinary use
- effect_summary: `allows mental conversation with a creature whose astral body is away while its physical body is in suspended animation.`

### Thought Capture
- entity_id: `adnd2e.spell.priest.thought-capture`
- assertion_id: `adnd2e.tome.priest1.thought-capture.v1`
- school: `Divination`
- sphere: `Thought`
- range: `0`
- components: `V, S`
- duration: `Instantaneous`
- casting_time: `3`
- area_of_effect: `10 yards`
- saving_throw: `None`
- locator: `Chapter 3: Priest Spells -> First-Level Spells -> Thought Capture`
- verification_status: `verified`
- source_text_required: `true`
- effect_summary: `detects/captures residual freestanding thoughts under the source's Thought-sphere theory; exact selection/content mechanics require source text.`

## Relationship / activation notes

- Each spell `--COLLECTED_IN--> Tome of Magic`.
- Wild-magic-tagged spells remain inactive unless the relevant wild-magic source scope is explicitly active.
- Priest sphere membership is source metadata, not automatic access for every priest.
- Setting-specific sources may include, exclude, or remap Tome spells; those are separate scoped assertions rather than edits to these generic Tome assertions.

## Runtime use

When a Tome spell becomes relevant:
`spell entity -> active class/sphere/system scope -> verified assertion -> exact source only if source_text_required or interaction-sensitive`
