---
description: "Language-inspired extension lenses integrated into the Pragmatic TypeScript schema"
globs: "**/*.{ts,tsx}"
alwaysApply: false
version: "3.0.0"
protocol_compat: "mcp: 2026-05"
dependencies: []
priority_schema: "critical > strong > guideline"
---

# Extension Lenses Index

<meta-instruction>
Extension lenses are part of the schema. They are not separate architecture. Use them as problem-shape detectors for ordinary TypeScript.
</meta-instruction>

## Lens map

```txt
Lua         typed executable config / plugins
Factor/Forth visible left-to-right pipelines
Elm         model, message, update, command
Elixir/Occam workers, messages, ownership, recovery
Julia       operations over domain variants
APL         arrays, tables, metrics, bulk data
miniKanren  constraints, matching, eligibility
Starset     sets, membership, overlap, missing values
Simula      lifecycle over time
SNOBOL      typed parsing and text patterns
Idris       simple validated guarantees
m4          code generation from source of truth
```

## Rules

<positive-directives>
- Apply lenses only when they make TypeScript clearer.
- Keep the base schema intact: types, core, shell, boundary.
- Prefer the smallest lens expression: a union, helper, set, parser, or worker.
- Explain language influence only when teaching or documenting schema design.
</positive-directives>

## Constraints

<absolute-constraints>
- DO NOT make TypeScript cosplay another language.
- DO NOT build fake actor systems, rule engines, or pipeline libraries.
- DO NOT apply every lens to every problem.
- DO NOT use lens names in code comments unless helpful to humans.
</absolute-constraints>

<pre-flight-checklist>
1. [ ] What shape is this problem?
2. [ ] Which lens, if any, makes it clearer?
3. [ ] Is the result ordinary TypeScript?
</pre-flight-checklist>
