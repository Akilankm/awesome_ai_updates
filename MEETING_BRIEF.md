# Meeting Brief

**Updated:** 2026-07-22 00:09 IST

## Language worth using

| Term | Precise meaning | Credible meeting formulation | Evidence |
|---|---|---|---|
| Task-conditioned model routing | Selecting models per stage using task difficulty, latency, tool needs, risk, expected quality, and complete-task cost | “The architecture should route work by task characteristics, not standardize on one model name.” | [Google](https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-3-6-flash-3-5-flash-lite-3-5-flash-cyber/) |
| Agent task economics | Total cost of an accepted outcome including tokens, reasoning steps, tool calls, retries, latency, and rework | “Per-token price is an input; cost per accepted task is the decision metric.” | [Google](https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-3-6-flash-3-5-flash-lite-3-5-flash-cyber/) |
| Trajectory-level agent control | Evaluating cumulative intent and outcome across a session, not isolated calls only | “A safe tool call does not guarantee a safe trajectory.” | [OpenAI](https://openai.com/index/safety-alignment-long-horizon-models/) |
| Edge world-action model | A compact model connecting observation, predicted consequence, and action generation | “This is a shared world/action representation, not merely an edge VLM.” | [Cosmos 3 Edge](https://huggingface.co/blog/nvidia/cosmos3edge) |
| Outcome-linked AI credit governance | AI allocation and control tied to workloads, limits, overages, and useful outcomes | “Separate entitlement pools from metered budgets, then attribute consumption to accepted outcomes.” | [GitHub pools](https://github.blog/changelog/2026-07-20-ai-credit-pools-for-cost-centers-in-the-billing-ui/) |
| Quality-adjusted AI engineering | Evaluating AI-assisted development through findings, gates, remediation, delivery, and cost | “The useful unit is an accepted change that passes explicit quality gates without downstream rework.” | [GitHub Code Quality](https://github.blog/changelog/2026-07-20-github-code-quality-is-now-generally-available/) |

## Questions that demonstrate depth

| Situation | Question | Evidence |
|---|---|---|
| Model selection | “What is the accepted task-completion rate, tool-call count, retry rate, latency, and total cost on our workload—not only the benchmark score?” | [Google](https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-3-6-flash-3-5-flash-lite-3-5-flash-cyber/) |
| Agent architecture | “Which stages require a strong planner, which can use a throughput model, and what triggers fallback or escalation?” | [Google](https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-3-6-flash-3-5-flash-lite-3-5-flash-cyber/) |
| Privileged tools | “Does every code-execution or computer-use route have sandboxing, scoped identity, egress controls, deterministic validation, and replay?” | [Google Cloud](https://docs.cloud.google.com/gemini-enterprise-agent-platform/reference/models/code-execution-api) |
| Physical-AI architecture | “Are reasoning, generated futures, and control actions validated separately even when they share representation?” | [Cosmos 3 Edge](https://huggingface.co/blog/nvidia/cosmos3edge) |
| Agent approval | “Can the policy engine detect an unauthorized objective emerging across many permissible actions?” | [OpenAI](https://openai.com/index/safety-alignment-long-horizon-models/) |
| AI coding economics | “What is total cost per accepted, quality-gated change after compute, licensing, review, and remediation?” | [GitHub Code Quality](https://github.blog/changelog/2026-07-20-github-code-quality-is-now-generally-available/) |

## Claims to avoid

| Weak claim | Why it is unsafe | Better formulation | Evidence |
|---|---|---|---|
| “Gemini 3.6 Flash is the best model for agents.” | Vendor and public benchmarks do not establish workload-specific reliability or total economics | “It is a strong candidate for controlled evaluation on our task distribution.” | [Google](https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-3-6-flash-3-5-flash-lite-3-5-flash-cyber/) |
| “Lower token price means lower agent cost.” | Tool calls, retries, reasoning length, latency, failures, and rework can dominate cost | “Compare total cost per accepted task.” | [Google](https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-3-6-flash-3-5-flash-lite-3-5-flash-cyber/) |
| “Flash-Lite should replace the stronger model everywhere.” | Throughput models and planner models serve different uncertainty and complexity regimes | “Use bounded routing with escalation and fallback.” | [Google](https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-3-6-flash-3-5-flash-lite-3-5-flash-cyber/) |
| “The cyber model autonomously secures software.” | Performance emerges from specialized training, orchestration, validation, containment, and restricted access | “Evaluate the complete cyber-agent system and its controls.” | [Google](https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-3-6-flash-3-5-flash-lite-3-5-flash-cyber/) |
| “Every action was approved, so the agent was safe.” | Individually acceptable actions can combine into an unauthorized outcome | “Approval must cover actions and cumulative trajectory intent.” | [OpenAI](https://openai.com/index/safety-alignment-long-horizon-models/) |
