---
description: "Type strategy for pragmatic TypeScript: domain types, validation, generated types, and modern TS features"
globs: "**/*.{ts,tsx,mts,cts}"
alwaysApply: false
version: "1.0.0"
model_target: "gpt-5.5-family"
protocol_compat: "mcp: 2026-05"
dependencies: ["typescript"]
priority_schema: "critical > strong > guideline"
---

# Type Strategy Contract

<meta-instruction>
Use this file when the task touches types, validators, schemas, parser boundaries, unknown input, Zod, Effect, generated clients, branded types, discriminated unions, or modern TypeScript features.
</meta-instruction>

## 1. Type Strategy Directives

<positive-directives>
- You MUST use types to name domain concepts, states, decisions, expected failures, and boundary contracts.
- You MUST convert unknown external data into validated internal data before persistence or business decisions.
- You MUST prefer discriminated unions for meaningful variants, workflows, parser outcomes, and lifecycle states.
- You MUST use generated types as source-of-truth boundaries when external schemas provide them.
- You MUST use modern TypeScript features only when they preserve meaning or enforce completeness.
</positive-directives>

## 2. Type Strategy Constraints

<absolute-constraints>
- DO NOT use `any` at domain boundaries when `unknown` plus validation is possible.
- DO NOT model meaningful states with boolean flag soup.
- DO NOT use type-level cleverness that the team cannot read or maintain.
- DO NOT duplicate generated schema/client types into parallel hand-written types without a reason.
- DO NOT introduce branded types for values that do not travel far or carry real risk.
</absolute-constraints>

## 3. Tool Guidance

<conditional-logic>
IF input comes from HTTP, form data, files, webhooks, protocol records, clipboard, config, or storage:
THEN treat it as `unknown` until parsed or validated.

IF the codebase already uses Zod or a similar validator:
THEN use it at boundaries for shape validation and use pure functions for domain validation.

IF the codebase is already Effect-shaped or needs typed effects, resources, retries, and concurrency:
THEN Effect may be appropriate; otherwise prefer small `Result<T, E>` values or repository conventions.

IF an object is a typed config, policy table, route map, handler registry, plugin config, or generated-shape glue:
THEN consider `satisfies`.

IF a helper must preserve precise literal inference for config maps:
THEN consider `const` type parameters.
</conditional-logic>

## 4. Context and Examples

<context>
Modern TypeScript features that fit the schema:

- `satisfies`: typed config, policy maps, complete error-message maps.
- `const` type parameters: precise define-style helpers.
- inferred predicates/type guards: parsers, matchers, filters.
- decorators: framework/service boundaries only.
- erasable/plain TS: prefer when runtime magic is unnecessary.

<example>
// Good: external unknown input becomes a typed decision.
type ClipboardParseDecision =
  | { kind: "mixed_content"; value: PastedMixedContent }
  | { kind: "excalidraw_elements"; elements: readonly ExcalidrawElement[] }
  | { kind: "plain_text"; value: string };
</example>

<example>
// Bad: raw JSON parse result flows into domain code without validation.
const data = JSON.parse(text);
return { elements: data.elements, files: data.files };
</example>
</context>

## 5. Type Strategy Pre-Flight Verification

<pre-flight-checklist>
Before finalizing type-heavy code, verify:
1. [ ] Did I name the real domain concept instead of only mirroring transport shape?
2. [ ] Did unknown external data become validated internal data?
3. [ ] Did I avoid boolean flag soup and impossible optional-field states?
4. [ ] Did any modern TS feature earn its place?
5. [ ] Did I avoid type puzzles that add ceremony without safety?
</pre-flight-checklist>
