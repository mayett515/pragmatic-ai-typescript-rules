# Validated Values, Brands, and Simple Guarantees

<meta-instruction>
Use simple type guarantees for costly invalid values. This is the Idris-inspired part of the schema, but keep it teachable TypeScript.
</meta-instruction>

## Good uses

<positive-directives>
- Use branded types for values validated once and passed far, such as Email, UserId, OrderId, Url.
- Use `NonEmptyArray<T>` when an empty array is invalid for a function.
- Use validated constructors returning `Result`.
- Use type guards at external boundaries.
- Keep brands internal if the wider repo does not use them.
</positive-directives>

## Constraints

<absolute-constraints>
- DO NOT brand every string in a small feature.
- DO NOT require casts at every callsite.
- DO NOT use complex conditional types when a runtime validator is clearer.
- DO NOT pretend TypeScript can prove properties it cannot actually enforce.
</absolute-constraints>

<context>
<example>
// Good: email is validated once and safer later.
type Brand<T, Name extends string> = T & { readonly __brand: Name };
type Email = Brand<string, "Email">;

function parseEmail(value: string): Result<Email, "invalid_email"> {
  const email = value.trim().toLowerCase();
  return email.includes("@")
    ? { ok: true, value: email as Email }
    : { ok: false, error: "invalid_email" };
}
</example>

<example>
// Bad: brand with no validated constructor.
type Email = string & { readonly __brand: "Email" };
const email = input as Email;
</example>
</context>

<pre-flight-checklist>
1. [ ] Does this guarantee prevent a real class of bugs?
2. [ ] Is there one clear constructor/parser?
3. [ ] Does the team avoid casts at normal callsites?
</pre-flight-checklist>
