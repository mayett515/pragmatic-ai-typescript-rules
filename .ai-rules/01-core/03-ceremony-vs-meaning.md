# Ceremony vs Meaning

<meta-instruction>
This file defines the central anti-overengineering rule. Apply it whenever a refactor adds files, classes, interfaces, wrappers, registries, or advanced types.
</meta-instruction>

## Definition

```txt
Ceremony = code that exists to support the architecture instead of solving or clarifying the problem.
```

## Good abstraction

<positive-directives>
- Good abstraction names a hidden domain concept.
- Good abstraction reduces repeated policy logic.
- Good abstraction isolates side effects from decisions.
- Good abstraction makes failure reasons explicit.
- Good abstraction creates a boundary for ownership.
- Good abstraction enables focused tests without fake world mocks.
</positive-directives>

## Bad ceremony

<absolute-constraints>
- DO NOT add interfaces around one implementation unless substitution is real.
- DO NOT create classes for pure functions.
- DO NOT split one readable file into many files just because names exist.
- DO NOT build fake engines for two conditions.
- DO NOT use advanced type puzzles when simple unions are enough.
- DO NOT use pattern names as justification for unnecessary structure.
</absolute-constraints>

## Detection question

<context>
Ask:

```txt
If I remove this layer, what knowledge do I lose?
```

If the answer is "almost nothing," the layer is ceremony.

<example>
// Good: removing this loses the return policy.
type ReturnDecision =
  | { kind: "allow"; refundAmount: number }
  | { kind: "deny"; reason: ReturnDenyReason };
</example>

<example>
// Bad: removing this loses almost nothing.
class RefundCalculator {
  calculate(item: Item, quantity: number): number {
    return item.unitPrice * quantity;
  }
}
</example>
</context>

<pre-flight-checklist>
1. [ ] What meaning does this abstraction reveal?
2. [ ] What bug or confusion does it prevent?
3. [ ] Would a simpler function/type/module do the same job?
</pre-flight-checklist>
