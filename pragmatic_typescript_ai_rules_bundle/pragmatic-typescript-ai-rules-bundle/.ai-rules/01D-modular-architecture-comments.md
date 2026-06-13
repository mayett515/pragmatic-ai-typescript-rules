---
description: "File splitting, modular architecture, and comment schema for pragmatic TypeScript"
globs: "**/*.{ts,tsx,mts,cts,md}"
alwaysApply: false
version: "1.0.0"
model_target: "gpt-5.5-family"
protocol_compat: "mcp: 2026-05"
dependencies: []
priority_schema: "critical > strong > guideline"
---

# Modular Architecture & Comment Contract

<meta-instruction>
Use this file when deciding file splits, folder layout, module boundaries, or comments. Architecture should make navigation easier by placing concepts where they belong.
</meta-instruction>

## 1. Modular Architecture Directives

<positive-directives>
- You MUST extract concepts before extracting files.
- You MUST keep small cohesive features in one file until density, reuse, or testability earns a split.
- You MUST place pure domain helpers near their feature before promoting them to shared/global modules.
- You MUST write comments that explain purpose, allowed responsibilities, forbidden responsibilities, or non-obvious domain rules.
- You MUST keep comments short enough to remain maintained.
</positive-directives>

## 2. Hard Modular Constraints

<absolute-constraints>
- DO NOT create `types.ts`, `errors.ts`, `helpers.ts`, `policy.ts`, and `service.ts` for a tiny feature by default.
- DO NOT split code only because a file passed an arbitrary line count.
- DO NOT write comments that merely narrate obvious syntax.
- DO NOT put framework objects into domain modules.
- DO NOT create shared utilities before at least two real call sites or a strong conceptual reason exists.
</absolute-constraints>

## 3. File Split Gates

<conditional-logic>
IF a file contains one feature under roughly a few hundred readable lines:
THEN keep related types, pure helpers, and shell together unless testing/reuse says otherwise.

IF pure policy helpers grow dense or need focused tests:
THEN split into a nearby feature file such as `asset-edit.domain.ts` or `uploadPolicy.ts`.

IF adapters hide external systems:
THEN place them near infrastructure or integration boundaries.

IF a workflow gains lifecycle states or worker behavior:
THEN consider a lifecycle or worker module.
</conditional-logic>

## 4. Comment Schema

<context>
Use file headers sparingly, mainly for boundary clarification.

Preferred comment blocks:

```txt
Purpose:
May:
May NOT:
```

Use inline comments for domain rules, failure models, and boundary intent. Do not comment obvious language mechanics.

<example>
// Good: explains why this function exists and what must stay out.
/**
 * Functional Core
 * Purpose: Decide whether an asset edit is allowed.
 * May: inspect asset facts and edit actions.
 * May NOT: access repositories, throw framework exceptions, or queue jobs.
 */
</example>

<example>
// Bad: repeats syntax without intent.
// Find the item by id.
const item = order.items.find(item => item.id === input.itemId);
</example>
</context>

## 5. Modular Pre-Flight Verification

<pre-flight-checklist>
Before finalizing modules/comments, verify:
1. [ ] Did I split by responsibility instead of aesthetics?
2. [ ] Did each new file have a clear reason to exist?
3. [ ] Did comments explain intent, boundaries, or domain meaning?
4. [ ] Did I avoid creating shared abstractions prematurely?
5. [ ] Would a future engineer know where to put the next related rule?
</pre-flight-checklist>
