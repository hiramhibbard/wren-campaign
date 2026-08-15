# Wren Campaign-Local Adventure Inventory

Status: live routing index, partial population
Purpose: fast published-adventure discovery without broad File Library scans
Authority: metadata/routing only; exact uploaded source remains authority for adventure content

This file is campaign-local and may contain Wren/Hiram-specific File Library handles. It must never be copied into the shared engine or another campaign.

## Runtime rule

When a published adventure is requested or becomes a plausible opportunity:

`this inventory -> availability filter -> fit/risk ranking -> exact source retrieval for finalist`

Do not infer the whole source library from a small semantic-search result set. Do not use web discovery to enlarge the playable pool.

An entry with `status: available` has a verified campaign-local exact-source handle. An entry with `status: unknown` is metadata-known but its exact governing issue/module binding has not yet been verified. `unknown` candidates may receive one bounded local lookup before selection.

If a source belongs to a player-declared corpus but exact binding lookup fails, preserve `unknown`/binding-gap status rather than claiming Hiram lacks the source or immediately asking for re-upload.

## Declared source corpora

- corpus: `Dungeon Magazine — AD&D 2e-era run`
  - declaration: Hiram reports the full 2e Dungeon collection is present in his uploaded library.
  - binding state: individual issue handles not yet enumerated
  - routing status: declared-present / per-issue verification required before exact play
  - note: index individual adventures, not just magazine containers

- corpus: `other setting adventures`
  - declaration: Hiram reports several additional setting-specific adventures are present.
  - binding state: partial / not yet exhaustively enumerated
  - routing status: incremental indexing

## Verified exact-source adventure entries

### `adnd2e.ravenloft.howls-in-the-night`
- title: `Howls in the Night`
- source family: standalone-adventure-module
- setting: Ravenloft
- system: AD&D 2e
- source-stated levels: 3–5
- status: available
- local_ref: `file_00000000171882309de2c8b8fd301a32`
- product: TSR 9466
- metadata verification: exact source cover/introduction inspected
- content authority: exact local_ref

### `adnd2e.ravenloft.book-of-crypts.bride-of-mordenheim`
- title: `Bride of Mordenheim`
- container: `Book of Crypts`
- source family: adventure-collection-scenario
- setting: Ravenloft
- system: AD&D 2e
- source-stated levels: 2–4
- status: available
- local_ref: `file_00000000395481fba4cf764c6d0f77d3`
- product: TSR 9336 / RR2
- exact locator hint: Chapter I begins p. 4 of printed book
- metadata verification: exact source table of contents/setup inspected
- content authority: exact local_ref

## Dungeon Magazine low-level candidate metadata — issue binding unresolved

The following entries are useful **candidate metadata only**. Their level/issue data was verified from locally uploaded TSR/Dragon advertisements, but the exact Dungeon issue file handle has not yet been resolved in this inventory. Therefore each remains `status: unknown` until the governing Dungeon issue is retrieved successfully.

### Dungeon #59

#### `dungeon.issue.59.adventure.wedding-day`
- title: `Wedding Day`
- author: Paul Culotta
- source family: dungeon-magazine-adventure
- issue: Dungeon #59
- system: AD&D
- source-stated levels: 1–2
- status: unknown
- corpus expectation: declared-present
- metadata provenance local_ref: `file_00000000a8588230bada9fad986e1203`
- metadata note: Dragon #228 advertisement lists issue/adventure/levels
- exact-source binding: unresolved

#### `dungeon.issue.59.adventure.seeking-bloodsilver`
- title: `Seeking Bloodsilver`
- author: Christopher Perkins
- source family: dungeon-magazine-adventure
- setting: Birthright
- issue: Dungeon #59
- source-stated levels: 2–4
- status: unknown
- corpus expectation: declared-present
- metadata provenance local_ref: `file_00000000a8588230bada9fad986e1203`
- exact-source binding: unresolved

#### `dungeon.issue.59.adventure.the-mothers-curse`
- title: `The Mother's Curse`
- source family: dungeon-magazine-adventure
- issue: Dungeon #59
- source-stated levels: 3–5
- status: unknown
- corpus expectation: declared-present
- metadata provenance local_ref: `file_00000000a8588230bada9fad986e1203`
- exact-source binding: unresolved

### Dungeon #62

#### `dungeon.issue.62.adventure.wild-in-the-streets`
- title: `Wild in the Streets`
- author: Jason Peck
- source family: dungeon-magazine-adventure
- issue: Dungeon #62
- system: AD&D
- source-stated levels: 1–3
- status: unknown
- corpus expectation: declared-present
- metadata provenance local_ref: `file_00000000a51882308d8bc6cbb12e672b`
- alternate metadata provenance local_ref: `file_0000000052c4823088b32a1347e85dd8`
- exact-source binding: unresolved

#### `dungeon.issue.62.adventure.the-ghost-at-widder-smithers`
- title: `The Ghost at Widder Smithers`
- author: John Baichtal
- source family: dungeon-magazine-side-trek
- issue: Dungeon #62
- system: AD&D
- source-stated levels: 1–3
- status: unknown
- corpus expectation: declared-present
- metadata provenance local_ref: `file_00000000a51882308d8bc6cbb12e672b`
- exact-source binding: unresolved

#### `dungeon.issue.62.adventure.dragons-delve`
- title: `Dragon's Delve`
- author: Christopher Perkins
- source family: dungeon-magazine-adventure
- issue: Dungeon #62
- system: AD&D
- source-stated levels: 3–6
- status: unknown
- corpus expectation: declared-present
- metadata provenance local_ref: `file_00000000a51882308d8bc6cbb12e672b`
- exact-source binding: unresolved

### Dungeon #63

#### `dungeon.issue.63.adventure.invisible-stalker`
- title: `Invisible Stalker`
- author: Jonathan Richards
- source family: dungeon-magazine-side-trek
- issue: Dungeon #63
- system: AD&D
- source-stated levels: 1–2
- status: unknown
- corpus expectation: declared-present
- metadata provenance local_ref: `file_00000000a6b882309c07a2e40a49f546`
- exact-source binding: unresolved

## Immediate 1st-level routing candidates

For a level-1 PC, the inventory currently knows these low-level Dungeon candidates whose exact issue binding should be checked before any player-facing offer:
- `Wedding Day` — levels 1–2 — Dungeon #59 — unknown binding
- `Wild in the Streets` — levels 1–3 — Dungeon #62 — unknown binding
- `The Ghost at Widder Smithers` — levels 1–3 — Dungeon #62 — unknown binding
- `Invisible Stalker` — levels 1–2 — Dungeon #63 — unknown binding

These are **not yet playable merely because they are indexed**. Runtime should attempt one bounded local issue/title lookup and promote only a successfully retrieved governing Dungeon source to `available`.

## Incremental population queue

Priority next passes:
1. resolve actual local handles for Dungeon #59, #62, #63;
2. batch-index remaining low-level Dungeon adventures (especially source-stated ranges containing level 1);
3. enumerate Hiram's standalone/setting adventure modules and collections;
4. enrich candidates with setting/environment/scenario tags only from verified source metadata;
5. continue wider Dungeon issue/article extraction during source conversion/maintenance.

Absence from this partial index is never evidence that an adventure or source is absent from Hiram's library.
