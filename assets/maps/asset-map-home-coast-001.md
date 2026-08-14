# Asset: Wren’s Home Coast

- `asset_id`: `asset-map-home-coast-001`
- `type`: `map`
- `status`: `active`
- `visibility`: `player-known`
- `current_version`: `v2`
- `title`: `Wren’s Home Coast`

## Aliases

- Wren’s map
- Wren's Home Coast
- home coast map
- coastal map
- Lowcove map
- Lowcove coast map

## Linked campaign entities

Known map labels/entities include:

- Lowcove — Wren’s home village
- Bridgeford — inland market town
- Saltwick — harbor settlement
- Seabreeze Hamlet
- Pine Hollow Farms
- Looking Glass Cove
- Old Observatory
- Wren’s Home Coast / surrounding coastal region

Canonical entity truth remains in the appropriate state/location records. This asset record is a media-routing record and does not supersede those records.

## Relationships

- `MAP_OF` — Wren’s Home Coast region
- `DEPICTS` — Lowcove
- `DEPICTS` — Bridgeford
- `DEPICTS` — Saltwick
- `DEPICTS` — Seabreeze Hamlet
- `DEPICTS` — Pine Hollow Farms
- `DEPICTS` — Looking Glass Cove
- `DEPICTS` — Old Observatory
- `v2 SUPERSEDES v1`

## Version history

### v1 — Original map

- State: `historical`
- Description: Original player-facing map before canonical settlement names were applied.
- Superseded labels:
  - `My Village (Home)` → `Lowcove`
  - `Market Town` → `Bridgeford`
  - `Harbor Settlement` → `Saltwick`
- Payload path: `assets/maps/asset-map-home-coast-001/v1-original.jpeg`
- MIME type: `image/jpeg`
- Dimensions: `1536x1024`
- SHA-256: `cf66d881b5da7040831dba220ad7b7c27ad36c8f24f71ab3d0be7502a922bc72`
- Git blob SHA: `a786588ef8748885fe3e476d89a5c6e715bcf977`
- Payload state: `verified`

### v2 — Named-location map

- State: `current`
- Description: Updated player-facing map using the established settlement names Lowcove, Bridgeford, and Saltwick.
- Payload path: `assets/maps/asset-map-home-coast-001/v2-current.jpeg`
- MIME type: `image/jpeg`
- Dimensions: `1536x1024`
- SHA-256: `94411c14e64180567ff82a60a6f82daa167f0c8d9a75a515f7eecad846a503da`
- Git blob SHA: `fd1b7672999b0672c3a1280c38dc25b5e853d970`
- Payload state: `verified`

## Provenance

Both versions were generated in ChatGPT during the Wren campaign and were re-supplied by Hiram in the same Project chat on 2026-08-13 so they could be brought under durable asset management.

The exact original-generation prompt/history is not required for identity. The v1/v2 relationship and supplied-file hashes are the durable comparison anchors.

Both payloads were manually transported to canonical GitHub `main` and readback-verified on 2026-08-13.

## Retrieval behavior

Unless Hiram explicitly requests the old/original version, references such as “Wren’s map,” “the coastal map,” or “the Home Coast map” resolve to `v2`.

The binary payloads are durably retrievable from canonical GitHub storage and should be fetched through this asset record rather than depending on conversation history or requiring Hiram to re-upload them.
