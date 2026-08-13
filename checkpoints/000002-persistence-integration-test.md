# Persistence Integration Test — Administrative Only

This checkpoint is an administrative protocol integration test. It does not change Wren campaign state and does not count toward maintenance thresholds.

- sequence: 000002
- transaction-id: wren-tx-20260813T230900Z-51f73f11
- kind: persistence-integration-test
- state-change: none
- schema-version: 1
- persistence-protocol-version: 1
- snapshot-generation: 1
- checkpoint-baseline-observed: 1
- base-root-blob-sha: 65c1201636503cade706f7ba19415ae0054120f1
- parent-checkpoint-sequence: 000001
- parent-checkpoint-blob-sha: d80255d489f8f91ae7e80b27eb0c7cff62d76823
- affected-domains: none

## Test Assertions

- Campaign semantic delta: none.
- Player-facing delta: none.
- DM-secret delta: none.
- Chronology/resource/location delta: none.
- Maintenance-count contribution: none.
- Purpose: verify connector append, exact canonical readback, parent/root metadata capture, transaction-ID discovery, and idempotent duplicate avoidance under `PERSISTENCE_PROTOCOL.md`.

## Idempotency Expectation

Any later attempt to persist this same logical transaction using transaction ID `wren-tx-20260813T230900Z-51f73f11` must discover and verify this checkpoint rather than creating another checkpoint.