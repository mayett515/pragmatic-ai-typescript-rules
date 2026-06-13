---
description: "Boundary rules, OOP ownership, GoF patterns, and dependency architecture"
globs: "**/*.{ts,tsx}"
alwaysApply: false
version: "3.0.0"
protocol_compat: "mcp: 2026-05"
dependencies: []
priority_schema: "critical > strong > guideline"
---

# Boundary Index

<meta-instruction>
A boundary is where clean program meaning meets messy external systems, frameworks, resources, dependencies, or lifecycle. Boundary does not automatically mean class.
</meta-instruction>

<routing-logic>
IF deciding between function/module/handler/class/adapter/worker:
THEN load `.ai-rules/05-boundaries/01-boundary-ladder.md`.

IF the task touches module use-case functions or dependency objects:
THEN load `.ai-rules/05-boundaries/02-module-boundaries.md`.

IF the task touches Next middleware, Remix actions, tRPC procedures, React hooks/components, NestJS controllers/services, VS Code commands, or framework APIs:
THEN load `.ai-rules/05-boundaries/03-framework-boundaries.md`.

IF the task touches external APIs, repositories, clients, Stripe, SendGrid, S3, Redis, Prisma adapters, or protocol clients:
THEN load `.ai-rules/05-boundaries/04-adapter-boundaries.md`.

IF the task involves classes, services, OOP, GoF patterns, or SOLID at boundaries:
THEN load `.ai-rules/05-boundaries/oop/00-oop-index.md`.
</routing-logic>

## Boundary rules

<positive-directives>
- Use a function when something only decides.
- Use a module when related functions belong together.
- Use a framework handler when the framework already gives a boundary.
- Use an adapter when hiding an external system.
- Use a class when ownership is real.
- Use a worker when lifecycle, retries, concurrency, or owned mutation matter.
</positive-directives>

## Boundary constraints

<absolute-constraints>
- DO NOT equate dependency presence with class necessity.
- DO NOT create classes for stateless pure helpers.
- DO NOT leak external API shapes deep into the functional core.
- DO NOT duplicate existing repo boundaries locally.
</absolute-constraints>

<context>
<example>
// Good: adapter owns external system weirdness.
class StripePaymentProvider implements PaymentProvider {
  constructor(private readonly stripe: StripeClient) {}
  refund(input: RefundInput) { return this.stripe.refunds.create(/* map */); }
}
</example>

<example>
// Bad: class wraps a pure calculation.
class TotalCalculator { calculate(cart: Cart) { return sum(cart.items); } }
</example>
</context>

<pre-flight-checklist>
1. [ ] What capability/resource/lifecycle is owned?
2. [ ] Is a class actually needed?
3. [ ] Is this the smallest honest boundary?
</pre-flight-checklist>
