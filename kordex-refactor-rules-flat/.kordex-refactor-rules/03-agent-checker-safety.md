---
description: "Manual checker and agent-created proposal safety rules for Kordex"
globs: "codelens-rn/src/features/ontology/**/*checker*.{ts,tsx}"
alwaysApply: false
version: "1.0.0"
model_target: "universal-router-hybrid"
protocol_compat: "mcp: 2026-05"
last_updated: "2026-06-13"
priority_schema: "critical > strong > guideline"
dependencies: ["zod", "vitest"]
---

# Agent And Checker Safety Contract

<meta-instruction>
You have been routed here because the task touches checker prompts, checker output validation, mapper behavior, manual checker runtime, model adapters, or agent-created suggestions. The checker is a proposal generator, not a mutation engine.
</meta-instruction>

## Why

The locked checker first slice is intentionally narrow: manual, branch-local, proposal-only, additive ontology-node/item-type proposals, strict validation, no auto-apply, no relationship/boundary/split/merge operations.

<positive-directives>
- Keep checker output read-only until validated and mapped by deterministic code.
- Pin checker-created proposals to branch-local targets with current branch revision snapshots.
- Require evidence references for checker-origin proposals.
- Dry-run proposal candidates before inserting them as pending proposals.
</positive-directives>

<absolute-constraints>
- DO NOT allow checker output to include persistence metadata supplied by the model.
- DO NOT create proposals when there is no active branch target; return explanation only.
- DO NOT insert proposals that are already conflicted against current target state.
- DO NOT create checker-run persistence tables in this first slice.
</absolute-constraints>

<conditional-logic>
IF the model returns unsupported shapes or unknown refs:
THEN reject or skip fail-closed with read-only explanation.

IF the checker suggests a future operation kind:
THEN keep it explanatory until the typed operation vocabulary exists.
</conditional-logic>

<context>
Target Directory Scope: `checkerPromptBuilder.ts`, `checkerProposalMapper.ts`, `checkerRunService.ts`.
Key Reference: https://raw.githubusercontent.com/mayett515/codelens-learning-your-code/refactor/ontology-profile/codelens-rn/ONTOLOGY_PROFILE_REFACTOR/41_CHECKER_RUNTIME_FIRST_SLICE_DECISION.md

<example>
// Good: validate model output, map to pending proposal, dry-run, insert survivor only
const proposals = mapValidatedCheckerOutputToCandidates(output, context);
</example>

<example>
// Bad: model returns SQL-ish patch and service applies it directly
await applyModelPatch(rawModelJson);
</example>
</context>

<pre-flight-checklist>
Before finalizing checker code, internally verify:
1. [ ] Did I keep checker behavior manual and proposal-only?
2. [ ] Did I reject unknown refs and unsupported operation kinds?
3. [ ] Did I avoid all direct durable ontology/profile mutation?
</pre-flight-checklist>
