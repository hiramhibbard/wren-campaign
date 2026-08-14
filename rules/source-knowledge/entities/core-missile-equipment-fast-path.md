# Compiled Source Objects — Core Missile Ranges / Common Equipment Fast Path

Status: verified structured assertions from uploaded AD&D 2e Player's Handbook. Uploaded source remains authoritative.

## Entity: Missile weapon range table

- entity_id: `adnd2e.rule.combat.missile.ranges-table45`
- entity_type: `rule`
- assertion_id: `adnd2e.phb.table45.missile-ranges.v1`
- source_id: `adnd2e.document.phb-deluxe`
- locator: `Chapter 6: Money and Equipment -> Table 45: Missile Weapon Ranges, printed p. 95`
- source_role: `core-rule-source`
- activation_requirement: `core-default; individual weapon availability remains campaign/setting dependent`
- verification_status: `verified`
- source_text_required: `true` for special weapon exceptions, unusual ammunition, or setting-specific replacements`

structured_data:
- units: `yards`
- rows:
  - `arquebus: ROF 1/3; short 50; medium 150; long 210`
  - `blowgun: ROF 2/1; short 10; medium 20; long 30`
  - `composite long bow + flight arrow: ROF 2/1; 60/120/210`
  - `composite long bow + sheaf arrow: ROF 2/1; 40/80/170`
  - `composite short bow: ROF 2/1; 50/100/180`
  - `longbow + flight arrow: ROF 2/1; 70/140/210`
  - `longbow + sheaf arrow: ROF 2/1; 50/100/170`
  - `short bow: ROF 2/1; 50/100/150`
  - `club: ROF 1; 10/20/30`
  - `hand crossbow: ROF 1; 20/40/60`
  - `heavy crossbow: ROF 1/2; 80/160/240`
  - `light crossbow: ROF 1; 60/120/180`
  - `dagger: ROF 2/1; 10/20/30`
  - `dart: ROF 3/1; 10/20/40`
  - `hammer: ROF 1; 10/20/30`
  - `hand axe: ROF 1; 10/20/30`
  - `harpoon: ROF 1; 10/20/30`
  - `javelin: ROF 1; 20/40/60`
  - `knife: ROF 2/1; 10/20/30`
  - `sling bullet: ROF 1; 50/100/200`
  - `sling stone: ROF 1; 40/80/160`
  - `spear: ROF 1; 10/20/30`
  - `staff sling bullet: ROF 2/1; short none; medium 30-60; long 90`
  - `staff sling stone: ROF 2/1; short none; medium 30-60; long 90`
- range_modifiers:
  - `short: 0`
  - `medium: -2 attack`
  - `long: -5 attack`
  - `arquebus if allowed: doubles range modifiers`
- semantics:
  - `ROF is shots per round and is independent of melee attacks/round`
  - `each category includes distances equal to or less than listed maximum`

## Entity: Weapon metadata semantics

- entity_id: `adnd2e.source-schema.weapon.phb`
- entity_type: `source-schema`
- assertion_id: `adnd2e.phb.weapon-fields.v1`
- source_id: `adnd2e.document.phb-deluxe`
- locator: `Chapter 6: Money and Equipment -> Weapons explanatory text immediately following Table 45`
- verification_status: `verified`
- source_text_required: `false` for field meaning; `true` for exact individual weapon row not already compiled`

structured_data:
- size:
  - `S: approximately 2 feet or less`
  - `M: approximately 2-5 feet`
  - `L: generally 6 feet or more`
  - `G/H: giant/huge, normally not ordinary PC-market equipment`
- wielding:
  - `weapon own size or smaller normally usable`
  - `one size larger generally requires two hands`
  - `larger than that normally unusable without special means`
- type:
  - `B = bludgeoning`
  - `P = piercing`
  - `S = slashing`
  - `type primarily matters when optional weapon-vs-armor rules are in use`
- speed_factor:
  - `lower is faster/easier to use`
  - `mechanically relevant only when the governing initiative procedure uses weapon speed`

## Entity: Wren-common PHB equipment lookup

- entity_id: `adnd2e.equipment.wren-common-phb`
- entity_type: `equipment-index`
- assertion_id: `adnd2e.phb.table44.wren-common-items.v1`
- source_id: `adnd2e.document.phb-deluxe`
- locator: `Table 44: Equipment, printed pp. 90-94`
- verification_status: `verified`
- source_text_required: `true` for items not listed below or ambiguous campaign-quality/availability questions`

structured_data:
- `knife: cost 5 sp; weight 1/2 lb`
- `small belt pouch: cost 7 sp; weight 1/2 lb`
- `backpack: cost 2 gp; weight 2 lb`
- `winter blanket: cost 5 sp; weight 3 lb`
- `flint and steel: cost 5 sp; listed weight negligible`
- `waterskin/wineskin: cost 8 sp; empty listed weight 1 lb`
- `large sack: cost 2 sp; weight 1/2 lb`
- `hemp rope 50 ft: cost 1 gp; weight 20 lb`
- `hooded lantern: cost 7 gp; weight 2 lb`
- `lamp oil one-pint flask: cost 6 cp; weight 1 lb`
- `quarterstaff: weight 4 lb; PHB table gives no purchase price`

notes:
- `This object is a lookup accelerator for common PHB equipment and does not alter Wren's canonical inventory.`
- `Campaign inventory remains governed by canonical state/checkpoints; this source object only supplies published cost/weight metadata.`

## Runtime routing

`missile declaration -> weapon/ammunition -> Table 45 range/ROF object -> range modifier -> exact weapon/source only if special case`

`ordinary equipment lookup -> common-item object if present -> exact PHB Table 44 or active setting equipment source if absent/overridden`

Setting-specific equipment sources may replace price, availability, material, damage, or other fields within their explicit scope; they are separate assertions rather than edits to this generic PHB object.