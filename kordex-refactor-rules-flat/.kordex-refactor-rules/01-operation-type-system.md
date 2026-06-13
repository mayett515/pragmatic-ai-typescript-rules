---
description: "Kordex operation/type-system algebra for patches, commands, events, and errors"
globs: "codelens-rn/src/features/ontology/**/*.{ts,tsx}"
alwaysApply: false
version: "1.0.0"
model_target: "universal-router-hybrid"
protocol_compat: "mcp: 2026-05"
last_updated: "2026-06-13"
priority_schema: "critical > strong > guideline"
dependencies: ["zod", "ts-pattern"]
---

# Kordex Operation Type-System Contract

<meta-instruction>
You have been routed here because the task touches Kordex operation shape design. Model the operation algebra with plain TypeScript ADTs first. Libraries interpret the algebra; they must not replace it.
</meta-instruction>

## Why

Kordex is strongest when ontology evolution is explicit: proposed operation -> validation -> preview/diff -> approval -> event log -> recomposed runtime state. The Kortex language/adapters decision names this as the durable path and warns against arbitrary source-code self-mutation.

<positive-directives>
- Define closed discriminated unions for `KordexPatch`, `KordexCommand`, `KordexEvent`, and `KordexError`.
- Keep v0 executable patches narrow; start with branch-local additive ontology-node patches before relationship or boundary operations.
- Validate persisted operation payloads with Zod or the currently adopted schema validator.
- Interpret operations through explicit `validate`, `preview`, `apply`, `describe`, and `risk` functions.
</positive-directives>

<absolute-constraints>
- DO NOT let raw UI actions, checker output, or agent output skip the command/patch layer.
- DO NOT store unversioned patch payloads.
- DO NOT add relationship, merge, move, rename, boundary, or maturity operations as executable code without a separate typed gate.
- DO NOT hide operation semantics inside React components.
</absolute-constraints>

<conditional-logic>
IF a new operation kind is introduced:
THEN update schema, validator, preview, apply, event emission, risk, description, and tests in the same slice.

IF the operation is speculative or future-facing:
THEN document it as non-executable until validation and apply semantics exist.
</conditional-logic>

<context>
Target Directory Scope: `src/features/ontology/**/*`
Key Libraries Allowed: `zod`, `ts-pattern`, optional future `effect/Schema` after a separate spike.

<example>
// Good: explicit patch ADT
export type KordexPatch =
  | { kind: "AddOntologyNode"; schemaVersion: 1; target: BranchTarget; node: NodeDraft; evidenceIds: string[] };
</example>

<example>
// Bad: hidden mutation without operation shape
await db.insertNode({ label, parentId });
</example>
</context>

<pre-flight-checklist>
Before finalizing operation code, internally verify:
1. [ ] Is every durable mutation represented as typed data first?
2. [ ] Does every operation have validation, preview, and apply semantics?
3. [ ] Did I keep future operation kinds behind explicit gates?
</pre-flight-checklist>
