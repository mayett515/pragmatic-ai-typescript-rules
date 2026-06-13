# Function Comments

<meta-instruction>
Use function comments to explain policy intent, failure model, purity boundary, or surprising constraints. Avoid narrating implementation.
</meta-instruction>

## Function comment rules

<positive-directives>
- Comment pure decision functions when the business rule is subtle.
- Comment shell functions when side-effect order matters.
- Comment adapter functions when provider quirks are mapped.
- Comment expected failure models when callers might mistake them for exceptions.
- Use short comments close to the function.
</positive-directives>

## Constraints

<absolute-constraints>
- DO NOT comment line-by-line obvious logic.
- DO NOT use comments instead of good names.
- DO NOT explain TypeScript syntax.
- DO NOT leave TODO-style uncertainty in architecture comments.
</absolute-constraints>

<context>
<example>
// Good: explains boundary and testability.
// Decide whether a return is allowed using only order facts.
// No DB, payment provider, email, or clock reads.
function decideReturn(...) {}
</example>

<example>
// Bad: repeats syntax.
// Find item by id.
const item = order.items.find(item => item.id === input.itemId);
</example>
</context>

<pre-flight-checklist>
1. [ ] Does this comment explain why?
2. [ ] Does the function name already say enough?
3. [ ] Is this a policy/boundary/failure/lifecycle detail?
</pre-flight-checklist>
