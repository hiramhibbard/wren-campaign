# Pending Campaign Asset Ingest

This file tracks assets whose canonical metadata exists but whose binary payload is not yet durably present/readback-verified in the repository.

## `asset-map-home-coast-001` — Wren’s Home Coast

Status: `manual-binary-transport-required`

The current GitHub connector can write UTF-8 repository files but does not provide a safe contents-API binary-file write that advances `main` for these supplied JPEGs. The metadata and exact file hashes are already canonical.

### Required binary destinations

1. `assets/maps/asset-map-home-coast-001/v1-original.jpeg`
   - SHA-256: `cf66d881b5da7040831dba220ad7b7c27ad36c8f24f71ab3d0be7502a922bc72`
   - 1536x1024 JPEG
   - Original map with placeholder labels `My Village (Home)`, `Market Town`, and `Harbor Settlement`.

2. `assets/maps/asset-map-home-coast-001/v2-current.jpeg`
   - SHA-256: `94411c14e64180567ff82a60a6f82daa167f0c8d9a75a515f7eecad846a503da`
   - 1536x1024 JPEG
   - Current map with Lowcove, Bridgeford, and Saltwick.

### Completion rule

After both binaries are placed at the exact paths above:

1. retrieve/read back the files from canonical `main`;
2. verify file identity/hash where tooling permits;
3. update `assets/maps/asset-map-home-coast-001.md` payload states from `pending-ingest` to `verified`;
4. update asset status to `active`;
5. update `assets/maps/INDEX.md` and `assets/INDEX.md` integrity status;
6. remove this pending entry only after readback verification.

Do not tell Hiram the asset is fully saved/retrievable across chats until those steps succeed.
