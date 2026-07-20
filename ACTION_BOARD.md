# AI Engineering Action Board

**Updated:** 2026-07-21 01:07 IST

## Build

| Priority | Action | Deliverable | Success criteria | Career value | Evidence |
|---:|---|---|---|---:|---|
| 1 | Build a trajectory-level agent monitor | Event stream, cumulative-policy evaluator, immutable replay log, alerts, and pause/resume control | Detects seeded multi-step constraint bypass while preserving legitimate long-running work | 9.9/10 | [OpenAI](https://openai.com/index/safety-alignment-long-horizon-models/) |
| 2 | Build an edge world-action evaluation harness | Replayable sensor-to-action scenarios with latency, action validity, predicted-consequence accuracy, recovery, memory, power, and thermal metrics | Produces hardware- and task-specific deployment evidence independent of vendor rank | 9.7/10 | [Cosmos 3 Edge](https://huggingface.co/blog/nvidia/cosmos3edge) |
| 3 | Build an incident-to-evaluation pipeline | Reproduction template, trajectory capture, replay environment, regression test, owner, and threshold | Every material agent incident becomes a replayable test before redeployment | 9.9/10 | [OpenAI](https://openai.com/index/safety-alignment-long-horizon-models/) |
| 4 | Extend the AI engineering scorecard with credit allocation and quality gates | Data model joining credits, cost centers, repositories, workloads, findings, gates, remediation, delivery, and accepted outcomes | Reports cost per accepted quality-gated change and approaching pool/budget limits without ranking people | 9.8/10 | [GitHub pools](https://github.blog/changelog/2026-07-20-ai-credit-pools-for-cost-centers-in-the-billing-ui/) · [Code Quality](https://github.blog/changelog/2026-07-20-github-code-quality-is-now-generally-available/) |
| 5 | Harden a long-running agent sandbox | Scoped identity, deny-by-default egress, short-lived credentials, runtime controls, limits, and kill switch | Persistent probing cannot expand identity or reach unapproved destinations | 9.9/10 | [OpenAI](https://openai.com/index/safety-alignment-long-horizon-models/) |
| 6 | Build an AI data-pipeline threat model | Attack tree and controls for loaders, parsers, workers, secrets, clusters, and publication | Every executable ingestion path has an owner, sandbox, credential boundary, egress rule, and playbook | 9.8/10 | [Hugging Face](https://huggingface.co/blog/security-incident-july-2026) |

## Study

| Topic | Why now | Learning outcome | Priority | Evidence |
|---|---|---|---:|---|
| World-action model architecture | Cosmos 3 Edge combines autoregressive reasoning and diffusion generation through shared attention | Explain observation encoding, shared representation, future-state generation, action decoding, embodiment mapping, and policy mode | 1 | [Cosmos 3 Edge](https://huggingface.co/blog/nvidia/cosmos3edge) |
| Edge physical-AI evaluation | Vendor throughput and benchmark rank do not establish workload fit | Design control-loop tests covering latency, action validity, recovery, memory, power, thermal limits, and safety fallback | 1 | [Cosmos 3 Edge](https://huggingface.co/blog/nvidia/cosmos3edge) |
| AI credit economics | GitHub now separates pools, budgets, overages, and user visibility | Model entitlement allocation, metered spend, hard-stop policy, forecasting, and cost per accepted outcome | 1 | [GitHub pools](https://github.blog/changelog/2026-07-20-ai-credit-pools-for-cost-centers-in-the-billing-ui/) |
| Trajectory-level policy evaluation | Long-horizon failures can emerge from sequences of acceptable actions | Model cumulative intent, constraint bypass, privilege expansion, destination, and outcome | 1 | [OpenAI](https://openai.com/index/safety-alignment-long-horizon-models/) |
| Layered code-quality architecture | GitHub combines deterministic CodeQL with AI-assisted detection and Autofix | Distinguish reproducible static evidence from probabilistic findings and design separate metrics | 1 | [GitHub Code Quality](https://github.blog/changelog/2026-07-20-github-code-quality-is-now-generally-available/) |

## Internal proposal opportunities

| Proposal | Business value | POC scope | Guardrail | Evidence |
|---|---|---|---|---|
| Edge world-action model POC | Tests whether shared perception, simulation, and policy reduce latency and integration complexity | One bounded camera-driven manipulation task comparing a modular stack with Cosmos 3 Edge | No production actuation; emergency stop; full trajectory logging; independent validation | [Cosmos 3 Edge](https://huggingface.co/blog/nvidia/cosmos3edge) |
| AI consumption control plane | Enables allocation, forecasting, limit policy, and outcome-adjusted unit economics | Join GitHub credits, cost centers, repository activity, quality gates, remediation, and delivery outcomes | Do not rank individuals; transparent attribution; exceptions and rollback | [GitHub pools](https://github.blog/changelog/2026-07-20-ai-credit-pools-for-cost-centers-in-the-billing-ui/) |
| Long-horizon agent control plane | Enables durable autonomy without relying on per-call approvals alone | One sandboxed agent with scoped identity, egress control, trajectory monitor, intervention, replay, and rollback | No irreversible actions; immutable audit; bounded duration and spend; kill switch | [OpenAI](https://openai.com/index/safety-alignment-long-horizon-models/) |
| Quality-adjusted AI coding control plane | Converts AI coding adoption into enforceable quality, delivery, risk, and cost governance | One repository joining activity, findings, coverage, gates, remediation, rework, deployment, and cost | Start in evaluate mode; minimum samples; privacy review; rollback | [GitHub Code Quality](https://github.blog/changelog/2026-07-20-github-code-quality-is-now-generally-available/) |