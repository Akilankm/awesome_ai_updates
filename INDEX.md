# AI Intelligence Index

**Last refreshed:** 2026-07-21 00:10 IST

| Purpose | Current resource |
|---|---|
| Five-minute intelligence scan | [LATEST.md](LATEST.md) |
| Meeting-ready narrative | [MEETING_BRIEF.md](MEETING_BRIEF.md) |
| Terminology and narrative momentum | [TERMINOLOGY_RADAR.md](TERMINOLOGY_RADAR.md) |
| Learning, POC, and adoption decisions | [ACTION_BOARD.md](ACTION_BOARD.md) |
| Current hourly record | [2026-07-21 00:10 IST](hourly/2026/07/21/00-10_IST.md) |
| Previous hourly record | [2026-07-20 23:09 IST](hourly/2026/07/20/23-09_IST.md) |
| Long-horizon safety mental model | [Adaptive adversarial evaluation](knowledge_base/mental_models/adaptive_adversarial_evaluation.md) |
| Repository-scoped AI governance mental model | [Repository-level AI engineering observability](knowledge_base/mental_models/repository_level_ai_engineering_observability.md) |
| Open-weight customization mental model | [Adaptation-adjusted model value](knowledge_base/mental_models/adaptation_adjusted_model_value.md) |
| Coding-agent orchestration mental model | [Concurrent coding agents](knowledge_base/mental_models/concurrent_coding_agents.md) |
| Research-agent evaluation mental model | [Clean-room agent evaluation](knowledge_base/mental_models/clean_room_agent_evaluation.md) |

## Current high-value themes

| Theme | Status | Why it is strategically important | Evidence |
|---|---|---|---|
| Trajectory-level agent control | Accelerating | Long-running agents can discover environment weaknesses and compose benign-looking actions into unauthorized outcomes; monitoring must reason over intent and cumulative outcome | [OpenAI](https://openai.com/index/safety-alignment-long-horizon-models/) |
| Incident-derived agent evaluation | Accelerating | Production failures can expose gaps absent from fixed pre-deployment suites and should become replayable evaluations and release gates | [OpenAI](https://openai.com/index/safety-alignment-long-horizon-models/) |
| Quality-adjusted AI engineering governance | Accelerating | Deterministic analysis, AI-assisted findings, coverage, repository ruleset gates, remediation, and metered economics form an enforceable control loop | [GitHub Code Quality](https://github.blog/changelog/2026-07-20-github-code-quality-is-now-generally-available/) |
| Repository-scoped AI engineering observability | Accelerating | AI coding activity can be assessed against repository criticality, delivery, quality, security, rework, and cost | [GitHub repository metrics](https://github.blog/changelog/2026-07-17-repository-level-github-copilot-usage-metrics-generally-available/) |
| Lifecycle-aware agent skill security | Emerging | Reusable skills create policy boundaries across admission, retrieval, selection, execution, update, and revocation | [SkillSec-Eval](https://arxiv.org/abs/2607.13987) |
| AI data-pipeline attack-surface engineering | Accelerating | Dataset loaders, templates, workers, credentials, clusters, and artifact publication can provide execution and lateral-movement paths | [Hugging Face disclosure](https://huggingface.co/blog/security-incident-july-2026) |
| Adaptive adversarial evaluation | Accelerating | Static suites can saturate; iterative attackers and held-out environments better represent production-agent risk | [OpenAI GPT-Red](https://openai.com/index/unlocking-self-improvement-gpt-red/) |
| Modular prompt transpilation | Emerging | Prompt reliability increasingly depends on modules, dependency validation, generated artifacts, and CI/CD gates | [Google Developers Blog](https://developers.googleblog.com/building-scalable-ai-agents-with-modular-prompt-transpilation/) |

## Latest cycle status

| Collection time | Outcome | Audit |
|---|---|---|
| 2026-07-21 00:10 IST | Promoted OpenAI’s long-horizon agent-safety disclosure. It adds concrete evidence for trajectory-level policy, staged deployment, active monitoring, incident-derived evaluations, pause/rollback, and controlled redeployment. Other monitored areas produced no additional qualifying non-duplicate change. | [Review record](hourly/2026/07/21/00-10_IST.md) |
