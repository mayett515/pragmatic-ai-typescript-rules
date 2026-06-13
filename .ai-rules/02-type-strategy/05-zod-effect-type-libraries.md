# Zod, Effect, and Type Libraries

<meta-instruction>
Schema/type libraries are tools for the type strategy. They do not replace the architecture. Use them where they clarify unknown input, typed effects, resources, or validation contracts.
</meta-instruction>

## Zod and schema validators

<positive-directives>
- Use Zod/Valibot/TypeBox/io-ts at untrusted boundaries such as HTTP, forms, webhooks, config, CLI, and external JSON.
- Use inferred types from schemas when the schema is the source of truth.
- Keep business rules in pure functions when they are more than structural validation.
- Use `safeParse` when expected validation failure should not throw.
</positive-directives>

## Effect-style systems

<positive-directives>
- Use Effect when typed effects, resources, retries, concurrency, layers, and error channels are central to the codebase.
- Do not import a full effect system just to avoid writing a small `Result<T, E>`.
</positive-directives>

## Constraints

<absolute-constraints>
- DO NOT treat Zod structural validation as the whole domain model.
- DO NOT hide business policy inside anonymous schema refinements when it deserves a name.
- DO NOT mix multiple schema libraries in one feature without repo convention.
- DO NOT use Effect as local ceremony in a non-Effect codebase.
</absolute-constraints>

<context>
<example>
// Good: schema checks shape; pure function checks business rule.
const TeamSchema = z.object({ plan: z.enum(["free", "pro"]), seats: z.number() });
function validatePlan(input: z.infer<typeof TeamSchema>): PlanDecision { /* policy */ }
</example>

<example>
// Bad: business policy is buried in a long anonymous refinement.
z.object({ /* fields */ }).refine(x => x.plan !== "free" || x.seats <= 3);
</example>
</context>

<pre-flight-checklist>
1. [ ] Is this structural validation or domain policy?
2. [ ] Is the schema source of truth?
3. [ ] Does the library match the repo’s architecture?
</pre-flight-checklist>
