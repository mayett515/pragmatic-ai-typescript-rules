---
description: "Functional core and procedural shell rules for TypeScript workflows"
globs: "**/*.{ts,tsx,mts,cts}"
alwaysApply: false
version: "1.0.0"
model_target: "gpt-5.5-family"
protocol_compat: "mcp: 2026-05"
dependencies: []
priority_schema: "critical > strong > guideline"
---

# Functional Core & Procedural Shell Contract

<meta-instruction>
Use this file when the task touches rules, validation, state transitions, workflows, async effects, service methods, route handlers, actions, jobs, or orchestration.
</meta-instruction>

## 1. Core and Shell Directives

<positive-directives>
- You MUST extract important policies, calculations, transitions, parser decisions, and eligibility checks into small pure functions when they carry meaning.
- You MUST keep database calls, network calls, filesystem calls, logging, email, payments, queues, timers, and randomness in the procedural shell.
- You MUST use readable step-by-step procedures for side-effect workflows.
- You MUST return typed results for expected business failures when that clarifies the caller contract.
- You MUST keep repository/framework conventions when they already define error and return shapes.
</positive-directives>

## 2. Hard Core and Shell Constraints

<absolute-constraints>
- DO NOT call external services from functions that look like calculations or validators.
- DO NOT mutate input objects in pure functions.
- DO NOT hide domain policy inside inline `if` statements in a large shell when the policy is testable independently.
- DO NOT force array chains or `reduce` where a simple loop over side effects is clearer.
- DO NOT use `Result<T, E>` for unexpected system failures that should remain exceptions.
</absolute-constraints>

## 3. Conditional Logic Gates

<conditional-logic>
IF a procedure contains more than one hidden policy decision:
THEN name the policies before splitting files.

IF a workflow does effects in order:
THEN keep it procedural and readable with early returns where helpful.

IF the code is a tiny pure utility:
THEN do not refactor unless a name or type improves clarity.

IF the code uses framework-specific response objects or exceptions:
THEN keep framework mapping at the boundary and keep the core framework-agnostic.
</conditional-logic>

## 4. Context and Examples

<context>
Procedural programming is part of the schema. Use functional code to decide, procedural code to orchestrate, and boundaries to own capabilities.

<example>
// Good: policy is pure; shell executes effects.
const decision = decideReturn(order, input);
if (!decision.ok) return decision;
await deps.payments.refund({ amount: decision.value.refundAmount });
</example>

<example>
// Bad: return policy, DB writes, payment, and email are all mixed inline.
if (order.status !== "fulfilled") throw new Error("Bad order");
await db.returns.create(...);
await stripe.refunds.create(...);
await email.send(...);
</example>
</context>

## 5. Core/Shell Pre-Flight Verification

<pre-flight-checklist>
Before finalizing workflow code, verify:
1. [ ] Did I name meaningful policies, plans, or decisions?
2. [ ] Did I keep effects out of the pure core?
3. [ ] Did I keep the shell readable and procedural?
4. [ ] Did I preserve repository/framework error conventions where appropriate?
5. [ ] Did I avoid turning one simple procedure into many ceremonial layers?
</pre-flight-checklist>
