---
description: "Main pragmatic multi-paradigm TypeScript architecture contract"
globs: "**/*.{ts,tsx,js,jsx,mts,cts}"
alwaysApply: false
version: "3.0.0-checkpoint"
model_target: "gpt-5.5-family"
protocol_compat: "mcp: 2026-05"
dependencies: []
priority_schema: "critical > strong > guideline"
---

# Pragmatic TypeScript Architecture Contract

<meta-instruction>
You are using the user's evolved TypeScript architecture schema. Treat this schema as a meaning-extraction system. It should reveal hidden domain meaning, explicit effects, and ownership boundaries without adding ceremony.
</meta-instruction>

<routing-logic>
IF the task touches types, validation, unknown input, Zod, Effect, codegen, parser outputs, or modern TypeScript features:
THEN you MUST load and comply with: `.ai-rules/01A-type-strategy.md`.

IF the task touches workflows, rules, decisions, async orchestration, side effects, Result values, or service methods:
THEN you MUST load and comply with: `.ai-rules/01B-functional-core-shell.md`.

IF the task touches classes, DI, clients, repositories, adapters, queues, workers, GoF patterns, decorators, or framework services:
THEN you MUST load and comply with: `.ai-rules/01C-boundaries-oop-patterns.md`.

IF the task touches file splits, modules, comments, folder layout, or architectural documentation:
THEN you MUST load and comply with: `.ai-rules/01D-modular-architecture-comments.md`.
</routing-logic>

## 1. Core Schema

```txt
Type Strategy
↓
Functional Core
↓
Procedural / Imperative Shell
↓
Smallest Honest Boundary
```

## 2. Positive Directives

<positive-directives>
- You MUST put domain meaning in types and pure functions.
- You MUST put execution, IO, and async workflows in procedural shells.
- You MUST put ownership of capabilities, resources, and lifecycle in boundaries.
- You MUST use classes only when ownership, framework integration, lifecycle, or dependency grouping earns them.
- You MUST prefer repository conventions over invented local architecture when the repository already has good boundaries.
</positive-directives>

## 3. Hard Constraints

<absolute-constraints>
- DO NOT add abstraction that does not reveal meaning.
- DO NOT hide business policy inside database calls, HTTP handlers, framework callbacks, or UI render code.
- DO NOT throw generic errors for expected domain failures when a typed decision/result would clarify the flow.
- DO NOT use inheritance where a discriminated union, function, adapter, or composition is clearer.
- DO NOT split files before extracting concepts.
</absolute-constraints>

## 4. Language Lens Map

<context>
The extension lenses are integrated into the schema:

- Haskell/Clojure: honest states, Result values, plain data, small pure functions.
- Lua: typed executable config and plugin boundaries.
- Factor/Forth: visible left-to-right data flow.
- Elm/Simula: UI/workflow state, messages, commands, lifecycle transitions.
- Elixir/Occam: workers, queues, ownership, messages, retries, cancellation.
- Julia: operations over domain variants.
- APL: collection/table/metric-shaped logic.
- miniKanren: constraints, matching, eligibility, policy filtering.
- Starset: sets for permissions, scopes, membership, overlap, missing values.
- SNOBOL: typed parsing of text, JSON-ish, clipboard, logs, URLs, protocols.
- Idris: validated values, branded types, simple compile-time guarantees.
- m4/codegen: generated boring code from one source of truth.

<example>
// Good: hidden magic callback outcomes become a named decision.
type BeforeUploadDecision =
  | { kind: "upload"; file: RcFile }
  | { kind: "skip" }
  | { kind: "ignore" };
</example>

<example>
// Bad: magic values leak through the component shell.
if (result === false) return false;
if ((result as any) === LIST_IGNORE) return false;
if (isPlainObject(result)) return result as RcFile;
</example>
</context>

## 5. Core Pre-Flight Verification

<pre-flight-checklist>
Before finalizing TypeScript changes, verify:
1. [ ] Did I identify the hidden policy, state, parser, transformation, or ownership problem?
2. [ ] Did I keep pure decisions free of IO, framework objects, logging, randomness, and hidden mutation?
3. [ ] Did I keep side effects in a readable procedural shell?
4. [ ] Did I choose the smallest honest boundary?
5. [ ] Did I avoid ceremony greater than meaning?
</pre-flight-checklist>
