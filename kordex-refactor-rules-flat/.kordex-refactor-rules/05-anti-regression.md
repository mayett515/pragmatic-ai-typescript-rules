---
description: "Anti-regression gates for Kordex ontology/proposal/checker refactor"
globs: "codelens-rn/src/features/ontology/**/*.{ts,tsx}"
alwaysApply: false
version: "1.0.0"
model_target: "universal-router-hybrid"
protocol_compat: "mcp: 2026-05"
last_updated: "2026-06-13"
priority_schema: "critical > strong > guideline"
dependencies: ["vitest", "fast-check"]
---

# Kordex Anti-Regression Contract

<meta-instruction>
You have been routed here because the task modifies stable ontology/profile/proposal/checker code or fixes a recurring bug. This file is Via Negativa: it bans known dangerous refactor drift.
</meta-instruction>

## Historical Context

<incident-reports>
- Incident KX-001: Checker or agent logic could become a second mutation path if model output is trusted too directly.
- Incident KX-002: Branch-local observations could accidentally widen into base/core proposals without mature UX and risk gates.
- Incident KX-003: Future operation names could be added before validation, preview, apply, and event semantics exist.
- Incident KX-004: Refactor tools could move code across layers and create hidden UI -> data or checker -> mutation imports.
</incident-reports>

## Hard Regression Bans

<absolute-constraints>
- REGRESSION BAN KX-001: DO NOT auto-apply checker-created proposals.
- REGRESSION BAN KX-002: DO NOT let checker output directly mutate ontology/profile state.
- REGRESSION BAN KX-003: DO NOT create checker base/core proposals in V0.
- REGRESSION BAN KX-004: DO NOT emit relationship, boundary, split, merge, rename, deprecate, move, or maturity operations from checker V0.
- REGRESSION BAN KX-005: DO NOT create duplicate pending checker proposals for the same target branch and proposed node id.
- REGRESSION BAN KX-006: DO NOT bypass dry-run-before-insert for checker-created proposal candidates.
</absolute-constraints>

<conditional-logic>
IF you alter checker runtime, proposal apply, branch freshness, or profile composition:
THEN verify the acceptance criteria from `41_CHECKER_RUNTIME_FIRST_SLICE_DECISION.md` still hold.
</conditional-logic>

<context>
Target Directory Scope: stable ontology/proposal/checker code.
Key Reference: checker first-slice decision and existing stage10 architecture guard tests.

<example>
// Good: fail closed for unsupported checker output
return { created: [], skipped: [{ reason: "unsupported_operation_kind" }] };
</example>

<example>
// Bad: silently reinterpret unsupported checker output as a supported mutation
return applyAsNodePatch(rawUnsupportedFinding);
</example>
</context>

<pre-flight-checklist>
Before finalizing the refactor or bug fix, explicitly verify:
1. [ ] Did I avoid all regression bans?
2. [ ] Did I preserve the proposal review/apply path as the only mutation path?
3. [ ] Did tests or guards prove the dangerous path stays blocked?
</pre-flight-checklist>
