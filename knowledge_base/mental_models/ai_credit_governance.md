# AI Credit Governance

## Control stack

| Control | Purpose | Failure if omitted | Evidence |
|---|---|---|---|
| License-funded credit pool | Allocates included AI entitlement to a cost center | One group can consume credits funded by another group’s licenses | [GitHub pools](https://github.blog/changelog/2026-07-20-ai-credit-pools-for-cost-centers-in-the-billing-ui/) |
| Metered-spend budget | Caps charges after included credits are exhausted | Overage can continue without a financial boundary | [GitHub pools](https://github.blog/changelog/2026-07-20-ai-credit-pools-for-cost-centers-in-the-billing-ui/) |
| Block-or-overage policy | Defines runtime behavior at the entitlement limit | Workloads fail unpredictably or spend continues without explicit approval | [GitHub pools](https://github.blog/changelog/2026-07-20-ai-credit-pools-for-cost-centers-in-the-billing-ui/) |
| User consumption visibility | Shows current-cycle credits consumed even when no individual budget exists | Users cannot contextualize or adjust their own consumption | [GitHub usage visibility](https://github.blog/changelog/2026-07-20-copilot-users-can-now-see-ai-credits-used-per-billing-cycle/) |
| Outcome attribution | Links consumption to repositories, workloads, quality gates, and accepted changes | Token or credit totals become cost data without value evidence | [GitHub usage visibility](https://github.blog/changelog/2026-07-20-copilot-users-can-now-see-ai-credits-used-per-billing-cycle/) |

## Mental model

AI economics should be governed as a layered system:

`entitlement allocation → user/workload consumption → metered budget → block or overage decision → accepted outcome → quality and rework adjustment`

Credits are an accounting unit, not a productivity metric. The decision unit is the total cost of a useful, accepted, quality-gated outcome.

## Metrics

| Metric | Interpretation |
|---|---|
| Credits per accepted change | Consumption efficiency after review and quality gates |
| Total cost per deployed change | Credits plus licenses, compute, review, remediation, and rework |
| Pool utilization by workload class | Whether included entitlement matches organizational priorities |
| Budget exhaustion forecast | Time-to-limit under current consumption and seasonality |
| Overage value ratio | Incremental accepted outcome value divided by incremental metered spend |
| Wasted-credit rate | Credits spent on abandoned, reverted, duplicate, or rejected work |

## Guardrails

Do not rank individuals by raw credit use. Normalize by task type, repository criticality, model, agent mode, review burden, and delivered outcome. Publish allocation rules, warning thresholds, exceptions, hard-stop behavior, and escalation paths before enforcement.