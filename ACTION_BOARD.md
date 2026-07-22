# AI Engineering Action Board

**Updated:** 2026-07-22 23:08 IST

## Build

| Priority | Action | Deliverable | Success criteria | Career value | Evidence |
|---:|---|---|---|---:|---|
| 1 | Build a governed production-agent lifecycle reference architecture | Workflow contract, scoped identity and knowledge, approved action registry, policy engine, escalation, simulations, graders, production telemetry, proposed-change pipeline, canary and rollback | A seeded policy change and failure are converted into a proposed update, regression-tested, approved, canaried, and rolled back without direct production mutation | 10.0/10 | [OpenAI Presence](https://openai.com/index/introducing-openai-presence/) |
| 2 | Build an adversarial evaluation containment harness | Dedicated identity, deny-by-default egress, hardened dependency proxy, secret isolation, trajectory monitor, canaries, automated pause, and replay | Seeded proxy abuse, credential theft, lateral movement, and exfiltration chains terminate before external reachability | 10.0/10 | [OpenAI](https://openai.com/index/hugging-face-model-evaluation-security-incident/) |
| 3 | Extend the AI engineering scorecard with adoption phases and quality-adjusted outcomes | Passive/Code-first/Agent-first/Multi-agent cohorts joined to repository type, quality, rework, lead time, incidents, accepted outcomes, and cost | Aggregate cohort comparisons include minimum samples, confounder notes, privacy review, and no individual ranking | 9.8/10 | [GitHub impact dashboard](https://github.blog/changelog/2026-07-22-new-copilot-usage-metrics-impact-dashboard/) |
| 4 | Implement a safety-control-ablation protocol | Versioned approval, safeguards removed, scope, connectivity, credentials, limits, monitors, and restoration checklist | No reduced-safeguard run starts without an approved compensating-control bundle | 9.9/10 | [OpenAI](https://openai.com/index/hugging-face-model-evaluation-security-incident/) |
| 5 | Build a task-conditioned model-routing evaluation harness | Provider-neutral task suite, router, fallback, route trace, and scorecard | Compares accepted completion, unwanted edits, tool calls, retries, latency, rework, and total cost | 9.9/10 | [Google](https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-3-6-flash-3-5-flash-lite-3-5-flash-cyber/) |
| 6 | Build a trajectory-level agent monitor | Event stream, cumulative-policy evaluator, immutable replay, alerts, and pause/resume control | Detects seeded multi-step constraint bypass while preserving legitimate work | 9.9/10 | [OpenAI](https://openai.com/index/safety-alignment-long-horizon-models/) |

## Study

| Topic | Why now | Learning outcome | Priority | Evidence |
|---|---|---|---:|---|
| Production-agent lifecycle engineering | Presence operationalizes scoped jobs, policies, actions, evaluations, escalation, feedback, controlled updates, and rollout | Design a complete agent operating model from workflow contract through retirement | 1 | [OpenAI Presence](https://openai.com/index/introducing-openai-presence/) |
| AI adoption analytics and causal discipline | GitHub now exposes behavioral adoption cohorts and delivery metrics | Separate descriptive cohort signals from causal productivity claims; control for workload, role, quality, rework, and selection | 1 | [GitHub impact dashboard](https://github.blog/changelog/2026-07-22-new-copilot-usage-metrics-impact-dashboard/) |
| Cyber-range and evaluation-environment security | A real incident originated from advanced-model evaluation | Design containment for hostile adaptive workloads | 1 | [OpenAI](https://openai.com/index/hugging-face-model-evaluation-security-incident/) |
| Task-conditioned model routing | Coordinated model portfolios are available | Design task taxonomies, routing rules, fallbacks, evaluations, and traces | 1 | [Google](https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-3-6-flash-3-5-flash-lite-3-5-flash-cyber/) |
| Trajectory-level policy evaluation | Long-horizon failures emerge from sequences of acceptable actions | Model cumulative intent, privilege expansion, destination, and outcome | 1 | [OpenAI](https://openai.com/index/safety-alignment-long-horizon-models/) |

## Internal proposal opportunities

| Proposal | Business value | POC scope | Guardrail | Evidence |
|---|---|---|---|---|
| Governed production-agent lifecycle | Converts demos into auditable services that adapt safely as policies and user behavior change | One support workflow with scoped tools, escalation, simulations, graders, production signals, proposed updates, regression comparison, approval, canary, and rollback | No autonomous production mutation; no broad credentials; immutable evidence; human approval for policy/action changes | [OpenAI Presence](https://openai.com/index/introducing-openai-presence/) |
| Quality-adjusted AI adoption maturity dashboard | Gives leadership a defensible view of adoption depth without confusing activity with value | Join GitHub adoption cohorts to quality, delivery, rework, incidents, accepted outcomes, and cost | Aggregate only; privacy review; no employee ranking; no causal claims without controlled evidence | [GitHub impact dashboard](https://github.blog/changelog/2026-07-22-new-copilot-usage-metrics-impact-dashboard/) |
| Adversarial evaluation containment control plane | Enables aggressive capability testing without turning research infrastructure into an attack surface | One cyber-evaluation workflow with dedicated identity, hardened package path, egress control, monitoring, pause, replay, and ablation approval | No production credentials; no unrestricted Internet; bounded compute; immutable logs; human kill switch | [OpenAI](https://openai.com/index/hugging-face-model-evaluation-security-incident/) |
| Task-conditioned model-routing control plane | Reduces agent cost and latency while preserving quality and portability | Planner, bounded subagent, validator, fallback, and route-level quality/cost telemetry | No irreversible actions; deterministic validation; bounded spend; rollback | [Google](https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-3-6-flash-3-5-flash-lite-3-5-flash-cyber/) |
| Quality-adjusted AI coding control plane | Converts AI coding adoption into enforceable quality, delivery, risk, and cost governance | One repository joining route, activity, findings, gates, remediation, rework, deployment, and cost | Start in evaluate mode; minimum samples; privacy review; rollback | [GitHub Code Quality](https://github.blog/changelog/2026-07-20-github-code-quality-is-now-generally-available/) |
