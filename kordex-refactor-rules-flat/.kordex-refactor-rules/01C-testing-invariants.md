---
description: "Kordex invariant and property-based testing rules"
globs: "codelens-rn/src/features/ontology/**/*.{test.ts,ts}"
alwaysApply: false
version: "1.0.0"
model_target: "universal-router-hybrid"
protocol_compat: "mcp: 2026-05"
last_updated: "2026-06-13"
priority_schema: "critical > strong > guideline"
dependencies: ["vitest", "fast-check"]
---

# Kordex Testing Invariants Contract

<meta-instruction>
You have been routed here because the task touches tests, invariants, property-based testing, or proposal safety laws. Treat invariants as part of the Kordex architecture, not as optional examples.
</meta-instruction>

## Why

Kordex risks are semantic: silent mutation, stale branch apply, checker auto-apply, duplicate proposals, and preview/apply mismatch. Example-based tests are useful, but property-based tests with `fast-check` can stress these laws across many generated states.

<positive-directives>
- Use normal Vitest examples for concrete regression cases.
- Use `fast-check` for core laws around preview/apply, freshness, branch-local isolation, and duplicate handling.
- Keep arbitrary generators small, readable, and domain-shaped.
- Test rejected and skipped paths as strongly as successful apply paths.
</positive-directives>

<absolute-constraints>
- DO NOT add operation kinds without tests proving unsupported future kinds fail closed.
- DO NOT rely on model output snapshots as proof of durable proposal safety.
- DO NOT persist proposals that would fail existing compile/dry-run checks.
- DO NOT let property tests generate impossible persisted shapes without schema validation.
</absolute-constraints>

<conditional-logic>
IF a mutation path changes:
THEN add or update invariants proving no base/profile/core state changes outside the intended layer.

IF a checker runtime writes proposals:
THEN test no auto-apply, no base/core target, evidence references, duplicate skip, and per-run cap.
</conditional-logic>

<context>
Target Directory Scope: `src/features/ontology/__tests__/**/*`, `src/__tests__/**/*stage*guard*`
Key Libraries Allowed: `vitest`, `fast-check`.

<example>
// Good: invariant test concept
fc.property(validBranchStateArb, patchArb, (state, patch) => preview(patch, state).diff === apply(patch, state).diff)
</example>

<example>
// Bad: only testing one happy-path proposal apply and assuming the invariant holds everywhere
expect(await apply(oneFixture)).toEqual(successFixture)
</example>
</context>

<pre-flight-checklist>
Before finalizing tests, internally verify:
1. [ ] Did I test both success and fail-closed paths?
2. [ ] Did I protect at least one semantic law with generated cases?
3. [ ] Did I keep generated data valid enough to represent real Kordex state?
</pre-flight-checklist>
