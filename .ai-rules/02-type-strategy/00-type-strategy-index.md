---
description: "Type strategy for Pragmatic TypeScript v3"
globs: "**/*.{ts,tsx}"
alwaysApply: false
version: "3.0.0"
protocol_compat: "mcp: 2026-05"
dependencies: []
priority_schema: "critical > strong > guideline"
---

# Type Strategy Index

<meta-instruction>
Use types to reveal domain meaning, not to display cleverness. This folder governs discriminated unions, Result types, branded values, generated types, schema libraries, and modern TypeScript features.
</meta-instruction>

<routing-logic>
IF a task models states, decisions, variants, external inputs, parse results, or failures:
THEN load `.ai-rules/02-type-strategy/01-domain-types.md` and `.ai-rules/02-type-strategy/02-results-errors.md`.

IF a task involves validated strings, IDs, non-empty arrays, or values that travel far after validation:
THEN load `.ai-rules/02-type-strategy/03-validated-values.md`.

IF a task involves Prisma, GraphQL, OpenAPI, ATProto Lexicons, generated clients, or codegen:
THEN load `.ai-rules/02-type-strategy/04-generated-types-codegen.md`.

IF a task involves Zod, Effect, TypeBox, Valibot, io-ts, or schema/type libraries:
THEN load `.ai-rules/02-type-strategy/05-zod-effect-type-libraries.md`.

IF a task mentions modern TypeScript features or config:
THEN load `.ai-rules/02-type-strategy/06-modern-typescript-features.md`.
</routing-logic>

## Core Type Directives

<positive-directives>
- Use discriminated unions for meaningful states, decisions, variants, and lifecycle outcomes.
- Use typed errors for expected business or validation failures.
- Use `unknown` at untrusted boundaries and validated types inside.
- Use generated types at external-schema boundaries instead of duplicating contracts.
- Use modern TypeScript features only when they reduce risk or preserve meaning.
</positive-directives>

## Hard Type Constraints

<absolute-constraints>
- DO NOT use `any` when `unknown`, a type guard, or generated type can express the boundary honestly.
- DO NOT use boolean flag soup for meaningful states.
- DO NOT create optional-field objects that allow impossible states.
- DO NOT use branded types if they cause casts everywhere and little safety.
- DO NOT turn simple validation into unreadable type-level puzzles.
</absolute-constraints>

<context>
<example>
// Good: decision reason is explicit.
type UploadDecision =
  | { kind: "upload"; file: RcFile }
  | { kind: "skip" }
  | { kind: "ignore" };
</example>

<example>
// Bad: callers must decode magic values.
type UploadDecision = false | File | "LIST_IGNORE";
</example>
</context>

<pre-flight-checklist>
1. [ ] Does the type name a real domain concept?
2. [ ] Does it prevent an invalid state or clarify a decision?
3. [ ] Is this simpler than a clever generic/type puzzle?
</pre-flight-checklist>
