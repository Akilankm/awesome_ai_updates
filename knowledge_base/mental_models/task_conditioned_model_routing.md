# Task-Conditioned Model Routing

**Added:** 2026-07-22 00:09 IST

## Core model

A production agent should not treat a model identifier as the architecture. The durable architecture is a governed routing system that selects a model and capability set for each stage based on task difficulty, latency objective, modality, tool requirements, risk, context size, and expected total cost.

| Layer | Question | Required evidence |
|---|---|---|
| Task classification | What kind of work is this and how uncertain or risky is it? | Task taxonomy, confidence, sensitivity, expected complexity |
| Route selection | Which model, thinking level, tool set, and budget should handle it? | Route policy version, model version, capability requirements |
| Execution | Did the route complete the stage efficiently and correctly? | Tool calls, retries, latency, tokens, intermediate artifacts |
| Validation | Is the result acceptable for the downstream decision? | Deterministic checks, model judge only where appropriate, human review for high-risk cases |
| Escalation | What condition sends the work to a stronger or safer route? | Failure, uncertainty, policy, timeout, quality, or risk triggers |
| Economics | What did the accepted outcome cost end to end? | Provider spend, compute, latency, retries, review, rework |
| Learning | How should routing change after evidence accumulates? | Route-level success distributions, drift, incidents, and counterfactual replay |

## Why this changed

Google’s July 21, 2026 portfolio release pairs Gemini 3.6 Flash as a workhorse model with Gemini 3.5 Flash-Lite for high-throughput workflows and Gemini 3.5 Flash Cyber as a specialized restricted-access model. The release explicitly connects model quality with output-token efficiency, reasoning steps, tool calls, latency, and price. This makes portfolio orchestration and task-level economics an immediate engineering concern rather than a theoretical optimization. [Primary release](https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-3-6-flash-3-5-flash-lite-3-5-flash-cyber/)

## Architecture pattern

```text
request
  -> task/risk classifier
  -> routing policy
       -> throughput route
       -> workhorse route
       -> specialist route
       -> human-controlled route
  -> tool-capability boundary
  -> deterministic validation
  -> escalation/fallback
  -> accepted outcome
  -> route-level quality, latency, safety, and cost telemetry
```

## Evaluation contract

| Metric family | Minimum metrics |
|---|---|
| Outcome | Accepted completion rate, exact/task-specific correctness, downstream usability |
| Agent behavior | Tool-call count, reasoning loops, retries, unwanted edits, failure recovery |
| Performance | Time to first useful artifact, wall-clock completion, throughput, tail latency |
| Economics | Input/output tokens, provider charge, compute, review time, rework, cost per accepted task |
| Safety | Privileged actions, policy interventions, egress attempts, credential access, rollback success |
| Portability | Reproduction across providers, model versions, prompts, and tool implementations |

## Routing principles

1. Use throughput models for bounded, high-volume, verifiable stages.
2. Use stronger models for uncertain planning, synthesis, and difficult recovery.
3. Escalate on measured uncertainty or validation failure, not on arbitrary prompt length alone.
4. Keep deterministic validators outside the generative route whenever possible.
5. Version model IDs, thinking levels, prompts, tools, policies, and evaluation sets together.
6. Preserve provider-neutral traces so a route can be replayed against another model.
7. Optimize cost per accepted outcome, not cost per token or model benchmark rank.
8. Apply stricter sandbox, identity, egress, approval, and trajectory controls to routes with code execution, computer use, or security capabilities.

## Failure modes

| Failure | Why it happens | Countermeasure |
|---|---|---|
| Cheapest-model routing | Optimizes token rate while ignoring failures and rework | Use total accepted-task economics |
| Strongest-model everywhere | Pays premium cost for bounded work and reduces system scalability | Decompose stages and validate throughput routes |
| Benchmark routing | Assumes public averages match internal task distribution | Maintain workload-specific replay sets |
| Silent fallback | Hides quality and cost regressions | Emit route and escalation telemetry |
| Provider lock-in | Prompts, tools, traces, and validators depend on one API | Use capability adapters and provider-neutral event schemas |
| Privilege leakage | A fast route inherits tools it does not need | Grant capabilities per route using least privilege |
| Router drift | Routing policy changes without regression evidence | Version policies and gate changes with replay evaluation |

## Meeting formulation

> “We are not selecting a single winning model. We are designing a governed routing system that chooses the least expensive route capable of producing an accepted outcome under the required latency, quality, and risk constraints.”

## Terms not to misuse

| Term | Do not imply |
|---|---|
| Workhorse model | Universal best model for every task |
| Throughput model | Low-quality model with no role in serious systems |
| Routing | Unobservable provider-side auto-selection with no evaluation contract |
| Cost efficiency | Lower per-token price without accepted-outcome measurement |
| Specialist model | Safe autonomous deployment without orchestration and controls |

## Concrete implementation target

Build a POC with one planner route, one throughput route, deterministic validation, an escalation route, and complete route telemetry. Compare it with a single-model baseline on at least 50 replayable tasks. Promote routing only when quality is non-inferior and either latency or cost improves materially, with no degradation in safety controls.

## Sources

| Source | Use |
|---|---|
| [Google: Gemini 3.6 Flash, 3.5 Flash-Lite, and 3.5 Flash Cyber](https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-3-6-flash-3-5-flash-lite-3-5-flash-cyber/) | Portfolio, efficiency, pricing, benchmarks, deployment surfaces, cyber access model |
| [Google Cloud: code execution](https://docs.cloud.google.com/gemini-enterprise-agent-platform/reference/models/code-execution-api) | Privileged capability and supported-model boundary |
| [GitHub: Gemini 3.6 Flash in Copilot](https://github.blog/changelog/2026-07-21-gemini-3-6-flash-is-now-available-in-github-copilot/) | Immediate coding-workflow availability |
