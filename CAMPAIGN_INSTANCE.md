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
  version: portable-v1
  commit: ca6c74370975834a8d1f7aaf065b2b6afe608230

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

The engine repository contains reusable procedures/templates only. Normal Wren gameplay, checkpoints, preferences, rulings, character/world facts, DM-only state, maps/assets, and chronology must continue to persist in `hiramhibbard/wren-campaign`.

The existing local bootstrap/schema/policy/procedure files remain a **compatibility mirror** during staged engine extraction so Wren's established operating path is not broken. Their existence does not make them reusable state for another campaign.

No engine extraction or upgrade may reinterpret or rewrite established Wren campaign facts merely to match a newer procedure. Engine changes apply prospectively unless a specific safe migration is explicitly performed.

An engine upgrade must update this binding only after compatibility/integrity verification.
