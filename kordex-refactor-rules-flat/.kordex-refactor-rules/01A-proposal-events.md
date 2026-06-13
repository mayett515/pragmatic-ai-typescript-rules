---
description: "Proposal workflow and event boundary rules for Kordex operation application"
globs: "codelens-rn/src/features/ontology/**/*.{ts,tsx}"
alwaysApply: false
version: "1.0.0"
model_target: "universal-router-hybrid"
protocol_compat: "mcp: 2026-05"
last_updated: "2026-06-13"
priority_schema: "critical > strong > guideline"
dependencies: ["zod", "ts-pattern"]
---

# Kordex Proposal And Event Workflow Contract

<meta-instruction>
You have been routed here because the task touches proposals, apply/reject/refresh, event history, or audit semantics. Preserve proposal review as the only durable ontology/profile mutation path.
</meta-instruction>

## Why

The checker first-slice decision says the architecture is correction/user-fit/graph context/checker analysis -> explanation -> evidence -> pending proposal -> user review -> typed validated apply -> audit event. That path must not become optional.

<positive-directives>
- Keep `KordexCommand` separate from `KordexPatch`; commands request workflow actions, patches describe semantic change.
- Emit durable events only after successful validated mutations.
- Snapshot freshness data such as `targetBranchUpdatedAt` when proposals target branch-local state.
- Preserve edit/supersede behavior instead of silently rewriting pending proposals.
</positive-directives>

<absolute-constraints>
- DO NOT auto-apply checker-created proposals.
- DO NOT update, upsert, delete, or rewrite pending checker proposals during checker runs.
- DO NOT create base/core proposals from branch-local checker evidence in V0.
- DO NOT emit audit events for failed, skipped, or rejected preview-only operations.
</absolute-constraints>

<conditional-logic>
IF a proposal is stale:
THEN require explicit refresh/rebase before apply.

IF a duplicate pending proposal exists:
THEN skip creation and mention the existing proposal in read-only explanation.
</conditional-logic>

<context>
Target Directory Scope: `src/features/ontology/**/*proposal*`, `src/features/ontology/data/**/*`
Key References: `41_CHECKER_RUNTIME_FIRST_SLICE_DECISION.md`.

<example>
// Good: command requests apply, service revalidates and emits event after success
{ kind: "ApplyProfileChangeProposal", proposalId, expectedProposalUpdatedAt }
</example>

<example>
// Bad: checker run writes profile state and marks proposal accepted in the same hidden path
await checkerApplyDirectly(modelFinding);
</example>
</context>

<pre-flight-checklist>
Before finalizing proposal code, internally verify:
1. [ ] Does apply revalidate freshness and patch validity?
2. [ ] Are skipped/duplicate/stale cases read-only or explicit failures?
3. [ ] Are durable events emitted only after successful mutation?
</pre-flight-checklist>
