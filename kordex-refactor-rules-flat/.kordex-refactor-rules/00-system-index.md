---
description: "Master router for the flat Kordex ontology refactor rules"
globs: "codelens-rn/src/features/ontology/**/*"
alwaysApply: false
version: "1.0.0"
model_target: "universal-router-hybrid"
protocol_compat: "mcp: 2026-05"
last_updated: "2026-06-13"
priority_schema: "critical > strong > guideline"
dependencies: ["mcp-filesystem", "pragmatic-ai-typescript-rules-v3-flat"]
---

# Kordex Refactor System Index

<meta-instruction>
You are operating inside the Kordex ontology/profile/proposal/checker refactor. This is a suggestion/inspiration ruleset, not a mandatory production spec unless the user explicitly adopts it. Route directly to the flat files below before changing code.
</meta-instruction>

<routing-logic>
IF the task touches ontology operation shapes, patch models, command models, event models, or typed errors:
THEN you MUST read and comply with: `.kordex-refactor-rules/01-operation-type-system.md` and `.kordex-refactor-rules/01A-proposal-events.md`.

IF the task touches Effect, typed async workflows, service dependencies, LLM/checker orchestration, or replacing `neverthrow`-style result handling:
THEN you MUST read and comply with: `.kordex-refactor-rules/01B-effect-runtime-spike.md`.

IF the task touches tests, invariants, property-based testing, or proposal safety laws:
THEN you MUST read and comply with: `.kordex-refactor-rules/01C-testing-invariants.md`.

IF the task is a refactor session using Codex, Graphify, Serena, Codebase-Memory, dependency-cruiser, ast-grep, Knip, or TypeDoc:
THEN you MUST read and comply with: `.kordex-refactor-rules/02-refactor-toolchain.md`, `.kordex-refactor-rules/02A-code-map-memory.md`, `.kordex-refactor-rules/02B-boundaries-codemods.md`, and `.kordex-refactor-rules/02C-function-catalog.md`.

IF the task touches manual checker runtime, checker output, checker proposal mapping, proposal insertion, or agent-created ontology suggestions:
THEN you MUST read and comply with: `.kordex-refactor-rules/03-agent-checker-safety.md` and `.kordex-refactor-rules/05-anti-regression.md`.

IF the task touches dependency choices, adding packages, or replacing validation/error/effect libraries:
THEN you MUST read and comply with: `.kordex-refactor-rules/04-package-policy.md`.
</routing-logic>

## System Purpose

The Kordex refactor should move toward explicit, validated, reviewable ontology operations without creating a second hidden mutation path. The repo decision says Kortex Core should stay TypeScript for now while keeping stable operation shapes that future adapters or DSLs can compile into: https://raw.githubusercontent.com/mayett515/codelens-learning-your-code/refactor/ontology-profile/codelens-rn/ONTOLOGY_PROFILE_REFACTOR/08_KORTEX_LANGUAGE_LAYER_AND_ADAPTERS.md

<positive-directives>
- Treat the generic Pragmatic TypeScript v3 flat bundle as the base TypeScript style layer.
- Treat this Kordex bundle as the ontology/proposal/refactor/tooling layer.
- Prefer explicit operation data over hidden service-side mutation behavior.
- Preserve review, preview, approval, event, and audit boundaries.
</positive-directives>

<absolute-constraints>
- DO NOT let checker/model output directly mutate ontology/profile state.
- DO NOT expand operation vocabulary without typed validation, preview, apply, event, and test coverage.
- DO NOT add nested rule folders or orphan rule files.
</absolute-constraints>

<context>
Target Directory Scope: `codelens-rn/src/features/ontology/**/*`
Key References: Kortex language/adapters decision, checker runtime first-slice decision, Pragmatic TypeScript v3 flat bundle.

<example>
// Good: load TypeScript rules, then Kordex router, then the specific flat subfile.
read .ai-rules/00-system-index.md
read .kordex-refactor-rules/00-system-index.md
read .kordex-refactor-rules/01-operation-type-system.md
</example>

<example>
// Bad: edit checker proposal writes without reading the checker safety and anti-regression files.
modify checkerRunService.ts directly
</example>
</context>

<pre-flight-checklist>
Before finalizing a Kordex refactor, internally verify:
1. [ ] Did I load the correct Kordex flat subfiles from the router?
2. [ ] Did I avoid duplicating rules from the generic TypeScript bundle?
3. [ ] Did I preserve proposal review/apply as the only durable mutation path?
</pre-flight-checklist>
