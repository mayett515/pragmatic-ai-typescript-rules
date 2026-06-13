---
description: "Procedural shell rules for async workflows and side effects"
globs: "**/*.{ts,tsx}"
alwaysApply: false
version: "3.0.0"
protocol_compat: "mcp: 2026-05"
dependencies: []
priority_schema: "critical > strong > guideline"
---

# Procedural Shell Index

<meta-instruction>
The procedural shell coordinates real-world actions. It is allowed to be imperative and step-by-step. The shell should call the functional core for decisions and boundaries/adapters for capabilities.
</meta-instruction>

<routing-logic>
IF the task touches async side effects, service methods, route handlers, commands, scripts, imports, exports, or workflows:
THEN load `.ai-rules/04-procedural-shell/01-orchestration.md`.

IF the task touches DB/API/email/payment/filesystem/logging/framework responses:
THEN load `.ai-rules/04-procedural-shell/02-side-effects.md`.

IF the task touches queues, workers, retries, cancellation, concurrent execution, or background jobs:
THEN load `.ai-rules/04-procedural-shell/04-workers-concurrency.md`.
</routing-logic>

## Shell Directives

<positive-directives>
- Write shells as clear procedures: load facts, decide, execute effects, return result.
- Use early returns for expected failures.
- Keep side effects in obvious order.
- Delegate business decisions to pure helpers.
- Delegate external system weirdness to boundaries/adapters.
</positive-directives>

## Shell Constraints

<absolute-constraints>
- DO NOT bury policy logic inside DB calls or framework response construction.
- DO NOT use clever promise chains when `async/await` is clearer.
- DO NOT fire-and-forget without explicit failure strategy.
- DO NOT hide retries or timeouts inside pure-looking helpers.
</absolute-constraints>

<context>
<example>
// Good: procedural shell reads like a workflow.
const order = await deps.orders.findById(input.orderId);
const decision = decideReturn(order, input);
if (!decision.ok) return decision;
await deps.payments.refund(...);
</example>

<example>
// Bad: policy, DB, payment, email all inline with generic throws.
async function requestReturn(input: any) { /* 300 lines */ }
</example>
</context>

<pre-flight-checklist>
1. [ ] Are side effects obvious and ordered?
2. [ ] Are decisions delegated to core helpers?
3. [ ] Are dependencies owned by an honest boundary?
</pre-flight-checklist>
