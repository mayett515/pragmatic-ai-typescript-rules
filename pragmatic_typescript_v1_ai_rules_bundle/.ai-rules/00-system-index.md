---
version: "3.0.0-checkpoint"
model_target: "universal-router-hybrid"
protocol_compat: "mcp: 2026-05"
dependencies: ["mcp-filesystem"]
last_updated: "2026-06-12"
priority_schema: "critical > strong > guideline"
---

# Master System Architecture & Execution Contract

<meta-instruction>
This document is the master router. Before writing or refactoring code, classify the task, load the relevant `.ai-rules` files, and apply the smallest honest boundary that reveals meaning without adding ceremony.
</meta-instruction>

<routing-logic>
IF the task touches TypeScript, JavaScript, React, Node, APIs, services, workflows, validation, parsing, repositories, adapters, or code architecture:
THEN you MUST load and comply with: `.ai-rules/01-pragmatic-typescript.md`.

IF the task touches type modeling, Zod, Effect, generated types, branded types, discriminated unions, schema validation, external input, parser results, or modern TypeScript features:
THEN you MUST load and comply with: `.ai-rules/01A-type-strategy.md`.

IF the task touches business rules, validation, workflows, side effects, service methods, async orchestration, Result values, or procedural shells:
THEN you MUST load and comply with: `.ai-rules/01B-functional-core-shell.md`.

IF the task touches classes, dependency injection, repositories, clients, adapters, workers, queues, plugins, GoF patterns, decorators, framework services, or ownership boundaries:
THEN you MUST load and comply with: `.ai-rules/01C-boundaries-oop-patterns.md`.

IF the task touches file splitting, modular architecture, comments, folder layout, rule files, or code organization:
THEN you MUST load and comply with: `.ai-rules/01D-modular-architecture-comments.md`.

IF the task is a code review, repo stress test, before/after refactor, schema comparison, or architecture evaluation:
THEN you MUST load and comply with: `.ai-rules/02-repo-review-framework.md`.

IF the task modifies stable systems, core business logic, prior bug fixes, recurring anti-patterns, or established boundaries:
THEN you MUST load and comply with: `.ai-rules/04-anti-regression.md`.
</routing-logic>

## 1. Global Default Behaviors

<positive-directives>
- You MUST optimize for clear data flow, honest types, explicit effects, and practical boundaries.
- You MUST treat the schema as a meaning-extraction system, not a universal refactoring machine.
- You MUST preserve good existing repository conventions when they already express the responsibility clearly.
- You MUST prefer the smallest code change that reveals the hidden policy, state, parser, transition, or boundary.
</positive-directives>

## 2. Global Hard Constraints

<absolute-constraints>
- UNDER NO CIRCUMSTANCES should you add a class around a pure calculation, mapper, validator, or parser only to look architectural.
- DO NOT introduce a file split unless density, reuse, independent testing, or conceptual ownership earns it.
- DO NOT replace repository conventions with local mini-architectures that duplicate existing helpers.
- DO NOT use modern TypeScript features when they add cleverness without revealing behavior.
- SILENT FAILURES ARE BANNED.
</absolute-constraints>

## 3. Global Conditional Logic Gates

<conditional-logic>
IF a code region is already small, pure, obvious, and testable:
THEN prefer leaving it alone or making only naming/type improvements.

IF a code region mixes policy decisions with DB/API/framework effects:
THEN extract the policy as a typed decision before touching the shell.

IF a class owns external capabilities, stateful resources, framework lifecycle, retries, queues, locks, or multiple related use cases:
THEN class/OOP is likely justified.

IF a class owns no capability and only wraps one pure operation:
THEN replace it with a function or module-level helper.
</conditional-logic>

## 4. Master Pre-Flight Verification

<pre-flight-checklist>
Before concluding, internally verify:
1. [ ] Did I identify the target responsibility instead of assuming the whole file needs a rewrite?
2. [ ] Did I separate meaning, execution, and ownership correctly?
3. [ ] Did I avoid ceremony that adds structure without meaning?
4. [ ] Did I choose the smallest honest boundary?
5. [ ] Did I follow every routed sub-file that applies?
</pre-flight-checklist>
