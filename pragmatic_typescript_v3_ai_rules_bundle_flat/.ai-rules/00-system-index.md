---
description: "Master router for the flat Pragmatic TypeScript v3 rules ecosystem"
globs: "**/*"
alwaysApply: true
version: "3.0.0"
model_target: "gpt-5.5-plus"
protocol_compat: "mcp: 2026-05"
dependencies: ["mcp-filesystem"]
priority_schema: "critical > strong > guideline"
---

# Master System Architecture & Execution Contract

<meta-instruction>
You are operating under the Pragmatic TypeScript v3 schema. Before writing or refactoring code, classify the task and load the directly referenced flat sibling files below. This file is the root router.
</meta-instruction>

<routing-logic>
IF the task asks for TypeScript architecture, refactoring, code review, or implementation:
THEN you MUST load `.ai-rules/01-core.md`, `.ai-rules/01A-decision-algorithm.md`, and `.ai-rules/01B-ceremony-review-ratings.md`.

IF the task touches domain modeling, errors, validation, schemas, branded values, generated types, Zod, Effect, fp-ts, ts-fp, or modern TypeScript features:
THEN you MUST load `.ai-rules/02-type-strategy.md`, `.ai-rules/02A-validation-libraries-modern-ts.md`, and `.ai-rules/02B-generated-types-codegen.md`.

IF the task touches business rules, pure decisions, transformations, parsing, lifecycle state, policies, permissions, constraints, sets, or functional SOLID:
THEN you MUST load `.ai-rules/03-functional-core.md`, `.ai-rules/03A-parsing-lifecycle-policies.md`, and `.ai-rules/03B-transformations-solid.md`.

IF the task touches async workflows, IO, database calls, HTTP, queues, workers, retries, cancellation, or use-case orchestration:
THEN you MUST load `.ai-rules/04-procedural-shell.md` and `.ai-rules/04A-workers-concurrency.md`.

IF the task touches services, adapters, repositories, framework handlers, OOP, GoF patterns, generated clients, or dependency ownership:
THEN you MUST load `.ai-rules/05-boundary-ladder.md`, `.ai-rules/05A-oop-classes-gof-solid.md`, and `.ai-rules/05B-framework-adapters-generated-clients.md`.

IF the task touches file structure, module boundaries, folder design, comments, documentation comments, or schema-native versus direct refactor comparisons:
THEN you MUST load `.ai-rules/06-modular-architecture.md` and `.ai-rules/06A-comment-architecture.md`.

IF the task asks about extension lenses, language inspiration, plugin systems, pipelines, UI workflows, actors, variants, collections, constraints, sets, parsers, guarantees, or codegen:
THEN you MUST load `.ai-rules/07-extension-lenses.md`, `.ai-rules/07A-extension-workflow-concurrency-variants.md`, and `.ai-rules/07B-extension-constraints-sets-parsing-codegen.md`.

IF the task asks to evaluate open-source repos or rate schema strength:
THEN you MUST load `.ai-rules/08-repo-review-framework.md`, `.ai-rules/08A-casebook-strong-fits.md`, `.ai-rules/08B-casebook-parsers-ui-tooling.md`, and `.ai-rules/08C-casebook-restraint-weak-fits.md`.

IF the task modifies stable core logic, fixes a bug, or risks recreating past architecture drift:
THEN you MUST load `.ai-rules/09-anti-regression.md`.

IF the task asks to generate or edit AI rule files:
THEN you MUST load `.ai-rules/90-schema-generation-spec.md`, `.ai-rules/90A-file-hierarchy-spec.md`, and the relevant template files in `.ai-rules/91*.md`.
</routing-logic>

<positive-directives>
- You MUST apply the schema as: Type Strategy → Functional Core → Procedural Shell → Smallest Honest Boundary.
- You MUST treat extension lenses as part of the schema, not as a separate architecture.
- You MUST rate schema strength against a target responsibility, not automatically against an entire file.
- You MUST preserve existing repo conventions unless doing an explicit schema-native redesign.
- You MUST prefer meaning over ceremony.
</positive-directives>

<absolute-constraints>
- DO NOT create nested `.ai-rules` folders.
- DO NOT apply all sibling files when only one domain is relevant.
- DO NOT use classes merely because dependencies exist.
- DO NOT introduce Result types, state machines, handlers, or folders when they add ceremony without meaning.
- DO NOT rewrite whole files when only a policy seam is the target.
</absolute-constraints>

<pre-flight-checklist>
1. [ ] Did I route to the correct flat sibling files?
2. [ ] Did I identify the target responsibility before applying the schema?
3. [ ] Did I preserve existing repo architecture unless asked for schema-native design?
4. [ ] Did I avoid ceremony that does not reveal meaning?
</pre-flight-checklist>
