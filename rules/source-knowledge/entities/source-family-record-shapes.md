# Compiled Source Objects — Monster / Magic-Item Record Shapes

Status: verified source-family structural metadata. These objects describe how major AD&D 2e reference works organize reusable entries; they do not instantiate campaign facts and do not substitute for entry-specific verification.

## Entity: Monstrous Compendium Annual entry schema

- entity_id: `adnd2e.source-schema.monster-entry.mca`
- entity_type: `source-schema`
- assertion_id: `adnd2e.mca3.how-to-use.entry-fields.v1`
- source_id: `adnd2e.document.monstrous-compendium-annual.v3`
- locator: `How to Use This Book, introductory pages`
- source_role: `monster-anthology-source`
- verification_status: `verified`
- source_text_required: `false` for field routing; `true` for exact entry values/definitions beyond compiled fields

structured_data:
- reusable_fields:
  - `climate-terrain`
  - `frequency`
  - `organization`
  - `activity-cycle`
  - `diet`
  - `intelligence`
  - `treasure`
  - `alignment`
  - `number-appearing`
  - `armor-class`
  - `movement`
  - `hit-dice`
  - `thac0`
  - `number-of-attacks`
  - `damage-per-attack`
  - `special-attacks`
  - `special-defenses`
  - `magic-resistance`
  - `size`
  - `morale`
  - `xp-value`
  - `combat`
  - `habitat-society`
  - `ecology`
- scope_warning: `Annual entries derive from many settings/products; even where adapted for broad use, distinctive setting-origin assumptions may remain and must be preserved as scoped assertions rather than flattened into generic truth.`
- index_relationships:
  - `primary-name`
  - `subentry/variant`
  - `alternative-name/aka`
  - `see/see-also`
  - `annual-volume/page locator`
  - `Monstrous Manual locator where applicable`

## Entity: Encyclopedia Magica item entry schema

- entity_id: `adnd2e.source-schema.magic-item.encyclopedia-magica`
- entity_type: `source-schema`
- assertion_id: `adnd2e.emag.v1.how-to-use.entry-fields.v1`
- source_id: `adnd2e.document.encyclopedia-magica.v1`
- locator: `How to Use These Books, introductory pages`
- source_role: `magic-item-anthology-source`
- verification_status: `verified`
- source_text_required: `false` for routing metadata; `true` for exact item powers/limitations unless that item assertion is separately compiled and verified`

structured_data:
- reusable_fields:
  - `item-name`
  - `item-type/group heading`
  - `xp-value`
  - `gp-value`
  - `source/provenance`
  - `detailed-description-locator`
  - `aliases/name-normalization`
  - `random-table membership where present`
  - `artifact/relic status where applicable`
- anthology_behavior:
  - `related items may be grouped under broad headings (e.g. swords) for findability`
  - `names may be normalized from earlier editions/product lines`
  - `source provenance must be retained so scope/version conflicts can be resolved`
- campaign_constraint: `compilation or anthology inclusion never means an item exists in Wren's campaign world`

## Ingestion consequence

Bulk extraction pipelines should use these source-native shapes rather than inventing a new lossy schema:

`entry -> stable entity -> one assertion per source/scope -> normalized structured fields -> exact locator -> typed relationships -> verification flags`

For monsters, habitat/society/ecology are first-class fields rather than decorative prose. For magic items, source provenance and aliases are first-class fields rather than cleanup metadata.
