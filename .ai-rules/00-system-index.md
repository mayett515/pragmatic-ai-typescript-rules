---
version: "3.0.0"
model_target: "universal-router-hybrid"
protocol_compat: "mcp: 2026-05"
dependencies: ["mcp-filesystem"]
last_updated: "2026-06-12"
priority_schema: "critical > strong > guideline"
---

# Master System Architecture & Routing Contract

<meta-instruction>
You are operating under the Pragmatic TypeScript v3 schema. Before writing or modifying code, route the task into the correct rule folders. The core schema is Type Strategy → Functional Core → Procedural Shell → Smallest Honest Boundary.
</meta-instruction>

<routing-logic>
IF the task involves TypeScript architecture, refactoring, domain logic, services, handlers, React components, workers, or repositories:
THEN you MUST load and comply with: `.ai-rules/01-core/00-core-index.md`.

IF the task creates or changes TypeScript types, schemas, errors, DTOs, parser outputs, generated types, Zod/Effect usage, or validation contracts:
THEN you MUST load and comply with: `.ai-rules/02-type-strategy/00-type-strategy-index.md`.

IF the task extracts business rules, validations, calculations, parsers, transformations, policies, constraints, or state transitions:
THEN you MUST load and comply with: `.ai-rules/03-functional-core/00-functional-core-index.md`.

IF the task touches async workflows, side effects, DB/API calls, payments, email, filesystem, queues, workers, logging, retries, or orchestration:
THEN you MUST load and comply with: `.ai-rules/04-procedural-shell/00-shell-index.md`.

IF the task touches classes, services, adapters, repositories, clients, framework handlers, workers, DI, GoF patterns, or OOP/SOLID decisions:
THEN you MUST load and comply with: `.ai-rules/05-boundaries/00-boundary-index.md`.

IF the task involves file layout, module boundaries, when to split files, folder structure, comments, or rule-file organization:
THEN you MUST load and comply with: `.ai-rules/06-modular-architecture/00-modular-index.md`.

IF the task asks for repo review, before/after refactoring, schema-strength ratings, or stress-testing against open-source code:
THEN you MUST load and comply with: `.ai-rules/08-repo-review/00-review-index.md`.
</routing-logic>

## Global Default Behaviors

<positive-directives>
- Use types and pure functions to reveal meaning.
- Use procedural shells to orchestrate side effects in clear order.
- Use boundaries to own capabilities, dependencies, resources, and framework integration.
- Apply extension lenses only when they make ordinary TypeScript clearer, safer, or easier to test.
- Prefer the smallest honest boundary over architecture ceremony.
</positive-directives>

## Global Hard Constraints

<absolute-constraints>
- DO NOT apply architecture that adds ceremony without revealing meaning.
- DO NOT hide business rules inside framework handlers, ORM calls, adapters, or UI components.
- DO NOT put side effects inside pure-looking decision functions.
- DO NOT create classes that own no dependency, resource, lifecycle, framework role, or stable capability.
- DO NOT split files merely because a concept can be named.
- DO NOT use advanced TypeScript features when plain types express the idea clearly.
</absolute-constraints>

## Global Conditional Logic

<conditional-logic>
IF code is already small, pure, obvious, and testable:
THEN leave it mostly alone and state that the schema confirms the current design.

IF code contains a hidden policy, lifecycle, permission, parser, transition, or external-data boundary:
THEN name that concept with a type or pure function before changing side-effect code.

IF a repo already has an existing architectural boundary:
THEN use that boundary instead of inventing a duplicate local architecture.
</conditional-logic>

## Master Pre-Flight Verification

<pre-flight-checklist>
1. [ ] Did I identify the target responsibility instead of assuming the whole file needs rewriting?
2. [ ] Did I separate meaning, execution, and ownership?
3. [ ] Did I choose the smallest honest boundary?
4. [ ] Did I avoid ceremony that does not reveal meaning?
5. [ ] Did I load the correct subfiles for the task?
</pre-flight-checklist>
