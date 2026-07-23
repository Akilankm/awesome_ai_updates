# Stateless MCP Interoperability

## Core thesis

The durable architecture is not “an agent connected to an MCP server.” It is a **versioned interoperability contract** joining stateless transport, explicit workflow state, method-aware gateways, authorization, trace propagation, conformance testing, and migration discipline.

**Evidence:** [MCP `2026-07-28` release candidate](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/) · [GitHub MCP Server implementation](https://github.blog/changelog/2026-07-23-github-mcp-server-supports-the-next-mcp-specification) · [MCP conformance suite](https://github.com/modelcontextprotocol/conformance)

## Layered model

| Layer | Responsibility | Required evidence |
|---|---|---|
| Protocol | Versioned request/response semantics, headers, schemas, errors, and extensions | Conformance scenarios |
| Gateway | Routing, rate limiting, policy, logging, secret scanning, and trace propagation | Method/name policy tests and failure injection |
| Identity | Issuer validation, credential binding, scopes, step-up, and token lifecycle | OAuth/OIDC negative and migration tests |
| Application state | Explicit handles for browser, basket, task, job, or transaction state | Ownership, expiry, replay, concurrency, and authorization tests |
| Long-running work | Task creation, status, update, cancellation, and terminal outcomes | Lifecycle and idempotency tests |
| Tool semantics | Business correctness, side effects, reversibility, and schema bounds | Integration and domain evaluation |
| Operations | Horizontal scaling, latency, tracing, caching, retries, and rollback | Load, chaos, observability, and rollback evidence |

## Architecture

```text
agent host
  → protocol adapter and version negotiation
  → stateless request
  → method/name-aware gateway
      → authorization policy
      → rate limit
      → trace propagation
  → any compatible MCP server replica
  → explicit application/task handle
  → downstream dependency
  → structured result
  → executable conformance and integration evidence
```

## Design rules

1. Keep protocol state, application state, identity state, and task state separate.
2. Represent workflow state through explicit, scoped handles rather than hidden transport affinity.
3. Treat the protocol version as deployment metadata and a CI dimension.
4. Run official conformance tests, but do not confuse conformance with production readiness.
5. Validate authorization independently from tool correctness.
6. Bound JSON Schema depth, validation time, payload size, and external reference behavior.
7. Propagate W3C trace context across the full host → client → server → downstream path.
8. Maintain a rollback adapter for the previous specification during migration.

## Evaluation contract

| Dimension | Metric or test | Failure meaning |
|---|---|---|
| Protocol conformance | Passed scenarios by client/server/spec version | Wire-level incompatibility |
| State correctness | Handle ownership, expiry, idempotency, concurrency | Cross-user leakage, duplication, or lost workflow state |
| Authorization | Issuer, audience, scope, redirect, credential binding, step-up | Identity confusion or privilege escalation |
| Horizontal scaling | Requests distributed across replicas without affinity | Hidden session coupling remains |
| Observability | End-to-end trace continuity and operation attribution | Incidents cannot be reconstructed |
| Reliability | Retry, cancellation, timeout, partial failure, and replay behavior | Long-running work is unsafe or irrecoverable |
| Security | Header/body mismatch, schema bombs, rate abuse, secret leakage | Gateway or parser boundary is exploitable |
| Migration | Dual-version compatibility and rollback | Upgrade cannot be safely staged |

## Failure modes

| Failure mode | Why it occurs | Control |
|---|---|---|
| “Stateless” server stores user workflow state globally | Transport simplification is mistaken for application-state design | Explicit scoped handles and tenancy tests |
| SDK upgrade is treated as completed migration | Application assumptions survive beneath compatible APIs | Workload replay and feature-by-feature migration matrix |
| Gateway trusts headers without validating body agreement | Metadata can be spoofed | Reject method/name mismatches and validate downstream payloads |
| Conformance green, production unsafe | Protocol tests omit domain and operational risks | Separate conformance, security, reliability, and business gates |
| Task handles become bearer secrets | Handle ownership is not bound to identity | Opaque scoped handles, authorization checks, expiry, rotation |
| Trace baggage leaks sensitive data | Observability metadata is overfilled | Baggage allowlist, size bounds, redaction, and retention policy |

## Meeting language

- “Stateless protocol does not mean stateless workflow; it means state becomes explicit, portable, and testable.”
- “MCP conformance is the interoperability floor, not the production-readiness ceiling.”
- “The migration unit is the complete client–gateway–server–authorization path, not the SDK package.”
- “Method-aware HTTP metadata enables routing and policy without making payload validation optional.”

## Terms to use carefully

| Term | Precise use |
|---|---|
| Stateless MCP | No hidden protocol session or sticky affinity is required |
| Conformant | Passes declared protocol scenarios for a specified version |
| Compatible | Interoperates for a defined capability and version matrix |
| MCP-native | Uses explicit versioning, authorization, observability, lifecycle, and conformance contracts |
| Production ready | Has conformance plus security, scale, reliability, rollback, and business evidence |

## POC target

Build a provider-neutral MCP interoperability lab with:

- one host and two server replicas behind round-robin routing;
- explicit workflow and long-running-task handles;
- method/name-aware gateway policy;
- OAuth/OIDC validation and negative tests;
- OpenTelemetry trace continuity;
- official client and server conformance suites;
- previous-version fallback and rollback;
- failure injection for replica loss, retries, cancellation, schema abuse, and authorization errors.

Promotion requires passing protocol conformance, horizontal failover, authorization isolation, task-lifecycle, trace-correlation, and rollback tests under a documented version matrix.
