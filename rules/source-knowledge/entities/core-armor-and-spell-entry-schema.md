# Compiled Source Objects — Core Armor Ratings and Spell Entry Schema

Status: verified structured assertions from uploaded AD&D 2e PHB. Uploaded source remains authoritative.

## Entity: Core armor class ratings

- entity_id: `adnd2e.rule.armor.class-ratings`
- entity_type: `rule`
- assertion_id: `adnd2e.phb.table46.armor-class-ratings.v1`
- source_id: `adnd2e.document.phb-deluxe`
- locator: `Chapter 6: Money and Equipment -> Table 46: Armor Class Ratings, printed p. 99`
- source_role: `core-rule-source`
- activation_requirement: `core-default, subject to class/source equipment restrictions and campaign availability`
- verification_status: `verified`
- source_text_required: `true` for shield facing/coverage, armor availability by era/setting, unusual armor, magical interaction, or detailed equipment properties`

structured_data:
- `none: AC 10`
- `shield only: AC 9`
- `leather or padded: AC 8`
- `leather/padded + shield OR studded leather OR ring mail: AC 7`
- `studded leather/ring mail + shield OR brigandine OR scale mail OR hide: AC 6`
- `scale/hide + shield OR chain mail: AC 5`
- `chain + shield OR splint OR banded OR bronze plate: AC 4`
- `splint/banded/bronze plate + shield OR plate mail: AC 3`
- `plate mail + shield OR field plate: AC 2`
- `field plate + shield OR full plate: AC 1`
- `full plate + shield: AC 0`

notes:
- `lower AC is better protection`
- `availability may depend on campaign era/locale`
- `shield details require exact source when facing/coverage matters`

## Source schema: AD&D spell-entry field semantics

- entity_id: `adnd2e.source-schema.spell-entry.phb`
- entity_type: `source-schema`
- assertion_id: `adnd2e.phb.spell-entry-fields.v1`
- source_id: `adnd2e.document.phb-deluxe`
- locator: `PHB magic/spell-description explanatory section preceding spell listings`
- source_role: `core-rule-source`
- verification_status: `verified`
- source_text_required: `true` for any interpretation beyond normalized field semantics`

structured_data:
- components:
  - `V = verbal`
  - `S = somatic`
  - `M = material`
  - `material components are expended when cast unless the spell says otherwise`
  - `priest holy symbols are not lost merely by casting`
- duration:
  - `instantaneous spells end immediately though results may persist`
  - `permanent duration lasts until negated by an applicable means`
  - `set-duration spells are tracked by player`
  - `variable-duration spells are normally secretly rolled/recorded by DM`
  - `dismissible spells require original caster within spell range and able to speak dismissal words`
- casting_time:
  - `numeric casting times matter when optional casting-time initiative rules are used`
  - `numeric casting time adds to initiative under that optional procedure`
  - `round-or-longer casting goes into effect at end of stated final round/turn`
- area_of_effect:
  - `records creatures/volume/dimensions/weight/etc. affected`
  - `shapeable areas have a minimum 10-foot dimension unless spell explicitly says otherwise`
  - `friend/enemy targeting is based on caster perception at cast time`

## Extraction use

Future PHB/Tome/Spell Compendium ingestion should normalize, when present:
- canonical name and aliases;
- class/list and spell level;
- school and/or sphere;
- range;
- components;
- duration;
- casting time;
- area of effect;
- saving throw;
- structured effect/lifecycle fields only where faithfully normalizable;
- exact source locator;
- activation/scope dependencies;
- `source_text_required` for nuanced targeting, stacking, exceptions, or interpretation.

This schema reduces inconsistent spell parsing across source families but does not make any optional spell system active.
