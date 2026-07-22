# Governed Production-Agent Lifecycle

## Core thesis

A production agent is not a model endpoint with tools. It is a versioned, workflow-specific service whose reliability depends on the combined design of job scope, knowledge boundaries, identity, approved actions, policies, escalation, evaluation, production evidence, controlled improvement, rollout, and rollback.

Primary evidence: [OpenAI Presence](https://openai.com/index/introducing-openai-presence/), published 2026-07-22.

## Lifecycle

```text
workflow selection
  → job contract
  → scoped knowledge and identity
  → approved action registry
  → policies, approvals, escalation
  → simulations and graders
  → limited deployment
  → production sessions and quality signals
  → issue classification
  → proposed change with provenance
  → regression comparison against production
  → human approval
  → canary rollout
  → monitor and rollback
  → versioned promotion or retirement
```

## Required contracts

| Contract | Required content | Failure prevented | Evidence |
|---|---|---|---|
| Job contract | User population, supported intents, success states, prohibited outcomes, escalation conditions | Scope drift and open-ended autonomy | [OpenAI Presence](https://openai.com/index/introducing-openai-presence/) |
| Access contract | Knowledge sources, identities, systems, data classes, credentials, and duration | Excess privilege and data leakage | [OpenAI Presence](https://openai.com/index/introducing-openai-presence/) |
| Action contract | Approved actions, parameters, preconditions, approval rules, postconditions, and rollback | Unauthorized or irreversible actions | [OpenAI Presence](https://openai.com/index/introducing-openai-presence/) |
| Evaluation contract | Common requests, edge cases, high-risk scenarios, outcome graders, policy adherence, tool correctness, and escalation quality | Demo-only validation and silent regressions | [OpenAI Presence](https://openai.com/index/introducing-openai-presence/) |
| Change contract | Evidence, proposed update, provenance, regression set, comparison baseline, approver, rollout, and rollback | Direct autonomous mutation of production behavior | [OpenAI Presence](https://openai.com/index/introducing-openai-presence/) |

## Mental-model shifts

| Old model | Updated model | Engineering consequence | Evidence |
|---|---|---|---|
| Agent equals model plus tools | Agent equals governed workflow service | Build lifecycle controls around the model | [OpenAI Presence](https://openai.com/index/introducing-openai-presence/) |
| Static pre-launch evaluation is sufficient | Evaluation continues through production evidence and controlled regression testing | Preserve sessions, escalations, graders, version lineage, and replay | [OpenAI Presence](https://openai.com/index/introducing-openai-presence/) |
| Feedback directly improves the live agent | Feedback creates a proposed change that is tested and approved | Separate observation, proposal, validation, approval, rollout, and rollback | [OpenAI Presence](https://openai.com/index/introducing-openai-presence/) |
| Human handoff is failure | Escalation is a designed control and quality signal | Measure correct escalation, premature escalation, and missed escalation separately | [OpenAI Presence](https://openai.com/index/introducing-openai-presence/) |

## Metrics

| Layer | Metrics |
|---|---|
| Outcome | Resolution quality, accepted completion, policy-correct outcome, customer or employee impact |
| Action | Correct tool, parameter validity, authorization, reversible completion, downstream consistency |
| Escalation | Correct escalation, missed escalation, unnecessary escalation, handoff completeness |
| Evaluation | Scenario coverage, grader reliability, regression detection, high-risk pass rate |
| Change | Proposal acceptance, regression delta, canary failure rate, rollback frequency, time to safe improvement |
| Economics | Total cost per accepted outcome, human review cost, escalation cost, rework, incident cost |

## Terms to avoid misusing

| Misuse | Correction |
|---|---|
| “Self-improving production agent” | Use “evidence-controlled agent improvement” unless production changes are proposed, tested, approved, and rolled out under explicit controls. |
| “Fully autonomous” | State the exact job, scoped access, approved actions, approval points, escalation rules, duration, and rollback capability. |
| “Human handoff rate proves quality” | Handoff is one signal; pair it with outcome quality, policy adherence, customer impact, missed escalation, and downstream rework. |
| “Agent accuracy” | Specify outcome, policy, tool-use, escalation, and regression metrics separately. |

## POC target

Implement one bounded support workflow with two policy versions and at least 50 replayable scenarios. Seed one policy change, one tool failure, one ambiguous high-risk request, and one escalation failure. Demonstrate that production evidence creates a versioned proposal, the proposal is compared against the deployed baseline, a human approves a canary, and the deployment can be rolled back without modifying production directly.
