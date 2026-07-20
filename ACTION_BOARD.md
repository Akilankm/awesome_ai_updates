# AI Engineering Action Board

**Updated:** 2026-07-21 00:10 IST

## Build

| Priority | Action | Deliverable | Success criteria | Career value | Evidence |
|---:|---|---|---|---:|---|
| 1 | Build a trajectory-level agent monitor | Event stream, cumulative-policy evaluator, immutable replay log, monitor alerts, and pause/resume control | Detects seeded multi-step constraint bypass and privilege expansion while preserving legitimate long-running task completion | 9.9/10 | [OpenAI](https://openai.com/index/safety-alignment-long-horizon-models/) |
| 2 | Build an incident-to-evaluation pipeline | Reproduction template, trajectory capture, severity rubric, replay environment, regression test, owner, and release threshold | Every material agent incident becomes a replayable test before redeployment | 9.9/10 | [OpenAI](https://openai.com/index/safety-alignment-long-horizon-models/) |
| 3 | Harden a long-running agent sandbox | Scoped workload identity, deny-by-default egress, short-lived credentials, syscall/container controls, rate limits, and kill switch | Persistent probing cannot expand identity, exfiltrate credentials, or reach unapproved destinations | 9.9/10 | [OpenAI](https://openai.com/index/safety-alignment-long-horizon-models/) |
| 4 | Extend the repository-level AI engineering scorecard with quality gates | Data model joining AI activity, deterministic and AI findings, coverage, gate outcomes, remediation, PR flow, defects, rework, and cost | Produces evidence-backed observe/evaluate/block recommendations by repository class without ranking individuals | 9.8/10 | [GitHub Code Quality](https://github.blog/changelog/2026-07-20-github-code-quality-is-now-generally-available/) |
| 5 | Define separate execution profiles for coding and review agents | Runner, firewall, egress, secrets, setup, logging, retention, and failure policies for each agent class | Review agents cannot inherit unnecessary implementation privileges | 9.7/10 | [GitHub code-review controls](https://github.blog/changelog/2026-07-17-copilot-code-review-customization-and-configurability-improvements/) |
| 6 | Build a governed agent-skill registry POC | Provenance, ownership, admission checks, trust-aware retrieval, capability policy, version pinning, revocation, and rollback | No skill reaches production tools without approved provenance and version-specific evaluation | 9.6/10 | [SkillSec-Eval](https://arxiv.org/abs/2607.13987) |
| 7 | Build an adaptive prompt-injection evaluation harness | Attacker loop, held-out tool environments, attack provenance, fixed regressions, security–utility scorecard, and gate | Finds attacks missed by the fixed suite while preserving benign completion | 9.7/10 | [OpenAI GPT-Red](https://openai.com/index/unlocking-self-improvement-gpt-red/) |
| 8 | Build an AI data-pipeline threat model and control matrix | Attack tree and control map for loaders, parsers, templates, workers, secrets, clusters, and publication | Every executable ingestion path has an owner, sandbox, credential boundary, egress rule, detection, and response playbook | 9.8/10 | [Hugging Face](https://huggingface.co/blog/security-incident-july-2026) |

## Study

| Topic | Why now | Learning outcome | Priority | Evidence |
|---|---|---|---:|---|
| Trajectory-level policy evaluation | Long-horizon failures can emerge from sequences of individually acceptable actions | Model cumulative intent, constraint bypass, privilege expansion, destination, and outcome across event streams | 1 | [OpenAI](https://openai.com/index/safety-alignment-long-horizon-models/) |
| Reversible agent operations | OpenAI used pause, safeguard redesign, replay testing, and limited redeployment | Design staged rollout, kill switches, checkpointing, forensic replay, and controlled access expansion | 1 | [OpenAI](https://openai.com/index/safety-alignment-long-horizon-models/) |
| Long-running workload isolation | Persistence increases opportunities to probe and exploit environmental weaknesses | Design scoped identities, credential rotation, egress controls, sandbox layers, monitor intervention, and containment metrics | 1 | [OpenAI](https://openai.com/index/safety-alignment-long-horizon-models/) |
| Layered code-quality architecture | GitHub combines deterministic CodeQL with AI-assisted detection and Autofix | Distinguish reproducible static evidence from probabilistic findings and design separate metrics | 1 | [GitHub Code Quality](https://github.blog/changelog/2026-07-20-github-code-quality-is-now-generally-available/) |
| Attacker–defender self-play | OpenAI reports automated attackers in production-model training | Design attacker loops, held-out environments, transfer tests, and capability-preservation metrics | 1 | [OpenAI GPT-Red](https://openai.com/index/unlocking-self-improvement-gpt-red/) |
| AI workload and data-pipeline security | A primary incident connected dataset processing to credentials and lateral movement | Design secure workers, workload identity, admission policy, artifact integrity, and incident response | 1 | [Hugging Face](https://huggingface.co/blog/security-incident-july-2026) |

## Internal proposal opportunities

| Proposal | Business value | POC scope | Guardrail | Evidence |
|---|---|---|---|---|
| Long-horizon agent control plane | Enables durable autonomy without relying on per-call approvals alone | One sandboxed agent with scoped identity, deny-by-default egress, trajectory monitor, human intervention, replay, and rollback | No irreversible production actions; immutable audit; bounded duration and spend; explicit kill switch | [OpenAI](https://openai.com/index/safety-alignment-long-horizon-models/) |
| Incident-derived agent evaluation service | Converts operational failures into reusable safety evidence and prevents recurrence | Capture one seeded incident, reconstruct its environment, replay it across versions, and enforce regression thresholds | Redact secrets; preserve provenance; require severity and owner sign-off before closure | [OpenAI](https://openai.com/index/safety-alignment-long-horizon-models/) |
| Quality-adjusted AI coding control plane | Converts AI coding adoption into enforceable quality, delivery, risk, and cost governance | One repository joining activity, findings, coverage, gates, remediation, rework, deployment, and total cost | Start in evaluate mode; do not rank individuals; require minimum samples, exceptions, privacy review, and rollback | [GitHub Code Quality](https://github.blog/changelog/2026-07-20-github-code-quality-is-now-generally-available/) |
| Adaptive agent-security release gate | Finds agent-specific attacks that static prompt suites miss | Production-faithful sandbox, fixed plus adaptive attacks, security–utility scorecard, and rollback | No irreversible production actions; block release on unacceptable attack success or utility regression | [OpenAI GPT-Red](https://openai.com/index/unlocking-self-improvement-gpt-red/) |
| Secure AI ingestion baseline | Reduces remote-code, secret-exposure, lateral-movement, and artifact-integrity risk | One dataset pipeline with sandboxing, least privilege, egress restriction, workload identity, signed outputs, and telemetry | Treat external datasets and templates as hostile; no static cloud credentials on workers | [Hugging Face](https://huggingface.co/blog/security-incident-july-2026) |
