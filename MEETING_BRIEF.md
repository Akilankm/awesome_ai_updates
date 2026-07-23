# Meeting Brief

**Updated:** 2026-07-24 04:09 IST

## Language worth using

| Term | Precise meaning | Credible meeting formulation | Evidence |
|---|---|---|---|
| Stateless MCP interoperability | A versioned tool-RPC contract with no hidden protocol session, explicit application state, method-aware routing, authorization, trace propagation, and executable conformance | “MCP is moving from session-oriented transport semantics to stateless tool RPC with explicit application state.” | [GitHub](https://github.blog/changelog/2026-07-23-github-mcp-server-supports-the-next-mcp-specification) · [MCP](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/) |
| Executable protocol conformance | Automated client and server scenarios that verify behavior against a declared specification version | “Conformance is becoming an executable release gate, not a documentation claim.” | [Conformance suite](https://github.com/modelcontextprotocol/conformance) · [MCP](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/) |
| Explicit workflow state | Application or task state represented by scoped handles rather than hidden transport affinity | “Stateless protocol does not mean stateless workflow; it makes state ownership explicit and testable.” | [MCP](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/) |
| Confidence-gated agent automation | Routing each proposed action to auto-apply, review, or deny using calibrated confidence, action consequence, reversibility, policy, and authorization | “Autonomy should be tuned per action class and error cost, not granted uniformly to the whole agent.” | [GitHub](https://github.blog/changelog/2026-07-23-agent-automation-controls-in-github-issues-in-public-preview) |
| Hardware-heterogeneous kernel authoring | Expressing kernel intent at a high level while lowering through accelerator-specific backends and validating each backend independently | “Performance portability is a compiler-and-evaluation contract, not identical low-level code across accelerators.” | [PyTorch](https://pytorch.org/blog/helion-on-tpu-towards-hardware-heterogeneous-kernel-authoring/) |
| Governed production-agent lifecycle | A workflow-specific operating model joining scoped access, policies, actions, evaluation, escalation, telemetry, controlled changes, rollout, and rollback | “A production agent is a governed service lifecycle, not a model endpoint with tools.” | [OpenAI Presence](https://openai.com/index/introducing-openai-presence/) |

## Questions that demonstrate depth

| Situation | Question | Evidence |
|---|---|---|
| MCP migration | “Which assumptions currently live in transport sessions, and how will they move into explicit, identity-bound workflow or task handles?” | [MCP](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/) |
| MCP compatibility | “Are we testing only SDK compatibility, or the full client–gateway–server–authorization path against versioned conformance and workload replay?” | [GitHub](https://github.blog/changelog/2026-07-23-github-mcp-server-supports-the-next-mcp-specification) · [Conformance suite](https://github.com/modelcontextprotocol/conformance) |
| MCP gateway | “Can routing, rate limiting, policy, and tracing use method and name metadata while still rejecting header and body mismatches?” | [MCP](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/) |
| Confidence routing | “Is the confidence score calibrated separately for each action type, and what false-auto-apply rate and business loss does the threshold imply?” | [GitHub](https://github.blog/changelog/2026-07-23-agent-automation-controls-in-github-issues-in-public-preview) |
| Custom-kernel portability | “Which parts are semantic intent, which are backend lowering, and how are correctness and performance validated per accelerator?” | [PyTorch](https://pytorch.org/blog/helion-on-tpu-towards-hardware-heterogeneous-kernel-authoring/) |
| Production-agent design | “What exact job contract, identities, actions, policies, evaluations, escalations, and rollback paths are bound to the deployment?” | [OpenAI Presence](https://openai.com/index/introducing-openai-presence/) |

## Claims to avoid

| Weak claim | Why it is unsafe | Better formulation | Evidence |
|---|---|---|---|
| “Stateless MCP means the workflow has no state.” | Only protocol-level session state is removed; applications can and often must retain explicit state | “Workflow state moves into explicit, scoped handles instead of hidden transport affinity.” | [MCP](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/) |
| “The SDK is backward compatible, so migration is complete.” | Application behavior, deprecated features, authorization, errors, and Tasks semantics may still change | “SDK compatibility is one gate; conformance, authorization, integration, and replay are separate.” | [GitHub](https://github.blog/changelog/2026-07-23-github-mcp-server-supports-the-next-mcp-specification) · [MCP](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/) |
| “Passing conformance proves production readiness.” | Conformance validates protocol behavior, not domain correctness, scale, latency, operational resilience, or rollback | “Conformance is the interoperability floor, followed by operational and business gates.” | [Conformance suite](https://github.com/modelcontextprotocol/conformance) |
| “High-confidence actions are safe.” | Confidence may be uncalibrated, distribution-dependent, and blind to consequence | “High confidence can support routing only after action-specific calibration and loss analysis.” | [GitHub](https://github.blog/changelog/2026-07-23-agent-automation-controls-in-github-issues-in-public-preview) |
| “Helion makes GPU and TPU kernels the same.” | The TPU path uses distinct Pallas lowering and accelerator-specific tuning | “Helion preserves high-level intent while producing backend-specific implementations.” | [PyTorch](https://pytorch.org/blog/helion-on-tpu-towards-hardware-heterogeneous-kernel-authoring/) |
