# Domain Types

<meta-instruction>
Use domain types to make important concepts visible. Prefer plain objects and discriminated unions over class hierarchies unless ownership/lifecycle requires OOP.
</meta-instruction>

## When to create a domain type

<positive-directives>
- Create a type when a concept recurs or carries business meaning.
- Create a union when a value can be one of several meaningful variants.
- Create a decision type when callers need to know what happened and why.
- Create state types when boolean flags can contradict each other.
- Keep types close to the feature until reuse earns a shared module.
</positive-directives>

## Anti-patterns

<absolute-constraints>
- DO NOT model meaningful states with multiple booleans.
- DO NOT use `string` for domain states when a union would be clearer.
- DO NOT add optional fields that only make sense for one variant.
- DO NOT export every internal helper type by default.
</absolute-constraints>

<context>
<example>
// Good: impossible combinations are removed.
type PaymentState =
  | { status: "unpaid" }
  | { status: "paid"; transactionId: string }
  | { status: "refunded"; transactionId: string; refundId: string };
</example>

<example>
// Bad: allows paid=false and refunded=true.
type PaymentState = {
  isPaid: boolean;
  isRefunded: boolean;
  transactionId?: string;
  refundId?: string;
};
</example>
</context>

<pre-flight-checklist>
1. [ ] Did the type remove an impossible state?
2. [ ] Is the type understandable by a normal TypeScript engineer?
3. [ ] Is the type scoped to the right module?
</pre-flight-checklist>
