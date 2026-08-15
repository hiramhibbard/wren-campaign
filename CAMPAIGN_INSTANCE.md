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
  version: portable-v1.2.3
  commit: 6de2b15188643e7be480b5e7398ae6acaa50e77d

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

The engine repository contains reusable procedures/templates, shared compiled source knowledge, source-availability routing, regional/world-motion procedure, specialist source routers, asset procedure, and growth/sharding procedure only. Normal Wren gameplay, checkpoints, preferences, rulings, character/world facts, DM-only state, maps/assets, chronology, optional-rule activations, campaign-local regional actors/clocks/populations, and campaign-local source bindings must continue to persist in `hiramhibbard/wren-campaign`.

The existing local bootstrap/schema/policy/procedure/source-object files remain a **compatibility mirror** while Wren migration is staged. Their existence does not make them reusable campaign state for another campaign.

The portable-v1.2.3 engine may provide shared verified source objects by stable bibliographic IDs, but Hiram-specific uploaded-file references remain local to Wren and are not part of the shared engine.

The portable-v1.2.3 upgrade is procedural only: inclusive character-identity startup and stricter source-first published-adventure routing. It does not reinterpret or rewrite any established Wren fact. Wren's existing canonical state and local compatibility records remain authoritative for Wren.

A future engine upgrade must update this binding only after compatibility/integrity verification.
