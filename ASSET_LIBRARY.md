# Campaign Asset Library Policy

**Status:** Normative campaign operating policy.

## Purpose

Provide durable identities, metadata, version history, visibility, provenance, and retrieval routes for campaign media such as maps, portraits, handouts, diagrams, scene art, tokens, audio, and other persistent assets.

Campaign assets must not depend on chat history for discoverability.

## Core invariant

If an image or other media object becomes meaningful to campaign continuity, it should be registered with a stable asset identity and canonical metadata. The media binary and its metadata are distinct: metadata is canonical campaign state; the media file is durable payload addressed by that metadata.

A user should not have to re-upload an already-registered campaign asset merely because play moved to another chat.

## Asset classes

- **Source asset** — originates in published or user-provided source material.
- **Campaign asset** — created or uploaded specifically for the live campaign.
- **Derived asset** — transformed from another asset, such as an annotated map, player-safe map, crop, resized copy, fog-of-war view, or alternate presentation.

## Required metadata

Each registered asset should record, where applicable:

- stable `asset_id`;
- title;
- type;
- status;
- visibility classification;
- aliases/natural-language references;
- current version;
- version records;
- durable payload path/reference;
- payload hash/checksum;
- MIME type and dimensions/technical metadata when relevant;
- provenance;
- linked canonical entities;
- typed asset relationships;
- chronology/version notes when the asset changes because campaign knowledge or world state changes.

## Visibility

Asset visibility is structural and must follow the same knowledge-boundary discipline as textual campaign state.

Typical values include:

- `player-known`;
- `character-known:<id>`;
- `party-known`;
- `dm-only`;
- `source-restricted`.

A player-safe derivative may be linked to a DM-only source asset without exposing the source asset.

## Versioning

Do not silently overwrite historically meaningful media.

Use version records when an asset changes because of:

- new labels or discovered information;
- annotations;
- player knowledge progression;
- map/world changes;
- corrected errors;
- alternate visibility layers;
- regenerated art intended to supersede an earlier version.

A version may be marked `current`, `historical`, `superseded`, or `alternate`.

## Typed relationships

Useful relationships include:

- `MAP_OF`;
- `PORTRAIT_OF`;
- `DEPICTS`;
- `HANDOUT_FOR`;
- `DERIVED_FROM`;
- `SUPERSEDES`;
- `PLAYER_VERSION_OF`;
- `DM_VERSION_OF`;
- `CURRENT_ASSET_FOR`;
- `SOURCE_ASSET_FOR`.

Relationships are routing metadata and must not invent campaign facts.

## Retrieval behavior

When a user refers to a known map, portrait, handout, or other durable media object:

1. resolve aliases and linked entities through `assets/INDEX.md` and the relevant asset registry;
2. fetch the canonical asset record;
3. select the current or explicitly requested version;
4. enforce visibility;
5. retrieve the durable payload;
6. use the asset together with canonical campaign state for viewing, editing, comparison, or generation.

Do not conclude that an asset does not exist merely because it is absent from recent conversation context.

## Editing and generation

When modifying an existing campaign image:

- use the registered current/requested version as the edit source;
- preserve the prior version unless the change is purely technical and explicitly non-historical;
- create a new version record;
- record provenance and relationship to the prior version;
- update `current_version` only after the new payload and metadata are durably available.

## Storage model

### Current GitHub prototype

Use:

- `assets/INDEX.md` for top-level routing;
- type-specific indexes such as `assets/maps/INDEX.md`;
- one metadata record per significant asset;
- durable binary files under the asset hierarchy when connector/runtime transport supports binary repository writes.

If binary transport is unavailable, register the metadata and exact expected destination, mark payload state as `pending-ingest`, preserve a checksum of the supplied file, and explicitly tell Hiram what manual transport is required. Do not claim the asset is fully durable until payload readback succeeds.

### Future application

Store binary media in object storage and canonical metadata/relationships/version records in the campaign database. Derived thumbnails, embeddings, OCR, and previews remain rebuildable projections.

## Integrity

An asset is fully registered only when:

- metadata exists canonically;
- the referenced durable payload exists;
- payload identity/hash matches metadata when a hash is recorded;
- the asset is routed by the relevant index;
- current-version pointers resolve successfully.

Metadata-only registration with a missing payload is `pending-ingest`, not complete.
