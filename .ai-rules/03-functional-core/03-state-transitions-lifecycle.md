# State Transitions and Lifecycle

<meta-instruction>
Use explicit state/event models when a value changes over time and the order of events matters. Avoid lifecycle flag soup.
</meta-instruction>

## Lifecycle rules

<positive-directives>
- Model meaningful lifecycle states as discriminated unions.
- Model events/messages as discriminated unions when transitions are complex.
- Put transition rules in pure functions.
- Keep commands/effects outside transition functions.
- Use fake clocks or passed-in dates for time-dependent transitions.
</positive-directives>

## Constraints

<absolute-constraints>
- DO NOT model lifecycle with contradictory booleans.
- DO NOT perform API calls inside transition functions.
- DO NOT read current time inside a transition without passing time as input.
- DO NOT add a full state machine if a simple decision union is enough.
</absolute-constraints>

<context>
<example>
// Good: lifecycle is explicit.
type ReturnState =
  | { status: "requested"; refundAmount: number }
  | { status: "received"; refundAmount: number }
  | { status: "refunded"; refundId: string };
</example>

<example>
// Bad: impossible combinations are allowed.
type ReturnState = { received: boolean; refunded: boolean; refundId?: string };
</example>
</context>

<pre-flight-checklist>
1. [ ] Is this actually a lifecycle?
2. [ ] Are invalid transitions prevented or obvious?
3. [ ] Is the transition pure?
</pre-flight-checklist>
