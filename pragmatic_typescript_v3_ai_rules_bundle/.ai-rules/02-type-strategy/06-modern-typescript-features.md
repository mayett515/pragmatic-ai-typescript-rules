# Modern TypeScript Feature Use

<meta-instruction>
Modern TypeScript is part of the schema only when it clarifies contracts, preserves literal meaning, or catches real bugs. Do not use features performatively.
</meta-instruction>

## Recommended features

<positive-directives>
- Use `satisfies` for typed config, route maps, handler registries, policy tables, and error-message maps.
- Use `const` type parameters for define-style helpers that should preserve literal inference.
- Use inferred type predicates and type guards for parser/matcher/collection code.
- Use modern decorators only at framework or boundary layers.
- Prefer strict compiler checks that protect functional-core logic.
- Prefer erasable/plain TS syntax when runtime TS-only constructs add little value.
</positive-directives>

## Constraints

<absolute-constraints>
- DO NOT use decorators for hidden business logic.
- DO NOT use `satisfies` when a simple annotation is clearer and literal preservation is irrelevant.
- DO NOT use `const` type parameters unless the helper’s purpose is preserving literals.
- DO NOT use enums where union literals are simpler and repo style prefers erasable syntax.
</absolute-constraints>

<context>
<example>
// Good: complete map checked against error union.
const messages = {
  invalid_email: "Invalid email",
  email_taken: "Email already taken",
} satisfies Record<CreateUserError, string>;
</example>

<example>
// Bad: modern syntax used without value.
const value = "x" satisfies string;
</example>
</context>

<pre-flight-checklist>
1. [ ] What risk does this TS feature reduce?
2. [ ] Does it preserve useful literal information?
3. [ ] Is it idiomatic for this repo?
</pre-flight-checklist>
