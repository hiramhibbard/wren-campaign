# Wren Campaign Instance

```yaml
campaign:
  id: wren
  name: Wren
  repository: hiramhibbard/wren-campaign
  branch: main
  root_manifest: Wren_Campaign_Ledger.md

player:
  name: Hiram

engine:
  repository: hiramhibbard/adnd2e-campaign-engine
  schema: 1
  version: portable-v1.2.5
  commit: 148d0a79571142b179a01be266d368ba299944ed

state:
  schema_version: 1
  local_compatibility_procedures: true

isolation:
  engine_repo_is_read_only_for_campaign_state: true
  campaign_state_must_remain_in_this_repository: true
  other_campaign_repositories_are_not_authority: true
```

## Authority and migration boundary

This repository remains the sole canonical durable state store for the Wren campaign.

The engine repository contains reusable procedures/templates, shared compiled source knowledge, persistent source-inventory routing procedure, source-availability routing, adventure-inventory routing procedure, regional/world-motion procedure, specialist source routers, asset procedure, and growth/sharding procedure only. Normal Wren gameplay, checkpoints, preferences, rulings, character/world facts, DM-only state, maps/assets, chronology, optional-rule activations, campaign-local regional actors/clocks/populations, and campaign-local source bindings/inventory must continue to persist in `hiramhibbard/wren-campaign`.

The existing local bootstrap/schema/policy/procedure/source-object files remain a **compatibility mirror** while Wren migration is staged. Their existence does not make them reusable campaign state for another campaign.

The portable-v1.2.5 engine may provide shared verified source objects and portable bibliographic/source metadata by stable IDs, but Hiram-specific uploaded-file references, corpus declarations, and source availability/inventory records remain local to Wren and are not part of the shared engine.

The portable-v1.2.5 upgrade is procedural/source-routing infrastructure only: inclusive character-identity startup, strict source-first published-adventure routing, persistent adventure inventory, and generalized persistent source inventory routing. It does not reinterpret or rewrite any established Wren fact. Wren's existing canonical state and local compatibility records remain authoritative for Wren.

A future engine upgrade must update this binding only after compatibility/integrity verification.