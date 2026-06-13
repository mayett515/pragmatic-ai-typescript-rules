# Elixir/Occam Lens: Messages, Ownership, Recovery

<meta-instruction>
Use this lens only when the problem shape matches: workers, queues, actors, retries, cancellation, shared mutation.
</meta-instruction>

## Guidance

<positive-directives>
- Use typed messages and one owner for mutable state. Avoid actors for simple direct calls.
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
type Job = { type: "send_receipt"; orderId: string; email: string };
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
