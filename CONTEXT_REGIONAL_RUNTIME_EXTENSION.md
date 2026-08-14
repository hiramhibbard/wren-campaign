# Context Architecture — Regional Runtime and Due-Event Extension — v1

This is a mandatory companion to `CONTEXT_ARCHITECTURE.md` whenever current/likely play intersects an active regional runtime under `REGIONAL_RUNTIME_POLICY.md`.

It does not create authority. It defines what regional/world-motion routing metadata belongs in disposable turn and Live Voice context.

## Session reconstruction integration

After checkpoint replay establishes the true current resume location and chronology:
1. determine the current active regional runtime profile(s);
2. load the applicable player-facing regional runtime profile;
3. load only the relevant DM-only active-world runtime records capable of affecting the likely play horizon;
4. derive the current due-event frontier from canonical clocks/triggers;
5. do not preload distant latent regions merely because they exist.

If the latest checkpoint moves Wren away from a previously active region, recompute this set instead of retaining stale regional preload state.

## Due-event frontier

Compile a compact disposable frontier containing only active elements whose next trigger can plausibly be crossed during likely immediate play.

For each entry preserve enough routing metadata to know:
- actor/process/event id;
- next trigger relative to canonical chronology;
- trigger type: time / condition / event / threshold / dependency;
- affected region/domain;
- canonical source path;
- whether resolution is deterministic, source-governed, or may require a bounded secret branching roll.

The frontier is not canonical truth. Canonical actor/process records and checkpoints remain authority.

When chronology advances:
- compare only against frontier entries whose trigger could be crossed;
- resolve due entries before dependent narration;
- refresh only changed entries after resolution;
- if elapsed time jumps beyond the current frontier, load/derive the next due entries as needed rather than scanning the entire repository.

## Live Voice preload

When Live Voice begins in or near an active region, preload as applicable:
- Wren's ordinary identity/mechanical/resource fast-path block;
- current regional runtime profile/zone;
- current consequential weather state and next weather trigger, if any;
- encounter procedure projection fields likely to be needed for the current travel mode/terrain;
- current prepared encounter-content reference/ingredients if a check can plausibly occur soon;
- the due-event frontier;
- active local/nearby actors/processes capable of changing circumstances during likely elapsed time;
- relevant rumor/knowledge reliability procedure only as compact routing instruction, not every rumor record;
- required DM-only causal state for likely clues/interactions.

Do not preload full encounter libraries, distant faction histories, broad rulebooks, or every active-world element in the campaign.

## Fast-path examples

Ordinary conversation in Lowcove:
`scene event -> no regional trigger crossed -> narration`

Wren sleeps one night:
`advance chronology -> compare due-event frontier -> resolve only crossed triggers -> refresh frontier -> narration`

Wren begins wilderness travel:
`regional zone/travel route -> encounter/weather/readiness domains -> use loaded projection fields where sufficient -> exact source only on unsupported edge case`

A population migrates into current region:
`world-state change -> invalidate affected encounter content + rumor/ecology dependencies -> refresh only those derived artifacts`

## Context invalidation

Recompile regional/Voice routing when any of these change consequentially:
- current location/region or planned route;
- active-horizon membership;
- actor/process reach;
- next due trigger/cadence;
- current weather state;
- encounter-content dependencies;
- active source/optional-rule scope;
- checkpoint replay reveals newer canonical state.

Do not retain stale derived frontier entries across these changes.

## Failure behavior

If a due regional/world-motion event is known to exist but its canonical actor/process record cannot be loaded, stop before narrating consequences that depend on it rather than improvising the hidden action.

During Voice, if the missing canonical fact/rule cannot be retrieved because tools are unavailable, preserve a pending lookup and follow the normal deferred-lookup rule after return to text.
