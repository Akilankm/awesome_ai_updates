# Meeting Brief

**Updated:** 2026-07-15 13:07 IST

## Language worth using

| Term | Precise meaning | Credible meeting formulation | Evidence |
|---|---|---|---|
| Socio-technical adoption | Productivity depends on technology plus peer diffusion, workflow fit, retained usage, and organizational enablement | “We should treat coding-agent rollout as a socio-technical adoption program, not a license-provisioning exercise.” | [Microsoft rollout study](https://arxiv.org/abs/2607.01418) |
| Merge-aware orchestration | Agent task allocation accounts for overlapping files, branches, dependencies, and integration risk | “Before scaling parallel coding agents, we need merge-aware orchestration and explicit ownership boundaries.” | [Agent PR concurrency study](https://arxiv.org/abs/2607.04697) |
| Clean-room evaluation | Evaluation prevents access to leaked answers or uncontrolled external evidence | “The research-agent benchmark should use a clean-room evidence harness so we measure synthesis rather than leakage.” | [SciConBench](https://arxiv.org/abs/2606.11337) |
| Claim-level evaluation | Conclusions are decomposed into atomic facts and scored for correctness and coverage | “Answer-level similarity is insufficient; we need factual precision and recall at the claim level.” | [SciConBench](https://arxiv.org/abs/2606.11337) |

## Questions that demonstrate depth

| Situation | Question |
|---|---|
| Coding-agent rollout | “What is our retained-use rate, and are we measuring accepted output, review burden, and rework alongside merged PRs?” |
| Multiple coding agents | “How are tasks partitioned to prevent file overlap, structural conflicts, and incompatible dependency changes?” |
| Deep-research system | “Can the agent abstain when sources conflict or when claim-level evidence is incomplete?” |
| Benchmark discussion | “Does this benchmark control tool access, information leakage, inference budget, and evidence availability?” |

## Claims to avoid

| Weak claim | Why it is unsafe | Better formulation | Evidence |
|---|---|---|---|
| “Coding agents improve every engineer’s productivity.” | Adoption and measured impact are heterogeneous; merged PRs are only a proxy for value | “The studied rollout found higher merged-PR output among adopters, while retention and organizational context remained important.” | [Paper](https://arxiv.org/abs/2607.01418) |
| “More agents mean faster delivery.” | Concurrent cross-agent work showed higher textual conflict rates | “Parallel agents can increase throughput only when coordination and integration costs are controlled.” | [Paper](https://arxiv.org/abs/2607.04697) |
| “Deep research produces reliable conclusions.” | Clean-room factual synthesis remained weak in the reported benchmark | “Research agents improve evidence gathering, but conclusions still require claim-level validation and abstention.” | [Paper](https://arxiv.org/abs/2606.11337) |