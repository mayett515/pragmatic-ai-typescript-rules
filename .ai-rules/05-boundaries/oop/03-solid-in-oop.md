# SOLID in OOP Boundaries

<meta-instruction>
Use SOLID to keep OOP boundaries focused and substitutable. Do not translate SOLID into excessive interfaces.
</meta-instruction>

## SOLID mapping

<positive-directives>
- SRP: a class should own one coherent capability or boundary.
- OCP: add adapters/strategies/handlers when extension is real.
- LSP: implementations of a port must have compatible behavior and failure semantics.
- ISP: expose narrow interfaces/ports.
- DIP: use boundaries that depend on ports, not concrete provider SDKs inside use cases.
</positive-directives>

## Constraints

<absolute-constraints>
- DO NOT create an interface for every class automatically.
- DO NOT violate port contracts with special-case behavior.
- DO NOT pass giant repositories/services when a narrow port is enough.
- DO NOT put business rules into provider adapters.
</absolute-constraints>

<context>
<example>
// Good: narrow port.
type PaymentProvider = { refund(input: RefundInput): Promise<void> };
</example>

<example>
// Bad: broad service leaks implementation.
type PaymentService = StripeClient & AnalyticsClient & Logger;
</example>
</context>

<pre-flight-checklist>
1. [ ] Is this class focused?
2. [ ] Is its public contract narrow?
3. [ ] Are implementations substitutable?
</pre-flight-checklist>
