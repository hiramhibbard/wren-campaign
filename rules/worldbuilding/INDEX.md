# Wren World-Building Source Registry

This registry routes original/unresolved campaign-world generation under `WORLD_BUILDER_RUNTIME_POLICY.md` and `SOURCE_KNOWLEDGE_LAYER_POLICY.md`.

## Active source

### World Builder's Guidebook
- source title: `World Builders Guidebook.pdf`
- product: TSR 9532
- system: AD&D 2nd Edition
- role: active DM world-generation procedure source for unresolved/original campaign space
- authority: subordinate to established Wren canon, active published setting/adventure sources, core mechanics, and explicit rulings
- default Wren use: microscopic/local campaign area expansion

High-value section locators:
- Introduction / DM's Notebook — source-role philosophy, minimum world components, progressive detail, campaign record categories
- Chapter One: Approaches — microscopic, macroscopic, sociological, character-based, situation-based, literary, historical
- Chapter Three: Continents and Geography — terrain/climate/water/human geography when larger geography becomes necessary
- Chapter Four: Kingdoms and Sociology — culture, government, physical cartography, population/resources
- Chapter Five: Cities and Provinces — Local Campaign Area, Cities/Towns/Villages, Monsters and Ecology, Sites of Interest
- Chapter Six: History and Mythology — progressive myth/history generation

## Runtime fast path

`unresolved consequential world detail -> existing verified compiled procedure/entity if available -> WORLD_BUILDER_RUNTIME_POLICY -> relevant chapter/domain or direct DM creation -> bounded generation -> campaign state if consequential`

Route specialist questions through `SUPPLEMENT_SOURCE_RESOLUTION_POLICY.md`, monster/ecology questions through monster policies, Dragon support through `DRAGON_MAGAZINE_SOURCE_POLICY.md`, and scenario/site opportunities through `ADVENTURE_OPPORTUNITY_POLICY.md`.

## Compiled source-object policy

Do not recreate the Guidebook as a second prose book.

However, broadly compile **reusable structured procedures, tables, categories, decision rules, tags, and locators** when that improves future generation speed or consistency. The compiled source layer may eventually cover much of the Guidebook's reusable machinery without copying its narrative prose.

Appropriate compiled objects include:
- generation approach definitions/routing metadata;
- settlement/local-area procedure steps;
- reusable population/resource/government categories;
- geography/terrain/climate generation tables;
- site-of-interest procedure metadata;
- history/mythology generation procedures;
- source relationships to specialist books/domains.

Complex explanatory/design prose should remain short summary + exact locator + `source_text_required` where nuance matters.

## Population strategy

Ordinary play: compile lazily after a correct reusable lookup.

Maintenance/offline work: batch-extract high-value World Builder procedure/table objects where doing so reduces repeated PDF scanning.

Do not let extraction itself generate Wren campaign facts. A world-building source object is reusable published machinery; campaign truth is created only when the runtime actually resolves/uses it for a consequential world need.
