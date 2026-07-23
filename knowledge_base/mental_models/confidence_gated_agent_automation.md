# Confidence-Gated Agent Automation

## Core idea

Agent autonomy should be routed per proposed action using calibrated confidence, consequence, reversibility, policy, and authorization—not granted uniformly to the whole agent.

GitHub Issues now exposes action-level rationale, confidence, optional approvals, and repository-level automation thresholds for supported issue mutations. GitHub also explicitly states that approvals are workflow convenience rather than a server-side security boundary. [Primary source](https://github.blog/changelog/2026-07-23-agent-automation-controls-in-github-issues-in-public-preview)

## Decision pipeline

```text
observation and evidence
  → proposed action
  → rationale and confidence
  → calibration model
  → consequence / reversibility class
  → policy decision
  → auto-apply | review | deny
  → immutable execution record
  → outcome feedback
  → recalibration
```

## Decision envelope

| Field group | Required contents |
|---|---|
| Provenance | Evidence references, source timestamps, agent/model version, tool version |
| Proposal | Action type, target, payload, rationale, raw confidence |
| Governance | Calibration version, policy version, risk class, required approval, authorization decision |
| Execution | Actor identity, approval state, execution timestamp, tool response |
| Outcome | Accepted, rejected, reverted, corrected, downstream impact, reviewer reason |

## Calibration contract

A confidence score is operationally useful only when it is calibrated for the specific action and deployment distribution.

| Metric | Meaning |
|---|---|
| False-auto-apply rate | Incorrect actions executed without review |
| Unnecessary-review rate | Correct actions held for avoidable review |
| Reviewer override rate | Suggested actions changed or rejected by humans |
| Reversion/correction rate | Applied actions later undone or repaired |
| Expected action loss | Probability-weighted business cost of errors and review |
| Coverage at risk bound | Share of actions automated while staying under an agreed error-cost limit |

## Architecture rules

1. Use different thresholds for labels, assignment, field changes, closure, deletion, and externally visible actions.
2. Treat reversibility and blast radius as first-class policy inputs.
3. Keep authorization, scoped identity, and server-side enforcement independent of approval UX.
4. Persist the complete decision envelope, not rationale text alone.
5. Recalibrate from accepted, rejected, reverted, and corrected actions.
6. Default unknown action classes and distribution shifts to review or denial.

## Failure modes

| Failure mode | Why it happens | Control |
|---|---|---|
| Confidence theatre | Raw model probability is treated as truth | Reliability testing and action-specific calibration |
| One global threshold | Different actions have different error costs | Cost-sensitive per-action routing |
| Approval-as-security | Review surface is mistaken for authorization | Independent server-side policy enforcement |
| Rationale-only audit | Explanation is stored without evidence or execution context | Versioned decision envelope |
| Silent distribution drift | Issue mix or agent version changes | Rolling calibration and drift monitoring |
| Review overload | Too many low-risk actions are held | Optimize thresholds against expected loss and reviewer capacity |

## Credible language

> “Confidence should route actions only after calibration against action-specific error cost.”

> “Rationale is provenance, not proof of correctness.”

> “Approvals manage workflow; permissions enforce security.”

## Terms to avoid misusing

| Term | Correct use | Common misuse |
|---|---|---|
| High confidence | A calibrated score associated with a measured error rate for a defined action and distribution | A synonym for safe or correct |
| Human-in-the-loop | A designed intervention point with clear decision rights and measured review value | Any UI containing an approve button |
| Audit trail | Reconstructable evidence, policy, identity, proposal, decision, execution, and outcome | Rationale text alone |
| Autonomous | A bounded action class permitted under explicit policy and evidence | Unrestricted agent operation |

## POC target

Build a replayable issue-triage system covering labels, fields, assignment, and closure. Compare three policies: review-all, one global confidence threshold, and calibrated action-specific routing. Promote only if the calibrated policy reduces review load without exceeding the agreed expected-loss bound and every action remains reconstructable and reversible.
