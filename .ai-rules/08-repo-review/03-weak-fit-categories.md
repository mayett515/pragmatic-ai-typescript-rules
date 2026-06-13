# Weak-Fit Categories

<meta-instruction>
Use this file to avoid forcing the schema onto code where it is weak. Weak fit is not failure; it is precision.
</meta-instruction>

## Weak categories

<positive-directives>
- Tiny pure utilities usually need no refactor.
- Infrastructure glue usually needs procedural clarity, not domain extraction.
- Framework registration often should stay boring.
- Highly optimized algorithms should prioritize correctness/performance/locality.
- Type-level library internals may need specialized type design outside this schema.
- Generated code should usually be left alone.
</positive-directives>

## Constraints

<absolute-constraints>
- DO NOT extract helpers from a tiny pure function unless reuse or clarity is real.
- DO NOT split framework registration files just to categorize them.
- DO NOT wrap generated code with manual architecture unless application semantics differ.
- DO NOT reduce algorithmic clarity by forcing policy abstractions.
</absolute-constraints>

<context>
<example>
// Good review outcome:
Original: 9/10
Our schema: confirms existing design.
Best action: leave it alone.
</example>

<example>
// Bad review outcome:
Turning hashKey() into HashKeyService, HashKeyStrategy, and HashKeyFactory.
</example>
</context>

<pre-flight-checklist>
1. [ ] Is this already small/pure/glue/generated?
2. [ ] Is there hidden meaning to extract?
3. [ ] Would a refactor add ceremony?
</pre-flight-checklist>
