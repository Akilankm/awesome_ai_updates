# Hardware-Heterogeneous Kernel Authoring

**Created:** 2026-07-24 01:11 IST

## Core model

A portable ML kernel system should preserve **semantic intent** while allowing each accelerator backend to specialize code generation, scheduling, pipelining, memory movement, and tuning.

```text
kernel intent
  → semantic validation
  → backend selection
  → backend-specific lowering
  → autotuning/search
  → generated executable
  → numerical conformance
  → performance envelope
  → deployment artifact + fallback
```

This is more precise than claiming one low-level kernel is portable. Helion’s TPU work demonstrates the pattern by compiling a PyTorch-embedded high-level DSL to Pallas while Helion’s established architecture targets Triton-oriented GPU paths. [PyTorch](https://pytorch.org/blog/helion-on-tpu-towards-hardware-heterogeneous-kernel-authoring/) · [Helion](https://github.com/pytorch/helion)

## Architectural layers

| Layer | Responsibility | Evidence to retain |
|---|---|---|
| Kernel intent | Mathematical operation, shape semantics, dtype behavior, masking, numerical expectations | Reference implementation, property tests, tolerance policy |
| Backend contract | Supported operations, layouts, dtypes, hardware generations, compiler requirements | Compatibility matrix and explicit unsupported cases |
| Lowering | Translate intent into backend-native primitives and schedules | Generated source/IR, compiler versions, lowering configuration |
| Autotuning | Search backend-specific tile, pipeline, memory, and scheduling choices | Search space, seed, budget, winning configuration, measurements |
| Conformance | Verify numerical and semantic equivalence | Error distributions, edge cases, determinism, failure cases |
| Performance envelope | Measure more than one preferred shape | Compile time, tuning time, latency, throughput, memory, power/cost where available |
| Deployment | Package the selected implementation under a defined validity envelope | Hardware/software fingerprint, cache key, rollback and fallback |

## Mental-model corrections

| Weak assumption | Better model |
|---|---|
| One source kernel should generate identical code everywhere | One semantic definition may generate materially different code per backend |
| A high-level DSL removes hardware expertise | It relocates hardware expertise into backend design, search spaces, validation, and performance engineering |
| One peak benchmark proves portability | Portability is a matrix of correctness coverage, performance ratio, tuning cost, failures, and maintenance burden |
| Autotuning is a temporary development step | The selected result and its validity envelope are versioned deployment artifacts |
| Custom kernel success is only a throughput question | Compile latency, tuning cost, numerical behavior, maintainability, fallback, and operational stability are equally material |

## Evaluation contract

| Dimension | Minimum measurement |
|---|---|
| Correctness | Reference comparison across representative and adversarial shapes with declared tolerances |
| Coverage | Supported shapes, dtypes, layouts, hardware versions, and unsupported combinations |
| Build behavior | Compilation success rate, compile latency, cacheability, and compiler-version sensitivity |
| Tuning economics | Search duration, accelerator-hours, cache hit rate, invalidation frequency |
| Runtime | P50/P95 latency, throughput, memory, utilization, warmup, and batch/sequence sensitivity |
| Reliability | Reproducibility, determinism expectations, regression rate, fallback success |
| Economics | Total cost per accepted workload, including tuning and engineering maintenance |

## Architecture implications

1. **Use backend adapters, not backend leakage.** Keep accelerator-specific details below a stable semantic boundary.
2. **Treat generated code as evidence.** Store IR/source, compiler logs, and selected tuning configuration for review and replay.
3. **Version the validity envelope.** Hardware generation, compiler, runtime, dtype, shape family, and tuning policy belong in the artifact identity.
4. **Retain a safe fallback.** Framework-native kernels should remain available when the tuned artifact is invalid, unavailable, or regresses.
5. **Gate promotion on a matrix.** Promote only after correctness, performance, operational, and economic criteria pass across representative workloads.

## Credible language

> “Performance portability is a compiler-and-evaluation contract, not identical low-level code across accelerators.”

> “The high-level kernel intent can remain stable while each backend specializes scheduling, memory movement, and pipelining.”

> “Autotuning output should be versioned like a deployable artifact because its validity depends on hardware, shapes, precision, and compiler state.”

## Terms to avoid misusing

| Term | Avoid | Precise use |
|---|---|---|
| Performance portable | “Fast everywhere” | Meets declared correctness and performance thresholds across a defined backend envelope |
| Hardware agnostic | “No hardware-specific work exists” | User-facing semantics are insulated from backend-specific lowering and tuning |
| Autotuned | “Automatically optimal” | Best observed configuration within a declared search space, budget, workload, and environment |
| Production ready | “A benchmark ran once” | Reproducible, monitored, versioned, fallback-enabled, and validated on representative production envelopes |

## Learning and POC target

Build one kernel portability experiment around a production-relevant bottleneck:

- Implement or adapt one attention, normalization, or fused elementwise kernel.
- Compare the high-level DSL route against framework-native baselines.
- Use at least three shape families and declared numerical tolerances.
- Record compile time, tuning time, runtime latency, throughput, memory, failures, and fallback behavior.
- Produce a portability scorecard rather than a single winner claim.

## Source basis

| Source | Contribution | Evidence quality |
|---|---|---|
| [PyTorch: Helion on TPU](https://pytorch.org/blog/helion-on-tpu-towards-hardware-heterogeneous-kernel-authoring/) | TPU-to-Pallas backend, autotuning behavior, and reported TPU v7 flash-attention performance | **A-** for architecture; **B+** for unreproduced benchmark claim |
| [pytorch/helion](https://github.com/pytorch/helion) | Maintained implementation, DSL positioning, Triton-oriented backend context, installation and generated-code workflow | **A** primary implementation source |