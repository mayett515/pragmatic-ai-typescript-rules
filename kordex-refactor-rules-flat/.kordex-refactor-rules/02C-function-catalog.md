---
description: "Function responsibility catalog and JSDoc/TypeDoc rules for Kordex core functions"
globs: "codelens-rn/src/features/ontology/**/*.{ts,tsx,md}"
alwaysApply: false
version: "1.0.0"
model_target: "universal-router-hybrid"
protocol_compat: "mcp: 2026-05"
last_updated: "2026-06-13"
priority_schema: "critical > strong > guideline"
dependencies: ["typedoc"]
---

# Kordex Function Catalog Contract

<meta-instruction>
You have been routed here because the task touches documenting what functions are for, generating a function catalog, or adding TypeDoc/JSDoc. Make intent explicit only where it protects architecture.
</meta-instruction>

## Why

No graph tool can perfectly infer Kordex intent. Core functions should state their role, layer, boundary, and invariants so humans and coding agents understand why they exist.

<positive-directives>
- Add JSDoc to exported ontology/proposal/checker functions that enforce boundaries or invariants.
- Use tags such as `@kordexRole`, `@kordexBoundary`, and `@kordexInvariant` for core functions.
- Generate TypeDoc only after comments describe actual stable responsibilities.
- Keep helper comments short unless the helper enforces a semantic invariant.
</positive-directives>

<absolute-constraints>
- DO NOT flood every tiny helper with noisy comments.
- DO NOT document aspirational behavior that the function does not enforce.
- DO NOT expose private helper functions just to make docs look complete.
- DO NOT let generated docs replace tests or boundary rules.
</absolute-constraints>

<conditional-logic>
IF a function is the only allowed entrypoint for mutation:
THEN document that boundary explicitly.

IF a function is moved or split during refactor:
THEN update its catalog comment before using code-memory tools again.
</conditional-logic>

<context>
Target Directory Scope: exported functions in `src/features/ontology`.
Key Tools: TypeDoc, Graphify, Serena/Codebase-Memory.

<example>
// Good: meaning-bearing JSDoc
/**
 * @kordexRole operation-interpreter
 * @kordexBoundary only-entrypoint-for-profile-patch-apply
 * @kordexInvariant rejects-stale-branch
 */
export async function applyKordexPatch(...) {}
</example>

<example>
// Bad: vague comment that adds no responsibility information
/** Does stuff with proposals. */
export async function handle(x) {}
</example>
</context>

<pre-flight-checklist>
Before finalizing docs, internally verify:
1. [ ] Did I document only meaningful boundaries/invariants?
2. [ ] Did I avoid making private helpers public for docs?
3. [ ] Did I update comments after refactor movement?
</pre-flight-checklist>
