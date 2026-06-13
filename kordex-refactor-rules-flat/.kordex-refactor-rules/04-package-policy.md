---
description: "Kordex package selection policy for refactor-related libraries"
globs: "codelens-rn/package.json"
alwaysApply: false
version: "1.0.0"
model_target: "universal-router-hybrid"
protocol_compat: "mcp: 2026-05"
last_updated: "2026-06-13"
priority_schema: "critical > strong > guideline"
dependencies: ["ts-pattern", "fast-check", "effect"]
---

# Kordex Package Policy Contract

<meta-instruction>
You have been routed here because the task touches dependency choices or package installation for the Kordex refactor. Keep the package set small, justified, and reversible.
</meta-instruction>

## Recommended Package Direction

The current app already uses React Native, Expo, OP-SQLite, Drizzle, Zod, Zustand, React Query, TypeScript, and Vitest. Add packages only where they directly protect the operation/proposal/checker refactor.

<positive-directives>
- Add `ts-pattern` for exhaustive handling of operation, proposal, status, and error ADTs.
- Add `fast-check` as a dev dependency for invariant/property-based tests.
- Consider `effect` only as an isolated core workflow spike.
- Prefer existing Zod schemas until an Effect or schema migration proves value.
</positive-directives>

<absolute-constraints>
- DO NOT add `neverthrow` while an Effect spike is still a serious option.
- DO NOT add `fp-ts`, `purify-ts`, `oxide.ts`, `hotscript`, or experimental algebraic-effect libraries for this refactor.
- DO NOT replace Zod with ArkType or Valibot without measured pain and a migration plan.
- DO NOT add Prolog, miniKanren, Datalog, Z3, or RDF tooling to the runtime unless a concrete Kordex use case demands it.
</absolute-constraints>

<conditional-logic>
IF Effect proves clearer for one real service:
THEN consider Effect only in ontology/proposal/checker core services.

IF Effect feels too heavy:
THEN stay with plain TypeScript ADTs, `ts-pattern`, Zod, and `fast-check`.
</conditional-logic>

<context>
Target Directory Scope: `package.json`, core ontology services.
Key Current Dependency Reference: https://raw.githubusercontent.com/mayett515/codelens-learning-your-code/refactor/ontology-profile/codelens-rn/package.json

<example>
// Good: conservative additions
npm install ts-pattern
npm install -D fast-check
</example>

<example>
// Bad: stacking overlapping FP/error libraries
npm install effect neverthrow fp-ts purify-ts oxide.ts
</example>
</context>

<pre-flight-checklist>
Before changing packages, internally verify:
1. [ ] Does this dependency solve an actual Kordex refactor problem?
2. [ ] Is it contained to the correct layer?
3. [ ] Did I avoid overlapping libraries with the same responsibility?
</pre-flight-checklist>
