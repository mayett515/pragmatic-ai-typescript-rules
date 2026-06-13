# SOLID Principles in Functional TypeScript

<meta-instruction>
Apply SOLID as design pressure, not class dogma. Functional TypeScript can satisfy SOLID with small functions, ports, decisions, and modules.
</meta-instruction>

## Functional SOLID mapping

<positive-directives>
- SRP: each function/module should have one reason to change.
- OCP: extend with new handlers, strategies, variants, adapters, or policy maps when extension is real.
- LSP: interchangeable functions/adapters must obey the same contract and error semantics.
- ISP: pass only the data/capabilities a function needs.
- DIP: use ports/functions/dependency objects instead of concrete clients inside use cases.
</positive-directives>

## Constraints

<absolute-constraints>
- DO NOT create an interface merely to satisfy SOLID terminology.
- DO NOT hide simple functions behind class hierarchies.
- DO NOT violate a dependency contract by returning subtly incompatible behavior.
- DO NOT pass a giant service object when a narrow capability is enough.
</absolute-constraints>

<context>
<example>
// Good DIP/ISP: use case depends on narrow capabilities.
type ReturnDeps = {
  orders: Pick<OrderRepository, "findById">;
  payments: Pick<PaymentProvider, "refund">;
};
</example>

<example>
// Bad: god dependency leaks everything.
async function requestReturn(app: EntireApplicationContainer, input: Input) {}
</example>
</context>

<pre-flight-checklist>
1. [ ] Is each unit focused?
2. [ ] Are dependencies narrow?
3. [ ] Is extension real or speculative?
</pre-flight-checklist>
