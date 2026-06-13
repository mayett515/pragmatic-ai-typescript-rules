---
description: "Boundary, OOP, SOLID, GoF, adapters, workers, and ownership rules for TypeScript"
globs: "**/*.{ts,tsx,mts,cts}"
alwaysApply: false
version: "1.0.0"
model_target: "gpt-5.5-family"
protocol_compat: "mcp: 2026-05"
dependencies: []
priority_schema: "critical > strong > guideline"
---

# Boundary, OOP & Pattern Contract

<meta-instruction>
Use this file when the task touches classes, dependency injection, adapters, clients, repositories, framework services, workers, queues, actors, decorators, plugins, or design patterns.
</meta-instruction>

## 1. Boundary Directives

<positive-directives>
- You MUST use a class when a boundary owns external capabilities, stateful resources, framework lifecycle, queues, workers, locks, caches, or multiple related use cases.
- You MUST prefer module functions or framework handlers when dependency ownership does not require a long-lived object.
- You MUST keep business rules out of OOP boundaries unless the rule depends on owned capabilities.
- You MUST treat GoF patterns as boundary collaboration shapes, not class-generation commands.
- You MUST use SOLID principles in TypeScript style: focused functions/modules, narrow ports, dependency inversion, and substitutable capabilities.
</positive-directives>

## 2. Boundary Constraints

<absolute-constraints>
- DO NOT create a class only because a function receives dependencies.
- DO NOT put pure domain decisions inside external adapter classes.
- DO NOT use inheritance trees for simple domain variants.
- DO NOT add factories, strategies, proxies, or decorators without real extension, ownership, or cross-cutting behavior.
- DO NOT use decorators to hide business logic.
</absolute-constraints>

## 3. Boundary Ladder

<conditional-logic>
IF there are no side effects:
THEN use a pure function or module helper.

IF there is one use case with injected dependencies and no lifecycle:
THEN prefer a module function with explicit dependency parameters.

IF the framework already provides a boundary through a route, action, middleware, hook, node, or procedure:
THEN use that framework boundary.

IF a boundary hides an external system:
THEN use an adapter/client class or object implementing a narrow port.

IF the code owns concurrency, retries, queues, cancellation, or mutable process state:
THEN use a worker/actor/process boundary.
</conditional-logic>

## 4. Pattern Map

<context>
GoF/OOP patterns usually belong in the boundary layer:

- Adapter: Stripe, SendGrid, S3, Redis, Prisma wrapper, external API clients.
- Facade: service/module hiding several dependencies.
- Proxy/Decorator: auth, caching, logging, retry, metrics wrappers.
- Factory: create clients/adapters from config.
- Command: jobs, queue messages, workflow commands.
- State: lifecycle object only when unions + pure transitions are not enough.
- Strategy: swappable policies when extension is real.
- Observer: events, subscribers, notifications.

<example>
// Good: class owns an external capability and hides provider details.
class StripePaymentProvider implements PaymentProvider {
  constructor(private readonly stripe: StripeClient) {}
  refund(input: RefundInput) { return this.stripe.refunds.create(...); }
}
</example>

<example>
// Bad: class wraps one pure calculation and owns nothing.
class RefundCalculator {
  calculate(item: OrderItem, quantity: number) { return item.unitPrice * quantity; }
}
</example>
</context>

## 5. Boundary Pre-Flight Verification

<pre-flight-checklist>
Before finalizing boundary/OOP code, verify:
1. [ ] What does this boundary own?
2. [ ] Is a class justified by ownership, lifecycle, DI, framework convention, or external capability?
3. [ ] Did I keep pure meaning outside adapter/client classes?
4. [ ] Did any GoF pattern reveal real collaboration instead of adding ceremony?
5. [ ] Did I keep ports/interfaces narrow enough for ISP and DIP?
</pre-flight-checklist>
