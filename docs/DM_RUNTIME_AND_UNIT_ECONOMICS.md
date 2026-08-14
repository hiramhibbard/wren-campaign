# DM Runtime, Model Routing & Unit Economics

**Status:** Product / engineering roadmap module. Not campaign canon.  
**Parent roadmap:** `docs/APPLICATION_ROADMAP.md`  
**Initialized:** 2026-08-13.

## Purpose

Define how a future Wren-derived application should power the AI DM for many users, route work across models/providers, meter cost, structure subscriptions, and validate unit economics before pricing.

The campaign engine should depend on capabilities rather than one provider or model name.

## Runtime boundary

Use a provider abstraction:

`Campaign Engine -> Model Router -> Provider/Model`

The campaign engine owns canonical state, context compilation, source retrieval, deterministic mechanics, persistence, knowledge boundaries, and transactions. Models provide reasoning, narration, interpretation, extraction, summarization, ranking, or realtime conversational capabilities.

Do not allow provider-specific model identifiers to leak deeply into campaign-state schemas.

## Capability-based routing

Define model capabilities such as:

- `adjudicate` — high-quality DM judgment and consequence reasoning;
- `narrate` — prose, dialogue, and scene presentation;
- `realtime_dm` — low-latency Voice conversation;
- `extract_state` — structured candidate deltas from a turn/session;
- `rank_context` — relevance/reranking when deterministic routing is insufficient;
- `summarize_history` — compact episodic summaries;
- `classify_visibility` — assist knowledge-boundary classification, with deterministic validation;
- `source_interpretation` — reason over retrieved rules/adventure excerpts.

The router may select models based on quality requirements, latency, context size, current cost, user subscription tier, provider health, and task risk.

High-consequence adjudication should not be silently downgraded merely to save cost.

## Deterministic work stays out of the model

Do not spend inference on work code can perform reliably:

- dice/randomness;
- arithmetic;
- encumbrance/resource bookkeeping;
- event sequencing;
- persistence transactions;
- typed relationship queries;
- direct canonical routing;
- authorization/visibility filtering;
- subscription/usage metering.

This improves both correctness and cost.

## Provider strategy

Start with one well-supported provider to minimize product complexity, while keeping the internal contract provider-neutral enough to support later fallback or alternate providers.

Potential later modes:

- hosted inference paid by the application;
- alternate-provider fallback;
- user-selectable premium model tier;
- Bring Your Own API Key/provider for advanced users;
- local/self-hosted models if quality and hardware economics become competitive.

BYO-key should be optional rather than required for a consumer product. It can reduce platform inference liability for power users but adds setup, security, support, and provider-compatibility complexity.

## Subscription ownership

Subscription/entitlement should belong primarily to the user/account, not to an individual AI agent or campaign record.

A user may own multiple campaigns under one account. Campaigns retain independent state and usage attribution.

Multiplayer billing is deferred until multiplayer is validated. Possible later models include campaign-owner sponsorship, per-seat plans, shared campaign pools, or hybrid entitlements.

## Internal cost buckets

Track unit economics separately for at least:

1. **Inference** — text/reasoning/realtime audio/model calls;
2. **Persistent infrastructure** — database, object storage, indexes, backups, bandwidth;
3. **Tool/content processing** — document parsing/indexing, image generation, map processing, premium integrations, or other metered services.

Do not price solely from model-token cost. Include infrastructure, payment fees, support, abuse/fraud, and reasonable margin.

## Usage metering

Internally meter actual provider usage in provider-native units where possible:

- uncached/cached input tokens;
- output/reasoning tokens where billed;
- realtime audio input/output duration or tokens;
- image/tool calls;
- source-processing jobs;
- storage and bandwidth where material.

Externally, prefer understandable product units rather than exposing raw token accounting to ordinary users.

Potential user-facing concepts:

- included monthly AI play allowance;
- included Voice hours/minutes;
- premium-model allowance;
- source-processing/storage allowance;
- optional top-ups for unusually heavy use.

## Subscription hypotheses to test

Do not commit to price points until measured session economics exist.

Candidate structures to simulate:

- text-first entry tier;
- standard tier with generous text play plus a moderate Voice allowance;
- premium/heavy-play tier with more Voice and access to higher-cost reasoning models;
- BYO-provider tier where the subscription primarily covers campaign engine/storage/product features;
- optional usage top-ups instead of hard lockout for occasional overages.

Avoid promising economically unbounded unlimited inference until real usage distributions prove it sustainable.

## Cost telemetry

Every runtime request should eventually be attributable to:

- account/user;
- campaign;
- session;
- capability requested;
- selected provider/model;
- context/input size;
- output size/duration;
- cache hit/miss where applicable;
- estimated/actual provider cost;
- latency;
- retry/failure/fallback status.

Aggregate these into per-session and per-user cost profiles without exposing DM-secret campaign content to billing analytics unnecessarily.

## Cost simulator milestone

Before setting public subscription prices, build a unit-economics simulator from genuine Wren-style sessions.

Inputs should include:

- text turns;
- Voice duration;
- compiled context sizes;
- cached versus uncached context;
- narration/adjudication output sizes;
- retrieval/tool calls;
- checkpoint/state-processing work;
- source lookups;
- candidate model-routing strategies.

Simulate realistic user populations and heavy-tail behavior at 100, 1,000, 10,000, and larger active-user counts.

Outputs should include:

- median and percentile cost per session/user/month;
- cost split by capability;
- Voice versus text economics;
- gross margin under candidate subscription plans;
- sensitivity to model-price changes;
- effect of caching/model routing;
- abuse/heavy-user exposure;
- break-even usage thresholds.

Do not set hard subscription pricing until this exists.

## Quotas and guardrails

The product needs graceful economic controls:

- account-level usage budgets;
- provider/model rate limits;
- per-session runaway protection;
- maximum source-processing job sizes;
- configurable premium-model use;
- alerts before unexpected spend spikes;
- degradation/fallback rules that preserve correctness.

Economic guardrails must not silently corrupt or truncate canonical campaign persistence. If compute limits prevent safe adjudication, the application should stop cleanly rather than fabricate campaign state.

## Caching economics

The Context Compiler should deliberately maximize safe reuse of stable prompt/context segments where provider caching supports it.

Candidates include:

- system/game invariants;
- stable rules-adapter instructions;
- unchanged immediate campaign state;
- persistent NPC/location context within a scene;
- source excerpts reused across consecutive adjudications.

Caching is an optimization layer only; correctness cannot depend on a cache hit.

## Model quality evaluation

Model routing must be driven by both cost and measured DM quality.

Maintain eval sets for:

- rules adjudication;
- NPC continuity;
- knowledge-boundary preservation;
- long-context retrieval use;
- consequence reasoning;
- state extraction;
- Voice responsiveness;
- hallucination/invention of canon.

A cheaper model is suitable for a capability only when it meets the quality threshold for that task.

## Pricing decision gate

Before launch pricing is considered stable, require:

1. real-play telemetry from prototype users;
2. cost simulator results;
3. model-routing quality benchmarks;
4. known Voice economics;
5. storage/source-library cost estimates;
6. heavy-user/abuse analysis;
7. candidate margin targets and sensitivity analysis.

Treat pricing as an empirical product decision, not an architectural constant.

## Near-term engineering hooks

After enough real Wren sessions exist to provide representative workloads:

1. instrument context size and turn/session shape;
2. define the capability enum/interface;
3. prototype a provider-neutral model-router contract;
4. record per-capability inference telemetry in a development harness;
5. replay real Wren sessions through candidate routing strategies;
6. build the first unit-economics simulator;
7. model text-heavy, Voice-heavy, and extreme-heavy-user cohorts;
8. compare hosted-inference and optional BYO-key economics;
9. use the results to inform the first product pricing experiments.

## Deferred decisions

Do not decide yet:

- exact subscription prices;
- exact included Voice limits;
- exact providers/models at launch;
- whether premium models are user-selectable or automatically routed;
- whether BYO-key ships in the first public version;
- multiplayer billing ownership;
- dedicated local/self-hosted inference support.

These should be decided from measured quality, cost, and user behavior rather than preference alone.
