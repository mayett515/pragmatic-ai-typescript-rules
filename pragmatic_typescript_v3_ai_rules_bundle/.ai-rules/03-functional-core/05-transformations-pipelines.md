# Transformations and Pipelines

<meta-instruction>
Use clear transformations for data cleanup, DTO mapping, UI display derivation, reports, metrics, and staged normalization.
</meta-instruction>

## Transformation rules

<positive-directives>
- Use small named transformation functions when intermediate concepts matter.
- Prefer left-to-right readability for staged transformations.
- Use collection helpers for collection-shaped problems.
- Keep React components focused on rendering when display data derivation grows.
- Use local helpers before global modules.
</positive-directives>

## Constraints

<absolute-constraints>
- DO NOT use `reduce` when a loop or `map/filter` chain is clearer.
- DO NOT chain many anonymous callbacks when named helpers would explain the steps.
- DO NOT use array methods for ordered side effects.
- DO NOT extract trivial one-line mappers unless reuse or naming value exists.
</absolute-constraints>

<context>
<example>
// Good: component renders; helper derives display data.
const tools = useMemo(
  () => deriveToolIcons(strategy.parameters, inputs.agent_parameters),
  [strategy.parameters, inputs.agent_parameters],
);
</example>

<example>
// Bad: display policy buried in JSX component body with `any` casts.
const tools = []; parameters.forEach(p => { /* mixed derivation */ });
</example>
</context>

<pre-flight-checklist>
1. [ ] Is this transformation meaningful enough to name?
2. [ ] Is the pipeline easier to read after extraction?
3. [ ] Did I avoid fake cleverness?
</pre-flight-checklist>
