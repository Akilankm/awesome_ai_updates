# AI Engineering Action Board

**Updated:** 2026-07-24 02:07 IST

## Build

| Priority | Action | Deliverable | Success criteria | Career value | Evidence |
|---:|---|---|---|---:|---|
| 1 | Build a confidence-gated issue-automation control plane | Replayable issue set, action proposals, decision-envelope schema, calibrated per-action confidence, policy router, reviewer queue, execution ledger, and outcome feedback | Compare review-all, global-threshold, and calibrated action-specific policies; reduce review load without breaching the agreed expected-loss bound | 10.0/10 | [GitHub](https://github.blog/changelog/2026-07-23-agent-automation-controls-in-github-issues-in-public-preview) |
| 2 | Build a governed production-agent lifecycle reference architecture | Workflow contract, scoped identity, action registry, policy engine, escalation, simulations, graders, telemetry, proposed-change pipeline, canary, and rollback | A seeded failure becomes a tested, approved, canaried, reversible update without direct production mutation | 10.0/10 | [OpenAI Presence](https://openai.com/index/introducing-openai-presence/) |
| 3 | Build an adversarial evaluation containment harness | Dedicated identity, deny-by-default egress, hardened dependency proxy, secret isolation, trajectory monitor, canaries, pause, and replay | Seeded abuse chains terminate before external reachability | 10.0/10 | [OpenAI](https://openai.com/index/hugging-face-model-evaluation-security-incident/) |
| 4 | Build a hardware-heterogeneous kernel portability lab | One custom kernel, backend adapters, native baselines, correctness suite, tuning provenance, and portability scorecard | Reproducible results across shapes with tolerances, tuning cost, throughput, memory, fallback, and version pins | 9.8/10 | [PyTorch](https://pytorch.org/blog/helion-on-tpu-towards-hardware-heterogeneous-kernel-authoring/) · [Helion](https://github.com/pytorch/helion) |
| 5 | Extend the AI engineering scorecard with adoption phases and quality-adjusted outcomes | Behavioral cohorts joined to repository type, quality, rework, lead time, incidents, accepted outcomes, and cost | Aggregate comparisons include minimum samples, confounder notes, privacy review, and no individual ranking | 9.8/10 | [GitHub impact dashboard](https://github.blog/changelog/2026-07-22-new-copilot-usage-metrics-impact-dashboard/) |

## Study

| Topic | Why now | Learning outcome | Priority | Evidence |
|---|---|---|---:|---|
| Selective prediction, confidence calibration, abstention, and cost-sensitive thresholds | GitHub now productizes confidence-routed issue actions | Explain reliability diagrams, expected calibration error, coverage-risk tradeoffs, conformal risk controls, and action-specific expected loss | 1 | [GitHub](https://github.blog/changelog/2026-07-23-agent-automation-controls-in-github-issues-in-public-preview) |
| Agent decision provenance and authorization boundaries | GitHub exposes rationale and approvals while warning that approvals are not security controls | Design a complete decision envelope and separate review UX from server-side enforcement | 1 | [GitHub](https://github.blog/changelog/2026-07-23-agent-automation-controls-in-github-issues-in-public-preview) |
| Production-agent lifecycle engineering | Presence operationalizes scoped jobs, policies, actions, evaluation, escalation, feedback, and controlled rollout | Design a complete agent operating model | 1 | [OpenAI Presence](https://openai.com/index/introducing-openai-presence/) |
| Helion, Pallas, Triton, and backend-lowered kernel design | Helion’s TPU backend makes multi-accelerator portability concrete | Explain lowering boundaries, scheduling, memory hierarchy, autotuning, generated code, and numerical conformance | 1 | [PyTorch](https://pytorch.org/blog/helion-on-tpu-towards-hardware-heterogeneous-kernel-authoring/) |
| Cyber-range and evaluation-environment security | A real incident originated from advanced-model evaluation | Design containment for hostile adaptive workloads | 1 | [OpenAI](https://openai.com/index/hugging-face-model-evaluation-security-incident/) |

## Internal proposal opportunities

| Proposal | Business value | POC scope | Guardrail | Evidence |
|---|---|---|---|---|
| Confidence-gated workflow automation control plane | Automates low-risk operational decisions while reserving review capacity for uncertain or consequential actions | One issue-triage workflow covering labels, fields, assignment, and closure with calibrated routing, immutable provenance, and outcome feedback | Approval UX must not replace permissions; no auto-closure until calibration, expected-loss, and rollback tests pass | [GitHub](https://github.blog/changelog/2026-07-23-agent-automation-controls-in-github-issues-in-public-preview) |
| Governed production-agent lifecycle | Converts demos into auditable services that adapt safely | One support workflow with scoped tools, escalation, simulations, graders, proposed updates, approval, canary, and rollback | No autonomous production mutation; no broad credentials; immutable evidence | [OpenAI Presence](https://openai.com/index/introducing-openai-presence/) |
| Hardware-heterogeneous kernel portability lab | Reduces accelerator lock-in and identifies useful custom-kernel opportunities | One production bottleneck expressed through a high-level DSL and compared with native baselines | Require conformance, reproducibility, cost accounting, version pinning, and native fallback | [PyTorch](https://pytorch.org/blog/helion-on-tpu-towards-hardware-heterogeneous-kernel-authoring/) · [Helion](https://github.com/pytorch/helion) |
| Quality-adjusted AI adoption maturity dashboard | Gives leadership a defensible view of adoption depth without confusing activity with value | Join adoption cohorts to quality, delivery, rework, incidents, accepted outcomes, and cost | Aggregate only; privacy review; no employee ranking; no causal claims without controlled evidence | [GitHub impact dashboard](https://github.blog/changelog/2026-07-22-new-copilot-usage-metrics-impact-dashboard/) |
| Adversarial evaluation containment control plane | Enables aggressive testing without turning research infrastructure into an attack surface | One cyber-evaluation workflow with dedicated identity, hardened package path, egress control, monitoring, pause, and replay | No production credentials; no unrestricted Internet; bounded compute; immutable logs; kill switch | [OpenAI](https://openai.com/index/hugging-face-model-evaluation-security-incident/) |
