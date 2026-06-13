---
description: "Complete manifest of the flat Pragmatic TypeScript v3 bundle"
globs: ".ai-rules/**/*.md"
alwaysApply: false
version: "3.0.0"
model_target: "gpt-5.5-plus"
protocol_compat: "mcp: 2026-05"
dependencies: []
priority_schema: "critical > strong > guideline"
---

# Manifest

<meta-instruction>
Use this file as the inventory for all flat sibling rule files. This is not the primary router; `00-system-index.md` is.
</meta-instruction>

## Core architecture

- `01-core.md` — mental model and core formula.
- `01A-decision-algorithm.md` — how to apply the schema.
- `01B-ceremony-review-ratings.md` — meaning vs ceremony and ratings.

## Type strategy

- `02-type-strategy.md` — domain types, decisions, errors.
- `02A-validation-libraries-modern-ts.md` — Zod, Effect, type libraries, modern TS.
- `02B-generated-types-codegen.md` — Prisma, Lexicon, OpenAPI, GraphQL, generated clients.

## Functional core and shell

- `03-functional-core.md` — pure decisions, validation, transformations.
- `03A-parsing-lifecycle-policies.md` — parsers, lifecycle, constraints, sets.
- `03B-transformations-solid.md` — pipelines, collection logic, functional SOLID.
- `04-procedural-shell.md` — orchestration and effects.
- `04A-workers-concurrency.md` — workers, queues, retries, cancellation.

## Boundaries and OOP

- `05-boundary-ladder.md` — smallest honest boundary.
- `05A-oop-classes-gof-solid.md` — classes, GoF, SOLID at boundaries.
- `05B-framework-adapters-generated-clients.md` — framework handlers, adapters, generated clients.

## Modularity and comments

- `06-modular-architecture.md` — file splitting, folders, schema-native comparison.
- `06A-comment-architecture.md` — file headers, function comments, anti-comments.

## Extension lenses

- `07-extension-lenses.md` — extension overview.
- `07A-extension-workflow-concurrency-variants.md` — Lua, Factor/Forth, Elm, Elixir/Occam, Julia, APL.
- `07B-extension-constraints-sets-parsing-codegen.md` — miniKanren, Starset, Simula, SNOBOL, Idris, m4.

## Review and regression

- `08-repo-review-framework.md` — real repo review protocol.
- `08A-casebook-strong-fits.md` — strong fit repo findings.
- `08B-casebook-parsers-ui-tooling.md` — parser/UI/tooling findings.
- `08C-casebook-restraint-weak-fits.md` — weak fit and restraint findings.
- `09-anti-regression.md` — global bans and historical drift prevention.

## Specs and templates

- `90-schema-generation-spec.md`
- `90A-file-hierarchy-spec.md`
- `91-template-domain.md`
- `91A-template-anti-regression.md`
- `91B-template-repo-review.md`
- `91C-template-policy-extraction.md`
