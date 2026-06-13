# Starset Lens: Sets as Domain Tools

<meta-instruction>
Use this lens only when the problem shape matches: permissions, scopes, tags, groups, flags, graph edges.
</meta-instruction>

## Guidance

<positive-directives>
- Use ReadonlySet for membership/overlap/missing values when order/duplicates do not matter.
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
const missing = difference(requiredScopes, grantedScopes);
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
