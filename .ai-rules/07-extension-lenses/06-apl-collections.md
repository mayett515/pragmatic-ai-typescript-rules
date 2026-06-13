# APL Lens: Arrays, Tables, and Bulk Data

<meta-instruction>
Use this lens only when the problem shape matches: analytics, reports, imports, metrics, derived arrays, matrices.
</meta-instruction>

## Guidance

<positive-directives>
- Let collection-shaped problems speak in collection operations. Avoid dense chains that hide debugging.
- Keep the result idiomatic TypeScript.
- Map the lens back to Type Strategy, Functional Core, Procedural Shell, or Boundary.
- Apply the smallest useful form of the idea.
</positive-directives>

## Constraints

<absolute-constraints>
- DO NOT apply this lens for novelty.
- DO NOT create abstractions that hide simple code.
- DO NOT violate existing repository conventions.
</absolute-constraints>

<context>
<example>
// Good: lens applied lightly.
const paidAmounts = orders.filter(isPaid).map(order => order.amount);
</example>

<example>
// Bad: lens turned into framework ceremony without real need.
// Overengineered abstraction omitted intentionally.
</example>
</context>

<pre-flight-checklist>
1. [ ] Does the task actually match this lens?
2. [ ] Did the lens reveal meaning?
3. [ ] Did the code remain ordinary TypeScript?
</pre-flight-checklist>
