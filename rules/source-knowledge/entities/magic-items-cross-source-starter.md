# Compiled Source Objects — Magic Item Cross-Source Starter Shard

Status: verified entry-level assertions from uploaded *Encyclopedia Magica* material. This shard demonstrates entity-centric item lookup plus provenance relationships to original published sources. It does not instantiate any item in Wren's campaign.

## Entity: Winged Mask

- entity_id: `adnd2e.magic-item.mask.winged`
- entity_type: `magic-item`
- canonical_name: `Winged Mask`
- aliases: `Mask, Winged`
- tags: `mask`, `flight`, `Dragon`, `Myth Drannor`

### Assertion: Ruins of Myth Drannor treatment
- assertion_id: `adnd2e.emag.v2.mask.winged.myth-drannor.v1`
- source_id: `adnd2e.document.encyclopedia-magica.v2`
- locator: `Mask -> Winged, Encyclopedia Magica Volume 2`
- original_source: `The Ruins of Myth Drannor`
- source_role: `magic-item-anthology-source`
- verification_status: `verified`
- source_text_required: `true` for exact interaction/adjudication beyond fields below
- xp_value: `750`
- gp_value: `7,500`
- structured_data:
  - flight: `at will`
  - maneuverability_class: `A`
  - movement: `Fl 24`
  - fatigue: `none from flight`
  - hover: `yes`
  - backward_flight: `yes`
  - intricate_tasks/spellcasting_in_flight: `permitted`
  - visible_effect: `soft white faerie fire while flying`
  - nonliving_carry_limit: `50 lb excluding mask`
  - additional_living_creature: `not supported; contact/grapple/carry causes wearer to fall`
  - fall_protection: `mask protects wearer with feather fall; not second creature`

### Assertion: Dragon Magazine 117 treatment
- assertion_id: `adnd2e.emag.v2.mask.winged.dragon117.v1`
- source_id: `adnd2e.document.encyclopedia-magica.v2`
- locator: `Mask -> Winged II, Encyclopedia Magica Volume 2`
- original_source: `Dragon Magazine 117`
- source_role: `magic-item-anthology-source with periodical provenance`
- verification_status: `verified`
- source_text_required: `true`
- xp_value: `1,200`
- gp_value: `12,000`
- structured_data:
  - flight: `at will`
  - maneuverability_class: `A`
  - movement: `up to 260 feet/round as stated in entry`
  - fatigue: `none from flight`
  - hover: `yes`
  - backward_flight: `yes`
  - intricate_tasks/spellcasting_in_flight: `permitted`
  - visible_effect: `soft white faerie fire while flying`
  - nonliving_carry_limit: `50 lb excluding mask`
  - additional_living_creature: `not supported; contact/grapple/carry causes wearer to fall`
  - fall_protection: `feather fall for wearer only`

relationships:
- `adnd2e.magic-item.mask.winged --HAS_ASSERTION_FROM--> The Ruins of Myth Drannor`
- `adnd2e.magic-item.mask.winged --HAS_ASSERTION_FROM--> Dragon Magazine 117`
- `adnd2e.emag.v2.mask.winged.dragon117.v1 --DERIVED_FROM--> Dragon Magazine 117`
- `adnd2e.emag.v2.mask.winged.myth-drannor.v1 --DERIVED_FROM--> The Ruins of Myth Drannor`

The two treatments are preserved as separate assertions rather than merged into one universal item definition.

## Entity family: Dragon Magazine 33 magical oils

- entity_id: `adnd2e.magic-item.oil.dragon33-family`
- entity_type: `magic-item-family`
- canonical_name: `Dragon Magazine 33 Magical Oils`
- source_id: `adnd2e.document.encyclopedia-magica.v2`
- original_source: `Dragon Magazine 33`
- locator: `Oil entries, Encyclopedia Magica Volume 2`
- verification_status: `verified`
- source_text_required: `true` for any entry not individually normalized below`

### Individually normalized assertions

- `Verbena`
  - assertion_id: `adnd2e.emag.v2.oil.verbena.dragon33.v1`
  - xp_value: `400`
  - gp_value: `1,200`
  - effect_summary: `protects user against curses and geas for 24 hours`

- `Oil of Vibration`
  - assertion_id: `adnd2e.emag.v2.oil.vibration.dragon33.v1`
  - xp_value: `300`
  - gp_value: `900`
  - effect_summary: `when applied to user and one victim, victim is charmed for 24 hours; application order matters`

- `Virgin Olive Oil`
  - assertion_id: `adnd2e.emag.v2.oil.virgin-olive.dragon33.v1`
  - xp_value: `100`
  - gp_value: `300`
  - effect_summary: `applied to priest holy symbol; +4 to turning roll and can damage undead on failed save; lasts 24 hours`

- `Oil of Vision`
  - assertion_id: `adnd2e.emag.v2.oil.vision.dragon33.v1`
  - xp_value: `900`
  - gp_value: `1,800`
  - effect_summary: `see invisible and ultraviolet for six turns`

- `Oil of Voodoo`
  - assertion_id: `adnd2e.emag.v2.oil.voodoo.dragon33.v1`
  - xp_value: `200`
  - gp_value: `600`
  - effect_summary: `thrown at enemy; failed save vs spell reduces Strength to 3`

- `Oil of Will Power`
  - assertion_id: `adnd2e.emag.v2.oil.will-power.dragon33.v1`
  - xp_value: `500`
  - gp_value: `1,500`
  - effect_summary: `raises Strength by 3 to max 18 and grants +3 to listed saving throw categories for 24 hours`

- `Wintergreen Oil`
  - assertion_id: `adnd2e.emag.v2.oil.wintergreen.dragon33.v1`
  - xp_value: `100`
  - gp_value: `300`
  - effect_summary: `heals 1d6 and grants +5 to saves vs disease/disease-mimicking effects except lycanthropy for 24 hours`

- `Oil of Wishing`
  - assertion_id: `adnd2e.emag.v2.oil.wishing.dragon33.v1`
  - xp_value: `900`
  - gp_value: `2,700`
  - effect_summary: `used with a candle and written wish; exact adjudication requires source text`
  - source_text_required: `true`

- `Witch's Oil`
  - assertion_id: `adnd2e.emag.v2.oil.witchs.dragon33.v1`
  - xp_value: `600`
  - gp_value: `1,800`
  - effect_summary: `hair-soaking curse; failed poison save causes death eight days later; evil-use/alignment caveat`
  - source_text_required: `true`

- `Xyz Oil`
  - assertion_id: `adnd2e.emag.v2.oil.xyz.dragon33.v1`
  - xp_value: `300`
  - gp_value: `900`
  - effect_summary: `makes user 10 years younger; system shock failure kills; resurrection note applies`
  - source_text_required: `true`

- `Ylang Ylang Oil`
  - assertion_id: `adnd2e.emag.v2.oil.ylang-ylang.dragon33.v1`
  - xp_value: `300`
  - gp_value: `900`
  - effect_summary: `Charisma +2 for 24 hours`

- `Zodiac Oil`
  - assertion_id: `adnd2e.emag.v2.oil.zodiac.dragon33.v1`
  - xp_value: `100`
  - gp_value: `300`
  - effect_summary: `+2 to reaction rolls when speaking with followers of lawful deities`

relationships:
- each normalized oil assertion `--DERIVED_FROM--> Dragon Magazine 33`
- each normalized oil entity `--COLLECTED_IN--> Encyclopedia Magica Volume 2`

## Runtime consequence

When an item name/alias matches one of these entities, lookup can route directly to the compiled assertion, source provenance, and exact anthology locator. If the campaign later has the original Dragon issue or original setting product available, that source may be attached as an additional assertion without replacing the anthology assertion by default.
