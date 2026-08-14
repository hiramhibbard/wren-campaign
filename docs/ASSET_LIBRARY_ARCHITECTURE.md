# Campaign Asset Library & Media Provenance

**Status:** Product / engineering roadmap module. Not campaign canon.  
**Parent roadmap:** `docs/APPLICATION_ROADMAP.md`

## Goal

Make maps, portraits, handouts, diagrams, scene art, tokens, audio, and other campaign media durable, retrievable, versioned, permission-aware objects instead of ephemeral chat attachments.

## Product requirement

A user who created or uploaded a meaningful campaign image once should be able to refer to it naturally months later without re-uploading it.

Examples:

- “Show me Wren’s map.”
- “Update the coastal map.”
- “Use the player-safe dungeon map.”
- “Give Edric the newer portrait.”
- “Compare the old and current map.”

## Architecture

```text
Campaign Asset Library
        |
        +-- canonical metadata / identity / permissions / relationships
        |
        +-- durable object payloads
        |
        +-- rebuildable previews / thumbnails / embeddings / OCR
        |
        +-- Context Compiler / retrieval router
```

Use object storage for binary payloads in the standalone application, with database records for asset identity, version history, provenance, relationships, visibility, hashes, and lifecycle state.

## Asset model

Suggested fields:

- `asset_id`
- `campaign_id`
- `title`
- `type`
- `status`
- `visibility`
- `current_version_id`
- aliases
- linked entity IDs
- typed relationships
- provenance
- source asset reference where relevant
- timestamps

Version records should include:

- `version_id`
- parent/prior version
- storage object key
- content hash
- MIME type
- dimensions/technical metadata
- created-by actor/tool
- change reason
- visibility
- state (`current`, `historical`, `alternate`, `superseded`)

## First-class relationships

Support at least:

- `MAP_OF`
- `PORTRAIT_OF`
- `DEPICTS`
- `HANDOUT_FOR`
- `DERIVED_FROM`
- `SUPERSEDES`
- `PLAYER_VERSION_OF`
- `DM_VERSION_OF`
- `CURRENT_ASSET_FOR`

These should integrate with the same stable entity-ID and relation architecture used by the campaign engine.

## Source assets vs campaign assets

Keep published/source media distinct from campaign-created derivatives.

Example:

`Published dungeon map -> campaign dungeon instance -> DM campaign map -> player-safe discovered map -> annotated player map`

This preserves provenance and avoids modifying protected source material when a campaign-specific derivative changes.

## Retrieval

Asset retrieval should use the same authority hierarchy as textual campaign retrieval:

1. direct stable ID;
2. alias/title lookup;
3. linked entity relationships;
4. structured filters (type, region, visibility, recency);
5. full-text metadata search;
6. semantic retrieval if needed;
7. canonical asset record fetch;
8. durable payload fetch.

Semantic search may suggest an asset candidate but cannot decide which version is authoritative.

## Context Compiler integration

The Context Compiler should include asset metadata or payloads only when relevant to the task.

Examples:

- map editing loads the exact requested/current image plus linked location state;
- NPC portrait generation loads current portrait plus canonical appearance description;
- play narration normally gets only compact metadata, not every image payload;
- Voice may prefetch likely nearby maps/handouts to reduce latency.

## Visibility and multiplayer

Visibility must be enforced before payload retrieval. This becomes critical for multiplayer and DM/player map variants.

A player client should never receive a DM-only payload merely because the model promises not to mention secret features.

## Versioning UX

Users should be able to:

- see current version;
- browse prior versions;
- restore/supersede explicitly;
- compare versions;
- create annotations/derivatives;
- understand why a version changed;
- distinguish a changed world map from a changed player-knowledge map.

## Storage lifecycle

Potential future lifecycle states:

- uploaded/generated;
- validating;
- active;
- superseded;
- archived;
- deleted/tombstoned.

Keep logical deletion/audit semantics separate from object-storage garbage collection.

## Cost/scale

Track media costs separately from inference:

- original storage;
- derived thumbnails/previews;
- bandwidth;
- image-generation/editing inference;
- OCR/embedding/index processing.

Large original files should not be injected into model context unnecessarily.

## Security and licensing

Design for:

- tenant/campaign isolation;
- signed/authorized object retrieval;
- DM/player access control;
- source-book licensing/provenance;
- malware/file validation for uploads;
- deletion/export rights;
- prompt-injection isolation for text extracted from images/documents.

## Near-term Wren prototype

Use the GitHub-backed `assets/` hierarchy governed by `ASSET_LIBRARY.md`.

The first concrete test asset is Wren’s Home Coast map, with original and renamed versions. The test should validate:

- stable asset identity;
- alias retrieval;
- linked location resolution;
- version preservation;
- current-version selection;
- payload integrity;
- cross-chat retrieval without re-upload.

This is a real observed failure mode from Wren play and should therefore be treated as evidence-driven work rather than speculative scope.
