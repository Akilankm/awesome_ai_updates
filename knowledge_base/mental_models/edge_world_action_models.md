# Edge World-Action Models

## Core model

| Layer | Role | Engineering question | Evidence |
|---|---|---|---|
| Observation | Encodes current visual and multimodal state | Are sensor timing, calibration, missing data, and uncertainty represented? | [Cosmos 3 Edge](https://huggingface.co/blog/nvidia/cosmos3edge) |
| Reasoning | Interprets state and task using autoregressive processing | Is reasoning latency bounded and is provenance preserved? | [Cosmos 3 Edge](https://huggingface.co/blog/nvidia/cosmos3edge) |
| World prediction | Generates plausible future states through diffusion processing | Are predicted consequences calibrated against observed outcomes? | [Cosmos 3 Edge](https://huggingface.co/blog/nvidia/cosmos3edge) |
| Action | Maps shared representation into embodiment-specific geometric vectors | Are translation, rotation, and manipulation outputs valid for the target controller? | [Cosmos 3 Edge](https://huggingface.co/blog/nvidia/cosmos3edge) |
| Control loop | Executes, observes the result, and replans | Can the system detect divergence, stop safely, and recover? | [Cosmos 3 Edge](https://huggingface.co/blog/nvidia/cosmos3edge) |

## Architecture principle

A shared representation can reduce integration boundaries between perception, prediction, and policy, but it does not remove modality-specific validation, deterministic safety controls, hardware limits, or recovery logic. The deployment unit is the complete observation–prediction–action loop.

## Evaluation scorecard

| Dimension | Minimum evidence |
|---|---|
| Task success | Repeated success across controlled scenarios and perturbations |
| Action validity | Controller-compatible actions within physical and policy constraints |
| Consequence accuracy | Agreement between predicted and observed post-action states |
| Real-time behavior | End-to-end latency, jitter, throughput, and missed deadlines on target hardware |
| Resource envelope | Memory, power, thermal behavior, sustained performance, and degradation |
| Robustness | Sensor noise, occlusion, distribution shift, embodiment variation, and recovery |
| Safety | Independent limits, emergency stop, bounded workspace, audit, and fallback controller |

## Career implication

Physical-AI engineers need competence across multimodal transformers, diffusion models, robotics policy learning, control-loop evaluation, edge inference optimization, hardware profiling, safety engineering, and trajectory observability—not only VLM prompting.