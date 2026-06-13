# Result Types and Error Modeling

<meta-instruction>
Use explicit results for expected failures. Keep exceptions for unexpected system failures or framework contracts that require throwing.
</meta-instruction>

## Result guidance

<positive-directives>
- Use `Result<T, E>` for validation, parsing, authorization, and business rule rejection.
- Use typed error unions when the caller can act differently by reason.
- Map typed errors to framework responses at the boundary.
- Keep error names domain-specific and stable.
- Respect existing repo error conventions when they are clear.
</positive-directives>

## Failure constraints

<absolute-constraints>
- DO NOT throw generic `Error` for normal validation/business failures when a typed result would clarify behavior.
- DO NOT introduce `Result` into code that already has a clear library-required throw contract unless it improves the boundary.
- DO NOT return `false` when the reason matters.
- DO NOT collapse unrelated failures into `unknown_error` unless no recovery or message distinction exists.
</absolute-constraints>

<context>
<example>
// Good: expected failure is explicit.
type CreateUserError = "invalid_email" | "email_taken";

type Result<T, E> =
  | { ok: true; value: T }
  | { ok: false; error: E };
</example>

<example>
// Bad: caller must parse strings.
throw new Error("Invalid email");
</example>
</context>

<pre-flight-checklist>
1. [ ] Is this failure expected or unexpected?
2. [ ] Can the caller use the error reason?
3. [ ] Is mapping to HTTP/UI/framework response kept at the boundary?
</pre-flight-checklist>
