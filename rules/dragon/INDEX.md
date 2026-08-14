# Wren Dragon Magazine Article Registry

This is an article-level routing registry for `DRAGON_MAGAZINE_SOURCE_POLICY.md` and the compiled source layer.

It does not activate Dragon rules and does not claim that every issue/article has already been cataloged.

## Article roles

- `dragon-setting-lore`
- `dragon-monster-ecology`
- `dragon-monster-mechanics`
- `dragon-race-culture`
- `dragon-class-profession`
- `dragon-religion-priesthood`
- `dragon-magic-spell`
- `dragon-magic-item-artifact`
- `dragon-npc-organization`
- `dragon-equipment-craft`
- `dragon-dm-procedure`
- `dragon-worldbuilding`
- `dragon-adventure-seed`
- `dragon-optional-rule`
- `dragon-inspiration`

## Lookup behavior

Prefer:

`current subject/domain -> active setting/scope -> compiled Dragon article/entity assertion if available -> targeted uploaded-file search if missing -> exact article -> role/authority classification -> compile reusable result when worthwhile`

Do not search by issue number alone unless the issue is already known to be relevant.

## Compiled article metadata

A Dragon article object may record under `SOURCE_KNOWLEDGE_SCHEMA.md`:
- stable article entity ID;
- issue/date;
- article title;
- author;
- page/source locator;
- edition/system;
- setting scope;
- article roles;
- subject/entity tags;
- authority/activation notes;
- conflict/supersession notes;
- relationships to monsters, spells, items, settings, organizations, adventures, procedures, etc.;
- verification/source fingerprint.

## Population strategy

During ordinary play, add/compile article records lazily when relevance or retrieval cost justifies it.

During maintenance/offline extraction, article-level metadata may be compiled in batches across available Dragon issues because metadata/entity routing is reusable and can materially improve cross-issue/cross-book discovery. Batch extraction still must preserve article scope and must not activate optional rules.

Do not reproduce whole article prose. Keep structured claims, short summaries, tags/relationships, and exact locators; mark nuance-heavy assertions `source_text_required`.

## Authority

The index/object layer is derived. Verified compiled assertions may be used when their scope is sufficient, but exact uploaded Dragon text remains the ultimate published source and is required for unverified/stale/exception-sensitive claims.

Absence from this registry is never evidence that the Dragon collection lacks relevant material.
