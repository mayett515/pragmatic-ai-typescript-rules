# Factor/Forth Lens: Visible Pipelines

<meta-instruction>
Use this lens only when the problem shape matches: normalizers, staged transformations, DTO mapping, parsing stages.
</meta-instruction>

## Guidance

<positive-directives>
- Make data flow left-to-right with named stages. Avoid point-free cleverness and custom pipe libraries unless repo already uses them.
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
const normalized = normalize(raw); const active = keepActive(normalized); return toPreview(active);
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
