---
description: "Isolated Effect runtime spike policy for Kordex core workflows"
globs: "codelens-rn/src/features/ontology/**/*.{ts,tsx}"
alwaysApply: false
version: "1.0.0"
model_target: "universal-router-hybrid"
protocol_compat: "mcp: 2026-05"
last_updated: "2026-06-13"
priority_schema: "critical > strong > guideline"
dependencies: ["effect"]
---

# Kordex Effect Runtime Spike Contract

<meta-instruction>
You have been routed here because the task touches Effect, typed async orchestration, service dependencies, or the decision to avoid `neverthrow`. Treat Effect as an isolated spike first, not a global rewrite.
</meta-instruction>

## Why

Kordex workflows are dependency-heavy and failure-heavy: load profile state, assemble context, call a model seam, validate output, map proposals, dry-run, transactionally insert, and return typed explanations. Effect can make success, failure, and required services explicit, but only if contained.

<positive-directives>
- Spike Effect on one workflow only: `runManualOntologyChecker` or `applyProfileChangeProposal`.
- Keep operation ADTs plain TypeScript so they survive with or without Effect.
- Model known failures as explicit `KordexError` variants.
- Keep React components and simple hooks outside Effect during the spike.
</positive-directives>

<absolute-constraints>
- DO NOT adopt Effect globally before comparing one real service against the current version.
- DO NOT introduce `neverthrow`, `fp-ts`, `purify-ts`, or `oxide.ts` in parallel with an Effect spike.
- DO NOT rewrite Zod schemas to `effect/Schema` until Effect proves itself in service code.
- DO NOT expose Effect types through UI component props in the first spike.
</absolute-constraints>

<conditional-logic>
IF the Effect spike makes dependencies, failures, cancellation, retries, and tests clearer:
THEN consider adopting Effect only inside the headless ontology/proposal/checker core.

IF the Effect spike adds ceremony without clearer tests or errors:
THEN revert and keep plain TypeScript ADTs plus `ts-pattern`.
</conditional-logic>

<context>
Target Directory Scope: `src/features/ontology/data/checkerRunService.ts`, proposal apply services.
Key Libraries Allowed: `effect`, existing `zod`, existing `vitest`.

<example>
// Good: Effect describes success, known error, and required services
Effect.Effect<ApplyProposalSuccess, ApplyProposalError, ProposalStore | ProfileStore | Clock>
</example>

<example>
// Bad: whole app converted to Effect before the core workflow spike proves value
export function OntologyScreen(): Effect.Effect<JSX.Element, never, AllServices> { ... }
</example>
</context>

<pre-flight-checklist>
Before finalizing Effect code, internally verify:
1. [ ] Is this limited to one core workflow?
2. [ ] Are operation ADTs still plain TypeScript?
3. [ ] Is the Effect version easier to test and reason about than the Promise version?
</pre-flight-checklist>
